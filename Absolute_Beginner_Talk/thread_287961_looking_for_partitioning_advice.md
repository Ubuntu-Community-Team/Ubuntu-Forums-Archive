---
title: "looking for partitioning advice"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by mendingo84 on 2006-10-29
i want to use separate partitions for /home and the rest of my edgy. how much space would the OS require? from a 20Gigabytes for example, how big should /home be and how much for the rest of the operating system? the idea is to keep my settings if i have to reinstall...

---

### Post by Bachstelze on 2006-10-29
10 GB is generally more than enough for the root partition. For the /home, it depends on what you're gonna store in it ;)

---

### Post by ThrobbingBrain66 on 2006-10-29
my edgy install (minus my /home partition) takes up about 2.6GBs.  You could partition in this manner.

5GBs /root
14GBs /home
1GB swap

---

### Post by hyby on 2006-10-29
howdy,

for your swap space, double your ram size and set it as that. 
i didnt really bother with /home partition as i only allocated 5 gig to linux.

So my setup is as follows:
8.8gig  ext3  /
1.9gig  swp
 

with this setup everything has been dandy. After i get my soundcard working, i ditching windoz for good. As i can write music without sound!

---

### Post by bodhi.zazen on 2006-10-29
/home is where you will store your user data. Make it as large as possible.

/swap = ram X2, max 2 Gb.
/ (root) 5 Gb.
/home 13 Gb.

You will need a bigger root if you plan on installing a lot of applications. Perhaps 10 Gb.

---

### Post by Bachstelze on 2006-10-29
"swap = RAM x2"

Not if you have enough RAM. I have 2 GB RAM, I created a 512 MB swap just in case and it's always 95+% free...

---

### Post by bodhi.zazen on 2006-10-29
> **HymnToLife said:**
> "swap = RAM x2"

Not if you have enough RAM. I have 2 GB RAM, I created a 512 MB swap just in case and it's always 95+% free...

I do not disagree. ram x2, max 2 Gb is the "conservative" advice and "enough RAM" depends on what applications you run.

I also have 2 Gb ram, but I, at times, run a memory (ram) intensive application and will then spill over to swap (FYI it is a windows application running in wine so memory utilization is "sloppy").

You will not need swap if your RAM >> applications need for memory.

---

### Post by housam on 2006-11-03
Hi every one, can I use the Dapper cd to resize my partitions as I already installed it together with win-xp. it only took 2.1G from a 20G free partition and left the rest unrecognised by either OS. I've downloaded the Gparted live cd but I don't know how to install it or use it. any help.
housam

---

### Post by bodhi.zazen on 2006-11-03
> **housam said:**
> Hi every one, can I use the Dapper cd to resize my partitions as I already installed it together with win-xp. it only took 2.1G from a 20G free partition and left the rest unrecognised by either OS. I've downloaded the Gparted live cd but I don't know how to install it or use it. any help.
housam

Perhaps it is as easy as you can only haev 4 primary partitions.

GParted is a live CD. You place it in the CDROM and boot it.

