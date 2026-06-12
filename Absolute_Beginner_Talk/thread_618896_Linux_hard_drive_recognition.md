---
title: "Linux hard drive recognition"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by xerxes-2 on 2007-11-20
Appreciate if someone could give some advice about how Linux recognizes hard drives.

I have set up my desktop pc as a dual boot Windows 2000 & Ubuntu. It has two hard drives with (in Windows-speak) Win2k on drive 1 (NTFS) & Linux on drive 2 .
On disk 2 I set up 45GB as FAT32 with the notion that could use both Linux & Windows to access files, etc there.  The problem is that Linux has somehow recognized this as removable media & I can't open it .  

With Linux clicking system, computer shows:
File system
74.4 GB volume:hda1
44.2 GB volume
29.3 GB volume:Root volume
109.8 MB volume:hda5
CD-ROM/DVD-ROM
Floppy drive

If I plug in a USB drive Linux recognizes it & I can read/write files

When I click on the 74.4 GM volume Linux correctly shows all the Windows files

Clicking on 29.3 GB volume Linux reveals all the Linux setup (has root, home, media, etc etc)

However when I click on the 44.2 GB volume Linux gives the following error message
Unable to mount the selected volume
error: device /dev/hdb7 is not removable
error: could not execute pmount.

On my system Linux has a "removable disk" icon beside the 44.2GB volume whereas it shows a "nonremovable" icon next to the 74.4GB volume. 

This is the only problem I have found so far - all else with Linux & the applications I have used (OpenOffice, GIMP) function fine.

Is there something I can do or set to tell Linux that my 44GB is a non removable drive.

---

### Post by 1337455 10534 on 2007-11-20
Eh, not sure. Tried GParted yet? Play with it for a while.

---

### Post by MegaJim on 2007-11-20
why not use NTFS?

---

### Post by 1337455 10534 on 2007-11-22
Ehm, so wait, you have an empty partition that you want to serve as a junkyard for files you need between OSs. Ubuntu thinks its removable and wont let you access it.
I agree with MegaJim. Convert this partition to NTFS and then ->
:.
Get NTFS Configuration Tool
Add/Remove Programs --> NTFS Configuration Tool.

This should give you (i.e Ubuntu) NTFS privilages. Wait, that spare HDD/Partition/w.e.

Btw; 7.10 has in-built NTFS access. Are you on Feisty or Gutsy?

---

