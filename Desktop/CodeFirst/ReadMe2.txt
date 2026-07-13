‎Title – A Novel Lightweight 3-Level 50-Layer Hierarchical Model-Based Crop Pest Identification System for Smart Farming.
====================

‎Description – The plant disease dataset used in this study is a publicly available image dataset designed for developing and evaluating deep learning models for plant disease detection and classification. It contains images of healthy and diseased plant leaves collected under real-world conditions, making it suitable for computer vision applications such as image classification and object detection.

The PlantDoc dataset, developed by researchers from the Indian Institute of Technology (IIT) and later made publicly available by Pratik Kayal, contains 2,569 images representing 13 plant species. The images are categorized into 30 classes, where each class corresponds to a specific plant species and its health condition (healthy or diseased). The dataset includes 8,851 annotated objects, making it useful for both image classification and object detection tasks. Unlike laboratory datasets, PlantDoc images were captured in natural environments with varying lighting conditions, backgrounds, and leaf orientations, providing a realistic benchmark for disease detection models.

In addition, the Crop Pest and Disease Dataset from Mendeley Data contains images collected from local farms in Ghana. The dataset includes 24,881 original images of four major crops—Cashew, Cassava, Maize, and Tomato—covering 22 disease and pest classes. An augmented version expands the dataset to 102,976 images, which are divided into training and testing sets. All images were validated by expert plant virologists, ensuring high-quality annotations suitable for machine learning research.

Together, these datasets provide a diverse collection of healthy and diseased plant images captured under different environmental conditions. Their diversity in crop species, disease categories, and image characteristics makes them valuable resources for training, validating, and benchmarking artificial intelligence models for automated plant disease diagnosis in precision agriculture.
====================

‎Dataset Information.
Dataset Name: Plant Disease Detection Dataset (PlantDoc)
Source: Publicly available on Kaggle; originally developed by researchers at the Indian Institute of Technology (IIT) and shared by Pratik Kayal on GitHub.
Total Images: 2,569
Plant Species: 13
Number of Classes: 30 (healthy and diseased categories)
Annotated Objects: 8,851
Image Type: RGB images of plant leaves captured under real-field conditions
Applications: Plant disease classification, object detection, and deep learning-based disease recognition.
====================

‎Code Information.
The proposed model is implemented using Python and the TensorFlow–Keras deep learning framework to perform multi-class plant disease classification. Images are loaded from the dataset directory using the ImageDataGenerator class, which performs preprocessing and data augmentation. The input images are resized to 224 × 224 pixels, normalized by scaling pixel values to the range [0, 1], and augmented through shearing, zooming, and horizontal flipping to improve model generalization. The dataset is automatically divided into 80% training and 20% validation using the validation_split parameter. Images are processed in batches of 32, and labels are encoded using one-hot (categorical) encoding for six output classes.

The proposed architecture is a custom U-Net-inspired classification network that combines dilated convolutions, attention mechanisms, depthwise separable convolutions, and dense feature connections. The encoder extracts hierarchical features using dilated convolution blocks followed by attention modules and max-pooling operations. The bottleneck consists of Depthwise Separable Dense Blocks and Dense Dilated Blocks, enabling efficient feature extraction while reducing computational complexity. The decoder reconstructs high-level feature representations through up-sampling and skip connections from the encoder, preserving important spatial information.

Instead of generating a segmentation map, the decoder output is passed through a Global Average Pooling (GAP) layer followed by a Softmax classification layer to predict the probability of each disease class. The model is compiled using the Adam optimizer with the categorical cross-entropy loss function and classification accuracy as the evaluation metric. Training is performed for 10 epochs, after which the trained model is saved in the .keras format (edge_model1.keras). Finally, the model is evaluated on the validation dataset to measure its classification accuracy.
====================

‎Usage Instructions.
Download the Plant Disease Detection Dataset and extract it into the project directory.
Organize the dataset in the following directory structure:
Dataset2/
└── training/
    ├── Class_1/
    ├── Class_2/
    ├── Class_3/
    ├── Class_4/
    ├── Class_5/
    └── Class_6/

Each class folder should contain the corresponding plant leaf images.

Install the required Python libraries:
pip install tensorflow numpy matplotlib pillow
Update the dataset path in the code if necessary:
train_dir = './Dataset2/training'
Run the Python script. The code automatically:
Loads the images from the dataset.
Resizes images to 224 × 224 pixels.
Normalizes pixel values.
Applies data augmentation (shear, zoom, and horizontal flip).
Splits the dataset into 80% training and 20% validation.
Trains the proposed deep learning model for 10 epochs.
After training, the model is automatically saved as:
edge_model1.keras
The trained model is evaluated on the validation dataset, and the final validation accuracy is displayed.

