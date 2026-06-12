---
title: "Grub restore problem"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by n0n@m3 on 2008-01-23
Hello,
I have two hard disks, one containing Windows XP and the other contaning Ubuntu 7.10. Grub has always been my boot loader. Some days ago that my XP-containing disk crashed,i realized that i wasn't able to boot Ubuntu for some reason.
Today i installed a fresh copy of Windows XP in a new disk and tried to restore the grub using a live cd, following these-> [(link)]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") instructions and everything seemed to be ok (i got no error messages), but when i try to boot either Ubuntu or Windows i get an Error 17: Could not mount the selected partition..

May someone help me please..?

PS: I had installed a 64bit version of ubuntu, but i use a live cd for the i386 version.. I hope that this is ok..

---

### Post by wolfen69 on 2008-01-23
is your bios set to boot to the xp disk? try switching the drive order.

---

### Post by n0n@m3 on 2008-01-24
I am able to boot Windows by changing the BIOS hard disk boot priority to the disk that I've installed them.
But when i try to boot them through GRUB, or boot Ubuntu through GRUB, i get the Error 17 problem..

---

