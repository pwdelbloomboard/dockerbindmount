# dockerbindmount

# Video Demo

.
# Prerequisites

* Docker

# Quick Install - Docker Version

1. With terminal, navigate to "/" - the root folder.
2. Run in the '/app' directory:

```
docker build -t jupyter/custom-notebook .
```

3. After image is built, go directly into the "/" base project directory from the terminal and run:

```
docker run -it --rm                                   \
-p 8888:8888                                          \
-e JUPYTER_ENABLE_LAB=yes                             \
--mount type=bind,source="$(pwd)"/target,target=/app  \
--name datanotebook                                   \
jupyter/custom-notebook
```

* -it ...is interactive tty mode.
* --rm ...Automatically removes the container when it exits
* -e ...Sets environment variables, in this case we ask to use the new version, "JUPYTER_ENABLE_LAB=yes" instead of Jupyter Notebook.
* -v ${PWD}:/app mounts a volume at "current_directory/app"

# Notes on Startup of Application

Once the application is launched, you will get the following messages:

```
Executing the command: jupyter notebook
[I 22:11:41.725 NotebookApp] Writing notebook server cookie secret to /home/jovyan/.local/share/jupyter/runtime/notebook_cookie_secret
[I 2021-10-27 22:11:42.818 LabApp] JupyterLab extension loaded from /opt/conda/lib/python3.9/site-packages/jupyterlab
[I 2021-10-27 22:11:42.818 LabApp] JupyterLab application directory is /opt/conda/share/jupyter/lab
[I 22:11:42.827 NotebookApp] Serving notebooks from local directory: /home/jovyan
[I 22:11:42.827 NotebookApp] Jupyter Notebook 6.4.5 is running at:
[I 22:11:42.827 NotebookApp] http://{serverid}:8888/?token={tokenvariable1}
[I 22:11:42.827 NotebookApp]  or http://127.0.0.1:8888/?token={tokenvariable1}
[I 22:11:42.827 NotebookApp] Use Control-C to stop this server and shut down all kernels (twice to skip confirmation).
[C 22:11:42.834 NotebookApp] 
    
    To access the notebook, open this file in a browser:
        file:///home/jovyan/.local/share/jupyter/runtime/nbserver-8-open.html
    Or copy and paste one of these URLs:
        http://{serverid}:8888/?token={tokenvariable1}
     or http://127.0.0.1:8888/?token=f92f0e4fbd972c18aafe298ca95e529fea733daf74fe17b5

```


# Demo Deployment:



# Notes

Prodution build was not used on the Demo Deployment, only dev build.
