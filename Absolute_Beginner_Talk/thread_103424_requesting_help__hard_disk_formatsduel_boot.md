---
title: "requesting help:  hard disk formats/duel boot"
date: 2005-12-14
forum: Absolute Beginner Talk
---

### Post by insub2 on 2005-12-14
i have:
~winXP sitting on a 4gb hard drive i used for a system drive while running XP.
~my personal files sitting on a 10gb (ntfs) hard drive.
~i have ubuntu installed as of now on a 120gb hard drive.
---those are physically seperate hard drives. not partitions.---

what i want to do:
boot up in winXP > format the 120gb > transfer personal files to the 120gb > reformat the 10gb into FAT32 > reinstall ubuntu onto the 120gb

the objective:
to have read/write capibilities on my personal files

the question:
how to i format in FAT32???

another question:
is it possible to set up a deul boot system if i were to, say, install ubuntu on a 20gb primary partition with a 100gb partition for files and a seperate hard drive (4gb) with winXP???  (by the by, i don't have a winXP disk of any kind...anymore)
AND if i where to do this, what format should the 100gb partition be to be accessed by both ubuntu and winXP?

---

### Post by Sokraates on 2005-12-14
The way you describe it, you want to create a FAT-partition before installing Ubuntu. So you will have to use XP for this. I remember haing the same problem with XP, namely ony having the option to format a drive as NTFS. I "solved" this by using a [Knoppix](http://www.knopper.net/knoppix/index-en.html) LiveCD. It has qt-parted installed and I used it to format the drive.

Regarding the other question: yes, it's possible. To be able to read and write the FAT-partition, follow [this](http://www.ubuntuguide.org/#automountfat) guide.

---

