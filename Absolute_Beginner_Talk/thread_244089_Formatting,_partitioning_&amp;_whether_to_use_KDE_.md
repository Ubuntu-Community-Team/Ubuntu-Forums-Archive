---
title: "Formatting, partitioning &amp; whether to use KDE in Ubuntu"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by Dar on 2006-08-25
Hi, I'm a new user to Linux (first used it as of 2 days ago) and I'm unable to work out how I can format a partition on one of my hard disks. I have two hard disks - a disconnected 120gb IDE HDD that contains my Windows XP install and is in NTFS file format. I have disconnected it so that when I installed Ubuntu to my second 200gb SATA (or it might be SCSI? I thought it was SATA, but see the term SCSI and I don't know if there's a difference) HDD, I would not write to the Windows MBR. I am at the 'shut down, reconnect Windows as slave' step from the two-HDD dual-boot instructions at [http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

Using System --> Administration --> Disks I can see my 200gb HDD is split into 3 partitions: 
Partition 1 
Device: /dev/sda1
Filesystem: Windows NTFS
Access path: none
Size 47.13GiB (free space not available)
Status: Inaccessible (I disabled it and have the option to reenable it, I thought disabling it might give me access to the formatting option and it did). 

Partition 2
Device: /dev/sda2
Filesystem: Extended 3
Access path: /
Size: 136.29GiB (122.54GiB Free)
Status: Accessible.

Swap Partition
Device: /dev/sda5
Filesystem: Memory Swap
Size: 2.90GiB

What I want to do is change the partition size if possible to reduce my Linux partition size to 30gb and increase my Partition 1 size by the amount removed from the linux partition. I want to make Partition 1 readable and writeable from both Windows XP and Linux. Which format should I try formatting it to? I want to place all the risk on the Linux install, rather than the Windows install, as I'm not prepared to reinstall Windows. 

When I click format I get the following options:
Extended 2
Extended 3
ReiserFS
XFS
JFS
Windows Virtual FAT (vfat)
Memory Swap

By the way, QTparted does not work on my system because when I try to login it says No Device Found. Maybe you're not using root user? 
However, I am the only user of this computer and I don't know how to log in to modify things except when I get prompted by a program to enter my password. 

In addition to my questions on formatting and resizing, I wanted to be able to use a KDE desktop in Ubuntu as some of the language-learning tools I have (i.e. Applications --> Chinese --> Chinese/English dictionary) don't work and I was thinking maybe it was because they only want to run in a KDE environment. Would I be better off creating a new partition and installing Kubuntu instead? Would having a KDE desktop environment accessible from Ubuntu slow my Ubuntu? By the way, I think I only know enough to screw up my computer, as I'm a linux newbie and a life-long Windows user (I could use a little MS-DOS when I was little, enough to know not to type deltree C: for the best game ever!). So if there are any major no-no's that a newb might not be aware of, if you can point me to a warning thread or just tell me here, I'd really appreciate any assistance. 

Cheers!

---

### Post by Bachstelze on 2006-08-25
Hi and welcome to UBuntu :)

AFAIK, you can't move the beginning of a partition so if you shrink your sda2 partition, all the free space will be after it, thus it won't be possible to grow sda1 of course. 

For a FS both readable and writeable by Linux and Windows, you can either use FAT32, read/writeable natively by both OSes, or ext3, for which you'll need a Windows driver to read/write. If you use FAT32, it's better to format it using XP's Disk Manager than parted.

I get it you're using Ubuntu, try gparted instead of qtparted as a GUI for parted.

---

### Post by Dar on 2006-08-25
Thanks HymnToLife. Okay, I have Gnome Partition Editor now. I unmounted the NTFS drive. How would I go about moving my linux installation to the start of the disk and creating a new, large partition for shared files? 

My current plan:
Unmount NTFS partition. Delete it. Create a new 10gb ext3 partition in that space, leaving the rest unused. Somehow copy all the contents of my current linux partition to the new partition. Delete the old linux partition, create a new partition in FAT32 (is it possible to select this or must I select VFAT and cross my fingers it chooses the right FAT32??). Avoid touching the swap file partition the whole time. 

So, could this plan work? What commands would I need to know? Where can it go wrong? I'm thinking maybe the swap partition file, which is /dev/sda5 and located inside /dev/sda3 (extended format) might be a potential problem.

---

### Post by Bachstelze on 2006-08-25
I don't know if it's possible to move the installation, if I were you I would just reinstall. All the rest is OK.

For the FAT32, as I told you, just create a patition and leave it unformated, then use XP's Disk Manager to format it as FAT32.

---

