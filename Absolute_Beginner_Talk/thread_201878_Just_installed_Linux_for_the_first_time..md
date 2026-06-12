---
title: "Just installed Linux for the first time."
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by stuart_75 on 2006-06-22
Hi all,

Im brand new to Linux, after hearing people saying how good it is. After getting sick of Microsofts world domination Ive decided to give Ubuntu a whirl.

Now then, after spending all day trying to set up a dual boot system I think Im nearly there.

One problem though, I hope you guys can help.

I have a 200Gb Hd and have split it 3 ways. XP pro on the first partition (NTFS),    ubuntu on the second partition(ext3)?? and a "My Files" partition (FAT32) at approx 120Gb.

When I try and access the "MY Files" partition in ubuntu, it says unable to mount and I cant access the partition. The same applies to the XP pro partition, but I knew that would happen being in NTFS.

Any Ideas where Im going wrong? I would like a common partition that both operating systems can write to.

Thanks!!

---

### Post by xxrealmsxx on 2006-06-22
[QUOTE=stuart_75]Hi all,

Im brand new to Linux, after hearing people saying how good it is. After getting sick of Microsofts world domination Ive decided to give Ubuntu a whirl.

Now then, after spending all day trying to set up a dual boot system I think Im nearly there.

One problem though, I hope you guys can help.

I have a 200Gb Hd and have split it 3 ways. XP pro on the first partition (NTFS),    ubuntu on the second partition(ext3)?? and a "My Files" partition (FAT32) at approx 120Gb.

When I try and access the "MY Files" partition in ubuntu, it says unable to mount and I cant access the partition. The same applies to the XP pro partition, but I knew that would happen being in NTFS.

Any Ideas where Im going wrong? I would like a common partition that both operating systems can write to.

Thanks!![/QUOTE]

Are you logged in as root?

---

### Post by odysseus.lost on 2006-06-22
First of all you could have mounted during the installation process, it usually has two default options (/dos or /windows).

Now, a simple way to mount the fat32 partition from the command line is make a dir somewhere:
let's say /mnt/fat32
then do
mount -t vfat /dev/hda# /mnt/fat32
where # is the partition number. Now this might only give you read permissions to the partition... but although it is very simple I cannot remember from the top of my head what is the extra argument to make it read/write (maybe -rw). Try the manual pages of mount (man mount).

If you want to permanently mount it add the following line to your /etc/fstab
/dev/hda#  /dos  vfat  defaults,utf8.umask=007,gid=## 0 1
where # will your fat32 partition number and ## will the group id of the group you want to have write permissions (I think).
and then do
mount -a

Some commands may need root privileges so prefix them with a sudo. If you don't know what sudo is, then check the man pages (man sudo).

One tip, your partitioning seems a bit bad... firstly hopefully you have defined a swap partition (I thinkubuntu does not let you proceed with the installation without it). Secondly it's safer to have /home on another partition since if you need to reinstall the system you will not have to lose your files.. furthermore the /home can be shared by more than one linux distros...

