# Skin Lesion Classification Using Deep Learning

**Author:** Sameer Shaik  
**Challenge:** [ISIC 2017 Skin Lesion Analysis](https://challenge.isic-archive.com/landing/2017/44/)

---

## 🧠 Overview

This project tackles binary classification of dermoscopic skin lesion images using deep learning techniques. It is part of the ISIC 2017 Challenge (Task 3: Lesion Classification), where the goal is to distinguish malignant lesions (melanoma) from benign types (nevus and seborrheic keratosis).

---

## 📁 Dataset

The dataset includes **2,000 dermoscopic images**, labeled as:

- **Melanoma:** 374 images  
- **Seborrheic Keratosis:** 254 images  
- **Nevus (Benign):** 1,372 images

For the binary classification task:

- **Class 1 (Malignant):** Melanoma  
- **Class 0 (Benign):** Nevus + Seborrheic Keratosis  

This creates a **highly imbalanced dataset** (1626 benign vs. 374 malignant).

---

## 🛠 Methodology

### ✅ Pretrained Models

- **DenseNet121**
- **ResNet50**

Both models were initialized with ImageNet pretrained weights to leverage general visual features like edges and textures.

### 🧪 Data Augmentation

To improve generalization, the following image transformations were applied:

- Resize to 256x256
- Random crop to 224x224
- Horizontal and vertical flips
- Random rotation and color jitter
- Image normalization

These techniques ensure the model sees varied forms of input during training, reducing overfitting.

### ⚖️ Handling Class Imbalance

Class weights were applied in the loss function to compensate for the skewed class distribution, helping the model focus more on correctly identifying malignant cases.

### 🔄 Learning Rate Scheduler

A `StepLR` scheduler was used to:

- Start with a higher learning rate
- Gradually reduce it every few epochs to stabilize learning

---

## 📊 Results

### 🔹 Image-Only Models (With Class Weights + LR Scheduler)

| Model       | F1 Score | Recall | Specificity |
|-------------|----------|--------|-------------|
| DenseNet121 | 0.5149   | 0.6933 | 0.7692      |
| ResNet50    | 0.5070   | 0.7200 | 0.7415      |

> Using class weights and a scheduler significantly improved performance, especially recall on the malignant class.

---

### 🔹 Models with Dermatological Features (Binary Inputs)

| Model       | Recall  | Specificity |
|-------------|---------|-------------|
| ResNet50    | 0.4267  | 0.8615      |
| DenseNet121 | 0.6533  | 0.5477      |

> Including dermatological features had a mixed impact. Although they added information, they sometimes disrupted learned image features and require better fusion strategies.

---

## ✅ Conclusion

The combination of:
- **Pretrained CNNs**
- **Data augmentation**
- **Class weighting**
- **Learning rate scheduling**

…proved effective for this medical classification task.

Future work may involve:
- Better integration of tabular features
- Feature selection or dimensionality reduction
- Exploring more advanced fusion architectures (e.g., attention-based)

---

## 🔗 Reference

[ISIC 2017 Challenge - Task 3](https://challenge.isic-archive.com/landing/2017/44/)


