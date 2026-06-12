---
title: "Back to Setting Up RAID"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by AKA3Toes on 2007-07-22
[FONT="Times New Roman"][SIZE="3"][COLOR="DarkRed"]*---Just ran through everything in BIOS and then ran the Alternate Disk under text installation. Logged back into my account and GNOME shows I have three "unknown" disks again. Tried mdadm and I didn't even have it, so I downloaded and installed and this is what I get:*[/COLOR][/SIZE][/FONT]> page1@book:~$ sudo mdadm --query --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Sun Jul 22 11:58:53 2007
     Raid Level : raid0
     Array Size : 673982784 (642.76 GiB 690.16 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Jul 22 12:40:18 2007
          State : active
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 64K

           UUID : 52b73368:6043d43a:cbc66c3c:dcec90fd
         Events : 0.3

    Number   Major   Minor   RaidDevice State
       0     254        3        0      active sync   /dev/mapper/nvidia_fdacjeca3
       1       8       19        1      active sync   /dev/sdb3
       2       8       35        2      active sync   /dev/sdc3
page1@book:~$ cat /proc/mdstat
Personalities : [raid0] 
md0 : active raid0 dm-3[0] sdc3[2] sdb3[1]
      673982784 blocks 64k chunks
      
md2 : active raid0 dm-2[0] sdc2[2] sdb2[1]
      29302272 blocks 64k chunks
      
md1 : active raid0 dm-1[0] sdc1[2] sdb1[1]
      29302272 blocks 64k chunks
      
unused devices: <none>
page1@book:~$ 
[FONT="Times New Roman"][SIZE="3"][COLOR="DarkRed"][I]---So, what's next? Seems ol Ubuntu doesn't want to play nice, even though the devices are there and can be read. Am I on to mounting? Since this close, I really don't want to mess anything up so I am waiting for any response... then again, I now have a log here :P

---Since mdadm wasn't installed, what else might I be missing? Importance here would be something that may require restart after installation.[/I][/COLOR][/SIZE][/FONT]

---

### Post by jpkotta on 2007-07-22
```
0 254 3 0 active sync /dev/mapper/nvidia_fdacjeca3
```

That just doesn't seem right.  Do you know anything about that device node?  I have RAID 1, and I don't even have any /dev/mapper directory.  All the devices in my array are block devs (like /dev/sda1).

---

### Post by jpkotta on 2007-07-22
Nevermind, that's something to do with LVM, right?  Sure is a strange name...

You can probably mix raw disk partitions and LVs, but is it the correct thing to do?  On my file server, I made a RAID 5 array and built an LV on top of that.  I used the LVM to carve it up, and to be able to add new storage more easily.  On my desktop, I did RAID 1 and no LVM, though I'd think about using LVM there too if I ever had to re-do it.

mdadm is simply an interface for things that are built-in to a default Ubuntu system.  You do not need to restart.  I really wish they would put it on the Live CD for administration/recovery purposes.

I  would try mounting.  You can use the "-o ro" option to mount to keep it read-only, and that should prevent anything on the disks from being mangled.

---

### Post by AKA3Toes on 2007-07-23
[FONT="Times New Roman"][SIZE="3"][COLOR="DarkRed"][I]---I believe the nVidia software RAID handler is responsible for that. If I had the disk that came with the MoBo, maybe I wouldn't be having this problem.
:](*,)
---Though I am not the only one to purchase a 9620, I'm quite surprised I am the only one to run into this problem when installing Linux/Unix. I guess no one here has the nForce4 RAID chipset, or they're busy elsewhere. 

---Man the posts sure do scroll fast on this board. Maybe I should create a "/root" thread and carry post all my questions there. I'm afraid that if I ask another question, by tomorrow they'll both be burried 
:lolflag:[/I][/COLOR][/SIZE][/FONT]

---

### Post by jpkotta on 2007-07-23
How are you setting up your system?  Is it hardware RAID, hardware FakeRAID, software RAID?  I've found that software RAID is easier to set up.  This thread may help: [http://ubuntuforums.org/showthread.php?t=355814](http://ubuntuforums.org/showthread.php?t=355814).  It has links to some FakeRAID HowTos.

---

