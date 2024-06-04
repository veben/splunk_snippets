# Splunk Standalone Instance

As described in the `docker-compose.yml`, this setup leverages a standalone installation of Splunk

## I. Prerequisites
**Docker** installed on your system

## II. Lanching
### Via **Docker compose**:
> If `SPLUNK_IMAGE` is not set, it defaults to `splunk/splunk:latest`
```sh
SPLUNK_PASSWORD=<password> docker-compose up -d
``` 

Replace `<password>` with a password with an important complexity

### or via **Docker CLI**
```sh
docker run --name so1 --hostname so1 -p 9000:8000 \
    -e "SPLUNK_PASSWORD=<password>" \
    -e "SPLUNK_START_ARGS=--accept-license" \
    -it splunk/splunk:latest
```

Replace `<password>` with a password with an important complexity

## III. Testing
- Check container status:
```sh
$ docker container ls
CONTAINER ID   IMAGE                  COMMAND                  CREATED          STATUS                             PORTS                                                                                              NAMES
5b405a3d0c19   splunk/splunk:latest   "/sbin/entrypoint.sh…"   32 seconds ago   Up 30 seconds (health: starting)   8065/tcp, 8088-8089/tcp, 8191/tcp, 9887/tcp, 9997/tcp, 0.0.0.0:9000->8000/tcp, :::9000->8000/tcp   so1
```
- Access Splunk via browser
    - URL: http://localhost:9000/
    - username: **admin**
    - password: what you defin in `SPLUNK_PASSWORD` environment variable
