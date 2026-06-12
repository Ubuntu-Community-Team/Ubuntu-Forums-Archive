---
title: "Ubuntu killed Vista??"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by munch3 on 2008-03-01
I had Vista Ultimate on one partition and a broken XP on another one.I formated the partition  on wich XP was so I got free disc space.I made a SWAP partition, and an ext 3 partition on wich I installed ubuntu.Later, Ubuntu automaticaly runs without grub, and without asking me if I want to boot Vista.So HOW DO I BOOT VISTA NOW

---

### Post by click4851 on 2008-03-01
I've had good luck with LiveCD version of the Super Grub Disk for setting up something like that.

---

### Post by Baelari on 2008-03-01
oh, hey, this is the question to the answer I posted here :
[http://ubuntuforums.org/showthread.php?p=4435993&posted=1#post4435993]("http://ubuntuforums.org/showthread.php?p=4435993&posted=1#post4435993")

someone will probably be able to tell you exactly what to do, though

---

### Post by ugm6hr on 2008-03-01
First thing - are you sure you didn't over-write Vista?
```
sudo fdisk -l
```
This will list you partitions to ensure Vista's is still there (PS: lowercase  L not 1)

If it is, GRUB has just forgotten to include Vista in the menu.

Post the contents of the file /boot/grub/menu.lst here for us to look at and edit for you.

Remember that you can access the GRUB menu by pressing Escape (I think) as GRUB loads.

---

