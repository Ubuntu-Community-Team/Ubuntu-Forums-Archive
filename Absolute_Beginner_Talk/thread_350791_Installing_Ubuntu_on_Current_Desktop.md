---
title: "Installing Ubuntu on Current Desktop"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by patoy on 2007-02-01
Hi!

I just want to know the steps in installing Ubuntu on my current system which has this setup:

Hard Drive partitioned into (4) drives: 

drive C (10GB): Windows XP Pro is installed using NTFS file system.
drive D (5GB): Data files using FAT32 file system. (I want Ubuntu to be installed)
drive E: (10GB)(Data files using FAT32 file system.
drive F: (15GB)Data files using FAT32 file system.

I want to Dual boot the system but the problem is what is the best primary os to be boot.

---

### Post by devils_casper on 2007-02-01
you have four Primary Partitions already. you need atleast two partitions for Ubuntu. / (root) and SWAP. 
boot up from Ubuntu LiveCD and open GParted. its in Menu. delete second partition. it will be listed as /dev/hda2. select Free Space and Create Extended partition. 
start Ubuntu Installation and in partition section, select 'Unpartitioned/free space for install'.

> I want to Dual boot the system but the problem is what is the best primary os to be boot.
i am not getting it. Ubuntu will install Boot Loader GRUB and you will have choice to boot up Windows or Ubuntu at startup. you can set any as Default OS.





Casper

---

### Post by patoy on 2007-02-01
The only Primary Partition is the Drive C:, other drives are Extended Partitions / Extended DOS Partitions.

---

### Post by smelly on 2007-02-01
I am in a similar position.  I too have an XP machine, and am looking to try Ubuntu.  I have a 'spare' 9GB :D in an extended partition.  I too would lke to use this for Ubuntu.  How do I get it onto that partition, or do I have to restructure al the partitions on the drive (currently 5 plus the spare 9GB).

Drive breakdown

C: Primary Partition (20GB)
D: Extended Partition (40GB
E: Extended Partition  (20GB)
F: Extended Partition  (20GB)
G: Extended Partition (20GB)

Spare unallocaed 9GB partition in Extended partition.

---

### Post by muguwmp67 on 2007-02-01
You do not necessarily have to repartition the drive manually.  The Ubuntu installer can guide you through the process without using the manual partitioning option (GParted), once you know where you want to install it.

---

### Post by devils_casper on 2007-02-01
[QUOTE=patoy]The only Primary Partition is the Drive C:, other drives are Extended Partitions / Extended DOS Partitions.
Reply With Quote[/QUOTE]
thats good. just delete D: drive through Windows Disk Management tool OR Gparted of Ubuntu.  leave it as it is.  
select unpartitioned free space during installation.

[QUOTE=smelly]I am in a similar position. I too have an XP machine, and am looking to try Ubuntu. I have a 'spare' 9GB in an extended partition. I too would lke to use this for Ubuntu. How do I get it onto that partition, or do I have to restructure al the partitions on the drive (currently 5 plus the spare 9GB).
[/QUOTE]

same procedure.  leave 9GB unpartitioned space as it is and install Ubuntu in it. 





Casper

---

### Post by smelly on 2007-02-01
Thanks for the guidance.  As you can probably tell I am a bit new to Ubuntu.  Do I need to format the partion as a Linux partition (Partition Magic), or will it do that itself?

---

### Post by devils_casper on 2007-02-01
dont format partition. leave it as unpartitioned/free. during Ubuntu installation, in partition section, select 'unpartitioned/free space fot install'.






Casper

---

### Post by smelly on 2007-02-01
casper.

Again, thanks for clearing things up.  However, what if I wanted to have a standalone Ubuntu system.  I have downloaded 6.10 (workstation) and burnt it to disk.  As the disk isn't bootable (unless I burnt it wrong), how would I install it; or would I be best installing onto a PC (with an existing OS) and then removing the existing OS to leave ubuntu :confused:

---

### Post by bobpur on 2007-02-01
In my opinion, I would backup anything I wanted to save to a cd or other media. Then, wipe the system and then do a fresh install. 
This method seems to work better than trying to repair an OS with missing files or folders.

                                     Just my 2 cents.   Good Luck

---

### Post by patoy on 2007-02-01
The version that i'm going to install is Ubuntu 5.04 which has an Install & Live CD. I tried using the Live CD and I can't seem to find  the Gparted program. Where can I specifically find that program?

---

### Post by devils_casper on 2007-02-03
download [GParted LiveCD]("www.gparted.sourceforge.net/livecd.php"), burn to CD and boot from it. 






Casper

---

