---
title: "Removing Ubuntu Installations &amp; updating grub"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by thefoolisme on 2007-04-01
Hi folks, 

I have a quick question.  For a school benchmarking project, I installed Ubuntu, Kubuntu, and Xubuntu all on the same hard drive, after a Windows XP installation.  Now that the project is over, I'd like to remove Kubuntu, and Xubuntu to give Ubuntu more room.   The order of installation was:

Windows XP
Ubuntu
Kubuntu
Xubuntu

I noticed when doing the installs that the final grub menu is from the file in Xubuntu.  I want to remove the other distributions now, but I'm afraid if I just delete the partitions it will mess up grub.  What is the best way to do this without deleting them all and starting all over?  

Thanks.

---

### Post by zvacet on 2007-04-01
Download Gparted live CD and erase patition you don´t need.After that extend Ubuntu partition o free space.To restore grub boot up your CD and choose **Recover a broken system**.After few dialogues you will see window in wich you will be asked to choose root device.because you are in dual boot it will be probably second one.Ubuntu will try to mount it.If everything is O.K. you will go to the next window and you will see option** Reinstall GRUB boot loader**.Select it.it ill ask where you want to install grub.Type hd0.When it is finished reboot.

---

