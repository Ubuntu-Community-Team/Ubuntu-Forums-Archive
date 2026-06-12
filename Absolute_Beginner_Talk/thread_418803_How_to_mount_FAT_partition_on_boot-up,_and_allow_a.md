---
title: "How to mount FAT partition on boot-up, and allow all everybody to read/write ?"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by medya on 2007-04-22
Hi I wamt to mount my FAT partition on boot-up, and allow all everybody to read/write ?
I have added this to my /etc/fstab :

> /dev/hda7   /home/fred/Storage   vfat    iocharset=utf8,umask=000  0    0


it mounts my partition but I can not delete files in that partition or I can not copy files into it .
when I delete files it says "not on the same file system"

what should I do , to have my FAT partition to act like a Normal partition I am tired of this permission stuff.

---

### Post by RobsterUK on 2007-04-22
This guide should give you the info you need:
[Link]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite")

If you are still stuck, post back

---

### Post by medya on 2007-04-22
hey that link has EXACTLY the same code ! please somebody help

---

### Post by raul_ on 2007-04-22
did you reboot?

---

### Post by anaconda on 2007-04-22
You must also make the folder you mount the fat-partition to, readable by all users

eg. if you mount it to /media/storage then you need to make that folder readable and writable by all users you want to be able to rw to it.

eg type in terminal.
sudo mkdir /media/storage
sudo chmod a+rwx /media/storage
and then change it to mount to that directory..


I think your problem is that you are mounting it under your home folder, which by default other people dont have writing permission to. 
you could also make the folder you are now using accessible to all if you prefer that..

---

