---
title: "Adding a new harddrive"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by tprzepiorka on 2006-08-17
Hello there,
I recently switched to Ubuntu from windows :D. When I was running windows the two harddrives  I have connected to my computer showed up, but when I switched to Ubuntu only one is there :confused: How can I add that harddrive so it displays under Computer as I am running out of space :(. Thanks,
TP

---

### Post by it.henrik on 2006-08-17
its easier to help if you give some more information like, is it a NTFS disk? 
what kind of harddrive, sata? ide? 
did you give it a mount point during the installation? 

I believe NTFS wont become mounted after an installation .. you have to mount it your self by hand becuase M$ wont give out specs. on NTFS. 

There are solutions to the problem, just search for 

NTFS mount

and you will find that you are not alone (if this is the case)

---

### Post by zxee on 2006-08-17
In a terminal type sudo fdisk -l post the output and have a look at and/or post your fstab. Sometimes you might figure out how to get the drive automounting by looking at how your current drive is listed in fstab. (/etc/fstab)

---

### Post by David Corrales on 2006-08-17
In which format is your other hard drive? NTFS, FAT32? How many partitions?
Edit: Bah, I was too slow posting :(

---

### Post by b_martinez on 2006-08-17
First, you need a way to mount and check disk geometry. GParted does well, but I do not know if it is available in Ubuntu repos. QTParted does as well, but is generally for KDE window system. If your OS can see it, these tools will help you to format and mount them.
You may even be able to use fdisk, I'm not that familiar with the *buntu system I have, so I don't know.

code
sudo fdisk -l

may work, but no guarantees. If it does, then 
code
sudo fdisk /dev/hdb
then "p" key to print out [show] the existing geometry of the disk

Your best bet would be to install GParted if you can. 
Bill
oops, type too slow.
Bill

---

