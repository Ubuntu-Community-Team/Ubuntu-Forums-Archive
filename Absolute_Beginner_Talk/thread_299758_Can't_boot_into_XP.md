---
title: "Can't boot into XP"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by JustinW on 2006-11-14
Well, I installed Ubuntu from the live CD, chose the first option, went with 20gb. etc.
I turn on my PC after getting home from school to do my homework, I choose XP on bootscreen, but nothing happens! I just get a black screen with the loading text.
Help please :(
EDIT: I'm currently using edgy 6.10

---

### Post by grim918 on 2006-11-14
You need to give us more information.

Have you booted into Ubuntu successfully?

If you have booted into Ubuntu successfully then open up a terminal and type in```
sudo fdisk -l
```
This should give you a list of the partitions on your disk. You should see a partition with a file system of NTFS. If you don't then that means that you may have deleted it. I doubt you deleted it since its listed on the grub menu.

---

### Post by BarfBag on 2006-11-14
What kind of text do you see?  Do you get an error message, or does it just hang?

Do you have your XP CD?  You might have to boot off of it and repair your installation.  Problem is - this will probably clear your MBR, which will erase Grub.

---

### Post by JustinW on 2006-11-14
grim918, yes, I can boot into Ubuntu great, here is the fdisk info :
```
   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2645    21245931    7  HPFS/NTFS
/dev/hda2            2646        9569    55617030   83  Linux
/dev/hda3            9570        9733     1317330    5  Extended
/dev/hda5            9570        9733     1317298+  82  Linux swap / Solaris

```
BarfBag, when I try to boot it, there is a normal boot message, then it just sits and does nothing.
I think I have my xp cd somewhere though, but I'm going to try this first.

---

