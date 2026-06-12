---
title: "trouble booting from cd"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by AJS302 on 2007-06-18
i have been trying to install ubuntu on an older computer that doesn't preload the cdrom drivers so it won't boot from the cd, is there anyway i can get it to install?

---

### Post by reset3x on 2007-06-18
Did you check in your bios to see if you can change the boot priority for you drives? CDROM being first?

---

### Post by AJS302 on 2007-06-18
yes i have checked and it is definitely set to boot from the cdrom drive but it still doesn't work

---

### Post by reset3x on 2007-06-18
OK... Thats good..... It really has nothing to do with any drivers... What version are you trying to use? And did you create your cd or dvd from an ISO? Also what do you have on the screen when you try to boot from that drive?

---

### Post by AJS302 on 2007-06-18
i am trying to install fiesty fawn (i;m currently running windows 98SE) i did create the cd from an iso and when i try and boot it from the cd drive it doesn't do anything regarding ubuntu just continues booting 98 like it normally does

---

### Post by oilchangeguy on 2007-06-18
> **AJS302 said:**
> i am trying to install fiesty fawn (i;m currently running windows 98SE) i did create the cd from an iso and when i try and boot it from the cd drive it doesn't do anything regarding ubuntu just continues booting 98 like it normally does

please advise your machines specs. it probably won't run 7.04.

---

### Post by reset3x on 2007-06-18
Sounds like an incorrect burn... When you look at the disk using Win 98 do you do you see one file called ubuntu-7.04-desktop-i386.iso? Or do you see files and folders? If it's the first of the two it's an incorrect burn.... If thats the case see here... [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by AJS302 on 2007-06-19
yes the cd is burnt correctly as for the specs it has 300mb of ram, a pentium 3 processor and a 20gb hard drive

---

### Post by dhopley on 2007-06-29
I have exactly the same problem on a Pentium III 450 mgz running 98SE . The Ubuntu alternate disk loads fine but all the other ISO CDs (Super Grub , Rescue CD and Gparted for instance) seem to have no automatic loading of the CD Rom drivers embedded in these ISO image CDs . In 98SE the problem is solved by a bootable floppy loading the CDROM drivers and then on entering an MS Dos command at the command prompt > to search the CD's directory for a * .exe program to run . In my case using the SmartBootManager floppy does not support the option to boot from CD either , presumably because neither BIOS nor the SBM.BIN floppy has loaded the CDROM drivers at that point . Obviously the ideal would be a Linux 'shell' to be loaded on a floppy in the A drive which could load CDROM drivers and then invoke the CDROM ISO image , but I've not found such as yet ,
Derek

---

