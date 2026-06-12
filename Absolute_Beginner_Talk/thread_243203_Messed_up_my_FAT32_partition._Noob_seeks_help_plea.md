---
title: "Messed up my FAT32 partition. Noob seeks help please."
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by stoer on 2006-08-24
[FONT="Comic Sans MS"][COLOR="Red"][SIZE="6"]PROBLEM SOLVED[/SIZE][/COLOR][/FONT]

Hi all.
6 weeks in and still in love with Ubuntu, still finding my way and trying not to kill my system!

Here's my problem, any help will be much appreciated.

After installing Ubuntu i followed the “how to” on mounting windows partitions at
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

I made a directory for windows;   /windows
and also one for my fat32 partition;    /fat_files

All went well, everything worked fine.  I could read and write files from and to the fat32 partition.

A couple of days ago, looking at my system in windows xp pro using patition magic 8 i noticed a problem with one partition “unknown start point (???)” Partition magic refused to work past reporting this, so i tried with Acronis disk suite, which showed some unallocated space lying between my windows partition and the Linux partition, but further no problems... Aaccording to the Acronis partitioner the space could be used by windows but not without difficulty by my Linux partition.
The unallocated free space, approx 450mb was sitting doing nothing.   I added the unallocated space to the windows partition.   But, now my fat32 file settings seem to be screwed, i can still read the fat32 map but only content that was added after the reallocation of space.  All the other stuff is still there but now only accessable in windows.

I think that i've "pooched" my "mount link" (???) through carrying out the above.

fdisk -l gives me the following:

steve@laptop:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2203    17695566    7  HPFS/NTFS
/dev/hda2            4331        9733    43399597+   f  W95 Ext'd (LBA)
/dev/hda3            2204        4330    17085127+  83  Linux
/dev/hda5            4426        8369    31680146    7  HPFS/NTFS
/dev/hda6            4331        4425      763024+  82  Linux swap / Solaris
/dev/hda7            8370        9733    10956298+   b  W95 FAT32

Partition table entries are not in disk order

and the /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /windows                ntfs    nls=utf8,umask=0222     0      $
/dev/hda6       /fat_files      vfat    iocharset=utf8,umask=000  0     0
/dev/hda5       /win_data_disk  ntfs    nls=utf8,umask=0222     0       0
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

unmount and mount don't seem to help me in this case either.
steve@laptop:~$ sudo mount /dev/hda6
mount: wrong fs type, bad option, bad superblock on /dev/hda6,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

dmesg | tail =

steve@laptop:~$ dmesg | tail
[17179610.828000] Bluetooth: L2CAP socket layer initialized
[17179610.852000] Bluetooth: RFCOMM socket layer initialized
[17179610.852000] Bluetooth: RFCOMM TTY layer initialized
[17179610.852000] Bluetooth: RFCOMM ver 1.7
[17179751.920000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17179752.012000] FAT: bogus number of reserved sectors
[17179752.012000] VFS: Can't find a valid FAT filesystem on dev hda6.
[17182093.828000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17182093.844000] FAT: bogus number of reserved sectors
[17182093.844000] VFS: Can't find a valid FAT filesystem on dev hda6.
steve@laptop:~$ 


Any help or ideas please.
Cheers Steve.

---

### Post by Iarwain ben-adar on 2006-08-24
Hi,
to unmount and mount, you have to use the correct device path (not dev/hda6!)

Try these
```
sudo mount /dev/hda2
OR
sudo mount /dev/hda7
```

/dev/hda6 is your swap (see the output of fdisk -l)


Iarwain

---

### Post by stoer on 2006-08-25
](*,) 
](*,) 
](*,) 
](*,) 
Must have been way too tired yesterday, couldn't see the wood for the trees!!!
](*,) 
](*,) 
](*,) 

Staring me in the face hda6 and 7 needed altering in /etc/fstab

changed it to read;
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /windows                ntfs    nls=utf8,umask=0222     0      $
/dev/[COLOR="Red"]hda7[/COLOR]       /fat_files      vfat    iocharset=utf8,umask=000  0     0
/dev/hda5       /win_data_disk  ntfs    nls=utf8,umask=0222     0       0
/dev/[COLOR="Red"]hda6[/COLOR]       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

And now works fine of course!
Sorry for this. I'll try and sleep on a problem next time ](*,) 

[FONT="Comic Sans MS"][SIZE="7"][COLOR="Red"]
PROBLEM SOLVED[/COLOR][/SIZE][/FONT]

---

