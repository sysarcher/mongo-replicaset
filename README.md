# Running Mongodb Replica Set

I created the `docker-compose.yaml` file using [this tutorial](https://www.mongodb.com/compatibility/deploying-a-mongodb-cluster-with-docker)

Set the version of mongodb to the one you want in the `.env` file.

Start the containers and networking:
```shell
$ docker compose up -d
```

Initiate the replicaset:
```shell
$ # initiate the replica set
$ docker exec -it mongo1 mongosh --eval "rs.initiate({
 _id: \"myReplicaSet\",
 members: [
   {_id: 0, host: \"mongo1\"},
   {_id: 1, host: \"mongo2\"},
   {_id: 2, host: \"mongo3\"}
 ]
})"
```

Verify:
```shell
$ docker exec -it mongo1 mongosh --eval "rs.status()"
```

