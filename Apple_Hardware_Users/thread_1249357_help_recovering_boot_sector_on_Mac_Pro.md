---
title: "help recovering boot sector on Mac Pro"
date: 2009-08-25
forum: Apple Hardware Users
---

### Post by cammc on 2009-08-25
Hi,

I made the mistake of attempting to install Ubuntu 9.04 on a Mac Pro (running Leopard) without reading the HOWTO first, figuring it is just an Intel machine, and thus not installing rEfit first. This was asking for trouble, and I have got it: when I try to boot the Mac, it returns a GRUB error 15. The Mac in question is previous generation 8-core Mac. It originally had 2 hard disks, one of which was for the OS, and the other, a backup drive. I stuck a 3rd disk in, which I installed Ubuntu on. GRUB installed on the 1st drive, and broke the boot record. I have tried booting from the Leopard DVD, and reinstalling the OS (archiving all settings). This won't work, because the OS drive is too full, and I am doubtful whether HFS+ support from booting the Ubuntu CD can allow me to delete files safely from the OS disk to make room. It has also been tried to install Mac OS X on the backup drive, but that will not work, as the installer dies. So, I am wondering whether I can repair the boot sector using the rEfit bootable CD, or perhaps via GRUB (I doubt this, since I assume rEfit needs to work magic on it to enable it to boot properly), or perhaps I can boot off the OS X DVD as I would a Ubuntu Live CD, and somehow restore the boot sector. I humbly ask if anyone has any helpful suggestions? I would be be grateful, and realise I have my self to blame!

Cheers

---

### Post by cammc on 2009-08-26
To reply to my own thread: I removed the disk with Ubuntu installed on it and then Mac OS X was able to boot from a second drive that we installed Mac OS X on. The bootloader needs fixing on the original drive (the first one), so I will attempt to fix it with either an official Apple tool or rEfit.

---

