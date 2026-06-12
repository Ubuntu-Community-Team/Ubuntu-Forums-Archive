---
title: "all directories placed on single partition"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by wet_colored_arch on 2007-08-25
Relative noob, toyed with Dapper and Edgy and have been running Fiesty in dual boot with few problems.  However, one of the remaining problems I have is with the directory structure and partitions.  All directories were placed on a single partition and this partition keeps filling up as I add applications and forces me to resize it even though other partitions are wholly empty.

**Can I simply move the directories with a mv to a new partition?  What does the terminal command look like?  Do I need to unmount anything first - how? Do I then need to remount and alter any path information or alter anything in /etc/fstab?  **

I did work with Gparted and can resize/enlarge the partition being used but I want to actually move the existing directories and use the memory available in these other partitions.  When I tried the liveCD  (recently, a second time)  it indicated that  the area with my  requested slimmed down boot directory would have to be reformatted and I was concerned that it wouldn't move the data from the "single, ever increasing partition" to the alternate partitions first, so I never executed. 

I also tried to "move" with File Browser but the empty partitions don't show up and there is no "move" capability (that I see). The disk usage analyzer does see the empty partitions and does indicate all directories are in a single partition - except for a single partition being used to preserve Windows XP for dual booting, which works fine.

I don't want to simply keep enlarging the partition currently being used because it has my boot directory on it and I have an older machine (extensive upgraded circa 2000 Gateway machine).  With Edgy I had a few problems initially because the boot partition was too large.  If I remember right, the problem was something to do with my older BIOS and the boot information needing to be in the first XXXXMb  of the partition.  This is forced by keeping it small - I think.   I have some concern that if I keep increasing this partition and ever use a disk management utility it will move the now increased in size boot partition information to an incompatible location for my BIOS.

I am getting pieces of the story from Forums and Ward's "How Linux Works" book but not getting enough details to make a change and know it won't screw my system up.  Yes, I have things backed up but don't want to spend the next week straightening things out and reloading if I don't have to. 

so... is it as "simple" as sudo mv partitionold\file partitionnew\file  or some such thing?  How can I preserver or correct the altered paths and what other things do I need to correct when I make such a move?  Ideally I want the current partition to be decreased in size and only have the boot directory - I think.

---

### Post by solar george on 2007-08-25
Right, under linux partitions are mounted as directories, so if you want to move a directory to another partition you would have to,

