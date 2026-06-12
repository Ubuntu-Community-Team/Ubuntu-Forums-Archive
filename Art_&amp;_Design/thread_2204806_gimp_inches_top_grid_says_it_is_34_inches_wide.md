---
title: "gimp inches top grid says it is 34 inches wide?"
date: 2014-02-10
forum: Art &amp; Design
---

### Post by sdowney717 on 2014-02-10
I took a picture of my gauge face to edit in gimp.
Ultimately the goal is to reprint and glue on a new face.
The size will need to be resized so it will fit.

In gimp, I have it done. Gimp says it is massive 34 wide and 25 inches tall.
When it prints on an 8 x 11 sheet it prints 5 inch circular image.

So what is it saying about the picture size?
How can i resize it to 3.5 inches wide?

---

### Post by sdowney717 on 2014-02-10
I found it under menu image scale image.
I scaled image to 5.25"
I used cubic interpolation.
By trial and error, I got to the right size so that a print will fit the old gauge.

Somehow a grid shows up on the image, which I have to go into the menu and check off the grid view.
Why is that?

---

### Post by ofnuts on 2014-02-10
Scaling the image is not necessary. What counts for Gimp is the size in pixels. When you want Gimp to use a physical size (display, measure, or print), you have to tell it how many pixels there are per physical unit. This is the "print definition". Most image formats have a field to keep a print definition, this is useful for instance in scanners, so that you can print an image at the very same size as the original. But it doesn't make sense for photography: an image can be a shot of the night sky (one parsec/pixel) or of a fly head (0.05mm/pixel). So cameras don't set this value or set the usual 72DPI default. In your case it seems to be pretty close to 100DPI, it could be your display screen definition (98DPI is not uncommon on displays).

If you scaled down your image to get the right size in inches, you will get that size, but only when printing at 100DPI, and this isn't very good quality printing (150DPI is "draft"). IMHO you should get back to the original, use "Image/Print size" to set the print definition to 600DPI (high quality print on laser printers); You will see that Gimp changes the physical size of the image to something smaller. Then you use Image/Scale image to set the physical size (in inches or cm) to what you need. Gimp will then set the image to the right pixels size to print the required physical size at 600DPI.

---

### Post by Buntu Bunny on 2014-02-11
Good question and good answer. I've had to prepare digital images for print and really struggled with it. I finally found a workaround but this is much easier. Thanks ofnuts.

---

