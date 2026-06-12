---
title: "Another boot problem after update"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by Tux Aubrey on 2006-09-17
I experienced a problem with the kernel update on 14 September and have been trawling the forum for something similar. It is not a graphics driver problem - I dont have nvidia graphics (SIS on an ABIT board).

Booting with the new kernel (2.6.15-26-386) hangs when trying to load the root filesystem. After 4 or 5 minutes waiting, it drops to a command line screen and says my primary linux partition (/dev/hda2) does not exist. (This is a dual boot XP/Windows P4 machine that has been working fine till now.)

My GRUB entries look fine.

This is the problem entry:

title Ubuntu, kernel 2.6.15-26-386
root (hd0,1)
kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro quiet splash
initrd /boot/initrd.img-2.6.15-26-386
savedefault
boot

Yet this still works fine:

title Ubuntu, kernel 2.6.15-23-386
root (hd0,1)
kernel /boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro quiet splash
initrd /boot/initrd.img-2.6.15-23-386
savedefault
boot

Strangely, booting with the "old" kernel after hanging with the new one results in a very unstable session - apps closing for no reason, freezes etc. A reboot seems to recover everthing OK.

Is there an option of re-installing the -26-386 kernel just to test whether it was a dirty install?

BTW. I have tried various work arounds suggested elsewhere (the noapci, pci=biosirq and the UUID rick) but none made any difference.

This is my first post and first time using Ubuntu, so be gentle with me.

---

### Post by petri on 2006-09-17
Can you boot to the recovery mode in some of the kernels you have? In that case you can follow instructions on this howto: [http://ubuntuforums.org/showthread.php?t=85917&highlight=386+686+k7](http://ubuntuforums.org/showthread.php?t=85917&highlight=386+686+k7)

In that way you should get a kernel that suits to your pc. BTW do you have a 64 bits Ubuntu? In that case it might be better do an reinstall with an ordinary 32 bits Ubuntu. There is too much problems with 64 bits Ubuntu for Desktop for a beginner.

---

### Post by Tux Aubrey on 2006-09-17
She floats! 

Many thanks Petri.  The 2.6.15-26-686 kernel booted fine.

I must have missed the info about the different flavours of kernel (Although I did know enough not to tamper with the 64 bit version).

---

### Post by petri on 2006-09-17
Glad to hear your pc is up and running again. :D

---

