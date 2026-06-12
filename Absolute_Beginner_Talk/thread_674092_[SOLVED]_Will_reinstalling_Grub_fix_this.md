---
title: "[SOLVED] Will reinstalling Grub fix this?"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by skymera on 2008-01-21
well i run 2 systems, Ubu and XP.

both on seperate drives :)

when i boot from my ubuntu drive (default) and load up GRUB.
When i choose XP it says

```
 NTLDR is missing Press CTRL+ALT+DELETE to restart 
```

yet if i boot from the windows drive, it boots.
how strange.


im lead to believe Grub is the culprit. 
is this true?

---

### Post by gangrelsurf on 2008-01-21
That is strange.
No solid answers here, but maybe some hunches:

NTLDR is the NT boot loader, so it sounds like grub is doing proper and booting the xp disk, then xp is failing.
[http://en.wikipedia.org/wiki/NTLDR](http://en.wikipedia.org/wiki/NTLDR)

I havn't looked at that wiki article, but maybe the NTLDR is part-of/pointed-to-on the mbr? Just a hunch, and when you boot off of the grub mbr some reference is lost? Dunno, but it sounds like grub is working.

Maybe you should change your root reference for the XP option in your /boot/grub/menu.lst to point to the XP disk?

Ah - I see you are beta testing sp3. I'd definitely blame microsoft. ;)

---

### Post by skymera on 2008-01-21
lol

it is weird.
i can boot windows from the windows drive.
but not the ubuntu drive. =S

i'll check my grub menu.lst now

---

### Post by bumanie on 2008-01-21
This may help 
[http://tinyempire.com/notes/ntldrismissing.htm](http://tinyempire.com/notes/ntldrismissing.htm)

---

### Post by torgrot on 2008-01-21
If you can boot windows off the windows drive but not from grub, there is a problem with grub.  Even though it says NTLDR is missing since you can boot from that drive into windows, it obviously is there.  Can you post the output of sudo fdisk -l ( that's a lower case L) and the contents of your menu.lst

torgrot

---

### Post by skymera on 2008-01-22
sure

```
 scott@scott-desktop:~$ sudo fdisk -l
[sudo] password for scott:

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19452   156248158+   7  HPFS/NTFS

Disk /dev/sdb: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d9a32

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5957    47849571   83  Linux
/dev/sdb2            5958        6079      979965   82  Linux swap / Solaris
/dev/sdb3            6080       18241    97691265    f  W95 Ext'd (LBA)
/dev/sdb5            6080       18241    97691233+   7  HPFS/NTFS

Disk /dev/sdc: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x230c85ca

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       10011    80413326    7  HPFS/NTFS
scott@scott-desktop:~$ 

```

---

### Post by Sef on 2008-01-22
> /dev/sda1   *           1       19452   156248158+   7  HPFS/NTFS

> /dev/sdc1   *           1       10011    80413326    7  HPFS/NTFS

Which hard drive contains XP?  Is the other one a home partition?  If not, what is it?  It looks like GRUB is pointing to the wrong partition.

---

### Post by skymera on 2008-01-22
sda1 was XP, sorry SDC1 is my external.

and i fixed it :)
it was either switching off my external drive, i doubt that.

but it turns out my wndows drive was turned off from booting in the BIOS
well i enabled it to boot and now i can choose Windows from Grub and woot it boots :)

thanks all

---

