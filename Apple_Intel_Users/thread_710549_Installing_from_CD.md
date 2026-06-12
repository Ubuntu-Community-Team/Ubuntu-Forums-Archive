---
title: "Installing from CD"
date: 2008-02-28
forum: Apple Intel Users
---

### Post by rafishalom on 2008-02-28
Hi,

I downloaded 7.10 on cd for 64 bit intel machines and I'm running an iMac with 2.0 Ghz core duo. I have installed leopard and partitioned the drive, leaving a 10GB partition for ubunto. From what I heard 10GB should be enough even though it's not enough for other OSs.

The CD works fine and I can boot from it. When I try to install I get several options, some of them include partitioning the drive. I want to be very careful not to lose data so I want to know if partitioning or installing may do that. I prefer not to partition it from the CD so I hope the partitions I made on the mac are enough. When I try to install the OS without partitioning I get a list of partitions but they don't have the names I gave them on the mac and I have to guess by their size and usage which is which. What is the best way of installment that would allow me to be sure I get the ubuntu installed on the empty 10GB partition, and that none of the data on my machine will be erased or influenced ?

Also, if after I install the booting process of ubunto fails or hangs for some reason, could it create a problem in case I want to boot from leopard ? Also, am I guaranteed that I will be able to boot from a leopard CD using the 'c' key ?

Thanks,

Rafi.

---

### Post by jken146 on 2008-02-28
If you just want to use all the unpartitioned space on the drive, you can use the "Use largest continuous free space" option.  If you want more control, use the manual partitioning option.  Don't be scared, it's not that hard :)

In Linux, drive names start with sd (sometimes hd) followed by a letter a, b, c, ... So the first drive would be sda, the second sdb, and so on.  Partitions are numbered, i.e. sda1, sda2, sda3...

To see the current partitions on your drives, type ```
sudo fdisk -l
``` in a terminal or use gparted, the graphical partition editor program that's on the live CD, in the menus under System -> Administration -> Partition Editor.

If you partition manually, you'll need a / partition and a swap partition.  You can have more partitions, but that's optional.  / is the root partition, the top of the file system for Ubuntu.  Swap is virtual memory, and should be around RAMx1.5 in size, but definitely not more than 1 GB.

If you do have trouble booting after installation, all bootable CDs will continue to work as before, so don't worry.

Finally, a word of warning -- partitioning and formatting partitions will cause data loss if you select the wrong one by mistake.  Just be careful :)  The installer does give you a little summary of what it's about to do before it actually does anything, so read this through.  If you're *really* worried that you might make a mistake, the only sound advice I can give you is to make a backup before you start.

Have fun!

---

### Post by cyberdork33 on 2008-02-28
> **jken146 said:**
> To see the current partitions on your drives, type ```
sudo fdisk -l
``` in a terminal or use gparted, the graphical partition editor program that's on the live CD, in the menus under System -> Administration -> Partition Editor.
Beware of fdisk on a  Mac. It does not mix well with GPT disks. Stick with gparted.

---

### Post by rafishalom on 2008-02-29
> **jken146 said:**
> 

If you partition manually, you'll need a / partition and a swap partition.  You can have more partitions, but that's optional.  / is the root partition, the top of the file system for Ubuntu.  Swap is virtual memory, and should be around RAMx1.5 in size, but definitely not more than 1 GB.


Thanks for the quick and helpful response. Here's a few more :) :
 
Since my original idea was to use one partition for linux I want to put both the / and the swap on the same 10GB partition. I suppose this means I have to partition the 10GB space into two partitions, say 9+1 using the partition editor. What would be the effect when I run leopard ? Will I see the original partition or two ? Will I have "normal" access to files in the ubunto partition, the way I can read files easily from my hfs+ partitions when I run the live CD ?

Originally the manual install was my intention. I ran the CD again, and tried to install this way. There were many choices for the partition. One of them was swap but the rest were "ext3, ext2, ifs, xfs ..." which I imagine are about the way the space is to be formatted and used for the / directory, but I can't tell which to choose. Given my above intentions, what would be best ? I also ran the partition editor which I suppose I should run first to turn the 10GB into a 9+1 GB before installing. Am I correct ?

Thanks,

Rafi.

---

### Post by cyberdork33 on 2008-02-29
You can also just make a swap file on the root partition if you rather, but making it a separate partition won't affect anything else.

Unless you are planning to make any extra partitions for home, var or whatever, just use the partition editor to delete the 10GB partition you made for Ubuntu then choose to install to the free space in the Installer. This will create a root and swap partition sized appropriately.

Stick with ext3 (the default) it is the traditional and likely most stable of filesystems available.

---

### Post by rafishalom on 2008-03-03
> **cyberdork33 said:**
> 

Unless you are planning to make any extra partitions for home, var or whatever, just use the partition editor to delete the 10GB partition you made for Ubuntu then choose to install to the free space in the Installer. This will create a root and swap partition sized appropriately.



If I delete the 10GB partition and install on free space would leopard be able to "see" the ubuntu file system ?

Rafi.

---

### Post by cyberdork33 on 2008-03-03
> **rafishalom said:**
> If I delete the 10GB partition and install on free space would leopard be able to "see" the ubuntu file system ?

Rafi.
yes, but OS X requires drivers to read ext3 (the default Ubuntu filesystem):
[http://sourceforge.net/project/showfiles.php?group_id=64713&package_id=101149&release_id=468470](http://sourceforge.net/project/showfiles.php?group_id=64713&package_id=101149&release_id=468470)

---

