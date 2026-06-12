---
title: "[SOLVED] Immage scale down / thumbnail"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by hhhhhx on 2007-12-19
I have a bunch of images that i need to make thimbnails for.  is there a good program to do this with

they dont haft to high quality or anything, just a thumbnail of the big pic

thanks in advance

xhhux

---

### Post by RomeReactor on 2007-12-19
Hi. You can do that with either GIMP or gThumb, both of which are already installed on your system; right-click on an image and select "Open with->Gimp" or "Open with->gThumb"; in either, press "Image" in the toolbar and there you'll find an option to resize the image; just make sure you "Save as..." so as to not delete the original.

---

### Post by hhhhhx on 2007-12-19
ya but is there a way that i can do that with a lot of images all at once

---

### Post by RomeReactor on 2007-12-19
You can use the **convert** command from the terminal; see [this thread]("http://ubuntuforums.org/showthread.php?t=303442").

I think convert  should be already installed in your system. If it isn't, install **imagemagick**:
```
sudo apt-get install imagemagick
```

---

### Post by FuturePilot on 2007-12-19
> **xhhux said:**
> ya but is there a way that i can do that with a lot of images all at once
Indeed there is!
```
sudo apt-get install nautilus-image-converter
```
Now you can highlight many images and then right click and in the menu you will see an option to "Resize Image..."
Click that and you will get a bunch of options for new size etc. It will batch convert them.

You might have to log out and back in to get the menu entries to show up.

---

### Post by stani on 2007-12-20
You can also use Phatch, it is especially designed for processing thousands of images:
[http://photobatch.stani.be](http://photobatch.stani.be) (free download below for ubuntu)

It can not only resize, but also apply rounded corners, shadows, watermarks, ...

I posted a tutorial here to get you started:
[http://photobatch.wikidot.com/getting-started](http://photobatch.wikidot.com/getting-started)

---

