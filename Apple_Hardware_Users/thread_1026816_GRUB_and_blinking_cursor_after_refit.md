---
title: "GRUB and blinking cursor after refit"
date: 2008-12-31
forum: Apple Hardware Users
---

### Post by zowey on 2008-12-31
I've installed ubuntu ibex on my macbook aluminium and i've installed refit. I have two penguins and one apple.
When I try to boot to ubuntu i just get GRUB and blinkin cursor
I tried to reintall GRUB but and it all seems fine

grub> root (hd0,2)
grub> setup (hd0,2)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,2)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,2)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,2) /boot/grub/stage2 p /boot/grub/menu
.lst "... succeeded
Done.

There is some kind of problem and i can't figure it out

---

### Post by cyberdork33 on 2008-12-31
> **zowey said:**
> I've installed ubuntu ibex on my macbook aluminium and i've installed refit. I have two penguins and one apple.
When I try to boot to ubuntu i just get GRUB and blinkin cursor
I tried to reintall GRUB but and it all seems fine

grub> root (hd0,2)
grub> setup (hd0,2)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,2)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,2)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,2) /boot/grub/stage2 p /boot/grub/menu
.lst "... succeeded
Done.

There is some kind of problem and i can't figure it out
do you get the same result using either tux?

---

### Post by zowey on 2009-01-01
yes, GRUB word and blinking cursor

---

### Post by cyberdork33 on 2009-01-02
> **zowey said:**
> yes, GRUB word and blinking cursor

Is it a grub commandline, like this:
grub>

or it just says grub and that's it.

Have you made sure the partitions are in sync with rEFIt?

---

### Post by zowey on 2009-01-02
it's not grub command line.. I can't type. and there is no '>' sign

---

### Post by pxwpxw on 2009-01-03
> **zowey said:**
> it's not grub command line.. I can't type. and there is no '>' sign

You must use the refit Partition Tool to sync the MBR partition table.
And then if neither refit Tux icon works, do a restart using the Option key,
try a couple of times.

---

### Post by zowey on 2009-01-03
i did sync.. when do i press option key?

---

### Post by pxwpxw on 2009-01-03
> **zowey said:**
> i did sync.. when do i press option key?

Hold Option key down as it restarts, until disk icons appear.
You can either restart from refit, or using the power off button.

---

