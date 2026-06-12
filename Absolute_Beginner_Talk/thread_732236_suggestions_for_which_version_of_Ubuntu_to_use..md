---
title: "suggestions for which version of Ubuntu to use."
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by phread59 on 2008-03-22
I have a new computer I built myself, specs as follows:

Asus P5N-E SLI Motherboard
Intell 6550 Core2 Duo Processor
4GB Patriot EPP 64 bit memory
XFX GeForce8600GT Vidio Card
320GB Segate Sata II HD
HPC5140 Combo Printer
LogitecZX7 Optical Mouse Cheepie keybord (Kensington)
And last and least XP Pro 64 bit

System works just fine.  I'm getting very tired of Cookies, Malware and just plain old attacks on my OS.  I have an interest in Linux.  So here I am.  I have downloaded rugular Ubuntu and am gonna download XUbuntu as well.  Just interested in which to install in a spare 500GB IDE drive I have.  Going to try to install a dual boot machine.  

I do have 2 stupid questions:
1) how to set up said dual boot system
2) will 64 bit Ubuntu work on an Intell based 64 bit machine.

I'm not to terribly afraid of a 64 bit op system.  I realize there is a 32 bit emulator for most applications.  Just want to know which would be more appropriate for a linux beginner.  BTW I can kick XP hard enough to get it to do most of what I want.  Just want to learn Linux as well.  Would primarily use it for secure web surfing and eventually using a server down the road.

Mark Shuman

---

### Post by PurposeOfReason on 2008-03-22
You can't get rid of cookies on any OS . . .

Anyways, go with 64bit Ubuntu, it'll work fine for intel and dual booting will be an option during the install when you're partitioning. You can either "use the whole disk" or move a slider to guide what you want to use for Ubuntu and leave the rest for windows.

---

### Post by jan quark on 2008-03-22
dual boot guides:
[http://apcmag.com/node/5162/](http://apcmag.com/node/5162/)

if you want to run 64 bit ubuntu check if there is a 64 bit support for your hardware ( network device the most important one)

---

### Post by phread59 on 2008-03-23
Jan thank you for your help.  I am currently running XP Pro 64 bit.  So I believe the 64 bit support is moot.  Your tutorial was a help.  However it assumes you want to boot from the same drive.  I want to boot from a different drive.  I have another IDE drive (am currently using a SATA drive) I want to use for Ubuntu and storage. I was going to partition it with 2 250GB partitions.  And try to load Ubuntu onto 1 of the partitions.

Any advantages to using Kbuntu over regular Ubuntu?  I just want to know which is the easiest to use.  I'm getting my feet wet here.  Any suggestions would be appreciated.

Mark Shuman

---

### Post by jken146 on 2008-03-23
As for Ubuntu (GNOME), Xubuntu and Kubuntu, the only difference is the desktop environment and, as such, you can start with just one install and then add as many other desktop environemnts and window managers as you like.  [www.psychocats.net/ubuntu](www.psychocats.net/ubuntu) has some simple instructions for this.


With partitions, you won't need 250 GB for Ubuntu, if you have a large storage partition.  Between 10 and 15 GB for / is all you'll need if you use the 'manual' partitioning option in the installer (mount point should be / and file system should be ext3).  Also make a 1 GB swap partition (virtual memory) at the beginning or end of the disk.  You can make another (large) partition and mount it as /home if you want to secure you users' personal files and settings against reinstallations.  Note that /home cannot be formatted as FAT or NTFS (this would ruin the file permissions and you wouldn't be able to log in).

That you have more than one hard disk does not matter.  Use the installer's default of installing GRUB (the bootloader) to the MBR of the first hard disk (you don't have to change anything) and you'll be fine.

I hope this clears things up.

---

