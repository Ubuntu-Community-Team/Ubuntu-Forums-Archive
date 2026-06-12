---
title: "Ubuntu 5.10 not listing existing partitions"
date: 2005-12-15
forum: Absolute Beginner Talk
---

### Post by Dhanagopal, R on 2005-12-15
I was trying to install ubuntu 5.10 in my system having already windows xp and Mandriva LE 2005 dualbooting with grub. My hdd's fstab entry is given below. My idea is to isntall Ubuntu 5.10 /dev/hda6  (in the empty fat32 partition) and to multiboot winxp, mandriva and ubuntu using grub. I am unable to proceed the ubuntu installation since the installer fails to display the existing partition in my hdd evenafter selecting the - manually edit 
partition table - option.  

it displays only the following line.
 -------------------------------------------------

IDE1 master (hda) - 40 GB ST340823A 

If I select this it displays the following message.

-----------------------------------------------------------------------

You have selected an entire device to partition. If you proceed creating a new partition 

table on the device, then all current partition will be removed

Note that you will be able to undo this operation later if you wish 

Creat a new empty partition table on this disk. 

Goback                                         Yes - No

--------------------------------------------------------------------------
 
Listing of FSTAB 

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
 
   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/hda2            1276        4865    28836675    f  W95 Ext'd (LBA)
/dev/hda3            4081        4774     5574555   83  Linux
/dev/hda5            1276        2677    11261533+   c  W95 FAT32 (LBA) 
/dev/hda6            2678        4080    11269566    c  W95 FAT32 (LBA) ..........> I have 

to install  ubuntu here
/dev/hda7            4775        4865      730894+  82  Linux swap

R.Dhanagopal

---

### Post by My8os on 2005-12-15
Every time i want to install a linux distribution i make sure that the partition that i want to use has to format.
Try deleting it through "Administation Tools" in windows...you'll probably end up with a FREE SPACE(green color) or an UNALLOCATED(black color) partition, in both cases when you run ubuntu installation you'll see it ;) .

---

### Post by roelofs on 2005-12-28
I had the exact same problem--a completely opaque extended partition even though Slackware can see it just fine--and I think it's a bug in Ubuntu's partition manager.  It appears to be unable to understand "W95 Extended" partitions correctly.  (In [another thread]("http://www.ubuntuforums.org/showthread.php?t=109593"), someone was able to get the tool to see the logical partitions but couldn't get it to manipulate them correctly.)

For reference, my (former) partition setup is in [this LinuxQuestions posting]("http://www.linuxquestions.org/questions/showthread.php?threadid=349241").  I was impatient, though, and ended up blowing away the entire thing.  I'd still like to see the real problem fixed, however...

---

