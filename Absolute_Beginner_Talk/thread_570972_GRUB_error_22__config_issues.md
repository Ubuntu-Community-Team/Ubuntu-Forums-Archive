---
title: "GRUB error 22 : config issues?"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by manij on 2007-10-08
Here is my system config 

HD1 : 160G total 

31  MB  unavailable partion (MBR) : came that way from DELL
110 GB XP home partion
~40 GB Had Linux installed (wouldn't boot1)


HD2 : 120 total
installed uduntu Dapper (works nicely!)

every thing was hunky dory until I formatted the 40Gb linux partition in HD1 to a FAT 32 partition using GPARTED. I did this to have a convenient way to move data in between the XP and Linux.

After doing this, I'm no longer able to boot my windows XP. I get a GRUB Error 22, something about hd0,1 not found.

Looking at the /boot/grub/menu.lst, the linux partition in HD1 is still showing

I interpret this as what ever I did with GPARTED is not being recognized by GRUB.

HOw do I fix this?

Here is my Fdisk -l output after messing with GPARTED


[B][I]Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 * 5 14179 113860687+ 7 HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 14409 115740261 83 Linux
/dev/sdb2 14410 14593 1477980 5 Extended
/dev/sdb5 14410 14593 1477948+ 82 Linux swap / Solaris[/I][/B]


I have no rpoblem booting from sdb1, but when I try to boot from sda1, I get error 22!

HELP!

Mani

---

### Post by rsambuca on 2007-10-08
Please do not make duplicate threads with the same question.

---

### Post by strabes on 2007-10-08
Please search the forums before posting. This question has been asked many, many times. Anyway, just reinstall GRUB. See the GRUB link in my signature.

---

