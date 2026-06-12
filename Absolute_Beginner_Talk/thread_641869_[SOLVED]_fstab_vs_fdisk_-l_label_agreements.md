---
title: "[SOLVED] fstab vs fdisk -l label agreements"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by mikebravo on 2007-12-15
I did a manual install off the Fiesty live disk to two clean hard drives. My boot drive is a SATA 340gig and the other is a 40 gig PATA. On the boot drive I put a /windows VFAT partition for future sharing on a local network. That all went well, I am using said computer right now. Just for the hell of it I also used PartedMagic to put a small NTFS partition on an unallocated part of the PATA.

QUESTION 1- why is it that sudo gedit /etc/fstab say that /windows is on sda10, but sudo fdisk -l implies that /windows is on sdb10 ?  sda, sdb seems to conflict for all entries on those two screens, it just happens that the /windows partition was the easiest to identify.  Is this a condition I need to fix? 

QUESTION 2 - Why is the NTFS partition the only drive to show up on the desktop "Places" drop down menu?  What I would really like to do is make some of the other partitions, especially /windows show up on the "places" menu or on the desktop.

---

### Post by thelatinist on 2007-12-15
Any time you're asking questions about partitioning or mounting it is a good idea to post the complete results of

```
sudo fdisk -l <-- lower case letter l, not number 1
cat /etc/fstab
```

Chances are that's the first question anyone trying to help you is going to ask.

---

