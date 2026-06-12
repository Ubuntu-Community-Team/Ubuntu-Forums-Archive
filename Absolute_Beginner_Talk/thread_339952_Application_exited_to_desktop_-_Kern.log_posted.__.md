---
title: "Application exited to desktop - Kern.log posted.  Am I REALLY out of memory?"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by emarkay on 2007-01-16
"Jan 16 12:08:56 localhost kernel: [17186885.596000] oom-killer: gfp_mask=0x280d2, order=0
Jan 16 12:08:57 localhost kernel: [17186885.596000] Mem-info:
Jan 16 12:08:57 localhost kernel: [17186885.596000] DMA per-cpu:
Jan 16 12:08:57 localhost kernel: [17186885.596000] cpu 0 hot: low 0, high 0, batch 1 used:0
Jan 16 12:08:57 localhost kernel: [17186885.596000] cpu 0 cold: low 0, high 0, batch 1 used:0
Jan 16 12:08:57 localhost kernel: [17186885.596000] DMA32 per-cpu: empty
Jan 16 12:08:57 localhost kernel: [17186885.596000] Normal per-cpu:
Jan 16 12:08:57 localhost kernel: [17186885.596000] cpu 0 hot: low 0, high 186, batch 31 used:29
Jan 16 12:08:57 localhost kernel: [17186885.596000] cpu 0 cold: low 0, high 62, batch 15 used:55
Jan 16 12:08:57 localhost kernel: [17186885.596000] HighMem per-cpu: empty
Jan 16 12:08:57 localhost kernel: [17186885.596000] Free pages:        3576kB (0kB HighMem)
Jan 16 12:08:57 localhost kernel: [17186885.596000] Active:83922 inactive:3459 dirty:0 writeback:0 unstable:0 free:894 slab:4055 mapped:82365 pagetables:419
Jan 16 12:08:57 localhost kernel: [17186885.596000] DMA free:1516kB min:104kB low:52kB high:104kB active:10732kB inactive:152kB present:16384kB pages_scanned:11435 all_unreclaimable? yes
Jan 16 12:08:57 localhost kernel: [17186885.596000] lowmem_reserve[]: 0 0 366 366
Jan 16 12:08:57 localhost kernel: [17186885.596000] DMA32 free:0kB min:0kB low:0kB high:0kB active:0kB inactive:0kB present:0kB pages_scanned:0 all_unreclaimable? no
Jan 16 12:08:57 localhost kernel: [17186885.596000] lowmem_reserve[]: 0 0 366 366
Jan 16 12:08:57 localhost kernel: [17186885.596000] Normal free:2060kB min:2392kB low:1196kB high:2392kB active:324956kB inactive:13684kB present:375480kB pages_scanned:0 all_unreclaimable? no
Jan 16 12:08:57 localhost kernel: [17186885.596000] lowmem_reserve[]: 0 0 0 0
Jan 16 12:08:57 localhost kernel: [17186885.596000] HighMem free:0kB min:128kB low:32kB high:64kB active:0kB inactive:0kB present:0kB pages_scanned:0 all_unreclaimable? no
Jan 16 12:08:57 localhost kernel: [17186885.596000] lowmem_reserve[]: 0 0 0 0
Jan 16 12:08:57 localhost kernel: [17186885.596000] DMA: 1*4kB 1*8kB 0*16kB 1*32kB 1*64kB 1*128kB 1*256kB 0*512kB 1*1024kB 0*2048kB 0*4096kB = 1516kB
Jan 16 12:08:57 localhost kernel: [17186885.596000] DMA32: empty
Jan 16 12:08:57 localhost kernel: [17186885.596000] Normal: 235*4kB 2*8kB 1*16kB 2*32kB 0*64kB 0*128kB 0*256kB 0*512kB 1*1024kB 0*2048kB 0*4096kB = 2060kB
Jan 16 12:08:57 localhost kernel: [17186885.596000] HighMem: empty
Jan 16 12:08:57 localhost kernel: [17186885.596000] Swap cache: add 0, delete 0, find 0/0, race 0+0
Jan 16 12:08:57 localhost kernel: [17186885.596000] Free swap  = 0kB
Jan 16 12:08:57 localhost kernel: [17186885.596000] Total swap = 0kB
Jan 16 12:08:57 localhost kernel: [17186885.596000] Free swap:            0kB
Jan 16 12:08:57 localhost kernel: [17186885.620000] 97966 pages of RAM
Jan 16 12:08:57 localhost kernel: [17186885.620000] 0 pages of HIGHMEM
Jan 16 12:08:57 localhost kernel: [17186885.620000] 1982 reserved pages
Jan 16 12:08:57 localhost kernel: [17186885.620000] 23926 pages shared
Jan 16 12:08:57 localhost kernel: [17186885.620000] 0 pages swap cached
Jan 16 12:08:57 localhost kernel: [17186885.620000] 0 pages dirty
Jan 16 12:08:57 localhost kernel: [17186885.620000] 0 pages writeback
Jan 16 12:08:57 localhost kernel: [17186885.620000] 82368 pages mapped
Jan 16 12:08:57 localhost kernel: [17186885.620000] 4055 pages slab
Jan 16 12:08:57 localhost kernel: [17186885.620000] 419 pages pagetables
Jan 16 12:08:57 localhost kernel: [17186885.620000] Out of Memory: Killed process 10609 (seamonkey-bin)."

