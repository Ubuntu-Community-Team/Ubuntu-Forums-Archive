---
title: "Grub error 22"
date: 2005-12-05
forum: Absolute Beginner Talk
---

### Post by blackicerose on 2005-12-05
I recently installed Linux onto a partition i set aside. I agreed to installed GRUB as it would make things easier to boot into windows. The problem arrised when i decided to uninstall linux. I thought i could just format the partition so i did. This then mean that when i booted my computer i got the message..

GRUB Loading stage 1.5

GRUB loading, please wait...
Error 15

It then sits there and i am unable to do a thing. I am unable to get to windows XP or far enough to start into recovery mode. So i though i would install Linux again and see if there was a different way of uninstalling it. I did and GRUB loaded fine so i was able to boot to windows. I then decided that a format and the deletion of the partition would erase everything. I did this and restarted only to have the same thing happen but now i get..

GRUB Loading stage 1.5

GRUB loading, please wait...
Error 22

Now because i have deleted the partition i cant install Linux to get back in to windows plus there is no Linux.

Thanks in advance.

---

### Post by Ted D. on 2005-12-05
I am absolutely new to Linux and Ubuntu so you your getting this information from very newcomer.
My understanding is that you should insert your WinXP install CD, reboot let it load.
Select the Recovery Console option.
Select the Windows intallation you want to repair. May need Admin password.
A text console appears on the screen. Type fixmbr and fixboot.
Then restart removing the CD before it boots again. The fixmbr will put the Widows MBR back on to the disk and the fixboot command will rewrite the volume partition code.
Credit to: Petervan der Linden

TedD.

---

### Post by amohanty on 2005-12-05
From:

[http://www.gnu.org/software/grub/manual/grub.html#Stage2-errors](http://www.gnu.org/software/grub/manual/grub.html#Stage2-errors)

> 15 : File not found
    This error is returned if the specified file name cannot be found, but everything else (like the disk/partition info) is OK. 


This is probably because of a bad menu.lst file, please post it once you are done reinstalling ubuntu. Located at /boot/grub/menu.lst

> 22 : No such partition
    This error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk. 

The reason you get this is that you deleted the Ubuntu partition but left GRUB as it is. So now when GRUB loads it still has the definition of the Ubuntu partition and since it can find it, it convulses and dies.

I thing if you reinstall Ubuntu using the install CD, everything should be fine.

HTH
AM

---

