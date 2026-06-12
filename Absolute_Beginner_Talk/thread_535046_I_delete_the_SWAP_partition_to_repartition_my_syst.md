---
title: "I delete the SWAP partition to repartition my system, now what?"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2007-08-26
Hi
thank you for reading my post
I have deleted my swap partition to make some changes in my hard disk partitioning.
I did not tried to load the ubuntu after i delete the swap partition and i thought its better to ask about possible outcome and workaround before i try to run the OS.

I delete the SWAP partition and add its space to an Extended partition and now i want to add this partition to be used as SWAP.

I can editi any file in my linux EXT3 partition from my windows and i would be happy if you tell me what i should change to ensure that linux is using the new partition.


Thanks.

---

### Post by InGunsWeTrust on 2007-08-26
No changes need to be made in Ubuntu for it to use a new SWAP partition. As long as there is a SWAP it will detect where it is and use it (I know, much better than windows haha)

---

### Post by legolas_w on 2007-08-26
Thank you for reply.
But problem is that i have a solaris partition which its type is like linux SWAP and if i let lenux automatically select the partition it may ruin my Solaris partition.


thanks

---

### Post by InGunsWeTrust on 2007-08-26
So you have a filesystem installed on a partition of the type "linux-swap?" I didn't even know that was possible haha. If you have enough RAM you may not need a swap as swap is a way to compensate for not having enough RAM.

---

### Post by fairuz27 on 2007-11-20
I made the same mistake too. Accidentally delete my swap partition in WinXP. Re-create my linux swap partition using partition magic in windows. 
Is there a way to confirm the Ubuntu detected my swap partion just to be sure.
appreciate your help..

Thanks,

---

### Post by InGunsWeTrust on 2007-11-21
Windows doesnt use a swap partition it uses a swap file. It is at the root of the drive and it is called pagefile.sys. If you did indeed delete this then Windows will not boot and there is no way to restore it. As said above in a previous post the only thing you have to do to add a swap to linux is to make a partition formatted to the type linux-swap. I don't know if partition magic does it or not but I know the gnome partition editor does.

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

---

### Post by fairuz27 on 2007-11-21
Thanks for replying. Yes i did accidentally delete linux-swap partion in Windows MMC console.
I re-create linux-swap again using partition magic.
I don't have issue logging in both windows and ubuntu. The problem i think is that i dont think ubuntu detecting it. 
In Ubuntu, when i go to system monitor, in swap shows as zero mb.
In /proc/swaps - no entry

Only when i enter command : swapon /dev/sda7
then in system monitor shows i have about 1.1g of swap

I also tried using mkswap -c /dev/sda7  prior swapon /dev/sda1 but every time system restart, when i check in sys monitor - swap still shows as zero.

How do i ensure that the system detects my swap?

---

### Post by dstew on 2007-11-21
In the terminal, enter the command ```
sudo fdisk -l
```and post the result. That will show us what your disks look like to Ubuntu. Then we can help figure out what to do next.

---

### Post by fairuz27 on 2007-11-21
fairuz@fairuz-desktop:/etc/network$ sudo fdisk -l

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x59885988

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2343    18820116    7  HPFS/NTFS
/dev/sda2            2344       16795   116085690    f  W95 Ext'd (LBA)
/dev/sda3           16796       20023    25928910   83  Linux
/dev/sda5            2344       12542    81923436    7  HPFS/NTFS
/dev/sda6           12543       16650    32997478+   7  HPFS/NTFS
/dev/sda7           16651       16795     1164681   82  Linux swap / Solaris 

-------------------------------------------------------------------------
fairuz@fairuz-desktop:/proc$ cat swaps
Filename                                Type            Size    Used    Priority
fairuz@fairuz-desktop:/proc$ 
--------------------------------------------------------------------------

fairuz@fairuz-desktop:/proc$ cat meminfo
MemTotal:       515792 kB
MemFree:         87668 kB
Buffers:          7504 kB
Cached:         196000 kB
SwapCached:          0 kB
Active:         327160 kB
Inactive:        61276 kB
HighTotal:           0 kB
HighFree:            0 kB
LowTotal:       515792 kB
LowFree:         87668 kB
SwapTotal:           0 kB
SwapFree:            0 kB
Dirty:               4 kB
Writeback:           0 kB
AnonPages:      185012 kB
Mapped:          61788 kB
Slab:            20752 kB
SReclaimable:    11924 kB
SUnreclaim:       8828 kB
PageTables:       2100 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
CommitLimit:    257896 kB
Committed_AS:   680624 kB
VmallocTotal:   507896 kB
VmallocUsed:     42920 kB
VmallocChunk:   458228 kB
fairuz@fairuz-desktop:/proc$

---

### Post by fairuz27 on 2007-11-21
after i entered command: sudo swapon /dev/sda7
It detected my swap

------------------------------------------------------------------
fairuz@fairuz-desktop:/proc$ sudo swapon /dev/sda7
fairuz@fairuz-desktop:/proc$ cat meminfo
MemTotal:       515792 kB
MemFree:         85208 kB
Buffers:          7776 kB
Cached:         197016 kB
SwapCached:          0 kB
Active:         328000 kB
Inactive:        62208 kB
HighTotal:           0 kB
HighFree:            0 kB
LowTotal:       515792 kB
LowFree:         85208 kB
SwapTotal:     1164672 kB
SwapFree:      1164672 kB
Dirty:              96 kB
Writeback:           0 kB
AnonPages:      185496 kB
Mapped:          61808 kB
Slab:            20748 kB
SReclaimable:    11924 kB
SUnreclaim:       8824 kB
PageTables:       2104 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
CommitLimit:   1422568 kB
Committed_AS:   681072 kB
VmallocTotal:   507896 kB
VmallocUsed:     43496 kB
VmallocChunk:   458228 kB

fairuz@fairuz-desktop:/proc$ cat swaps
Filename                                Type            Size    Used    Priority
/dev/sda7                               partition       1164672 0       -1

---

### Post by fairuz27 on 2007-11-21
Hi,

Managed to resolved it on my own. 
Used Storage device manager (GUI)  to mount my swap partition without making manual changes to /etc/fstab file. figure it wasn't mount automatically when the system start up.

**Before:** 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=e6e7537f-171d-4883-83e3-a84874c0a325 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda7
UUID=36d0eeb5-9b01-441c-ad4d-56b894a9bf90**[COLOR="Red"] none[/COLOR]   **         swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

**After**
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/sda3
UUID=e6e7537f-171d-4883-83e3-a84874c0a325  /              ext3         defaults,errors=remount-ro  0  1  
# /dev/sda7
UUID=36d0eeb5-9b01-441c-ad4d-56b894a9bf90  none           swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec            0  0  
/dev/sda7                               **  [COLOR="Red"] /swap[/COLOR] **         swap         sw                          0  0  

Cheers,

---

