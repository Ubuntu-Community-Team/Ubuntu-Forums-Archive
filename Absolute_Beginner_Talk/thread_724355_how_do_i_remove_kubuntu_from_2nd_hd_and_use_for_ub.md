---
title: "how do i remove kubuntu from 2nd hd and use for ubunto second /home"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by robalcorn on 2008-03-14
My system has Ubuntu 7.10 installed on sata 250gb drive and kbuntu on 120gb eide (which i installed this morning to check it out) and xp on a 30gb eide. Grub is loaded on the xp drive i think? So how do I remove kubuntu and access the drive through ubuntu and use as another /home(2) for my media and clean up grub so it doesnt show so many boot options? Also is there a graphical utility to do this with as I ran  sudo nautilus in a terminal and do not see the other drives. Thanks in advance to anyone that can help.

---

### Post by sandysandy on 2008-03-14
>   clean up grub so it doesnt show so many boot options? 

u can edit the menu.lst file  

code is

> 

gksudo gedit /boot/grub/menu.lst 

please take backup of menu.lst before attempting anything.

regards

---

