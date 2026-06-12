---
title: "Format Hard Drive"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by bena on 2007-03-22
I have a second hard drive set up as a slave.  It is formatted in NTFS.  I want to be able to use this hard drive with Linux.  Is there a program out there I can get to format this hard drive to ext3 so that I can mount it in Linux?

---

### Post by justleen on 2007-03-22
try gparted, id say..

---

### Post by floke on 2007-03-22
You can use the GParted utilty from the LiveCD, or as part of a system rescue disk.

See: [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

---

### Post by anaconda on 2007-03-22
or from the terminal with:
sudo mke2fs -j /dev/hdaX

just change the hdaX to be the right partition.. might be sdaX if you have a sata-hd. and the X is a number..
if you type:
sudo fdisk -l
you will see which partition is which..

---

### Post by indytim on 2007-03-22
-or-

you can download and burn the iso for a LiveGParted 

[GParted]("http://gparted.sourceforge.net/index.php")

options - options and more options :) 

IndyTim

---

### Post by bena on 2007-03-22
I tried Gparted from the LiveCD and it said that my hard drive which is /dev/hdb1 was formatted as ext3, however when I restarted the computer and went into terminal and did: sudo fdisk -l, it said:  

Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       10586    80030128+   7  HPFS/NTFS

Why is is still saying that it is NTFS?

---

### Post by taurus on 2007-03-22
```
sudo umount /dev/hdb1
sudo mke2fs -j /dev/hdb1
sudo fdisk -l
```

---

### Post by Rhubarb on 2007-03-22
GParted will only let you view / change partitions of one physical hard disk at a time.
So you where probably looking at the master hard drive, which would've been formatted as EXT.

In the top right hand corner of GParted you can select which drive you wish to view.

---

### Post by bena on 2007-03-22
rhubarb:  If I am not mistaken, I did click on the other hard drive in the corner and it said ext3.  

taurus:  I tried that and it still said HPFS/NTFS

---

