---
title: "Grub Loading 1.5 Error 21"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by Gazmondo on 2008-02-05
Hiya,

I am having some problems getting both Xp and Ubuntu to boot, and having scrolled through google and this forum, I believe this error to be related to the GRUB Loader not being able to find a specified disk, though I can't seem to find a solution.

I have the following setup:

36gbx2 RAID0 (XP)
200GB (XP - backup to RAID)
500GB - 300gb for XP and 186gb for Ubuntu.

I cannot boot into either XP or Ubuntu without either getting the GRUB Loader 1.5 Error 21 screen or having to use the XP or Ubuntu CD.  If I put the XP CD in it will boot into XP on my raid array which is fine, and when I put the Ubuntu CD in it will boot into Ubuntu fine, though it won't work if I do not use any CDs.

I'm new to using LINUX so i'm not too familiar with it's nature, so any help would be appreciated.

---

### Post by philinux on 2008-02-05
i'm not familiar with raid but if you post the output of

cat /boot/grub/menu.lst

someone may be able to help.

---

### Post by Trail on 2008-02-05
Is your HD boot sequence correct (through BIOS)?

---

### Post by Gazmondo on 2008-02-05
> **philinux said:**
> i'm not familiar with raid but if you post the output of

cat /boot/grub/menu.lst

someone may be able to help.

Is it this you're requesting:

See;grub(8), info grub, update-grub(8)
grub-install(8), grub0floppy(8)
grub--md5, crypt, /usr/share/doc/grub
and usr/share/doc/grub-doc/.

Trail: Boot sequence is set to:

RAID
200GB
500GB

I was planning on editing the boot.ini of my RAID so that it gave me the option of booting into both xp and ubuntu.

---

### Post by Trail on 2008-02-05
Boot into ubuntu (not the live cd) and execute the command
```
cat /boot/grub/menu.lst > ~/here.txt
```
This will create a file named here.txt in your home directory, that you can post here.

---

