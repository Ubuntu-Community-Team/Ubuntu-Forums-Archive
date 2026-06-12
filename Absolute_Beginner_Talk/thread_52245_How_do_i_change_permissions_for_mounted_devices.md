---
title: "How do i change permissions for mounted devices?"
date: 2005-07-27
forum: Absolute Beginner Talk
---

### Post by sammyguy193 on 2005-07-27
I am trying to access on of my mounted storage drives as my regular user. everything is mounted correctly, but i cant see the drives when i go media:/ . 
Then i sudo konqueror and i can see everything and move, and copy and do whatever, but i dont want to sudo.. i just want to use my damn computer. so i tried to change the permissions, but it wont let me.  ](*,) sudp is pissing me off... i just wish i could set my username as root... that would take care of everything...:twisted:

---

### Post by frodon on 2005-07-27
Ok have you added some lines in your fstab file ?
Have you a NTFS ot FAT32 drive ?
what is the name of your partitions ? if you don't know```
sudo fdisk -l
```
Could you post here your fstab file and answer to the questions then I will give you the lines to add in fstab or correct the wrong one : ```
sudo gedit /etc/fstab
```You just have to put user parameter when you mount the drive to have user permissions.

---

### Post by poofyhairguy on 2005-07-27
[QUOTE=sammyguy193]I am trying to access on of my mounted storage drives as my regular user. everything is mounted correctly, but i cant see the drives when i go media:/ . 
Then i sudo konqueror and i can see everything and move, and copy and do whatever, but i dont want to sudo.. i just want to use my damn computer. so i tried to change the permissions, but it wont let me.  ](*,) sudp is pissing me off... i just wish i could set my username as root... that would take care of everything...:twisted:[/QUOTE]

Create a root user (look at the Ubuntu guide for that) and log in as that user, Windows style.

---

### Post by sammyguy193 on 2005-07-27
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       /archives       ext3    defaults        0       2
/dev/hda1       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


the partition i want to add is listed as hdb1 and it is an NTFS partition

---

### Post by poofyhairguy on 2005-07-28
look at this:

[http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)

---

