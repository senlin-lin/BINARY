# BINARY Installation Guide

Follow these instructions to install BINARY, PySODB, and SOView in your Conda environment.

## 1. Extract BINARY installation package:

```bash
unzip BINARY.zip
cd BINARY/
```

## 2. Setup Conda Environment:

```bash
conda create -n binary python=3.8
conda activate binary
```

## 3. Install PyTorch with CUDA support:

Replace <torch_version> and <cuda_version> with the desired version.
```bash
pip install torch==<torch_version>+<cuda_version> -f https://download.pytorch.org/whl/<cuda_version>/torch_stable.html
```

Example:
```bash
pip install torch==1.13.0+cu117 -f https://download.pytorch.org/whl/cu117/torch_stable.html
```

## 4. Install PyTorch Geometric:

Visit the PyTorch Geometric Installation page(https://pytorch-geometric.readthedocs.io/en/latest/notes/installation.html) and then execute the copied command.

Example:
```bash
pip install pyg_lib torch_scatter torch_sparse torch_cluster torch_spline_conv torch_geometric -f https://data.pyg.org/whl/torch-1.13.0+cu117.html
```

## 5. Install additional Python packages:
```bash
pip install -r requirements.txt
```

##  6. Install mclust library:

```bash
conda install -c r rpy2
```

Then, set the R environment variables. Replace <user_name> and <environment_name> with appropriate values:

```bash
export R_HOME=/home/<user_name>/anaconda3/envs/<environment_name>/lib/R
export R_LIBS_USER=/home/<user_name>/anaconda3/envs/<environment_name>/lib/R/library
```
When configuring the installation paths for R_HOME and R_LIBS_USER, the standard Linux and Conda environment paths (such as .conda) may not be applicable. In such cases, users need to locate the R path and library path within the Conda virtual environment's Python packages and replace them accordingly.

Now, install the mclust library using Python:

```bash
python -c "import rpy2.robjects.packages as r; utils = r.importr('utils'); package_name = 'mclust'; utils.install_packages(package_name)"
```

##  7. Install PySODB:
Keep the binary conda environment active and execute:
```bash
git clone https://github.com/TencentAILabHealthcare/pysodb.git
cd pysodb/
python setup.py install
```

## 8. Install SOView:
```bash
git clone https://github.com/yuanzhiyuan/SOView.git
cd SOView/
pip install .
```

