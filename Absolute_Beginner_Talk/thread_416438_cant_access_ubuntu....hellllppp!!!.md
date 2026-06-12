---
title: "cant access ubuntu....hellllppp!!!"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by prateekkalyankar on 2007-04-21
Hey guys.... I recently installed ubuntu 6.06 on my machine on one partition and windows xp on another one. I installed windows AFTER I installed ubuntu 6.06. However, I am unable to access ubuntu. The OS choices menu does not appear and the system directly switches to windows xp. Please help!!!!!

---

### Post by Rui Pais on 2007-04-21
hi,
you need to recover grub.
Try this:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

good luck.

---

### Post by GSF1200S on 2007-04-21
> **prateekkalyankar said:**
> Hey guys.... I recently installed ubuntu 6.06 on my machine on one partition and windows xp on another one. I installed windows AFTER I installed ubuntu 6.06. However, I am unable to access ubuntu. The OS choices menu does not appear and the system directly switches to windows xp. Please help!!!!!

What exactly did you install windows with? Was it with an install disk or a recovery disc. If it was a recovery disk, you may have actually wiped your hard drive and installed Windows. Windows should be installed first before Ubuntu in order to avoid issues with the MBR.

If you did use a Windows install disc, then the post before this is the fix. If you used a recovery cd, you could use a gparted liveCD to make sure your Ubuntu partition still exists. If it does, fix the MBR. If not, then reinstall Ubuntu.

Good luck!

---

### Post by prateekkalyankar on 2007-04-23
hi there......
i have installed windows using an install disk. i had partitioned my drive while installing ubuntu and installed windows on the rest of the hard drive.

---

### Post by GSF1200S on 2007-04-23
> **prateekkalyankar said:**
> hi there......
i have installed windows using an install disk. i had partitioned my drive while installing ubuntu and installed windows on the rest of the hard drive.

Another words, you installed Windows AFTER you installed Ubuntu. 

What I would suggest is dowloading gparted and burning it as an ISO to a CD (link to website explaining this below). Then, reboot the computer and change the boot order to boot from CDROM.

Once Gparted is open DO NOT FORMAT ANYTHING! Just take a look at the partitions it lists and see if your Ubuntu partition is there (it will be an EXT3 partition). If it is, than you installing Windows messed up the MBR. As Ive never had this happen, I dont know how exactly to fix it. Do a few forum searches or make a thread listing your MBR as messed up and someone will help you.

If gparted doesnt show an EXT3 partition, than windows completely wiped the drive and installed itself. In this case, youll have to reinstall Ubuntu using the LiveCD.

Good Luck!

[http://www.brunolinux.com/01-First_Things_To_Know/Windows_Tools_-_Gparted.html](http://www.brunolinux.com/01-First_Things_To_Know/Windows_Tools_-_Gparted.html)

---

