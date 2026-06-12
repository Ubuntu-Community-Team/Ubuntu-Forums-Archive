---
title: "Help me, need to rebuild array I think"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by seepage87 on 2008-01-09
I used mdadm to build a RAID 5 out of 4 SATA disks.  I just added another SATA drive to my computer and now mdadm thinks one of my drives isn't working.

I don't think I broke the old drive in the install process since it's still listed find with fdisk.  My guess is this: the new SATA drive is sdb, which is what my old drive was.  mdadm sees the new drive isn't set up properly for the array and assumes it's broken, not knowing it should have been looking at sde now for that part of the array.

I really know nothing about how to work mdadm, so how do I point it in the right direction and rebuild my array?

Thanks so much.

---

### Post by AusIV4 on 2008-01-10
Run:```
cat /proc/mdstat
```
Give us the results.

PM me in a day or two if you don't get any other answers. I'm likely to forget about responding to this thread and not check back later.

---

### Post by seepage87 on 2008-01-10
Will do when I get home.  It may also be worth noting that now that I have messed this up if I detach the new HD, the array doesn't configure properly.  I don't know whether this indicates there's actually a problem, or if mdadm reconfigures to work with a degenerated array properly and can't automagically go back to the old way.  Any advice?

-A

---

### Post by seepage87 on 2008-01-10
Here's the cat /proc/mdstat

```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sda1[0] sdd1[3] sdb1[1]
      1465151808 blocks level 5, 64k chunk, algorithm 2 [4/3] [UU_U]
      
unused devices: <none>

```

This might be helpful too:

```
root@Tess:~# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c97fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000f04aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c026c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000beecc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sde: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x083eb5de

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1       29131   233994726    7  HPFS/NTFS
/dev/sde2           29132       30279     9221310   83  Linux
/dev/sde3           30280       30401      979965   82  Linux swap / Solaris

Disk /dev/md0: 1500.3 GB, 1500315451392 bytes
2 heads, 4 sectors/track, 366287952 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

```

And this:

```
root@Tess:~# mdadm -D /dev/md0 
/dev/md0:
        Version : 00.90.03
  Creation Time : Sun Dec  9 17:13:20 2007
     Raid Level : raid5
     Array Size : 1465151808 (1397.28 GiB 1500.32 GB)
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Jan 10 00:59:44 2008
          State : clean, degraded
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 62637b60:43cdfd6a:1cc26ced:e8d9c0eb
         Events : 0.46670

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       0        0        2      removed
       3       8       49        3      active sync   /dev/sdd1

```

---

### Post by AusIV4 on 2008-01-10
It looks like /dev/sdc1 has gotten dropped from the array.

Run
```
sudo mdadm /dev/md0 -a /dev/sdc1
```
And it should start rebuilding. I'd suggest running:
```
watch cat /proc/mdstat
```
so you can see how long until it's done. I'd try not to do much with your computer while it's rebuilding, as anything that requires hard drive access slows way down.

---

### Post by seepage87 on 2008-01-10
largely seems to be working, though I thought it would be a much faster process since nothing has been written to the array since the drive dropped.  I figured it would see it's there, do a quick check to see everything is alright, then be good as new.

---

### Post by seepage87 on 2008-01-11
Yeah, it worked.  I haven't restarted my computer yet to see if it holds, though I'll probably build a new config file anyway.

---

### Post by dgray_from_dc on 2008-01-23
Have a look here [http://ubuntuforums.org/showthread.php?t=667326](http://ubuntuforums.org/showthread.php?t=667326)

I'm waiting on an answer that may help to prevent this from happening again.

---

