---
title: "Best way to make a PDF from a bunch of images?"
date: 2011-07-24
forum: Art &amp; Design
---

### Post by Potters Son on 2011-07-24
Please forgive me if I posted this in the wrong subforum, but I have a bunch of images (100+) that I'd like to assemble into a PDF file, and I don't know a good way to do it. Unfortunately, Simple Scan only does this if you got the images from a scanner. :(

---

### Post by Framli on 2011-07-24
The **convert** command from the **imagemagick** package does exactly what you are asking.
In a terminal:
```
cd folder_containing_your_images/
convert *.jpg bunch_of_images.pdf
```

---

### Post by Potters Son on 2011-07-24
Framli,
Thanks so much! It worked wonderfully! I feel kinda foolish now, though; I'd just started reading about Imagemagick the other day.

---

