---
title: "MY slave drive"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by kingvicious on 2006-08-04
i get an error when i try to open my locol disk drive can someone help me mount it? i didnt really understand the guides for the partitions very help i got this error when i try to open it tho

error: device /dev/hdb1 is not removable

error: could not execute pmount

---

### Post by Tomosaur on 2006-08-04
try this:

sudo mkdir /media/hdb1
mount /dev/hdb1 /media/hdb1

---

### Post by rck_hitokiri on 2006-08-04
try this site. aysiu has a lot here. it helped me before and im sure it'll prove usefull for you. [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by kingvicious on 2006-08-04
how do u save the file after opening  sudo nano /etc/fstab ?
i got it all edited but i cant save this file after opening it in the terminal

---

### Post by FsFrey on 2006-08-04
I think F3 will save the file.

---

### Post by rck_hitokiri on 2006-08-04
ctrl x to save the nano.... then sudo mount -a

---

### Post by kingvicious on 2006-08-04
mmm when i tryed the mount command i got this error 

[mntent]: line 5 in /etc/fstab is bad

---

### Post by kingvicious on 2006-08-04
ok ok i made a few changes and i thought i had it but when i did the mount command i got this..

kingvicious@kingvicious:~$ sudo mount -a
mount: /dev/hda1 already mounted or /windows busy
mount: according to mtab, /dev/hda1 is mounted on /
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by kingvicious on 2006-08-04
well since no one is responding iam guessing that no one knows so mybe if i give more info i can get some help ok when i put sudo nano /etc/fstab in my terminal and went to that thing to edit this is how i edited it( its the code at bottom) let me know if i did it right... which iam guessing i didnt.
also when i try to open my local disk i get this error.
mount: only root can mount /dev/hdb1 on /fat_files



# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>                <dump>  <pass>
proc            /proc           proc    defaults                 0       0
/dev/hda1       /windows        ntfs    nls=utf8,unmask+022      0       0
/dev/hdb1       /fat_files      vfat    iocharset=utf8,umask=000 0       0
/dev/hda5       none            swap    sw                       0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto          0       0

---

