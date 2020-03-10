# 操作步骤

1、修改 application-dev.yml 中数据库连接为你本地连接地址

2、执行 table.sql 中 sql 语句

3、修改 TransactionProducer 及 Consumer 中 nameServer 地址

4、启动 MainApplication

5、用户 1 给用户 2 转账操作，访问 http://localhost:8080/test/mqTest，每次转账 100 元

```
    用户1初始金额100
    用户2初始金额0
    
    第一次转账用户1金额足够，操作成功，发送prepare消息并commit，消息被成功投递，consumer消费到
    第一次转账用户2金额不够，操作失败，发送prepare消息并rollback，消息被丢弃
```   

# rocket

docker 目录中为 rocket 的 docker-compose.yml 文件，需要将 opt/rocketmq/conf/broker.conf 中的 brokerIP1 改为服务器的 IP 才可以使用