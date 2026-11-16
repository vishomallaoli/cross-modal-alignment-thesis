# Table 5.1. Alignment metrics

CKA is on raw features over all examples (z-scored in brackets). Procrustes is the relative residual on held-out examples after PCA to a common dimension. GW columns: optimised distance from an independent-coupling start, and cost of the identity (paired) coupling vs a random-permutation coupling.

| Comparison | Linear CKA | Procrustes residual | GW optimised | GW paired / shuffled cost |
| --- | --- | --- | --- | --- |
| ResNet-50 vs Mistral-7B, last layer (paired) | 0.312 (0.314) | 1.265 | 0.034 | 0.084 |
| ResNet-50 vs Mistral-7B, last layer (shuffled pairs) | 0.014 ± 0.000 (0.026 ± 0.000) | 1.930 | n/a | 0.082 |
| ResNet-50 vs Mistral-7B, middle layer (paired) | 0.336 (0.278) | 1.321 | 0.039 | 0.075 |
| ResNet-50 vs Mistral-7B, middle layer (shuffled pairs) | 0.017 ± 0.000 (0.025 ± 0.000) | 1.934 | n/a | 0.078 |
| ResNet-50 vs CLIP image encoder (same images) | 0.564 (shuffled 0.016 ± 0.000) | 0.957 | 0.046 | 0.064 |
| CLIP image vs CLIP text (jointly trained reference) | 0.473 (shuffled 0.012 ± 0.000) | n/a | n/a | n/a |
| Analytic isotropic-Gaussian null (Appendix A.5.5) | ResNet-Mistral 0.362; ResNet-CLIP 0.164 | n/a | n/a | n/a |

# Table 5.2. Image-to-caption retrieval

1000 candidate captions per query; mean ± std over anchor draws.

## Caption features: mistral_last

| Condition | Recall@1 | Recall@5 | Recall@10 |
| --- | --- | --- | --- |
| Chance | 0.1% | 0.5% | 1.0% |
| Zero-shot, PCA to common dimension | 0.1% | 0.3% | 0.9% |
| Zero-shot, truncate to common dimension | 0.1% | 0.6% | 1.4% |
| ridge map, k = 10 | 0.7% ± 0.1% | 3.2% ± 0.3% | 6.0% ± 0.3% |
| ridge map, k = 50 | 1.9% ± 0.2% | 8.1% ± 0.7% | 14.4% ± 0.7% |
| ridge map, k = 100 | 2.9% ± 0.4% | 12.6% ± 0.6% | 21.5% ± 0.3% |
| ridge map, k = 500 | 6.6% ± 0.3% | 22.4% ± 0.9% | 35.2% ± 0.6% |
| ridge map, k = 1000 | 8.3% ± 0.8% | 26.5% ± 0.5% | 41.2% ± 0.9% |
| ridge map, k = 4000 | 9.6% ± 0.0% | 29.2% ± 0.0% | 44.0% ± 0.0% |
| procrustes map, k = 10 | 0.7% ± 0.2% | 3.0% ± 0.3% | 5.2% ± 0.4% |
| procrustes map, k = 50 | 2.3% ± 0.2% | 10.0% ± 0.4% | 16.7% ± 0.7% |
| procrustes map, k = 100 | 3.7% ± 0.2% | 15.4% ± 0.8% | 26.0% ± 0.8% |
| procrustes map, k = 500 | 9.3% ± 0.7% | 29.1% ± 1.1% | 45.3% ± 1.1% |
| procrustes map, k = 1000 | 11.2% ± 0.4% | 33.6% ± 1.1% | 49.6% ± 0.7% |
| procrustes map, k = 4000 | 14.7% ± 0.0% | 38.2% ± 0.0% | 54.5% ± 0.0% |

## Caption features: mistral_mid

| Condition | Recall@1 | Recall@5 | Recall@10 |
| --- | --- | --- | --- |
| Chance | 0.1% | 0.5% | 1.0% |
| Zero-shot, PCA to common dimension | 0.1% | 0.6% | 1.3% |
| Zero-shot, truncate to common dimension | 0.2% | 1.3% | 1.8% |
| ridge map, k = 10 | 0.7% ± 0.3% | 2.7% ± 0.8% | 4.7% ± 1.0% |
| ridge map, k = 50 | 1.7% ± 0.2% | 7.8% ± 0.5% | 12.0% ± 1.1% |
| ridge map, k = 100 | 2.9% ± 0.7% | 11.4% ± 0.6% | 18.9% ± 1.2% |
| ridge map, k = 500 | 6.1% ± 0.5% | 20.1% ± 1.1% | 32.3% ± 1.3% |
| ridge map, k = 1000 | 5.7% ± 0.6% | 19.2% ± 0.8% | 30.8% ± 1.0% |
| ridge map, k = 4000 | 8.5% ± 0.0% | 27.0% ± 0.0% | 41.1% ± 0.0% |
| procrustes map, k = 10 | 0.7% ± 0.1% | 2.5% ± 0.3% | 4.9% ± 0.6% |
| procrustes map, k = 50 | 2.2% ± 0.2% | 8.8% ± 0.9% | 14.9% ± 1.0% |
| procrustes map, k = 100 | 3.4% ± 0.4% | 14.5% ± 0.8% | 23.2% ± 1.3% |
| procrustes map, k = 500 | 8.1% ± 0.9% | 26.0% ± 0.6% | 41.2% ± 0.6% |
| procrustes map, k = 1000 | 9.8% ± 0.5% | 30.5% ± 0.5% | 46.6% ± 0.8% |
| procrustes map, k = 4000 | 13.3% ± 0.0% | 36.2% ± 0.0% | 53.1% ± 0.0% |

CLIP jointly trained reference: R@1 52.1%, R@5 80.0%, R@10 88.9%
