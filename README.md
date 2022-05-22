# Federated-Learning-Introduction
This is a introduction repository that helps you hands on Federated Learning.

# 1. Introduction

* FL is a distributed machine learning framework.
* FL Collaboratively learns a model without sharing any raw data over the network to protect the security and privacy of data on each device.
* [Federated Learning – A Beginners Guide](https://www.analyticsvidhya.com/blog/2021/05/federated-learning-a-beginners-guide/)

# 2. FL Types

## 2.1 Model-Centric  FL

* Data distributed in the locally clients (each client cannot read the data of other clients, data is neither distributed independently nor identical) is used to improve a central model (e.g. Google uses [FederatedSGD and averaging](https://inst.eecs.berkeley.edu/~cs294-163/fa19/slides/federated-learning.pdf) to achieve this).

### 2.1.1 Horizontal FL (sample-based FL)

* FL on horizontal data. **Horizontal data** shares the same feature space but different in sample. e.g. BMW provides similar selling services (same feature space) to different users (different samples)

* Training process:
  * 1). each client download the model from the central sever
  * 2). each client train the model locally and then send the trained gradients to the central sever in an encrypted approach
  * 3). the central sever aggregates all the gradients received from the clients
  * 4). the central sever update the model
  * 5). repeat 1).

  ![img](https://miro.medium.com/max/1400/0*O-8W-wIPKnOS1O2B.png)

  https://medium.com/disassembly/architecture-of-federated-learning-a36905c1d225

* each client has the same model as the central sever, the clients do not communicate with each other in the training process


### 2.1.2 Vertical FL (feature-based FL)

* Vertical FL is applied on two datasets that share the same sample space whereas differ in feature space. e.g. In the same city, a bank and a supermarket provide two datasets respectively. The two datasets are created on a same group of citizens (same sample space) but differ in their own usages (different feature space).

**Training Process**:

* Stage 1: Encrypted entity alignment
  
* stage 2: Encrypted model training
  
  * 1). Collaborator C sends public keys to corp. A and corp. B for encrypting their own data
  * 2). A and B compute and exchange their own intermediate results in an encrypted way
  * 3). A and B compute their own gradients and loss, encrypt, mask and send to C 
  * 4). C decrypts the gradients and loss, and then aggregates them
  * 5). C sends the aggregated results back to A and B; A and B update their own model
  
  ![Architecture for a vertical federated learning system](https://www.researchgate.net/profile/Tianjian-Chen-3/publication/331086697/figure/fig3/AS:726048543084544@1550114870226/Architecture-for-a-vertical-federated-learning-system.ppm)
  
  https://www.researchgate.net/figure/Architecture-for-a-vertical-federated-learning-system_fig3_331086697

### 2.1.3 Federated Transfer Learning (FTL)

* FTL is applied on a situation when the datasets from different corporations barely share the sample space nor feature space. e.g. A bank in city A corporates with a insurance company in city B. The two companies build their own datasets for their own usages and they collect their own data on two different groups of citizens. 

## 2.2 Data-Centric FL

* The data owner can provide access without sharing the data for others to build models.
* The data owner only wants to protect their data rather than models built upon the data.

![img](https://cdn-images-1.medium.com/max/1600/1*yTG72Uj7crgvwVZL4fMecg.png)

https://blog.openmined.org/federated-learning-types/

## 2.3 Other FL Concepts

* **Cross-Silo FL **-- data is widely distributed on different corporations for example, insurance companies, supermarket, banks etc.
* **Cross-Device FL** -- learning models on remote devices for example smart phones, personal PCs, APPs etc. , and updating a central model. 

# 3. Important Paper Summary

## 3.1 FL Pioneer -- Google's three paper

* [Communication-Efficient Learning of Deep Networks from Decentralized Data](https://www.arxiv-vanity.com/papers/1602.05629/): the paper firstly introduces the term Federated Learning and shows how FL is implemented through two techniques -- Federated Averaging and Federated SGD
* [Federated Optimization: Distributed Machine Learning for On-Device Intelligence](https://www.arxiv-vanity.com/papers/1610.02527/) (**Model Centric FL**): the author invented **Federated Optimization** to solve distributed optimization problem in machine learning in which data are unevenly distributed 
* [Federated Learning: Strategies for Improving Communication Efficiency](https://www.arxiv-vanity.com/papers/1610.05492/): the paper improves the communication efficiency between clients and central sever

## 3.2 FL Overview

* [Federated Machine Learning: Concept and Applications](https://www.arxiv-vanity.com/papers/1902.04885/): the authors come up with the concept of **Secure FL** framework which includes horizontal FL, vertical FL and federated transfer learning
* [Federated Learning: Challenges, Methods, and Future Directions](https://arxiv.org/pdf/1908.07873.pdf): overview
* [Advances and Open Problems in Federated Learning](https://www.nowpublishers.com/article/Details/MAL-083): summary

## 3.3 FL Specifics

* [Federated Learning with Non-IID Data](https://arxiv.org/abs/1806.00582): the paper shows how Non-IID data distributed on client device used for Federated training significantly decreases the accuracy of prediction, and indicates that a small globally shared dataset on all the devices recover the accuracy
* [Federated Learning for Open Banking](https://arxiv.org/pdf/2108.10749.pdf)
* [A Secure Federated Transfer Learning Framework](https://arxiv.org/pdf/1812.03337.pdf): FTL allows knowledge to be shared without compromising user privacy, and thereby enables a target-domain party to build flexible and effective models by leveraging rich labels from a source domain

# 4. FL Tools and Libs

* [FedML](https://github.com/FedML-AI/FedML)
* [FATE: Federated AI Technology Enabler](https://github.com/FederatedAI/FATE)
