---
title: "Acronis True Image, Norton Ghost and Ubuntu"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by teabuntu on 2007-11-22
Hello,
I'm looking to get a hard drive image restorer ASAP, and I've narrowed down to either Acronis True Image Home version either 10 or 11 (11 is not yet released in my country), or Norton Ghost 12.0.  With Acronis version 11, it says the following: support for Linux Ext2/Ext3, ReiserFS-3 and Linux Swap; sector-based support for other operating systems.  Not sure if version 10 of Acronis supports linux.  Does anyone know?

I'm looking to install Gutsy Gibbon, and was wondering if what Acronis says above supports Ubuntu and specifically Gutsy?  Also, does anyone have advice on which one to get, in terms of pros and cons for each and why you would recommend one over the other?

Thanks for your help.

---

### Post by teabuntu on 2007-11-22
bump

---

### Post by lynnevan on 2007-11-22
I had an older copy of Acronis (before true image) & liked it.  It saw linux partitions no problem.  The only thing i didn't like is that it couldn't see thumbdrives.
I didn't know ghost could see linux.
I've had tremendous luck just raw copying entire partitions from one disk to another w/ gparted live disk.  Doesn't matter what file type or OS it is.

good luck

lynnevan:)

---

### Post by tj.c on 2007-11-22
I use SystemRescue CD. It's a boot cd and works greta with both Winblows and Linux. 
[http://www.sysresccd.org](http://www.sysresccd.org)

---

### Post by torgrot on 2007-11-22
I have used both Acronis v10 and v11 and both are able to back up and restore Linux file systems.  It can do it to a thumb drive CD/DVD or an external HD.  I have done from Windows and I have done it from the standalone CD.  I highly recommend it as a backup solution.

torgrot

---

### Post by crjackson on 2007-11-22
> **teabuntu said:**
> Hello,
I'm looking to get a hard drive image restorer ASAP, and I've narrowed down to either Acronis True Image Home version either 10 or 11 (11 is not yet released in my country), or Norton Ghost 12.0.  With Acronis version 11, it says the following: support for Linux Ext2/Ext3, ReiserFS-3 and Linux Swap; sector-based support for other operating systems.  Not sure if version 10 of Acronis supports linux.  Does anyone know?

I'm looking to install Gutsy Gibbon, and was wondering if what Acronis says above supports Ubuntu and specifically Gutsy?  Also, does anyone have advice on which one to get, in terms of pros and cons for each and why you would recommend one over the other?

Thanks for your help.

I use Acronis TI 9.1 Workstation.  It works fine.  Keep in mind there is only a windows installer.  I installed in windows and made a boot CD.  Using the CD works flawless.  Also, on my desktop, I dual boot and run it from windows to backup/restore the Linux drive.

I downloaded the Linux version and couldn't get it to install on Feisty.

---

### Post by teabuntu on 2007-11-23
Thank you for your posts.

---

### Post by Wynne G Oldman on 2007-11-23
I'd go with Acronis too. GHOST 2003 sees Ext3 partitions, and will copy them to an image, but it will corrupt data. I think it will only work if you're doing a sector to sector copy from one identical drive to another. I use Acronis off the boot CD to create backup images, and it works great for me.

---

