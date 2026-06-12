---
title: "Shared Linux/XP partition went missing after installation!"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by kiwi8mail on 2007-12-09
Hi all - good to finally get Ubuntu installed!   However, I have a slight problem.   I am an absolute Ubuntu beginner, and have tried a few solutions seen in forums, as yet with no luck.   I'd appreciate any assistance someone can give...

In general installation went well - a dual boot system with XP.   However, during installation I attempted to set up a shared partition (FAT32) to give both Ubuntu and XP read and write access to my documents and photos.   Installation seemed to go ok, but the trouble is that this partition doesn't show up following the installation, in either Ubuntu or XP.   It should be about 14GB in size from memory.   (There is also a swap partition I created, and that does show up - see below).

Is it just not showing up because it hasn't been formatted?    (Incidentally the Linux partition doesn't show up at all in XP, although I understand that's normal). 

I've done an fdisk command, and this is what I get:

     andrew@andrew-laptop:~$ sudo fdisk -l

     Disk /dev/sda: 40.0 GB, 40007761920 bytes
     255 heads, 63 sectors/track, 4864 cylinders
     Units = cylinders of 16065 * 512 = 8225280 bytes

        Device Boot      Start         End      Blocks   Id  System
     /dev/sda1   *           1        1824    14651248+   7  HPFS/NTFS
     /dev/sda2            1825        2006     1461915   82  Linux swap / Solaris
     /dev/sda3            2007        3222     9767520   83  Linux
     andrew@andrew-laptop:~$ 

Any assistance in locating this missing space would be appreciated!   Apart from anything else, I need a space in which to transfer all my legacy documents and photos (temporarily backed up externally).

Thanks!
Andrew

---

### Post by The Cog on 2007-12-09
Well, that fdisk says its not there. I don't know what went wrong at install time.

I notice that there seems to be spare space on the disk. sda3 ends at cylinder 3222 but the disk has 4864 cylinders. So you could make another partition. I suggest that you install package gprted, and then use gparted to make/format the fourth partition.

---

