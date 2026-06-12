---
title: "Help with dual boot from Ubuntu to Ubuntu+XP!"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by Fixman on 2007-10-04
Im using [This]("http://www.acpmag.com/5459/dualboot_ubuntu_and_windows_xp") guide to dual boot my ubuntu to ubuntu+XP, but, once I partition the disk and I run the XP CD, press enter, and it tells me that "Theres no hard disk connected to the computer". I tried everything: from rebooting, to changing the new partition to FAT32 type of files. Ubuntu boots properly. Any suggestions?

---

### Post by Fixman on 2007-10-04
BUMP.
(this is important!)

---

### Post by rickycodie on 2007-10-04
the easiest thing to do is to backup all your data and install windows first, then partition and install ubuntu. 

short of that see if your bios settings allow you to set your hdd to a compatability mode.

---

### Post by Malibu Illusion on 2007-10-04
Is this a Windows support board too now?  This is entirely a Windows issue; not Linux.

I would suggest that however you're running your drive(s) is not recognized by Windows XP's drivers that come with its setup CD.  I believe you have to install third party drivers from a floppy disk during the installation process if, for instance, you require to support a RAID controller/SCSI adaptors.  This may be relevant to you.

---

### Post by Gone fishing on 2007-10-04
The problem is XP doesn't have SATA drivers very old OS!

You need to put in the SATA driver (on a floppy!) when you boot from the cd and it asks about scsi drives.

The instructions you are using are good :)

---

### Post by notwen on 2007-10-04
Find SATA Drivers for your mobo and then use nLite to add them to your WinXP image using [nLite]("http://www.nliteos.com/nlite.html").  It will in-turn make a new WinXP cd w/ SATA support included.

---

### Post by rickycodie on 2007-10-04
> **Fixman said:**
> Im using [This]("http://www.acpmag.com/5459/dualboot_ubuntu_and_windows_xp") guide to dual boot my ubuntu to ubuntu+XP, but, once I partition the disk and I run the XP CD, press enter, and it tells me that "Theres no hard disk connected to the computer". I tried everything: from rebooting, to changing the new partition to FAT32 type of files. Ubuntu boots properly. Any suggestions?

do you have a sata drive?

---

### Post by Fixman on 2007-10-04
> **rickycodie said:**
> do you have a sata drive?
yes, I am, but I could install XP in this computer before (without ubuntu preinstalled) witput any problems

---

### Post by rickycodie on 2007-10-04
could you give us some specs? how new is the motherboard? is the copy of xp a sp2 copy?

---

### Post by Fixman on 2007-10-04
> **rickycodie said:**
> could you give us some specs? how new is the motherboard? is the copy of xp a sp2 copy?

Well, yes, its a sp2 copy. But if what I need is a SATA driver, could someone tell me where to get one? (I don't think I own a diskette wiht those files)

---

### Post by rickycodie on 2007-10-04
if you have western digital or seagate i know that you can download the drivers direct from the website.

---

### Post by cranshinibon on 2007-10-04
What I would try doing first is grabbing a floppy disk and copying the SATA Boot files from the manufacturers website and put the floppy in while Windows Is "scanning for hardware configuration" while installing. 

Also, try installing XP on a partition then having the right amount set aside for ubuntu and install ubuntu second....I've noticed that sometimes the mbr gets kind of screwy when you install ubuntu first, then windows. So if the SATA files don't work do a kill disk, fdisk the /mbr, and install windows first, then ubuntu. I hope this helps a little

---

### Post by Fixman on 2007-10-04
I can't find the drivers on the creators home page. Could someone post a like to it?

EDIT: is [this]("http://www.serialata.org/index.asp") the home page?

---

### Post by Fixman on 2007-10-04
bump

---

### Post by Gone fishing on 2007-10-05
You should have a cd for your mother board the driver will be on that, often they are bootable and will ask you to put a floppy to install the SATA drivers.

---

