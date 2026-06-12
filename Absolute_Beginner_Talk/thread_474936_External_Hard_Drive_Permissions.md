---
title: "External Hard Drive Permissions"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by Phalangees on 2007-06-15
I have an external hard drive that I can't change permissions on. It's set that I can read, write, and execute but others can't read which is what I would like to be able to do. I've tried right clicking on the folder I want to change permissions for and clicking the Others: Read checkbox and it checks for half a second and then unchecks itself. I'm not double clicking or doing anything like that. Any help would be great. Thanks!

---

### Post by Inxsible on 2007-06-15
you probably need to take ownership. The owner is probably root and so its not allowing you to change anything. You can take ownership by the following command:
 
```
sudo chown -R <your username>:<your group> <device mount path>
```
 
post the output of ```
sudo fdisk -l
``` and ```
gksudo gedit /etc/fstab
```
 
This will help us give you a proper command to change ownership.

---

### Post by Phalangees on 2007-06-15
When I right click on the /media/HD PART/ and go to permissions I am the owner and it's under my group.

sudo fdisk -1 output (the external hard drive part)
```
Disk /dev/sda: 159.9 GB, 159909916672 bytes
255 heads, 63 sectors/track, 19441 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19442   156161770    c  W95 FAT32 (LBA)

```

The contents of my fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdd1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdd5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

Thanks for your help!

---

### Post by Phalangees on 2007-06-15
Does anybody know?

---

### Post by Phalangees on 2007-06-18
Seriously?? Nobody knows how to change permissions on an external hard drive? Please help me out.

---

### Post by _Agrajag_ on 2007-06-22
I'd like to know how too.  Anybody?

---

### Post by alan tait on 2007-08-23
I've been having similar problems (except Feisty only lets me read my external NTFS disk). Having read a million of these posts, and getting nowhere, I've got to a workaround using ntfs-3g and ntfs-config from Synaptic - I needed both BTW. Search this forum for more details. 

Now after connecting the drive, I open Applications>System Tools>ntfs Configuration Tool once, and I can write. :) I still have to unmount from terminal, though.

---

