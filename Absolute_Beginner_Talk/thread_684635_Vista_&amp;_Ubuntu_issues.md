---
title: "Vista &amp; Ubuntu issues"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by SyrusMX on 2008-02-01
Ok, here's what's up.

I had Windows Vista installed. I downloaded Ubuntu 7.10 and burned a live cd. Installed Ubuntu and manually setup a new partition and swap for Ubuntu. Installed just fine, booted into Ubuntu, now I can't see Vista. It's not mounted, and it doesn't show up in fdisk -l. I added ```
title Windows Vista
root (hd0,0)
savedefault
makeactive
chainloader +1
``` to the /boot/grub/menu.lst, but it booted into Ubuntu. I fiddled around with the hd numbers, and didn't find anything. I changed the root hd to 1,0 and it said it needed a boot disk. Didn't specify what OS it was looking at though, and I don't have a Vista boot disk.

Here's my current fdisk -l```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19080   153260068+  83  Linux
/dev/sda2           19081       19457     3028252+   5  Extended
/dev/sda5           19081       19457     3028221   82  Linux swap / Solaris
``` This is the 160gb partition I made for Linux in the Ubuntu installer. The drive is 250gb.

Question is, how do I get back to Vista without whacking my whole drive and re-installing Vista?

---

### Post by airbornemist6 on 2008-02-01
Install gnome partition manager and have it take a look at your partitions, it should detect the NTFS. If not, you probably messed up when installing and accidentally killed your Vista partition. I hope you didn't, I did that once upon a time... but with XP. It's not a fun thing to see.

---

### Post by Shinbu-Otaku on 2008-02-01
from what i understand, there is a Vista equivalent of the GRUB boot manager, and you need to try to re-install that. I may be wrong, maybe you need to reinstall GRUB on linux instead...

thts wat i'd do anyway...

---

### Post by SyrusMX on 2008-02-01
The NTFS partition does not show up in GParted.

So, I'm going to have to whack the drive then aren't I? And start over completely eh?

---

### Post by opscure on 2008-02-01
do you have unallocated space showing up in gparted?  If so you can format this for your vista install.  This means you will only have to reinstall windoze.  It will save you the time of having to reinstall ubuntu anyway.  Will vista even fit on 90GB??? :rolleyes:  bloatware.

---

