---
title: "RAID NOOB Question (filesystem sizes)"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by isaaca on 2008-01-04
I'm setting up a new system with two disks that I want to run a RAID1 array on. I found this guide: 
[http://users.piuha.net/martti/comp/ubuntu/en/raid.html](http://users.piuha.net/martti/comp/ubuntu/en/raid.html)
Setup was pretty straightforward and the machine is running smoothly. However, the free space listed in gnome doesn't seem right.

Here's my setup:

2x1TB drives (Listed 1TB, means 10^12 bytes = 931.51GB)

I partitioned both drives with

/dev/sda&b1: 20 billion-byte partition (18.63GB) (RAID, bootable)
/dev/sda&b2: 1 billion-byte partition (949MB) (RAID)
/dev/sda&b3: The rest of the drive (911.95GB) (RAID)

/dev/sda&b1 -> /dev/md0 (ext3) (mount point: /)
/dev/sda&b2 -> /dev/md1 (swap)
/dev/sda&b3 -> /dev/md2 (ext3) (mount point: /home)

After installing Ubuntu, gnome says that /home has 48KB used and 851.8GB free. 

Shouldn't the free space in /home be 911GB? Also, gParted lists /dev/sda&b3 as 911.95GB partitions with 14.53GB used. (free space = 897.42GB) and gParted says /dev/md2p1 is a 911GB partition.

I am running Gutsy amd64.
Is this normal for RAID? This is my first time using RAID and I'm still learning, but I haven't seen any mentions space overhead (and certainly didn't expect this). Or maybe I missed something obvious?

Thanks

---

### Post by pjkoczan on 2008-01-04
ext3 does reserve some disk space on a given partition for journaling and metadata. I think that software RAID also reserves disk space for RAID-array metadata. Because of these, you're not going to get 100% usable space out of a disk, at least not for user files.

I believe the inconsistency of reported numbers is due to gnome and gparted looking at different numbers. Gparted is likely looking at the raw partition size, and gnome is looking at the space available as reported by the formatted filesystem.

Can you open a terminal and paste the output of the 'df' command? It will list information on mounted filesystems (be sure to mount /home before running this). It *should* report roughly the same space as what gnome reports.

---

### Post by isaaca on 2008-01-04
Output of 'df -h' (human readable)

Filesystem            Size  Used Avail Use% Mounted on
/dev/md0               19G  2.7G   15G  16% /
varrun               1008M  208K 1008M   1% /var/run
varlock              1008M     0 1008M   0% /var/lock
udev                 1008M   84K 1008M   1% /dev
devshm               1008M     0 1008M   0% /dev/shm
lrm                  1008M   38M  971M   4% /lib/modules/2.6.22-14-generic/volatile
/dev/md2              898G  217M  852G   1% /home

It's the same as what gnome says. I guess loosing ~50GB to file system overhead seemed large to me, but it is actually ~6% of the total partition size. It wasn't that long ago that a 50GB drive was huge...

---

### Post by pjkoczan on 2008-01-04
Losing 5-6% of partition space to filesystem overhead is common. See [http://ubuntuforums.org/showthread.php?t=523939&page=2](http://ubuntuforums.org/showthread.php?t=523939&page=2) for a discussion on this.

---

### Post by isaaca on 2008-01-04
Yep, I did some more looking and learned a bit about reserved blocks under ext3. By default, 5% of the blocks are set aside and accessible only to root for use in case the file system becomes full. Apparently, the system can get squirrelly when out of space. The reserved blocks allow root to some breathing room when dealing with an overloaded system. I have to question the default value of 5% for large drives like mine. 50GB of 'breathing room' seems excessive. Also, it seems that the reserved blocks are mostly important on '/' part of the file system, so I set the reserved to 0% and I now have the full 911GB on my /home.

This thread was informative:
[http://ubuntuforums.org/showthread.php?t=215177](http://ubuntuforums.org/showthread.php?t=215177)

---

