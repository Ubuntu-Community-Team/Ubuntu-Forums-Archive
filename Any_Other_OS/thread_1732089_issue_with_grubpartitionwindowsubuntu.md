---
title: "issue with grub/partition/windows/ubuntu"
date: 2011-04-17
forum: Any Other OS
---

### Post by derik123derik123 on 2011-04-17
Alright, my story starts off like this.
I decided to dual boot with win7 and mint.
I loaded up gparted live cd.
was going to split the main win7 drive 50/60
for some reason i could only take 7 gigs out of my win7 partition.
So i figured that would be enough and didn't attempt to get more.
after installing mint i decided to go into gparted and wipe my mint so that i could redo it and install ubuntu instead of mint.
So i went to boot into win7 and I got this
```
GRUB loading.
error: no such partition
grub rescue>
```
I knew this was because I wiped the partition with he grub information. so i wanted to wait a couple of days and just use win7.
So i attempted to fix the issue with grub and went through a couple of tutorials in order to restore MBR.
But they all didn't work.
the last thing I tried was booted up gparted and marked the partition that I have win7 installed on as a boot label and restarted.
Now in gparted my win7 partition is marked as unknown.
I try and load the win7 DVD and it can't find the win7 partition.

So... Help?

thanks guys

---

### Post by derik123derik123 on 2011-04-17
[IMG]http://i51.tinypic.com/2qcquk4.png[/IMG]

---

### Post by kiyop on 2011-04-17
One way is to use testdisk to recover /dev/sda2.
But you should know how to use testdisk in order to recover.

I want to know information on /dev/sda2 in partition table and whether "backup boot sector" of /dev/sda2 exists or not.
Boot with Ubuntu(or mint)  LiveCD and open terminal
"Application" -> "Accessory" -> "Teminal"
and copy the following and paste into the opened window.
```
sudo su
fdisk -lu /dev/sda
dd if=/dev/sda bs=512 count=1 skip=$(fdisk -lu 2>/dev/null|grep /dev/sda2|tr -s " "|cut -d " " -f2) 2>/dev/null|hd
dd if=/dev/sda bs=512 count=1 skip=$(fdisk -lu 2>/dev/null|grep /dev/sda2|tr -s " "|cut -d " " -f3) 2>/dev/null|hd
```and press ENTER key once.
Copy all the contents in the opened window and paste to "Reply" "Message" and submit.

---

### Post by Perfect Storm on 2011-04-17
Moved to Other OS/Distro Talk.

---

### Post by derik123derik123 on 2011-04-17
> **kiyop said:**
> One way is to use testdisk to recover /dev/sda2.
But you should know how to use testdisk in order to recover.

I want to know information on /dev/sda2 in partition table and whether "backup boot sector" of /dev/sda2 exists or not.
Boot with Ubuntu(or mint)  LiveCD and open terminal
"Application" -> "Accessory" -> "Teminal"
and copy the following and paste into the opened window.
```
sudo su
fdisk -lu /dev/sda
dd if=/dev/sda bs=512 count=1 skip=$(fdisk -lu 2>/dev/null|grep /dev/sda2|tr -s " "|cut -d " " -f2) 2>/dev/null|hd
dd if=/dev/sda bs=512 count=1 skip=$(fdisk -lu 2>/dev/null|grep /dev/sda2|tr -s " "|cut -d " " -f3) 2>/dev/null|hd
```and press ENTER key once.
Copy all the contents in the opened window and paste to "Reply" "Message" and submit.

Okay! Thank you very much for your reply. I'm at work right now, but i can do it when i get home. 

Many thanks.

---

### Post by derik123derik123 on 2011-04-18
> **kiyop said:**
> One way is to use testdisk to recover /dev/sda2.
But you should know how to use testdisk in order to recover.

