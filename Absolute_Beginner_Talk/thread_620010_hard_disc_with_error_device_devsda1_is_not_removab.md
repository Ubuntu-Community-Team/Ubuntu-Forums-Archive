---
title: "hard disc with error: device /dev/sda1 is not removable"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by patricio.ivan on 2007-11-22
I have a HP tx 1215 nr, 160 hard disc, 1 Gb RAM and AMD turion64 x2.
the computer has two partition , 160 Gb windows vista and 9 Gb to recovery

when I used ubuntu from live CD I can't  access to my window partition ( my hard disc ) this is the message that I get from ubuntu   

error: device /dev/sda1 is not removable
error: could not execute pmount

Addtionally, if I go to system/administration/disc and I enable then window partition the I can't get into because I don't have permiss, the message is

You do not have the permissions necessary 
to view the contents of "disks-conf-sda1".

On other hand, If i tried to install ubuntu 6.06  configuring the partition or even autmatically the computer report and error and it doesn't follow with the partition process.  I can't install Ubuntu =(.

I want Ubuntu in my laptop!!.  I appreciate any help to resolve this issue!!!!, thanks

---

### Post by u-slayer on 2007-11-22
try

mount | grep sda1 to see if you're hard drive is already mounted. If not, mount it with:

```
mount /dev/sda1 /mnt -t ntfs-3g
```

---

