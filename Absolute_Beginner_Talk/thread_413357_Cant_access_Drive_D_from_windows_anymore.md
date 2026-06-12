---
title: "Cant access Drive D from windows anymore"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by John82 on 2007-04-19
I had windows XP intalled on my C: drive and all my softwares on Drive D:. I installed Ubuntu (probably on Drive d:?) by checking the "Resize IDE1 master partition #1(hda) and use free space". So far so good, I have a dual boot as a result. When I go back to windiow and try clicking on Drive D:, it says that the 'drive is not formatted'. How do I get all that data back that I had been storing on Drive D: in windows?? Have I lost all my data on Drive D:?    
note: I only have 1 Hard disk.

---

### Post by Jussi Kukkonen on 2007-04-19
Can't really help with windows, but in Ubuntu *"sudo fdisk -l"* (on the command line) will show you the different partitions on the disk. That should give you some information (paste here if it doesn't make sense)

---

### Post by seshomaru samma on 2007-04-19
Well - if Windows can't see it , it does sound like bad news but 
Boot into Ubuntu , and post the output of :
```
sudo fdisk -l 
```

---

### Post by bullgr on 2007-04-19
> **John82 said:**
> I had windows XP intalled on my C: drive and all my softwares on Drive D:. I installed Ubuntu (probably on Drive d:?) by checking the "Resize IDE1 master partition #1(hda) and use free space". So far so good, I have a dual boot as a result. When I go back to windiow and try clicking on Drive D:, it says that the 'drive is not formatted'. How do I get all that data back that I had been storing on Drive D: in windows?? Have I lost all my data on Drive D:?    
note: I only have 1 Hard disk.

im afraid that you overwrited the drive d: partition...
before you do some issues you must first backup to be sure if something went wrong, to not loose your data...

sorry...

---

### Post by John82 on 2007-04-19
Hi All,
Thanks for your replies. I tried the command 'sudo fdisk -1' at the terminal and below is what I got. Can anyone explain this to me as I AM A COMPLET NEWBIE :( 

fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

---

### Post by John82 on 2007-04-19
Also I must clarify that In windows I am being able to see Drive D: but when I double click it, "it say the drive isnt formatted and needs to be formatted" what do I do?

---

### Post by bullgr on 2007-04-19
> **John82 said:**
> Hi All,
Thanks for your replies. I tried the command 'sudo fdisk -1' at the terminal and below is what I got. Can anyone explain this to me as I AM A COMPLET NEWBIE :( 

fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

sudo fdisk -l

this means a small cap L (l) and not the number 1
use copy and paste to the terminal to avoid misstypos

---

### Post by John82 on 2007-04-19
Okay, After typing 'sudo fdisk -l'  Below is what it shows. What exactly does all this mean? Thanks.

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         721     5791401    f  W95 Ext'd (LBA)
/dev/hda2   *        1276        4997    29896965    7  HPFS/NTFS
/dev/hda3             722        1275     4450005   83  Linux
/dev/hda5               2         692     5550457+   7  HPFS/NTFS
/dev/hda6             693         721      232911   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by george29 on 2007-04-19
Device Boot Start End Blocks Id System
/dev/hda1 1 721 5791401 f W95 Ext'd (LBA)
/dev/hda2 * 1276 4997 29896965 7 HPFS/NTFS
/dev/hda3 722 1275 4450005 83 Linux
/dev/hda5 2 692 5550457+ 7 HPFS/NTFS
/dev/hda6 693 721 232911 82 Linux swap / Solaris

a strange partition layout... hda1 appears to be an extended partition containing an ntfs partition (hda5) and a swap partition (hda6)
hda2 is probably your XP partition
hda3 is your ubuntu partition.. 

as for you windows D: drive - probably lost forever.

---

### Post by Jussi Kukkonen on 2007-04-19
> as for you windows D: drive - probably lost forever.
I'm not so sure, that still leaves us with hda5, which is still >5GB...

John82, you have these partitions (omitting swap and extended, sizes approximate):
hda2 (30GB NTFS)
hda3 (4.5 GB ext3)
hda5 (5.5 GB NTFS)

If you want to, we can help you mount the windows (NTFS) partitions so you can check what they contain on ubuntu -- as a starting point, go here if you are on Feisty: [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions) (otherwise ask for help) . If you want to solve this on Windows, I'm afraid that's out of my area of expertise.

---

### Post by John82 on 2007-04-19
Thanks for your replies,
**Yes I would like to mount the hda5 (5.5 GB NTFS) as suggested by Jussi**. How can I do that? No point in mounting the /dev/hda2  though as it contains my Windows, and I can access those files when I boot to windows anyway.  Also whats in my first partition /dev/hda1  its taking up 5 gb of space. I am posting the result of  'sudo fdisk -l' again so everyone can see.  Thanks!


Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         721     5791401    f  W95 Ext'd (LBA)
/dev/hda2   *        1276        4997    29896965    7  HPFS/NTFS
/dev/hda3             722        1275     4450005   83  Linux
/dev/hda5               2         692     5550457+   7  HPFS/NTFS
/dev/hda6             693         721      232911   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by freebird54 on 2007-04-19
If you are on a laptop, the 'mystery' partition is probably the 'restore' Windows partition. so leave it alone :)  (unless you have a system restore CD as well.)  The hda5 entry could very well be your D drive - so don't do anything drastic to it yet.

The best bet is to mount the drive from Ubuntu and see what's there.  Getting Win to find it can be worked around if you get at the data first.  You can always copy it off, and restore it when Windows admits there is a space for it!

---

### Post by george29 on 2007-04-19
/dev/hda1 is an extended partition - consisting of the logical partitions /dev/hda5 and /dev/hda6. - at least that is how i'm reading the partition table...

you can only have 4 primary partitions, but as many logical partitions in a single extended partition as you'd like.

to try mounting hda5 

```

sudo mkdir /media/NTFS_drive_hda5

sudo mount /dev/hda5 /media/NTFS_drive_hda5

```

then you should find the partition is mounted.

---

