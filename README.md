![](https://img.shields.io/github/v/release/pureone-tcy/elastic-stack-local)
![](https://img.shields.io/github/last-commit/pureone-tcy/elastic-stack-local)

# Elastic Stack Local
- Build Elasticsearch, Kibana, Logstash environment (v7.2.0) on local docker container.
- Use `Logstash File input plugin` to automatically push json file under `logstash/pipeline/input/` to Elasticsearch.

## Build & Run
```bash
$ docker-compose up -d
```
- Access to Kibana (http://localhost:5601/)

## Setting files
- Data pipeline  
  `logstash/pipeline/logstash.conf`
- Index Template  
  `logstash/pipeline/template/index_template.json`
- Add Sample Data  
  `logstash/pipeline/input/*.json`

## Stop
```bash
$ docker-compose stop 
```

## Delete environment
```bash
$ docker-compose down
```

```bash
$ docker images
REPOSITORY                                      TAG                 IMAGE ID
docker.elastic.co/logstash/logstash             7.2.0               XXXXXXXXXXXX
docker.elastic.co/kibana/kibana                 7.2.0               XXXXXXXXXXXX
docker.elastic.co/elasticsearch/elasticsearch   7.2.0               XXXXXXXXXXXX
$ docker rmi IMAGE ID
```

## Bulk Import
- Example of importing json file for bulk import  
  (The sample zip file was downloaded from Elastic's official website.)
```
$ cd data
$ unzip accounts.zip
$ curl -s -H "Content-Type: application/x-ndjson" -XPOST localhost:9200/_bulk --data-binary @accounts.json
```