1. Mount the partition under /media/*partition*

2. Move the directory across e.g from /home/ to /media/*partition*, preserving permisions.

3. Remount the partition where you moved the directory from and update /etc/fstab.
[COLOR="DarkRed"]
DON'T follow this - this is just an overview of what needs to happen tell me exactly what you want to do (what directory, what partition, partition layout ect.) and I will write a proper guide.[/COLOR]

---

### Post by wet_colored_arch on 2007-08-25
My apologies if I am "mixing" partitioning and directories terminology inappropriately.  I don't understand the concept very well as I don't understand why a partition should be "mounted" on a directory.  Intuitively, I think of it as the other way around where the directory is mounted on the partition.  I think this concept is confusing me.

**right now everything (almost) is in root:**

michael@kitchen-desktop:/$ ls -l
total 76
drwxr-xr-x   2 root root  4096 2007-04-20 20:10 bin
drwxr-xr-x   3 root root  4096 2007-06-24 20:53 boot
lrwxrwxrwx   1 root root    11 2007-04-20 19:55 cdrom -> media/cdrom
drwxr-xr-x  12 root root 13860 2007-08-25 17:57 dev
drwxr-xr-x 111 root root  4096 2007-08-25 18:26 etc
drwxr-xr-x   7 root root  4096 2007-04-21 10:12 home
drwxr-xr-x   2 root root  4096 2007-04-15 07:48 initrd
lrwxrwxrwx   1 root root    33 2007-05-28 14:43 initrd.img -> boot/initrd.img-2.6.20-16-generic
lrwxrwxrwx   1 root root    33 2007-04-20 20:08 initrd.img.old -> boot/initrd.img-2.6.20-15-generic
drwxr-xr-x  16 root root  4096 2007-04-20 20:10 lib
drwx------   2 root root 16384 2007-04-20 19:53 lost+found
drwxr-xr-x   5 root root  4096 2007-08-25 17:57 media
drwxr-xr-x   2 root root  4096 2007-04-12 05:11 mnt
drwxr-xr-x   3 root root  4096 2007-07-29 19:21 opt
dr-xr-xr-x 132 root root     0 2007-08-25 13:56 proc
drwxr-xr-x  10 root root  4096 2007-08-11 20:47 root
drwxr-xr-x   2 root root  4096 2007-07-29 15:08 sbin
drwxr-xr-x   2 root root  4096 2007-04-15 07:48 srv
drwxr-xr-x  11 root root     0 2007-08-25 13:56 sys
drwxrwxrwt  11 root root  4096 2007-08-25 18:09 tmp
drwxr-xr-x  12 root root  4096 2007-02-07 08:04 usr
drwxr-xr-x  16 root root  4096 2007-04-15 08:01 var
lrwxrwxrwx   1 root root    30 2007-05-28 14:43 vmlinuz -> boot/vmlinuz-2.6.20-16-generic
lrwxrwxrwx   1 root root    30 2007-04-20 20:08 vmlinuz.old -> boot/vmlinuz-2.6.20-15-generic


**I'd like to get thispartition smaller and only include boot, moving the other directories to available partitions.  ** (for reasons cited previously above).  Currently hda1 is where my windows XP information resides, hda2 is where "/" resides (I think).  I have had to repetitively increase size of hda2 as it fills up.  I was/am a little surprised to see the mounting on hda6, 7, 8 below with home, usr, var as in root there are directories with this information.  I think this happened yesterday when I was tinkering with the live CD to try and repartition and move the directories.  It looks like it changed the mounting but the original directories remained in hda2.  (I had tried to cancel without changing anything yesterday but I am guessing it changed the fstab)

michael@kitchen-desktop:/dev$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda2              5036764   3758400   1124864  77% /
varrun                  160480       216    160264   1% /var/run
varlock                 160480         0    160480   0% /var/lock
procbususb              160480       112    160368   1% /proc/bus/usb
udev                    160480       112    160368   1% /dev
devshm                  160480         0    160480   0% /dev/shm
lrm                     160480     33788    126692  22% /lib/modules/2.6.20-16-generic/volatile
/dev/hda6             30233896    176200  28521884   1% /home/hda6
/dev/hda1             25587040   9044720  16542320  36% /media/hda1
/dev/hda9             30233896    176200  28521884   1% /media/hda9
/dev/hda7             30233896    176200  28521884   1% /usr/hda7
/dev/hda8             30233896    176200  28521884   1% /var/hda8

---

### Post by solar george on 2007-08-26
Can you post a screen shot of cfdisk,

> sudo cfdisk /dev/hda

cfdisk is a console partition manager, and /dev/hda is your harddrive (in linux everything is represented by a file).

---

### Post by vanadium on 2007-08-26
If you are not quite confortable with the difference between directories and partitions, then do not bother resizing partitions and moving entire system directory trees. You will probably get a long way already just by reorganizing your user data over the available partitions. You can just move portions of your user documents to other partitions, then create a symbolic link in the old location to the new location. That way, your data will be available in the same location just like before, only will they physically live on a different partition.

---

### Post by wet_colored_arch on 2007-08-26
I figure I'm in this for the long term so if solar george is willing to get me started, I'll muddle along.  (I have things well backed up if I screw up too.)  It's not that I don't understand directories and partitions at all, its just that my understanding is incomplete and "feels" wrong in a few areas.  The biggest things I don't get are:
+ why are partitions "mounted" to directories?  I would of thought directories would "mount" on partitions.
+ if I move application or user files, how will the system find them?  (Is there an equivalent to windows shortcuts for the paths that have to be modified when I move application files?)

I don't need every detail for every directory, but if I can see how to successfully move/mount, alter the path (if needed) for one directory, fstab, then I hope I can go from there.    (cfdisk is below: pretty sure hda1 is my XP installation, The free space on hda2 is what I recently increased using Gparted because I couldn't log on because it was full.  The error message I was getting indicated that a user file related to password couldn't be accessed or some such thing and when I searched .... the search results suggested disk full was the root cause.  When I used "du", it was indeed full at 100%.)

Disk Drive: /dev/hda
                       Size: 203928109056 bytes, 203.9 GB
             Heads: 255   Sectors per Track: 63   Cylinders: 24792

    Name        Flags      Part Type  FS Type          [Label]        Size (MB)
 ------------------------------------------------------------------------------
    hda2                    Primary   Linux ext3                        5239.51 
                            Primary   Free Space                        2632.09
    hda1        Boot        Primary   W95 FAT32 (LBA)                  26213.97
    hda5                    Logical   Linux swap / Solaris              2097.45
    hda6                    Logical   Linux ext3                       31453.48
    hda7                    Logical   Linux ext3                       31453.48
    hda8                    Logical   Linux ext3                       31453.48
    hda9                    Logical   Linux ext3                       31453.48
    hda10                   Logical   Linux                            41924.26

---

### Post by solar george on 2007-08-27
> why are partitions "mounted" to directories? I would of thought directories would "mount" on partitions.

Historically that's how UNIX has done it (I think) and it makes it much more convenient when spreading files across several different partitions - you remember in Windows how you had to tell a program to install on D: instead of C:.

> + if I move application or user files, how will the system find them? (Is there an equivalent to windows shortcuts for the paths that have to be modified when I move application files?)

You can use symbolic links (symlinks) which are better than windows shortcuts as they redirect everything - windows short cuts only work within the GUI.

You should try and find a basic guide to the linux directories and partitions - it will be help you to understand what you are doing - not just slavishly follow a guide. Try looking on the wiki.

---

### Post by solar george on 2007-08-27
This may be of interest to you [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by wet_colored_arch on 2007-09-11
thanks .. I was able to adapt the information at the link to get what I wanted but have two last questions:
1) should I be concerned if I have a partition mounted to two points - see screenshot in attached file for hda7
2) where is the filesystem "held"? while things are mounted to it.  As I still think it terms of windows it isn't intuitive to me yet that physical things (partitions on hard drive) can be mounted on virtual filesystem.   I am starting to think of mounting as "associating".  I continue to read different forums but haven't found one yet that makes this entirely clear to me.  any comments to help me understand?

things seem to work fine and thanks

---

### Post by vanadium on 2007-09-11
Linux is very simple in terms of organising your data. At the very top, there is the root directory /.  In the root directory, there are directories ("folders") that in turn contain other folders. All you have on your system is located somewhere in that directory structure.

"Mounting" means attaching something, for example the partition of an external drive, on a directory within that directory structure. The directory where you mount is called the "mount point". Once the partition is mounted, the directory where it is mounted does not anymore appear to be empty, but it contains the directories and data of your drives' partition. This way, you can expand your directory structure.

This indeed, partitions are mounted within a directory structure. The top of that directory structure, / or root, obviously by itself lives on a partition, your root partition on one of your drives.

> 1) should I be concerned if I have a partition mounted to two points - see screenshot in attached file for hda7

When you are root, you can do anything you want under Linux, even mess up your system. Technically indeed, a partition can be mounted several times. This is not a tidy approach, though. You should mount any partition only once, preferably (but this is merely convention) in an easy to remember point, i.e. /mnt of /media. I advice to mount permanent drives in /mnt and leave /media to the automatic mounting of removable USB sticks and drives.

As a root, you want to make your system user friendly to users. Users, however, should never have to look into /mnt to find their data. For this reason, you should create appropriate symbolic links to the mounted data within the user's home directory. That way, the user can find and access all his data under his own home directory. For practical purposes, a symbolic link acts the same as a directory.

> where is the filesystem "held"? while things are mounted to it. As I still think it terms of windows it isn't intuitive to me yet that physical things (partitions on hard drive) can be mounted on virtual filesystem. I am starting to think of mounting as "associating". I continue to read different forums but haven't found one yet that makes this entirely clear to me. any comments to help me understand?


As I already said, your root directory resides on a partition on the disk where the operating system is booted. Also the mount points are physically located there. To these mount points, you then attach other partitions that can reside on the same drive, on different drives or on a network.

---

### Post by hyper_ch on 2007-09-11
Psychocat's homepage has it all explained very easily:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

This is for making a seperate /home dir but you can use it to move any dir to its own partition.

---

