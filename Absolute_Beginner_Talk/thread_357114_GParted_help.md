---
title: "GParted help"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by antihero on 2007-02-09
Hey!  My Windows partition bit the dust and I need to reformat it.  I want to wipe Windows out along with Dell's Media Direct and Restore partitions.  My problem is that when I run GParted from Ubuntu it doesn't show any partitions at all.  It shows my entire HDD as unallocated.

Here's a snapshot of my fdisk -l:
```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 13727 13987 2096451 c W95 FAT32 (LBA)
/dev/sda2 * 7 3654 29302560 7 HPFS/NTFS
/dev/sda3 3655 13987 82999822+ f W95 Ext'd (LBA)
/dev/sda4 13988 14593 4867695 db CP/M / CTOS / ...
/dev/sda5 13727 13987 2096451 dd Unknown
/dev/sda6 3655 6086 19534977 83 Linux
/dev/sda7 6087 13599 60348141 83 Linux
/dev/sda8 13600 13726 1020096 82 Linux swap / Solaris

Partition table entries are not in disk order
```

I've never used Gparted before so I could easily be doing something wrong.  Thanks for your help!

---

### Post by NicePics13 on 2007-02-09
Weird.. I see you have a SATA HD, but gparted should have no problem with those. Why not try qtparted?

---

### Post by antihero on 2007-02-09
I think this might be the problem, although I have no idea what to do about it:
```

Using /dev/sda
(parted) print
Error: Can't have overlapping partitions.
```

---

### Post by antihero on 2007-02-09
Here's a clearer shot of fdisk -lu so you can see the overlap (start and end):

```

Device Boot      Start         End      Blocks   Id  System
/dev/sda1           13727       13987     2096451    c  W95 FAT32 (LBA)
/dev/sda2   *             7        3654    29302560    7  HPFS/NTFS
/dev/sda3            3655       13987    82999822+   f  W95 Ext'd (LBA)
/dev/sda4           13988       14593     4867695   db  CP/M / CTOS / ...
/dev/sda5           13727       13987     2096451   dd  Unknown
/dev/sda6            3655        6086    19534977   83  Linux
/dev/sda7            6087       13599    60348141   83  Linux
/dev/sda8           13600       13726     1020096   82  Linux swap / Solaris
```

---

### Post by az on 2007-02-09
How did your partition table get broken like that?

Assuming that they were not created by you, what happens if you try to delelte hda4 and hda5?

(Back up any date you have, first.  Although this will not touch any data on your drive, the partition order may be changed and that may affect how easy it will be for you to boot into ubuntu).

---

### Post by antihero on 2007-02-09
I have no idea how it got like this.  Everything was working fine and one day I couldn't boot into Windows,  When I booted into Ubuntu and looked at my partition table it was jacked up.  It used to be much simpler.  I think it might have something to do with Dell's crappy Restore and Media Direct partitions.

How do I delete a partition if I Gparted sees everything as unallocated??

Thanks again.

---

### Post by antihero on 2007-02-09
Anymore ideas?

---

### Post by az on 2007-02-09
> **antihero said:**
> I have no idea how it got like this.  Everything was working fine and one day I couldn't boot into Windows,  When I booted into Ubuntu and looked at my partition table it was jacked up.  It used to be much simpler.  I think it might have something to do with Dell's crappy Restore and Media Direct partitions.

How do I delete a partition if I Gparted sees everything as unallocated??

Thanks again.

sudo cfdisk /dev/sda

---

### Post by antihero on 2007-02-10
Ok, so I deleted the bad uknown partiton (sda5) in fdisk and then rebooted.  Now I get the error:

> 
GRUB Loading stage1.5.

GRUG loading. please wait....
Error 15


The good news is that I can boot to the Windows CD now.  The bad news is that I can't boot from the harddrive at all.

I'm assuming I need to boot to a LIVE CD and fix the GRUB config files??  Can someone please help me do this?  

Thanks again.

---

### Post by Herman on 2007-02-10
Hello antihero,
This link should just about be self explanatory, but if you have any questions, please feel free to ask,
[Re-install Grub with a GRUB shell eg; with Live CD]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD")

Regards, Herman :)

---

### Post by antihero on 2007-02-10
Thanks Herman.  I followed your instructions.  

I did setup (hd0) and setup (hd0,4) where 4 is my Linux / partition.

Now, GRUB starts upon boot-up and I was able to boot into Windows. 

Only now I can't boot into Ubunutu.  When I select Ubunutu from the boot list I get:

> 
root (hd0,5)
 Filesystem type is ext2fs, partition type 0x83
kernel  /boot/vmlinuz-2.6.15.27-686 root=/dev/sda6 ro quiet splash

