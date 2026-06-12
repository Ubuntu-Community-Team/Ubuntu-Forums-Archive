---
title: "New Install to Boot Ubuntu from USB external drive"
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by sfcwoods on 2006-11-20
Okay, here is the situation. I am brand new to Ubuntu, I tried to mess with some other distro's of linux a couple of years ago to no avail. Kind of liking this now. 

I want to install it on my laptop TO an external USB drive so that I can actually boot to Ubuntu from virtually any machine. I HOPE.

At any rate, I can NEVER get it to install to the USB Drive so I pulled the windows xp drive out of the laptop and put another one in, ran ubuntu cd rom and intalled. No problem and I can boot to Ubuntu as long as THAT drive is IN the laptop.

When I put that fully bootable drive in the USB case and try to boot from USB device, I get this error:

/bin/sh: can't access tty; job control turned off
(initramfs)

I tried to edit GRUB
root (hd0,0) to (hd1,0) as well and that does not work either.  I tried several methods after searching the forums here and I must still be missing something.. The only way I can edit any files is to boot back into Ubuntu with the CD and then change the root password and login access so I can log in to Ubuntu with the root id, access the menu.lst on the USB drive and make the changes there, but alas, still to no avail.

I am using Ubuntu and Grub on my desktop PC, but I would really like to get it going on my laptop with the external drive.  Once I get that figured out, then I will start working on 'why' Ubuntu wireless will not work on my wireless network. :-)

Any assistance would be greatly appreciated..

---

### Post by dmizer on 2006-11-20
try this: [http://www.ubuntuforums.org/showthread.php?t=266068&highlight=howto+ubuntu+usb+boot](http://www.ubuntuforums.org/showthread.php?t=266068&highlight=howto+ubuntu+usb+boot) post number 6 has the directions.

---

### Post by gn2 on 2006-11-20
> **sfcwoods said:**
> Okay, here is the situation. I am brand new to Ubuntu, I tried to mess with some other distro's of linux a couple of years ago to no avail. Kind of liking this now. 

I want to install it on my laptop TO an external USB drive so that I can actually boot to Ubuntu from virtually any machine. I HOPE.

At any rate, I can NEVER get it to install to the USB Drive so I pulled the windows xp drive out of the laptop and put another one in, ran ubuntu cd rom and intalled. No problem and I can boot to Ubuntu as long as THAT drive is IN the laptop.

When I put that fully bootable drive in the USB case and try to boot from USB device, I get this error:

/bin/sh: can't access tty; job control turned off
(initramfs)

I tried to edit GRUB
root (hd0,0) to (hd1,0) as well and that does not work either.  I tried several methods after searching the forums here and I must still be missing something.. The only way I can edit any files is to boot back into Ubuntu with the CD and then change the root password and login access so I can log in to Ubuntu with the root id, access the menu.lst on the USB drive and make the changes there, but alas, still to no avail.

I am using Ubuntu and Grub on my desktop PC, but I would really like to get it going on my laptop with the external drive.  Once I get that figured out, then I will start working on 'why' Ubuntu wireless will not work on my wireless network. :-)

Any assistance would be greatly appreciated..

It can be done in Ubuntu but it's significantly easier with PCLinuxOS which offers USB as an install option in the Draklive Installer....

Very simple user friendly Distro it is too. 
I use it on my desktop PC, and Xubuntu on my laptop

---

### Post by rlozano on 2006-11-21
tried this one with dapper and it worked. USB drives are normally detected as sdxx in your grub. so instead of hdxx use sdxx. and your computer must be capable of booting to USD as well.

i actually have a mobile ubuntu fo several months already, actually... :)

---

### Post by sfcwoods on 2006-11-21
but how do I know what to use for (hd0,0)??? do I use sda1 I (believe that is what it is) instead of (hd0,0)?  Also, are you using a boot cd for your external ubuntu???

---

### Post by randomxm on 2006-11-26
Im trying to do this also but what the heck is grub?!?! im new at this, where can i learn about things like "grub" and using the terminal?

---

