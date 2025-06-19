# 🚦 YOLOv8-Based Traffic Detection using Aerial Imagery

This project uses the YOLOv8 deep learning model to perform real-time traffic and vehicle detection on aerial images from the VisDrone dataset. The workflow includes preprocessing, model training, performance evaluation, and visual result generation, making it suitable for intelligent transportation systems research.

## 📂 Dataset

- **Dataset:** [VisDrone2019-DET](https://github.com/VisDrone/VisDrone-Dataset)
- **Structure:**
  - `VisDrone2019-DET-train/`
  - `VisDrone2019-DET-val/`
  - `VisDrone2019-DET-test-dev/`
- Each folder contains `images/` and corresponding `annotations/`.

## 🧠 Model

- **Model used:** YOLOv8n (`ultralytics` library)
- **Transfer Learning:** Pretrained YOLOv8 weights fine-tuned on VisDrone data.
- **Classes Detected:** pedestrian, person, car, van, bus, truck, motor, bicycle, awning-tricycle, tricycle

## 🚀 Setup Instructions

1. Clone the repository and install dependencies:
    ```bash
    git clone https://github.com/your-username/YOLOv8-Traffic-Detection.git
    cd YOLOv8-Traffic-Detection
    pip install -r requirements.txt
    ```

2. Organize the dataset and create a `data.yaml` file:
    ```yaml
    train: path/to/train/images
    val: path/to/val/images
    test: path/to/test/images

    nc: 10
    names: ["pedestrian", "person", "car", "van", "bus", "truck", "motor", "bicycle", "awning-tricycle", "tricycle"]
    ```

3. Train the model:
    ```python
    from ultralytics import YOLO
    model = YOLO("yolov8n.pt")
    model.train(data="path/to/data.yaml", epochs=10, imgsz=640, batch=8)
    ```

4. Run evaluation:
    ```python
    model.val(data="path/to/data.yaml", split='test')
    ```

5. Inference:
    ```python
    model.predict(source="path/to/test/images", save=True)
    ```

## 📊 Evaluation

- **Metrics:** mAP@50, mAP@50-95, Precision, Recall
- **Visualizations:** Confusion matrix, Precision-Recall curve, F1-Score curve
- **Tools Used:** Python, PyTorch, Ultralytics, Google Colab

## 📁 Outputs

- Trained model weights (`best.pt`)
- Zipped predictions (`visdrone_predictions.zip`)
- Evaluation charts (F1, PR, Confusion Matrix)
- Tabulated class-wise detection performance
- 
---

## 🧠 Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.
