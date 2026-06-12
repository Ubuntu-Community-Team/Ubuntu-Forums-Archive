---
title: "syslinux onto usb drive"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-12-22
I have a harddrive (20gig) in a usb cradle. I want to format it for linux w/o installing they OS, only the file system.

In old MS-DOS the command was format c:/sys

what is the command in Linux?

mark@Lexington-19:~$ man format
No manual entry for format
mark@Lexington-19:~$ man syslinux
No manual entry for syslinux
mark@Lexington-19:~$ man sys
No manual entry for sys
mark@Lexington-19:~$ man disk
No manual entry for disk
mark@Lexington-19:~$ man system
No manual entry for system
mark@Lexington-19:~$ man filesystem
No manual entry for filesystem

Learned a little since posting an hour ago. It must be mkfs, but how through a usb cable?

---

### Post by Mark_in_Hollywood on 2007-12-22
Bump with some help:

mark@Lexington-19:~$ lsusb
Bus 004 Device 004: ID 06e1:d804 ADS Technologies, Inc. 

 
mark@Lexington-19:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)

/dev/sdb1 on /media/UDISK 28X type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

**/dev/sdc1 on /media/disk type ext3 (rw,nosuid,nodev)**

mark@Lexington-19:~$ sudo mkfs /dev/sdc1 -cV
[sudo] password for mark:
mke2fs 1.40.2 (12-Jul-2007)
        Using EXT2FS Library version 1.40.2

mark@Lexington-19:~$ sudo mkfs /dev/sdc -V
mkfs (util-linux-ng 2.13)
mkfs.ext2 /dev/sdc 
mke2fs 1.40.2 (12-Jul-2007)
/dev/sdc is entire device, not just one partition!
Proceed anyway? (y,n) y
/dev/sdc is apparently in use by the system; will not make a filesystem here!

How do I do the formatting?

---

### Post by Mark_in_Hollywood on 2007-12-22
SOOO 

After UNMOUNTING the drive:

mark@Lexington-19:~$ sudo mkfs /dev/sdc -V
mkfs (util-linux-ng 2.13)
mkfs.ext2 /dev/sdc 
mke2fs 1.40.2 (12-Jul-2007)
/dev/sdc is entire device, not just one partition!
Proceed anyway? (y,n) y
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
2448000 inodes, 4887792 blocks
244389 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
150 block groups
32768 blocks per group, 32768 fragments per group
16320 inodes per group
Superblock backups stored on blocks: 
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
        4096000

Writing inode tables: done                            
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 22 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.

---

### Post by Mark_in_Hollywood on 2007-12-22
What command will change file permissions on this usb disk to allow users (and root) to read and write?

---

### Post by eternicode on 2007-12-22
Just to be clear, you're trying to format your external USB drive (sdc, with the main/only partition being sdc1) with ext3 (a Linux format) for use as Linux-only storage?

```
user@computer:~$ mkfs.ext3
Usage: mkfs.ext3 [-c|-t|-l filename] [-b block-size] [-f fragment-size]
        [-i bytes-per-inode] [-I inode-size] [-j] [-J journal-options]
        [-N number-of-inodes] [-m reserved-blocks-percentage] [-o creator-os]
        [-g blocks-per-group] [-L volume-label] [-M last-mounted-directory]
        [-O feature[,...]] [-r fs-revision] [-R options] [-qvSV]
        device [blocks-count]

```

"man mkfs" for details on the switches.

Make sure it's unmounted first ("sudo umount /dev/sdc1") then ```
sudo mkfs -t ext3 /dev/sdc1
```
[color="red"]This will erase all data on the drive, and format it as ext3[/color]

Here's a test run that I just did with a file (yes, I formatted the file to ext3 ;) dd used to create the 1GB file):

```

user@computer:~$ dd if=/dev/zero of=./test.img bs=1024 count=1000000
1000000+0 records in
1000000+0 records out
1024000000 bytes (1.0 GB) copied, 30.2136 seconds, 33.9 MB/s

user@computer:~$ mkfs -t ext3 ./test.img
mke2fs 1.40-WIP (14-Nov-2006)
./test.img is not a block special device.
Proceed anyway? (y,n) y
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
125184 inodes, 250000 blocks
12500 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=260046848
8 block groups
32768 blocks per group, 32768 fragments per group
15648 inodes per group
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376

