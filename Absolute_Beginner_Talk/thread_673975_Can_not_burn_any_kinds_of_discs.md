---
title: "Can not burn any kinds of discs"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by chaulkster on 2008-01-21
Good day,

I have switched to Ubuntu about a month ago (best computing decision I ever made). However, there are a few issues.

The one that’s really bothering me right now is that I cannot burn any sort of disc. Either is be a DVD or a CD or any sort of thing it will not burn it. It will read them, but will not burn it.


Here’s what happens:

The drive with spin up and it will recognize that there is a blank disc in the drive. I add my contents to the disc and try to write it. The drive spins up again and the light on the drive starts flashing. Ubuntu will prep the disc but then it will just hang. The computer will not freeze up but the mouse will just seemingly refresh VERY slow and nothing responds unless you wait a bout 30 seconds or so.  The drive keeps spinning the disc with the light flashing until you restart the computer.

Does anyone have any ideas? I really need to get this working. 

Thank you very much.

---

### Post by Sef on 2008-01-21
1) I wonder if your burner is bad.

2) What do you use for burning?

3) Try another burn software.   I use gnomebaker.  Also k3b is popular.  Both are available from Add/Remove.

---

### Post by hyper_ch on 2008-01-21
What program did you try to burn with?

I normally use K3B which works just fine.

---

### Post by minnielion on 2008-02-03
I'm having a very similar issue.  I can sometimes burn CD-R media, but can no longer burn CD-RW or DVD-RW media.  Regardless of which software I use, it's always the same outcome -- starts the write, but within a few seconds the mouse starts lagging (it eventually moves, but only after about 5 second delay).   

I  just started noticing this within the past few days and had not run into this previously.  I'm currently running gutsy/  7.10 (2.6.22-14-386 #1 Tue Dec 18 07:34:24 UTC 2007 i686 GNU/Linux) with an HP dvd740 lightscribe drive.  

There are errors in my log files.  Here are some snippets, please let me know what additional information would be helpful:

kern.log:

Feb  3 10:13:58 xxxxxx kernel: [ 6330.736000] hdd: status timeout: status=0xc0 { Busy }
Feb  3 10:13:58 xxxxxx kernel: [ 6330.736000] ide: failed opcode was: unknown
Feb  3 10:13:58 xxxxxx kernel: [ 6330.736000] hdd: drive not ready for command
Feb  3 10:21:50 xxxxxx kernel: [ 6802.540000] UDF-fs: No VRS found
Feb  3 10:21:50 xxxxxx kernel: [ 6802.600000] ISO 9660 Extensions: Microsoft Joliet Level 3
Feb  3 10:21:50 xxxxxx kernel: [ 6802.604000] ISO 9660 Extensions: RRIP_1991A

messages:

Feb  3 10:13:58 xxxxxx kernel: [ 6330.736000] hdd: status timeout: status=0xc0 { Busy }
Feb  3 10:13:58 xxxxxx kernel: [ 6330.736000] ide: failed opcode was: unknown
Feb  3 10:21:50 xxxxxx kernel: [ 6802.540000] UDF-fs: No VRS found
Feb  3 10:23:01 xxxxxx kernel: [ 6874.176000] UDF-fs: No VRS found

syslog:

Feb  3 10:13:58 xxxxxx kernel: [ 6330.736000] hdd: status timeout: status=0xc0 { Busy }
Feb  3 10:13:58 xxxxxx kernel: [ 6330.736000] ide: failed opcode was: unknown
Feb  3 10:13:58 xxxxxx kernel: [ 6330.736000] hdd: drive not ready for command


~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51G [GeForce 6100] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.2 Multimedia audio controller: nVidia Corporation MCP51 AC97 Audio Controller (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:06.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)

~$ sudo hdparm /dev/hdd

/dev/hdd:
 IO_support    =  1 (32-bit)
 unmaskirq     =  1 (on)
 using_dma     =  1 (on)
 keepsettings  =  0 (off)
 readonly      =  0 (off)
 readahead     = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

~$ sudo hdparm /dev/hdd

:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda6
UUID=cea5ab2a-81c0-40c5-8113-5cf4d3ca641b /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda7
UUID=350f1c6f-e090-428e-b851-f51444e95695 /home           ext3    defaults        0       2
# /dev/hda9
UUID=4f62c9e0-7735-4984-9a31-21d4038f88d9 /usr            ext3    defaults        0       2
# /dev/hda8
UUID=6b8f7485-cf21-4b58-bae9-b3401571062a /var            ext3    defaults        0       2
# /dev/hda5
UUID=30c70e71-ee9c-4643-89e9-8d127ec7ba8b none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


Any help would be greatly appreciated.

---

### Post by bakermiller on 2008-02-04
I've had the same problem all day, i lost 2 disks. I finally got it working by going System >>  preferences >> removable drives and media >> and unselecting the "burn a cd when a blank disc is inserted" button. I get it must be a problem with the  way nautilus-cd-burner handles blank CD/DVDs, but i have no idea what i'm talking about. 

then i used Gnomebaker and it works fine at great speed.

---

