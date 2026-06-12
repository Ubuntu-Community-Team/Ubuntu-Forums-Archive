---
title: "BOOTMGR Missing - Windows XP / 7 + GRUB"
date: 2012-03-15
forum: Any Other OS
---

### Post by palyons on 2012-03-15
Here's the problem, right now I have Windows XP and Windows 7 installed, along with GRUB as the bootloader of choice.

I can boot into Windows 7 just fine--with GRUB, and also into XP using Windows 7's BCD, but when I try to load XP with GRUB, I am presented with BOOTMGR is Missing Press Ctrl+Alt+Del to Restart.

Below is the contents of my results.txt file after running the BootInfo script.

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => No known boot loader is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.
 => Grub Legacy (v0.97) is installed in the MBR of /dev/sdc and looks on the 
    same drive in partition #3 for /grub/stage2 and /grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdd.

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sdc2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Boot/BCD /Windows/System32/winload.exe

sdc3: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/menu.lst

sdc4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sdc5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   According to the info in the boot sector, sdd1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdd1 starts at sector 63.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x20622062

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda2    *         16,065   976,768,064   976,752,000   5 Extended
/dev/sda5              16,128   682,714,304   682,698,177   7 NTFS / exFAT / HPFS
/dev/sda6         682,714,368   976,768,064   294,053,697   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa35b611a

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   625,137,344   625,137,282   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3ea76cd5

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  63    83,923,559    83,923,497   7 NTFS / exFAT / HPFS
/dev/sdc2    *     83,924,992   167,845,887    83,920,896   7 NTFS / exFAT / HPFS
/dev/sdc3         167,847,120   167,863,184        16,065  83 Linux
/dev/sdc4         167,863,246 1,953,520,064 1,785,656,819   5 Extended
/dev/sdc5         167,863,248 1,953,520,064 1,785,656,817   7 NTFS / exFAT / HPFS


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 2032 MB, 2032664576 bytes
255 heads, 63 sectors/track, 247 cylinders, total 3970048 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1                  63     3,970,007     3,969,945   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda5        3BDF1BEB52CE4DF2                       ntfs       
/dev/sda6        31EB7F5D8C5AEB60                       ntfs       Capture
/dev/sdb1        248203A9B3621220                       ntfs       
/dev/sdc1        5680E7E080E7C499                       ntfs       
/dev/sdc2        18F08FD3F08FB592                       ntfs       
/dev/sdc3        8c6929c0-773c-4c60-8b9d-69d15fe227bd   ext3       GRUB
/dev/sdc5        B3828538B32DCA89                       ntfs       
/dev/sdd1        85F8-1DEA                              vfat       UNTITLED

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdd1        /media/UNTITLED          vfat       (rw,nosuid,nodev,uhelper=hal,utf8,shortname=winnt,uid=999)


================================ sdc1/boot.ini: ================================

--------------------------------------------------------------------------------
;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT /USEPMTIMER
--------------------------------------------------------------------------------

============================= sdc3/grub/menu.lst: ==============================

--------------------------------------------------------------------------------
default=0

timeout=60

color cyan/blue white/blue

title Windows 7 Ultimate
rootnoverify (hd0,0)
makeactive
chainloader (hd0,0)+1

title Windows XP Professional
rootnoverify (hd0,1)
makeactive
chainloader (hd0,1)+1
--------------------------------------------------------------------------------

=================== sdc3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             grub/menu.lst
            ?? = ??             grub/stage2
            ?? = ??             vmlinuz-2.6.27-7-generic

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown MBR on /dev/sda

