---
title: "fonts:///"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by delsydebothom on 2008-04-14
I have discovered that since I upgraded to 8.04, I've been unable to install my fonts the way I always have: by opening fonts:/// and dragging the ones I want into the folder. It says that "Nautilus can handle fonts: locations." :( 

From what I understand, having looked the problem up, this is a known bug, and steps are being taken to correct it. In the meantime, though, are there any easy ways for me to install new fonts, or is the fonts folder locked entirely?

---

### Post by conscious on 2008-04-14
I think they just go to /usr/share/fonts .

---

### Post by delsydebothom on 2008-04-14
There are a number of folders in there, and I'm not sure which one to put my fonts in :lolflag:.

---

### Post by erginemr on 2008-04-14
Please also refer to:
[http://ubuntuforums.org/showthread.php?t=420877](http://ubuntuforums.org/showthread.php?t=420877)

---

### Post by hyperair on 2008-04-14
I'm not sure, but I think putting them in ~/.fonts works too. Otherwise just dump them in a folder in /usr/share/fonts or /usr/local/share/fonts.

---

### Post by Screaming Monkey on 2008-04-16
> **delsydebothom said:**
> There are a number of folders in there, and I'm not sure which one to put my fonts in :lolflag:.

Use the 
```
gksudo nautilus 
```
trick and make a directory called "myfonts" or something like that.  That's what I do.

---

