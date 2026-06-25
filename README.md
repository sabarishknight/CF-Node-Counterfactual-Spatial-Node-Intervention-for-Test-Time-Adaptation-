
# CF-NODE

## Counterfactual Lesion Node Editing for Test-Time Adaptation Under Domain Shift in Diabetic Retinopathy Grading

Official PyTorch implementation of **CF-NODE**, a Test-Time Adaptation (TTA) framework for improving domain robustness under domain shift in diabetic retinopathy grading through counterfactual lesion node editing.

> **IEEE Access (Under Review)**

<p align="center">
  <img width="241" height="355" alt="image" src="https://github.com/user-attachments/assets/3e8f4aa8-e361-48f7-b2d1-4eb3e513f4cc" />
</p>

---

## Overview

CF-NODE is a training-free Test-Time Adaptation framework that improves the robustness of diabetic retinopathy grading models under domain shift by identifying important lesion representations, generating counterfactual feature interventions, and refining predictions using ordinal reasoning and source prior correction.

---

## Repository Structure

```text
CF-NODE/

├── cfnode/
│   ├── cfnode.py
│   ├── config.py
│   └── __init__.py
│
├── model/
│   ├── model.py
│   ├── train.py
│   ├── config.py
│   └── README.md
│
├── figures/
│
├── README.md
├── requirements.txt
└── LICENSE
```

---

## Installation

```bash
git clone https://github.com/yourusername/CF-NODE.git

cd CF-NODE

pip install -r requirements.txt
```

---

## Train the Reference Model

The repository includes the DeepSet reference model used in our experiments.

```bash
python model/train.py
```

---

## Apply CF-NODE

CF-NODE expects the model to return

```python
(
    logits,
    node_features,
    ordinal_logits
)
```

Once the model follows this interface, CF-NODE can be integrated directly into the inference pipeline.

```python
from cfnode.cfnode import run_tta

predictions = run_tta(
    model,
    loader,
    cfg
)
```

---

## Reference Model

The `model/` directory contains the complete DeepSet reference implementation used in our experiments, including

- model architecture
- training configuration
- training script

The reference model can be used directly or adapted for other datasets.

---

## License

This project is released under the MIT License. See the `LICENSE` file for details.
