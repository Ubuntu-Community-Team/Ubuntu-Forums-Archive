---
title: "Install OS X after Kubuntu dual boot"
date: 2010-06-23
forum: Apple Hardware Users
---

### Post by raafe on 2010-06-23
Hi all,

Having successfully installed kubuntu 10.04 on my Powermac G5 i was wondering if i can install os x and dual boot, there are plenty of tutorials around but all of them involve installing kubuntu on a system with os x already installed. If there is any danger of damaging Kubuntu then i will leave it as i really don't want to go through the hell of getting it working properly again! Also i have plenty of hard drives kicking about - would it be safer/easier to install os x on it's own hard drive? And if so how would things work with yaboot?

Thanks in advance

---

### Post by linuxopjemac on 2010-06-23
You need free space on a hard disk to accomplish that. It won't be easy, in case you used the whole drive, to make space for osx. I would then go for another drive.

---

### Post by Frobber on 2010-06-23
The reason you need to install OSX first is the OSX installation disk checks the MBR and cleans it of anything not apple.

I've installed using multiple partitions, formating the second partition for OSX, and other partitions HFS+ (osx extended non-journaled). this allows yot to format the first partition ext3 or 4 to support Linux; and, use another HFS+ partition for 'data' leaving the first and second partitions only for their respective OS and apps.   

During this type install Yaboot searches the hard drive for additional OS's and creates a menue to support.

Atter this type install, if the OSX install disk is used again for any reason, this record is cleaned and you need to reinstall Linux.

---

