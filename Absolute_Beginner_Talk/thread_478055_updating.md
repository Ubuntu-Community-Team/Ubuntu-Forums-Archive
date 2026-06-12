---
title: "updating"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by johnnyw on 2007-06-18
I have 6.06 and have downloaded 6.1.
I have it as an iso and have mounted it just as if I had it inserted in my drive. How can I do to make the update manager notice of the existence of it as my connection is way to crappy to DL the updates

Thx

J

---

### Post by meatpan on 2007-06-18
This can be done by editing the file /etc/apt/sources.list 

Here is a walk-through guide of using apt to scan a local file repository:
[http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html#s-dpkg-scanpackages](http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html#s-dpkg-scanpackages)

---

### Post by johnnyw on 2007-06-18
johnnyw@johnnyw-desktop:~$ sudo apt-cdrom add -d /media/isoimage
Using CD-ROM mount point /media/isoimage/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter
Mounting CD-ROM...
E: Failed to mount the cdrom.

---

### Post by meatpan on 2007-06-19
It looks like you tried to do something different than what you described in the first post.   Were you able to treat the mounted iso like a file, as mentioned in the faq?

If you want to do apt-cdrom, can you verify that the cd will mount on its own?  Just try to mount the cd, independent of apt, and see if there are any problems.

---

