# Identifying-and-Mitigating-Spurious-Correlations-for-Improving-Robustness-in-NLP-Models
NAACL 2022 Findings

Tianlu Wang, Rohit Sridhar, Diyi Yang, Xuezhi Wang

## Abstract

Recently, NLP models have achieved remarkable progress across a variety of tasks; however, they have also been criticized for being not robust. Many robustness problems can be attributed to models exploiting "spurious correlations", or "shortcuts" between the training data and the task labels. Most existing work identifies a limited set of task-specific shortcuts via human priors or error analyses, which requires extensive expertise and efforts. In this paper, we aim to automatically identify such spurious correlations in NLP models at scale. We first leverage existing interpretability methods to extract tokens that significantly affect model's decision process from the input text. We then distinguish "genuine" tokens and "spurious" tokens by analyzing model predictions across multiple corpora and further verify them through knowledge-aware perturbations. We show that our proposed method can effectively and efficiently identify a scalable set of ``shortcuts'',  and mitigating these leads to more robust models in multiple applications.

## Requirements:
- Pytorch
- Transformers = 3.2.0 (whatever versions should be fine if you finetune your own models)
- Python 2/3

## Data
We used publicly avaible [SST-2](https://huggingface.co/datasets/glue/viewer/sst2/test), [yelp](https://www.yelp.com/dataset) and [Amazon review](https://jmcauley.ucsd.edu/data/amazon/) datasets. The paper only tackles sentiment classification tasks but the proposed method can be potentially applied on general text classification tasks (datasets).

## Model training:
1. Please follow the [transformer](https://github.com/huggingface/transformers) repository to finetune your model. Replace the trainer.py and run_glue.py in transformers repository with the trainer.py and run_attention.py provided in this repo, install transformers by running ```pip install -e .``` run_attention.py will save all predictions and attentions score.
2. Feel free to explore other methods to extract important tokens. To test the proposed method, you only need the model predictions and the "importantce scores".
3. To find synonyms, we use the counter-fitting word embeddings as shown in [Textfooler](https://github.com/jind11/TextFooler) as well as WordNet.

## Citing
If you find our paper/code useful, please consider citing:
```
@misc{https://doi.org/10.48550/arxiv.2110.07736,
  doi = {10.48550/ARXIV.2110.07736},
  
  url = {https://arxiv.org/abs/2110.07736},
  
  author = {Wang, Tianlu and Yang, Diyi and Wang, Xuezhi},
  
  keywords = {Computation and Language (cs.CL), FOS: Computer and information sciences, FOS: Computer and information sciences},
  
  title = {Identifying and Mitigating Spurious Correlations for Improving Robustness in NLP Models},
```
