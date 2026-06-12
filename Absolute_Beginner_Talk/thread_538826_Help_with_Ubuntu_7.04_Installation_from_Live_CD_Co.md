---
title: "Help with Ubuntu 7.04 Installation from Live CD Configurations"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by orang_redux_777 on 2007-08-30
Hi, People:

I'd appreciate some help from those who are far more accomplished than myself.

I have a Fiesty Fawn (Ubuntu 7.04) Live CD from a Netherlands sub-contractor.

The CD works fine in both running atop a WinXP Pro SP2 OS and from  a BIOS-configured CD-ROM Boot.

My questions revolve around two central issues:

1) Does the Live CD, following the U .04 partition/format/install phase, write-back to the new partitioning data to the Live CD disk?

2) If so, how does one remove the new partiioning/installation data from the Live CD ***without*** it affecting the actual HDD partitions?

I've sought to, upon 9 different occasions, and using both the Guided and Manual partitioning sub-utilities, install the 7.04 OS on two different HDDs. 

The first partitioning C:\ Drive "go-round" via Guided went just fine, except for the fact that the disk percentage of the Free Space I assigned via slider was *not* replicated by the actual installation (even allowing for the Swap File.)  In fact, the space allocation of 30% was
doubled; that is, including the Swap file, it came out to be in reality over 60% of the System Drive HDD.

Subsequent attempts (#s 2-9,) via Manual partiitoning\MB assignment configuration\installation, have yielded further anomalies, including:

1)  the faux "read-back "of assignment of non-logical and system drive desiginations;

2)  the inaccuracy of the actual partition(s) size(s) of respective drives which do not in fact exist (either virtually or physically;) 

3) the continued misassignment of the partition-allocation sizes that I specified for the SATA 000 P-2 (Secondary Partition on the Primary System Drive.)  

All of the 9 attempt's worth of partitioning\installation data is still contained on the Live CD, making it a bit hard for me, a doofus-brain when it comes to using the Live CD, but not to drive partitioning per se, to get things right. 

I would sincerely value any help you can give me.

My best 2 all.

:-)

/.\ Orang /.\

{- On the h'ware compatibility/driver end of things, there are no discernible problems with my "rig," which I must say, is a very welcome change from the "days of yesteryear,"  from compiling and assembling various Linux-based distro sub-components, etc., etc.  For this I am sincerely grateful and sincerely applaud all the many, many contributions of the Ubuntu Open Source crew, be they curerntly housed in South Africa or in any other points of origin.}

[{ Basic H'ware\non-Ubuntu OS & Complete System Specs Data will be supplied if you deem it to be of pertinence.  THX again.  }]

---

### Post by dstew on 2007-08-30
Answers to questions:

1. After partitioning, no data is written back to the LiveCD. It is not writeable. However, when the LiveCD-booted Linux operating system is running, it sets up a file system in RAM that can be written to. It is even possible to install new programs on a LiveCD-booted system using Synaptic, and run them. However, since the new program is in the RAM file system, it will be gone when you shut off the computer.

2. The LiveCD system does not remember the partitioning data once that system is shut down. It only remembers it while it is running. But, once you partition the hard disk, it is permanently changed. My guess is that you are seeing the cumulative effects of all your partitioning attempts in one very complex partition table.

To get oriented, boot the LiveCD, and in a terminal window enter the command **sudo fdisk -l**. If it asks for a password, just hit return. That will tell us what your current partition table looks like. Post the result to this forum.

By the way, do you have your disks configured in a RAID? That can be a cause for much confusion.

---