Error 15: File not found

Press any key to continue....


I'm very close to getting everything cleared up.  Thanks again.

---

### Post by antihero on 2007-02-10
Hmm... I think root should be sda5 right?  Since Linux is installed on (hd0,4)?

---

### Post by Miaowara on 2007-02-22
My partitions seem to be messed up as well. Not sure how it happened but I suspect it has something to do with reinstalling a window image (c/o Toshiba's Rescue disks). Looks like hda3 should come between hda5 and hda6. hda2 only seems to show up in sfdisk (and appears to be before hda1, perhaps the mbr partition?). How can I go about remedying these problems? Check out ze outputz:

  
**sudo sfdisk -lV**

```
Disk /dev/hda: 7296 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/hda1   *      0+   1379    1380-  11084818+   7  HPFS/NTFS
/dev/hda2          0       -       0          0    0  Empty
/dev/hda3       2686+   4774    2089-  16779892    7  HPFS/NTFS
                start: (c,h,s) expected (1023,254,63) found (1023,0,2)
/dev/hda4       1380    7295    5916   47520270    f  W95 Ext'd (LBA)
                start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/hda5       1380+   2685    1306-  10490413+   7  HPFS/NTFS
                start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/hda6       4775+   5029     255-   2048256    b  W95 FAT32
                start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/hda7       5030+   7175    2146-  17237713   83  Linux
                start: (c,h,s) expected (1023,254,63) found (1023,1,2)
/dev/hda8       7176+   7295     120-    963868+  82  Linux swap / Solaris
Warning: partition 3 does not start at a cylinder boundary
```
**sudo fdisk -l**

```
Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1380    11084818+   7  HPFS/NTFS
/dev/hda3            2687        4775    16779892    7  HPFS/NTFS
/dev/hda4            1381        7296    47520270    f  W95 Ext'd (LBA)
/dev/hda5            1381        2686    10490413+   7  HPFS/NTFS
/dev/hda6            4776        5030     2048256    b  W95 FAT32
/dev/hda7            5031        7176    17237713   83  Linux
/dev/hda8            7177        7296      963868+  82  Linux swap / Solaris

Partition table entries are not in disk order
```

And best for last:

**parted**

```
Error: Cannot have overlapping partitions.
```

thnks...

---

### Post by bodhi.zazen on 2007-02-22
That is one UGLY partition table :(

Do you have any idea of the previous geometry ?

---

### Post by Miaowara on 2007-02-22
Heh, well, I remember the partitions all being in order. ;) Then I didn't use Ubuntu for a while cause reinstalling Windows re-wrote the mbr and I didn't have an easy way to restore it [mbr] so I just did without access to the partition for a while.

I've only within the last week or two, using Wingrub, created a  grub boot loader on a cfcard. Upon re-entry into Ubuntu, I thought I noticed some funny changes in the partition numbers but wasn't sure if it was just because I wasn't remembering correctly. Obviously something had changed.

Any ideas on how to clean it up?

---

### Post by bodhi.zazen on 2007-02-22
OK, here is my best guess then

Boot the the Ubuntu desktop (live) cd

Open a terminal, enter :

```
sudo cfdisk /dev/hda
```

Delete what is called partition /dev/hda3

start 2687 end 4775

make the other geometries like this :

> /dev/hda1   *           1        1380    11084818+   7  HPFS/NTFS
/dev/hda4            1381        7296    47520270    f  W95 Ext'd (LBA)
/dev/hda5            1381        2686    10490413+   7  HPFS/NTFS
/dev/hda6            2687        4775    16779892    7  HPFS/NTFS
/dev/hda7            4776        5030     2048256    b  W95 FAT32
/dev/hda8            5031        7176    17237713   83  Linux
/dev/hda9            7177        7296      963868+  82  Linux swap / Solaris

What you will do is delete partition /dev/hda3

Now make a new LOGICAL partition starting at 2687 and ending at 4775

write to disk

exit cfdisk

The "problem" is /dev/hda3 is supposed to be a logical partition and it has been written as a primary partition. The location is OK, but it conflicts with your extended partiton, /dev/da4

HTH 

sorry the terminology is confusing

See here for terminology : [http://www.ubuntuforums.org/showthread.php?t=282018](http://www.ubuntuforums.org/showthread.php?t=282018)

8)

---

### Post by Miaowara on 2007-02-22
I get ya. I'll try that and post my results. Thanks for your help!

**---UPDATE---**

Hurray! It worked just as you predicted (though I had to use Acronis Disk Director in Windows to delete the partition cause my computer won't boot from cd/dvds, blarg)! Thanks again for your help!=D>

---