### Post by zowey on 2009-01-04
unfortunately that didn't help.
I held option and I got two hard drive pictures... osX and Windows option, I selected windows drive and again it was GRUB and blinking cursor. I tried again and again two penguins, but with the same result :(

---

### Post by pxwpxw on 2009-01-04
> **zowey said:**
> unfortunately that didn't help.
I held option and I got two hard drive pictures... osX and Windows option, I selected windows drive and again it was GRUB and blinking cursor. I tried again and again two penguins, but with the same result :(

Thats strange.
There may be something wrong with the ubuntu install - but do not change it, just do these checks from MacOSX and post the result, perhaps we can see where the problem is. 

From Applications:Utilities:Terminal
```

diskutil list

sudo hexdump -Cn512 /dev/disk0

sudo hexdump -Cn512 /dev/disk0s3


```

And from Applications:Utilities: Partition Inspector 
Get a Partition report and post it.

---

### Post by zowey on 2009-01-04
sh-3.2# hexdump -Cn512 /dev/disk0
00000000  eb 48 90 00 00 00 00 00  00 00 00 00 00 00 00 00  |?H..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000030  00 00 00 00 00 00 00 00  00 00 00 00 00 00 03 02  |................|
00000040  ff 00 00 80 00 48 7b 11  00 08 fa 90 90 f6 c2 80  |?....H{...?..??.|
00000050  75 02 b2 80 ea 59 7c 00  00 31 c0 8e d8 8e d0 bc  |u.?.?Y|..1?.?.&#1084;|
00000060  00 20 fb a0 40 7c 3c ff  74 02 88 c2 52 be 7f 7d  |. ??@|<?t..?R?.}|
00000070  e8 34 01 f6 c2 80 74 54  b4 41 bb aa 55 cd 13 5a  |?4.??.tT?A??U?.Z|
00000080  52 72 49 81 fb 55 aa 75  43 a0 41 7c 84 c0 75 05  |RrI.?U?uC?A|.?u.|
00000090  83 e1 01 74 37 66 8b 4c  10 be 05 7c c6 44 ff 01  |.?.t7f.L.?.|?D?.|
000000a0  66 8b 1e 44 7c c7 04 10  00 c7 44 02 01 00 66 89  |f..D|?...?D...f.|
000000b0  5c 08 c7 44 06 00 70 66  31 c0 89 44 04 66 89 44  |\.?D..pf1?.D.f.D|
000000c0  0c b4 42 cd 13 72 05 bb  00 70 eb 7d b4 08 cd 13  |.?B?.r.?.p?}?.?.|
000000d0  73 0a f6 c2 80 0f 84 ea  00 e9 8d 00 be 05 7c c6  |s.??...?.?..?.|?|
000000e0  44 ff 00 66 31 c0 88 f0  40 66 89 44 04 31 d2 88  |D?.f1?.?@f.D.1?.|
000000f0  ca c1 e2 02 88 e8 88 f4  40 89 44 08 31 c0 88 d0  |???..?.?@.D.1?.?|
00000100  c0 e8 02 66 89 04 66 a1  44 7c 66 31 d2 66 f7 34  |??.f..f?D|f1?f?4|
00000110  88 54 0a 66 31 d2 66 f7  74 04 88 54 0b 89 44 0c  |.T.f1?f?t..T..D.|
00000120  3b 44 08 7d 3c 8a 54 0d  c0 e2 06 8a 4c 0a fe c1  |;D.}<.T.??..L.??|
00000130  08 d1 8a 6c 0c 5a 8a 74  0b bb 00 70 8e c3 31 db  |.?.l.Z.t.?.p.?1?|
00000140  b8 01 02 cd 13 72 2a 8c  c3 8e 06 48 7c 60 1e b9  |?..?.r*.?..H|`.?|
00000150  00 01 8e db 31 f6 31 ff  fc f3 a5 1f 61 ff 26 42  |...?1?1???.a?&B|
00000160  7c be 85 7d e8 40 00 eb  0e be 8a 7d e8 38 00 eb  ||?.}?@.?.?.}?8.?|
00000170  06 be 94 7d e8 30 00 be  99 7d e8 2a 00 eb fe 47  |.?.}?0.?.}?*.??G|
00000180  52 55 42 20 00 47 65 6f  6d 00 48 61 72 64 20 44  |RUB .Geom.Hard D|
00000190  69 73 6b 00 52 65 61 64  00 20 45 72 72 6f 72 00  |isk.Read. Error.|
000001a0  bb 01 00 b4 0e cd 10 ac  3c 00 75 f4 c3 00 00 00  |?..?.?.?<.u??...|
000001b0  00 00 00 00 00 00 00 00  46 18 8b 58 cf c9 00 fe  |........F..X??.?|
000001c0  ff ff ee fe ff ff 01 00  00 00 27 40 06 00 00 fe  |??????....'@...?|
000001d0  ff ff af fe ff ff 28 40  06 00 00 00 5c 0f 80 fe  |??????(@....\..?|
000001e0  ff ff 83 fe ff ff 00 48  66 0f 00 50 3b 03 00 00  |??.???.Hf..P;...|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U?|
00000200
sh-3.2# hexdump -Cn512 /dev/disk0s3
00000000  eb 48 90 00 00 00 00 00  00 00 00 00 00 00 00 00  |?H..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000030  00 00 00 00 00 00 00 00  00 00 00 00 00 00 03 02  |................|
00000040  ff 00 00 80 28 c8 f2 0f  00 08 fa 90 90 f6 c2 80  |?...(??...?..??.|
00000050  75 02 b2 80 ea 59 7c 00  00 31 c0 8e d8 8e d0 bc  |u.?.?Y|..1?.?.&#1084;|
00000060  00 20 fb a0 40 7c 3c ff  74 02 88 c2 52 be 7f 7d  |. ??@|<?t..?R?.}|
00000070  e8 34 01 f6 c2 80 74 54  b4 41 bb aa 55 cd 13 5a  |?4.??.tT?A??U?.Z|
00000080  52 72 49 81 fb 55 aa 75  43 a0 41 7c 84 c0 75 05  |RrI.?U?uC?A|.?u.|
00000090  83 e1 01 74 37 66 8b 4c  10 be 05 7c c6 44 ff 01  |.?.t7f.L.?.|?D?.|
000000a0  66 8b 1e 44 7c c7 04 10  00 c7 44 02 01 00 66 89  |f..D|?...?D...f.|
000000b0  5c 08 c7 44 06 00 70 66  31 c0 89 44 04 66 89 44  |\.?D..pf1?.D.f.D|
000000c0  0c b4 42 cd 13 72 05 bb  00 70 eb 7d b4 08 cd 13  |.?B?.r.?.p?}?.?.|
000000d0  73 0a f6 c2 80 0f 84 ea  00 e9 8d 00 be 05 7c c6  |s.??...?.?..?.|?|
000000e0  44 ff 00 66 31 c0 88 f0  40 66 89 44 04 31 d2 88  |D?.f1?.?@f.D.1?.|
000000f0  ca c1 e2 02 88 e8 88 f4  40 89 44 08 31 c0 88 d0  |???..?.?@.D.1?.?|
00000100  c0 e8 02 66 89 04 66 a1  44 7c 66 31 d2 66 f7 34  |??.f..f?D|f1?f?4|
00000110  88 54 0a 66 31 d2 66 f7  74 04 88 54 0b 89 44 0c  |.T.f1?f?t..T..D.|
00000120  3b 44 08 7d 3c 8a 54 0d  c0 e2 06 8a 4c 0a fe c1  |;D.}<.T.??..L.??|
00000130  08 d1 8a 6c 0c 5a 8a 74  0b bb 00 70 8e c3 31 db  |.?.l.Z.t.?.p.?1?|
00000140  b8 01 02 cd 13 72 2a 8c  c3 8e 06 48 7c 60 1e b9  |?..?.r*.?..H|`.?|
00000150  00 01 8e db 31 f6 31 ff  fc f3 a5 1f 61 ff 26 42  |...?1?1???.a?&B|
00000160  7c be 85 7d e8 40 00 eb  0e be 8a 7d e8 38 00 eb  ||?.}?@.?.?.}?8.?|
00000170  06 be 94 7d e8 30 00 be  99 7d e8 2a 00 eb fe 47  |.?.}?0.?.}?*.??G|
00000180  52 55 42 20 00 47 65 6f  6d 00 48 61 72 64 20 44  |RUB .Geom.Hard D|
00000190  69 73 6b 00 52 65 61 64  00 20 45 72 72 6f 72 00  |isk.Read. Error.|
000001a0  bb 01 00 b4 0e cd 10 ac  3c 00 75 f4 c3 00 00 00  |?..?.?.?<.u??...|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U?|
00000200
---------------------------


