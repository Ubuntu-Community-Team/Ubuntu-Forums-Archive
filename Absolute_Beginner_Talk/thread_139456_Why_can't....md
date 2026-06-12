---
title: "Why can't..."
date: 2006-03-04
forum: Absolute Beginner Talk
---

### Post by Cousindaddy on 2006-03-04
...FreeBSD's bootloader boot Ubuntu? It finds and boots XP without any problem. I had been led to believe that the problem lies in GRUB...but now, I'm not so sure. 
Here is the output of  ***sudo fdisk -l***:
> [B]Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device   Boot  Start      End      Blocks         Id   System
/dev/hda1            1         2550    20482843+   7    HPFS/NTFS
/dev/hda2          2551     7140    36869175      f     W95 Ext'd (LBA)
/dev/hda3   *      7141     11190    32531625   83   Linux
/dev/hda4   *      11191   14886    29688120   a5   FreeBSD
/dev/hda5           2551     5651     24908751    7    HPFS/NTFS
/dev/hda6           6965     7140     1413688+   82   Linux swap / Solaris
[/B] Is it possible that the problem could lie with the *Boot* locations /dev/hda3 & /dev/hda4)? 

Any super-sleuths have any ideas?

(I've resigned myself to the fact that I'll probably have to reinstall Ubuntu...so I'm willing to entertain any suggestions short of *format c:*)

---

### Post by Pragmatist on 2006-03-04
> FreeBSD's bootloader boot Ubuntu
Why not use GRUB to boot all of the OSes on your computer?

---

