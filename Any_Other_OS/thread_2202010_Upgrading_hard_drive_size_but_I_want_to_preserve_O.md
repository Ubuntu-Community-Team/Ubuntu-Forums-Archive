---
title: "Upgrading hard drive size but I want to preserve OS on original system"
date: 2014-01-27
forum: Any Other OS
---

### Post by kevdog on 2014-01-27
I have a 160GB drive which dual boots windows and Arch.  The disk is nearly entirely full.  I bought a 500GB hard disk.  I'd like to preserve the original data on the drive, but allocate more size to certain partitions, so I don't think this exactly falls under the guise of "cloning" since the source and destination partition size will be different:

/dev/sda1 = ntfs 119Gb ------> /dev/sdb1 = ntfs 200Gb
/dev/sda2 = ext4 200Mb (/boot partition) --------> /dev/sdb2 = ext4 200MB (/boot partition)
/dev/sda3 = ext4 20GB (/ partition) -------------->/dev/sdb3 = ext 100Gb (/ partition)
/dev/sda4 (extended partition) ------------------>/dev/sdb4 (extended partition)
/dev/sda5 = ext4 5Gb (/home partition) ----------->/dev/sdb5 = ext4 165GB (/home partition)
/dev/sda6 = swap 4GB------------------------------->/dev/sdb6 = swap 4GB

Because the partition sizes are different between source and destination -- what is the best way to go about this?  I don't believe I want to use the dd command rather than the cp -a command?  I would mount the various partitions and then cp from one partition to the other.  What do I do however about the bootloader -- specifically GRUB?

Am I off in left field here, or is there a better way?

---

### Post by TheFu on 2014-01-27
fsarchive

---

### Post by buzzingrobot on 2014-01-27
Is the new drive going to be used in addition to the existing drive, or will it replace it?

---

### Post by oldfred on 2014-01-27
Probably better to clone Windows with Windows tools. It has some things that do not easily copy.
       
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

To buzzingrobots's point. If using both drives, you cannot clone as UUIDs will be the same which is not allowed. Often then easily just to reinstall any Linux and copy /home and maybe some settings from /etc. Not sure about Arch, but with Ubuntu you would also want a list of installed apps.
If you copy or clone you have to change UUIDs in one install or the other, and update fstab, grub and maybe a few other settings. Again Arch may be even more difficult?

---

### Post by kevdog on 2014-01-28
No I'm working on a laptop and want to replace the old drive with the new drive.  The old drive is dual booted.  I've managed to copy the partitions and then later resize the partitions to the new drive using gparted, however I'm very concerned now how to install grub.  I'm not sure how to do this now that the partitions have changed in sizes?

---

### Post by TheFu on 2014-01-28
**Boot-repair** can often "fix" dual boot issues on HDDs. My signature has links.  The only time it didn't work for me was when the hardware decided the connected flash drive was _before_ the internal spinning HDD.

If that doesn't work, it is time to break out "grub_install", read the man page and go for it.

---

### Post by kevdog on 2014-02-01
crap -- I think Ive defaulted to grub_install.   Anyone with any tips?

---

### Post by kevdog on 2014-02-06
I'll probably have to write up the information on how to do this procedure, since I basically got it solved, and to my knowledge is probably applicable to any version of linux combined with a windows dual boot system.  In a nutshell I was upgrading from a 160Gb hard disk to a 500Gb hard disk.  I wanted to maintain the partition structure of organization, but basically resize some of the partitions because I had run out of space -- ie on the windows ntfs partition, the main linux partition, and my home partition.  

The tool i used for this systemrescueCd which is a live boot CD with gentoo that contains an xcfe window system with a bunch of preinstalled tools. I basically formatted the new hard disk with the same number but resized partitions with gparted.  I then copied each respective partition from source to destination disk with the dd command.  Repaired each partition using gparted so that the I could take advantage of the entire partition space. Verified the /etc/fstab file on the new linux partition contained the appropriate UUIDs.  Then basically reinstalled grub on the new drive.  Swapped the drives, rebooted, did a system upgrade, and viola -- success.  There was a lot of information floating out on the internet and with the Ubuntu help site that described other methods, but I found they really didn't work.  The beauty of this method is basically it requires one rescue CD, one program -- gparted, and a few command line methods -- dd, grub-install, to do the trick.

