## Introduction
This directory contains the sources for an example project as part of the Java Tutorial found at
<https://bazel.build/start/java>.

## Getting Started

Here is a summary of important commands from the tutorial to get started with this Java Tutorial.
All commands should be executed from **java-tutorial** directory

### Development

- Build the project
  ```shell
  bazel build //:ProjectRunner
  ```

- Test build binary
  ```shell
  ./bazel-bin/ProjectRunner
  ```
  
- Review the depedency graph. You can visualize the graph  by pasting the output into [GraphViz](http://www.webgraphviz.com/).
  ```shell
  bazel query  --notool_deps --noimplicit_deps "deps(//:ProjectRunner)" --output graph
  ```

- Build **greeter** java library target
  ```shell
   bazel build //:greeter
  ```
  
- Build a new package by full package path
  ```shell
  bazel build //src/main/java/com/example/cmdline:runner
  ```
  
- Test package built binary
  ```shell
  ./bazel-bin/src/main/java/com/example/cmdline/runner
  ```
  
### Deployment

- Check content of java binary using the following command, you can see that dependencies (Greeting.class) are not included in the jat file
  ```shell
  jar tf bazel-bin/src/main/java/com/example/cmdline/runner.jar
  ```

- Package a Java target for deployment by appending *_deploy.jar* to the target name
  ```shell
  bazel build //src/main/java/com/example/cmdline:runner_deploy.jar
  ```