*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    258097191  Mac OS X HFS+
 3      258361344    312580095  EFI System (FAT)

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    258097191  af  Mac OS X HFS+
 3 *    258361344    312580095  83  Linux

MBR contents:
 Boot Code: GRUB

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+

Partition at LBA 258361344:
 Boot Code: GRUB
 File System: ext3
 Listed in GPT as partition 3, type EFI System (FAT)
 Listed in MBR as partition 3, type 83  Linux, active

---

### Post by pxwpxw on 2009-01-04
zowey

Your hexdumps show that grub stage1 is installed, so that gets the GRUB - cursor, it just cant find its second stage and menu. You get 2 penguins because it is installed twice but that won stop it working.

The problem could be here -
```

*** Report for internal hard disk ***

Current GPT partition table:
# Start LBA End LBA Type
1 40 409639 EFI System (FAT)
2 409640 258097191 Mac OS X HFS+
3 258361344 312580095 EFI System (FAT)

```

Could you also check with 
```

diskutil list

```
It should confirm you have 2 EFI partitions, it is the easiest way to check.

In fact there should be only one EFI System , on the  #1 partition.

The GPT #3 partition should be just 'Basic Data'
( That is your ubuntu Linux partiton).

The second EFI happens if the 'boot' flag is set on the #3 sda3 linux partiton by gparted or the installer.

