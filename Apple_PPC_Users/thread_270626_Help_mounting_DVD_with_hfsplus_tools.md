---
title: "Help mounting DVD with hfsplus tools"
date: 2006-10-03
forum: Apple PPC Users
---

### Post by brownsteve on 2006-10-03
Hi folks --

I am running Edgy on a SMP-686 Dell laptop, but I was hoping the fellow Mac-heads around here could help me out.  I had a HFS+ disk image I converted to ".CDR master" (iso) format with Disk Utility, then burned onto a DVD, and now I'd like to mount it on my edgy laptop to copy the files off.

Here's some things I've tried.  It looks like the image had blocks of size 512 bytes, but the Linux DVD driver defaults to 2048 bytes.  My main questions: 
1) Does anyone know how to force the linux kernel and hfsplus tools to use a sector size of 512 bytes?  Parted won't even print the partition table out as it stands.
2) Is hpmount even able to tackle disk images?  I thought this was just a plain old Mac partition table, then a HFS wrapper, then the HFS+ disk itself.  Is this really a disk-image-format volume I've burned and not a straight HFS+ disk?


Thanks so much for any insights.
Steve Brown


I have manually viewed the partition map with dd | xxd.  It seems to be valid but hpmount won't digest it for some reason, neither will parted:

root@lithium:~# hpmount -r /dev/scd0 /media/cdrom0
hpmount: /dev/scd0: Neither Wrapper nor native HFS+ volume header found (Unknown error 4294967295)
root@lithium:~# hpmount -r -p1 /dev/scd0 /media/cdrom0
hpmount: /dev/scd0: This is not a HFS+ volume (Unknown error 4294967295)
root@lithium:~# hpmount -r -p0 /dev/scd0 /media/cdrom0
hpmount: /dev/scd0: Neither Wrapper nor native HFS+ volume header found (Unknown error 4294967295)
root@lithium:~# hpmount -r -p2 /dev/scd0 /media/cdrom0
hpmount: /dev/scd0: No valid Apple_HFS partition found (Unknown error 4294967295)

root@lithium:~# parted /dev/scd0
Warning: Unable to open /dev/scd0 read-write (Read-only file system).  /dev/scd0 has been opened
read-only.
Warning: Device /dev/scd0 has a logical sector size of 2048.  Not all parts of GNU Parted support this
at the moment, and the working code is HIGHLY EXPERIMENTAL.

Warning: Unable to open /dev/scd0 read-write (Read-only file system).  /dev/scd0 has been opened
read-only.
GNU Parted 1.7.1
Using /dev/scd0
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print                                                            
Error: Unable to open /dev/scd0 - unrecognised disk label.   

Valid mac disk header:
root@lithium:~# dd if=/dev/scd0 bs=512 count=1 skip=0 | xxd
0000000: 4552 0200 008c 0e40 0000 0000 0000 0000  ER.....@........

Partition 0 (the map itself)
root@lithium:~# dd if=/dev/scd0 bs=512 count=1 skip=1 | xxd
0000000: 504d 0000 0000 0003 0000 0001 0000 003f  PM.............?
0000010: 4170 706c 6500 0000 0000 0000 0000 0000  Apple...........
0000020: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000030: 4170 706c 655f 7061 7274 6974 696f 6e5f  Apple_partition_
0000040: 6d61 7000 0000 0000 0000 0000 0000 0000  map.............
0000050: 0000 0000 0000 003f 0000 0003 0000 0000  .......?........

Partition 1 (the disk image)
root@lithium:~# dd if=/dev/scd0 bs=512 count=1 skip=2 | xxd
0000000: 504d 0000 0000 0003 0000 0040 008c 0df0  PM.........@....
0000010: 6469 736b 2069 6d61 6765 0000 0000 0000  disk image......
0000020: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000030: 4170 706c 655f 4846 5300 0000 0000 0000  Apple_HFS.......
0000040: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000050: 0000 0000 008c 0df0 4000 0033 0000 0000  ........@..3....

Partition 2 leadout; I've seen these Apple_free partitions on my disks often
root@lithium:~# dd if=/dev/scd0 bs=512 count=1 skip=3 | xxd
0000020: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000030: 4170 706c 655f 4672 6565 0000 0000 0000  Apple_Free......
0000040: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000050: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000060: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000070: 0000 0000 0000 0000 0000 0000 0000 0000  ................

Here's the HFS+ master directory block (I think)
root@lithium:~# dd if=/dev/scd0 bs=512 count=1 skip=66| xxd
0000000: 482b 0004 0000 2100 4846 534a 0000 0801  H+....!.HFSJ....
0000010: c113 a4f5 c114 1845 0000 0000 c113 f955  .......E.......U
0000020: 0000 909c 0000 164e 0000 1000 0011 81be  .......N........
0000030: 0001 34ac 0003 c2ef 0001 0000 0001 0000  ..4.............
0000040: 0000 a7a0 0000 bc99 0000 0000 0000 0001  ................

---

