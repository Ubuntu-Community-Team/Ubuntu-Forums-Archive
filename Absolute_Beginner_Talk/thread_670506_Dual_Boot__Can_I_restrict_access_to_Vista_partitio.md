---
title: "Dual Boot:  Can I restrict access to Vista partition?"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by TucsonTarheel on 2008-01-17
I have noticed that that I can access my Vista partition from my Ubuntu desktop and  file manager.   Is there any way to keep a user from being able to see/access other partitions on the HDD?   I'd like to install Edubuntu on my children's PC (which would also be dual boot), but I need to keep my 13 year old from being able to access the Vista side.   He likes to experiment and I know it wouldn't be long before he'd trash Vista.

---

### Post by forestpixie on 2008-01-17
Could be wrong and I'm sure someone else would say if that was the case

But I think only the first user get's to use sudo, if you made a user for the inquisitive one after you did your's 

Then make sure the partition isn't in tour fstab - it wouldn't get mounted at start, but you could through nautilus with sudo rights.

At least it appeared that way with mine before I put the partition in the fstab file

---

### Post by apothecaryaaron on 2008-01-17
I think this should accomplish what you are asking:

First, make a backup:
```
sudo cp /etc/fstab /etc/fstab.bak
```Then, edit the fstab:
```
gksudo gedit /etc/fstab
```Should look something like this:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=dd59cd89-f140-4389-8e75-665ce0240fb0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=54D41059D4103FA2 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb3
UUID=B0CF-61B5  /mnt/share      vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sdb2
UUID=ee1d4159-3a31-4b1a-8ce4-417c84646a9f none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```I would just comment (add a #) out the ntfs partition and see how that does.  It should keep it from mounting automatically and require sudo password to do it manually.

---

### Post by forestpixie on 2008-01-17
a bit more detailed than mine then :) , effectively I guess that as long as you don't comment the partitions relating to ubuntu you can comment out as many as you like

if you're not sure which partition to amend use fdisk to show your partitions

```
sudo fdisk -l
```

but it does depend on the ability of second user to use sudo or not
just wondering if there's a more elegant solution to it

---

### Post by TucsonTarheel on 2008-01-17
> **apothecaryaaron said:**
> I think this should accomplish what you are asking:

First, make a backup:
```
sudo cp /etc/fstab /etc/fstab.bak
```Then, edit the fstab:



DUH! ](*,)  I should have remembered fstab!   Thanks!

---