It can be unset by running gparted and selecting 'manage flags', but then you will have to run the refit Partition Tool to resync your MBR partitions, because gparted resets them.

Can you do that using your install CD?

You dont need to reinstall anything.

---

### Post by zowey on 2009-01-04
there should not be boot flag on third partition??
well i thought there should be..
i think i can remove it from there

---

### Post by pxwpxw on 2009-01-04
> **zowey said:**
> there should not be boot flag on third partition??
well i thought there should be..
i think i can remove it from there

Yes, try clearing any flag on the #3 partition (that is a GPT flag as gparted sees it)
Could well be the bug.

---

### Post by zowey on 2009-01-05
Thank u so much :) This really works. I got one penguin! and I can boot ubuntu normally. I like it. mmmm now remains only reboot problem :)

---

### Post by pxwpxw on 2009-01-05
> **zowey said:**
> Thank u so much :) This really works. I got one penguin! and I can boot ubuntu normally. I like it. mmmm now remains only reboot problem :)

What reboot problem is that?

---

### Post by zowey on 2009-01-06
Blank screen and system beeping

---

### Post by pxwpxw on 2009-01-07
> **zowey said:**
> Blank screen and system beeping

I dont understand. Can you explain fully please.

---

### Post by emmary on 2009-01-07
China Digital Photo Frame Wholesale 
  
Digital Photo Frame:How do you display the pictures in your digital camera, printing them out and clipping in the album just like the traditional photos? Why not getting yourself a digital photo frame and then you can appreciate the rotating set of your favorite photos in a neat and attractive frame. Our products mainly fall into two categories, namely the key-chain frame and the luxuriously large LCD display, considering the different needs. The key-chain ones are for portability. On the other hand, the large screen is for aesthetically pleasing ornament hanging on the wall or standing on the table. Best of all, TRADESTEAD offers you fairly competitive price. 

Related Categories:Digital Cameras Digital Camcorders photo album Key chains MP4 Player Bluetooth
 
 
 


 Photo Album Key Chains 
 
 


 Photo Frames

---

### Post by zowey on 2009-01-08
I don't know, maybe is problem of ACPI module, When I try to restart from ubuntu he  only goes blank screen and start beeping than i must turn off the computer and than turn it on again

---

### Post by ercoppa on 2009-05-20
I have the same issue of zowey with GRUB.

From the beginning: I have Ubuntu 8.10 (installed in november), yesterday I decide to resize my root partition, delete the swap partition and create a new primary partition (for data files).

Before:
sda1 -> EFI
sda2 -> Mac OS X
sda3 -> Ubuntu / ext3
sda4 -> swap

After (I use the parttion tool on the live CD of Ubuntu 9.04):
sda1 -> EFI
sda2 -> Mac OS X
sda3 -> Ubuntu / ext3 (no boot flag)
sda4 -> empty ext3 partition (np boot flag)

I no need to syncronized GPT table with Refit (tool on the live CD does by self?) but when select the tux icon I have only a "GRUB" with a blinking cursor.

I tried to manually reinstall GRUB with:
```
root (hd0,2)
setup (hd0,2)
```
But nothing changes.

```
Last login: Wed May 20 13:23:16 on console
ercoppa-laptop:~ emiliocoppa$ diskutil list
/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *149.1 Gi   disk0
   1:                        EFI                         200.0 Mi   disk0s1
   2:                  Apple_HFS Macintosh HD            40.9 Gi    disk0s2
   3:       Microsoft Basic Data                         98.4 Gi    disk0s3
   4:       Microsoft Basic Data                         9.5 Gi     disk0s4

```

