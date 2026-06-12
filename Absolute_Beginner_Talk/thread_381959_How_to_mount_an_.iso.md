---
title: "How to mount an .iso"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by tcebak on 2007-03-11
Hello  i was wondering if there was a GUI way of mounting .iso files. i know the command line:

mount -o loop -t iso9660 filename.iso /mnt/

but i tend to messt that up. but is there a program any one can direct me to (i tried kiso but lots of errors poped up. but any info would be great. (or if the command line is the best just tell me) I appericate your time

---

### Post by Iarwain ben-adar on 2007-03-11
I don't know about a GUI way,
but if you searc on kde-look (provided you have KDE) you can find a mounting plug-in there..

The command is
```
sudo mount /path/to/iso -o loop /place/to/mount
```

I use it all the time :D


Iarwain

---

### Post by tcebak on 2007-03-11
Thank you!!! (i was born in belgium :))

---

### Post by astrolabio on 2007-03-11
you pehaps should take a look to cdemu and AcetoneISO
[http://www.kde-apps.org/content/show.php?content=44805&PHPSESSID=bd812be1e299e8efc68b8633c9292ac3](http://www.kde-apps.org/content/show.php?content=44805&PHPSESSID=bd812be1e299e8efc68b8633c9292ac3)

---

### Post by Iarwain ben-adar on 2007-03-11
> **tcebak said:**
> Thank you!!! (i was born in belgium :))

Nice!

Where were you born? I'm from Oost-Vlaanderen :D


Iarwain

---

### Post by tcebak on 2007-03-11
thanks for the post. but i'm using gnome.  maybe they have them for gnome?

---

### Post by Najand on 2007-03-11
> **tcebak said:**
> Hello  i was wondering if there was a GUI way of mounting .iso files. i know the command line:

mount -o loop -t iso9660 filename.iso /mnt/

but i tend to messt that up. but is there a program any one can direct me to (i tried kiso but lots of errors poped up. but any info would be great. (or if the command line is the best just tell me) I appericate your time

You probably either need to run "sudo modprobe loop" before mount command or you need to use SUDO  before mount command to do it.

---

### Post by tcebak on 2007-03-11
the town of Mons.

---

### Post by sad_iq on 2007-03-11
Read these 2 posts ...maybe they'r helpful 
 [http://www.ubuntuforums.org/archive/index.php/t-194889.html](http://www.ubuntuforums.org/archive/index.php/t-194889.html)
 [http://ubuntuforums.org/showthread.php?t=67730](http://ubuntuforums.org/showthread.php?t=67730)

---

