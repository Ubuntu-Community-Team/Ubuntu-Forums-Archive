---
title: "Help me P-L-E-E-Z-E !!"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by Bob Bloch on 2007-05-27
I'm a Linux/Ubunto Newbie rapidly becoming frustrated. 

(1) My old Dell Dimension has 2 HDs - Win XP/SP2 on 'primary' and Ubuntu 6.06 on 'secondary' (dual-boot capability). Too often "GRUB ERROR 2" appears during bootup (stage 1.5).  No consistent cause has been found. Only solution is to reinstall Ubuntu - i'm getting really good at it but want to progress. After re-install both OSes work OK. A 'bug' report has been entered by no response so far.

(2) Searching the online forums for possible solutions does NOT work properly since '2' is only single digit & apparently there is a weird restriction of minimum of TWO characters in search argument. ("GRUB ERROR 2" does not compute).

(3) I have not yet found how to completely UNINSTALL Ubuntu & GRUB loader so that Win XP can be tested standalone for other suspected problems.

Plz advise asap. I don't have much hair left to pull out. thanx.

Balding Bob

---

### Post by aidanr on 2007-05-27
1)

> 2 : "Selected disk doesn't exist"

This error is returned if the device part of a device- or full filename refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system.

need some more info, motherboard make & model, the contents of /boot/grub/menu.lst and the output of sudo fdisk -l

btw, you can grab those from within the live cd, the linux partiton should be automatically mounted, just make sure you grab the menu.lst from the harddrive installation and not the live cd

2) use google

3) format the second harddrive, boot the xp install disk, go into recovery console and type fixmbr

---

