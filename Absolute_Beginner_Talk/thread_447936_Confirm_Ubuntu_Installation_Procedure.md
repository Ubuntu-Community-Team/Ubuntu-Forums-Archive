---
title: "Confirm Ubuntu Installation Procedure"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by S15_88 on 2007-05-18
I am currently in the process of downloading Ubuntu 7.04 (Feisty Fawn) Desktop CD (i386).  I am wondering if anyone can confirm the following steps that I will take as proper ones and any problems that may arise during this process.

Burn as ISO Image on CD

Boot from CD using Dell Inspiron 640m
Specs:
Intel(R) Core(TM)2 Duo processor 2.00GHz
2GB Dual Channel DDR2 SDRAM
160GB Hard Drive
Intel 945GM Graphics
14.1" Wide XGA+ Resolution 1440 by 900
Intel Wireless Next-Gen + Bluetooth

Then install, no idea what errors my occur at this step as i am not there yet.  But if anyone could give me a heads up about any before hand that'd be great! Also do I need to have my hard drive partitioned before the install or does Ubuntu have a partition program that allows you to make these changes during the install?

Thanks, Alain

---

### Post by Happy_Man on 2007-05-18
Ubuntu will let you partition before install, and you look A-OK! Go ahead and boot up the LiveCD.

---

### Post by chamberlain2006 on 2007-05-18
From what I can tell, the only thing that will cause you a bit of problems is the wireless, but it's fairly easy to overcome.

---

### Post by carlosqueso on 2007-05-18
Ubuntu has a partitioner, although if it gives you problems, you can always use the gparted live cd to do your partitioning.  One peice of advice...make sure that you have a seperate partition for /home (this should be your biggest one), as it'll make recovery from system screw-ups a lot easier.

---

### Post by mikewhatever on 2007-05-18
Look at the pictures to get familiar with the installation process:
[http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Good luck and welcome.

---

### Post by Happy_Man on 2007-05-18
> **carlosqueso said:**
> Ubuntu has a partitioner, although if it gives you problems, you can always use the gparted live cd to do your partitioning.  One peice of advice...make sure that you have a seperate partition for /home (this should be your biggest one), as it'll make recovery from system screw-ups a lot easier.

Just in case you have no idea what he's talking about: In Linux, /home is where all your personal files and settings are stored. It's like My Documents and Application Data in Windows rolled up into one. If you put this on a separate partition from the rest of your install, if you ever have to reinstall, it will be like you never did a reinstall; all your wallpapers, themes, program settings, etc. will still be there, intact and pristine. Just about the most useful thing Linux can do, IMO.

---

### Post by Inxsible on 2007-05-18
Do you have an OS (Windows) already loaded on the computer?
 
If so, Do you plan to keep Windows and have a dual boot?
 
If yes, Make sure you don't install Ubuntu over the windows partition. DO NOT OPT FOR THE 1ST OPTION IN THE PARTITIONER !!!!
 
Select the 'Manual' option for partitioning !
 
Use this link for a bit more info
 
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by S15_88 on 2007-05-18
I've taken a different version of Ubuntu for a spin on my desktop looked pretty sweet, as for the partitions i'll have my OS(vista) NTFS , the recovery drive NTFS, and i'll have to make a LinuxSwap and LinuxRoot(/home).  Is there a possibility that my graphics card will give me any troubles due to the resolution,1440 by 900, or the fact that it's wide screen? ps. those links to the graphical Install will come in handy!

Thanks, Alain

---

### Post by Inxsible on 2007-05-18
I have a 17" wide screen too... Mine worked right out of the box. But I have NVidia, so I cant say for sure. But if it doesn't recognize then it is still an easy fix !
 
Install it....we are here to help :)

---

### Post by mikewhatever on 2007-05-18
> Is there a possibility that my graphics card will give me any troubles due to the resolution,1440 by 900, or the fact that it's wide screen?
That's certainly possibly, but is usually fixable.

---

