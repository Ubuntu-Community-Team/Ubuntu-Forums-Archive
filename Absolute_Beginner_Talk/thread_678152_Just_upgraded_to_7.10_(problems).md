---
title: "Just upgraded to 7.10 (problems)"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by kliljedahl on 2008-01-25
Just reinstalled XP & 6.06 Wednesday to go back to dual boot. Upgraded to 7.04 yesterday & found Automatix was for 7.10 so upgraded to 7.10 this morning. First problem is when I boot up I get all kinds of error messages. Finally reach the point where "control D" will allow me to log on. Now that I have there are issues with recognition of hard drives (I have 4) The 4th is not seen at all.
Under "places" there are two discs labeled "disc1", Identical, one labeled "disc 2" which is my second internal. "Disc 3" seems to to be the MS operating system, and one just labeled "Disc" which is my first external.

I ran sudo fdisk -l and got:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb74510e2

Device Boot Start End Blocks Id System
/dev/sda1 * 1 4081 32780601 7 HPFS/NTFS
/dev/sda2 9138 9729 4755240 5 Extended
Partition 2 does not end on cylinder boundary.
/dev/sda3 4082 9137 40612320 83 Linux
/dev/sda5 9356 9729 3004123+ 82 Linux swap / Solaris
/dev/sda6 9138 9355 1751022 82 Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffa8ffa8

Device Boot Start End Blocks Id System
/dev/sdb1 1 14593 117218241 83 Linux

Disk /dev/sdc: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e3c9c

Device Boot Start End Blocks Id System
/dev/sdc1 1 5005 40202631 83 Linux

Disk /dev/sdd: 122.9 GB, 122941341696 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x06eb1ada

Device Boot Start End Blocks Id System
/dev/sdd1 * 1 14946 120053713+ 83 Linux
kliljedahl@kliljedahl-desktop:~$

The one labeled sdd is the second external? That's the one I see nowhere else.

Also, videos no longer play in Firefox

---

### Post by kplaxmaster on 2008-01-25
Automatix messes up Ubuntu.  It isn't recommended software (if it was, it would happily be added in the repository.  However, it doesn't follow packaging guidelines and thus is frowned upon).

In fact, you don't even need Automatix anymore because of the new Ubuntu 7.10 features, which include the ability to install missing plug-ins right away.  In addition, ```
sudo apt-get install ubuntu-restricted
```gets you pretty much all you need that automatix gives you.  Automatix is a great utility for new linux users, but can cause a lot of problems when upgrading to new versions.

I suggest you download the live-cd of Ubuntu 7.10, backup all your necessary information from your old linux (you shouldn't have much since you said you just re-installed ubuntu recently).  This clean install will make sure you have no old config files anywhere lieing around from the older version.  In addition, you will notice Automatix won't be necessary.  This will ensure that automatix can't mess up your files anymore since you wont install it agian (right??).

Hope this helps a bit.

As for your fourth partition not showing up, lets see if anything gets fixed once you do a fresh-install from 7.10.

Although this isn't prob the best answer, its definitely something I would do.  It can't hurt to have a clean install of 7.10 instead of upgrading and upgrading again, and trying to fix  everything that automatix *could have* messed up.

Also, one of your hard-drives will be your "/" directory which doesn't show up.  Thus, if you have 4 hard-drives and boot into one of them (assuming that there isn't another mounted partition on the same hard-drive you are mounting), only 3 of them will show up since one is what linux is on, and the other 3 are needed to be mounted.

Hope this is a good starting point.

---

### Post by nowshining on 2008-01-26
uprading from an earlier version of ubuntu to gutsy is a no no, best bet is to - backup and do a full re-install of the system using 7.10.

---

### Post by kliljedahl on 2008-01-27
I've downloaded the 7.10 disc and now have another problem. I reinstalled windoze XP on thr first HD in order to go back to dual boot. When I insert the CD and go to install it doesn't seem to recognize the NTFS. It shows the entire disc as unallocated with an unrecognized label. There is no way to shrink the NTFS partition. My only option is to install on the whole disc.

---

### Post by Moop on 2008-01-27
Sometimes windows doesn't shut down right and leaves the hard drive unrecognizable to Ubuntu. I would boot back into XP and defragment the hard drive, then reboot into the live cd and see if it's recognized.

 If it's still unreadable then you will need to check the hard drive for errors. I use a Seagate Tools bootable cd. It works on most hard drives.

---

### Post by kliljedahl on 2008-01-27
Just did a total defrag & nothing hass changed. As much as I hate to I'll reinstall windoze and try again.

---

### Post by nowshining on 2008-01-27
remember install windows first - then ubuntu :)

---

