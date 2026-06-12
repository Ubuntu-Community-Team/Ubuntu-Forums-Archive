---
title: "help, i think i destroy my harddisk :("
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by Raxza on 2007-06-03
Hi, 
I have Vista and Ubuntu 7.04 installed in my harddisk. Then yesterday I decide to try out another distro. 
So, I change my harddisk partition to make space for this new distro. Somehow, something went wrong in the installation process and I can't finish the installation. I then restart the computer. 

And suddenly I cant boot into Ubuntu or Vista. 

So, I load up the Ubuntu live CD. My Vista partitions are still there but my Ubuntu partitions are gone. So I thought I just reinstall Ubuntu and everything will be fine again. 

Problem is Gparted doesn't recognize my old partitions (they're still tehere. I can access my Windows files through Nautilus). 

When I open "HardDisk Information" on Gparted  it says something about "disklabeltype = unrecognized"

So, my question is can I save my old partition or do I have to format my entire hard disk? 

Thank you for any help you can give me..

---

### Post by cantormath on 2007-06-03
Using gparted, you should be able to delete the old ubuntu partition, probably hda2, without touching the Vista partition, probably hda1.  You can then create a new partition for ubuntu and format it, then install to that new partition with vista intacted.

you will need to use the live cd to do this......

---

### Post by Raxza on 2007-06-03
How do I do that? 

Because when I open Gparted, it shows my hard disk as one big unallocated chunk. 
When I try to create new partition, it ask me to set a DiskLabel. But creating a DiskLabel will erase all data on my hard disk.

---

### Post by louieb on 2007-06-03
[FONT=Arial][COLOR=#0000ff]Hard to say if it can be saved. You say you can see the Vista partition from the live CD. Can you see your data. If so get it copied off before doing anything else. The first thing I would get is the System Rescue CD  (Google it). It has tools for fixing and Repairing broken operating systems.       [/COLOR][/FONT]

---

### Post by Raxza on 2007-06-03
System Rescue CD does work!! :D

Well actually I use a programme called Test Disk (which is part of System Rescue CD). It analyse my hard disk and then re-write the partition table. Everything is back to normal now. 

Thx louieb..

PS. System Rescue CD can be found here: [www.sysresccd.org](www.sysresccd.org)

---

