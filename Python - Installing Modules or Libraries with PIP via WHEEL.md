
Here are some instructions for installing/upgrading a python package/library/module via python
this is compiled via notes pulled from the following url, and limited to just what is necessary to install:
  https://packaging.python.org/tutorials/installing-packages/

  https://packaging.python.org/tutorials/installing-packages/#ensure-you-can-run-pip-from-the-command-line
  ## check pip version
  ```python py -m pip --version```
  
  
  ## check if pip is installed
    ```python py -m ensurepip --default-pip```



  https://packaging.python.org/tutorials/installing-packages/#ensure-pip-setuptools-and-wheel-are-up-to-date
    ```python py -m pip install --upgrade pip setuptools wheel```


  https://packaging.python.org/tutorials/installing-packages/#optionally-create-a-virtual-environment
    ```python py -m venv this-is-your-environment-and-folder-name```
  
  ############
  ## EXAMPLE #
  ############
  
  ## venv notes
  ### how venv works:
  _just replace the <DIR> with the path name for your environment from that python's working directory_
    ```python
    py -m venv <DIR>
    <DIR>\Scripts\activate```
  
  ## 1. change to starting directory (so we don't work from the first directory/folder that command prompt opens in
    ```python cd my-python-directory-to-start-with```
  
  ## 2. create your python folder AND virtual-environment at same time with:
    ```python py -m venv my_python_project```
  
  
  ## USE _pip_ FOR INSTALLING
  https://packaging.python.org/tutorials/installing-packages/#installing-from-pypi
  pip is the recommended installer. Below, we’ll cover the most common usage scenarios.
  For more detail, see the pip docs, which includes a complete Reference Guide.
  pip:      https://packaging.python.org/key_projects/#pip
  pip-docs: https://pip.pypa.io/en/latest/
  
  ## INSTALLING FROM PyPI
  https://packaging.python.org/tutorials/installing-packages/#installing-from-pypi
  The most common usage of pip is to install from the Python Package Index using a requirement specifier.
  Generally speaking, a requirement specifier is composed of a project name followed by an optional version
    specifier.
  PEP 440 contains a full specification of the currently supported specifiers. Below are some examples.
  
  ### To install the latest version of “SomeProject”:
    ```python py -m pip install "SomeProject"

  ### To install a specific version:
    ```python py -m pip install "SomeProject==1.4"```


  ### To install greater than or equal to one version and less than another:
    ```python py -m pip install "SomeProject>=1,<2"```

  ### To install a version that’s “compatible” with a certain version: [4]
  ```python py -m pip install "SomeProject~=1.4.2"```
  In this case, this means to install any version “==1.4.*” version that’s also “>=1.4.2”.

  ## Source Distribution versus Wheels
  https://packaging.python.org/tutorials/installing-packages/#source-distributions-vs-wheels
  
  `pip` can install from either Source Distributions (sdist) or Wheels, but if both are present on PyPI,
    pip will prefer a compatible wheel.
  You can override pip`s default behavior by e.g. using its `–no-binary` option.
  `Wheels` are a pre-built distribution format that provides faster installation compared to Source 
    Distributions (sdist), especially when a project contains compiled extensions.
  If `pip` does not find a `wheel` to install, it will locally build a `wheel` and cache it for future 
    installs, instead of rebuilding the source distribution in the future.

  ## Installing to the User Site
  https://packaging.python.org/tutorials/installing-packages/#installing-to-the-user-site
  
  To install packages that are isolated to the current user, use the `--user` flag:
    ```python py -m pip install --user SomeProject```
  
  For more information see the User Installs section from the pip docs.

  Note that the --user flag has no effect when inside a virtual environment - all installation commands will affect the virtual environment.

  If SomeProject defines any command-line scripts or console entry points, `--user` will cause them to be installed inside the user base’s
    binary directory, which may or may not already be present in your shell’s PATH.
  (Starting in version 10, pip displays a warning when installing any scripts to a directory outside PATH.)
  If the scripts are not available in your shell after installation, you’ll need to add the directory to your PATH:
    •On Linux and macOS you can find the user base binary directory by running python -m site --user-base and adding bin to the end.
      For example, this will typically print `~/.local` (with ~ expanded to the absolute path to your home directory) so you’ll need
      to add `~/.local/bin` to your `PATH`. You can set your PATH permanently by modifying `~/.profile`.
    •On _**Windows**_ you can find the user base binary directory by running `py -m site --user-site` and replacing site-packages
      with Scripts.
      For example, this could return `C:\Users\Username\AppData\Roaming\Python36\site-packages` so you would need to set your `PATH`
      to include `C:\Users\Username\AppData\Roaming\Python36\Scripts`.
      You can set your user PATH permanently in the Control Panel.
      You may need to log out for the PATH changes to take effect.

