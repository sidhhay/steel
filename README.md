# Tata Steel Surface Crack Detection

An AI-assisted steel-surface inspection project that uses a **Convolutional Neural Network (CNN)** to classify steel-surface images as **Crack Detected** or **No Crack Detected**. The project includes a Streamlit dashboard for image upload and camera capture, confidence visualization, Grad-CAM explainability, and CSV export of batch predictions.

## Features

- **CNN-based classification** of steel surface images.
- **Upload mode** for one or more JPG, JPEG or PNG images.
- **Camera mode** to capture an image using a webcam.
- **Confidence display** and crack/no-crack probability visualization.
- **Grad-CAM heatmap** overlay to show image regions influencing the model's prediction.
- **CSV export** of predictions for uploaded image batches.
- **Streamlit dashboard** with model information and performance summary.

## Repository contents

| File / folder | Purpose |
|---|---|
| `Tata steel Crack Prediction.ipynb` | Jupyter Notebook for the crack-prediction work |
| `streamlit_app.py` | Streamlit application and inference dashboard |
| `cnn_crack_model_final.h5` | Saved CNN model weights used by the dashboard |
| `requirements.txt` | Python dependencies |
| `sample_images/` | Sample steel-surface images |

## Model and image processing

The Streamlit application rebuilds a CNN with an input size of **128 × 128 × 3**, convolution and max-pooling layers, batch normalization, a dense layer, dropout and a sigmoid output. It loads the trained weights from `cnn_crack_model_final.h5`.

Uploaded images are converted to RGB, resized to 128 × 128 and normalized to the 0–1 range before prediction. A sigmoid score above 0.5 is labelled **Crack Detected**; otherwise it is labelled **No Crack Detected**.

Grad-CAM is used to produce a heatmap overlay that helps visualize the regions influencing the model's prediction.

## Setup

### 1. Clone the repository

```bash
git clone https://github.com/sidhhay/tatasteel.git
cd tatasteel
```

### 2. Create and activate a virtual environment (recommended)

**Windows PowerShell**
```powershell
python -m venv venv
.\venv\Scripts\Activate.ps1
```

**macOS / Linux**
```bash
python3 -m venv venv
source venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Run the dashboard

```bash
streamlit run streamlit_app.py
```

Streamlit will print a local URL in the terminal. Open that URL in your browser.

## Using the dashboard

1. Start the Streamlit application.
2. Choose **Upload Images** to submit one or more steel-surface images, or choose **Live Camera Feed** to capture an image.
3. Review the predicted class and confidence.
4. Inspect the Grad-CAM overlay for the model's highlighted image regions.
5. In upload mode, download the prediction results as a CSV file.

## Requirements

The project dependencies are listed in `requirements.txt`, including Streamlit, TensorFlow, NumPy, Pandas, OpenCV, Pillow and Matplotlib.

The dashboard expects `cnn_crack_model_final.h5` in the repository root. Ensure the model weights are present before starting the app.

## Important notes

- The accuracy values displayed in the dashboard are values written into the application UI; they should not be interpreted as independently reproduced evaluation results without reviewing the training and evaluation procedure.
- Grad-CAM generation is wrapped in error handling. If it cannot be generated for the loaded model, the dashboard displays the original resized image instead.
- This is a project/demo inspection aid. Predictions should be validated by qualified inspection processes before being used for industrial quality or safety decisions.

## Tech stack

- Python
- TensorFlow / Keras
- Convolutional Neural Network (CNN)
- Streamlit
- OpenCV
- NumPy and Pandas
- Pillow and Matplotlib
- Grad-CAM

---

**Project:** Tata Steel Surface Crack Detection  
**Repository:** [sidhhay/tatasteel](https://github.com/sidhhay/tatasteel)