Writing inode tables: done
Creating journal (4096 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 33 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.

user@computer:~$ mkdir test

user@computer:~$ sudo mount -o loop -t ext3 ./test.img ./test

user@computer:~$ df -h test
Filesystem            Size  Used Avail Use% Mounted on
/home/andrew/test.img
                      962M   18M  896M   2% /home/andrew/test

user@computer:~$    

```

------------------------------------

Did your mkfs.ext2 on /dev/sdc work??  You're supposed to format the partition, not the drive :-P but if it works, I guess it works ;)

As for permissions, use the dmask and umask options.  For world access, use "-o fmask=0777,dmask=0777" on a command line mount, or "fmask=0000,dmask=0000" in your fstab.  dmount is for directories, fmask is for files, and umask can be used for both (I think).

---

### Post by Mark_in_Hollywood on 2007-12-22
> **eternicode said:**
> ------------------------------------

Did your mkfs.ext2 on /dev/sdc work??  You're supposed to format the partition, not the drive :-P but if it works, I guess it works ;)

It had Gutsy on it,


As for permissions, use the dmask and umask options.  For world access, use "-o fmask=0777,dmask=0777" on a command line mount, or "fmask=0000,dmask=0000" in your fstab.  dmount is for directories, fmask is for files, and umask can be used for both (I think).

For starters:

mark@Lexington-19:~$ man dmask
No manual entry for dmask

so, please tell me how to change the file permissions so that ME, the user named "mark' can write, read and delete files on this usb drive.

---

### Post by eternicode on 2007-12-22
:D

"dmask" is an option for the "mount" command, not a command itself.

Try

```
sudo mount -t ext2 -o fmask=0777,dmask=0777 /dev/sdc1 /media/disk
```

replace ext2 with the filesystem type (or leave it blank to have mount guess), /dev/sdc1 with the appropriate device, and /media/disk with the appropriate mount point.  For more info, read the results of "man mount"

---

### Post by Mark_in_Hollywood on 2007-12-22
mark@Lexington-19:/media/sdb1$ sudo mount -t ext3 -o fmask=0777,dmask=0777 /dev/sdc1 /media/disk
mount: special device /dev/sdc1 does not exist
mark@Lexington-19:/media/sdb1$ sudo mount -t ext3 -o fmask=0777,dmask=0777 /dev/sdb1 /media/disk
mount: /dev/sdb1 already mounted or /media/disk busy
mount: according to mtab, /dev/sdc is already mounted on /media/disk

It is labeled  /dev/sdb because I have a memory stick as sda. At least I think that's what it is.

---

### Post by eternicode on 2007-12-22
This line: 
> mount: according to mtab, /dev/sdc is already mounted on /media/disk
Indicates that you have a (partitionless...) drive somewhere called /dev/sdc (I'm assuming this is probably the drive you just reformatted, since sdc is mounted instead of sdc1).  I'm not sure how well a partitionless drive is supposed to work, but I would suggest repartitioning it so it has at least one partition.  GParted is a good tool to use for this.

Actually, if you're logged in as a user, and then you plug in (and automount) a USB drive, it should be under ownership of the logged-in user...which means you should already have read/write access to it.  But in any case...

OK, use ```
sudo fdisk -l
``` This will give you a listing of all drives connected to your system and their partitions.  Each drive's section will have a header of the format ```
Disk <device>: <size> GB, <size> bytes
```  Here's an example of mine:

```

Disk /dev/sda: 58.5 GB, 58506416640 bytes
255 heads, 63 sectors/track, 7113 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        3791    30411045    7  HPFS/NTFS
/dev/sda3            6682        7112     3462007+  db  CP/M / CTOS / ...
/dev/sda4            3792        6681    23213925    5  Extended
/dev/sda5            3792        4052     2096451    b  W95 FAT32
/dev/sda6            6421        6681     2096451   82  Linux swap / Solaris
/dev/sda7            4053        6420    19020928+  83  Linux

```

Once you know which drive/partition you want to access, make sure it's not mounted (the "mount" command by itself will show what filesystems are mounted and where).  If it's mounted, unmount it ("sudo umount <device>").  Then try the mount command, and make sure you're mounting it on a directory that is not already used as a mount point (again, the "mount" command by itself gives this info).  You may have to make a new directory in the "/media" directory (sudo mkdir /media/disk2 or something similar).

---

### Post by Mark_in_Hollywood on 2007-12-22
OK, I'm lost.

I have run GParted LiveCd and 'partitoned' /dev/sdb so that now there is: /dev/sdb1

I want the entire disk as storage drive.

I cannot read or write to or from this device. It is owned by 'root'.

Please see the attached screenshots.

What command line or modifying of fstab is required to make the owner of this disk the (one and only) user?

---

### Post by eternicode on 2007-12-22
I don't know how to change the ownership of the drive.  If it's USB, it should automatically be owned by the user who plugged it in.

Nonetheless, anytime you want to edit its files, you can unmount it and mount it with with world r/w privileges.

Assuming /dev/sdb1 is the drive and /media/disk is the moint point.

```

# Unmount the drive...
$ sudo umount /dev/sdb1

# Remount the drive with world read-write permissions
sudo mount -o dmask=0000,fmask=0000 /dev/sdb1 /media/disk

# Access the drive as desired

# Unmount the drive
sudo umount /dev/sdb1

# Eject the drive

```

Might also look into the pmount command.  I've never used it, but it's purpose is to allow users to mount removable media.

Good luck.

---

### Post by Mark_in_Hollywood on 2007-12-22
> **eternicode said:**
> I don't know how to change the ownership of the drive.  If it's USB, it should automatically be owned by the user who plugged it in.

Nonetheless, anytime you want to edit its files, you can unmount it and mount it with with world r/w privileges.

Assuming /dev/sdb1 is the drive and /media/disk is the moint point.

[code]
# Unmount the drive...
$ sudo umount /dev/sdb1

# Remount the drive with world read-write permissions
sudo mount -o dmask=0000,fmask=0000 /dev/sdb1 /media/disk

# Access the drive as desired

# Unmount the drive
sudo umount /dev/sdb1.

My results:

mark@Lexington-19:~$ sudo umount /dev/sdb1
mark@Lexington-19:~$ sudo mount -o dmask=0000,fmask=0000 /dev/sdb1 /media/disk
mount: mount point /media/disk does not exist


why?

---

