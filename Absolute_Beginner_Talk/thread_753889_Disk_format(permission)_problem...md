---
title: "Disk format(permission) problem.."
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by _mOrgoth_ on 2008-04-13
So... I conected empty disk(WD40Gb) into my pc(runing Ubuntu 7.10). So I used gparted, it set disklabel msdos and after that I format it into ext3. Now I see disk under places and Computer, I can mount it bun not without superviser password. It say that disk is restricted??? So I can acses to it but can't create folders etc..nothing without sudo command.. Wtf?? Where I make mistake??

---

### Post by Michael.Godawski on 2008-04-13
Can you please post the outout of these terminal commands:

```
sudo fdisk -l
ls media -la
```

---

### Post by Polyrhythm_oly on 2008-04-13
im having the same problem

---

### Post by sisco311 on 2008-04-13
chown the disk.
```
sudo chown -R username:username /media/disk
```assuming that
username is your user name
/media/disk is the mount point of the disk

---

### Post by Polyrhythm_oly on 2008-04-13
Disk /dev/sda: 4310 MB, 4310433792 bytes
255 heads, 63 sectors/track, 524 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e1567

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         494     3968023+  83  Linux
/dev/sda2             495         524      240975    5  Extended
/dev/sda5             495         524      240943+  82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f3d0f3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14240   114382768+  83  Linux
/dev/sdb2           14241       14593     2835472+   5  Extended
/dev/sdb5           14241       14593     2835441   82  Linux swap / Solaris

---

### Post by Polyrhythm_oly on 2008-04-13
polyrhythmoly@ubuntu:~$ sudo chown -R username:polyrhythmoly /media/disk
chown: `username:polyrhythmoly': invalid user
polyrhythmoly@ubuntu:~$ sudo chown -R username:username /media/disk
chown: `username:username': invalid user
polyrhythmoly@ubuntu:~$ sudo chown -R polyrhythmoly:username /media/disk
chown: `polyrhythmoly:username': invalid group

---

### Post by _mOrgoth_ on 2008-04-13
Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001c0af

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4676    37559938+  83  Linux
/dev/sda2            4677        4863     1502077+   5  Extended
/dev/sda5            4677        4863     1502046   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00097f18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4863    39062016   83  Linux

on command ls media -la: no such file or directory

---

### Post by sayakb on 2008-04-13
I hope that you are running gparted as root: ```
gksudo gparted
```  Plus, try deleting the partition and creating a new one instead of formatting it.

---

### Post by Polyrhythm_oly on 2008-04-13
yeah i got that too

---

### Post by sisco311 on 2008-04-13
> **Polyrhythm_oly said:**
> polyrhythmoly@ubuntu:~$ sudo chown -R username:polyrhythmoly /media/disk
chown: `username:polyrhythmoly': invalid user
polyrhythmoly@ubuntu:~$ sudo chown -R username:username /media/disk
chown: `username:username': invalid user
polyrhythmoly@ubuntu:~$ sudo chown -R polyrhythmoly:username /media/disk
chown: `polyrhythmoly:username': invalid group

```
sudo chown -R polyrhythmoly:polyrhythmoly /media/<mount point>
```but first post the output from:
```
mount
```to get the correct mount point

It's an external or internal disk?

---

### Post by _mOrgoth_ on 2008-04-13
I tryed delete partition and creat new but nothing.. same thing as before. Then I downloaded Gparted live cd, but it can not start cause VESA or any other driver won't work with my gpu chip(think its intel 82851) LOL!!!!!
So.. this is my sudo fdisk -l:
Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001c0af

Device Boot Start End Blocks Id System
/dev/sda1 * 1 4676 37559938+ 83 Linux
/dev/sda2 4677 4863 1502077+ 5 Extended
/dev/sda5 4677 4863 1502046 82 Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00097f18

Device Boot Start End Blocks Id System
/dev/sdb1 1 4863 39062016 83 Linux

and this is ls -al /media:
a:~$ ls -al /media
total 20
drwxr-xr-x  4 root    root    4096 2008-04-13 14:31 .
drwxr-xr-x 21 root    root    4096 2008-04-12 19:12 ..
lrwxrwxrwx  1 root    root       6 2008-04-12 18:56 cdrom -> cdrom0
drwxr-xr-x  2 root    root    4096 2008-04-12 18:56 cdrom0
drwxr-xr-x  3 morgoth morgoth 4096 2008-04-13 12:02 disk
-rw-r--r--  1 root    root      44 2008-04-13 14:31 .hal-mtab
-rw-------  1 root    root       0 2008-04-13 13:54 .hal-mtab-lock

I tried sudo chown -R morgoth:morgoth /media/disk bud didn't help..

---

### Post by _mOrgoth_ on 2008-04-13
I resolved problem. First I used Partition magic boot cd. I creadted partition etx3 and enterd ladel SKLADISTE. After I enterd ubuntu same thing happend again. 
So I used this two commands
sudo chown -R morgoth:morgoth /media/SKLADISTE
sudo chmod 777 /media/SKLADISTE

now everithing works fine..

---