If you are a  beginner the ubuntu started guide will save you a lot of trouble and frustration...
[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

---

### Post by learning on 2006-06-22
Check out this link.

[http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)

This guide is great

---

### Post by mips on 2006-06-22
When you installed ubuntu the system partition should be "/" and the data partition should be "/home", these options are available during install.

---

### Post by presentt on 2006-06-22
A couple of things might be wrong.  First, if you formatted your FAT32 partition as 120GB during the WinXP install, it won't work.  XP's installer's partitioner cannot create FAT32 partitions greater than 32GB; it can mount them if they were created *after* the installation, but not if they were made during the installation.

Also, watch what partition you are trying to mount.  You didn't mention it, but by default Ubuntu creats a swap partition to use as virtual memory, kind of like the XP pagefile.  It's possible you are trying to mount that partition instead of the FAT32 partition.

The way I have my partition tables set up is as follows:
--  an XP NTFS filesystem mounted as /media/sda1 in Ubuntu, accessed natively by Windows
-- an ext3 filesystem mounted as / in Ubuntu, viewable but not writeable by Windows
-- an ext2 filesystem mounted as /home in Ubunty, both viewable and writeable by Windows using [this tool]("http://www.fs-driver.org/index.html").  There are other tools that do the same thing.  Search google for '[windows mount ext2]("http://www.google.com/search?hl=en&q=windows+mount+ext2&btnG=Google+Search").'
-- a swap partition that remains unmounted

I'm very happy with my setup; I easily switch between XP and Ubuntu, and have all of my personal files on /home.  It's my home folder under Linux, and set as My Documents under Windows.  If you don't have many files, I'd recommend formatting your current FAT32 partition as ext2, and mounting it as /home, **after backing everything up**.

Good luck, hope this helps.

---

### Post by stuart_75 on 2006-06-22
Blimey, I didnt expect this kind of response so quickly!

Ive tried using the disk manager to set up the partition correctly, but i dont understand all this /root /boot /home business???

The partition has now dissapeared from the file manager and I cant open disk manager as I get a error message.

Shall I format everything and start from scratch??

Ive used xp for years and know it quite well, but this seems like a whole new kettle of fish. I think I need to read up about linux, as if I cant grasp these basic commands then Im going to be stuffed.

Thanks for the help!

---

### Post by rccharles on 2006-06-22
[QUOTE=stuart_75]
The same applies to the XP pro partition, but I knew that would happen being in NTFS.

[/QUOTE]

How to mount a ntfs filesystem in linux:
  [http://www.psychocats.net/ubuntu/mountwindows.php](http://www.psychocats.net/ubuntu/mountwindows.php)

And the whole thing:
  [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

I suggest going to the library or bookstore and getting a book on Linux.

Robert

---

### Post by steve.horsley on 2006-06-22
Linux is certainly a bit different to windows. There is some learning and also some un-learning to be done. The hardest part is the un-learning, I think.

Have a google for linux guide, linux intro etc. Also, this site [http://www.tldp.org/](http://www.tldp.org/) has good stuff. 

Please open a command terminal (Applications->Accessories->Terminal), enter the following commands and post the results back here. They will tell us a lot about the state of your disks. The first one will prompt ypu for your password again because you are asking for SuperUser rights:
[B]sudo fdisk -l
df
cat /etc/fstab
[/B]

---

### Post by stuart_75 on 2006-06-23
Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...
gunny@gunny-desktop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda3             45841712   2137076  41376016   5% /
varrun                  518048        80    517968   1% /var/run
varlock                 518048         4    518044   1% /var/lock
udev                    518048       108    517940   1% /dev
devshm                  518048         0    518048   0% /dev/shm
lrm                     518048     18856    499192   4% /lib/modules/2.6.15-25-3 86/volatile
gunny@gunny-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
gunny@gunny-desktop:~$

I hope this helps Steve.

Ive seen what looks like a decent book about linux and based on the ubuntu release, downside its £23. But i guess reference books arnt cheap, so might be a good investment.

Stuart

---

### Post by steve.horsley on 2006-06-23
From what I see here, your disk is not partitioned into three as you said it was. At least - I don't think so. Your Ubuntu is installed on the third partiton /dev/hda3 and you are using the seventh (hda7) partition for swap space. We really need the output from 
**sudo fdisk -l**
but notice that is a lower-case 'L' at the end. It seems you typed something different, maybe a 1.

Do you have any idea what the other partitions are?

---

### Post by stuart_75 on 2006-06-23
[QUOTE=steve.horsley]From what I see here, your disk is not partitioned into three as you said it was. At least - I don't think so. Your Ubuntu is installed on the third partiton /dev/hda3 and you are using the seventh (hda7) partition for swap space. We really need the output from 
**sudo fdisk -l**
but notice that is a lower-case 'L' at the end. It seems you typed something different, maybe a 1.

Do you have any idea what the other partitions are?[/QUOTE]

This might help....

Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3276    26314438+   7  HPFS/NTFS
/dev/hda2            3277       18994   126254835    f  W95 Ext'd (LBA)
/dev/hda3           18995       24792    46572435   83  Linux
/dev/hda5            3277       18745   124254711    b  W95 FAT32
/dev/hda6           18746       18994     2000061   82  Linux swap / Solaris
gunny@gunny-desktop:~$

---

### Post by steve.horsley on 2006-06-23
That's a little odd - your fstab says the swap partition is on hda7, but fdisk says it's on hda6. I guess your installer got confused. 

Try making /etc/fstab look like this (after backing up the original). You need to choose where to mount the two windows partitions - I have suggested /media/ntfs and /media/fat - change the names if you prefer. First create the mount points with these two commands:
[B]sudo mkdir /media/ntfs
sudo mkdir /media/fat[/B]
Here is the new /etc/fstab for you to try:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda3 / ext3 defaults,errors=remount-ro 0 1
/dev/hda6 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hda1 /media/ntfs ntfs  nls=utf8,umask=222  0       1
/dev/hda5  /media/fat  vfat    iocharset=utf8,umask=000 0       1

```
See this guide:
[http://ubuntuguide.org/wiki/Dapper#Windows](http://ubuntuguide.org/wiki/Dapper#Windows)

---

### Post by stuart_75 on 2006-06-23
[QUOTE=steve.horsley]That's a little odd - your fstab says the swap partition is on hda7, but fdisk says it's on hda6. I guess your installer got confused. 

Try making /etc/fstab look like this (after backing up the original). You need to choose where to mount the two windows partitions - I have suggested /media/ntfs and /media/fat - change the names if you prefer. First create the mount points with these two commands:
[B]sudo mkdir /media/ntfs
sudo mkdir /media/fat[/B]
Here is the new /etc/fstab for you to try:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda3 / ext3 defaults,errors=remount-ro 0 1
/dev/hda6 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hda1 /media/ntfs ntfs  nls=utf8,umask=222  0       1
/dev/hda5  /media/fat  vfat    iocharset=utf8,umask=000 0       1

```
See this guide:
[http://ubuntuguide.org/wiki/Dapper#Windows](http://ubuntuguide.org/wiki/Dapper#Windows)[/QUOTE]

Thanks for the help Steve, but I'll be honest with you, Im totally lost. The Dapper Drake starter guide, is very very confusing, and it asumes you already know the basic structure of Linux (which I dont). Ill be buying a book and will try to gain some more knowledge. Im not giving up yet!

Thanks again.

Stuart

---

### Post by steve.horsley on 2006-06-24
In unix, drives don't appear as C:, D: etc. You have a root partition that contains the root directory, and other drives get grafted onto the tree as though they were just other directories. In fact, the other drives must replace an existing (usually empty) directory. So if you want your otehr two partitions to be visible to you, you have to create a directory (mount point) to mount them at. 

Here we create a couple of empty directories to mount the other two drives on. The command to create a directory is mkdir. Because we are making the directories in a place outside your home directory, you need SuperUser rights to do it, so you precede the command with **sudo**.  Open a command prompt (Applications->Accessories->Terminal) and enter the following commands:
[B]sudo mkdir /media/ntfs
sudo mkdir /media/fat[/B]
While you are there, you can make a backup of the /etc/fstab file. This file tells Ubuntu what partitions to mount and where, and we are going to edit it. So we make a backup copy first, to copy back if necessary. The copy command is cp:
[B]
sudo cp /etc/fstab /etc/fstab.backup[/B]

Now you can edit /etc/fstab and replace the contents with those I posted. It's easiest with gedit. To launch graphical programs with superuser rights, use the command gksudo first:
**gksudo gedit /etc/fstab**
Replace the contents of the file, and reboot. Hopefuly, that should do the trick.

---

