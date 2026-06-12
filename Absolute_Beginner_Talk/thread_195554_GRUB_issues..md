---
title: "GRUB issues."
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by dobbs3x on 2006-06-13
Hi everyone,

   I have been trying to install Ubuntu for the past few hours everything seems well and I have followed a lot of good guides on the process but have ran into a barrier. When GRUB try's to install it hangs at 50%. I read around the net that it could be some script not telling GRUB to sync and there is a fix for it. 

   Well the thing is I don't know how to download the fix. I run the Ubuntu install/boot CD and press alt f2 to go in to a cosole and get a little lost. I have tried mounting my harddrive with the install of Ubuntu but get lost there too. I am thinking I have to get it mounted to access ftp mayby so I can download this fix. 

   So if someone could tell me how I can start my Unbuntu from the install/boot cd I would appreciate it and if anyone has any info on the GRUB issue that would be cool too.
    
    thanks, Jeremy

---

### Post by anaconda on 2006-06-13
GRUB can be installed separately afterwards. Did rest of ubuntu install successfully?

[http://www.gnu.org/software/grub/grub-2-download.en.html](http://www.gnu.org/software/grub/grub-2-download.en.html)

should get you started.. From there you should be able to find image of grub boot floppy. And using it you should be able to install grub....

Wish you luck

---

### Post by dobbs3x on 2006-06-13
How do I load the base install kernal that I have installed on my hard drive while booted from CD? Since I can't get grub installed I need to boot from CD then mount my Hard drive somehow and load the kernal that way or?

Also I can't seem to download the latest GRUB version all the ftp links are timing out on their site.

---

### Post by dobbs3x on 2006-06-13
btw. Yes unbuntu all instaleld just fine, its just GRUB and/or LILO having issues. I think its because I am trying to use a RAID0 configuration. I have read a guide on how to setup the partitions and all that seems good just sounds like GRUB on the BOOT/Install CD I use does not have a script to sync the drives before it installs itself or something. I heard the latest GRUB has this capilbility. But am clueless at this point on how to get it installed.

Possibly get my kernal on my Hard Drive running and then download and run the tarball or get a GRUB boot CD with the latest version and boot with it.

---

### Post by dobbs3x on 2006-06-13
Also how can I find out what version of GRUB is currently on my CD. The CD is from an ISO I downloaded from ubuntu.com yesterday

---

### Post by drtvasudevan on 2006-06-13
[QUOTE=dobbs3x]btw. Yes unbuntu all instaleld just fine, its just GRUB and/or LILO having issues. I think its because I am trying to use a RAID0 configuration. I have read a guide on how to setup the partitions and all that seems good just sounds like GRUB on the BOOT/Install CD I use does not have a script to sync the drives before it installs itself or something. I heard the latest GRUB has this capilbility. But am clueless at this point on how to get it installed.

Possibly get my kernal on my Hard Drive running and then download and run the tarball or get a GRUB boot CD with the latest version and boot with it.[/QUOTE]

if i remember right the alternate cd has the configuration for  RAID  as opposed to the desktop live.
 TV

---

### Post by dobbs3x on 2006-06-13
thanks, I am downloading the alternate iso right now, will give it shot.....hope it works :)

---

### Post by dobbs3x on 2006-06-14
Well still did the same thing, GRUB freezes at 50%. Getting frustrated maybe I shoudl go look at another distro that has raid 0 support.....

---

