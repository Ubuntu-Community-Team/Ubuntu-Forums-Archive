---
title: "Dual-Booting Ubuntu and Vista installing prob"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by jkalex05 on 2008-02-08
I know they are plenty of threads about this however I am a young and somewhat new computer user. I am 21 and have been using computers since I was about 10 years old.

I am a noobie to linux and ubuntu all together. I currently have 2 SATA hard drives. 1 hard drive currently has Vista 32bit Home Premium with all my games, files, and info.

When I tried to install on my second hard drive it was giving me an error.

I went the manual route. sda1 using ntfs has 500105mb with 113100mb used which is my main hard drive with vista installed.

Then I have sbd1 using ntfs has 500105mb available with 3200mb used so this has to be my unused HD.

So I picked the HD to install on and it gave me error No Root File system is denied. I want to mess around but don't want to screw up anything.

What do you all suggest? Thx from a noob!

---

### Post by smartboyathome on 2008-02-09
Try following [this guide]("http://ubuntuforums.org/showthread.php?t=678146"), it is for external hard drives, but I have a feeling that it will help you with your setup as well, since it is similar to that of an external hard drive.

---

### Post by bumanie on 2008-02-09
Your idea of using the manual option for partitioning was the correct way to go. However in linux, you need at least two partitions to install to. Firstly you need a / partition and you also need a swap partition. You should be able to choose these during the partitioning stage. It is also necessary to choose the to format in ext3 file system type. This guide should help you [http://img379.imageshack.us/my.php?image=feistydual10ea7.png](http://img379.imageshack.us/my.php?image=feistydual10ea7.png)
It is for ubuntu 7.04, but the partitioning is the same in gutsy. In addition to having a / and a swap partition, many users also make a /home partition for storing all their documents. That was if something happens to the essential / file system, you can reinstall and your documents are safe. If you choose this set up, 10g should be enough for / swap should 1-2x the amount of your ram and /home can be as much space as you wish to allocate.
Hope this helps and is clear.

---

