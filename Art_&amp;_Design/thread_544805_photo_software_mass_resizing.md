---
title: "photo software mass resizing"
date: 2007-09-06
forum: Art &amp; Design
---

### Post by h0lix on 2007-09-06
does anyone know of a program available for ubuntu that you can use to resize the resolution of all of the photos in one folder? i use gimp so resize a photo one at a time but that can be rather time consuming if you have to do each one manually.

---

### Post by Paul820 on 2007-09-06
Is this useful to you? [http://ubuntuforums.org/showthread.php?t=96333&highlight=resize+jpeg+script]("http://ubuntuforums.org/showthread.php?t=96333&highlight=resize+jpeg+script")

---

### Post by stani on 2007-09-24
Probably phatch (= photo & batch) fills your need:
[http://photobatch.stani.be](http://photobatch.stani.be)

Stani

---

### Post by kaczus on 2009-01-04
> **stani said:**
> Probably phatch (= photo & batch) fills your need:
[http://photobatch.stani.be](http://photobatch.stani.be)

Stani

Just wanted to say thanks man, somehow I missed that when searching in synaptic. Great tool.

---

### Post by canvasdezign on 2009-01-05
you visit these sites it might be helpful for you [http://oriens-jpeg-free.qarchive.org/,http://www.smokinglinux.com/tutorials/howto-batch-image-resize-on-linux,http://mac.softpedia.com/get/Graphics/iResize.shtml](http://oriens-jpeg-free.qarchive.org/,http://www.smokinglinux.com/tutorials/howto-batch-image-resize-on-linux,http://mac.softpedia.com/get/Graphics/iResize.shtml) all the best.

---

### Post by mcduck on 2009-01-05
I prefer Imagemagick:
```

for f in *.jpg; do convert "$f" -resize 640x480 -strip -quality 86 "$f"; done
```

That will go through all .jpg-images in current directory, resize them to fit 640x480 (while maintaining original aspect ratio), remove all EXIF data and then compress the images with 86% quality.

Imagemagick handles pretty much all the same things graphical apps like Photoshop and Gimp can do, but since it's command-line based you can easily use it with scripts to automatically handle quite massive image operations.

[http://www.imagemagick.org/script/index.php](http://www.imagemagick.org/script/index.php)

---

### Post by kayosiii on 2009-01-08
digikam provides a nice frontend to image magick

---

### Post by BEARSPIDER on 2011-10-10
Nautilus image converter - Software Center

---

### Post by nothingspecial on 2011-10-10
Please don't bump old threads to the top.

Closed.

---

