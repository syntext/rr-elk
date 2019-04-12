#Source
https://github.com/deviantony/docker-elk
https://qbox.io/blog/elasticsearch-logstash-kibana-manage-nginx-logs
https://github.com/elastic/logstash/blob/v1.4.2/patterns/grok-patterns
https://stackoverflow.com/questions/44128855/how-to-grok-the-java-stack-trace-in-elasticsearch-using-logstash
http://grokconstructor.appspot.com/do/match
http://www.madhur.co.in/blog/2017/04/09/usingcuratordeleteelasticindex.html


#Tutorials
Use Logstash to load CSV into Elasticsearch
https://www.youtube.com/watch?v=rKy4sFbIZ3U


#Linux - Create data directory
mkdir data
chmod 777 data

#Using curator to delete older elasticsearch indices
To run this action, simple use the command

```bash
curator ./delete_index.yml --config ./curator.yml --dry-run
2017-04-09 17:27:46,075 INFO      Preparing Action ID: 1, "delete_indices"
2017-04-09 17:27:46,080 INFO      Trying Action ID: 1, "delete_indices": Delete indices older than 45 days (based on index name), for logstash- prefixed indices. Ignore the error if the filter does not result in an actionable list of indices (ignore_empty_list) and exit cleanly.
2017-04-09 17:27:46,538 INFO      DRY-RUN MODE.  No changes will be made.
2017-04-09 17:27:46,538 INFO      (CLOSED) indices may be shown that may not be acted on by action "delete_indices".
2017-04-09 17:27:46,538 INFO      Action ID: 1, "delete_indices" completed.
2017-04-09 17:27:46,538 INFO      Job completed.
```

If you want to schedule it in a cron, you can do so using crontab -e
```bash
0 4 * * * curator /home/ron/docker-elk/delete_index.yml --config /home/ron/docker-elk/curator.yml
```