I was doing some researching and had multiple tabs and windows open - but I thought that Linux used much less memory than Windows.  I don't remember seeing this error in Win98SE before ("Out of memory, Close other applications to continue" (I recall)) whils doing similar searches.

What's going on?

---

### Post by emarkay on 2007-01-17
ANYONE?

I added the system monitor and as of now - new boot, this is what it says. 

45% in use by programs
50% in use as cache
no swap space
20% average load 

With 349Megs of RAM, can an idle Ubuntu use 45% memory???

I did some research and found that "clamd" (is that the ClamA/V?) is the biggest 'hog' just sitting there  using 22M of VM and 18 of RAM, and  I forgot about my SETI program (I thought I had it set for 'only as available' - I must check that) is using 46/30.  
Also now, my browser is using 92/37.

Didn't think I'd need to add RAM in Linux!!!!!

---

### Post by pandisv on 2007-01-17
To begin with, you surely don't have 349MB of RAM. Assuming you have 384, depending on what you do it could or could not be sufficient. Since adding more RAM evidently is not an option, you should strongly consider adding some swap space. Make room for a decent swap partition (think >100MB) to make sure things don't get killed when you run out. 

How many things do you have running in the background? AFAIK a default boot uses ~ 100-150MB of RAM (excluding cache, which is obviously purged when you begin running out of RAM).

---

### Post by emarkay on 2007-01-17
Yea typo - 384 megs - SM shows 375.2MiB.

I can add another 128Meg if I swap an existing SIMM for a new one, but I'd rather not.

I have 512Megs of swap space and using the toolbar System monitor applet I have NEVER seen ANY swap space being used!

I have attached my memory usages screens.

---

### Post by pandisv on 2007-01-17
Jan 16 12:08:57 localhost kernel: [17186885.596000] Free swap = 0kB
Jan 16 12:08:57 localhost kernel: [17186885.596000] Total swap = 0kB
Jan 16 12:08:57 localhost kernel: [17186885.596000] Free swap: 0kB

 
Are you sure your swap is being mounted correctly ? Try 'df -ah' in a terminal window ...

---

### Post by emarkay on 2007-01-18
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda7              36G  3.1G   32G   9% /
proc                     0     0     0   -  /proc
/sys                     0     0     0   -  /sys
varrun                188M   92K  188M   1% /var/run
varlock               188M  4.0K  188M   1% /var/lock
procbususb               0     0     0   -  /proc/bus/usb
udev                  188M  128K  188M   1% /dev
devpts                   0     0     0   -  /dev/pts
devshm                188M     0  188M   0% /dev/shm
lrm                   188M   18M  170M  10% /lib/modules/2.6.15-27-686/volatile
/dev/hda5              56G   49G  7.7G  87% /media/hda5
/dev/hdb1             4.9G  494M  4.4G  10% /media/hdb1

Um I don't see anything called swap there.  And I have installed 4 PC's with Ubuntu in the exact same manner - this is the only one available at the moment.

I used the Gparted disk to repartition my disks on all PC's.  These are ext3 filesystems and  I added the swap partition  at that time.  When I installed Ubuntu,I had to manually set up partitions but I just "OK" the settings - I THINK I had to reformat the ROOT and SWAP partitions to get it tp proceed though.

Thanks.

BTW: In Disks Manager, the SWAP is dev/hda8 and is 1004.03Mib, filesystem is "memory swap" and the FORMAT button is greyed out.

