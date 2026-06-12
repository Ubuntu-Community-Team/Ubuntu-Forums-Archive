---
title: "Partition plan for new install"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by leavingOS2 on 2006-12-28
I'd appreciate advice or comment on my plan to partition my hard drives for a new install of Ubuntu.  I have limited experience with Linux, but significant experience with multiboot systems including OS2 (and its boot manger and LVM), Win2K and WinXP, as well as Partition Magic.  I've been able to boot from the Ubuntu live CD and like what I saw.  However, I would like to keep a number of old operating systems available either from certain software/hardware that I have that will only run from one OS, or compatibility with my employer's system.  Here is what I have and then what I plan to do (which includes replacing the 9GB physical disk one with a 73GB disk):

AS IS--
	Physical Drive 1   9GB
Pri 1     IBM Boot Mgr                        7MB
Pri 2     C: Win 98               FAT32     2GB
            empty space                        2.5GB
Log 1     F: OS2 system       HPFS       1GB
Log 2     G: OS2 apps/data  JFS(OS2) 2GB
            empty                                  1GB

	Physical Drive 2     18 GB
Pri 1      D: WinXP               NTFS       12GB
Log 1    Data                      FAT32       6GB

TO BE--			
	New Physical Drive 1     73GB
Pri 1     IBM Boot Mgr                         7MB
Pri 2     C: Win 98               FAT32      2GB
Pri 3     /boot                      ext3        100MB
Pri 4     E: W2K                   NTFS       5GB
Log 1    F: OS2 system        HPFS       1GB
Log 2    G: OS2 apps/data   JFS(OS2)  2GB
Log 3    /swap                     ext3        1.5GB
Log 4    / (root)                   ext3        31GB
Log 5    Data1                     NTFS       20GB
Log 6    Data2                     FAT32      10GB

	Physical Drive 2     18 GB
Pri 1     D: WinXP                NTFS        18GB


While I'd like to say "I'd like to keep things simple," I guess I can only really say "I'd like to introduce as few new complexities as I can get away with, until I feel more confident with Linux/Ubuntu.

Comments?
LeavingOS2

---

### Post by paridoth on 2006-12-28
wow thats a pretty complicated setup there, looks like you got everything though, just make sure you have everything backed up, never know what could go wrong, and i suggest not using partition magic if you can help it, i used partition magic when i first started using ubuntu and i had all sorts of problems, but that could have been just me

---

### Post by Sef on 2006-12-28
> i suggest not using partition magic if you can help it, i used partition magic when i first started using ubuntu and i had all sorts of problems, but that could have been just me

No, it wasn't you.  Partition Magic and Linux tend not to get along.   Instead get [GParted]("http://gparted.sourceforge.net"), it works great and costs $0.00.

---

### Post by leavingOS2 on 2006-12-28
Thanks for the replies.  I was planning to use PM to set up the rest of the partitions, leaving the linux areas unpartitioned.  Then move to the OS2 LVM tool to add things to the boot manager.  Only then was I going to go to the Ubuntu install and let it partition the remaining unpartitioned space.

I'll have to see when and where I can reset the active partition from the boot manager partition to Ubuntu to make it through the install process.

Maybe I can reduce complexity by leaving out the W2k, since I have other computers in the home network running W2K.

Thanks again.
LeavingOS2

---

