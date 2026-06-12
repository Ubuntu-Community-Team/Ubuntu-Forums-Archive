---
title: "Can't install Ubunto on partitioned space"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by JerseyDevil1111 on 2008-01-25
I am attempting to install Ubuntu on a hdd partition. I have two partitions on the drive  but when I try to install UB on the partition I get a root file system not present error. The partition is allocated as G drive and is empty.

---

### Post by taurus on 2008-01-25
Right now, you probably have that partition mounted to something like /media/sda2 (or whatever the name of the drive is).  You need to mount it to /.

---

### Post by stoodleysnow on 2008-01-25
Have you formatted the partition as Ext3, do you have any Swap space on your hard drive?
Because if you formatted it as NTFS, instant explanation is right there.:)

---

### Post by logos34 on 2008-01-25
Are you using the 7.10 live cd?  'Guided' or 'manual' partitioning option?  Windows on other partition?  More details

---

### Post by JerseyDevil1111 on 2008-01-25
It's NTFS and mounted sda... as above. How do I change that? Can I use the Ubuntu disc  and how long will it take?

---

### Post by logos34 on 2008-01-25
Try this (from the live cd):

>applications>accessories>terminal

sudo gparted

if the partition is mounted ('padlock' symbol), right-click on it>unmount

delete the partition and exit gparted

Now click on the desktop 'install' icon...choose 'guided' install on largest continuous free space.  It wil make a ext3 / and /swap in the empty space formerly occupied by G:

---

