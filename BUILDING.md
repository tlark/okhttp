Building
============

Maven (okhttp_3.x)
------------------

To build the entire project and install jars in your local Maven repo:
```
mvn clean install -DskipTests
```

To build the entire project and publish jars to jfrog.io (libs-snapshots-local):
```
mvn clean deploy -DskipTests
```

If you try to do `mvn clean install deploy -DskipTests`, it will fail since 
duplicate uploads are attempted.

Make sure your `~/.m2/settings.xml` have entries for `libs-snapshot-local`,
`libs-release-local` and `everything`.  Some thing like this:
```
  <profiles>
    <profile>
      <repositories>
        <repository>
          <snapshots>
            <enabled>false</enabled>
          </snapshots>
          <id>central</id>
          <name>libs-release</name>
          <url>https://zimperium.jfrog.io/zimperium/libs-release</url>
        </repository>
        <repository>
          <snapshots />
          <id>snapshots</id>
          <name>libs-snapshot</name>
          <url>https://zimperium.jfrog.io/zimperium/libs-snapshot</url>
        </repository>
        <repository>
          <snapshots>
            <enabled>false</enabled>
          </snapshots>
          <id>everything</id>
          <name>everything</name>
          <url>https://zimperium.jfrog.io/zimperium/everything</url>
        </repository>
      </repositories>
      <pluginRepositories>
        <pluginRepository>
          <snapshots>
            <enabled>false</enabled>
          </snapshots>
          <id>central</id>
          <name>plugins-release</name>
          <url>https://zimperium.jfrog.io/zimperium/plugins-release</url>
        </pluginRepository>
        <pluginRepository>
          <snapshots />
          <id>snapshots</id>
          <name>plugins-release</name>
          <url>https://zimperium.jfrog.io/zimperium/plugins-release</url>
        </pluginRepository>
        <pluginRepository>
          <snapshots>
            <enabled>false</enabled>
          </snapshots>
          <id>everything</id>
          <name>everything</name>
          <url>https://zimperium.jfrog.io/zimperium/everything</url>
        </pluginRepository>
      </pluginRepositories>
      <id>artifactory</id>
    </profile>
  </profiles>
  <activeProfiles>
    <activeProfile>artifactory</activeProfile>
  </activeProfiles>
```