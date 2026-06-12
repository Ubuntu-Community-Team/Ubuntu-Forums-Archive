---
title: "Blinking cursor on black screen"
date: 2010-12-17
forum: Apple Hardware Users
---

### Post by rpglover64 on 2010-12-17
I ran an install of Ubuntu 10.10 on /dev/sda4 of my machine.  The install succeeded.  Unfortunately, when I try to boot Ubuntu (either by holding down option or by selecting it with rEFIt) all I get is a blinking cursor in the upper left corner of a black screen.

My OSX partition boots fine.

Here is output of some commands I have read requested:

```
alex@yabloko:~ $ diskutil list
/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *320.1 GB   disk0
   1:                        EFI                         209.7 MB   disk0s1
   2:                  Apple_HFS Macintosh HD            41.9 GB    disk0s2
   3:                  Apple_HFS Windows                 100.0 GB   disk0s3
   4:       Microsoft Basic Data                         20.1 GB    disk0s4
   5:                  Apple_HFS Home                    157.4 GB   disk0s5

```
```

alex@yabloko:~ $ sudo hexdump -Cn512 /dev/disk0
Password:
00000000  eb 63 90 d0 bc 00 7c 8e  c0 8e d8 be 00 7c bf 00  |.c....|......|..|
00000010  06 b9 00 02 fc f3 a4 50  68 1c 06 cb fb b9 04 00  |.......Ph.......|
00000020  bd be 07 80 7e 00 00 7c  0b 0f 85 0e 01 83 c5 10  |....~..|........|
00000030  e2 f1 cd 18 88 56 00 55  c6 46 11 05 c6 46 10 00  |.....V.U.F...F..|
00000040  b4 41 bb aa 55 cd 13 5d  72 0f 81 fb 55 aa 75 09  |.A..U..]r...U.u.|
00000050  f7 c1 01 00 74 03 fe 46  10 66 00 80 d6 f0 96 10  |....t..F.f......|
00000060  00 00 00 00 ff fa 90 90  f6 c2 80 75 02 b2 80 ea  |...........u....|
00000070  74 7c 00 00 31 c0 8e d8  8e d0 bc 00 20 fb a0 64  |t|..1....... ..d|
00000080  7c 3c ff 74 02 88 c2 52  bb 17 04 80 27 03 74 06  ||<.t...R....'.t.|
00000090  be 88 7d e8 1c 01 be 05  7c f6 c2 80 74 48 b4 41  |..}.....|...tH.A|
000000a0  bb aa 55 cd 13 5a 52 72  3d 81 fb 55 aa 75 37 83  |..U..ZRr=..U.u7.|
000000b0  e1 01 74 32 31 c0 89 44  04 40 88 44 ff 89 44 02  |..t21..D.@.D..D.|
000000c0  c7 04 10 00 66 8b 1e 5c  7c 66 89 5c 08 66 8b 1e  |....f..\|f.\.f..|
000000d0  60 7c 66 89 5c 0c c7 44  06 00 70 b4 42 cd 13 72  |`|f.\..D..p.B..r|
000000e0  05 bb 00 70 eb 76 b4 08  cd 13 73 0d f6 c2 80 0f  |...p.v....s.....|
000000f0  84 d0 00 be 93 7d e9 82  00 66 0f b6 c6 88 64 ff  |.....}...f....d.|
00000100  40 66 89 44 04 0f b6 d1  c1 e2 02 88 e8 88 f4 40  |@f.D...........@|
00000110  89 44 08 0f b6 c2 c0 e8  02 66 89 04 66 a1 60 7c  |.D.......f..f.`||
00000120  66 09 c0 75 4e 66 a1 5c  7c 66 31 d2 66 f7 34 88  |f..uNf.\|f1.f.4.|
00000130  d1 31 d2 66 f7 74 04 3b  44 08 7d 37 fe c1 88 c5  |.1.f.t.;D.}7....|
00000140  30 c0 c1 e8 02 08 c1 88  d0 5a 88 c6 bb 00 70 8e  |0........Z....p.|
00000150  c3 31 db b8 01 02 cd 13  72 1e 8c c3 60 1e b9 00  |.1......r...`...|
00000160  01 8e db 31 f6 bf 00 80  8e c6 fc f3 a5 1f 61 ff  |...1..........a.|
00000170  26 5a 7c be 8e 7d eb 03  be 9d 7d e8 34 00 be a2  |&Z|..}....}.4...|
00000180  7d e8 2e 00 cd 18 eb fe  47 52 55 42 20 00 47 65  |}.......GRUB .Ge|
00000190  6f 6d 00 48 61 72 64 20  44 69 73 6b 00 52 65 61  |om.Hard Disk.Rea|
000001a0  64 00 20 45 72 72 6f 72  0d 0a 00 bb 01 00 b4 0e  |d. Error........|
000001b0  cd 10 ac 3c 00 75 f4 c3  92 30 00 00 00 00 00 fe  |...<.u...0......|
000001c0  ff ff ee fe ff ff 01 00  00 00 27 40 06 00 00 fe  |..........'@....|
000001d0  ff ff af fe ff ff 28 40  06 00 00 00 e0 04 00 fe  |......(@........|
000001e0  ff ff af fe ff ff 28 40  ea 04 78 3b a4 0b 80 fe  |......(@..x;....|
000001f0  ff ff 83 fe ff ff a0 7b  92 10 c0 01 56 02 55 aa  |.......{....V.U.|
00000200

```
```

alex@yabloko:~ $ sudo hexdump -Cn512 /dev/disk0s4
00000000  eb 63 90 00 00 00 00 00  00 00 00 00 00 00 00 00  |.c..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000050  00 00 00 00 00 00 00 00  00 00 00 80 d0 97 97 10  |................|
00000060  00 00 00 00 ff fa 90 90  f6 c2 80 75 02 b2 80 ea  |...........u....|
00000070  74 7c 00 00 31 c0 8e d8  8e d0 bc 00 20 fb a0 64  |t|..1....... ..d|
00000080  7c 3c ff 74 02 88 c2 52  bb 17 04 80 27 03 74 06  ||<.t...R....'.t.|
00000090  be 88 7d e8 1c 01 be 05  7c f6 c2 80 74 48 b4 41  |..}.....|...tH.A|
000000a0  bb aa 55 cd 13 5a 52 72  3d 81 fb 55 aa 75 37 83  |..U..ZRr=..U.u7.|
000000b0  e1 01 74 32 31 c0 89 44  04 40 88 44 ff 89 44 02  |..t21..D.@.D..D.|
000000c0  c7 04 10 00 66 8b 1e 5c  7c 66 89 5c 08 66 8b 1e  |....f..\|f.\.f..|
000000d0  60 7c 66 89 5c 0c c7 44  06 00 70 b4 42 cd 13 72  |`|f.\..D..p.B..r|
000000e0  05 bb 00 70 eb 76 b4 08  cd 13 73 0d f6 c2 80 0f  |...p.v....s.....|
000000f0  84 d0 00 be 93 7d e9 82  00 66 0f b6 c6 88 64 ff  |.....}...f....d.|
00000100  40 66 89 44 04 0f b6 d1  c1 e2 02 88 e8 88 f4 40  |@f.D...........@|
00000110  89 44 08 0f b6 c2 c0 e8  02 66 89 04 66 a1 60 7c  |.D.......f..f.`||
00000120  66 09 c0 75 4e 66 a1 5c  7c 66 31 d2 66 f7 34 88  |f..uNf.\|f1.f.4.|
00000130  d1 31 d2 66 f7 74 04 3b  44 08 7d 37 fe c1 88 c5  |.1.f.t.;D.}7....|
00000140  30 c0 c1 e8 02 08 c1 88  d0 5a 88 c6 bb 00 70 8e  |0........Z....p.|
00000150  c3 31 db b8 01 02 cd 13  72 1e 8c c3 60 1e b9 00  |.1......r...`...|
00000160  01 8e db 31 f6 bf 00 80  8e c6 fc f3 a5 1f 61 ff  |...1..........a.|
00000170  26 5a 7c be 8e 7d eb 03  be 9d 7d e8 34 00 be a2  |&Z|..}....}.4...|
00000180  7d e8 2e 00 cd 18 eb fe  47 52 55 42 20 00 47 65  |}.......GRUB .Ge|
00000190  6f 6d 00 48 61 72 64 20  44 69 73 6b 00 52 65 61  |om.Hard Disk.Rea|
000001a0  64 00 20 45 72 72 6f 72  0d 0a 00 bb 01 00 b4 0e  |d. Error........|
000001b0  cd 10 ac 3c 00 75 f4 c3  00 00 00 00 00 00 00 00  |...<.u..........|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```
```

Hardware Overview:

  Model Name:	MacBook Pro
  Model Identifier:	MacBookPro6,2
  Processor Name:	Intel Core i5
  Processor Speed:	2.4 GHz
  Number Of Processors:	1
  Total Number Of Cores:	2
  L2 Cache (per core):	256 KB
  L3 Cache:	3 MB
  Memory:	4 GB
  Processor Interconnect Speed:	4.8 GT/s
  Boot ROM Version:	MBP61.0057.B0C
  SMC Version (system):	1.58f16
  Serial Number (system):	W80385VDAGU
  Hardware UUID:	2267DE0D-3C9E-5724-9E66-27036C477502
  Sudden Motion Sensor:
  State:	Enabled

```

I would prefer to use rEFIt as my primary [apparently it's not actually a] bootloader, rather than tinker with grub-efi.

Any advice?  I miss having a linux box.
Thanks in advance.

---

### Post by rpglover64 on 2010-12-17
I've shut down my macbook several times and reinstalled grub on the partition...

No dice. :(

---

### Post by rpglover64 on 2010-12-18
I'm not sure what you mean...

Anyway, I managed to "fix" it.

I installed Windows on another partition, which conveniently wiped grub from the MBR and I installed grub on the linux partition (using the discouraged blocklist).  Everything magically works, now.  It's actually a bit terrifying.

---

