# Grafana Setup using Docker Compose

The Repo contains a basic setup configuration for Grafana using Docker compose

The compose file contains 3 services
1. Grafana
2. Prometheus
3. Node Exporter

To run Grafana, follow
```
# git clone the repo and cd into it
docker compose up -d
```

PromQL for some common use cases:

1. CPU Usage :

```(1 - avg(irate(node_cpu_seconds_total{mode="idle"}[10m])) by (instance)) * 100```

2. Memory Usage :

```100 * (1 - ((avg_over_time(node_memory_MemFree_bytes[10m]) + avg_over_time(node_memory_Cached_bytes[10m]) + avg_over_time(node_memory_Buffers_bytes[10m])) / avg_over_time(node_memory_MemTotal_bytes[10m])))```