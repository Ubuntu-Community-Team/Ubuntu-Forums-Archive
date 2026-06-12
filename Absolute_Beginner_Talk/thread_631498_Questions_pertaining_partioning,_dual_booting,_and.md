---
title: "Questions pertaining partioning, dual booting, and importing files"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by 449 on 2007-12-04
Hey, I have a Pentium 4, 512MB RAM running off an external HDD that is one big partition. My primary goal is to be able to successfully created two new partitions: one for installing and running Mint and one for storing backup files and detectable by Windoze. So here are my questions:

Since I'm running Ubuntu 7.10 off an external HDD I'm guessing I'll need to use the Gparted live cd on another computer. Do I need to unmount the drive even though I using a different machine? 

Will it be possible to dual boot without getting a Grub error?

---

### Post by ajgreeny on 2007-12-04
So you have no internal hard disk, is that right, or is that where your windows is installed?  And you want to add Mint to your ubuntu install on the external on the same disk?  Where is grub at the moment, not the** /boot/grub** folder, but the actual grub program?  If it is on the external disk it shouldn't be a problem as grub can just be overwritten when you install Mint and maybe similarly if grub is on an internal hard disk, but really this is an unusual request and we don't have enough info about your set-up to be certain of a correct answer. Tell us more.

---

### Post by 449 on 2007-12-04
There is no internal HDD whatsoever. Ubuntu is on the ex HDD. I want to add two additional partitions. One for Mint, one for various files.

---

### Post by crjackson on 2007-12-04
> **449 said:**
> Hey, I have a Pentium 4, 512MB RAM running off an external HDD that is one big partition. My primary goal is to be able to successfully created two new partitions: one for installing and running Mint and one for storing backup files and detectable by Windoze. So here are my questions:

Since I'm running Ubuntu 7.10 off an external HDD I'm guessing I'll need to use the Gparted live cd on another computer. Do I need to unmount the drive even though I using a different machine? 

Will it be possible to dual boot without getting a Grub error?

With your external HDD plugged in, boot from a gparted CD, create your desired partitions, shutdown, reboot using the MintCD, install on the desired partition.  Format the partition you intend to share with windows to NTFS.

Mint will update the current Grub so that shouldn't be an issue.

**_[COLOR="Red"][SIZE="5"]EDIT: As always, backup all your data before editing your partitions.[/SIZE][/COLOR]_**

---

