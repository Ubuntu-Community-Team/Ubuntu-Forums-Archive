---
title: "Resize Mutiple Photos"
date: 2010-01-04
forum: Art &amp; Design
---

### Post by CarlosinFL on 2010-01-04
My digital camera takes .jpg images at the highest quality available. After shooting 200+ high resolution JPG files, I don't have time and or patience to copy them and resize the duplicates to a smaller scale for Facebook uploads. Can someone tell me if I can use Gimp or a plugin to resize several JPG files rather than doing them manually?

Please help!

---

### Post by realzippy on 2010-01-04
[http://ubuntuforums.org/showthread.php?t=830970](http://ubuntuforums.org/showthread.php?t=830970)

---

### Post by _sAm_ on 2010-01-04
Phatch([http://photobatch.stani.be/](http://photobatch.stani.be/))

Install via Synaptic.

---

### Post by mcduck on 2010-01-04
Phatch is a nice GUI tool for simpler editing/resizing, for more complex stuff (or if you like using command line) you should try Imagemagick.

For example the following command would use Imagemagick to resize all JPG images in current directory and strip any EXIF data from them, and save the new images with new names (so the originals are not changed):
```

For f in *.jpg; do convert "$f" -resize 640x480 -strip small-"$f"; done
```

---

### Post by Newfoundlander on 2010-01-05
For resizing multiple images, I use **Nautilus Image Converter**. After installing, just right-click on the image(s) and select "Resize Images". 

sudo apt-get install nautilus-image-converter

---

