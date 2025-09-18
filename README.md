# ⚡ Memory Optimized Stable Diffusion Text-to-Image Generator

A lightning-fast, memory-efficient Stable Diffusion implementation with real-time progress tracking, specifically optimized for Google Colab. Generate high-quality images from text prompts in 10-60 seconds with intelligent memory management and live progress updates.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/)
[![Python 3.7+](https://img.shields.io/badge/python-3.7+-blue.svg)](https://www.python.org/downloads/)
[![MIT License](https://img.shields.io/badge/license-MIT-green.svg)](https://opensource.org/licenses/MIT)

## 🚀 Features

- **⚡ Ultra-Fast Generation**: 10-60 seconds per image (vs 10+ minutes with standard implementations)
- **📊 Real-Time Progress Tracking**: Live percentage completion, elapsed time, and ETA
- **🧠 Memory Optimized**: Runs smoothly on Google Colab free tier without crashes
- **🎨 Multiple Quality Presets**: Ultra Fast (8 steps), Balanced (15 steps), High Quality (25 steps)
- **📱 Beautiful Gradio UI**: Intuitive interface with tabs, presets, and system monitoring
- **🔄 Automatic Memory Management**: Smart cache clearing and CPU offloading
- **🎯 Input Validation**: Prevents settings that would exhaust Colab resources

## 📋 Quick Start

### Option 1: Google Colab (Recommended)
1. Open a new [Google Colab notebook](https://colab.research.google.com/)
2. Enable GPU: `Runtime` → `Change runtime type` → `Hardware accelerator` → `GPU`
3. Run these cells in order:

**Cell 1 - Install Dependencies:**
```bash
!pip install -q diffusers[torch] transformers accelerate
!pip install -q gradio safetensors
```

**Cell 2 - Check GPU Status:**
```python
import torch
print('GPU Available:', torch.cuda.is_available())
if torch.cuda.is_available():
    print('GPU Model:', torch.cuda.get_device_name())
    print('GPU Memory:', f'{torch.cuda.get_device_properties(0).total_memory/1e9:.1f} GB')
```

**Cell 3 - Run the Generator:**
```python
# Copy and paste the main script here
```

### Option 2: Local Installation
```bash
# Clone the repository
git clone https://github.com/yourusername/memory-optimized-stable-diffusion.git
cd memory-optimized-stable-diffusion

# Install dependencies
pip install -r requirements.txt

# Run the application
python main.py
```

## 🎯 Performance Benchmarks

| Setting | Resolution | Steps | Generation Time | Quality |
|---------|------------|-------|----------------|---------|
| Ultra Fast | 512x512 | 8 | ~10-15s | Good |
| Balanced | 512x512 | 15 | ~20-30s | Great |
| High Quality | 640x640 | 25 | ~40-60s | Excellent |

*Benchmarks on Google Colab with T4 GPU*

## 🛠️ Technical Optimizations

### Memory Management
- **CPU Offloading**: Automatically moves model components to CPU when not in use
- **Attention Slicing**: Reduces VRAM usage during generation
- **VAE Slicing & Tiling**: Additional memory optimizations for larger images
- **FP16 Precision**: Uses half-precision on GPU to save memory
- **Automatic Garbage Collection**: Smart memory cleanup after each operation

### Speed Optimizations
- **EulerDiscreteScheduler**: Faster sampling method than default DPM
- **Disabled Safety Checker**: Removes unnecessary processing overhead
- **Aggressive Memory Slicing**: Maximum memory efficiency
- **Optimized Pipeline**: Streamlined generation process

## 📊 Real-Time Monitoring

The interface provides comprehensive progress tracking:

- **Model Loading Progress**: Shows download and setup completion percentage
- **Generation Progress**: Live updates with:
  - Current step / total steps
  - Percentage completion (0-100%)
  - Elapsed time
  - Estimated remaining time
- **Memory Usage**: Real-time GPU memory monitoring
- **Performance Metrics**: Generation time and efficiency stats

## 🎨 Usage Examples

### Basic Generation
```python
# Simple prompt
"a beautiful sunset over mountains, highly detailed"

# With negative prompt
"a serene lake at dawn"
# Negative: "blurry, low quality, distorted"
```

### Advanced Prompts
```python
# Artistic styles
"a cyberpunk cityscape at night, neon lights, highly detailed, cinematic lighting, 4k"

# Portrait photography
"portrait of a wise old wizard, intricate details, studio lighting, professional photography"

# Fantasy landscapes
"magical forest with glowing mushrooms, fairy lights, mystical atmosphere, digital art"
```

## ⚙️ Configuration Options

| Parameter | Range | Default | Description |
|-----------|-------|---------|-------------|
| Inference Steps | 8-30 | 15 | More steps = better quality, longer time |
| Guidance Scale | 3-15 | 7.5 | Higher = follows prompt more closely |
| Width/Height | 256-768 | 512 | Image dimensions (GPU memory dependent) |
| Seed | -1 to ∞ | -1 | -1 for random, fixed number for reproducible results |

## 🔧 Troubleshooting

### Common Issues

**"CUDA out of memory" Error:**
- Reduce image dimensions (try 384x384 or 256x256)
- Lower inference steps to 8-12
- Restart Colab runtime and try again

**Slow Generation Times:**
- Ensure GPU is enabled in Colab
- Use the "Ultra Fast" preset
- Avoid very large images (>512px)

**Model Loading Fails:**
- Check internet connection
- Restart Colab runtime
- Try a different model from the dropdown

### Performance Tips

1. **For Speed**: Use 8-12 steps with 512x512 resolution
2. **For Quality**: Use 20-25 steps with detailed prompts
3. **For Memory**: Keep dimensions ≤ 512px and use CPU offloading
4. **For Consistency**: Use fixed seeds for reproducible results

## Sample Input:
A complete view of a 45 degree angle parked Dark Blue Lamborghini Revuelto with red and white double stripes in the middle and with a scenic city night background behind

## Sample Output:
![image](https://github.com/user-attachments/assets/aa45c0ce-d50f-48bb-91d8-d474ef8507c2)

```

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

1. **Fork the repository**
2. **Create a feature branch**: `git checkout -b feature/amazing-feature`
3. **Commit your changes**: `git commit -m 'Add amazing feature'`
4. **Push to the branch**: `git push origin feature/amazing-feature`
5. **Open a Pull Request**

### Areas for Contribution
- Additional model support (SDXL, ControlNet, etc.)
- More memory optimizations
- UI/UX improvements
- Documentation and examples
- Performance benchmarking

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- [Hugging Face Diffusers](https://github.com/huggingface/diffusers) - Core diffusion library
- [Gradio](https://gradio.app/) - Web interface framework
- [Stability AI](https://stability.ai/) - Stable Diffusion models
- [Google Colab](https://colab.research.google.com/) - Free GPU compute platform

## 📞 Support

- **Issues**: [GitHub Issues](https://github.com/yourusername/memory-optimized-stable-diffusion/issues)
- **Discussions**: [GitHub Discussions](https://github.com/yourusername/memory-optimized-stable-diffusion/discussions)
- **Email**: your.email@domain.com

## 🌟 Star History

If you find this project useful, please consider giving it a star! ⭐

---

**Made with ❤️ for the AI art community**