I want to know information on /dev/sda2 in partition table and whether "backup boot sector" of /dev/sda2 exists or not.
Boot with Ubuntu(or mint)  LiveCD and open terminal
"Application" -> "Accessory" -> "Teminal"
and copy the following and paste into the opened window.
```
sudo su
fdisk -lu /dev/sda
dd if=/dev/sda bs=512 count=1 skip=$(fdisk -lu 2>/dev/null|grep /dev/sda2|tr -s " "|cut -d " " -f2) 2>/dev/null|hd
dd if=/dev/sda bs=512 count=1 skip=$(fdisk -lu 2>/dev/null|grep /dev/sda2|tr -s " "|cut -d " " -f3) 2>/dev/null|hd
```and press ENTER key once.
Copy all the contents in the opened window and paste to "Reply" "Message" and submit.

```


derik@derik-linux-desktop ~ $ sudo su
[sudo] password for derik: 
 _____________________________________
( Q: Why did the astrophysicist order )
( three hamburgers? A: Because he was )
( hungry.                             )
 -------------------------------------
  o
   o   \_\_    _/_/
    o      \__/
           (oo)\_______
           (__)\       )\/\
               ||----w |
               ||     ||
derik-linux-desktop derik # fdisk -lu /dev/sda

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x15841583

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          206848   609892351   304842752   83  Linux
Partition 2 does not end on cylinder boundary.
/dev/sda3       609894398   625139711     7622657    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sda5       609894400   624947199     7526400   83  Linux
/dev/sda6       624949248   625139711       95232   82  Linux swap / Solaris
derik-linux-desktop derik # dd if=/dev/sda bs=512 count=1 skip=$(fdisk -lu 2>/dev/null|grep /dev/sda2|tr -s " "|cut -d " " -f2) 2>/dev/null|hd
00000000  fa 31 c0 8e d8 8e d0 bc  00 7c 89 e6 06 57 8e c0  |.1.......|...W..|
00000010  fb fc bf 00 06 b9 00 01  f3 a5 ea 1f 06 00 00 52  |...............R|
00000020  52 b4 41 bb aa 55 31 c9  30 f6 f9 cd 13 72 13 81  |R.A..U1.0....r..|
00000030  fb 55 aa 75 0d d1 e9 73  09 66 c7 06 8d 06 b4 42  |.U.u...s.f.....B|
00000040  eb 15 5a b4 08 cd 13 83  e1 3f 51 0f b6 c6 40 f7  |..Z......?Q...@.|
00000050  e1 52 50 66 31 c0 66 99  e8 66 00 e8 21 01 4d 69  |.RPf1.f..f..!.Mi|
00000060  73 73 69 6e 67 20 6f 70  65 72 61 74 69 6e 67 20  |ssing operating |
00000070  73 79 73 74 65 6d 2e 0d  0a 66 60 66 31 d2 bb 00  |system...f`f1...|
00000080  7c 66 52 66 50 06 53 6a  01 6a 10 89 e6 66 f7 36  ||fRfP.Sj.j...f.6|
00000090  f4 7b c0 e4 06 88 e1 88  c5 92 f6 36 f8 7b 88 c6  |.{.........6.{..|
000000a0  08 e1 41 b8 01 02 8a 16  fa 7b cd 13 8d 64 10 66  |..A......{...d.f|
000000b0  61 c3 e8 c4 ff be be 7d  bf be 07 b9 20 00 f3 a5  |a......}.... ...|
000000c0  c3 66 60 89 e5 bb be 07  b9 04 00 31 c0 53 51 f6  |.f`........1.SQ.|
000000d0  07 80 74 03 40 89 de 83  c3 10 e2 f3 48 74 5b 79  |..t.@.......Ht[y|
000000e0  39 59 5b 8a 47 04 3c 0f  74 06 24 7f 3c 05 75 22  |9Y[.G.<.t.$.<.u"|
000000f0  66 8b 47 08 66 8b 56 14  66 01 d0 66 21 d2 75 03  |f.G.f.V.f..f!.u.|
00000100  66 89 c2 e8 ac ff 72 03  e8 b6 ff 66 8b 46 1c e8  |f.....r....f.F..|
00000110  a0 ff 83 c3 10 e2 cc 66  61 c3 e8 62 00 4d 75 6c  |.......fa..b.Mul|
00000120  74 69 70 6c 65 20 61 63  74 69 76 65 20 70 61 72  |tiple active par|
00000130  74 69 74 69 6f 6e 73 2e  0d 0a 66 8b 44 08 66 03  |titions...f.D.f.|
00000140  46 1c 66 89 44 08 e8 30  ff 72 13 81 3e fe 7d 55  |F.f.D..0.r..>.}U|
00000150  aa 0f 85 06 ff bc fa 7b  5a 5f 07 fa ff e4 e8 1e  |.......{Z_......|
00000160  00 4f 70 65 72 61 74 69  6e 67 20 73 79 73 74 65  |.Operating syste|
00000170  6d 20 6c 6f 61 64 20 65  72 72 6f 72 2e 0d 0a 5e  |m load error...^|
00000180  ac b4 0e 8a 3e 62 04 b3  07 cd 10 3c 0a 75 f1 cd  |....>b.....<.u..|
00000190  18 f4 eb fd 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 a8 01 0d 0a  |................|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200
derik-linux-desktop derik # dd if=/dev/sda bs=512 count=1 skip=$(fdisk -lu 2>/dev/null|grep /dev/sda2|tr -s " "|cut -d " " -f3) 2>/dev/null|hd
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 f0 00 00 28 03 00  |........?....(..|
00000020  00 00 00 00 80 00 80 00  ff 0f 57 24 00 00 00 00  |..........W$....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  a7 93 b5 88 b1 b5 88 12  |................|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200
derik-linux-desktop derik # 

```

thank you very much.

---

### Post by kiyop on 2011-04-18
One problem is that /dev/sda2 is recognized as 83(linux) not 07(ntfs) at partition table in MBR.
> /dev/sda2          206848   609892351   304842752   83  LinuxSecond problem is that the partition boot record of /dev/sda2 is corrupt.

The backup of the former partition boot record of /dev/sda2 seems to have been saved in the last sector of /dev/sda2.
And fortunately, the information on total sectors in the backup:
> 00000020  00 00 00 00 80 00 80 00  ff 0f 57 24 00 00 00 00  |..........W$....|ff 0f 57 24 (little endian) = 24 57 0f ff =609685503
is same as 
609892351-206848
So, the backup boot sector was saved after /dev/sda3 was formed, I guess.

If the sectors after the PBR of /dev/sda2 has been modified badly, it is very difficult to restore /dev/sda2.
I hope it has not been modified.

Boot with Live CD (mint?) and mount /dev/sda5 to /mnt.
```
sudo mount -t auto /dev/sda5 /mnt -o rw && nautilus /mnt
```If success, file manager (nautilus) opens.
If file manager does not open, do not go ahead.

Backup the (corrupt) current PBR of /dev/sda2 into /mnt (/dev/sda5) with name "sda2pbrbackup".
```
sudo dd if=/dev/sda2 bs=512 count=1 of=/mnt/sda2pbrbackup
```Backup the backup boot sector (at the end of /dev/sda2) into /mnt (/dev/sda5) with name "sda2backupbs".
```
sudo dd if=/dev/sda bs=512 count=1 skip=609892351 of=/mnt/sda2backupbs
```Confirm saving,
```
sudo sync
```Write the saved backup boot sector (/mnt/sda2backupbs) into /dev/sda2 PBR.
```
sudo dd if=/mnt/sda2backupbs bs=512 count=1 of=/dev/sda2
```Confirm saving,
```
sudo sync
```Edit:
I forgot one thing.
To change the filesystem type of /dev/sda2 in partition table in MBR(83) to NTFS(07), execute the following:
```
sudo fdisk /dev/sda
t
2
07
w
```

Confirm saving,
```
sudo sync
```

Shutdown and remove Live CD and reboot.

---

### Post by derik123derik123 on 2011-04-18
> **kiyop said:**
> One problem is that /dev/sda2 is recognized as 83(linux) not 07(ntfs) at partition table in MBR.
Second problem is that the partition boot record of /dev/sda2 is corrupt.

The backup of the former partition boot record of /dev/sda2 seems to have been saved in the last sector of /dev/sda2.
And fortunately, the information on total sectors in the backup:
ff 0f 57 24 (little endian) = 24 57 0f ff =609685503
is same as 
609892351-206848
So, the backup boot sector was saved after /dev/sda3 was formed, I guess.

If the sectors after the PBR of /dev/sda2 has been modified badly, it is very difficult to restore /dev/sda2.
I hope it has not been modified.

Boot with Live CD (mint?) and mount /dev/sda5 to /mnt.
```
sudo mount -t auto /dev/sda5 /mnt -o rw && nautilus /mnt
```If success, file manager (nautilus) opens.
If file manager does not open, do not go ahead.

Backup the (corrupt) current PBR of /dev/sda2 into /mnt (/dev/sda5) with name "sda2pbrbackup".
```
sudo dd if=/dev/sda2 bs=512 count=1 of=/mnt/sda2pbrbackup
```Backup the backup boot sector (at the end of /dev/sda2) into /mnt (/dev/sda5) with name "sda2backupbs".
```
sudo dd if=/dev/sda bs=512 count=1 skip=609892351 of=/mnt/sda2backupbs
```Confirm saving,
```
sudo sync
```Write the saved backup boot sector (/mnt/sda2backupbs) into /dev/sda2 PBR.
```
sudo dd if=/mnt/sda2backupbs bs=512 count=1 of=/dev/sda2
```Confirm saving,
```
sudo sync
```Edit:
I forgot one thing.
To change the filesystem type of /dev/sda2 in partition table in MBR(83) to NTFS(07), execute the following:
```
sudo fdisk /dev/sda
t
2
07
w
```

Confirm saving,
```
sudo sync
```

Shutdown and remove Live CD and reboot.



Thanks for your reply, i really appreciate it. I'll try this when I get home and see what happens.

---

### Post by derik123derik123 on 2011-04-18
> **kiyop said:**
> One problem is that /dev/sda2 is recognized as 83(linux) not 07(ntfs) at partition table in MBR.
Second problem is that the partition boot record of /dev/sda2 is corrupt.

The backup of the former partition boot record of /dev/sda2 seems to have been saved in the last sector of /dev/sda2.
And fortunately, the information on total sectors in the backup:
ff 0f 57 24 (little endian) = 24 57 0f ff =609685503
is same as 
609892351-206848
So, the backup boot sector was saved after /dev/sda3 was formed, I guess.

If the sectors after the PBR of /dev/sda2 has been modified badly, it is very difficult to restore /dev/sda2.
I hope it has not been modified.

Boot with Live CD (mint?) and mount /dev/sda5 to /mnt.
```
sudo mount -t auto /dev/sda5 /mnt -o rw && nautilus /mnt
```If success, file manager (nautilus) opens.
If file manager does not open, do not go ahead.

Backup the (corrupt) current PBR of /dev/sda2 into /mnt (/dev/sda5) with name "sda2pbrbackup".
```
sudo dd if=/dev/sda2 bs=512 count=1 of=/mnt/sda2pbrbackup
```Backup the backup boot sector (at the end of /dev/sda2) into /mnt (/dev/sda5) with name "sda2backupbs".
```
sudo dd if=/dev/sda bs=512 count=1 skip=609892351 of=/mnt/sda2backupbs
```Confirm saving,
```
sudo sync
```Write the saved backup boot sector (/mnt/sda2backupbs) into /dev/sda2 PBR.
```
sudo dd if=/mnt/sda2backupbs bs=512 count=1 of=/dev/sda2
```Confirm saving,
```
sudo sync
```Edit:
I forgot one thing.
To change the filesystem type of /dev/sda2 in partition table in MBR(83) to NTFS(07), execute the following:
```
sudo fdisk /dev/sda
t
2
07
w
```

Confirm saving,
```
sudo sync
```

Shutdown and remove Live CD and reboot.

I love you. it worked perfectly. thank you so much:)

---

