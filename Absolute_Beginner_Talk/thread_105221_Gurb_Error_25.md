---
title: "Gurb Error 25"
date: 2005-12-17
forum: Absolute Beginner Talk
---

### Post by saabirsa on 2005-12-17
Hello All,
 
I have just finished installing the first part of the Ubuntu installation, and after it says to remove the CD and reboot, it says,
 
>  
GRUB Loading Stage1.5
 
 
 
GRUB Loading, please wait...
(It takes about half an hour here)
Error 25

 
Anyone know how to resolve this? (PS, This is my first time installing Linux, be gentle ;).)
 
Thanks
Saabir Salim

---

### Post by fannymites on 2005-12-18
Did you do a default or expert install?
Do you remember where you told it to install grub?  master boot record or a partition?
Are you using one or more drives or more than one partition and where is ubuntu 
located on the drive?

---

### Post by amohanty on 2005-12-18
From the grub [manual]("http://www.gnu.org/software/grub/manual/grub.html#Stage2-errors"):

> 25 : Disk read error
    This error is returned if there is a disk read error when trying to probe or read data from a particular disk. 

In addition to fannymites (do you really mean what I think you mean :) ) questions also post:

1. Configuration of your hard drives and partitions?
2. What hdd and partition has what os?
3. (optional) Boot off of a live cd and post the output of:
```
fdisk -l
```

---

### Post by saabirsa on 2005-12-18
[quote=fannymites]Did you do a default or expert install?
Do you remember where you told it to install grub? master boot record or a partition?
Are you using one or more drives or more than one partition and where is ubuntu 
located on the drive?[/quote]
 
Defaullt Install,
Master Boot Record,
1 Drive, main drive
 
Thanks for all your help, now im off to download the liveCD and see what happens :smile:
 
Saabir Salim

---

