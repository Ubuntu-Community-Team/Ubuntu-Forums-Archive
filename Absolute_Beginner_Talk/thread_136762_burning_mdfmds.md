---
title: "burning mdf/mds"
date: 2006-02-26
forum: Absolute Beginner Talk
---

### Post by time_shift on 2006-02-26
how do you burn mdf/mds onto a cd, and is there any cd/dvd emulating software for linux

---

### Post by BeatBoxRocker on 2006-02-26
You can use [mdf2iso]("http://mdf2iso.berlios.de/") to create the iso file and burn or mount it under linux.

To mount an iso file:
- Create a folder to mount the iso, for example /media/iso (you can use the mount point of a normal cd drive)
- Open console and type: sudo mount -t iso9660 myimage.xxx /media/iso -o loop
- myimage.xxx : the name of the image and its extension (maybe iso or mdf if it works)

If you cant mount the mdf file directly try the program mdf2iso. Here is a ver good HOWTO with several cd images format: [LinuxQuestions]("http://wiki.linuxquestions.org/wiki/CD_Image_Conversion#mdf2iso").

Saludos!

---

### Post by nolan- on 2006-05-18
Hi,

mdf2iso will not convert large images, say a DVD.
It will complain that the image is too large.

K3B will however burn the image without problems!
Just click "Burn DVD ISO image" then browse to your MDF file and on the filter dropdown menu choose all files and then select the MDF file.

K3B will check the file and providing everything is ok you will be able to burn it.

I'm using K3B 0.12.14 which is the latest from the repositories.

NoL

---

### Post by TrendyDark on 2006-05-18
K3B works with MDF files?

---

### Post by nolan- on 2006-05-18
[QUOTE=TrendyDark]K3B works with MDF files?[/QUOTE]

Yeah it will mate, it seems to just treat them as iso files if you knock the filter off.

Nero does the same in *cough* windows with img files etc....

I have burned a lot of mdf files without one problem in k3b.

---

### Post by xloris on 2008-03-19
With the .mds format  (and the other .i00 .i01 etc ... image files) there is an easy way to solve the buring problem: no need to install new software!
You just have to combine the .i0* files in one .iso with the following command:

cat filename.I00 filename.I01 filename.I02 ... > filename.ISO

Then you can burn your .iso image with your regular program (K3b)
It works!

bye,
Loris

---

