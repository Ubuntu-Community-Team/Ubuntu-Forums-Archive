---
title: "[SOLVED] Dual Boot Problems"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by Bheegerji on 2007-11-27
Please forgive me if this is an unnecessary post.

 I've read through many forums and threads to set up a dual boot setup with Windows XP and Ubuntu 7.10, but could only get  confronting suggestions. In one thread, it has been said that it is unsafe to install two OSs' in a single partition. But in the official documentation provided with the Ubuntu Live CD, it's asking me to "Select the partition which contains Windows" under "Manually edit partition table".

After reading a lot of these threads and I've decided to follow a method for setting up a dual boot. Please read through and tell me whether there are any problems in following this method. Here goes,

1) Make backups of all necessary files.

2) Install Windows XP afresh with the following partitions:
	
	C drive: 19.5 GB  (Windows instalation drive)
	D drive: 19.5 GB  (free space)
	E drive: 2.0  GB  (free space)
	F drive: 32.5 GB  (free space)

3) Start Windows, insert the Ubuntu 7.10 Live CD in and install "Windows based Ubuntu Installer", i.e. executing the file "wubi-cdboot" found in the Live CD.

4) Restart the system.

5) Install Ubuntu 7.10 allocating the total D drive for installation and the E drive for the SWAP Partition by manually editing partition table.

6) Restart.


Atleast after this, Will I be getting a screen asking which OS to load?

or have I missed anything else?



I screwed up once trying to set up a dual boot, thats why this time I want to be pretty sure of what I'm doing. I've a 80 GB HDD with 1GB RAM and running on a Pentium 4 (i386 PC).

---

### Post by keskew on 2007-11-27
I recently did a dual boot with Windows XP and Ubuntu 7.10.  First, I used gparted to create the partitions on a blank hard disk.  Next, I installed Windows XP on its partition using the Windows XP installation CD.  Then, I installed Ubuntu on its partition (plus swap) using the Ubuntu CD.  I booted into the Ubuntu CD directly, not from within Windows.  When my computer starts, the GRUB boot menu appears giving me the choice of what OS I want to boot into.

There are a lot of good sites that offer tutorials on how to set up a dual boot system.  I found the site below helpful.

[http://www.users.bigpond.net.au/hermanzone/]("http://www.users.bigpond.net.au/hermanzone/")

---

### Post by bobpur on 2007-11-27
This whole dualbooting thing probably seems more intimidating than what it should be:)
1). Make a NTFS paretition for Windows
2). Make a EXT3 partition for Linux w/ SWAP partition for, well, SWAP
3). Install Windows first. (This is important)
4). Install Ubuntu
5). Have fun:)
The two OS's do not interact so you don't boot into Windows to install Linux.
If you have Windows installed already, you're half-way there. Resize the NTFS partition and install Linux as above.
Something to think about-- Add a second hdd to your system for linux. Leave Windows on the first hdd and put linux on the second. I like this method better as you are less likely to screw up Windows.(Worse than it already is:) :))

Good Luck.

---

### Post by dpar on 2007-11-27
I find that this is the best set of instructions.....

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Bheegerji on 2007-11-27
Thanks for the links guys. I'll check through them.

> **bobpur said:**
> This whole dualbooting thing probably seems more intimidating than what it should be:)
1). Make a NTFS paretition for Windows
2). Make a EXT3 partition for Linux w/ SWAP partition for, well, SWAP
3). Install Windows first. (This is important)
4). Install Ubuntu
5). Have fun:)
The two OS's do not interact so you don't boot into Windows to install Linux.
If you have Windows installed already, you're half-way there. Resize the NTFS partition and install Linux as above.
Something to think about-- Add a second hdd to your system for linux. Leave Windows on the first hdd and put linux on the second. I like this method better as you are less likely to screw up Windows.(Worse than it already is:) :))

Good Luck.


