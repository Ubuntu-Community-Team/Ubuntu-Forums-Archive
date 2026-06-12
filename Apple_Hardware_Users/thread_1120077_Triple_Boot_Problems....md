---
title: "Triple Boot Problems..."
date: 2009-04-08
forum: Apple Hardware Users
---

### Post by sudo101 on 2009-04-08
Hey... 

    I just finished installing Ubuntu and Vista alongside with OSX and i ended up with a problem which is : i cant boot into my Ubuntu or Vista and OS X is running fine... what happened is that i installed OSX and i used Boot Camp and formated 60GB for windows. after installing windows i installed rEFIt and both OSX and Vista worked just prefect. and then i booted Ubuntu Live CD and i resized the 60GB partition to 30GB with Ext3 and i installed Ubuntu on it along with GRUB boot loader in the same sda4.. I think that was it.. anyway it was the last one.. So now when i boot up i get  3 options of all 3 OS's but when i boot Ubuntu or Vista I just get the Pointer blinking and thats it.. nothing at all. 

so can anyone help with this please  ??

Thanks alot guyz..

MRB,

---

### Post by cyberdork33 on 2009-04-08
Please check the directions in the wiki:
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

---

### Post by sudo101 on 2009-04-09
Thanks a lot for your advice. But the thing is that's exactly what i did. i followed the exact instructions. but what i got is only one  OS which boots right which is OS X ! thanks again for your help.. and i wish i can find how to solve this problem without having to reinstall everything..

---

### Post by pxwpxw on 2009-04-09
Have you run the refit Partition Tool to check and update the MBR.

---

### Post by sudo101 on 2009-04-09
Yes Done that...

---

### Post by pxwpxw on 2009-04-09
> **sudo101 said:**
> Yes Done that...

Please check what is on your sda  MBR and partition sda4 using hexdump from macOSX terminal command line, like this
```

sudo hexdump -Cn512 /dev/disk0

sudo hexdump -Cn512 /dev/disk0s4

```
They will print what is in the first 512 bytes of each, please post.

---

### Post by sudo101 on 2009-04-09
basel-hamadehs-macbook-pro:~ mrb$ sudo hexdump -Cn512 /dev/disk0
00000000  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001c0  01 00 ee fe ff ff 01 00  00 00 af 9e a1 12 00 00  |..????....?.?...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 80 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U?|
00000200
basel-hamadehs-macbook-pro:~ mrb$ sudo hexdump -Cn512 /dev/disk0s4
00000000  eb 48 90 00 00 00 00 00  00 00 00 00 00 00 00 00  |?H..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000030  00 00 00 00 00 00 00 00  00 00 00 00 00 00 03 02  |................|
00000040  ff 00 00 80 3d fa b9 10  00 08 fa 90 90 f6 c2 80  |?...=??...?..??.|
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
basel-hamadehs-macbook-pro:~ mrb$ 

that's it.. Copied and pasted..
i dont understand it. i hope u do..
thanks for your help

---

### Post by cyberdork33 on 2009-04-09
Please put terminal output in [noparse]```
code tags
```[/noparse]. It makes it a lot easier to read.

---

