---
title: "How do I change the size of a large number of png files?"
date: 2006-11-16
forum: Art &amp; Design
---

### Post by pain of salvation on 2006-11-16
I have some 128 x 128 png icons, and I want to resize them to 48 x 48. Is there a easy way to resize them all?

---

### Post by earobinson on 2006-11-16
convert -resize 48X48 *.png

---

### Post by pain of salvation on 2006-11-16
convert: command not found :confused:

---

### Post by Aelfric5578 on 2006-11-16
I don't know for sure, and can't test it at the moment, but that command is probably related to the program ImageMagick.  You may need to install that program to get the command to work.

---

### Post by savohead on 2006-11-17
i'm not at home so i can't check, but maybe there's a way to create a rule in gimp, so that you launch it and it opens the files changing the resolution and saves 'em.
i'll try to find out.

---

### Post by earobinson on 2006-11-17
googled: convert linux command
found: [http://linux.about.com/od/commands/l/blcmdl1_convert.htm](http://linux.about.com/od/commands/l/blcmdl1_convert.htm)
> Convert recognizes the image formats listed in ImageMagick(1). My guess is you need to install ImageMagick

---

### Post by pain of salvation on 2006-11-17
Ok, thanks..

---

### Post by earobinson on 2006-11-17
assuming it worked? If so do use a favor and edit the original post, click advanced, and mark the thread as resolved!

---

