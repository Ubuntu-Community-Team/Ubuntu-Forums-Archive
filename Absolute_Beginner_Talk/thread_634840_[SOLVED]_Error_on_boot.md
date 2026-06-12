---
title: "[SOLVED] Error on boot"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by hogwartsnigel on 2007-12-08
Hi all after the 3rd attempt at dual booting with Sabayon my boot returns a minor error. The command line enables me to "exit" and the boot continues fine to logon screen, all loads no problem from then.

Here is the log file saved by the system reporting the error stored ay var/log/fsck/chekfs

[COLOR="Blue"][I]Log of fsck -C -R -A -a 
Sat Dec  8 21:26:42 2007

fsck 1.40.2 (12-Jul-2007)
/dev/hda3: clean, 1881/34193408 files, 1149841/68376656 blocks
/dev/hdb1: clean, 13/30654464 files, 1009877/61277926 blocks
fsck.ext3: Unable to resolve 'UUID=12a94fa5-4bed-4644-9a78-8beb86b8b483'

fsck.ext3: Unable to resolve 'UUID=4a1af1bd-c1ff-4ae4-bbd1-9545badd8e09'

fsck died with exit status 8

anyone that can help as it is a little annoying.

Thanks

Nigel


Sat Dec  8 21:26:43 2007[/I][/COLOR]

---

### Post by PmDematagoda on 2007-12-08
Post the results of:-

```
cat /etc/mtab
```

and

```
sudo fdisk -l
```

---

### Post by hogwartsnigel on 2007-12-08
[I]nigel@nigel-ubuntu:~$ Log of fsck -C -R -A -a 
bash: Log: command not found
nigel@nigel-ubuntu:~$ Sat Dec  8 21:26:42 2007
bash: Sat: command not found
nigel@nigel-ubuntu:~$ 
nigel@nigel-ubuntu:~$ fsck 1.40.2 (12-Jul-2007)
bash: syntax error near unexpected token `('
nigel@nigel-ubuntu:~$ /dev/hda3: clean, 1881/34193408 files, 1149841/68376656 blocks
bash: /dev/hda3:: No such file or directory
nigel@nigel-ubuntu:~$ /dev/hdb1: clean, 13/30654464 files, 1009877/61277926 blocks
bash: /dev/hdb1:: No such file or directory
nigel@nigel-ubuntu:~$ fsck.ext3: Unable to resolve 'UUID=12a94fa5-4bed-4644-9a78-8beb86b8b483'
bash: fsck.ext3:: command not found
nigel@nigel-ubuntu:~$ 
nigel@nigel-ubuntu:~$ fsck.ext3: Unable to resolve 'UUID=4a1af1bd-c1ff-4ae4-bbd1-9545badd8e09'
bash: fsck.ext3:: command not found
nigel@nigel-ubuntu:~$ 
nigel@nigel-ubuntu:~$ fsck died with exit status 8
fsck 1.40.2 (12-Jul-2007)
Usage: fsck.ext3 [-panyrcdfvstDFSV] [-b superblock] [-B blocksize]
                [-I inode_buffer_blocks] [-P process_inode_size]
                [-l|-L bad_blocks_file] [-C fd] [-j external_journal]
                [-E extended-options] device

Emergency help:
 -p                   Automatic repair (no questions)
 -n                   Make no changes to the filesystem
 -y                   Assume "yes" to all questions
 -c                   Check for bad blocks and add them to the badblock list
 -f                   Force checking even if filesystem is marked clean
 -v                   Be verbose
 -b superblock        Use alternative superblock
 -B blocksize         Force blocksize when looking for superblock
 -j external_journal  Set location of the external journal
 -l bad_blocks_file   Add to badblocks list
 -L bad_blocks_file   Set badblocks list
nigel@nigel-ubuntu:~$ 
nigel@nigel-ubuntu:~$ Sat Dec  8 21:26:43 2007
[/I]




fdisk=
[I]Disk /dev/hda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1695d55b

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3647    29294496   83  Linux
/dev/hda2            3648        4863     9767520   82  Linux swap / Solaris
/dev/hda3            4864       38913   273506625   83  Linux

Disk /dev/hdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01206277

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       30515   245111706   83  Linux

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00006a32

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+  83  Linux
/dev/sda2            3825        5099    10241437+  82  Linux swap / Solaris
/dev/sda3            5100       14593    76260555   83  Linux

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0bc4063e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14593   117218241    f  W95 Ext'd (LBA)
/dev/sdb5               2       14593   117210208+   7  HPFS/NTFS

Disk /dev/sdc: 4126 MB, 4126670848 bytes
16 heads, 32 sectors/track, 15742 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0xc8ff0faf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       15742     4029936    c  W95 FAT32 (LBA)
nigel@nigel-ubuntu:~$ 
/I]

---

### Post by PmDematagoda on 2007-12-08
No:-

```
cat /etc/fstab

