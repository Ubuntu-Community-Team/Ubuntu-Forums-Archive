---
title: "Problems mounting USB devices."
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by Captainm on 2007-04-27
I realize that this has been posted before and I tried most of the stuff there, but I can't seem to make USB devices work. I have a pendrive and an external hdd both not working. They used to be recognized when plugged in at startup but that has stopped too recently.

Here's my fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=26bb4a20-bbdb-40b5-aaad-29ac20fd5b83 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=7C7814E57814A046 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=d47f5c26-ab46-f699-3290-438638525103 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdb       /media/IOMEGA_HDD vfat   noauto,owner,kuzu 0       0
```

/media/IOMEGA_HDD is one of the devices I'm trying to mount, the other one isn't listed. 

I thought I got the whole mounting thing but apparently not.

Could somebody help me get these damn things mounted?

---

### Post by Captainm on 2007-04-27
Bump.

---

### Post by Captainm on 2007-04-27
I realize that this question has been posted but I just can't figure it out. There must be someone on here who can help me.

---

### Post by mikeyphi on 2007-04-27
Presumably you've checked the boxes under Preferences - Removable Drives andMedia?
If the drive shows under Places - Computer....right-click and select mount volume.
If none of the above: open a terminal and type
Quote
ls -1 /dev/sd*
this should tell you which drives are available...note the appropriate name sda1/sdb1/sdc1 etc...and type
Quote
sudo mount -t vfat /dev/sd** /mnt

---

### Post by Captainm on 2007-04-27
Haha, that's funny. I tried ```
sudo mount -t vfat /dev/sdb1 /media

``` (media instead of mnt) And now all my mounted drives disappeared. Only root and my CD drive are there. At least something happened. The ext. hdd did show up in /media but I couldn't mount it by right clicking because I didn't have the user rights.

---

### Post by dentaku65 on 2007-04-27
> **Captainm said:**
> Haha, that's funny. I tried ```
sudo mount -t vfat /dev/sdb1 /media

``` (media instead of mnt) And now all my mounted drives disappeared. Only root and my CD drive are there. At least something happened. The ext. hdd did show up in /media but I couldn't mount it by right clicking because I didn't have the user rights.

I have the same problem, I fill a bug in launchpad...
[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/110555](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/110555)

...I think that between hal and usb there is some problems....

---

