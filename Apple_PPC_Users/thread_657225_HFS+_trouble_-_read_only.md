---
title: "HFS+ trouble - read only"
date: 2008-01-03
forum: Apple PPC Users
---

### Post by samden on 2008-01-03
I know this is a very common question with heaps of posts about it. However for some reason I cannot get it to work however many suggestions I try from other posts, so I am forced to post the same question again. 

I am running Feisty on an iBook G4. I have currently got Feisty installed on an external firewire hard drive. This drive also contains a hfs+ partition that I need to be able to mount in Ubuntu. Journaling is disabled on this partition, and just to make sure I have enabled and disabled it through the command line in OSX.

The partition appears on the desktop and mounts when I double click on it. However it only mounts as read only. The permissions dialog gives the owner as root.

I have tried the following commands to get it to mount:
```
sudo umount /dev/sda5
sudo mount -t hfsplus /dev/sda5 /mnt/SD_Backup
```
This gives no error messages, but changes nothing - the partition mounts as read only.

I have also edited my /etc/fstab to the following:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=f44e66af-e259-4c6d-8fea-00f2a5453b8d /               ext3    defaults,erro$
# /dev/sda8
UUID=398e2dec-40e1-4084-9d8b-068b0d41475c none            swap    sw           $
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda5       /mnt/SD_Backup hfsplus user,noauto,rw 0 0 
```
This also does not appear to make a difference.

What am I doing wrong?

---

### Post by frog_pilot on 2008-01-03
IMHO this mistake isn't a result of your ubuntu configuration.

You have to do a proper shut down of your OSX system. If your OSX freezes during shutdown, your hfs volumes seem to be corrupted for ubuntu. Do a proper shut down in OSX and try again. When your problem still exists, start a volume repair with OSX disk utility. After this it should be possible to mount this volume as rw from ubuntu with your settings. Note, that ubuntus hfs tools are very sensitive in these cases, my hfs volumes often mount ro due to similar problems.

---

### Post by Gen2ly on 2008-01-04
I wrote a post on this that might be helpful:

[http://ubuntuforums.org/showthread.php?t=392287&highlight=repair+hfsplus](http://ubuntuforums.org/showthread.php?t=392287&highlight=repair+hfsplus)

---

### Post by samden on 2008-01-07
frog_pilot:
Thanks for the suggestion. I always do a proper shutdown of OSX, it never freezes, so I doubt this is the problem. However just to be sure I have conducted a volume repair with disk utility. I have also unmounted the drive in OSX before shutting down just to make sure it is unmounted correctly. Neither of these things have fixed the problem, I am still only able to mount the partition as read only.

Dirk.R.Gently:
Thankyou for the link, it is a good how-to. I had a look at it previously and tried some of the suggestions, as I recall it still wasn't working after the first half of the instructions, I then had problems with compiling build-essential. However this was last week and my memory is not serving me well. I will go back through your instructions in detail and post again when I have done so.

---

### Post by oswaldkelso on 2008-01-09
> **samden said:**
> 
What am I doing wrong?

This is how I do it from my notes.

How to  read and write to osx patrition from debian (and probably ubuntu)

The way I did this was create a user on my Debian system with the same user name and password as the user on my osx partition. I can now read all that user data. I can  also write to the osx partition. If your osx partition is formatted as hfs you can read and write to it. The standard mac file system is hfs+(plus)
To change your mac file system to hfs  from hfsplus (journaled)  Start your computer from  a install disk or another mac partition and using the disk utility change  the file system  with cmd- j
Note: If using a disk as soon as the install disk has started  select top left icon - disk utilities then change file system with cmd-j  its easy to miss this. Exit out and restart osx, in osx I select the  hd icon and  select cmd-i, this will give you imformation on the drive.  goto ownership and permissions the sections are: you can -  owner - access and  group - access and others. change these setting, put read & write  to the users and groups you require then click applly to enclosed items.

Back in debian/ubuntu open a terminal create a mount point.

code: 

mkdir /media/emac1

to mount that partition manually

code:

mount /dev/hda9 /media/emac1 -t hfsplus

code:

mkdir /media/emac2

to mount that partition manually

code:
mount /dev/hda10 /media/emac2 -t hfsplus

NOTE: I have 2 mac partitions called emac1 and emac2 change the names to the names of your partitions. Also my partitions are mounted at hda9 and hda10 to find out where your partitions are in a terminal type.

CODE:

$ df -h

this is what was shown on my system

g5@debian1333:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda17            6.5G  4.3G  1.9G  71% /
tmpfs                 505M     0  505M   0% /lib/init/rw
udev                   10M  176K  9.9M   2% /dev
tmpfs                 505M     0  505M   0% /dev/shm
/dev/hda19             20G   19G  705M  97% /home
/dev/hda10             30G   22M   30G   1% /media/emac2
/dev/hda9             101G   72G   30G  71% /media/emac1
/dev/hdc              4.4G  4.4G     0 100% /media/cdrom0

........................................................................................................................

to list the file systems as root

# fdisk -l

be careful with fdisk as you can deleat your system with it. read man fdisk

this is what was shown on my system you can see my partition names for hfs at dev/hda9 and dev/hda10 

debian1333:/home/g5# fdisk -l
fdisk: Symbol `sys_errlist' has different size in shared object, onsider re-linking
/dev/hda
        #                    type name                  length   base      ( size )  system
