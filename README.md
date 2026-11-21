# boot2docker-cli

boot2docker-cli manages a lightweight boot2docker virtual machine when you need a local Docker environment backed by VirtualBox. It downloads the boot2docker ISO, configures the VM networks, and provides commands for starting, stopping, and accessing the VM.

> **Deprecated:** This project is retained for reference. Use [Docker Machine](https://docs.docker.com/machine/) for new setups.

## Features

- Download the boot2docker ISO image.
- Create a VirtualBox VM with NAT and host-only networks.
- Initialize, start, stop, and delete the VM with `init`, `up`, `down`, and `delete`.
- Connect to the VM over SSH and run remote commands.
- Report the VM's host-only IP address with `ip`.
- Read VM and network settings from a boot2docker profile.

## Installation

### Precompiled binaries

Download a release binary from the [boot2docker-cli releases page](https://github.com/boot2docker/boot2docker-cli/releases).

### Install from source

The source build requires Go and a configured `GOPATH`:

```sh
go get github.com/boot2docker/boot2docker-cli
```

The binary is installed at `$GOPATH/bin/boot2docker-cli`. To build with version information, clone the repository and run:

```sh
git clone https://github.com/boot2docker/boot2docker-cli.git
cd boot2docker-cli
make goinstall
```

The host also needs VirtualBox, an SSH client, and `ssh-keygen`. The `make` targets can build binaries for supported platforms:

```sh
make darwin
make linux
make windows
make all
```

## Usage

Initialize and start a VM:

```sh
boot2docker-cli init
boot2docker-cli up
```

Show its host-only IP address:

```sh
boot2docker-cli ip
```

Run a command on the VM over SSH:

```sh
boot2docker-cli ssh ip addr show eth1
```

Stop the VM when it is no longer needed:

```sh
boot2docker-cli down
```

Delete the VM and its associated configuration:

```sh
boot2docker-cli delete
```

The command reads configuration from `$BOOT2DOCKER_PROFILE`, `$BOOT2DOCKER_DIR/profile`, `$HOME/.boot2docker/profile`, or `%USERPROFILE%/.boot2docker/profile` on Windows. Run `boot2docker-cli config` to display the active configuration path and settings.

## License

This project is licensed under the Apache License 2.0.

boot2docker-cli is based on [boot2docker/boot2docker-cli](https://github.com/boot2docker/boot2docker-cli). Copyright and license notices from that project are retained in accordance with Apache-2.0 attribution requirements.
