# Resnet Comparison
## Here we compare the changes in output observed for different resnet architecture and learning rate changes

# Dataset
## Source : Intel Image Classification Dataset(via Kaggle)
## Classes:
## Buildings
## Forest
## Glacier
## Mountain
## Sea
## Street
## Image Size: 128 x 128 x 3

# Model Architecture
## Custom Resnet-style CNN
## Residual blocks with skip connections
## Architecture highlights:
### Conv --> BatchNorm --> ReLU
### Residual Blocks(32 --> 64 --> 128 filters)
### MaxPooling for downsampling
### Global Average Pooling
### Dropout(0.3)
### Dense Softmax output (6 classes)

# Training Setup
## Optimizer : Adam
## Loss: Sparse Categorical Crossentropy
## Epochs : 20
## Batch Size: 32
## Train/Test split: 90 % / 10%

# Experiments
## We systematically evaluated the effect of :
## 1. Data Augmentation
## 2. Dropout
## 3. Learning Rate

# Results Summary
## Model Variant	Test Accuracy
## Full Model (baseline)	--> 75%
## Without Data Augmentation -->	58% 
## Without Dropout	--> 79% 
## Learning Rate = 1e-4	--> 76%

# Key Observations
## Data Augmentation
### Strong impact on generalization
### Without augmentation --> severe overfitting

## Dropout
### Removing dropout improved performance 
### Indicates:
### Model capacity was not too high
### BatchNorm already providing regularization

## Learning Rate
### Lower LR (1e-4) --> more stable but slower convergence compared to 1e-3
### Slightly lower final accuracy than default Adam

# Confusion Matrix Insights
## Mountain Class --> hardest to classify(low recall)
## Confusion between:
### Glacier  <-->  Mountain
### Buildings <--> Street 
## High performance:
### Forest(very high precision)
### Sea(high recall)

# Evaluation Metrics
## Example (Baseline Model):
## Accuracy: 75%
## Macro Avg F1: 0.74
## Weighted Avg F1: 0.74

# How to Run

## Install dependencies
### pip install tensorflow matplotlib scikit-learn kaggle
## Download dataset via Kaggle API
### kaggle datasets download -d puneet6060/intel-image-classification
### unzip intel-image-classification.zip

### Then run the training script

# Future Improvements
## Use pretrained models(Resnet50, EfficientNet)
## Add learning rate scheduler
## Use MixUp/ CutMix augmentation
## Hyperparameter tuning
## Class imbalance handling

# Conclusion
## Data augmentation
## Dropout was not necessary in this setup
## Residual connections helped stable training
## Model achieves solid performance with relatively simple design

# Contributions
## contributions and pull up requests are welcome



