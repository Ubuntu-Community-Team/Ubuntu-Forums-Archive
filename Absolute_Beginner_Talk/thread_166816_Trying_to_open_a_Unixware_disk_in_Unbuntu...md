---
title: "Trying to open a Unixware disk in Unbuntu.."
date: 2006-04-27
forum: Absolute Beginner Talk
---

### Post by blaa on 2006-04-27
My mission is to be able to open some UnixWare 2.1 formatted MO disks, in unbuntu. I have gig's of data I need to be able to open up, to eventually convert to a windows format (boo hiss!).
         I can't seem to be able to get ubuntu to recognise the disk however.

It is a Sony SMO-F541, running on an Adaptec SCSI PCI card. The machine has an IDE hard disk (just so you know nothing else is on the SCSI).

I have been getting loads of help over on another forum, but unfortunately I have exhausted the resources. So although I am a newbie on Linux, I have had a little introduction into perhaps the info you might need?

```
sleep@standalone:~$ sudo hexdump -c /dev/sda4|head
0000000   "   "   "   "   "   "   "   "   "   "   "   "   "   "   "   "
*
0003a00  \0  \0  \0  \0  \r   `   ^ 312 004  \0  \0  \0
0003a10                                   H 004  \0  \0   @  \0  \0  \0
0003a20      \0  \0  \0  \0 002  \0  \0      \0  \0  \0  \0  \0  \0  \0
0003a30  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0
*
0003a50  \0  \0  \0  \0 234   :  \0  \0   < 001  \0  \0  \0   <  \0  \0
0003a60  \0  \b  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0
0003a70  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0
sleep@standalone:~$ sudo hexdump -C /dev/sda4|head -n 20
Password:
00000000  22 22 22 22 22 22 22 22  22 22 22 22 22 22 22 22  |""""""""""""""""|
*
00003a00  00 00 00 00 0d 60 5e ca  04 00 00 00 20 20 20 20  |.....`^.....    |
00003a10  20 20 20 20 20 20 20 20  48 04 00 00 40 00 00 00  |        H...@...|
00003a20  20 00 00 00 00 02 00 00  20 00 00 00 00 00 00 00  | ....... .......|
00003a30  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00003a50  00 00 00 00 9c 3a 00 00  3c 01 00 00 00 3c 00 00  |.....:..<....<..|
00003a60  00 08 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00003a70  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00003a90  00 00 00 00 00 00 00 00  00 00 00 00 ee de 0d 60  |...............`|
00003aa0  04 00 00 00 2f 64 65 76  2f 72 64 73 09 00 00 00  |..../dev/rds....|
00003ab0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00003ad0  00 00 00 00 00 00 00 00  05 00 01 02 20 00 00 00  |............ ...|
00003ae0  e0 3f 22 00 04 00 00 02  00 08 00 00 00 38 22 00  |.?"..........8".|
00003af0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00003b20  00 00 00 00 00 00 00 00  00 00 00 00 01 00 01 02  |................|
```


and

```
sleep@standalone:~$ sudo fdisk -l
Password:

Disk /dev/hdc: 20.4 GB, 20411080704 bytes
16 heads, 63 sectors/track, 39549 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1       12118     6107440+   7  HPFS/NTFS
/dev/hdc2           12119       39541    13821129+   f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/hdc5           12119       18350     3140896+   b  W95 FAT32
/dev/hdc6           18361       19285      465853+  82  Linux swap / Solaris
/dev/hdc7           21612       28401     3421813+  83  Linux
/dev/hdc8           28401       39541     5614686   83  Linux
/dev/hdc9           19285       21612     1172713+  83  Linux

Partition table entries are not in disk order

Disk /dev/sda: 1149 MB, 1149418496 bytes
64 heads, 32 sectors/track, 1096 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda4   *           1        1096     1122288   63  GNU HURD or SysV
sleep@standalone:~$ sfdisk -V /dev/sda
Warning: partition 4 extends past end of disk
```

and

```
cat /proc/filesytems:
nodev sysfs
nodev rootfs
nodev bdev
nodev proc
nodev sockfs
no dev pipefs
nodev futexfs
nodev tmpfs
nodev inotiyfs
nodev eventpollfs
nodev devpts
         ext2
         cramfs
nodev  ramfs
nodev devfs
nodev mqueue
nodev usbfs
         ext3
         sysv
         v7
         vfat
         ntfs
```

The chaps over at urban75 were saying that perhaps I need to install a new format (I think this is what they were saying...), and then I'd be able to read it...

Plz help! :P

---

### Post by mips on 2006-04-27
Unixware v7 is based on SVR5, earlier versions on SVR4.2.
File System supported:

* VxFS [Veritas File System - VxFS1, VxFS2 & VxFS4] and UFS File system.
Also seems to use BFS.

Looks like you need to use **Vxtools**

I hope this applies to MO disks as well.

[http://www.linux.com/howtos/Filesystems-HOWTO-9.shtml](http://www.linux.com/howtos/Filesystems-HOWTO-9.shtml)
[http://www.penguin.cz/~mhi/fs/vxfs/](http://www.penguin.cz/~mhi/fs/vxfs/)
[http://www.tldp.org/HOWTO/Filesystems-HOWTO-9.html](http://www.tldp.org/HOWTO/Filesystems-HOWTO-9.html)
[http://uw713doc.sco.com/en/FS_admin/CONTENTS.html](http://uw713doc.sco.com/en/FS_admin/CONTENTS.html)
[http://www.ibiblio.org/filesystems/howto/Filesystems-HOWTO.txt](http://www.ibiblio.org/filesystems/howto/Filesystems-HOWTO.txt)

---

