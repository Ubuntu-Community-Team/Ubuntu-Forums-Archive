---
title: "fdisk and gparted giving conflicting information"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by eternicode on 2008-01-07
OK, long post...

I have a MobiBlu B153 mp3 player; its setup allows me to use it like a normal 2GB flash drive.  The site I ordered it from is no longer live (go figure).

A while back, it completely froze up on me, and I had to have warranty work done on it.  When I got it back (long before I installed Ubuntu), it worked perfectly fine on Windows.  Now I've dug it out again, plug it into my USB port, and it pops up on my desktop as a flash drive, and I can drag-n-drop music as I wish.  However, while I was setting Amarok up to work with it, I noticed that it wasn't /dev/sdb1 that was mounted, but /dev/sdb :confused:

```
/dev/sdb on /media/disk-1 type vfat (rw,nosuid,nodev,noatime,uid=1000,utf8,shortname=lower)
```

I tried putting its UUID (obtained from blkid) in my fstab so I can let Amarok mount it:

```

andrew@Ximplix:~$ blkid /dev/sdb
/dev/sdb: UUID="D070-49DD" TYPE="vfat"

```
```

UUID=D070-49DD  /media/B153     vfat        defaults,noauto,users  0  0

```

But I can't even mount it from a command line:

```

andrew@Ximplix:~$ sudo mount /media/B153
mount: special device /dev/disk/by-uuid/D070-49DD does not exist
andrew@Ximplix:~$

```

Since it auto mounts when I plug it in (even more confusing...), I decide to pull all my data off of it onto my desktop, make a dd backup of the entire drive (just in case), and reformat the thing.

I pull GParted up (after unmounting the player), and it shows the whole thing as unallocated, which is not surprising.  However, when I go to create a new partition, it says I have to create a disklabel before I can continue.  I click "OK", and it starts rescanning the drive, with the same results as before (unallocated drive).  Same thing no matter how many times I try.

So I went into fdisk, and added a partition.  It defaulted to linux, I'm not sure how to change it to FAT32 from within fdisk:

```

andrew@Ximplix:~$ fdisk -l

Disk /dev/sdb: 2127 MB, 2127167488 bytes
66 heads, 62 sectors/track, 1015 cylinders
Units = cylinders of 4092 * 512 = 2095104 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1015     2076659   83  Linux

```

But gparted still says it's all unallocated. :confused:

A couple other things:
```

andrew@Ximplix:~$ sudo mount /dev/sdb1 /media/B153
mount: you must specify the filesystem type

```
using types ext3 and ext2 do me no good.

After running
```

andrew@Ximplix:~$ mkfs.vfat -f 2 -F 32 /dev/sdb1
mkfs.vfat 2.11 (12 Mar 2005)

```
I can mount it as vfat, but GParted still says "unallocated" :confused:

EDIT:
I just re-transferred the data to /dev/sdb1 and turned the thing on to a "Root: no file" screen.  So, obviously the firmware doesn't like partitions.  Great :p

---

### Post by ryanVickers on 2008-01-07
Sometimes drives like this will just randomly lock up and to fix it you can unplug it and plug it back in. Also, I would not recommend changing partitions on mp3 players; like you found out, they don't like it ;)

also, I believe the naming scheme of sda1, sda2, sda3, sdb1, sdb2, sdb3, goes like this - the letter goes up when its a new/different physical drive, and the number goes up per partition


to solve your problem, hopefully, I would try to set it back to the way it came....

---

### Post by eternicode on 2008-01-08
The drive wasn't locked up...I could mount/unmount /dev/sdb (or, after I added it, /dev/sdb1) and work with the files, but GParted didn't like the non-partitioned aspect of it.  Unless you're talking about the disklabel.  Didn't think to try unplugging it :)

I restored it from my dd backup image, and it works fine, just not with Amarok (yet...I'll try some other stuff to see if I can't get it working ;) )

I just found it strange that 1) it was using the entire drive, without partitions, and 2) a partition added manually through fdisk wasn't seen by gparted.

---

### Post by ryanVickers on 2008-01-08
some times they are strange... my Sansa e260 - it has most of the drive as FAT32, but theres this section on the end that's black and it seems to know theres something there but its screwed up or something.... but it isn't
Then in windows it sees it as one normal FAT32 drive (E:), and another "corrupt" drive (F:)

All this leads me to believe there is a special partition for the system thats kept separate from everything else... (although system files all show up on the E:...)

---