```
p:~ emiliocoppa$ sudo hexdump -Cn512 /dev/disk0
Password:
00000000  fa 31 c0 8e d8 8e c0 8e  d0 bc 00 7c fb fc 89 e6  |?1?.?.?.&#1084;.|??.?|
00000010  bf 00 06 b9 00 01 f3 a5  ea 1d 06 00 00 88 16 00  |?..?..??.......|
00000020  08 b4 08 cd 13 31 c0 88  f0 40 a3 f0 06 80 e1 3f  |.?.?.1?.?@??..??|
00000030  88 0e f2 06 be be 07 31  c0 b9 04 00 f6 04 80 74  |..?.??.1??..?..t|
00000040  03 40 89 f7 83 c6 10 e2  f3 83 f8 01 75 73 8a 16  |.@.?.?.??.?.us..|
00000050  00 08 b8 00 41 bb aa 55  31 c9 30 f6 f9 cd 13 72  |..?.A??U1?0???.r|
00000060  23 81 fb 55 aa 75 1d f6  c1 01 74 18 57 be e0 06  |#.?U?u.??.t.W??.|
00000070  8b 5d 08 89 5c 08 8b 5d  0a 89 5c 0a 8a 16 00 08  |.]..\..]..\.....|
00000080  b4 42 eb 2a 57 8b 45 08  8b 55 0a f7 36 f2 06 42  |?B?*W.E..U.?6?.B|
00000090  89 d1 31 d2 f7 36 f0 06  88 c5 d1 e8 d1 e8 24 c0  |.?1??6?..?????$?|
000000a0  08 c1 88 d6 8a 16 00 08  bb 00 7c b8 01 02 cd 13  |.?.?....?.|?..?.|
000000b0  72 16 5e 81 3e fe 7d 55  aa 75 08 fa ea 00 7c 00  |r.^.>?}U?u.??.|.|
000000c0  00 77 05 be f4 06 eb 03  be 0f 07 ac 20 c0 74 0c  |.w.??.?.?..? ?t.|
000000d0  b4 0e 8a 3e 62 04 b3 07  cd 10 eb ef eb fe 00 00  |?..>b.?.?.????..|
000000e0  10 00 01 00 00 7c 00 00  00 00 00 00 00 00 00 00  |.....|..........|
000000f0  00 00 00 00 4d 69 73 73  69 6e 67 20 6f 70 65 72  |....Missing oper|
00000100  61 74 69 6e 67 20 73 79  73 74 65 6d 0d 0a 00 4f  |ating system...O|
00000110  70 65 72 61 74 69 6e 67  20 73 79 73 74 65 6d 20  |perating system |
00000120  6c 6f 61 64 69 6e 67 20  65 72 72 6f 72 0d 0a 00  |loading error...|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 fe  |...............?|
000001c0  ff ff ee fe ff ff 01 00  00 00 27 40 06 00 00 fe  |??????....'@...?|
000001d0  ff ff af fe ff ff 28 40  06 00 00 00 1c 05 80 fe  |??????(@.......?|
000001e0  ff ff 83 fe ff ff 28 40  22 05 fc 19 4e 0c 00 fe  |??.???(@".?.N..?|
000001f0  ff ff 83 fe ff ff 24 5a  70 11 9d 30 31 01 55 aa  |??.???$Zp..01.U?|
00000200
ercoppa-laptop:~ emiliocoppa$ sudo hexdump -Cn512 /dev/disk0
00000000  fa 31 c0 8e d8 8e c0 8e  d0 bc 00 7c fb fc 89 e6  |?1?.?.?.&#1084;.|??.?|
00000010  bf 00 06 b9 00 01 f3 a5  ea 1d 06 00 00 88 16 00  |?..?..??.......|
00000020  08 b4 08 cd 13 31 c0 88  f0 40 a3 f0 06 80 e1 3f  |.?.?.1?.?@??..??|
00000030  88 0e f2 06 be be 07 31  c0 b9 04 00 f6 04 80 74  |..?.??.1??..?..t|
00000040  03 40 89 f7 83 c6 10 e2  f3 83 f8 01 75 73 8a 16  |.@.?.?.??.?.us..|
00000050  00 08 b8 00 41 bb aa 55  31 c9 30 f6 f9 cd 13 72  |..?.A??U1?0???.r|
00000060  23 81 fb 55 aa 75 1d f6  c1 01 74 18 57 be e0 06  |#.?U?u.??.t.W??.|
00000070  8b 5d 08 89 5c 08 8b 5d  0a 89 5c 0a 8a 16 00 08  |.]..\..]..\.....|
00000080  b4 42 eb 2a 57 8b 45 08  8b 55 0a f7 36 f2 06 42  |?B?*W.E..U.?6?.B|
00000090  89 d1 31 d2 f7 36 f0 06  88 c5 d1 e8 d1 e8 24 c0  |.?1??6?..?????$?|
000000a0  08 c1 88 d6 8a 16 00 08  bb 00 7c b8 01 02 cd 13  |.?.?....?.|?..?.|
000000b0  72 16 5e 81 3e fe 7d 55  aa 75 08 fa ea 00 7c 00  |r.^.>?}U?u.??.|.|
000000c0  00 77 05 be f4 06 eb 03  be 0f 07 ac 20 c0 74 0c  |.w.??.?.?..? ?t.|
000000d0  b4 0e 8a 3e 62 04 b3 07  cd 10 eb ef eb fe 00 00  |?..>b.?.?.????..|
000000e0  10 00 01 00 00 7c 00 00  00 00 00 00 00 00 00 00  |.....|..........|
000000f0  00 00 00 00 4d 69 73 73  69 6e 67 20 6f 70 65 72  |....Missing oper|
00000100  61 74 69 6e 67 20 73 79  73 74 65 6d 0d 0a 00 4f  |ating system...O|
00000110  70 65 72 61 74 69 6e 67  20 73 79 73 74 65 6d 20  |perating system |
00000120  6c 6f 61 64 69 6e 67 20  65 72 72 6f 72 0d 0a 00  |loading error...|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 fe  |...............?|
000001c0  ff ff ee fe ff ff 01 00  00 00 27 40 06 00 00 fe  |??????....'@...?|
000001d0  ff ff af fe ff ff 28 40  06 00 00 00 1c 05 80 fe  |??????(@.......?|
000001e0  ff ff 83 fe ff ff 28 40  22 05 fc 19 4e 0c 00 fe  |??.???(@".?.N..?|
000001f0  ff ff 83 fe ff ff 24 5a  70 11 9d 30 31 01 55 aa  |??.???$Zp..01.U?|
00000200

```

