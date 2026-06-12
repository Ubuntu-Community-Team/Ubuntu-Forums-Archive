---
title: "Dual Boot install -- Grube loading error 2"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by panther_sn on 2007-08-22
Hi all, my dad just installed Ubuntu FF on his old PC currently he needs windows still on it so he had decided to Dual boot.

He has 2 HD's and installed Ubuntu onto the 2nd HD, it installed no problems but when he tries to boot, he gets 
Grub Loading:
Grub error 2

We are wondering where to go from here, as we loaded the Live CD and checked menu.lst and it seems to be correct, so we really aren't sure, and at this time he has no internet (he lives in the middle of nowhere) so We are willing to try things but I will be reading instructions over the phone, and typeing in his reults if nescesarry.

So anyway any help with this would be greatly appreciated

---

### Post by confused57 on 2007-08-23
If it's Windows XP & your dad has an XP install cd, he can overwrite grub's IPL with Window's IPL...boot up the XP install cd, press "r" for recovery, select his Window's partition, then enter the command "fixmbr" , without quotes.  If he has a Windows 98SE boot floppy, he can use "fdisk /mbr".

He might want to go into his bios setup and make sure the secondary hard drive is detected correctly & is set to "auto" or possibly "enabled".  He could also try reinstalling Ubuntu, but set his secondary drive to boot before the Windows drive in bios, before trying to reinstall.

The best solution would be the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
I realize he doesn't have an internet connection, so he couldn't download SGD himself.

---

### Post by panther_sn on 2007-08-23
Ok thanks for your response, and I will let him know, and if all else fails I'll download SGD and send him a copy.

---

