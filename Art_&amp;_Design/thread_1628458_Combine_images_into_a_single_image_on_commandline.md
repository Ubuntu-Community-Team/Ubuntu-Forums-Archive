---
title: "Combine images into a single image on commandline"
date: 2010-11-22
forum: Art &amp; Design
---

### Post by GammaPoint on 2010-11-22
Hi, I am interested in combining two separate images (say *png files) into a single *png image via the command line. They will not necessarily be the same size and I don't want them to overlay ontop of each other. Can imagemagick or another program handle this?

Thanks in advance for your help!

---

### Post by Framli on 2010-11-23
Hi GammaPoint, 
the "montage" command from imagemagick can do a lot.

For example
```
montage -geometry 200x200+0+0 image1.png image2.png out.png
```
-> will resize each image (to 200px with no deformation) and combine them (separated by 0px).

A lot to learn from :
[http://www.imagemagick.org/Usage/montage/](http://www.imagemagick.org/Usage/montage/)
[http://www.imagemagick.org/script/montage.php](http://www.imagemagick.org/script/montage.php)

---

### Post by GammaPoint on 2010-11-23
This looks exactly like what I need Framli. Thanks so much for your help, I appreciate it!

---

### Post by paulmilliken on 2010-11-30
Moreover, if you wanted to ensure all the component images are scaled and stretched to fill 200x200 pixels you would do:
```
montage -resize 200x200! -geometry 200x200+0+0 image1.png image2.png out.png
```

---

