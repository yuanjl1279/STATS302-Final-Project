# Flow Matching vs DDPM for 2D Vorticity Field Generation

This project implements and compares **Flow Matching (FM)** and **Diffusion Models (DDPM / DDIM sampling)** for generating 2D vorticity fields.

The goal is to provide a controlled and fair comparison between ODE-based generative modeling and diffusion-based generative modeling under equal computational budgets.

---

## Overview

Two generative paradigms are compared:

- **Flow Matching (FM)**
- **Diffusion Models (DDPM with DDIM sampling)**

Both models are trained on the same 2D vorticity dataset and evaluated under an **Equal-NFE (Number of Function Evaluations)** benchmark.

The comparison focuses on:

- Generation quality  
- Computational efficiency  
- Spectral fidelity  

---

## Notebook 1: Model Training

### 01_train_flowmatching_ddpm.ipynb

This notebook includes:

### Model Definitions
- Flow Matching model  
- Diffusion model  
- U-Net-style neural network backbone (separately parameterized)

### Training Procedure
- Supervised velocity field learning for Flow Matching  
- Noise prediction objective for Diffusion  
- Fixed random seeds for reproducibility  

### Sampling Methods
- FM with:
  - Euler solver  
  - RK4 solver  
- DDIM sampling for Diffusion  

### Training Diagnostics
- Loss curves  
- Generated sample visualization  
- Sanity checks  

This notebook produces trained models and intermediate outputs used for benchmarking.

---

## Notebook 2: Benchmark & Figures

### 02_visualization_and_benchmark.ipynb

This notebook focuses on evaluation and visualization.

It performs:

### Equal-NFE Benchmark

For a fixed number of function evaluations (NFE), the following methods are compared:

- FM (Euler)  
- FM (RK4)  
- DDIM  

This ensures fair computational comparison.

---

### Quantitative Metric

The primary evaluation metric is:

#### SpecErr  
Radial spectrum log-error measuring mismatch in Fourier spectral energy distribution.

---

### Publication-Style Figures

The notebook generates:

- NFE vs SpecErr curves  
- Method comparison plots  
- High-quality visualizations suitable for reports or research presentations  

---

## Experimental Setup

All experiments use:

- The same dataset  
- The same resolution  
- The same number of generated samples  
- Equal NFE constraint across methods  

This ensures fairness between:

- ODE-based Flow Matching solvers  
- Diffusion-based samplers  

---

## Methods Compared

| Method     | Solver Type       | Description                         |
|------------|------------------|-------------------------------------|
| FM-Euler   | First-order ODE  | Fast, lower computational cost      |
| FM-RK4     | Fourth-order ODE | Higher accuracy integration         |
| DDIM       | Diffusion-based  | Iterative denoising sampling method |

---

## Reproducibility

To reproduce the results:

1. Run `01_train_flowmatching_ddpm.ipynb`
   - Train models  
   - Generate samples  

2. Run `02_visualization_and_benchmark.ipynb`
   - Load results  
   - Generate benchmark plots  

Random seeds are fixed inside the notebooks to ensure consistent results.

---

## Requirements

The notebooks depend on:

- Python  
- PyTorch  
- NumPy  
- Matplotlib  

No additional external frameworks are required.

---

## Summary

This project demonstrates:

- A controlled comparison between Flow Matching and Diffusion models  
- Equal computational budget benchmarking  
- Spectral-level evaluation of generative performance  
- The impact of ODE solver order (Euler vs RK4)

The repository structure separates:

- Model training  
- Quantitative benchmarking  
- Figure generation  

This provides a clean and reproducible experimental pipeline.