---
title: "How to do this in GIMP"
date: 2012-04-03
forum: Art &amp; Design
---

### Post by Ranko Kohime on 2012-04-03
My Google-fu is failing me, for the simple reason that I do not know the correct term for the effect I want to create.

I want to take a square image, and place it in the left half of a blank image that is twice as wide as the first image, and then have the first image "echo" towards the right, with descending opacity.  So that, say first image is binary black and white, the first echo the black is dark grey, the next echo a slightly lighter color, and so on until nearly white at the right edge.

I suppose I could do this with layers, editing each layer by hand, but I wanted to see if there was an easier way about it.

ETA: On second thought, I can't even seem to get the effect I want using layers...

---

### Post by BcRich on 2012-04-03
Hi
If you want the image to fade to white (is that what you want?) you could try gradually increasing the brightness of each layer as they move off to the right.
Colors > Brightness/Contrast

(GIMP 2.6x)

---

### Post by ofnuts on 2012-04-03
> **Ranko Kohime said:**
> My Google-fu is failing me, for the simple reason that I do not know the correct term for the effect I want to create.

I want to take a square image, and place it in the left half of a blank image that is twice as wide as the first image, and then have the first image "echo" towards the right, with descending opacity.  So that, say first image is binary black and white, the first echo the black is dark grey, the next echo a slightly lighter color, and so on until nearly white at the right edge.

I suppose I could do this with layers, editing each layer by hand, but I wanted to see if there was an easier way about it.

ETA: On second thought, I can't even seem to get the effect I want using layers...
- Create an image big enough for two squares (background automatically filled to white)
- Add new layer with half the canvas size, with required image (bucket-fille with checkerboard below)
- Duplicate layer
- Drag the layers to opposite sides of the canvas
- Select layer on the right
- Layer/Mask/add layer mask (init to white)
- Use the blend tool to draw a white-to-black horizontal gradient on the mask (first image)
- You can use Curves/Levels on the mask to adjust how the blend behaves (2nd image)

---

