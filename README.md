An example of installing [mongo shell and tools](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-ubuntu/) in a docker container.

* **mongodb-org-shell**, contains the mongo shell.
* **mongodb-org-tools**, contains the following MongoDB tools: mongoimport bsondump, mongodump, mongoexport, mongofiles, mongorestore, mongostat, and mongotop.

```
docker build --rm -t thelebster/mongo-shell-example .

docker run -ti --rm --name mongo-shell-example -d thelebster/mongo-shell-example
```

```
docker exec -it mongo-shell-example bash
```

```
docker run -ti --rm --name mongo-shell-example -v "$PWD"/data:/var/mongo/data -d thelebster/mongo-shell-example

docker exec -it mongo-shell-example mongoexport --host 127.0.0.1 --port 27017 --collection MONGODB_COLLECTION --db MONGODB_NAME --jsonArray --out /var/mongo/data/"$(date +"%m_%d_%Y-%H:%M")".json

docker exec -it mongo-shell-example mongodump --host 127.0.0.1 --port 27017 --db MONGODB_NAME --gzip --archive=/var/mongo/data/"$(date +"%m_%d_%Y-%H:%M")".gz
```
