# Pegasus Llama
# install
```
module purge
curl -sSf https://rye.astral.sh/get | bash

Details:
  Rye Version: 0.39.0
  Platform: linux (x86_64)

✔ Continue? · yes
✔ Select the preferred package installer · pip-tools (slow, higher compatibility)
✔ What should running `python` or `python3` do when you are not inside a Rye managed project? · Run a Python installed and managed by Rye
✔ Which version of Python should be used as default toolchain? · cpython@3.12

source "$HOME/.rye/env"
rye init
source .venv/bin/activate

module load openmpi/4.1.6/gcc11.4.0-cuda12.3.2
module load cudnn/9.0.0/cuda12

rye add transformers
rye add torch
rye sync
```

# test
```
qlogin -q interactive_ccs -A NBB -T openmpi -v NQSV_MPI_VER=4.1.6/gcc11.4.0-cuda12.3.2 -b 1
cd /path/to/pegasusllama
module purge
module load "openmpi/$NQSV_MPI_VER"
module load cudnn/9.0.0/cuda12

source "$HOME/.rye/env"
source .venv/bin/activate
check-cuda
CUDA is available!
Number of GPUs: 1
Current GPU: NVIDIA H100 PCIe
```
