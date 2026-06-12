---
title: "Dual boot Ubuntu 7.10 w/dual SATA drives."
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by Bubonic on 2008-01-04
I have installed XP and Ubuntu on two separate  physical SATA hard drives and I don't get the GRUB boot screen when I start my system. I took a look at some of the stuff other people have posted but thats all about a method that does not involve changing the Windows boot record. I want to change the MBR and need to know how. Right now my PC just boots Windows XP which is my primary OS.
I looked around at what I could find about GRUB and got completely lost.

Can anyone tell me where to download GRUB and how to install it? Also how to change the windows mbr OR Point me to a good tutorial?

---

### Post by stump138 on 2008-01-04
this is the tutorial I follow for these issues [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

I've had to do this a few times and this works well.

---

### Post by kenboyles72 on 2008-01-04
Also, make sure you have changed the boot order for your hard drives in the BIOS. If the boot order is still the same, you will keep booting into XP. You need to change the boot order to have to hdd that ubuntu is installed on to boot first.

---

### Post by Bubonic on 2008-01-05
Ok... I checked some of that  stuff out. I was trying the "Using the Desktop/LiveCD and Overwriting the Windows bootloader" guide. I got to the part about creating the /mnt/root folder and was not able to create the folder since I'm running off a CD. 

Next I tried using the Super Grub Disk. I got grub to work properly on my linux HD but windows does not appear and everytime I try to select Ubuntu to boot up it just says "Error 22: no such partition". Also my windows install does not show up on the Grub list.

I noticed that the link you gave me is for restoring the Grub menu when you have installed Windows after Ubuntu. I installed Windows before Ubuntu and am still totally lost.

---

