---
title: "mbr bootbug 222126 supporting data"
date: 2008-11-13
forum: Apple Hardware Users
---

### Post by pxwpxw on 2008-11-13
You dont want to read this, and don't try it.

this is a copy of my attachment to 
[https://bugs.edge.launchpad.net/ubuntu/+source/ubiquity/+bug/222126/](https://bugs.edge.launchpad.net/ubuntu/+source/ubiquity/+bug/222126/)
some destructive tests on intel mac MBR partiton data. 
Here for any discussion arising.

```

MacBook2.1 80GB HD. Ubunu 704 and 810 parted comparison.
Fri Nov 14 01:42:47 EST 2008

1. The sda sector0  and MBR was wiped to 00*55aa (msdos MBR disk signature).
MBR=4x16byte partition entries above 446 bytes.

# dd if=/dev/zero of=/dev/sda bs=510 count=1
# hexdump -Cn512 /dev/sda
00000000  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Then using 704 live cd 
#  parted /dev/sda toggle 1 boot 
done twice, no net no effect on gpt flag, but causing write to the disk MBR. 

2. The MBR as parted on 704 left it.

00000000  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 fe  |................|
000001c0  ff ff ee fe ff ff 01 00  00 00 27 40 06 00 80 fe  |..........'@....|
000001d0  ff ff af fe ff ff 28 40  06 00 30 a1 7e 02 00 fe  |......(@..0.~...|
000001e0  ff ff af fe ff ff 58 e1  88 02 08 20 ae 00 00 fe  |......X.... ....|
000001f0  ff ff 83 fe ff ff 60 01  37 03 de 0e e9 02 55 aa  |......`.7.....U.|
00000200

root@wdc:/home/pxw# gptsync /dev/sda

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640     42262871  Mac OS X HFS+
 3       42525016     53936479  Mac OS X HFS+
 4       53936480    102764605  Basic Data
 5      102764606    106670856  Linux Swap
(free space remaining)
Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2 *       409640     42262871  af  Mac OS X HFS+
 3       42525016     53936479  af  Mac OS X HFS+
 4       53936480    102764605  83  Linux

Status: Tables are synchronized, no need to sync.

root@wdc:/home/pxw# 

 Can boot using MBR without gptsync (boot sector code below MBR appeared later).
=====================

2. Wipe the MBR again to check 810 parted (from xububtu810 on external disk)

root@wdc:/home/pxw# dd if=/dev/zero of=/dev/sda bs=510 count=1
1+0 records in
1+0 records out
510 bytes (510 B) copied, 0.000584095 s, 873 kB/s
root@wdc:/home/pxw# hexdump -Cn512 /dev/sda
00000000  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

root@wdc:/home/pxw# gptsync /dev/sda

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640     42262871  Mac OS X HFS+
 3       42525016     53936479  Mac OS X HFS+
 4       53936480    102764605  Basic Data
 5      102764606    106670856  Linux Swap

Current MBR partition table:
 No partitions defined

Status: MBR table must be updated.

Proposed new MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640     42262871  af  Mac OS X HFS+
 3       42525016     53936479  af  Mac OS X HFS+
 4 *     53936480    102764605  83  Linux

May I update the MBR as printed above? [y/N] n
No

//just checking its valid for gptsync, but leaved empty.

root@wdc:/home/pxw# parted

toggle 1

//810 parted complained, but offered choice of gpt disk, and then allowed the toggle operaation.
Flag to Invert?  boot/hidden/raid/lvm/hp-service/msftres/bios_grub? boot  

Information: You may need to update /etc/fstab.                           

root@wdc:/home/pxw# parted /dev/sda p

Model: ATA TOSHIBA MK8034GS (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                  Flags  
 1      20.5kB  210MB   210MB   fat32        EFI System Partition  msftres
 2      210MB   21.6GB  21.4GB  hfs+         Apple_HFS_Untitled_1         
 3      21.8GB  27.6GB  5843MB  hfs+         Apple_HFS_Untitled_2         
 4      27.6GB  52.6GB  25.0GB  ext3         root1                        
 5      52.6GB  54.6GB  2000MB  linux-swap                                

toggle back to boot on

root@wdc:/home/pxw# parted /dev/sda toggle 1 boot p
Model: ATA TOSHIBA MK8034GS (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                  Flags
 1      20.5kB  210MB   210MB   fat32        EFI System Partition  boot 
 2      210MB   21.6GB  21.4GB  hfs+         Apple_HFS_Untitled_1       
 3      21.8GB  27.6GB  5843MB  hfs+         Apple_HFS_Untitled_2       
 4      27.6GB  52.6GB  25.0GB  ext3         root1                      
 5      52.6GB  54.6GB  2000MB  linux-swap                              

Information: You may need to update /etc/fstab.                           

root@wdc:/home/pxw#
//that has reset the sector0 mbr to one partition, full disk size, valid for gptsync. 

root@wdc:/home/pxw# hexdump -Cn512 /dev/sda
00000000  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001c0  01 00 ee fe ff ff 01 00  00 00 af f8 50 09 00 00  |............P...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
root@wdc:/home/pxw# 


root@wdc:/home/pxw# gptsync /dev/sda

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640     42262871  Mac OS X HFS+
 3       42525016     53936479  Mac OS X HFS+
 4       53936480    102764605  Basic Data
 5      102764606    106670856  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1    156301487  ee  EFI Protective

Status: MBR table must be updated.

Proposed new MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640     42262871  af  Mac OS X HFS+
 3       42525016     53936479  af  Mac OS X HFS+
 4 *     53936480    102764605  83  Linux

May I update the MBR as printed above? [y/N] y
Yes

Writing new MBR...
MBR updated successfully!

root@wdc:/home/pxw# 
root@wdc:/home/pxw# hexdump -Cn512 /dev/sda

00000000  fa 31 c0 8e d8 8e d0 bc  00 7c 89 e6 06 57 52 8e  |.1.......|...WR.|
00000010  c0 fb fc bf 00 06 b9 00  01 f3 a5 ea 20 06 00 00  |............ ...|
00000020  52 b8 00 41 bb aa 55 31  c9 30 f6 f9 cd 13 72 13  |R..A..U1.0....r.|
00000030  81 fb 55 aa 75 0d d1 e9  73 09 66 c7 06 8f 06 b4  |..U.u...s.f.....|
00000040  42 eb 15 5a b4 08 cd 13  83 e1 3f 51 0f b6 c6 40  |B..Z......?Q...@|
00000050  f7 e1 52 50 66 31 c0 66  99 e8 67 00 e8 24 01 4d  |..RPf1.f..g..$.M|
00000060  69 73 73 69 6e 67 20 6f  70 65 72 61 74 69 6e 67  |issing operating|
00000070  20 73 79 73 74 65 6d 2e  0d 0a 00 66 60 66 31 d2  | system....f`f1.|
00000080  bb 00 7c 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..|fRfP.Sj.j...f|
00000090  f7 36 f4 7b c0 e4 06 88  e1 88 c5 92 f6 36 f8 7b  |.6.{.........6.{|
000000a0  88 c6 08 e1 41 b8 01 02  8a 16 fa 7b cd 13 83 c4  |....A......{....|
000000b0  10 66 61 c3 e8 c4 ff be  be 7d bf be 07 b9 20 00  |.fa......}.... .|
000000c0  f3 a5 c3 66 60 89 e5 bb  be 07 b9 04 00 31 c0 53  |...f`........1.S|
000000d0  51 f6 07 80 74 03 40 89  de 83 c3 10 e2 f3 48 74  |Q...t.@.......Ht|
000000e0  5c 79 39 59 5b 8a 47 04  3c 0f 74 06 24 7f 3c 05  |\y9Y[.G.<.t.$.<.|
000000f0  75 22 66 8b 47 08 66 8b  56 14 66 01 d0 66 21 d2  |u"f.G.f.V.f..f!.|
00000100  75 03 66 89 c2 e8 ac ff  72 03 e8 b6 ff 66 8b 46  |u.f.....r....f.F|
00000110  1c e8 a0 ff 83 c3 10 e2  cc 66 61 c3 e8 64 00 4d  |.........fa..d.M|
00000120  75 6c 74 69 70 6c 65 20  61 63 74 69 76 65 20 70  |ultiple active p|
00000130  61 72 74 69 74 69 6f 6e  73 2e 0d 0a 00 66 8b 44  |artitions....f.D|
00000140  08 66 03 46 1c 66 89 44  08 e8 2f ff 72 13 81 3e  |.f.F.f.D../.r..>|
00000150  fe 7d 55 aa 0f 85 04 ff  bc fa 7b 5a 5f 07 fa ff  |.}U.......{Z_...|
00000160  e4 e8 1f 00 4f 70 65 72  61 74 69 6e 67 20 73 79  |....Operating sy|
00000170  73 74 65 6d 20 6c 6f 61  64 20 65 72 72 6f 72 2e  |stem load error.|
00000180  0d 0a 00 5e ac 20 c0 74  0c b4 0e 8a 3e 62 04 b3  |...^. .t....>b..|
00000190  07 cd 10 eb ef cd 18 f4  eb fd 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 fe  |................|
000001c0  ff ff ee fe ff ff 01 00  00 00 27 40 06 00 00 fe  |..........'@....|
000001d0  ff ff af fe ff ff 28 40  06 00 30 a1 7e 02 00 fe  |......(@..0.~...|
000001e0  ff ff af fe ff ff 58 e1  88 02 08 20 ae 00 80 fe  |......X.... ....|
000001f0  ff ff 83 fe ff ff 60 01  37 03 de 0e e9 02 55 aa  |......`.7.....U.|
00000200
======

The MBR boot flag at 0x1ee on partition #4 is not shown by parted; appears irrelevant here.

root@wdc:/home/pxw# parted /dev/sda p free
Model: ATA TOSHIBA MK8034GS (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                  Flags
        17.4kB  20.5kB  3072B   Free Space                              
 1      20.5kB  210MB   210MB   fat32        EFI System Partition  boot 
 2      210MB   21.6GB  21.4GB  hfs+         Apple_HFS_Untitled_1       
        21.6GB  21.8GB  134MB   Free Space                              
 3      21.8GB  27.6GB  5843MB  hfs+         Apple_HFS_Untitled_2       
 4      27.6GB  52.6GB  25.0GB  ext3         root1                      
 5      52.6GB  54.6GB  2000MB  linux-swap                              
        54.6GB  80.0GB  25.4GB  Free Space                              


gptsync now reports " Status: Tables are synchronized, no need to sync."

Ready to boot MBR loaders.
=======




```

---

### Post by cyberdork33 on 2008-11-13
thanks for the help man. That has been a long-standing bug,

---

### Post by pxwpxw on 2008-11-14
Here is part 2 -

Two more tests were done to reproduce the flashing [?] folder, with the unbootable  hard disk. 

On a MacBook2,1 the only other way I could reproduce it was by using fdisk and (ignoring warnings) to delete the single full disk partition it shows for the gpt default entry. This zeroed the MBR. I dont think it is a parted bug. 
I have rechecked all this, but it has all been done on a MacBook2,1. I dont know if there are any different issues for other macs e.g. with drive differences. 

Warning -
Do not do this test unless you understand the risk and can recover.

1. I zeroed out the whole first sector of the disk with dd to give this hexdump

```

root@wdc:~/devsda-zap00# hexdump -Cn512 /dev/sda

00000000  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000200

```

Restart goes to  [?] flash folder after ~30 seconds, and nothing will boot from the HD.

Then checked with gptsync running from the refit CD (which still boots).

```

root@wdc:~/zapdevsda-00# gptsync /dev/sda

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640     42262871  Mac OS X HFS+
 3       42525016     53936479  Mac OS X HFS+
 4       53936480    102764605  Basic Data
 5      102764606    106670856  Linux Swap

Current MBR partition table:
 No MBR partition table present!


```

So the GPT table above the first sector is ok, but gptsynce is no help here.
But it can easily be fixed, read on.

2.  restore the 55aa msdos signature bytes 511, 512.
(note 1).

```

root@wdc:~/zapdevsda-00# hexdump -Cn512 /dev/sda 
00000000  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

This gets the same [?] folder, nothing boots, but gptsync from the CD now recognises MBR present, and can sync, restoring full MBR and all fixed
.
```

root@wdc:~/zapdevsda-00# gptsync /dev/sda

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640     42262871  Mac OS X HFS+
 3       42525016     53936479  Mac OS X HFS+
 4       53936480    102764605  Basic Data
 5      102764606    106670856  Linux Swap

Current MBR partition table:
 No partitions defined

Status: MBR table must be updated.

Proposed new MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640     42262871  af  Mac OS X HFS+
 3       42525016     53936479  af  Mac OS X HFS+
 4 *     53936480    102764605  83  Linux

May I update the MBR as printed above? [y/N] y
Yes

Writing new MBR...
MBR updated successfully!

```
(hexdump note2)

All fixed if you have grub on another partition, not the MBR.

3. [COLOR="Red"]HAZARDOUS[/COLOR] - I also found that ubuntu 810 parted can be made to regenerate a valid gpt sector1 (ie.e bootable and acceptable to gptsync) ) by toggling the partition 1 boot flag off and on. Parted complains at first and has to be told that it has a GPT table.** If you make a mistake here and tell it that it is an MBR disk it can convert to msdos partitioning and lose everything.**
   
------------------
Note 1. restoring the hex 55aa.  (echo uses octal).

```

$ dd if=/dev/zero of=testsector bs=512 count=1
$ echo -en "\0125\0252" > hex55aa && dd if=hex55aa of=testsector seek=1 bs=510
pxw@g5:~/test$ hexdump -C testsector 
00000000  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

Note 2. restored MBR and bootcode
 MacBook2,1 80GB GPT/MBR disk.
```

root@wdc:~/zapdevsda-00# hexdump -Cn512 /dev/sda 
00000000  fa 31 c0 8e d8 8e d0 bc  00 7c 89 e6 06 57 52 8e  |.1.......|...WR.|
00000010  c0 fb fc bf 00 06 b9 00  01 f3 a5 ea 20 06 00 00  |............ ...|
00000020  52 b8 00 41 bb aa 55 31  c9 30 f6 f9 cd 13 72 13  |R..A..U1.0....r.|
00000030  81 fb 55 aa 75 0d d1 e9  73 09 66 c7 06 8f 06 b4  |..U.u...s.f.....|
00000040  42 eb 15 5a b4 08 cd 13  83 e1 3f 51 0f b6 c6 40  |B..Z......?Q...@|
00000050  f7 e1 52 50 66 31 c0 66  99 e8 67 00 e8 24 01 4d  |..RPf1.f..g..$.M|
00000060  69 73 73 69 6e 67 20 6f  70 65 72 61 74 69 6e 67  |issing operating|
00000070  20 73 79 73 74 65 6d 2e  0d 0a 00 66 60 66 31 d2  | system....f`f1.|
00000080  bb 00 7c 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..|fRfP.Sj.j...f|
00000090  f7 36 f4 7b c0 e4 06 88  e1 88 c5 92 f6 36 f8 7b  |.6.{.........6.{|
000000a0  88 c6 08 e1 41 b8 01 02  8a 16 fa 7b cd 13 83 c4  |....A......{....|
000000b0  10 66 61 c3 e8 c4 ff be  be 7d bf be 07 b9 20 00  |.fa......}.... .|
000000c0  f3 a5 c3 66 60 89 e5 bb  be 07 b9 04 00 31 c0 53  |...f`........1.S|
000000d0  51 f6 07 80 74 03 40 89  de 83 c3 10 e2 f3 48 74  |Q...t.@.......Ht|
000000e0  5c 79 39 59 5b 8a 47 04  3c 0f 74 06 24 7f 3c 05  |\y9Y[.G.<.t.$.<.|
000000f0  75 22 66 8b 47 08 66 8b  56 14 66 01 d0 66 21 d2  |u"f.G.f.V.f..f!.|
00000100  75 03 66 89 c2 e8 ac ff  72 03 e8 b6 ff 66 8b 46  |u.f.....r....f.F|
00000110  1c e8 a0 ff 83 c3 10 e2  cc 66 61 c3 e8 64 00 4d  |.........fa..d.M|
00000120  75 6c 74 69 70 6c 65 20  61 63 74 69 76 65 20 70  |ultiple active p|
00000130  61 72 74 69 74 69 6f 6e  73 2e 0d 0a 00 66 8b 44  |artitions....f.D|
00000140  08 66 03 46 1c 66 89 44  08 e8 2f ff 72 13 81 3e  |.f.F.f.D../.r..>|
00000150  fe 7d 55 aa 0f 85 04 ff  bc fa 7b 5a 5f 07 fa ff  |.}U.......{Z_...|
00000160  e4 e8 1f 00 4f 70 65 72  61 74 69 6e 67 20 73 79  |....Operating sy|
00000170  73 74 65 6d 20 6c 6f 61  64 20 65 72 72 6f 72 2e  |stem load error.|
00000180  0d 0a 00 5e ac 20 c0 74  0c b4 0e 8a 3e 62 04 b3  |...^. .t....>b..|
00000190  07 cd 10 eb ef cd 18 f4  eb fd 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 fe  |................|
000001c0  ff ff ee fe ff ff 01 00  00 00 27 40 06 00 00 fe  |..........'@....|
000001d0  ff ff af fe ff ff 28 40  06 00 30 a1 7e 02 00 fe  |......(@..0.~...|
000001e0  ff ff af fe ff ff 58 e1  88 02 08 20 ae 00 80 fe  |......X.... ....|
000001f0  ff ff 83 fe ff ff 60 01  37 03 de 0e e9 02 55 aa  |......`.7.....U.|
00000200

```
=============

---

### Post by cyberdork33 on 2008-11-16
I can confirm this indirectly. I was attempting to clear the bootloader data from the MBR awhile back and this caused the flashing question mark. I had to restore my MBR backup to have it bootable again.

---

### Post by pxwpxw on 2008-11-22
More -
MBR bootable, partitions OK.
Open gparted, EFI partition, manage flags, tick boot off, decide not to, tick boot back on.
Exit without applying anything "no changes" nothing to apply.
Result -
MBR is bombed back to GPT version, no MBR boot.
====

---

### Post by cyberdork33 on 2009-03-28
Progress!
[https://bugs.edge.launchpad.net/mactel-support/+bug/222126](https://bugs.edge.launchpad.net/mactel-support/+bug/222126)

---

