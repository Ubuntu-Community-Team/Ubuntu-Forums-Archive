---
title: "Boot problem -- after deletion of window partition and installation of Ubuntu"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by aas452 on 2007-10-07
Hey all

I am a new user to Linux and after getting everything I needed to work a few days ago,l I decided to completely delete the windows partition.

I then deleted and reloaded Ubuntu on to my system.

But now I receive an error when I boot which seems like a system freeze. The word GRUB continuously loops on the display. So I  inserted the CD again and the only thing which took me into the GUI is if I choose the last option on the CD -- to boot from the FIRST DISK. 

Has anyone had a similar error or solution/direction to the solution to this problem???

---

### Post by jovannicabanag on 2007-10-08
> **aas452 said:**
> Hey all

I am a new user to Linux and after getting everything I needed to work a few days ago,l I decided to completely delete the windows partition.

I then deleted and reloaded Ubuntu on to my system.

But now I receive an error when I boot which seems like a system freeze. The word GRUB continuously loops on the display. So I  inserted the CD again and the only thing which took me into the GUI is if I choose the last option on the CD -- to boot from the FIRST DISK. 

Has anyone had a similar error or solution/direction to the solution to this problem???



You've mentioned that you remove Windows OS from your HD then also you deleted the partition.
You need to create a new one partition then format the HD.
Try to use the program part240 which is downloadable from the Internet.

Turn on pc go to CMOS. change the boot sequence, make sure that you are going to point the boot to A:
Insert the disk where the program part240 is saved and run the program.

part240 will provide you options on how much amount of HD that needs to be partitioned.
then Format the partitioned drive.

---

### Post by aas452 on 2007-10-12
Does this mean I have to re-install windows to run the .exe, or do I have to save this file on a disk and run it when I boot???

---

