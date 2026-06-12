---
title: "[SOLVED] Resizing Partitions"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by tranquito on 2007-11-24
Hi there,

I recently installed Ubuntu as a dual boot with Windows XP. Although both OS are not on the same drive, my entire music and film collection was on the drive I wanted to use for Ubuntu. Because of this, I partitioned that drive leaving its music etc contents in an NTFS file system with quite a bit of space left over. I now want to bring these files to my Ubuntu partition but in order to that I have to decrease my storage drive size. This is the problem, while using GPArted the oftion for resizing the NTFS partition is "greyed out"!! Why don't I have sufficiant privilages to do this?

Thanks in advance to anyone who can help.

---

### Post by ag65151 on 2007-11-24
In order to use GParted to resize any parition, the partition must be unmounted. If you are running Ubuntu from your hard-drive, it is mounted. Use GParted from the LiveCD and you should be able to do everything you want to do.

---

### Post by markharding557 on 2007-11-24
download gparted livecd,this will allow you to do what you need without worrying about what's monuted or whatever link below
[http://gparted-livecd.tuxfamily.org/]("http://gparted-livecd.tuxfamily.org/")

---

### Post by tranquito on 2007-11-27
Thank you, that worked perfectly!:KS

---

