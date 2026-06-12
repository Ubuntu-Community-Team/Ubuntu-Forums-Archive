---
title: "Help Installing to a USB drive then booting internally."
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by dfk789 on 2006-12-21
OK. so i have a bit of a problem, and im not really sure whats causing it to happen or what to do to fix it.

So here it is. My old laptop has broken, it does not have a cd drive or floppy drive so i cannot boot anything from it. I removed the hard drive, and have it hooked up to my sisters laptop through a hdd usb adaptor. Booted the spare live cd i had and installed Ubuntu 6.06 onto the usb HDD. I used to have windows xp installed on the drive but  all that had been deleted priot to installing ubuntu. Now when i put the hard drive back in my old laptop i get the error operating system not found. 

I do not see GRUB either....i remmebr when i had this installed previsuly GRUB would load up....

any help or input is greatly appreciated :D

---

### Post by logos34 on 2006-12-21
maybe grub installed to your sister's c:/ drive.

---

### Post by scrooge_74 on 2006-12-21
Your laptop is one of those that uses a docking station? i think it would be easier if you could use one for a while.

Another idea, take your sister HD out install your then install again. Take it out and put it back on your laptop...dont forget to put your sister's laptop back together :D

---

### Post by dfk789 on 2006-12-21
i have a docking station but i dont see how that helps.....still no cd drive.
I unfortunatley cannot take swap the hard drives due to not having the right darned screwdriver](*,) 

Ive comeplty installed it again on the usb drive no errors nor problems. but still will not boot from the laptop internally. 

So ive been lurkning around reading this and that, and ive come to the conclusion that this FSTAB file needs changing. making the HDD from sda1 and sda2 to hda1 and hda2 respectivly. But i have a problem when trying to edit the FSTAB file, The whole drive ive installe ubuntu to, appears as read only. whihc means i cannot make the changes. and i dnt know what to do now.

help me please :)

---

### Post by dfk789 on 2006-12-21
well, i managed to change what i thought would fix the problem. sda to hda.....buut, it like didnt actually work nor do anything. So now im back to trying to get GRUB recognised, i think i read somewhere, that knoppix can install grub on an external HDD, but i dunno. i'd really really like some input since im really confused :(

---

### Post by logos34 on 2006-12-22
why not try install once more but this time unplug the cable from your sister's hard drive just to make sure grub is not trying to install to the MBR of that disk.  Then it will have no other choice but to go onto the usb drive.

---

