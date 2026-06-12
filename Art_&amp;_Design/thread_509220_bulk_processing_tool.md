---
title: "bulk processing tool??"
date: 2007-07-25
forum: Art &amp; Design
---

### Post by robgr85 on 2007-07-25
Hi!

Is there any script/program available to batch/bulk process images that would give ability to:

- add signature to photos,
- resize them,
- create thumbnails,

I know that something like that exists, but can not remember its name,

It would be also nice to be able to edit ITPC metadata of group of files at once (4 eg adding keywords etc)

Any sugestions?

Robert

---

### Post by beefcurry on 2007-07-25
try digiKam

---

### Post by robgr85 on 2007-07-26
any other suggestions? I remember that there was some command line tool/script for that.

---

### Post by Dragonbite on 2007-07-26
Is this something Imagemagick can do?
> magemagick is a set of programs to manipulate various image formats (JPEG, TIFF, PhotoCD, PBM, XPM, etc...). All manipulations can be achieved through shell commands as well as through an X11 graphical interface (display).

Possible effects: colormap manipulation, channel operations, thumbnail creation, image annotation, limited drawing, image distortion, etc...

This package suggests a postscript interpreter (gs) to read postscript files. It will however function happily without it (as long as you don't want to read postscript). 

---

### Post by meatpan on 2007-07-26
Definitely a job for imagemagick.  The name of the command line program for performing you operations is 'convert'

---

### Post by robgr85 on 2007-07-26
Thank You.

Robert

---

### Post by rejser on 2007-07-27
There is a thread about it.
Seen the other thread about pbatch? Should be on some of the first pages in arts department.

---

### Post by CrownP10:8 on 2007-07-29
> **robgr85 said:**
> Hi!


- add signature to photos,
- resize them,
- create thumbnails,

It would be also nice to be able to edit ITPC metadata of group of files at once (4 eg adding keywords etc)



Start by installing "imagemagick" and "exiv2" packages.

[FONT="Courier New"]$ sudo apt-get install imagemagick exiv2[/FONT]

I use for loops in the shell to process my photos.

Add signature/watermark - here a transparent PNG on all JPG in current directory:

[COLOR="black"][COLOR="black"][FONT="Courier New"]$ for i in *.jpg; do composite -dissolve 50% -gravity southeast /my/watermark.png $i watermarked-$i; done[/FONT][/COLOR][/COLOR]

Resize:

[FONT="Courier New"]$ for i in *.jpg; do convert -resize 1024x768 $i small-$i; done[/FONT]

Thumbnail (this uses "basename", there is probably an easier way):

[FONT="Courier New"]$ for i in *.jpg; do convert -resize 320x240 $i `basename $i .jpg`.png ; done[/FONT]

As for the metadata, the "exiv2" program can do all sorts of things with that.

---

### Post by geovino on 2007-07-29
I just installed imagemagick, but it's not on the menu list nor does it open when typing it in the console.

I installed it through synaptic.

---

### Post by mcduck on 2007-07-30
> **geovino said:**
> I just installed imagemagick, but it's not on the menu list nor does it open when typing it in the console.

I installed it through synaptic.

It's a set of command line applications. So there's nothing to show on the menus. The ones you are most likely to need are called 'convert' and 'mogrify'. (so there is no command 'imagemagick')

[http://www.imagemagick.org/Usage/]("http://www.imagemagick.org/Usage/")

---

### Post by geovino on 2007-07-30
Thanks for the info... but I'll use Digikam instead.

---

### Post by CrownP10:8 on 2007-07-30
Yep, the "convert" and "composite" commands in my examples above are utilities provided by the "imagemagick" package.

---

### Post by stani on 2007-08-02
> **rejser said:**
> There is a thread about it.
Seen the other thread about pbatch? Should be on some of the first pages in arts department.
The real name is phatch:
'Phatch is a simple to use cross-platform GUI Photo Batch Processor which handles all popular image formats and can duplicate (sub)folder hierarchies. Phatch can batch resize, rotate, rename, ... and more in minutes instead of hours or days if you do it manually. Phatch will also support a console version in the future to batch photos on webservers.'

For more info and screenshots, see here
[http://ubuntuforums.org/showthread.php?t=466598](http://ubuntuforums.org/showthread.php?t=466598)

---

