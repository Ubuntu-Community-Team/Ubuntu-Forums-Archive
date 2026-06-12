---
title: "Windows XP, GRUB, and NTLDR (not the usual)"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by Eloyo on 2007-12-20
Hi everyone, i hope someone can help. 

I installed Ubuntu Gutsy, and configured it.

then, I installed Windows XP, and configured it too.

the partiution table is as follows:

   Device Boot      Start         End      Blocks   Id  System

/dev/hda1               1        3039    24410736   83  Linux
/dev/hda2            3040        3161      979965   82  Linux swap / Solaris
/dev/hda3   *        3162        4997    14747670    7  HPFS/NTFS

You've noticed that my windows installation is on the third partition. When windows installed, it prompted "You need to make this partition the active partition; you can still configure this later" 

Whatever, windows booted normally, but no linux in the boot menu. So i fixed de GRUB loader from the usual tutorials.

The windows' entry in Menu.lst is this:

title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

anyway, now GRUB works, but windows doesn't load. 
Loading windows throws "Can't find NTLDR"

Fixing the MBR from windows would only screw up GRUB again, so, how do i fix the windows booting without coming back to the same issue?

thank you everyone, 
!!

---

### Post by mikewhatever on 2007-12-20
Try it without chainloading and with correct partition, something like this:
title Microsoft Windows XP Professional
root (hd0,2)
savedefault
makeactive
chainloader +1

---

### Post by Eloyo on 2007-12-20
Allright, i tried that.

root (hd0,3) is it? 

and then it said: "ERROR 18: SELECTED CYLINDER EXCEED MAXIMUM SUPPORTED BY BIOS"

so i went back and did 

$ sudo grub-install --force-lba /dev/hda3

to allow grub to be installed on that cylinder, but now it just loads grub again when booting hda3 so i messed it up.

---

### Post by meierfra on 2007-12-20
> root (hd0,3) 

No, you needed to use "root (hd0,2)". Grub start counting at zero. So (hd0,2) is the third partition on the first hard drive.


> sudo grub-install --force-lba /dev/hda3

Bad idea. You destroyed the windows boot sector. If you have a Windows CD, you can fix the boot sector via "fixboot" in the recovery console.  Otherwise get Supergrub (see my signature). It also can fix your boot sector.

---

### Post by Eloyo on 2007-12-23
Allready fixed. 
Windows won't ever boot in a secondary partition in the hd.

I put window on hda
and linux in hdb1

and everything works fine.

---

