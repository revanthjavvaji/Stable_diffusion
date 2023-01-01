# Stable Diffusion

Stable Diffusion is a text-to-image latent diffusion model created by the researchers and engineers from CompVis, Stability AI and LAION. It's trained on 512x512 images from a subset of the LAION-5B database. This model uses a frozen CLIP ViT-L/14 text encoder to condition the model on text prompts. With its 860M UNet and 123M text encoder, the model is relatively lightweight and can run on many consumer GPUs. See the model card for more information.

Stable Diffusion is based on a particular type of diffusion model called Latent Diffusion, proposed in High-Resolution Image Synthesis with Latent Diffusion Models.

General diffusion models are machine learning systems that are trained to denoise random gaussian noise step by step, to get to a sample of interest, such as an image. For a more detailed overview of how they work, check this colab.

Diffusion models have shown to achieve state-of-the-art results for generating image data. But one downside of diffusion models is that the reverse denoising process is slow. In addition, these models consume a lot of memory because they operate in pixel space, which becomes unreasonably expensive when generating high-resolution images. Therefore, it is challenging to train these models and also use them for inference.


Latent diffusion can reduce the memory and compute complexity by applying the diffusion process over a lower dimensional latent space, instead of using the actual pixel space. This is the key difference between standard diffusion and latent diffusion models: in latent diffusion the model is trained to generate latent (compressed) representations of the images.

There are three main components in latent diffusion.

1.An autoencoder (VAE).

2.A U-Net.

3.A text-encoder, e.g. CLIP's Text Encoder.

Why is latent diffusion fast and efficient?

Since the U-Net of latent diffusion models operates on a low dimensional space, it greatly reduces the memory and compute requirements compared to pixel-space diffusion models. For example, the autoencoder used in Stable Diffusion has a reduction factor of 8. This means that an image of shape (3, 512, 512) becomes (3, 64, 64) in latent space, which requires 8 × 8 = 64 times less memory.

This is why it's possible to generate 512 × 512 images so quickly, even on 16GB Colab GPUs!

## Stable Diffusion during inference

Putting it all together, let's now take a closer look at how the model works in inference by illustrating the logical flow.
![stb](https://user-images.githubusercontent.com/114976742/210177478-271fd9a6-0f64-4371-9cce-5de5c08073a0.png)


# Art Generation Using Stable Diffusion

* Extract Stable Diffusion WebUi - [Stable Diffusion Web UI](https://github.com/AUTOMATIC1111/stable-diffusion-webui)

* Download Stable Diffusion Model (Pre Trained Weights) - [HuggingFace](https://huggingface.co/runwayml/stable-diffusion-v1-5#:~:text=v1%2D5%2Dpruned%2Demaonly.ckpt%20%2D%204.27GB%2C%20ema%2Donly%20weight.%20uses%20less%20VRAM%20%2D%20suitable%20for%20inference) 

* Running the WebUI on Local Host

* Generating the Image 
## Before
![sdd](https://user-images.githubusercontent.com/114976742/210178810-75b0555e-1d75-47b9-a7b0-ef0d533b069c.jpg)

## After 
![sd_art](https://user-images.githubusercontent.com/114976742/210178822-1f1134d1-5e48-40f5-9b70-d8348a2ae9a2.png)
