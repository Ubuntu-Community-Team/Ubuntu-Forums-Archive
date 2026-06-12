---
title: "Imac 27"
date: 2014-09-12
forum: Apple Hardware Users
---

### Post by ernestj on 2014-09-12
Where can I get instructions on installing 14.04 on a Imac 27"? I do not care about dual booting, unless there is a good reason to keep OSX on the system.

Thanks, Ernie

---

### Post by este.el.paz on 2014-09-12
> **ernestj said:**
> Where can I get instructions on installing 14.04 on a Imac 27"? I do not care about dual booting, unless there is a good reason to keep OSX on the system.

Thanks, Ernie


@Ernie:

The general wisdom is that it is best to keep OSX on the unit . . . for "firmware" issues, etc--so that would mean "dual boot" . . . the ubuntu wiki is probably adequate to answer your questions or google your question(s) and look to see what shows up in Ubuntu wiki or forum.  You might try to download the 14.04  "amd64 + mac" "desktop" iso and either burn it or make a bootable USB drive and try to boot up the DVD and test the system out, see how it works.  If you like it "rodbooks" offers some tips on dual booting, although I **don't** recommend using Bootcamp to set up the partitions, just use Disk Utility to cut out perhaps 50 GB and set it to "FAT32" or "Free space" . . . then boot the installer and see if it offers a "Install in largest free space" option . . . if it does, use that; if not use "manual" and then use the GParted disk utility to partition at least 3 spaces . . . about 10 MB flagged as "bios_grub" for GRUB, the larger portion for "/" --flagged as "/" for root and home, and about what you have in RAM for "swap" . . . it used to be 2x or 1.5x RAM, but it seems like the installer is using RAM . . . so whatever RAM you have in GBs IS "swap" . . . run the installer, enjoy the fun.  Ah, don't forget to check the md5sum or the other checksum number of your downloaded iso file . . . if it doesn't match, try again.

e.e.p.

---

