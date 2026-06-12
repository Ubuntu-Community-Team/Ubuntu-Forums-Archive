---
title: "Fixing Boot Loader outside Ubuntu"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by kevcham on 2006-04-04
I am brand new to Ubuntu, have set it up on a computer this way:
First hard drive- Win98 partition, WinXP partition, Linux partitions
Second hard drive- FAT32 storage partition, NTFS storage partition, XP test setup.

The XP test setup is a partition I created on the second drive in order to test programs before installing them on the main system.  So I leave it unactivated until it expires, and then reinstall if I still need it.  

Here's the situation.  The setup has worked fine since adding Ubuntu.  The GRUB loader starts, and if a family member wants XP or 98 they choose the last line which loads the boot.ini file on drive C:.  Since Ubuntu has updated, the GRUB loader has excess entries I would like to remove, but first things first.

As often happens, when testing something on the XP test drive, things got pretty mangled... no problem, simply reinstall XP on that partition.  So I've done that, but now I've lost the GRUB boot loader.  Machine goes directly to boot.ini, so I can run any MS OS, but no access to the Ubuntu partition.  Now I know I can get everything working back to the way it was if I just reinstall Ubuntu, but is there an easier way?

How do I access and re-activate the GRUB boot loader from Windows, or how do I use the Ubuntu DVD I created to quickly fix the boot?

---

### Post by az on 2006-04-04
Boot the installer and type 
rescue

it will offer to mount a number of partitions as root.  Pick the ubuntu partition and get to the shell.  At the shell type:

grub-install /dev /hda (if that is the correct first hard drive.)

---

