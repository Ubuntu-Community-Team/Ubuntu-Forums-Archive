---
title: "photography"
date: 2010-04-16
forum: Art &amp; Design
---

### Post by goldshirt9 on 2010-04-16
sorry if i have posted in the wrong thread.

i am after a program to stitch panoramic photo's together.
i use sony raw files" arw" when possible.

i run Ubuntu karmic koala .
any help or directions to the right thread would be appreciative :P

many thanks in advance

---

### Post by Directive 4 on 2010-04-16
Hugin Panorama creator


from the software center/

---

### Post by goldshirt9 on 2010-04-16
all i get is a tiff library error.

---

### Post by Directive 4 on 2010-04-16
sorry, i have no further information.

---

### Post by ajgreeny on 2010-04-16
Try using pandora plugin for gimp, together with the gimp-ufraw plugin.  I have used pandora several times with success, but not on raw file formats.  However, gimp can be made to open arw files with the gimp-ufraw apparently, so it's worth a try.  Both packages are available from the repos.

---

### Post by goldshirt9 on 2010-04-17
i have added that plugin for gimp .:)
unfortunately sony raw files are a bit of a bitch to view in programs.:(

i have learnt to to import to gimp via rawstudio only.


it looks like i'll have to learn as i go with this project.

Directive 4 , thanks for the speedily reply.

ajgreeny again thanks.

---

### Post by guine on 2010-04-17
I use autostitch(run through wine) and have never had any problems with it.  [http://cvlab.epfl.ch/~brown/autostitch/autostitch.html](http://cvlab.epfl.ch/~brown/autostitch/autostitch.html)

---

### Post by jessel on 2010-04-20
I just started using hugin myself. I have found that it doesn't see the raw files (for my canon camera). It can see jpg and tiff, so a lot of times I shoot in raw + jpg. Since you can't go back in time, you will need to convert the raw files (jpg or tiff) before hugin will look at them. At least thats my understanding...

---

### Post by earlycj5 on 2010-04-20
You'll need to create .jpg or .tif files from the .arw files for Hugin to work.

The .tif files that you get from the .arw files are small thumbnails for .arw display purposes in file managers, etc.

Use RawStudio, Bibble, LightZone, UFRAW, Gimp-UFRAW plugin, whatever, to develop your raw files into a raster format that Hugin can read first.  Then stitch them in Hugin.

---