/dev/hda1     Apple_partition_map Apple                     63 @ 1         ( 31.5k)  Partition map
/dev/hda2          Apple_Driver43 Macintosh                 56 @ 64        ( 28.0k)  Driver 4.3
/dev/hda3          Apple_Driver43 Macintosh                 56 @ 120       ( 28.0k)  Driver 4.3
/dev/hda4        Apple_Driver_ATA Macintosh                 56 @ 176       ( 28.0k)  Unknown
/dev/hda5        Apple_Driver_ATA Macintosh                 56 @ 232       ( 28.0k)  Unknown
/dev/hda6          Apple_FWDriver Macintosh                512 @ 288       (256.0k)  Unknown
/dev/hda7      Apple_Driver_IOKit Macintosh                512 @ 800       (256.0k)  Unknown
/dev/hda8           Apple_Patches Patch Partition          512 @ 1312      (256.0k)  Unknown
/dev/hda9               Apple_HFS mac1               210682256 @ 1824      (100.5G)  HFS
/dev/hda10              Apple_HFS mac2                62914560 @ 210684080 ( 30.0G)  HFS
/dev/hda11        Apple_Bootstrap untitled                1954 @ 331180673 (977.0k)  NewWorld bootblock
/dev/hda12        Apple_UNIX_SVR2 etchr1              13671876 @ 331182627 (  6.5G)  Linux native
/dev/hda13              Apple_HFS untitled                1954 @ 273598640 (977.0k)  HFS
/dev/hda14        Apple_UNIX_SVR2 swap                 2337891 @ 344854503 (  1.1G)  Linux swap
/dev/hda15        Apple_UNIX_SVR2 etchh1              51104694 @ 347192394 ( 24.4G)  Linux native
/dev/hda16        Apple_Bootstrap untitled                1954 @ 273600594 (977.0k)  NewWorld bootblock
/dev/hda17        Apple_UNIX_SVR2 root2               13671876 @ 273602548 (  6.5G)  Linux native
/dev/hda18        Apple_UNIX_SVR2 swap                 1951172 @ 287274424 (952.7M)  Linux swap
/dev/hda19        Apple_UNIX_SVR2 home2               41955077 @ 289225596 ( 20.0G)  Linux native

Block size=512, Number of Blocks=398297088
DeviceType=0x0, DeviceId=0x0
Drivers-
1: @ 64 for 23, type=0x1
2: @ 120 for 36, type=0xffff
3: @ 176 for 21, type=0x701
4: @ 232 for 34, type=0xf8ff

/dev/hdc
        #                    type name                length   base    ( size )  system
/dev/hdc1     Apple_partition_map Apple                   63 @ 1       ( 31.5k)  Partition map
/dev/hdc2               Apple_HFS DiscRecording 3.1.3f2 9064484 @ 1160    (  4.3G)  HFS

Block size=2048, Number of Blocks=2266121
DeviceType=0x0, DeviceId=0x0

............................................................................................................................................................................................

Then i added them to my fstab file (the last 2 lines) so they were there on boot.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda17      /               ext3    defaults,errors=remount-ro 0       1
/dev/hda19      /home           ext3    defaults        0       2
/dev/hda18      none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

/dev/hda9       /media/emac1     hfsplus user,noauto,rw 0 0
/dev/hda10      /media/emac2     hfsplus user,noauto,rw 0 0

....................................................................................................................................................................................
Note : even though I changed  from hfsplus to hfs I have not changed my fstab file  as "if it aint broke dont fix it" i.e. its been working fine  so I left it.
Done.

EDIT:
I just noticed an Error in my notes the command is df -h not du -h I 'll go change my notes!!!

g5@debian1333:~$ df -h

Filesystem Size Used Avail Use% Mounted on
/dev/hda17 6.5G 4.8G 1.4G 79% /
tmpfs 505M 0 505M 0% /lib/init/rw
udev 10M 176K 9.9M 2% /dev
tmpfs 505M 0 505M 0% /dev/shm
/dev/hda19 20G 11G 7.9G 58% /home
/dev/sda1 110M 110M 0 100% /media/sda1
/dev/hda9 101G 85G 16G 85% /media/emac1
/dev/hda10 30G 29G 1.1G 97% /media/emac2
g5@debian1333:~$
__________________

---

