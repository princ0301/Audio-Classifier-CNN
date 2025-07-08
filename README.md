# Audio-Classifier-CNN

**Audio-Classifier-CNN** is a project that leverages a deep Convolutional Neural Network (CNN) to classify audio clips, specifically using the [ESC-50 dataset](https://github.com/karolpiczak/ESC-50). The project supports both training and inference, and includes a web-based visualization tool for exploring model predictions and feature maps.

## Features

- **CNN-based Audio Classification**: Implements a deep residual CNN (`AudioCNN`) for robust audio recognition.
- **ESC-50 Dataset Support**: Designed for environmental sound classification with 50 classes.
- **Training Pipeline**: Modular code for training on GPUs using PyTorch and torchaudio.
- **Model Accuracy**: Achieves an accuracy of 83% on the ESC-50 dataset.
- **Inference API**: RESTful API endpoint for making predictions on uploaded WAV files.
- **Visualization App**: Web frontend (T3 Stack + Next.js) for uploading audio, visualizing predictions, and inspecting neural network feature maps.

## Project Structure

```
.
├── main.py                      # Inference API and entrypoint
├── model.py                     # CNN model and blocks
├── train.py                     # Training script (ESC-50)
├── requirements.txt             # Python dependencies
├── audio-cnn-visualization/     # Web frontend (T3 Stack & Next.js)
│   └── 
└── ...
```

## Getting Started

### Prerequisites

- Python 3.8+
- PyTorch, torchaudio, librosa, modal, soundfile
- Node.js (for frontend)
- GPU recommended for training

### Install Python Dependencies

```bash
pip install -r requirements.txt
```

### Training

The training script downloads the ESC-50 dataset and trains the CNN:

```bash
python train.py
```

Model checkpoints are saved in `/models`.

### Running Inference

Launch the inference API (using Modal or locally):

```bash
python main.py
```

You can send a POST request to the API or use the provided web frontend.

### Frontend Visualization

See `audio-cnn-visualization/README.md` for details. In short:

```bash
cd audio-cnn-visualization
npm install
npm run dev
```

Then visit `http://localhost:3000` and upload a WAV file for classification and visualization.

## Model

The core model is a deep CNN with multiple residual blocks, trained to recognize 50 environmental sound classes. Audio is processed into Mel-spectrograms before being fed into the network.

**Performance**:  
- Accuracy on ESC-50: **83%**
