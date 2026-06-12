---
title: "simple 16 bit image editor?"
date: 2010-08-15
forum: Art &amp; Design
---

### Post by pootle42 on 2010-08-15
I'm trying to find a simple 16bit image editor to adjust the gamma in a 16 bit linear tiff image.

Gimp is obviously hopeless as it doesn't have 16 bit support.

Cinepaint sounded promising but seems to have died and I cannot find a repo to install it on 9 or 10

Krita sounded promising but the performance is awful (I have a 120Mb tiff file, if I touch anything it takes 30 - 40 seconds to repaint the screen even with opengl and shader support turned on)

Digikam editor looked promising but comes up with strange artifacts when I load the image. (and the main part of digikam is just a nuisance in this context)

All I need to do to the image is adjust the brightness and turn on some gamma, preferably interactively, but there doesn't seem to be anything around to do this.  

(I can do it from command line of course, but that's a bit tedious when it comes to fine tuning.)

(I'm doing focus stacking starting from 30ish raw files, processed through dcraw, then align image stack and enfuse)

---

### Post by robert shearer on 2010-08-15
Fotoxx ?  It is in the repos. (and from the site there are debs of more recent versions.  [http://kornelix.squarespace.com/fotoxx](http://kornelix.squarespace.com/fotoxx) ) 



> Fotoxx is a free open source Linux program for photo editing and collection management. The goal is to meet most user needs while remaining fast and easy to use.

Overview
Navigate a large image collection using a thumbnail browser. Import camera RAW files and edit with 16-bit color. Save edited images as TIFF-8/16, PNG or JPEG with adjustable compression. Edit the whole image or a selected area, with adjustable edge-blending. Edit functions have live feedback using the full window. Undo/redo up to 99 edits. Add tags, dates, and star-ratings to images and search using these criteria and (wildcard) file names. Fotoxx does not use filters, layers, and masks - the edit functions work directly on the image.

---

### Post by pootle42 on 2010-08-15
Thanks Robert, just had a quick look, but it won't open files output by either align_image_stack or enfuse :(  just going to check if the alpha hack that gimp used to need makes a difference - Nope the alpha jhack doesn't fix it, it won't load these files, just says it can only load a tiff or jpeg.  I've run from command line and there's no more info there either.

Also it doesn't appear to have a simple gamma tweaker in the tools, so I don't think this is the answer even if the tiff issue is fixed

---

### Post by robert shearer on 2010-08-15
Well, it is a while since I have used stacking and fotoxx but it did work.
used this tutorial  [http://photoblog.edu-perez.com/2009/01/greater-depth-field-macro.html](http://photoblog.edu-perez.com/2009/01/greater-depth-field-macro.html)

If I recall the problem was in the naming. Try renaming the file to .tif or .tiff to get fotoxx to recognise it.  
> pootle42...just says it can only load a **tiff** or jpeg.

I have just purged the fotoxx version from the  Ubuntu repo and downloaded the deb for 10.8.3
When it first runs it has an info update about tag handling and seems to have moved to a more universal notation.


Darktable might be worth a look....[http://darktable.sourceforge.net/](http://darktable.sourceforge.net/)

---

### Post by DzmitryG on 2010-09-21
ImageJ, although is more for scientists, handles 16 bit well. GUI is ugly, but functionality is great. Can be found in Ubuntu Software Centre/Science/Biology.

---

