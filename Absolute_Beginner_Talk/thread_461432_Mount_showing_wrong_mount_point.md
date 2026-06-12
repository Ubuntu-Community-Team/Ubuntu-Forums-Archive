---
title: "Mount showing wrong mount point"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2007-06-01
I installed the latest Fedora on another partition to just see it and when I erased it and booted into ubuntu, my 
data partition shows /mnt/Storage when it's really mounted at /media/Storage. Everything is functional, but it 
displays as /mnt/Storage instead of /media/Storage. A little annoying. Any idea how to fix this?

---

### Post by annda on 2007-06-01
check your /etc/fstab and correct the mount point to your liking.

---

### Post by shanepardue on 2007-06-01
fstab shows the right mount point and the partition is mounted correctly..it just shows the wrong name of the 
mount. It's actually mounted on /media/Storage, but it shows /mnt/Storage on the desktop and everywhere else.
 It's a little hard to explain.

---

### Post by shanepardue on 2007-06-01
DON'T EVER CREATE A DISKLABEL THROUGH GPARTED!!!

[Spinrite]("http://www.grc.com/sr/spinrite.htm"), please save me now!

---

### Post by Lucifiel on 2007-06-01
Yikes!!!!

I hope things go well for you. O_o;;

---

### Post by shanepardue on 2007-06-01
ANYWAYS! [Testdisk]("http://www.cgsecurity.org/wiki/TestDisk_Download") saved my behind!

I still have the same problem with the mounts though.

---

### Post by shanepardue on 2007-06-02
So I guess it's the disk label that is incorrect, but as I made the mistake before, I can't "set the disklabel".

How would I change the label of this volume is the real question.

---

### Post by trak87 on 2007-06-04
This link may help:

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

---

### Post by shanepardue on 2007-06-09
> **trak87 said:**
> This link may help:

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)
There we go! That was exactly what I needed!! Thank you very much trak87!!

---

