# danielguerra/moloch

Docker Moloch 18.2 container

Image is based on the [ubuntu](https://hub.docker.com/r/library/ubuntu/) 16.04 image

## Docker image usage

First start elasticsearch 5.2.2

```
docker run -d --name es elasticsearch:5.2.2-alpine
```

Then start moloch
```
docker run --link es:elasticsearch danielguerra/moloch [capture]
```

## Examples

Run capture on docker container eth0 interface:

```
docker run --link es:elasticsearch danielguerra/moloch capture
```

Run viewer and import pcap to analyze:

```
docker run -d --name moloch --link es:elasticsearch -v /path/to/host/pcap:/data/pcap:rw danielguerra/moloch
docker exec containerid /data/moloch/bin/moloch-capture -r /data/pcap/sniff.pcap -t mysniff
```
