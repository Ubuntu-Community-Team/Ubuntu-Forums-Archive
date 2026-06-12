---
title: "Starting over"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by Zerostarhx on 2006-07-27
I'm having trouble completly wiping my Master drive. I want to completly reinstall both ubuntu and windows, that way I can play all my games still. Is there a best way to do this if you don't have another computer to work with?

---

### Post by Metacarpal on 2006-07-27
Hi Zerostarhx,

The first thing you'll want to do is back up all of your data.  Anything you can't easily replace, burn to CDs or other media.

Then startup your computer with the XP install CD in the drive.  (Make sure your BIOS is set to boot from CD-ROM before HDD.)  When the XP setup gives you the option to format and partition, create a partition of the size you desire (say, half your HDD or whatever's on your mind) for Windows, and leave the rest as unformatted, unallocated space.  Don't create a second partition at this time.

Then continue your WinXP install normally.  When you (eventually) get everything installed and configured for XP, then drop in your Ubuntu install CD and reboot.

When Ubuntu prompts you to partition your drive, tell it to install in the existing unallocated free space.  That way, it'll create a partition for Ubuntu without messing with your Windows install.  (If you want a separate partition for /home, you'll need to manually set those partitions.)

Then complete the install for Ubuntu regularly.  GRUB will detect your Windows install, so you can choose which to boot to each time you start your computer.

---

### Post by Zerostarhx on 2006-07-27
Thankyou very much! This helps so much.

---

### Post by Metacarpal on 2006-07-27
You're welcome!  Just passing along what I've learned hanging around here.

Let us know how it goes! :D

---

