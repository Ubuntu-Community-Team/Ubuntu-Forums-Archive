---
title: "Bootloader for macbook"
date: 2014-12-07
forum: Apple Hardware Users
---

### Post by Jakesploder on 2014-12-07
Im deciding weither i should dual boot mac osx, windows and ubuntu on my mac but i want to know is if ubuntu will install some other boot loader (Like grub) instead of the standard mac boot loader.

---

### Post by este.el.paz on 2014-12-08
> **space core said:**
> Im deciding weither i should dual boot mac osx, windows and ubuntu on my mac but i want to know is if ubuntu will install some other boot loader (Like grub) instead of the standard mac boot loader.

What you are describing is "triple boot" . . . ubuntu does install GRUB . . . whatever you install should go in ****after OSX**** . . . .

e.e.p.

---

### Post by Jakesploder on 2014-12-10
So, if grub decides to replace the mac osx boot loader with itself, will there be any way to remove grub without messing everything up?
Anyways, Thanks for your help

---

### Post by este.el.paz on 2014-12-10
> **space core said:**
> So, if grub decides to replace the mac osx boot loader with itself, will there be any way to remove grub without messing everything up?
Anyways, Thanks for your help

@space:

GRUB doesn't make any decisions to replace the OSX boot loader, it's better to think of it as "in addition to" . . . .  Actually since you are mentioning this would be for a PPC machine it would probably be "Yaboot" that will handle booting the linux system.  If you hold the option key down at boot the OSX boot loader will still load . . . if you see the linux disk there, when you select that, the next window would be the Yaboot window then the splash.

The latest 'buntu flavor that has a PPC variation is Lubuntu 14.04 . . . there might be a need for an xorg.conf file . . . and a few other details to get it running on an iMac . . . .  The best thing to do is to try out the LiveDVD of the system and see how it runs on your computer **before*** trying to install it.

It ***might*** be easier to start with Xubuntu 12.04 to get some experience with installing linux on an apple . . . .  There are a number of threads here about "G4/G5 in 12.04" . . . .  

In some ways it's "easier" to get the PPC flavors installed . . . .  I would recommend that you set up your potential linux partition in OSX Disk Utility first, set it as "FAT32" or "Free space" . . . then in the linux installer process, see if the "install into largest free space" option is available . . . and let the installer set up the install . . . .  After install, then shut the computer down . . . on reboot possibly the Yaboot window will open first and give you the choices . . . .  But first try out the LiveDVD for the general sense of how things are running on your computer . . . .

e.e.p.

---

### Post by Jakesploder on 2014-12-10
OK Thanks for your help!

---

