---
title: "Setting Drive Permissions"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by AKA3Toes on 2007-07-20
[FONT="Times New Roman"][SIZE="2"][color=darkred][I]---I'm very new to Ubuntu/Linux. Bear with me please.

---Okay, this is fairly simple I am sure, but I haven't found any info on it yet. I have a 250GB hard drive for storing files. It's ready to go under the name "New Volume". 

---How do I set permission for the entire drive including all subfolders and their contents? I want to allow adding, deleting, reading and writing for all* folders and files on this drive... and my RAID array when I get that sorted out. This all needs to be done for networking purposes, so if any other info is needed for setting up networking privileges, please include that info, so I can include it while editing the file

---Also need to know how to change the name of the drive(s).

system name = "Book"
my user name = "page one"
other network user names = "page number _x_"
New Volume = 

... for anyone on the network

---A preempt Thank You.[/I][/COLOR][/SIZE][/FONT]

---

### Post by bodhi.zazen on 2007-07-20
Mounting and permissions depends on the file system:

_Windows:_ [Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
For read-write: [list=number][*]vfat (FAT) use umask=000
[*]ntfs use [ntfs-3g](http://doc.gwos.org/index.php/NTFS-3g) and a fstab entry something like this:
```
/dev/hda1  /media/windows  ntfs-3g  defaults  0  0
```
[*]An alternate is ntfs-config. ntfs-config uses ntfs-3g to mount windows partitions via a gui :)
[indent][http://doc.gwos.org/index.php/Ntfs-config](http://doc.gwos.org/index.php/Ntfs-config)[/indent][/list]

_Linux_: [Psychocats Mount Linux](http://www.psychocats.net/ubuntu/mountlinux)
To set permissions, mount the partition, then chmod```
sudo chmod 777 /mount/point
```

To mount at boot you will need to edit /etc/fstab (as outlined in the links above).
For an overview of fstab see: [How to fstab](http://www.ubuntuforums.org/showthread.php?&t=283131)

_For access to ext2/3 from windows see_ : [http://www.fs-driver.org/](http://www.fs-driver.org/)

[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

---

### Post by AKA3Toes on 2007-07-23
[FONT="Times New Roman"][SIZE="2"][COLOR="DarkRed"][I]---Thanks, I'll look into it once I can offer my disks. I'm still having RAID problems and that's gotta be fixed soon or I'm gonna go berzerk. I've dug everywhere I can think of for the disk.

---There seems to be some work going on over at Linux and at nVidia, but none of the work is on the Ubuntu Distro. Would there be another distro's  kernel that would work? (E.G., SUSE, Fedora5) 

---If you'd like to take a gander at the results from mdadm, maybe you'll think something different than I, but it's looking like communication ends where the MoBo is trying to talk to Ubuntu. Ubuntu's not listening... or it stashed my combined discs somewhere... maybe I should search for a while for references in my mdadm.[/I][/COLOR][/SIZE][/FONT][CENTER]> page1@book:~$ sudo mdadm --query --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Sun Jul 22 11:58:53 2007
     Raid Level : raid0
     Array Size : 673982784 (642.76 GiB 690.16 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Jul 22 12:40:18 2007
          State : active
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 64K

           UUID : 52b73368:6043d43a:cbc66c3c:dcec90fd
         Events : 0.3

    Number   Major   Minor   RaidDevice State
       0     254        3        0      active sync   /dev/mapper/nvidia_fdacjeca3
       1       8       19        1      active sync   /dev/sdb3
       2       8       35        2      active sync   /dev/sdc3
page1:~$ cat /proc/mdstat
Personalities : [raid0] 
md0 : active raid0 dm-3[0] sdc3[2] sdb3[1]
      673982784 blocks 64k chunks
      
md2 : active raid0 dm-2[0] sdc2[2] sdb2[1]
      29302272 blocks 64k chunks
      
md1 : active raid0 dm-1[0] sdc1[2] sdb1[1]
      29302272 blocks 64k chunks
      
unused devices: <none>[/CENTER][FONT="Times New Roman"][SIZE="3"][COLOR="DarkRed"][I]

---Can't mount anything, gives me no choice to do so. Can't swap on, can't do nothin. 

---Gonna try changing from JBOD to RAID0 on my next reboot. Maybe I'll have some luck there, but I'm beginning to doubt it.

---What is LVM anyway? I've got my flags in GNOME set for RAID... also, I noticed when I was trying to raid in GNOME, that I didn't have any selection for partition for RAID, just ext3, ext2, FAT16, FAT32, linux-swap and REISERFS. AM I missing something in the program?
[/I][/COLOR][/SIZE][/FONT]

---

### Post by bodhi.zazen on 2007-07-23
> The Linux Logical Volume Manager (LVM) is a mechanism for virtualizing disks. It can create "virtual" disk partitions out of one or more physical hard drives, allowing you to grow, shrink, or move those partitions from drive to drive as your needs change. It also allows you to create larger partitions than you could achieve with a single drive.

Traditional uses of LVM have included databases and company file servers, but even home users may want large partitions for music or video collections, or for storing online backups. LVM and RAID 1 can also be convenient ways to gain redundancy without sacrificing flexibility.

[http://www.linuxdevcenter.com/pub/a/linux/2006/04/27/managing-disk-space-with-lvm.html](http://www.linuxdevcenter.com/pub/a/linux/2006/04/27/managing-disk-space-with-lvm.html)

---

