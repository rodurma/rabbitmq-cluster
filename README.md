# RabbitMQ Cluster

Start with this command:

```
docker compose up -d
```

Access the second container:

```
docker exec -it cluster-rabbitmq-2 /bin/bash
```

And run:

```
rabbitmqctl --node cluster-rabbitmq-2@host-rabbitmq-2 stop_app
rabbitmqctl --node cluster-rabbitmq-2@host-rabbitmq-2 join_cluster cluster-rabbitmq-1@host-rabbitmq-1
rabbitmqctl --node cluster-rabbitmq-2@host-rabbitmq-2 start_app
```

Access the third container:

```
docker exec -it cluster-rabbitmq-3 /bin/bash
```

And run:

```
rabbitmqctl --node cluster-rabbitmq-3@host-rabbitmq-3 stop_app
rabbitmqctl --node cluster-rabbitmq-3@host-rabbitmq-3 join_cluster cluster-rabbitmq-1@host-rabbitmq-1
rabbitmqctl --node cluster-rabbitmq-3@host-rabbitmq-3 start_app
```

Access management:

- http://localhost:15672/
- http://localhost:15673/
- http://localhost:15674/