[See here](http://ubuntuforums.org/showthread.php?t=282018) for a partitioning overview.

If not, can you post your partitioning table?

---

### Post by housam on 2006-11-04
Hi, my partition table is as follows :I've 2 HDD , one for win-xp and the other for Dapper.

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               2        1275    10233405    f  W95 Ext'd (LBA)
/dev/hda2   *        1276        4997    29896965    c  W95 FAT32 (LBA)
/dev/hda5               2        1275    10233373+   b  W95 FAT32

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        9729    78148161    f  W95 Ext'd (LBA)
/dev/hdb5               2        2264    18177547+   b  W95 FAT32
/dev/hdb6            2552        5101    20482843+   7  HPFS/NTFS
/dev/hdb7            5102        9729    37174378+   7  HPFS/NTFS
/dev/hdb8   *        2265        2534     2168743+  83  Linux
/dev/hdb9            2535        2551      136521   82  Linux swap / Solaris

Partition table entries are not in disk order

/dev/hdb5 is the rest of the 20G partition that I want to merge with the boot drive /dev/hdb8 to enable more software installation.  

thanx 
Housam

---

### Post by bodhi.zazen on 2006-11-04
I do not think you can merge the space directly.

You would need to re-partition hdb5,6,7, and 8.

---

### Post by housam on 2006-11-05
It means that I'll loose all the data on these partitions including the ubuntu itself.or resizing through Gparted can solve it?
housam

---

### Post by bodhi.zazen on 2006-11-05
You can try to move the partitions (with GParted). I have not done this. Normally you add free space to a partitions if the free space is adjacent, usually following, the partition to which you want to add.

In your case hdb5 is not adjacent to hdb8, this is problematic.

---

### Post by housam on 2006-11-07
Bad news. I've used Gparted live CD and made some actions i.e.
- shrinking hdb5 to the min. leaving about 16G unallocated behind
- enlarging and moving hdb8 to be about 18.5G.
- enlarging the swap hdb9 to about 1G.
- start enabling the choices.
** after finishing the job there was an error message that an error happened during writing to disk - save details.
*** after saving details every thing was gone. the whole disk was empty. 76G transfered to be unallocated.NO UBUNTU , NO DATA and the other OS unable to start either.

that's what happened yesterday. I'll start today repartitioning the disk and reinstall Dapper.no problem but the data I've lost was very valuable.
Any idea how to enlarge the Dapper partition from the begining.

---

### Post by bodhi.zazen on 2006-11-07
Your data is likely recoverable if you:

[list=number][*]Do not format the disk.
[*]Restore the partition table to what it was before you modified it with Gparted.
[*]You may have to do this with fdisk (you have the start and end blocks from your previous post)[/list]

If you get your data back, BACKUP BEFORE YOU EDIT YOUR PARTITION TABLE.

(Sorry, I thought backup was self evident and I should have advised a back up sooner).

If needed: 
```
sudo fdisk /dev/hdb
```

[How to fdisk](http://community.linux.com/howtos/Partition/partition-5.shtml)

Write the partition table with fdisk. DO NOT FORMAT.

---

### Post by handy on 2006-11-07
If you have > or = a gig of ram you really don't need to double it to get your safe swap partition size.

One gig swap is plenty, it will rarely ever be used at all.

---

### Post by handy on 2006-11-07
> **housam said:**
> Bad news. I've used Gparted live CD and made some actions i.e.
- shrinking hdb5 to the min. leaving about 16G unallocated behind
- enlarging and moving hdb8 to be about 18.5G.
- enlarging the swap hdb9 to about 1G.
- start enabling the choices.
** after finishing the job there was an error message that an error happened during writing to disk - save details.
*** after saving details every thing was gone. the whole disk was empty. 76G transfered to be unallocated.NO UBUNTU , NO DATE and the other OS unable to start either.

that's what happened yesterday. I'll start today repartitioning the disk and reinstall Dapper.no problem but the data I've lost was very valuable.
Any idea how to enlarge the Dapper partition from the begining.

Did you try to salvage the data?

Don't give up without a good fight!

Have a look here too:

$ **man  e2fsck 8**

---

### Post by housam on 2006-11-07
Kindly note that I'm replying through my office computer because my home one is dead ( no bootibg from either OS).
Do you mean that I can recover my hdb partitions using fdisk.
Do I have to use the windows starting floppy or the ubuntu live cd to write to fdisk?

---

### Post by handy on 2006-11-07
hi, because of the seriousness of your problem, if I were you I would post description of your situation in the **Hardware** sub-forum.

& then patiently wait until you are confident in the help you are given, ***before you do anything***.

These kinds of problems can be salvagable, but doing one thing can mean that it is no longer salvagable.

With a little good fortune, & patience, you may yet get all your data back.

---

### Post by handy on 2006-11-07
Sorry double post :confused:  :)

---

### Post by housam on 2006-11-07
i'm using a Desktop compatable : P4 ,3.0 GHz, 512 DDR ,128 VGA , 2 HDD one 40G primary master & the other is 80G primary slave ( which has the problem ). partitions was as described in my previous posts.

---

### Post by bodhi.zazen on 2006-11-07
> **housam said:**
> Kindly note that I'm replying through my office computer because my home one is dead ( no bootibg from either OS).
Do you mean that I can recover my hdb partitions using fdisk.
Do I have to use the windows starting floppy or the ubuntu live cd to write to fdisk?

Yes, you may be able to recover you partitions with fdisk. I have had this problem with GParted before and it worked for me.

I have only used the Linux version.

Boot with the Ubuntu live CD.

In a terminal run:```
sudo fdisk /dev/hdb
```

Re-create your partitions. You should read the link I gave you about fdisk first. Enter the starting and ending blocks **EXACTLY** as they were. Enter the type of partition. **DO NOT FORMAT**.

From your previous post:
> Device Boot Start End Blocks Id System
/dev/hdb1 1 9729 78148161 f W95 Ext'd (LBA)
/dev/hdb5 2 2264 18177547+ b W95 FAT32
/dev/hdb6 2552 5101 20482843+ 7 HPFS/NTFS
/dev/hdb7 5102 9729 37174378+ 7 HPFS/NTFS
/dev/hdb8 * 2265 2534 2168743+ 83 Linux
/dev/hdb9 2535 2551 136521 82 Linux swap / Solaris

You have all the information you need. All you need to do is **READ MY LINK ON FDISK**.

---

### Post by housam on 2006-11-08
Thanks for your help. I've read the content of the link yesterday and I'll try to do the job after going home.

---