### Post by pxwpxw on 2009-04-09
> **sudo101 said:**
> 
that's it.. Copied and pasted..
i dont understand it. i hope u do..
thanks for your help
Easier to read thus -
```

basel-hamadehs-macbook-pro:~ mrb$ sudo hexdump -Cn512 /dev/disk0
00000000 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 |................|
*
000001c0 01 00 ee fe ff ff 01 00 00 00 af 9e a1 12 00 00 |..????....?.?...|
000001d0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 |................|
000001e0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 80 00 |................|
000001f0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 aa |..............U?|
00000200
basel-hamadehs-macbook-pro:~ mrb$ sudo hexdump -Cn512 /dev/disk0s4
00000000 eb 48 90 00 00 00 00 00 00 00 00 00 00 00 00 00 |?H..............|
00000010 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 |................|
*
00000030 00 00 00 00 00 00 00 00 00 00 00 00 00 00 03 02 |................|
00000040 ff 00 00 80 3d fa b9 10 00 08 fa 90 90 f6 c2 80 |?...=??...?..??.|
00000050 75 02 b2 80 ea 59 7c 00 00 31 c0 8e d8 8e d0 bc |u.?.?Y|..1?.?.&#1084;|
00000060 00 20 fb a0 40 7c 3c ff 74 02 88 c2 52 be 7f 7d |. ??@|<?t..?R?.}|
00000070 e8 34 01 f6 c2 80 74 54 b4 41 bb aa 55 cd 13 5a |?4.??.tT?A??U?.Z|
00000080 52 72 49 81 fb 55 aa 75 43 a0 41 7c 84 c0 75 05 |RrI.?U?uC?A|.?u.|
00000090 83 e1 01 74 37 66 8b 4c 10 be 05 7c c6 44 ff 01 |.?.t7f.L.?.|?D?.|
000000a0 66 8b 1e 44 7c c7 04 10 00 c7 44 02 01 00 66 89 |f..D|?...?D...f.|
000000b0 5c 08 c7 44 06 00 70 66 31 c0 89 44 04 66 89 44 |\.?D..pf1?.D.f.D|
000000c0 0c b4 42 cd 13 72 05 bb 00 70 eb 7d b4 08 cd 13 |.?B?.r.?.p?}?.?.|
000000d0 73 0a f6 c2 80 0f 84 ea 00 e9 8d 00 be 05 7c c6 |s.??...?.?..?.|?|
000000e0 44 ff 00 66 31 c0 88 f0 40 66 89 44 04 31 d2 88 |D?.f1?.?@f.D.1?.|
000000f0 ca c1 e2 02 88 e8 88 f4 40 89 44 08 31 c0 88 d0 |???..?.?@.D.1?.?|
00000100 c0 e8 02 66 89 04 66 a1 44 7c 66 31 d2 66 f7 34 |??.f..f?D|f1?f?4|
00000110 88 54 0a 66 31 d2 66 f7 74 04 88 54 0b 89 44 0c |.T.f1?f?t..T..D.|
00000120 3b 44 08 7d 3c 8a 54 0d c0 e2 06 8a 4c 0a fe c1 |;D.}<.T.??..L.??|
00000130 08 d1 8a 6c 0c 5a 8a 74 0b bb 00 70 8e c3 31 db |.?.l.Z.t.?.p.?1?|
00000140 b8 01 02 cd 13 72 2a 8c c3 8e 06 48 7c 60 1e b9 |?..?.r*.?..H|`.?|
00000150 00 01 8e db 31 f6 31 ff fc f3 a5 1f 61 ff 26 42 |...?1?1???.a?&B|
00000160 7c be 85 7d e8 40 00 eb 0e be 8a 7d e8 38 00 eb ||?.}?@.?.?.}?8.?|
00000170 06 be 94 7d e8 30 00 be 99 7d e8 2a 00 eb fe 47 |.?.}?0.?.}?*.??G|
00000180 52 55 42 20 00 47 65 6f 6d 00 48 61 72 64 20 44 |RUB .Geom.Hard D|
00000190 69 73 6b 00 52 65 61 64 00 20 45 72 72 6f 72 00 |isk.Read. Error.|
000001a0 bb 01 00 b4 0e cd 10 ac 3c 00 75 f4 c3 00 00 00 |?..?.?.?<.u??...|
000001b0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 |................|
*
000001f0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 aa |..............U?|
00000200
basel-hamadehs-macbook-pro:~ mrb$ 

