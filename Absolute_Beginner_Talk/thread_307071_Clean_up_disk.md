---
title: "Clean up disk"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by phelixnyc on 2006-11-26
I am new to Ubuntu, and using a Windows OS for a long time I've become so use too cleaning out my hard drive and defragmenting the drive all the time. My question is, is that necessary with Ubuntu and if so, how?

---

### Post by Gannin on 2006-11-26
No, it's not :).  You don't need to defragment your drive in Linux.  Welcome to Ubuntu.

---

### Post by kinematic on 2006-11-26
just a tip....localepurge and deborphan will get rid of any unwanted localisations and orphaned libraries.
also....fragmentation can happen(not to the degree you'd experience in windows)if you do a lot of torrent downloading and you don't pre-allocate space for the download.

---

### Post by xyz on 2006-11-26
This may be of help:
[Cleaning up all those unnecessary junk files...]("http://ubuntuforums.org/showthread.php?t=140920")

---

### Post by JurB on 2006-11-26
The amount of fragmentation that occurs in linux filesystems is minimal, the filesystem acctually does the defragmentation for you, you don't need to worry about it. 
However, the filesystem needs some amount of free space to defrag.
A harddrive that's close to it's limit of capacity will not be able to defrag .

---

### Post by xyz on 2006-11-26
This one may come in handy,too:
[Bonager: The Boot Scan Manager]("http://ubuntuforums.org/showthread.php?t=295262")
>  Bonager is an easy way to manage that unpredictable and sometimes very annoying disk scan that happens when the computer is turned on. 
To set check disk opttions, I also use the following command line:
```
sudo tune2fs -c 50 /dev/hdx**@**
```
where @ would be, for instance in my case, /dev/hda**2**...my Ubu partition.
The number "50" means it will ckfs at the 50th boot. Change that number to your liking.
Some more command lines...just in case:
```
fsck : check and repair a Linux file system
dosfsck : check and repair MS-DOS file systems
e2fsck : check a Linux ext2/ext3 file system
expiry : check and enforce password expiration policy
fsck.ext2 : check a Linux ext2/ext3 file system
fsck.ext3 : check a Linux ext2/ext3 file system
fsck.minix : a file system consistency checker for Linux
fsck.msdos : check and repair MS-DOS file systems
fsck.reiser4 : the program for checking and repairing reiser4 filesystem.
fsck.reiserfs : The checking tool for the ReiserFS filesystem.
fsck.vfat : check and repair MS-DOS file systems
hpfsck : check integrity of an HFS+ volume
reiserfsck : The checking tool for the ReiserFS filesystem.
xfs_check : check XFS filesystem consistency

```

---

### Post by AlphaMack on 2006-11-26
Baobab. ;)

---

### Post by phelixnyc on 2006-11-26
Thank you.

---

