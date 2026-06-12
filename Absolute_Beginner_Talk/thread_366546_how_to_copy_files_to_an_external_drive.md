---
title: "how to copy files to an external drive"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by jprb85 on 2007-02-21
I am having a very difficult time saving files to my external hard drive. I have a 40 GB external Maxtor hard drive. I am able to easily copy files from my external hard onto my Ubuntu computer but I cannot save files onto my external hard drive with my Ubuntu computer. Every time I do that it tells me that I do not have the permissions but I have never set the permissions to prevent saving on the external hard drive. I am able to easily save files onto the external hard drive from Microsoft Windows but not Ubuntu. I would greatly appreciate if you could tell me what I need to do in order to be able to save onto my external drive. Thank you. 
:popcorn:

---

### Post by finer recliner on 2007-02-21
what format is your external HDD? if its NTFS. you wont be able to save to it without installing  some beta software

---

### Post by Skia_42 on 2007-02-21
The drive is probably mounted as a read only harddrive. You need to enable it by going to: System->Administration->Disks The full discritption is here:
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch10s02.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch10s02.html)

---

### Post by jprb85 on 2007-02-21
Unfortunately when I go to system/administration there is no disks menu. I would greatly appreciate if you could tell me how to find the disks menu. 

Thanks

:popcorn:

---

### Post by taxi taxi! on 2007-09-19
myes i cant find the disks menu either :s and i have the same problem

---

### Post by expatCM on 2007-09-20
Could this be a permissions problem?

Why not launch nautilus and then have a look for the drive under Media.  Right click and see what permissions are set?

---

### Post by alienexplorers on 2007-09-20
Try running from terminal:
> gksudo nautilus
then try copying files to your drive.

You could also try using the command > ls -l to see what person and group own the permissions to the drive.

---

