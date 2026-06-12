---
title: "Image viewer - recursive directories"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by Dasein3 on 2006-08-15
Hi, I've been looking for something that'll let me view a slideshow of recursive directories.  I've been looking around and find it hard to beleive it's such an uncommon option.

I'd like to stick with gthumb if it's possible to do this with that program, as I've got ubuntu on an OLD laptop and don't want to have to install too much more stuff.

Anyone know of a simple little slideshow program that'll play all the images in a directory and its subdirectories?

---

### Post by ComplexNumber on 2006-08-15
try f-spot. the other week, i imported a direcory containing several lower lovel direcories of images. then you can select slideshow.

---

### Post by Dasein3 on 2006-08-15
thanks for the advice.  I was toying with the idea of installing something like that.  It seems to do a lot of photo management and editing stuff that I don't need though.  I'm a bit worried about overloading my machine.

Any idea why this option isn't native in gthumb?  Seems like a pretty easy thing to include.  Not that I'm a linux expert, but I've done some scripting on unix.

Since I now know F-spot does recursive directories, I might just give it a go and see what happens to my poor old machine : )

---

### Post by VirtuAlex on 2006-08-17
You can overcome this by managing catalogs in gthumb. You'd have to add files to a catalog by hands though. What feature gthumb really lacks is respect for orientation tag. I do not want to alter my original image data unless it is absolutely necessary. My camera detects orientation automatically and sets the tag. Actually this tag is present in most, if not all, exif headers from any cameras, it is just set to default value if camera lacks the autodetection feature. You can set this tag to proper value for lossless rotation. I dislike f-spot for many reasons, but it is the only viewer (afaik) which respects orientaiton tag.

---

### Post by AThomsen on 2006-08-22
Theres a small viewer called "feh" that can do this.
It's command-line based but easy to use.
```
apt-get install feh
```

---

### Post by VirtuAlex on 2006-08-22
feh is a very nice super flexible tool, but still no sign of orientation tag support

---

