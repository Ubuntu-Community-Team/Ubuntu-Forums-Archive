---
title: "Ubuntu 7.04 64bit to 32bit"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by seuzo on 2007-09-01
Hi, 

Not sure anyone got advise on this 64bit to 32bit. I would be format my 2nd harddisk.

But my first harddisk is window xp. would my boot table not working when i format the 2nd harddisk and wat happen after i format it and install the 32bit ubuntu 7.04? my boot table would come out alot of OS selection?

---

### Post by meborc on 2007-09-01
if you format the harddisk your ubuntu system is on, AND install a new system on it, the new install will also reinstall GRUB in MBR so that you have all the OS in the selection menu... just be sure not to do anything with the disk/partition your windows install is on

---

### Post by seuzo on 2007-09-01
just one more question, would the old boot menu still exit?? 
or a total new menu with the 32 bit ubuntu system to selection?

---

### Post by meborc on 2007-09-01
if your 64bit system is on the 2nd harddrive you will be installing the 32bit on, then no... the installation will replace your ubuntu 64bit with the 32bit one... and the GRUB is installed from clean sheet...

you will see only the new menu

---

### Post by seuzo on 2007-09-01
ok, thanx very much about it. thanx for the great help.

By the way now 64bit ubuntu 7.04 got flash player plugin ?

or java plugin for 64bit? seem like i can't it to down load.

---

### Post by meborc on 2007-09-01
i do not use 64bit so i can't say for sure... i know people can get them to work with some hassle, but i would recommend sticking with the 32bit version... the speed gain from 64bit is way too small to go through a lot of pain installing 64bit flash and java... i'm not sure if it is easier now, but half a year ago, i had a lot of problems with the 64bit version :)

---

### Post by seuzo on 2007-09-01
guess would not be a pain for me to format it and install the 32bit version. since i just started using it.

just wanna to know more. if two OS is on one harddisk. then u wanna to change like my case here. is there any easy way?? or would be the same method?

---

### Post by rsambuca on 2007-09-01
> **meborc said:**
> i do not use 64bit so i can't say for sure... i know people can get them to work with some hassle, but i would recommend sticking with the 32bit version... the speed gain from 64bit is way too small to go through a lot of pain installing 64bit flash and java... i'm not sure if it is easier now, but half a year ago, i had a lot of problems with the 64bit version :)

Both Flash and Java work very well now with 64bit ubuntu.  There are scripts for both, so all you have to do is double click the script and run it.  Not what I would call a hassle.

---

### Post by seuzo on 2007-09-01
> **rsambuca said:**
> Both Flash and Java work very well now with 64bit ubuntu.  There are scripts for both, so all you have to do is double click the script and run it.  Not what I would call a hassle.

oic. so the guide and scripts u are saying can be found at the x86 64-bit users forum?

---

### Post by rsambuca on 2007-09-01
Yes.

[http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)

and 

[http://www.ubuntuforums.org/showthread.php?t=202537&highlight=java](http://www.ubuntuforums.org/showthread.php?t=202537&highlight=java)

---

