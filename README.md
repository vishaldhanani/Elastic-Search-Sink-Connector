# Elastic-Search-Sink-Connector
Getting data from the Confluent Audit Log Cluster to Elastic Search using Elastic Search Sink Connector

```
{
  "name": "elasticsearch-sink-confluent-audit-log-events-connector",
  "config": {
    "connector.class": "io.confluent.connect.elasticsearch.ElasticsearchSinkConnector",
    "tasks.max": "1",
    "key.converter": "org.apache.kafka.connect.storage.StringConverter",
    "value.converter": "org.apache.kafka.connect.json.JsonConverter",
    "topics": "confluent-audit-log-events",
    "connection.url": "https://your-elastic-search-url:9200",
    "connection.username": "username",
    "connection.password": "password",
    "type.name": "_doc",
    "key.ignore": "true",
    "schema.ignore": "true",
    "behavior.on.malformed.documents": "WARN",
    "consumer.override.sasl.jaas.config": "org.apache.kafka.common.security.plain.PlainLoginModule required username='${AuditLogClusterAPIKey}' password='${AuditLogClusterAPISecret}';",
    "consumer.override.bootstrap.servers": "confluent-auditlog-cluster-url:9092",
    "consumer.override.sasl.mechanism": "PLAIN",	
    "key.converter.schemas.enable": "false",
    "value.converter.schemas.enable": "false",
    "consumer.override.security.protocol": "SASL_SSL",
    "consumer.override.interceptor.classes": "io.confluent.monitoring.clients.interceptor.MonitoringConsumerInterceptor",
    "consumer.override.confluent.monitoring.interceptor.bootstrap.servers": "http://127.0.0.1:9092",
    "consumer.override.confluent.monitoring.interceptor.sasl.jaas.config" : "org.apache.kafka.common.security.plain.PlainLoginModule required username=\"localusername\" password=\"password\";",
    "consumer.override.confluent.monitoring.interceptor.sasl.mechanism": "PLAIN",
    "consumer.override.confluent.monitoring.interceptor.security.protocol": "SASL_SSL"
  }
}
```
