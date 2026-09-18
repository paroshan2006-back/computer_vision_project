# Edge Detection System

A simple Computer Vision project that implements and compares four classic
edge detection techniques on any input image:

- **Sobel** – gradient-based edge detection (x and y direction magnitudes)
- **Laplacian of Gaussian (LoG)** – blur first, then second-derivative edge detection
- **Canny** – multi-stage detector (blur → gradient → non-max suppression → hysteresis thresholding)
- **Difference of Gaussians (DoG)** – subtracts two differently blurred versions of the image
---

## 1. Requirements

- Python 3.8 
- pip

## 2. Installation

Open a terminal in the folder containing `edge.py` and run:

```bash
pip install opencv-python-headless numpy matplotlib
```

| Package | Purpose |
|---|---|
| `opencv-python-headless` | Core image processing (Sobel, Canny, Laplacian, Gaussian blur) |
| `numpy` | Array and math operations |
| `matplotlib` | Builds the side-by-side comparison chart |

If `pip` doesn't work, try `pip3` instead.

## 3. Usage

### Run image

Place an image file  in the same folder, then run:

```bash
python edge.py im1.png
```

## 4. Output

Running the script creates an output folder containing:

- `original.png`
- `sobel.png`
- `laplacian_log.png`
- `canny_<low>_<high>.png`
- `difference_of_gaussians.png`
- `comparison.png` — all five results shown side by side

## 5. Project Structure

```
.
├── edge_detection.py   # main script
├── README.md           # this file
└── output/             # generated results (created after running)
```

## 6. How It Works 

1. The image is loaded in grayscale.
2. Each method applies Gaussian blurring first to reduce noise sensitivity.
3. **Sobel** computes horizontal and vertical intensity gradients and combines
   them into a gradient magnitude image.
4. **Laplacian (LoG)** applies a second-derivative filter to highlight regions
   of rapid intensity change.
5. **Canny** refines gradients with non-maximum suppression and links strong/weak
   edges via hysteresis thresholding, producing thin, clean edge lines.
6. **DoG** approximates edge/blob structures by subtracting two Gaussian-blurred
   versions of the image at different scales.

## 7. Troubleshooting

- **`ModuleNotFoundError: No module named 'cv2'`** → re-run the pip install command above.
- **`pip: command not found`** → try `pip3` instead of `pip`.
- **`Could not read image at: ...`** → check the image path/filename is correct and the file exists in the same folder.
