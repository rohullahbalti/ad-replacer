# 📌 **AI-Powered Image Editing with SAM + Stable Diffusion Inpainting**

A complete pipeline for intelligent, high-quality image editing using **Meta’s Segment Anything Model (SAM)** and **Stable Diffusion / SDXL Inpainting**.
This project allows users to:

* Automatically detect objects
* Select the mask to edit
* Replace regions using AI-generated texture
* OR upload a manual replacement image
* Perform seamless inpainting that blends naturally into the original photo

Both **automatic segmentation** and **manual workflows** are supported.

---

## 🚀 **Features**

### 🔹 1. **Automatic Object Segmentation**

Uses the **Segment Anything Model (SAM)** to extract high-quality masks from any uploaded image.

### 🔹 2. **Interactive Mask Selection**

Users can:

* Visualize all masks
* See mask IDs on the image
* Select the region they want to edit

### 🔹 3. **AI Inpainting Using Stable Diffusion**

Replace selected areas with:

* SD 1.5 Inpainting
* SDXL Inpainting
* RePaint Pipeline

### 🔹 4. **Manual Replacement Image Support**

User can upload:

* A base image
* A replacement texture/logo
* Then map it onto the masked region

### 🔹 5. **Clean UI Through Google Colab Widgets**

Buttons, radio choices, image previews, and mask selection.

### 🔹 6. **Full-Resolution Processing**

Image is NOT resized.
SAM processes raw resolution for best segmentation.

---

## 🧠 **Tech Stack**

| Component                   | Purpose                   |
| --------------------------- | ------------------------- |
| **Python**                  | Core language             |
| **PyTorch**                 | ML backbone               |
| **Segment Anything (SAM)**  | Automatic mask generation |
| **Stable Diffusion / SDXL** | AI Inpainting             |
| **Diffusers (HuggingFace)** | Pipeline integration      |
| **OpenCV**                  | Contours, mask processing |
| **PIL**                     | Image handling            |
| **NumPy**                   | Array operations          |
| **ipywidgets**              | Interactive UI            |

---

## 📂 **Project Structure**

```
📁 AI-Image-Editor/
│── README.md
│── notebook.ipynb
│── sam_vit_h_4b8939.pth
│── examples/
│   ├── input.jpg
│   ├── mask.png
│   └── output.png
│── utils/
│   ├── mask_display.py
│   ├── inpaint_utils.py
│   └── manual_replace.py
```

---

## ⚙️ **Installation**

### 1. Clone the repository

```bash
git clone https://github.com/yourusername/AI-Image-Editor.git
cd AI-Image-Editor
```

### 2. Install dependencies

```bash
pip install torch torchvision torchaudio
pip install diffusers transformers accelerate
pip install opencv-python pillow numpy matplotlib
pip install ipywidgets
```

### 3. Download SAM Checkpoint

```bash
wget https://dl.fbaipublicfiles.com/segment_anything/sam_vit_h_4b8939.pth
```

---

## 🖼️ **Usage**

### ▶️ **1. Upload Main Image**

The notebook loads full-resolution images without resizing.

### ▶️ **2. Run SAM Segmentation**

This generates masks + areas + IoU scores.

### ▶️ **3. Visualize All Masks**

Each mask appears with a colored overlay + ID number.

### ▶️ **4. Select Mask to Edit**

Example:

```python
mask_index = 1
```

### ▶️ **5. Choose Editing Mode**

* **AI Replacement (Stable Diffusion / SDXL / RePaint)**
* **Manual Replacement Image**

### ▶️ **6. Generate Final Output**

The selected area is replaced and blended cleanly.

---

## 🧩 **How It Works Internally**

### **1. Mask Generation**

SAM generates:

* Segmentation map
* Bounding box
* Mask area
* Predicted IoU

### **2. Mask Display**

Contours → centroid → indexed mask display.

### **3. Inpainting Logic**

Stable Diffusion Inpaint works using:

* source_image
* segmentation mask converted to 255
* prompt + negative prompt

### **4. Manual Replacement Flow**

1. User uploads replacement image
2. SAM segments the replacement
3. User chooses replacement mask
4. Mask region is resized + warped
5. Overlaid on original mask area

---

## 📸 **Screenshots**

| Step               | Image              |
| ------------------ | ------------------ |
| Original           | *(add screenshot)* |
| Mask Visualization | *(add screenshot)* |
| Inpainted Output   | *(add screenshot)* |

---

## 🔮 **Future Improvements**

These ideas can be added later:

### **1. Video Support (Frame-by-Frame Editing)**

* Apply SAM and SD to each frame
* Track objects across frames
* Maintain temporal consistency

### **2. Manual Drawing Mode**

* User draws a freehand mask
* Convert drawing → segmentation mask

### **3. Texture Transfer**

* Instead of a whole replacement image, extract style/texture and replicate it on target mask

### **4. Local UI (Streamlit or Gradio)**

* Full app interface with drag-and-drop
* Real-time preview

### **5. Object Removal / Logo Removal Mode**

* Fill area with background using SDXL

---

## 🤝 **Contributing**

Pull requests are welcome!
Please open an issue before making major changes.

---

## 📝 **License**

This project is open-source under the **MIT License**.

---

## 🙌 **Credits**

* **Meta AI** — Segment Anything
* **Stability AI** — Stable Diffusion
* **HuggingFace Diffusers** — Inpainting pipelines
* **Google Colab Widgets** — Interactive UI components

-