Yea looks lik no swap.  Can you tell me how to test further and if it's not correct how to fix it. - No let me try this on my own.

Found this post:
[http://ubuntuforums.org/showthread.php?t=321807&highlight=enable+swap](http://ubuntuforums.org/showthread.php?t=321807&highlight=enable+swap)
Did the following tests:

sudo swapon -v /dev/sda8
Password:
swapon on /dev/sda8
swapon: cannot stat /dev/sda8: No such file or directory
-desktop:~$ sudo swapon -av
-desktop:~$
*****
-desktop:~$  ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2007-01-18 10:14 0000-0E7F -> ../../hda7
lrwxrwxrwx 1 root root 10 2007-01-18 10:14 0000-0E86 -> ../../hda6
lrwxrwxrwx 1 root root 10 2007-01-18 10:14 0f16ecb5-8908-43dd-84f4-8ce6962c6 ac4 -> ../../hda8
lrwxrwxrwx 1 root root 10 2007-01-18 04:14 1271-15EF -> ../../hdb5
lrwxrwxrwx 1 root root 10 2007-01-18 04:14 274A-11EF -> ../../hda1
lrwxrwxrwx 1 root root 10 2007-01-18 04:14 4349-15E8 -> ../../hdb1
lrwxrwxrwx 1 root root 10 2007-01-18 10:14 74C0-22AC -> ../../hda5
******
-desktop:~$ sudo fdisk -l

Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2432    19535008+   c  W95 FAT32 (LBA)
/dev/hda2            2433       24792   179606700    f  W95 Ext'd (LBA)
/dev/hda5            2433        9728    58605088+   c  W95 FAT32 (LBA)
/dev/hda6           14593       24792    81931468+   c  W95 FAT32 (LBA)
/dev/hda7            9729       14464    38041888+  83  Linux
/dev/hda8           14465       14592     1028128+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdb: 15.3 GB, 15303075840 bytes
255 heads, 63 sectors/track, 1860 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1         638     5124703+   b  W95 FAT32
/dev/hdb2             639        1860     9815715    f  W95 Ext'd (LBA)
/dev/hdb5             639        1860     9815683+   b  W95 FAT32
*********
-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda7       /               ext3    defaults,errors=remount-ro,data=writeback,noatime 0
#/dev/hda1       /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0 1
/dev/hda5       /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1#/dev/hda6       /media/hda6     vfat    defaults,utf8,umask=007,gid=46 0 1
/dev/hdb1       /media/hdb1     vfat    defaults,utf8,umask=007,gid=46 0       1#/dev/hdb5       /media/hdb5     vfat    defaults,utf8,umask=007,gid=46 0 1
#/dev/hda8       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
******

Found a possibility based on that post - Hmmm - let me remove that "#" 
Back while I reboot.

---

### Post by emarkay on 2007-01-18
Nope - that opnl enabled a disk I didn't want Linux enabled.
Let me remove ALL the "#" now to test and see.
Back in a few.

---

### Post by jvc26 on 2007-01-18
Another thing could be the output of
```

top

```
```

free

```
That will tell you if you have any swap or if it is being used (the output from 'free')
top will give you the output of what resource is using what.
Il

---

### Post by emarkay on 2007-01-18
Well lookee here - I think I got it.     

-desktop:~$ free
             total       used       free     shared    buffers     cached
Mem:        384192     307112      77080          0       6472     178216
-/+ buffers/cache:     122424     261768
Swap:      1028120          0    1028120
*******
-desktop:~$ top
top - 11:58:08 up 3 min,  1 user,  load average: 1.02, 0.77, 0.32
Tasks:  91 total,   1 running,  90 sleeping,   0 stopped,   0 zombie
Cpu(s): 10.6% us,  2.0% sy,  0.0% ni, 87.4% id,  0.0% wa,  0.0% hi,  0.0% si
Mem:    384192k total,   356448k used,    27744k free,     7040k buffers
Swap:  1028120k total,        0k used,  1028120k free,   203556k cached


Of course WHY this happened and why I haven't noticed this in almost 6 months is a mystery.

I must pull those PC's I did and see if THEY are cache disabled, too.

One would thing that there would be some "indicator" SOMEWHERE as a "reminder" that you are running Ubuntu "cacheless".  I wonder how many others are "cache-challenged", too?

THANKS!

---

### Post by SMS on 2007-01-22
so how do you enable cache

---

