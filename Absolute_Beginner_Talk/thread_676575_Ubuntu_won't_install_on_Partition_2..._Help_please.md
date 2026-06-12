---
title: "Ubuntu won't install on Partition 2... Help please"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by Vapourstreak on 2008-01-23
hey

I'm having trouble installing ubuntu...

ive used the GParted on the LiveCD to create 2 partitons, both 93.15GB.  I've installed windows xp on Partition 1, but when I try to insatll ubuntu on the second (after I install Windows XP), there are some problems.  At 73%, the installer says '100% of /target has been used' and the installer quits.  I can't even go into Windows XP anymore because i assume the GRUB menu has been partially installed because it has the 'OS can not be booted'

please help

thanks

---

### Post by Sef on 2008-01-23
With the Ubuntu Live CD, do this:

Applications > Accessories > Terminal

then type in this code:

```
sudo fdisk -l
``` (Small L.)  Then post the results here.

---

### Post by Vapourstreak on 2008-01-23
It says

[QUOTE=sudo fdisk -l]

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2f622f61

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       12161    97675200    7  HPFS/NTFS
/dev/sda2           12162       24321    97675200   83  Linux

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x666f837b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4865    39078081    b  W95 FAT32
[/QUOTE]

---

### Post by ryanVickers on 2008-01-23
looks ok... it was just checking for disk errors and partition info.

Oh, and Grub as far as I remember isn't installed until everything else is done, its usually the last step.  But I suppose it's possible that was the problem...

As for why the installer failed, I would try the alternate CD, and see how that goes.  If there's still a problem, then something weird is up...

EDIT: This seems ridiculous, so I assume this is an error on my part, but are those partitions... overlapping???  That could be the problem if that is actually true; they are both destroyed... (But it is extremely unlikely)

---

### Post by Vapourstreak on 2008-01-23
this is the third time i formatted my drive and created the exact same partitions in GParted because of the same errors... well, it worked on hte same setting the first time, but I screwed up the panels, so I decided to re install it.  IT didnt work after that.  This is the second Ubuntu disk i tried.  after the first disk didnt work 2 times, I made a new one.  Same error.  checked the cd for defects, there were none

---

### Post by ryanVickers on 2008-01-23
Well, I have no clue, if you've tried both disks, the hard drive is good, and your computer is not overheating, then it should work!! :mad:
(the overheating thing is more of a joke btw, unless your area is unusually hot...)

---

### Post by Vapourstreak on 2008-01-23
ill take screenies and post them up in a sec

---

### Post by Vapourstreak on 2008-01-24
nvm.  i tried using hte 'use largest continuous space' instead of 'sda partition 2 100%' option and it worked.  yay :D

---

