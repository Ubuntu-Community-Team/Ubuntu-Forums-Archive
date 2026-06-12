---
title: "GIMP Batch Mask"
date: 2011-10-21
forum: Art &amp; Design
---

### Post by God of the Meeps on 2011-10-21
Hey guys, 

I have a program that likes to output files as .png files without an alpha channel. As a result, the pictures have white backgrounds. These pictures are for a card game my friend and I are working on. As a result, we have quite a few cards (somewhere around 300-400). I have a mask that correctly eliminates the white background, but I'd rather not do it by hand. Is it possible to use GIMP to apply the mask to each and every image? If so, how?

Thanks in advance.

---

### Post by ofnuts on 2011-10-21
> **God of the Meeps said:**
> Hey guys, 

I have a program that likes to output files as .png files without an alpha channel. As a result, the pictures have white backgrounds. These pictures are for a card game my friend and I are working on. As a result, we have quite a few cards (somewhere around 300-400). I have a mask that correctly eliminates the white background, but I'd rather not do it by hand. Is it possible to use GIMP to apply the mask to each and every image? If so, how?

Thanks in advance.Look at ImageMacick instead (imagemagick in your repository). 
One way is to perform a first call to split your image into three images with each of its RGB components, and do a second call to rebuild the image for the 3 components plus an "opacity" component (your mask) (see [http://www.imagemagick.org/script/command-line-options.php#combine](http://www.imagemagick.org/script/command-line-options.php#combine)). The more savvy users at the imagemagick.org forums may have a more direct solution.

If you think it's complicated, you've not yet used Gimp in batch mode ;)

---

### Post by God of the Meeps on 2011-10-22
I just looked up GIMP's batch mode, and I must say that I agree with you, haha.

ImageMagick looks like a pretty solid choice from here. I'll be giving that a try as soon as I get 11.10 up and running.

---

