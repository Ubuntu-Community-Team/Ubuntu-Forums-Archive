---
title: "testDisk"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by rfmChile on 2007-10-19
Hi, I have a big big problem with my hard disk, I have Ubuntu Feisty and can not mount file system on boot then  booted my pc with live cd of knoppix and run testdisk, I can see my disk, but i can not mount it and the command fdisk - l show nothing.
I tried with fsck /dev/hbd1 and e2fsck -b 8193 /dev/hbd1 but nothing 
I think that the problem is the partition table, but I don't know as repair this with testDisk.
the partition has ext3

any idea?
thanks in advanced
Rodolfo

---

### Post by MinstrelBoy on 2007-10-19
I wouldn't try repairing anything until you've tried to backup your data with testdisk.
Type sudo testdisk into terminal and analyse the faulty disk. You should then be able to copy off all your files onto another disk, ie ext usb drive or second hdd.
Remember, if you can, backup your data first, just in case things go wrong.

---

### Post by rfmChile on 2007-10-19
Sorry, but how I can backup my data with testDisk? , I can't mount the disk , the mount command show this error

# sudo mount -t ext3 /dev/hdb1 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/hdb1
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so


thanks
Rodolfo

---

### Post by Pumalite on 2007-10-19
Gparted Lice CD also has software to check and fix your drive. I don't remember the commands, but they are in the Manual:
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

---

### Post by Pumalite on 2007-10-19
If that doesn't work, try rescuecd: [http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)
[http://www.sysresccd.org/Online-Manual-EN](http://www.sysresccd.org/Online-Manual-EN)

---

### Post by MinstrelBoy on 2007-10-19
You don't need to mount the disk before running testdisk.
From memory ...
sudo testdisk
choose the drive
Analyse
P  to list files
C  to copy files to another drive

---