```
ercoppa-laptop:~ emiliocoppa$ sudo hexdump -Cn512 /dev/disk0s3
00000000  eb 48 90 00 00 00 00 00  00 00 00 00 00 00 00 00  |?H..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000030  00 00 00 00 00 00 00 00  00 00 00 00 00 00 03 02  |................|
00000040  ff 00 00 80 3f 96 47 0f  00 08 fa 90 90 f6 c2 80  |?...?.G...?..??.|
00000050  75 02 b2 80 ea 59 7c 00  00 31 c0 8e d8 8e d0 bc  |u.?.?Y|..1?.?.&#1084;|
00000060  00 20 fb a0 40 7c 3c ff  74 02 88 c2 52 be 7f 7d  |. ??@|<?t..?R?.}|
00000070  e8 34 01 f6 c2 80 74 54  b4 41 bb aa 55 cd 13 5a  |?4.??.tT?A??U?.Z|
00000080  52 72 49 81 fb 55 aa 75  43 a0 41 7c 84 c0 75 05  |RrI.?U?uC?A|.?u.|
00000090  83 e1 01 74 37 66 8b 4c  10 be 05 7c c6 44 ff 01  |.?.t7f.L.?.|?D?.|
000000a0  66 8b 1e 44 7c c7 04 10  00 c7 44 02 01 00 66 89  |f..D|?...?D...f.|
000000b0  5c 08 c7 44 06 00 70 66  31 c0 89 44 04 66 89 44  |\.?D..pf1?.D.f.D|
000000c0  0c b4 42 cd 13 72 05 bb  00 70 eb 7d b4 08 cd 13  |.?B?.r.?.p?}?.?.|
000000d0  73 0a f6 c2 80 0f 84 ea  00 e9 8d 00 be 05 7c c6  |s.??...?.?..?.|?|
000000e0  44 ff 00 66 31 c0 88 f0  40 66 89 44 04 31 d2 88  |D?.f1?.?@f.D.1?.|
000000f0  ca c1 e2 02 88 e8 88 f4  40 89 44 08 31 c0 88 d0  |???..?.?@.D.1?.?|
00000100  c0 e8 02 66 89 04 66 a1  44 7c 66 31 d2 66 f7 34  |??.f..f?D|f1?f?4|
00000110  88 54 0a 66 31 d2 66 f7  74 04 88 54 0b 89 44 0c  |.T.f1?f?t..T..D.|
00000120  3b 44 08 7d 3c 8a 54 0d  c0 e2 06 8a 4c 0a fe c1  |;D.}<.T.??..L.??|
00000130  08 d1 8a 6c 0c 5a 8a 74  0b bb 00 70 8e c3 31 db  |.?.l.Z.t.?.p.?1?|
00000140  b8 01 02 cd 13 72 2a 8c  c3 8e 06 48 7c 60 1e b9  |?..?.r*.?..H|`.?|
00000150  00 01 8e db 31 f6 31 ff  fc f3 a5 1f 61 ff 26 42  |...?1?1???.a?&B|
00000160  7c be 85 7d e8 40 00 eb  0e be 8a 7d e8 38 00 eb  ||?.}?@.?.?.}?8.?|
00000170  06 be 94 7d e8 30 00 be  99 7d e8 2a 00 eb fe 47  |.?.}?0.?.}?*.??G|
00000180  52 55 42 20 00 47 65 6f  6d 00 48 61 72 64 20 44  |RUB .Geom.Hard D|
00000190  69 73 6b 00 52 65 61 64  00 20 45 72 72 6f 72 00  |isk.Read. Error.|
000001a0  bb 01 00 b4 0e cd 10 ac  3c 00 75 f4 c3 00 00 00  |?..?.?.?<.u??...|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U?|
00000200
ercoppa-laptop:~ emiliocoppa$ 

