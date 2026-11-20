# CAS Management Overlay

这是一个 CAS Management WAR overlay 配置示例。Gradle 定义构建，外部配置独立于 WAR。JDK 11 是仓库声明的构建环境。可以从 [Gradle 构建](build.gradle)、[外部配置](etc/cas/config/management.properties) 和 [Docker 构建](Dockerfile) 沿着打包与部署过程阅读。下方保留原有构建文档。

CAS management web application WAR overlay for CAS with externalized configuration.

# Versions

```xml
<cas.version>6.3.x</cas.version>
```

# Requirements

* JDK 11

# Build

To see what commands are available to the build script, run:

```bash
./build.sh help
```

To package the final web application, run:

```bash
./build.sh package
```

To update `SNAPSHOT` versions run:

```bash
./build.sh package -U
```

## Windows Build

On Windows you can run build.cmd instead of build.sh. The usage may differ from build.sh, run "build.cmd help" for usage.

## Note

If you are running the management web application on the same machine as the CAS server web application itself, 
you will need to evaluate the build script and make sure the configuration files don't override each other.

# Deployment

## Embedded Tomcat

CAS will be available at:

* `http://cas.server.name:8080/cas-management`
* `https://cas.server.name:8443/cas-management`

## External

Deploy resultant `target/cas-management.war`  to a servlet container of choice.

### Dockerfile

You can also use the native Docker tooling and the provided `Dockerfile` to build and run CAS Management.

```bash
chmod +x *.sh
./docker-build.sh
./docker-run.sh
```
