---
title: "grub error 25"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by dave.galaxian on 2008-01-02
ok i know i have done wrong i have vista on pc new build i have installed gutsy now all i get in error 25 i have seen there are problems with vista but cant it to boot into vista i installed onto a seperate hdd is there a easy way or should i start again 
thanks

---

### Post by spiderbatdad on 2008-01-02
try hitting the esc key when you start your computer to get to boot options. there you might be able to select other operating system. I'm sory i could not understand the question very well.

---

### Post by dstew on 2008-01-02
Boot the Ubuntu Live CD, open a terminal window, and enter the command```
fdisk -l
```. That should tell us what your partitions look like. Then we might have to do some fixing up.

---

### Post by dave.galaxian on 2008-01-02
ok this what i get

fdisk: invalid option -- L

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

and i get this for just fdisk

ubuntu@ubuntu:~$ fdisk

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...
hope this will help i feel like i real idiot not reading help files before jumping in :)

---

### Post by torgrot on 2008-01-02
Uh that's fdisk with a lowercase "L" Linux is case sensitive. 
```
fdisk -l
```

If you are getting a grub error 25 take a look at this page [http://users.bigpond.net.au/hermanzone/p15.htm#25](http://users.bigpond.net.au/hermanzone/p15.htm#25)

torgrot

---

### Post by dave.galaxian on 2008-01-02
sorry forgot to say -l does not do anything hense the uppercase L above

---

### Post by spiderbatdad on 2008-01-02
fdisk<space>-l

---

### Post by dave.galaxian on 2008-01-02
yea i did put the space in just tryed uppercase because i got nothing from lower case
just going to try rebooting and have a look at the bios see if that cures it 
thanks for the help but may be back yet

cheers

---

### Post by jken146 on 2008-01-02
From the live CD, ```
sudo fdisk -l
``` should work.

---

### Post by dave.galaxian on 2008-01-03
still having booting problems i have try'd booting from diff hdd from bios still get same error this what i get from the last posted command 
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 20.4 GB, 20404101120 bytes
255 heads, 63 sectors/track, 2480 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf74df74d

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2480    19920568+   7  HPFS/NTFS

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2a412a40

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23588   189470578+  83  Linux
/dev/sda2           23589       24321     5887822+   5  Extended
/dev/sda5           23589       24321     5887791   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664832 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7df36155

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4865    39078081    7  HPFS/NTFS

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4af24af2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9728    78140128+   7  HPFS/NTFS
ubuntu@ubuntu:~$ 


pointers gratfully received

---

### Post by dave.galaxian on 2008-01-03
sorted i put in a hdd from a old pc it had win2000 on it i was going to format it looks like it was stopping things from working once i had disconnected it linux fired up thanks to all who sent reply's they where a help in pointing me in right direction :))

---

