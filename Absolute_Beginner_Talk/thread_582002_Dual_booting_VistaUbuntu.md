---
title: "Dual booting Vista/Ubuntu"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by Lee7 on 2007-10-19
Hi all, I tried dual booting previously with Ubuntu 7.04 and failed. I used the same method I'll describe below to dual boot with the new 7.10 but failing again:

C: Has Windows Vista installed
L: Is where I want Ubuntu
M: Backups

These are three seperate hard drives. 

When running the Ubuntu installation, I tell the boot loader to be installed at "(hd,1)" because I've selected the installation to use the whole of L drive. I then go into Vista and open EasyBCD to add Ubuntu.

When rebooting, I can select between Vista and Ubuntu. When selecting Ubuntu, it says it was unable to load the partition or it couldn't find the boot loader on the hard drive.

Any ideas?

---

### Post by mlentink on 2007-10-19
Ah...
Seems to me that by using this, eh, bcd?, you've sorta wrecked the linux boot-loader (GRUB), which would've otherwise worked fine.
Quick solution: reinstall Ubuntu, and this time don't mess with stuff like bcd. GRUB is entirely capable of managing three (or more) partitions/os's

---