I already have windows installed as in the first post, then why do I have to resize my partition? I want the entire D drive to be taken up by linux.

---

### Post by candtalan on 2007-11-27
> **Bheegerji said:**
> [...]But in the official documentation provided with the Ubuntu Live CD, it's asking me to[...] 
I do not see this with the Live CD - can you explain where it is please?

> 
3) Start Windows, insert the Ubuntu 7.10 Live CD in and install "Windows based Ubuntu Installer", i.e. executing the file "wubi-cdboot" found in the Live CD.

I do not think the wubi install is included in the official ubuntu live CD, but it may be part of another related teams work (wubi). This will install into a windows system, into the same single windows partition. This may be still a bit experimental, and I have not tried it.

---

### Post by fineas on 2007-11-27
Having the "windows" partitions (c: and f: drives) in not-continuous spaces in your hard disk, make impossible to decrease one of them in favor of the other in the future. If you don't plan to do this, you don't have to resize your partitions before installing ubuntu.
The link that has been provided by dpar is quite instructive. I always prefer the manual partitioning. Place your swap partition in E:drive and  / (or any other partition you intend to make) in d: and it would be fine. Bare in mind that you can have up to 4 primary partitions in a hard disk and one is already the microsoft windows instalation drive.
Restarting after the installation of ubuntu, we will have a screen asking which OS to load.
Best wishes

---

### Post by samuel.rajesh on 2007-11-27
> **candtalan said:**
> I do not see this with the Live CD - can you explain where it is please?


I do not think the wubi install is included in the official ubuntu live CD, but it may be part of another related teams work (wubi). This will install into a windows system, into the same single windows partition. This may be still a bit experimental, and I have not tried it.

Wubi installs linux under windows but u still will boot into ubuntu or windows ,it does not need separate partion when installed using Wubi it will get installed in the same partion that windows is .

---

### Post by gn2 on 2007-11-27
OK here goes, this is how I've done it many times for other people, sizes based on your 80gb drive, can be adjusted for a bigger HDD.

1: Boot with XP CD in drive.

2: Delete ALL partitions on the drive.

3: Create 15gb NTFS partition 

4: Create another NTFS partition (of desired size for My Documents) and leave the rest unallocated.

5: Install XP into the first partition.

6: Boot into XP and change target of My Documents to the second NTFS partition.

7: Boot the Ubuntu Live CD (or Alternate CD as desired) and begin install procedure.

8: At the partitioning stage, select "Manual"

9: Create 6-10gb ext3 partition, bootable flag on, mount point /

10: Create ext3 partition with the remaining space minus 1gb, bootable flag off, mount point /home

11: Create 1gb swap partition.

12: Complete the installation.

Done.

---

### Post by fineas on 2007-11-27
It seems you must specify if you want a "pure" ubuntu installation or an installation through wubi> Bare in mind that, as it is explained in wubi faq ([http://wubi-installer.org/faq.php):](http://wubi-installer.org/faq.php):) 

[I]What is the performance?

The performance is identical to a standard installation, except for hard-disk access which is slightly slower. If your hard disk is very fragmented the performance will degenerate. However, once the Ubuntu install created by Wubi has been transferred to a dedicated partition using LVPM, the hard drive access speed will be identical to that of a standard Ubuntu installation.[/I]
In plain words, you will not run ubuntu with its full potential.

---

### Post by Bheegerji on 2007-11-27
Thanks for the support guys. Let me try these methods n i'll let u know whether i succeeded or not.

---

### Post by Bheegerji on 2007-11-27
Voilla. Welcome me to the club of dual boots.
Thank you very much guys, especially gn2 for making this possible.

A short documentation on what i did:

1) Installed XP afresh allocating 30 GB out of 80. Left the remaining space unpartioned.

2) Installed Ubuntu with a Live CD, Selected the option "Use continuous free space - Guided partitioning"

and presto, i'm shown a screen asking which OS to load.

---

