<h1>Installing ContainerSSH</h1>

ContainerSSH is provided on the [GitHub releases page](https://github.com/containerssh/containerssh/releases). You can install it in a containerized environment or as a standalone software on Windows, Linux, and MacOS.

## Running in a containerized environment

When running ContainerSSH in a containerized environment we recommend using the image `containerssh/containerssh`. You will also need to mount or provide the following files:

`/etc/containerssh/config.yaml`
: This is the base [configuration file](../configuration/). Parts of it can be modified by the configuration server call.

`/var/secrets/ssh_host_rsa_key`:
: This is the default path for the host key. You can generate this host key using the OpenSSH tool `ssh-keygen -t rsa -b 4096 -P /var/secrets/ssh_host_rsa_key`

When using the `dockerrun` backend, you can also mount `/var/run/docker.sock` into the container. Alternatively, you can set up the [Docker socket via TCP](https://docs.docker.com/engine/security/https/).

## Running as a standalone application

ContainerSSH is supplied as a single binary that runs on all major platforms. After downloading the binary and [creating the configuration file](../configuration/) you can run ContainerSSH with the following command:

```
containerssh --config /path/to/your/configuration/file
```