```

=========
The /dev/disk0 is your MBR and it shows it needs to be updated by the refit Partition Tool (there is no partiton table information).  The refit Partition Tool is on the bottom row of refit icons.

The /dev/disk0s4 looks good, it has the grub boot code all ready to go once the MBR partition table  is fixed to find it. Vista will then have to be booted via grub, until you fix the MBR from Vista to replace the 'Missing operating system' stuff. But I dont use Vista so I cant show you that bit.

===================
My disk -
Before update MBR
```

im81:~ pxw$ sudo hexdump -Cn512 /dev/disk0
Password:
00000000  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001c0  01 00 ee fe ff ff 01 00  00 00 af ea 42 25 00 00  |..????....??B%..|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U?|
00000200
im81:~ pxw$ 

```
After update MBR, the partition table is starts at the end of the 000001b0 line
```

im81:~ pxw$ sudo hexdump -Cn512 /dev/disk0
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
000001d0  ff ff af fe ff ff 28 40  06 00 f8 eb 1d 05 00 fe  |??????(@..??...?|
000001e0  ff ff af fe ff ff 20 2c  28 05 00 00 3c 01 80 fe  |?????? ,(...<..?|
000001f0  ff ff 83 fe ff ff 20 2c  68 06 c9 17 a8 04 55 aa  |??.??? ,h.?.?.U?|
00000200
im81:~ pxw$

```

---

### Post by sudo101 on 2009-04-10
```
basel-hamadehs-macbook-pro:~ mrb$ sudo hexdump -Cn512 /dev/disk0
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
000001d0  ff ff af fe ff ff 28 40  06 00 00 00 fc 0a 80 fe  |??????(@....?..?|
000001e0  ff ff 07 fe ff ff b9 35  06 0b 7c b4 cb 03 00 fe  |??.????5..|??..?|
000001f0  ff ff 83 fe ff ff 35 ea  d1 0e bf 1f a6 03 55 aa  |??.???5??.?.?.U?|
00000200
basel-hamadehs-macbook-pro:~ mrb$ 

```

after updating the MBR the outcomes is the above and something change though at first when i chose an OS it goes after the logo screen and i get a black screen with a blinking courser but now it just stops a the OS logo screen. I hope that means good

---

### Post by sudo101 on 2009-04-10
Hey.. I got some updates.. Ubuntu is running prefect.. but vista has some problem with its BootLoader i guess it requested me to put the Disk and repair it.. i dont wanna do it before i know what will happen cuz i am afraid that it will break the Other OS's

---

### Post by pxwpxw on 2009-04-10
> **sudo101 said:**
> ```
basel-hamadehs-macbook-pro:~ mrb$ sudo hexdump -Cn512 /dev/disk0
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
000001d0  ff ff af fe ff ff 28 40  06 00 00 00 fc 0a [COLOR="Red"]80[/COLOR] fe  |??????(@....?..?|
000001e0  ff ff 07 fe ff ff b9 35  06 0b 7c b4 cb 03 00 fe  |??.????5..|??..?|
000001f0  ff ff 83 fe ff ff 35 ea  d1 0e bf 1f a6 03 55 aa  |??.???5??.?.?.U?|
00000200
basel-hamadehs-macbook-pro:~ mrb$ 

```

after updating the MBR the outcomes is the above and something change though at first when i chose an OS it goes after the logo screen and i get a black screen with a blinking courser but now it just stops a the OS logo screen. I hope that means good

That looks better, but for some reason /dev/sda3 is marked as boot (80) instead of /dev/sda4.
What is on /dev/sda3? - please do a hexdumpp for sda3
```

sudo hexdump -Cn512 /dev/disk0s3

```

---

### Post by pxwpxw on 2009-04-10
> **sudo101 said:**
> Hey.. I got some updates.. Ubuntu is running prefect.. but vista has some problem with its BootLoader i guess it requested me to put the Disk and repair it.. i dont wanna do it before i know what will happen cuz i am afraid that it will break the Other OS's

You should be able to boot Vista from the grub menu, please see my other post as well.

---

### Post by sudo101 on 2009-04-12
Thanks alot guyz is working now.. appreciate your help...

---

