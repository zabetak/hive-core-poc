# Apache Hive core jar generation (POC)

This project showcases how a project can produce jar(s) with content similar to the hive-exec-core.jar, which was
removed from Apache Hive 4.0.0 as part of [HIVE-25531](https://issues.apache.org/jira/browse/HIVE-25531), by exploiting
the [unpack goal](https://maven.apache.org/plugins/maven-dependency-plugin/usage.html#dependency:unpack) of the
maven-dependency-plugin.

The project is divided into two modules:
* hive-exec-core
* consumer

The hive-exec-core module contains a vanilla usage of the maven-dependency-plugin to create a jar that contains all
classes under the `org.apache.hadoop.hive.ql` package from the hive-exec module of Hive.

The consumer module demonstrates that the generated jar can be used in the rest of the build as usual by simply
declaring its respective module as dependency.

To compile the project run `mvn clean install`.

To inspect the content of the generated "core" jar run `jar tf hive-exec-core/target/hive-exec-core-1.0-SNAPSHOT.jar`.