---

### Post by rewyllys on 2014-02-08
Sounds like a good idea to write this up. I hope you do so.

---

### Post by TheFu on 2014-02-08
> **rewyllys said:**
> Sounds like a good idea to write this up. I hope you do so.

I just did this today for a virtual machine that needed more storage.

It is pretty simple to swap in a new, larger HDD using gparted. This assumes the OLD HDD will be repurposed.

*** Always create a 100% backup before attempting any partition-related work. This is dangerous stuff.**
*** If you do not understand partition names, STOP.  Getting these incorrect WILL destroy data. The partition names for YOUR system may or may not be the same as used below.** It is highly unlikely that sdb is really the correct NEW HDD name on every system. You have been warned.
* Connect both HDDs, NEW and OLD, to the system
* Boot off a gparted ISO/boot disk
* Create a new partition table as needed (GPT for 2TB and larger HDDs)
* Create partitions on the NEW HDD  of the sizes you'd like - match the partition names on the OLD HDD.
** sda1 --> sdb1
** sda2 --> sdb2
etc.
* For each partition
** right click on the sda (OLD HDD) partition, select "copy"
** change to the sdb (NEW HDD) partition of the matching name, and select "paste".
** move on to the next partition, in order, until done
* Click "Apply"
* Wait for the data to be copied over. This can take 1 minute or 10 days or anywhere between depending on the CPU, backplane, RAM, disk controllers, HDD performance .... USB will be slower than eSATA or SATA connected HDDs.
* Remove the OLD HDD from the connection, probably swap the SATA cables to ensure the same SATA port is used for the NEW HDD (if you use UUIDs to mount partitions, this is not needed)
* Remove the gparted ISO/boot disk
* Reboot the system

These steps **do not** account for everything. There are shorter ways to accomplish the same things, if you know what you are doing with gdisk, sfdisk, and the partitioning header (MBR/GPT) are the same between the HDDs.
There are situations where these instructions do not work.

******* Caution - If MS-Windows is involved, a UEFI partition will be necessary if GPT is used on the NEW HDD and that will probably break the order of partitions.** Trying to use UEFI on hardware that does NOT support UEFI will not work.  A recovery disk will be necessary if any hope of this working for Windows.

Use of sfdisk and fdisk for many versions of Linux DO NOT SUPPORT GPT partitioned HDDs. This is why gdisk, parted and gparted are required. Eventually, a corrected version of fdisk that works with GPT will be the default. Unless you are certain of this support on YOUR system, use parted, gparted for all partitioning work. Both of these tools also automatically address 512b and 4Kb alignment concerns too. Not honoring the suggested alignment for 4K-sector HDDs can cause 50% performance degradation.

For MBR partitioned HDDs and less than 2TB HDDs, it is easy to clone the MBR partition table from sda to sdb:
As root, run: 
```
# sfdisk -d /dev/sda | sfdisk /dev/sdb
```

If you just want to mirror everything from sda to sdb, including the partition table, then boot off any liveCD/USB and run as root:
```
dd if=/dev/sda of=/dev/sdb bs=1024000
``` If the in/out counts do not match, there is an error so ddrescue should be used instead of plain dd.  Check the ddrescue man page for detailed options.
After the entire disk is cloned, you can use **parted** or **gparted** to resize most of the partitions.  I've had issues with extended partition resizing - basically it would not let me under any situation, which is why the instructions at the top have a manual step to create the partitions you like. If the extended partition has extra space, resizing logical partitions _inside_ should not be a problem.  That is one way that GPT partitioning is better than MBR, no more extended or logical partitions. There are others ways too.

---

