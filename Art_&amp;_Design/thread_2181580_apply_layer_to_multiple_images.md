---
title: "apply layer to multiple images"
date: 2013-10-18
forum: Art &amp; Design
---

### Post by Johannes_Grillet on 2013-10-18
Hi,

How can I apply a layer to a series of images? I want to apply a copyright, digital watermark, to a folder of images at once instead op applying it image per image.

Can this be done with Gimp?

Thank you

---

### Post by varunendra on 2013-10-19
Welcome to the forums Johannes!

> **Johannes_Grillet said:**
> I want to apply a copyright, digital watermark, to a folder of images at once instead op applying it image per image.

Please try "Phatch" -
```
sudo apt-get install phatch
```
It is a batch image processor especially designed for such tasks. Watermarking includes selecting your chosen image to overlay, select its orientation, position etc. and select its opacity.

Basically, you select and 'Add' an action > customize it per your needs > save it > execute it on a selected directory. All through an intuitive GUI, although it's commandline version is also available (phatch-cli).

It saves the results as 'copies', but still it is recommended to keep the originals safe, and only perform the actions on copies of the originals.

---

### Post by ofnuts on 2013-10-19
> **Johannes_Grillet said:**
> Hi,

How can I apply a layer to a series of images? I want to apply a copyright, digital watermark, to a folder of images at once instead op applying it image per image.

Can this be done with Gimp?

Thank you

Install the imagemagick package and use its "compose" command to merge your watermark on your images.

---

### Post by Johannes_Grillet on 2013-10-22
Thank you very much. Very useful information.

---

