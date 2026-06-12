---
title: "Install Ubuntu on hdb with Linspire 5.0 on hda?"
date: 2006-01-27
forum: Absolute Beginner Talk
---

### Post by Ichido on 2006-01-27
I've been experimenting with Linux for about 7 months now.
Started with M$- DOS 3.1 in 1985, ending with Win98SE.
I purchased this PC with Linspire Installed.
I want to add an 'old' hard drive, that used to be in a Windoze Box, to install Ubuntu on it.
Any help as to how to set up Partitions on hdb for Ubuntu?
What file system should I use, ext2, ext3 or Linux type 83?
I would like a Dual Boot System that doesn't 'Hurt' my Linspire until I'm ready to switch to Ubuntu.
The Kbuntu Live 5.10 gets stuck at "Retrieving dhcp-client-udeb  16%".
Ubuntu Live 5.10 loads and runs great.
Both CDs came from [www.linuxcd.org](www.linuxcd.org).
I'm running an AMD Athalon 2200+ with 725MB DDR-RAM.
Any Help, Ideas, Suggestions?

---

### Post by nanotube on 2006-01-27
use the ext3 filesystem, unless you have a good reason not to.  

tell ubuntu to "automatically partition" your drive - that will be sufficient.

if you dont want to install grub (the boot manager) and mess with mbr, i suppose you could just tell the installer not to install grub. although grub /should/ detect your linspire install automatically, anyway, and then you will be able to dual boot. i dont know what boot loader comes with linspire...

---

### Post by amohanty on 2006-01-27
> I want to add an 'old' hard drive,

As long as it is large enough (I think 5G should be enough - please verify) there should be no probs. What does Linspire use as bootloader - grub, lilo or something else?

AM

---

### Post by Ichido on 2006-01-29
It says "GRUB 1.5".

---

### Post by amohanty on 2006-01-29
Then you are all set to go. Ubuntu _will_ overwrite the bootloader with GRUB, but thats ok, since you already have grub. It will also automagically detect LInspire and add an entry for it in the grub menu file.

AM

---

