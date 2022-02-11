# Trying out C development with VSCode remote

This repository is based on: [https://github.com/Microsoft/vscode-remote-try-cpp](https://code.visualstudio.com/docs/remote/containers).

Contains an example of how VS Code can be used for C/assembly development on a Linux enviroment using [Visual Studio Code Remote - Containers](https://code.visualstudio.com/docs/remote/containers).

## Trying it out

1. Ensure this VSCode extension is installed - [https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers).
1. Ensure [Docker Desktop](https://www.docker.com/products/docker-desktop) is installed.
1. Clone this repo into a local folder and open VS Code on it.
1. On VS Code left bottom corner there will be a little green icon. Select it and the choose `Open in container`.
     - This will restart VS Code in a remote mode - see [Remote development in Containers](https://code.visualstudio.com/docs/remote/containers) - and start a new Docker container (may take some time on the first run due to the image downloading).
     - The VS Code UI will be running in the host OS (e.g. Windows or macOS), connected to a **VS Code Server** running inside the container.
1. Open a terminal and run `uname`. The output should be `Linux`, i.e., that terminal is running _inside_  the container.
1. Open `main.c` and add a breakpoint to the `int theAnswer = answer();` line. Notice how the C/C++ VS Code development tools are already installed.
1. Press F5 (`Start Debugging`) and see how a debug session starts.
1. On the guest OS, run `docker ps` to see the running containers and then run `docker exec -ti <container-name> bash` to open a shell inside the container. Run `ps -a` and see how a `gdb` process is running. End the debug session on VS Code and run `ps -a` again. Yes the `gdb` process is gone, because the debug session being shown by VS Code was running inside the container.
