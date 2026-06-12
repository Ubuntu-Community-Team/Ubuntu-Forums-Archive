---
title: "Another topic about dual-booting with WinXP"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by stroberaver on 2007-08-04
Hi all,

Firstly, sorry for yet another topic about dual booting with WinXP. I've read through the stickied threads, and the relevant links to other topics, and followed more links from them too. But I ended up confusing myself and getting a headache, and I don't think I saw anyone ask about the particular arrangement of drives that I have.

I'd like to achieve a dual-boot system of WinXP Home and Ubuntu 7.04. But the drives for Windows and Ubuntu will be on different controllers. Here's an outline of my system:

**SATA primary:**
160GB NTFS drive with Windows and all it's apps and settings (Windows C: drive)

**SATA secondary:**
160GB drive split into 2 NTFS partitions - the largest partition occupies the vast majority of the disk and is used for my docs, backups, etc (Windows D: drive). The small partition is for the Windows swap file (E: drive).

**Primary IDE channel:**
Master device is an 80GB NTFS drive, used as a general dumping ground, torrent store, etc. (Windows F: drive)
Slave device is an empty, unformatted 40GB old drive that I'd like to put Ubuntu on.

**Secondary IDE channel** is a pair of optical drives.

You can probably guess where I'm going with this. When it comes to installing Ubuntu from the cd, and I tell it to use all of the 40gig drive, what do I need to do regarding bootloaders to give me a dual-boot system?

I understand that grub could be loaded onto the SATA drive (and if necessary it's easy enough to get rid of it by doing fixmbr in Windows recovery console), but I saw several other things discussed about loading it onto a master ide drive even though Windows is on SATA, or people who's BIOSes seemed able to give them a choice of boot drives. But I'm not even sure how to go about getting grub onto the primary sata drive and linking it back to Ubuntu on a primary ide slave drive.

My system is an Asus A7N8X Deluxe (nForce2), AthlonXP 2600, gig of ram, Geforce 5900LX. Boot order is currently set to floppy, optical, sata. I can't recall whether there's an option for a fourth boot device, but I have a hunch there isn't.

I'm generally a competent Windows user, able to configure it as I wish. I also occasionally use unix at work, so I'm no stranger to the CLI, but that's very much as a user rather than configuring and installing stuff and playing around with mbrs, which at the moment seems like something of a dark art to me. As such, if anyone can provide some advice on what option is best for me, and how to go about it, I'd be most grateful. :)

---

### Post by benx009 on 2007-08-04
boy you have a lot of drives lol....
well, if i were in your position, i would install grub to your primary sata drive.  if that's where windows boots from, then that'd be your best option.  just like you said, you can easily undo this process w/ "fixmbr" from the recovery console on your windows disc.  however, before you install ubuntu, i would highly recommend creating a swap file for ubuntu partiton on your 40 gig disc.  it doesn't have to be anything big, just a gigabyte or two should suffice.

---

### Post by stroberaver on 2007-08-10
Thanks for the reply. :) I need lots of hard drive space, I'm a keen photographer. ;)

So when it comes to the final stage of installing Ubuntu, and I go to the advanced/extra box to choose where the bootloader goes, what exactly should I put, in order to put the boot menu program into the Windows drive? :confused:

Thank you in advance.

---

### Post by bodhi.zazen on 2007-08-10
Install grub (the default Ubuntu/Linux Boot loader) onto the MBR (Master Boot Record) of the first hard drive,  SATA primary (Windows C:\) drive

Basic Linux Partitioning : [http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

---

### Post by stroberaver on 2007-08-10
Thanks for the link. It mostly seems to make sense to me.

So, I've booted from the live cd, hit the "install" icon on the desktop, chosen all of the 40gig IDE drive as described above, reached step 7 of 7 and clicked the "advanced" button to choose the bootloader location, which is pre-filled with
```
(hd0)
```

So I change this to...?

The partitioning basics is good but doesn't seem clear at this point:
> GRUB.
Grub numbers drives starting with 0.
Grub also names partitions starting with 0.
**Thus grub (hd0,0) = Linux hda1 or sda1 (depending on if you have ATA, SATA, or SCSI drives).**
So if I have both SATA and ATA drives present, what is (hd0) referring to?

---

### Post by bodhi.zazen on 2007-08-10
Install grub to (hd0) I can not tell from what you have posted which devices grub is numbering how.

---

### Post by stroberaver on 2007-08-11
Erm, so now I don't need to change anything? :confused:

What do I need to post to be able to find out what drive grub is referring to with (hd0)?

---

### Post by gn2 on 2007-08-11
If you can change the BIOS to have your 40gb drive first in the boot order you could install Grub to the 40gb drive.

Have a good read through the Hermanzone link in my sig for heaps of relevant info.

It may take a while, but better to study it all now.

I wish I had read it before I started using Ubuntu.

---

### Post by rrinker on 2007-08-11
My previous system had that same motherboard. I had an 80GB SATA drive plugged in as my only drive originally, with XP installed. Everything worked great. I had an extra 40GB drive I wanted to install Ubuntu on, but it was an IDE drive. No matter what I did, if I enabled toe 40GB drive int he BIOS, it always wanted to see that as the C: drive in Windows, even if it wasn;t being booted from. As such, with the 40GB drive enabled, I could boot Ubuntu but not Windows. If I disabled the 40GB drive, Windows would boot. I tried all sorts of combinations in the BIOS to no avail, so left it that I just had to go into setup and change the active drive to switch between each OS.

---

