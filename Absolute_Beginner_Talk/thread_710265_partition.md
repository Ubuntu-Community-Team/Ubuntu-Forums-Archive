---
title: "partition"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by phanipalagummi on 2008-02-28
1. now i am very new to linux
but i know little bit of linux file hierarchy
now please tell me the wrong what i had done in this partition

/ 20GB
/usr 20GB
swap 2 GB


2. is it i should give the mount point for 
linux specific partition (ext 2)
if at all yes then how to give a linux partition such way that
all the data i put in that drive should not go to any specific dir
(by data i mean books,songs,photos,exe files of some softwares etc)

please reply to two of my questions

---

### Post by taurus on 2008-02-28
1.  Personally, I would go with this

/ -- 20GB
/home -- 20GB
swap -- 2GB

2.  If you want to mount another partition so you can store your personal files, you need to add an entry in /etc/fstab and if it is ext2/ext3, then you can change the ownership of the mount point from root to your login name so you can write to it anytime you want.

---

### Post by clb137 on 2008-02-28
HI,

First welcome to linux,

1.Why do you think you have done something wrong?

2.How are you trying to install the lunux software?

3.You can store data where you like as long as your system is set up for it

Before more specific help can be giving, I need to know excatly what your problem is

thanks

Clint

---

### Post by spamzilla on 2008-02-28
> **phanipalagummi said:**
> 1. now i am very new to linux
but i know little bit of linux file hierarchy
now please tell me the wrong what i had done in this partition

/ 20GB
**/usr** 20GB
swap 2 GB

Change /usr to /home as this is where you save all your personal info, not /usr

> 
2. is it i should give the mount point for 
linux specific partition (ext 2)
if at all yes then how to give a linux partition such way that
all the data i put in that drive should not go to any specific dir
(by data i mean books,songs,photos,exe files of some softwares etc)

please reply to two of my questions

The way Ubuntu works is that by default you cannot change or write any files into the filesystem (excluding your /home folder) due to security reasons. This means you cannot write anything to the file system without root permissions. However, since you have the permissions to write to your /home folder, this is where you will save all your pictures, docs, info, pr0n etc :)

As for the mount points:

/root - mount point is simply "/" and filesystem is ext2 (or what ever you choose)

/**home** (I believe you mean /home here) - mount point is "/home"

/swap - mount point is /swap or linuxswap

---

