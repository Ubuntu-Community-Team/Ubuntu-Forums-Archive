---
title: "I can;t instal UBUNTU 5.04"
date: 2005-08-29
forum: Absolute Beginner Talk
---

### Post by micomator on 2005-08-29
I got a disc from my mate which is ubuntu and it has a bunch of other software on it. I think the disc is by "my open cd", It says, to install, just reboot with UBUNTU in your CD-ROM. I do that and it just starts windows normally. How can I install UBUNTU?

---

### Post by manicka on 2005-08-29
change the boot order of your devices in the bios

currently you probably have floppy,hardrive,cdrom

change it to

floppy,cdrom,hardrive
or 
cdrom,floppy,hardrive

---

### Post by grim42 on 2005-08-29
You need to tell your computer to boot from the CDROM. This is done in the BIOS setup.

Normally you access  this by pressing "Delete" just as the computer is booting up and doing it's memory check, hard drive detecting, etc.

You'll need to look for something called "Boot Device Priority" or "First Boot Device" -- something along those lines -- it;s probably set to something like "HDD0". Change to CDROM.

---

