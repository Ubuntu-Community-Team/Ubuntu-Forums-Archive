---
title: "ubuntu does not identify my sata disk"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by Kans on 2007-05-14
Hi All,

I am trying to install ubuntu, but it does not recognize my sata disk. (A dell e510 desktop).
Also right now most part of it is one partition (70G/80) with NTFS (win xp).

Somebody pls let me know how to proceed.

Thanks,
Kannan.

---

### Post by taurus on 2007-05-14
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by Cypher on 2007-05-14
Which version of Ubuntu and are you running from the LiveCD?

---

### Post by Kans on 2007-05-15
Thank you for the help.

I am using Ubuntu 7.04 CD image

sudo fdisk -l shows my disk

Disk /dev/sda: 80.0 GB,  ...

Device 

/dev/sda1   1    6   48163+ de Dell Utility
/dev/sda2   7   9118 73192140 7 HPFS/NTFS
/dev/sda3  9120 9725 4867  db  CP/M  / CTOS  / ...

How do I go about resizing my ntfs partition?

Also I have an Airlink 101 wireless pci adapter. I am able to see the wireless networks available, configured my network, got it connected , but it doesnt get the ip address from the wireless router. 

I ran GParted and it shows the disks. It also has a Resize/Move options, is it safe to use that to resize my ntfs partition. Dont want to ruin my existing files/XP installation.

Thanks,
Kannan.

---

### Post by pulp999 on 2007-05-15
Hi, I had a similar problem; my SATA with 3 windows ntfs partitions was not recognized; I consolidated data over 2 partitions and then deleted the 3rd using Windows device manager.
Rebooted with Ubuntu 7.04 and clicked on System --> Preferences --> Removable Drives and Media and turned off automatic mounting of removable drives and removable media....
After that the installer saw the 2 windows partitions and I manually installed on the free partition.
I was also able to import my Data from Windows....

cheers,

Rolf

---

### Post by Kans on 2007-05-21
Hi,

Still trying to install ubuntu

/dev/sda1 1 6 48163+ de Dell Utility
/dev/sda2 7 9118 73192140 7 HPFS/NTFS
/dev/sda3 9120 9725 4867 db CP/M / CTOS / ...

I used gparted to shrink my ntfs partition to 40 G, and I wanted to use the rest of the free space to install linux.
I need a dual boot system (with existing win xp & linux).

How do I go about partitioning disk? I managed to shrink the NTFS partition, now it shows 40 G in NTFS and 30 G as free space.g

First I tried to put the whole free space (30 G) into ext3 and formatted it.
Install program said it needs 2 partitions (1 root & 1 swap)

So I went back tried to create one more partition, got into cannot create more than 4 primary partitions.

How should I partition (primary/extended) and how do get around this root partition issue in install?

There seems to be already 3 primary partition, how do I get it to install without disturbing the existing partition?
I read in wikipedia there can only be 4 primary partitions / 3 primary partition and 1 extended partition?

Can I make the 30 G as extended partition and split it into two for root and swap?
Can I boot 

Please help.

S:confused::confused:

Thanks,
Kannan.

---

### Post by dbansal on 2007-05-21
From my experience NTFS has always been a real pain, especially to get it shared via Samba, etc..

I would convert it to either a FAT32 or linux file format, and then edit it your /etc/fstab accordingly. 

Then all it is sudo mount -a

---

