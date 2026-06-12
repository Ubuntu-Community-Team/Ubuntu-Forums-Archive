---
title: "format internal hard drive"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by will71110 on 2007-08-14
Is there a way to format a second hard drive using the terminal (something aleady built into Ubintu 7.04)?  My comuter is running ubuntu on a VM an dosnt have network connection so I cant get gparted.  Also I would like to mout this too.

---

### Post by dwisianto on 2007-08-14
try 
man fdisk 
man mkfs

---

### Post by will71110 on 2007-08-14
LOL....how do you get out of man after you enter it?

---

### Post by wolfen69 on 2007-08-14
```
sudo -s -H
```
```
sudo apt-get install gparted
```
run gparted. format.

---

### Post by will71110 on 2007-08-14
Like I said,  cant get gparted because I dont have a network connection. 

Ok I got Fdisk to partition the drive but now I cant get the type of format.  I want to put ext3 on it.

---

### Post by will71110 on 2007-08-14
Ok I discovered cfdisk but I cant seem to find ext3 on the list of type of file systems.

---

### Post by RomeReactor on 2007-08-14
Hi. Personally haven't used it, but maybe **mkfs.ext3** could help you:
```
man mkfs.ext3
```

---

### Post by will71110 on 2007-08-14
Ah haha...That worked...thanks...Here is what I did:

fdisk -l
  To list the drives. hdb1 was the one I wanted to format and mount.

cfdisk /dev/hdb1 
  To partition the drive (Put the type to linux(ext3 option 83) but it did not acctually make it fully ext3)

mkfs.ext3 /dev/hdb1
 To make the file system ext3

mkdir /media/harddrive2
 To make a directory for the harddrive

Mount -t ext3 /dev/hdb1 /media/harddrive2
 Mounted the harddrive

:)

---

### Post by will71110 on 2007-08-15
Also I another note on this.  The hard drive wont show up in the file system browser until you reboot. ;)

---

### Post by splintercellguy on 2007-08-15
> **will71110 said:**
> LOL....how do you get out of man after you enter it?

The letter q.

---

