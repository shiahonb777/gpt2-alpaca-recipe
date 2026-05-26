# gpt2-alpaca-recipe

A GPT-2 Alpaca LoRA fine-tune, distributed as an
[`mlrecipe`](https://github.com/shiahonb777/mlrecipe).

The fine-tune itself was trained by
[monsterapi](https://huggingface.co/monsterapi/gpt2_alpaca-lora). This
repo doesn't host the weights — it hosts a 1.1 MB recipe that re-derives
them locally.

## Use it

```bash
pip install git+https://github.com/shiahonb777/mlrecipe.git

mlrecipe clone shiahonb777/gpt2-alpaca-recipe@v1
cd gpt2-alpaca-recipe
mlrecipe materialize ./merged
```

This downloads:
- this 1.1 MB recipe
- the `gpt2` base from HF Hub (~500 MB; cached locally for next time)
- and reconstructs the merged checkpoint in `./merged/`

Total network transfer for the *fine-tune part*: **1.1 MB**.

## Verify

The merged result is bit-identical to PEFT's `merge_and_unload`:

```bash
git clone https://github.com/shiahonb777/mlrecipe
cd mlrecipe
python examples/gpt2_alpaca/verify.py
```

```
148/148 tensors match within 1e-4 tolerance
max absolute difference across all tensors: 0.000000e+00
```
