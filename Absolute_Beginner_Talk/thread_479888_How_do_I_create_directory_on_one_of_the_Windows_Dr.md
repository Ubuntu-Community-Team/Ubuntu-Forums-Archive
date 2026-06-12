---
title: "How do I create directory on one of the Windows Drives"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by videocheez on 2007-06-20
I am running Feisty with dual boot.  Feisty is on one 74GB drive and the other 1.2TB are drives are the ones that  Windows XP Pro utilize.  My media is on a few of the 1.2TB drive space and I can play music and watch video from these drives fine in Feisty but I can't create directories or write files.  Of the 1.2 TB, all are NTFS except for one drive is FAT32.    Is there away that Linux programs such Nicotine can write to the drives that the Windows OS utilize?

Thanks in advance,

VC

---

### Post by drivel on 2007-06-20
If it's fat drive,create it normally,other,install ntfs-3g with command'sudo apt-get install ntfs-3g-*'

---

### Post by videocheez on 2007-06-20
Roger That!:D

---

### Post by videocheez on 2007-06-22
Ok.  I installed the program and the following message came ou on the terminal:

Setting up ntfs-3g (1.328-1) ...
Setting ntfs-3g suid root with group fuse...done
Users from 'fuse' group can now mount NTFS volume.

What is fuse group?  I still can't write to NTFS volume

thx in advance

VC

---

