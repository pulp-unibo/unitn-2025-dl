# UNITN PULP PhD School

## Environment setup
This setup targets advanced deployment tools related to the PULP setup.
The execution environment for this class is distributed as a Docker container available in Docker Hub for both x86_64 (Intel / AMD based machines) and arm64 devices (Apple M-series processors, other devices using Qualcomm SoCs).
The same setup will be used also in the other lab sessions.

### Quick look at first usage
![Alt Text](https://raw.githubusercontent.com/EEESlab/hsdes-2025/refs/heads/main/screencast/setup_screencast.gif)

### Recommended setup: Docker + VSCode + Dev Container
1. Install Docker. You can follow instructions here: [Docker Desktop](https://www.docker.com/products/docker-desktop/) for Windows or macOS and [Docker Engine](https://docs.docker.com/engine/install/) for Linux distros.
2. Install [Visual Studio Code](https://code.visualstudio.com/)
3. Open Visual Studio Code, then through the Extensions tab look for the [Dev Containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers) extension.
4. Open this folder (HSDES-LAB01-PULP_Embedded_Programming) from Visual Studio Code. VSCode will ask you (bottom-right corner) to "Reopen in Container": select yes. The required setup should be automatically downloaded.
5. The Visual Studio Code terminal on the bottom will use an already configured workspace. The lab folder will be mounted under `/workspaces`.

### Alternate setup: Docker + Own editor
1. Install Docker. You can follow instructions here: [Docker Desktop](https://www.docker.com/products/docker-desktop/) for Windows or macOS and [Docker Engine](https://docs.docker.com/engine/install/) for Linux distros.
2. Open a terminal. You can pull the Docker container with the following command:
```
docker pull fconti/unitn25-qnn
```
3. Enter the folder of this lab session, and run the following to enter the container shell.
```
docker run --rm -it -v "$(pwd)":/workspaces -w /workspaces fconti/unitn25-qnn
```
4. The Docker terminal that is opened will contain an already configured workspace. The lab folder will be mounted under `/workspaces`.

## Installing 
First of all, make sure all submodules are properly initialized:
```
git submodule update --init --recursive
```
After that, install Deeploy and DeepQuant:
```
cd Deeploy && pip install -e . && cd ..
cd DeepQuant && pip install -e . && cd ..
```
We use an editable install to allow (if necessary or desired) to modify the tools.

## Tutorials
There are three tutorials available here:
 1. `brevitas-deepquant-tutorial`: shows how to go from the training of a DNN (using a simple Fashion-MNIST example) down to a deployable format
 2. `deeploy-user-tutorial`: this tutorial introduces Deeploy and how to use it, and understand what it does internally
 3. `deeploy-newop-tutorial`: this (advanced) tutorial on Deeploy introduces how to add a new modified operator to the tool