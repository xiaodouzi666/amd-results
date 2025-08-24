# amd-results

modified vllm repo: https://github.com/xiaodouzi666/vllm

# How to run

cd /vllm-dev
pip uninstall -y vllm || true
pip install -e .

export VLLM_NUM_LOOKAHEAD_SLOTS=12

# Model side
export VLLM_MAX_SEQ_LEN_TO_CAPTURE=16384

# Scheduling side
export VLLM_CUDA_GRAPH_SIZES=4096,8192

pkill -f "vllm serve" || true
./1_bench.sh server

# Testing
./1_bench.sh perf
