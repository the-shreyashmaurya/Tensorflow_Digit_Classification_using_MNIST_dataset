# MNIST Dataset Classification with TensorFlow

## Overview
This repository demonstrates how to train a neural network for digit classification using the MNIST dataset and TensorFlow. The MNIST dataset consists of 60,000 training images and 10,000 test images of handwritten digits (0-9), each represented as a 28x28 grayscale image. The model is built using TensorFlow and Keras, incorporating activation functions such as ReLU and Softmax for optimal performance.

## What is TensorFlow?
TensorFlow is an open-source machine learning framework developed by Google. It provides a flexible and efficient platform for building, training, and deploying deep learning models. With TensorFlow, users can define computational graphs, optimize models using automatic differentiation, and leverage GPU acceleration for faster training.

## What are Activation Functions?
Activation functions introduce non-linearity into neural networks, enabling them to learn complex patterns. Two key activation functions used in this project are:

### ReLU (Rectified Linear Unit)
ReLU is a widely used activation function defined as:

$$
f(x) = \max(0, x)
$$

This function allows positive inputs to pass through while setting negative inputs to zero. ReLU helps mitigate the vanishing gradient problem and improves model convergence.

### Softmax
Softmax is typically used in the output layer of a classification model. It converts raw logits into probabilities, ensuring that the sum of all output probabilities equals 1.Softmax helps in multi-class classification by assigning probabilities to different classes.

## Defining Layers in the Neural Network
The model in this repository is built using TensorFlow's Keras API. Below is an explanation of the key layers used:

1. **Flatten Layer**: Converts the 28x28 input images into a 1D array of 784 pixels.
2. **Dense (Fully Connected) Layers**:
   - First hidden layer with 128 neurons and ReLU activation.
   - Second hidden layer with 64 neurons and ReLU activation.
3. **Output Layer**:
   - Contains 10 neurons (one for each digit) and uses the Softmax activation function to output class probabilities.

### Example Code for Model Definition:
```python
import tensorflow as tf
from tensorflow import keras

# Load MNIST dataset
(x_train, y_train), (x_test, y_test) = keras.datasets.mnist.load_data()

# Normalize pixel values
x_train, x_test = x_train / 255.0, x_test / 255.0

# Define the model
model = keras.Sequential([
    keras.layers.Flatten(input_shape=(28, 28)),
    keras.layers.Dense(128, activation='relu'),
    keras.layers.Dense(64, activation='relu'),
    keras.layers.Dense(10, activation='softmax')
])

# Compile the model
model.compile(optimizer='adam',
              loss='sparse_categorical_crossentropy',
              metrics=['accuracy'])

# Train the model
model.fit(x_train, y_train, epochs=10, validation_data=(x_test, y_test))
```

## Installation & Usage
To run this project, ensure you have Python and TensorFlow installed.

### Install TensorFlow:
```sh
pip install tensorflow
```

### Clone this Repository:
```sh
git clone https://github.com/the-shreyashmaurya/Tensorflow_Digit_Classification_using_MNIST_dataset.git
cd Tensorflow_Digit_Classification_using_MNIST_dataset
```

### Run the Script:
```sh
jupyter notebook Digit_classification_using_MNIST_dataset.ipynb
```

## Results
After training the model, you can expect an accuracy of approximately **98%** on the test dataset. The trained model can recognize handwritten digits with high precision.

## Contributing
If you would like to contribute to this project, feel free to fork the repository and submit a pull request with your improvements.

## License
This project is open-source and available under the **MIT License**.
