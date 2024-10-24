## PSG(Problem-Solving Guide) : Predicting Algorithm Tags and Difficulty

[![arXiv](https://img.shields.io/badge/arXiv-2310.05791-b31b1b.svg)](https://arxiv.org/abs/2310.05791)

### Predicting the Algorithm Tags and Difficulty for Competitive Programming Problems

- This repository provides official PyTorch implementations for <b>Multi-Task PSG(Problem-Solving Guide)</b>.
- This work has been accepted to the [AAAI2024 Workshop on AI for Education](https://ai4ed.cc/workshops/aaai2024).

### Authors

- [Juntae Kim](https://github.com/sronger), [Eunjung Cho](https://github.com/EunJung516), [Dongbin Na](https://github.com/ndb796)

### Abstract

> The recent program development industries have required problem-solving abilities
> for engineers, especially application developers. However, AI-based education
> systems to help solve computer algorithm problems have not yet attracted attention,
> while most big tech companies require the ability to solve algorithm problems
> including Google, Meta, and Amazon. The most useful guide to solving algorithm
> problems might be guessing the category (tag) of the facing problems. Therefore,
> our study addresses the task of predicting the algorithm tag as a useful tool for
> engineers and developers. Moreover, we also consider predicting the difficulty
> levels of algorithm problems, which can be used as useful guidance to calculate the
> required time to solve that problem. In this paper, we present a real-world algorithm
> problem multi-task dataset, AMT, by mainly collecting problem samples from the
> most famous and large competitive programming website Codeforces. To the best
> of our knowledge, our proposed dataset is the most large-scale dataset for predicting
> algorithm tags compared to previous studies. Moreover, our work is the first to
> address predicting the difficulty levels of algorithm problems. In conclusion, we
> present a deep learning-based novel method for simultaneously predicting algorithm
> tags and the difficulty levels of an algorithm problem given.

### Model perfomance comparison

<img src="./resources/Model_perfomance_comparison.png" width="90%">

### Source Codes

- Our code can be run on Google Colab.
  - [Multi-Task PSG](https://colab.research.google.com/drive/1dhnU-EqRz4jI4acqUXavaYnO_oYNhct1?usp=sharing)
    - In the config, you can adjust the loss by tuning the lambda value.
  - [BigBird-based Single-Task Model](https://colab.research.google.com/drive/10Vfh_eBl6WfMA_fjQ_PcEqeIjWJbPCVB?usp=sharing)
    - In the config, you can choose 'tag' or 'rating' for the task.

### Model Weights

- You can check the model weights at the following address
  - https://drive.google.com/drive/folders/1-rCNt72t4uwvl0WdPCyqdiJ1-yKKrmjn?usp=sharing

### Preprocessing

- The **AMT dataset** has been processed using our preprocessing techniques.
- The technical details are as follows.
  - Substitute exponential notation.
    - 10^6 -> 1000000
  - Insert spaces between the dollar signs.
    - $$$n$$$ -> $$$ n $$$
  - Convert to lowercase.
    - This is an interactive task. -> this is an interactive task.
  - Calculate the expression. (optional)
    - 2 \cdot 100000 -> 200000
  - Remove stopwords using the nltk library.
  - Lemmatize using the nltk library.

### Datasets

- All data was collected from the [Codeforces website](https://codeforces.com/).

  - The tag distribution is as follows.

    - Top-5 Frequent Categories
      <img src="./resources/Top-5_Frequent_Categories.png" width="90%" height="120%">
    - Selected-10 Categories
      <img src="./resources/Selected-10_Categories.png" width="90%" height="110%" >

    - Top-20 Frequent Categories (except constructive algorithms and \*special)
      <img src="./resources/Top-20_Frequent_Categories.png" width="90%" >

  - The rating distribution is as follows.

    - Top-5 Frequent Categories Difficulty distribution
      <img src="./resources/Top-5_Frequent_Categories_Difficulty_distribution.png" width="90%" >
    - Selected-10 Categories Difficulty distribution
      <img src="./resources/Selected-10_Categories_Difficulty_distribution.png" width="90%" >
    - Top-20 Frequent Categories Difficulty distribution
      <img src="./resources/Top-20_Frequent_Categories_Difficulty_distribution.png" width="90%" >

### Classification Models Performance

| Architectures                              | λ   | Accuracy  | CS (θ=3)  | CS (θ=5)  | MAE      | AUROC     | F1-Macro |                                                                                                                            |
| ------------------------------------------ | --- | --------- | --------- | --------- | -------- | --------- | -------- | -------------------------------------------------------------------------------------------------------------------------- |
| BigBird-based Single-Task Model for Rating | N/A | **11.24** | **23.71** | **34.54** | **4.55** | N/A       | N/A      | ([code](https://colab.research.google.com/drive/10Vfh_eBl6WfMA_fjQ_PcEqeIjWJbPCVB?usp=sharing) \| [dataset](./data/AMT10)) |
| BigBird-based Single-Task Model for Tag    | N/A | N/A       | N/A       | N/A       | N/A      | **80.70** | 42.78    | ([code](https://colab.research.google.com/drive/10Vfh_eBl6WfMA_fjQ_PcEqeIjWJbPCVB?usp=sharing) \| [dataset](./data/AMT10)) |
| Multi-Task PSG                             | 1   | 8.35      | 19.07     | 32.68     | 4.74     | 69.08     | 25.16    | ([code](https://colab.research.google.com/drive/1dhnU-EqRz4jI4acqUXavaYnO_oYNhct1?usp=sharing) \| [dataset](./data/AMT10)) |
| Multi-Task PSG                             | 10  | 10.10     | 20.41     | 33.71     | 4.79     | 79.12     | 41.08    | ([code](https://colab.research.google.com/drive/1dhnU-EqRz4jI4acqUXavaYnO_oYNhct1?usp=sharing) \| [dataset](./data/AMT10)) |
| Multi-Task PSG                             | 100 | 8.76      | 15.46     | 23.20     | 7.09     | 79.59     | 41.63    | ([code](https://colab.research.google.com/drive/1dhnU-EqRz4jI4acqUXavaYnO_oYNhct1?usp=sharing) \| [dataset](./data/AMT10)) |

### Citation

If this work can be useful for your research, please cite our paper:

<pre>
@misc{kim2024problemsolvingguidepredictingalgorithm,
      title={Problem-Solving Guide: Predicting the Algorithm Tags and Difficulty for Competitive Programming Problems}, 
      author={Juntae Kim and Eunjung Cho and Dongbin Na},
      year={2024},
      eprint={2310.05791},
      archivePrefix={arXiv},
      primaryClass={cs.CL},
      url={https://arxiv.org/abs/2310.05791}, 
}
</pre>
