---
title: "D Partition gone"
date: 2012-08-04
forum: Any Other OS
---

### Post by SuperTocka on 2012-08-04
Hi everyone.. I'm new at linux so i wanted to try it. During installing Ubuntu it just stoped installing.. I tried it many times, same thing.. I even tried completely deleting Windows and install Ubuntu, same thing.. So i decided to put Windows XP back and i don't remember what i've done to fix that error but i did it.. I couldn't install Windows coz it says that Windows can't be installed at partition ntfs or fat32 something like that... So i fixed that problem on C drive and i don't remember anymore how... And now D partition is missing.. I'm thinking that the same problem is with it. I mean i need to convert it so D drive shows up in My computer but I'm not sure.. Does anymore experienced this before?
Sorry for my English..
P.S. I dont know if this is in right category place so please move it if needed..
Thanks!

---

### Post by Ubun2to on 2012-08-04
I'm confused. Do you have Ubuntu on your computer or not?
Windows can only read off NTFS and FAT32 partitions, so if you want to access your Ubuntu partition, good luck with that (unless you told Ubuntu to use NTFS rather than ext4).

---

### Post by oldfred on 2012-08-04
Welcome to the forums.

Really a Windows question, moved to other OS.

From liveCD you can post this to see your partitions.

sudo fdisk -lu

or a screenshot from gparted. You can use the paperclip icon in the edit panel to attach the sceenshot.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by SuperTocka on 2012-08-04
No i deleted Ubuntu coz it won't finish installation. I triedd many times but it just says it can't be installed at a half installation... So i deleted all and tried XP again its just theres no D partition anymore.. Not sure if Ubuntu installation convert it to something that Windows can't run it or something...

---

### Post by Ubun2to on 2012-08-04
> **SuperTocka said:**
> No i deleted Ubuntu coz it won't finish installation. I triedd many times but it just says it can't be installed at a half installation... So i deleted all and tried XP again its just theres no D partition anymore.. Not sure if Ubuntu installation convert it to something that Windows can't run it or something...

You probably don't have the D partition because you wiped the disk.
If it's a CD/DVD drive that it's not recognizing, that's a hardware problem, and it means you need drivers or you need a new CD/DVD drive.

---

