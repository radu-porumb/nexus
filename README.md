# Nexus Repository Manager OSS

[![](https://images.microbadger.com/badges/image/raduporumb/nexus.svg)](https://microbadger.com/images/raduporumb/nexus "Get your own image badge on microbadger.com")

A Sonatype Nexus Repository Manager image based on Alpine with OpenJDK 8.

Running Nexus with:
* Repository on port 8081
* Docker Registry (hosted) on port 5000
* Data persistence on a host directory

```
docker run -d --name nexus \
    -v /path/to/nexus-data:/nexus-data \
	-p 8081:8081 \
	-p 5000:5000 \
	raduporumb/nexus
```

## Notes

* Default credentials are: `admin` / `admin123`

* It can take some time for the service to launch in a new container. You can tail the log to determine once Nexus is ready:

```
$ docker logs -f nexus
```

* Test with curl:

```
$ curl -u admin:admin123 http://localhost:8081/service/metrics/ping
```

* Installation of Nexus is to `/opt/sonatype/nexus-version`.  

* A persistent directory, `/nexus-data`, is used for configuration, logs, and storage.

* Three environment variables can be used to control the JVM arguments

  * `JAVA_MAX_MEM`, passed as -Xmx.  Defaults to `1200m`.

  * `JAVA_MIN_MEM`, passed as -Xms.  Defaults to `1200m`.

  * `EXTRA_JAVA_OPTS`.  Additional options can be passed to the JVM via this variable.