00000000  e8 12 01 b9 f0 01 be 10  7c bf 10 06 57 f3 a4 c3  |........|...W...|
00000010  8b 4e 14 83 f9 0e 75 08  8d 5e 07 43 02 07 e2 fb  |.N....u..^.C....|
00000020  8c 56 0c 8c 56 0e 75 69  8a 56 10 84 d2 79 62 e8  |.V..V.ui.V...yb.|
00000030  f6 00 bb aa 55 cd 13 72  6f 3b 5e 5c 75 6a d1 e9  |....U..ro;^\uj..|
00000040  73 66 b4 42 c6 46 02 01  eb 66 89 b6 f6 fe 8a 44  |sf.B.F...f.....D|
00000050  04 84 c0 74 0f 3c 05 74  0b 3c 0f 74 07 8a 14 80  |...t.<.t.<.t....|
00000060  e2 80 75 cb 83 c6 10 06  c4 5c 08 89 5e 08 8c 46  |..u......\..^..F|
00000070  0a 07 fe 8e f9 fe 75 d2  b0 31 c6 46 d7 50 88 46  |......u..1.F.P.F|
00000080  d4 be 6a 07 ac 84 c0 74  08 b4 0e b3 07 cd 10 eb  |..j....t........|
00000090  f3 e8 81 00 88 46 11 be  ae 07 3c 05 75 c6 cd 16  |.....F....<.u...|
000000a0  33 d2 89 56 08 89 56 0a  e8 7d 00 72 1b b8 01 02  |3..V..V..}.r....|
000000b0  bf 05 00 8b dc 56 50 50  32 e4 cd 13 58 8b f5 cd  |.....VPP2...X...|
000000c0  13 58 5e 73 03 4f 75 eb  b0 32 72 b2 40 8a 66 11  |.X^s.Ou..2r.@.f.|
000000d0  9e 7b 04 c6 47 02 0e 72  35 75 0c 88 57 40 c4 4e  |.{..G..r5u..W@.N|
000000e0  08 89 4f 1c 8c 47 1e 79  06 8a 4e 12 88 4f 25 80  |..O..G.y..N..O%.|
000000f0  c7 02 81 7f fe 55 aa 75  85 81 7f fa cd 19 75 09  |.....U.u......u.|
00000100  c6 47 fa e9 c7 47 fb 94  88 e8 1c 00 ff e4 74 ce  |.G...G........t.|
00000110  88 57 24 eb c9 5d 33 c0  8e d8 8e c0 8e d0 bc 00  |.W$..]3.........|
00000120  7c 55 bd a2 07 fc fb c3  b4 08 52 06 cd 13 07 72  ||U........R....r|
00000130  33 33 db 8a de 8b 46 0a  33 d2 83 e1 3f f7 f1 91  |33....F.3...?...|
00000140  97 8b 46 08 f7 f7 42 87  ca 3b da 72 17 43 f7 f3  |..F...B..;.r.C..|
00000150  8a f2 86 c5 d1 e8 d1 e8  0a c8 d0 cc d0 cc 0a f4  |................|
00000160  84 e4 74 02 b4 41 5b 8a  d3 c3 0d 0a 4d 42 52 20  |..t..A[.....MBR |
00000170  45 72 72 6f 72 20 00 0d  0a 00 72 65 73 73 20 61  |Error ....ress a|
00000180  6e 79 20 6b 65 79 20 74  6f 20 62 6f 6f 74 20 66  |ny key to boot f|
00000190  72 6f 6d 20 66 6c 6f 70  70 79 2e 2e 2e 00 00 00  |rom floppy......|
000001a0  00 00 10 00 01 00 00 7c  00 00 00 00 00 00 00 00  |.......|........|
000001b0  00 00 00 00 00 00 00 00  62 20 62 20 00 00 00 00  |........b b ....|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 80 00  |................|
000001d0  01 01 05 fe ff ff c1 3e  00 00 80 0d 38 3a 00 00  |.......>....8:..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sdd1

00000000  eb 58 90 42 53 44 20 20  34 2e 34 00 02 08 20 00  |.X.BSD  4.4... .|
00000010  02 00 00 00 00 f0 00 00  20 00 ff 00 00 00 00 00  |........ .......|
00000020  99 93 3c 00 1e 0f 00 00  00 00 00 00 02 00 00 00  |..<.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 ea 1d f8 85 55  4e 54 49 54 4c 45 44 20  |..)....UNTITLED |
00000050  20 20 46 41 54 33 32 20  20 20 fa 31 c0 8e d0 bc  |  FAT32   .1....|
00000060  00 7c fb 8e d8 e8 00 00  5e 83 c6 19 bb 07 00 fc  |.|......^.......|
00000070  ac 84 c0 74 06 b4 0e cd  10 eb f5 30 e4 cd 16 cd  |...t.......0....|
00000080  19 0d 0a 4e 6f 6e 2d 73  79 73 74 65 6d 20 64 69  |...Non-system di|
00000090  73 6b 0d 0a 50 72 65 73  73 20 61 6e 79 20 6b 65  |sk..Press any ke|
000000a0  79 20 74 6f 20 72 65 62  6f 6f 74 0d 0a 00 00 00  |y to reboot.....|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by sp-1070 on 2012-03-16
I have no real idea of the problem or its answer but you should take a look here [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) maybe join the forum and ask around.

---

### Post by palyons on 2012-03-16
I just tried those programs, and unfortunately, they are completely useless, doesn't really solve my problem at all.

---

### Post by YannBuntu on 2012-03-16
Hello paylons,
1) Your system does not contain any Ubuntu. 
2) You're trying to use an obsolete version of GRUB.

If 1) is on purpose, you should ask help on Windows forums.
If not, you should backup your documents and reinstall an up-to-date Ubuntu.

---

### Post by palyons on 2012-03-16
> **YannBuntu said:**
> Hello paylons,
1) Your system does not contain any Ubuntu. 
2) You're trying to use an obsolete version of GRUB.

If 1) is on purpose, you should ask help on Windows forums.
If not, you should backup your documents and reinstall an up-to-date Ubuntu.

Yes, you are right, there is no form of Ubuntu installed at all on my system, I just wish to use the bootloader, but I have seen another thread very similar to this one, on this forum from 3 years ago. But unfortunately, I wasn't really able to solve my solution using that thread either.

---

### Post by LostFarmer on 2012-03-16
That is normal.  When you install Win7 it  wrote its boot files on to the XP's partition and wrote 7's boot code to it.  

I do not use win7,  you would need win7 to write its boot info on its own partition. Only after fixing win7 'NOT before' then boot into XP's recovery console and run 'fixboot'.

---

### Post by oldfred on 2012-03-16
Moved to other OS sub forum.

Easier to do when you install, but you may be able to repair your installs.

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

Make Windows repairCD/USB.
Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

I have used my Windows 7 repair USB to run chkdsk on my XP install, but it then put a Windows 7 boot sector in my XP install, so I ran the repairs to fix the boot sector.

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors - Use diskpart, then list volumes to see which drive to use 
bootsect.exe /nt52 c:  *compatible* with operating systems older (XP) than Windows Vista.
bootsect.exe /nt60 c:  *compatible* with Windows Vista, Windows Server 2008 or later

Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe

---