```?

---

### Post by hogwartsnigel on 2007-12-08
Thanks Here it is:

[COLOR="Navy"][I]nigel@nigel-ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=f22487e8-90b2-4035-89cf-662431cc0487 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda3
UUID=a99bc51e-28e6-49bf-a91a-2a7fdeb04186 /home           ext3    defaults        0       2
# /dev/hdb1
UUID=a569b390-488d-473b-af8e-5da63fc76e42 /media/hdb1     ext3    defaults        0       2
# /dev/sda1
UUID=12a94fa5-4bed-4644-9a78-8beb86b8b483 /media/sda1     ext3    defaults        0       2
# /dev/sda3
UUID=4a1af1bd-c1ff-4ae4-bbd1-9545badd8e09 /media/sda3     ext3    defaults        0       2
# /dev/sdb5
UUID=9094CD9394CD7C6A /media/sdb5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda2
UUID=26bbde29-76e3-48a8-9560-50f4822aa6c3 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
nigel@nigel-ubuntu:~$ [/I][/COLOR]

---

### Post by PmDematagoda on 2007-12-08
Well, here are the lines causing the problems:-

```
# /dev/sda1
UUID=12a94fa5-4bed-4644-9a78-8beb86b8b483 /media/sda1 ext3 defaults 0 2

# /dev/sda3
UUID=4a1af1bd-c1ff-4ae4-bbd1-9545badd8e09 /media/sda3 ext3 defaults 0 2
```


Try this:-
1) Open up the fstab file for editing.

2) Edit it to this:-

```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/hda1
UUID=f22487e8-90b2-4035-89cf-662431cc0487 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda3
UUID=a99bc51e-28e6-49bf-a91a-2a7fdeb04186 /home ext3 defaults 0 2
# /dev/hdb1
UUID=a569b390-488d-473b-af8e-5da63fc76e42 /media/hdb1 ext3 defaults 0 2

[B][COLOR="Red"]/dev/sda1 /media/sda1 ext3 defaults 0 2

/dev/sda3 /media/sda3 ext3 defaults 0 2[/COLOR][/B]

# /dev/sdb5
UUID=9094CD9394CD7C6A /media/sdb5 ntfs defaults,umask=007,gid=46 0 1
# /dev/hda2
UUID=26bbde29-76e3-48a8-9560-50f4822aa6c3 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto,exec 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec 0 0
```

Save the file and try and see if the problem is solved.

---

### Post by hogwartsnigel on 2007-12-08
Thank you most sincerly, all is well in the world loads perfectly....may I ask what it was we just did, was it as I think a remount of the drives conerned?

Also if I may trouble you for more info, I have an install of Sabayon on the sda drive, and these problems arose after its install. I don't need Sbayon was just trying it, but how would I avoid it doing whatever it did to the disc ( a seperate physical drive Ubuntu is installed on?
On partitioning on install I noticed it wrongly identified ubuntu as being on the 4th partion on hd0 when it is actually on the first partition.

Thank you though for your time and patience.

Nigel

---

### Post by PmDematagoda on 2007-12-08
Thanks, I was glad to help:).

Concerning the problem, it could have been that the UUID was inaccurate after Sabayon was installed since it must have made minute changes which still were enough to cause the problem.

If you want to avoid that problem, then I believe you should provide a direct path to the drive or partition in question which would be more reliable than an ID, this is what we did partly.

---

### Post by hogwartsnigel on 2007-12-08
Thanks again, if ever your in Oz..
Blessings to you

---

### Post by PmDematagoda on 2007-12-08
> **hogwartsnigel said:**
> Thanks again, if ever your in Oz..
Blessings to you

Oh, you use OzOS? Interesting:).

And the same to you, happy holidays:).

---

