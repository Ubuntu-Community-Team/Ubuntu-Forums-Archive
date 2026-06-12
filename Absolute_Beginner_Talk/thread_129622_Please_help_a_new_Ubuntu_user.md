---
title: "Please help a new Ubuntu user"
date: 2006-02-14
forum: Absolute Beginner Talk
---

### Post by JFlindt on 2006-02-14
Hi everyone...

I've just recently switched to Ubuntu and I'm using it as well as Win XP Pro.
I've made a dual-boot on my laptop (because many of the programs I use in school doesn't work on Ubuntu).

_But anyway back to my question:_
When I installed Ubuntu I made a partition (FAT32 of course) so I could move documents and files between Ubuntu and XP Pro.
But my default user can't write to the partition (since only root is able to write to the partition) and I can't change the permissions on the drive.
I've tried as my "regular default" user, as sudo and as root but nothing works.
I also tried the chown command but that didn't work either.

Can anyone give me a clue to how I make it possible to write to the drive?

_Permissions:_
*drwxr-xr-x  4 root root 4096 1970-01-01 01:00 dual-stash/*

---

### Post by frodon on 2006-02-14
you should post here your fstab file : ```
sudo gedit /etc/fstab
```And you should add/modify the corresponding fstab line like that : [http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)

---

### Post by wcks48 on 2006-02-14
i got the almost same problem with you. but something worst actually. that means, both windows and kubuntu cannot detect my third partition (1st for windows, 2nd for linux), which i made it as Fat 32 during the installation of Kubuntu.

---

### Post by JFlindt on 2006-02-14
_**My fstab looks like this:**_
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                /proc           proc    defaults                                    0       0
/dev/sda2       /                  ext3    defaults,errors=remount-ro     0       1
/dev/sda7       /boot           ext3    defaults                                    0       2
**/dev/sda8       /dual-stash  vfat    defaults                                    0       0**
/dev/sda5       /home          ext3    defaults                                   0       2
/dev/sda1       /media/sda1     ntfs    defaults                                0       0
/dev/sda6       none            swap    sw                                            0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto               0       0

The /dual-stash marked with bold is the one I want to be able to write to.
(Didn't get the answer you posted- sorry but as my signature says I'm a n00b so I'm not so good as this yet.)

---

### Post by rmjokers on 2006-02-14
Basically, you need to change that line to look like this:

/dev/sda8 /dual-stash vfat iocharset=utf8,umask=000 0 0

Then unmount/remount the drive:

sudo umount /dual-stash
sudo mount /dual-stash

---

### Post by JFlindt on 2006-02-14
Okay I'll try that.

Thanks man.

---

### Post by dvarsam on 2006-02-14
I honestly have never tried to install BOTH Ubuntu & Windows on one Hard Drive.

And I am new at Ubuntu also...

However, I have read some past articles about this, & they suggest that when you create a FAT32 partition to **create it** from Windows & NOT from Kubuntu.

I do not know though, if this will help solve your problem.

Hope I Helped.

---

### Post by veniceanonymus on 2006-02-14
try this: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/) , scroll down and choose FAT 32 or NTSF. Also check the bottom page of sticky note: Is Ubuntu for you?

---

### Post by veniceanonymus on 2006-02-14
Read also, 'Windows Partitions' in the Ubuntu 5.10 Starter guide in your 'Help' menu in your top panel on your desktop (System menu - Help - Ubuntu 5.10 Starter Guide - Windows partitions). Hopefully will give you some usefull hints.

---

### Post by JFlindt on 2006-02-14
[QUOTE=dvarsam]I honestly have never tried to install BOTH Ubuntu & Windows on one Hard Drive.

And I am new at Ubuntu also...

However, I have read some past articles about this, & they suggest that when you create a FAT32 partition to **create it** from Windows & NOT from Kubuntu.

I do not know though, if this will help solve your problem.

Hope I Helped.[/QUOTE]

I did use Windows to make the partition so that didn't work as planned but **rmjokers** hint did the trick so it works like a charm now. But thanks for replying.

---