```

Any ideas?

---

### Post by ercoppa on 2009-05-20
Ok, I fix my problem. I use old live CD (8.10) that not auto-sync GPT table (I erase and recreate the fourth partition). Refit sync it correctly and now  Grub works well.

In conclusion: no trust in partition tool on the new live CD (9.04).

Greets, ercoppa.

---

### Post by cyberdork33 on 2009-05-21
.

---

### Post by kneekos on 2013-01-14
Hello,

I am trying to run linux on a macbook pro 3,1. The installation goes well. Refit installs ok and syncs ok but I get the word GRUB and a blinking cursor _  after refit.

I used crunchbang linux x64bit version, practicaly the same installer as debian.

I do get two tux pictures on refit boot up, but that shouldn't be a major problem. I am running mountain lion 10.8, thus the recovery partition.


diskutil list

/dev/disk0
   #:                       TYPE NAME                                SIZE       IDENTIFIER
   0:      GUID_partition_scheme                          *160.0 GB    disk0
   1:                        EFI                                         209.7 MB   disk0s1
   2:                  Apple_HFS Macintosh HD            139.2 GB    disk0s2
   3:                 Apple_Boot Recovery HD              650.0 MB   disk0s3
   4:          Microsoft Basic Data                           20.0 GB     disk0s4

I tried through gparted to remove any flags from sda4, so there are none now but I still cannot boot.

Could anyone help?

---