Input: RGB plant leaf images of size 224 × 224 × 3.
Output: Predicted plant disease class (one of the six predefined classes) along with its classification probability using the Softmax layer.
====================

‎Requirements –  dependencies.
TensorFlow 2.x – Deep learning framework for building and training the model.
Keras (included with TensorFlow) – High-level API for model development.
NumPy – Numerical computations and array operations.
Matplotlib – Visualization of training and validation performance (optional).
Pillow (PIL) – Image processing and loading.

====================
‎Methodology – Steps taken for data processing or modeling.
Dataset Collection:
Plant leaf images are collected from the Plant Disease Detection dataset and organized into separate folders based on their disease classes.
Data Preprocessing:
Images are resized to 224 × 224 pixels.
Pixel values are normalized to the range [0, 1].
Data augmentation techniques, including shearing, zooming, and horizontal flipping, are applied to improve model generalization.
The dataset is split into 80% training and 20% validation.
Feature Extraction:
The input images are processed through a custom U-Net-inspired encoder, which employs:
Dilated convolution blocks for capturing multi-scale contextual information.
Attention convolution blocks to emphasize important feature channels.
Batch normalization to improve training stability.
Bottleneck Processing:
Deep feature representations are learned using:
Depthwise Separable Dense Blocks for computational efficiency.
Dense Dilated Blocks to enhance feature reuse and expand the receptive field.
Feature Reconstruction:
A decoder with up-sampling and skip connections combines high-level and low-level features, preserving important spatial information extracted during encoding.
Classification:
The decoder output is passed through a Global Average Pooling (GAP) layer followed by a Softmax layer to classify each image into one of the six plant disease classes.
Model Training:
The model is trained using the Adam optimizer with the categorical cross-entropy loss function for 10 epochs, while classification accuracy is used as the evaluation metric.
Model Evaluation and Saving:
After training, the model is evaluated on the validation dataset to determine its performance, and the trained model is saved as edge_model1.keras for future inference and deployment

====================
‎Citations  – dataset was used in research, provide references.
1. PlantDoc Dataset

Singh, D., Jain, N., Jain, P., Kayal, P., Kumawat, S., & Batra, N. (2020). PlantDoc: A Dataset for Visual Plant Disease Detection. Proceedings of the 7th ACM IKDD CoDS and 25th COMAD. https://doi.org/10.1145/3371158.3371196

Kayal, P. PlantDoc Dataset (GitHub Repository). Available at: https://github.com/pratikkayal/PlantDoc-Dataset

Kaggle Dataset: Plant Diseases Detection Dataset. Available at: https://www.kaggle.com/datasets/kamipakistan/plant-diseases-detection-dataset

2. Crop Pest and Disease Dataset (Mendeley Data)

Abdulai, A.-R., Nyarko-Boateng, O., & Osae, E. A. (2022). Crop Pests and Disease Detection Dataset. Mendeley Data, Version 1. https://doi.org/10.17632/bwh3zbpkpv.1

Dataset available at: https://data.mendeley.com/datasets/bwh3zbpkpv/1

These are the recommended references to include in the bibliography or references section of your research paper or project report.
====================

License
The PlantDoc Dataset is publicly available for research and educational purposes. Users should comply with the license and terms of use provided by the original authors and the hosting platforms (GitHub and Kaggle).
The Crop Pest and Disease Dataset is publicly available through Mendeley Data. Users should follow the dataset license and provide appropriate citation when using the dataset in research or publications.
Any redistribution or commercial use should adhere to the respective dataset licenses and attribution requirements specified by the original publishers.
Contribution Guidelines

Researchers and developers who wish to extend or improve this work are encouraged to:

Contribute additional plant species or disease classes to improve dataset diversity.
Add more annotated images collected under different environmental conditions.
Improve image quality, labeling accuracy, and metadata.
Enhance the proposed deep learning model by experimenting with alternative architectures, hyperparameter tuning, or optimization techniques.
Report issues, suggest improvements, or submit enhancements through the respective dataset repositories (GitHub or Mendeley Data), where applicable.
When publishing research based on these datasets, provide proper citations to acknowledge the original dataset creators.
====================