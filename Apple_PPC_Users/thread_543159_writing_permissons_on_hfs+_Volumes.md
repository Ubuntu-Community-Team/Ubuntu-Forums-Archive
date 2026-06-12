---
title: "writing permissons on hfs+ Volumes"
date: 2007-09-04
forum: Apple PPC Users
---

### Post by frog_pilot on 2007-09-04
Hi there,

I've installed the packages 'hfsplus' and 'hfsutils'. Then I created 2 Partitioms under MAC OSX on the Harddrive, where Ubuntu is installed. With Macintosh extended (Journaled) filesystem. Then I turned of the journalling with OSX's diskutil.

Under Ubuntu I added the Lines```
# /dev/hdc7
UUID=85AAAB80C93A6DAF /media/data     hfsplus    rw,user,auto        0       2
# /dev/hdc6
UUID=E23F74EE3B949781 /media/musik    hfsplus    rw,user,auto        0       2
```to my /etc/fstab
Now I can mount the volumes and access the data, but when I try to```
sudo mkdir /media/data/LINUX
```i get the message```
mkdir: can't create folder &#8222;/media/data/LINUX&#8220; : Read-only file system
```What the hell is the matter here??? :confused:
Any help appreciated.

---

### Post by simonn on 2007-09-04
Linux does not support writing to journaled HFS+ volumes, see [http://gentoo-wiki.com/HOWTO_hfsplus#Disable_Journaling](http://gentoo-wiki.com/HOWTO_hfsplus#Disable_Journaling)

---

### Post by frog_pilot on 2007-09-05
> **frog_pilot said:**
> Then I turned off the journalling with OSX's diskutil.this way```
cd /Volumes/
sudo diskutil disableJournal data/
sudo diskutil disableJournal musik/
```Isn't it sufficient? Or is formatting these partitions with "Macintosh extended" without journalling the better choice?

---

### Post by frog_pilot on 2007-09-13
the problem remains after formatting the drives with "macintosh extended" filesystem without journalling.

I have the mount-options mentioned above in my /etc/fstab

but when right-click on the drives and look on the "properties"-Volume-Tab, it tells me the mount-options ro nosuid nodev noexec umask=22 uid=0 gid=0 nls=utf8.

Please help me find the right options to write on these volumes... :confused:

---

### Post by frog_pilot on 2007-09-13
there is some information, I can add here

The partitions were mounted as rw, i think last time, i booted up in linux. After this Iadded some files and folders under OS X. When I booted back to linux, I had this problem, that the volumes in hfs+ (unjournaled) were mounted as ro. I didn't want to change the ownership of my mountpoint. Thats why I created a folder on eych hfs+ volume as root and passed it to my user with chown. Then I had access to these folders. Now, after rebooting it is impossible.

ls -la shows```
drwxr-xr-x 14 root  root  4096 2007-09-13 18:32 .
drwxr-xr-x 21 root  root  4096 2007-09-01 23:24 ..
lrwxrwxrwx  1 root  root     6 2007-09-01 21:34 cdrom -> cdrom0
drwxr-xr-x  2 root  root  4096 2007-09-01 21:34 cdrom0
drwxr-xr-x  2 root  root  4096 2007-09-01 21:34 cdrom1
[COLOR="MediumTurquoise"]drwxr-xr-x  1   501   501   14 2007-09-13 11:56 data[/COLOR] [COLOR="MediumTurquoise"]internal drive[/COLOR]
[COLOR="Red"]drwxrwx--- 11 mpunk mpunk 4096 2007-09-01 12:53 ext_data
drwxrwxrwx  1 mpunk mpunk 4096 2007-09-13 18:21 ext_ntfs[/COLOR] [COLOR="Red"]usb-drive[/COLOR]
[COLOR="YellowGreen"]drwxr-xr-x  2 root  root  4096 2007-08-30 01:07 fiwiboot[/COLOR]
-rw-r--r--  1 root  root     0 2007-09-13 18:32 .hal-mtab
----------  1 root  root     0 2007-09-01 23:32 .hal-mtab-lock
drwxr-xr-x  2 root  root  4096 2007-08-21 22:05 icke
[COLOR="YellowGreen"]drwxr-xr-x  1 root  root     9 2007-09-05 18:44 LIN_DATA
drwxr-xr-x  1 root  root    15 2007-09-06 22:58 MAC_DATA[/COLOR] [COLOR="YellowGreen"]firewire-drive[/COLOR]
[COLOR="MediumTurquoise"]drwxr-xr-x  1   501   501   20 2007-09-13 08:37 musik[/COLOR]
[COLOR="YellowGreen"]drwxr-xr-x  2 root  root  4096 2007-08-30 01:07 OS_X_live[/COLOR]
drwxrwxr-t  1 root     80   31 2007-09-12 22:40 PowerMAC_G4_Dual <--- MAC-HD
```
501 is the ID of my OS X-User

fdisk -l shows```
/dev/sdb
        #                    type name                  length   base      ( size )  system
/dev/sdb1     Apple_partition_map Apple                     63 @ 1         ( 31.5k)  Partition map
/dev/sdb2              Apple_Free                       262144 @ 64        (128.0M)  Free space
/dev/sdb3               Apple_HFS Apple_HFS_Untitled_1  61115480 @ 262208    ( 29.1G)  HFS
/dev/sdb4              Apple_Free                       262144 @ 61377688  (128.0M)  Free space
/dev/sdb5               Apple_HFS Apple_HFS_Untitled_2 281620264 @ 61639832  (134.3G)  HFS
/dev/sdb6              Apple_Boot eXternal booter        17408 @ 343260096 (  8.5M)  Unknown
/dev/sdb7               Apple_HFS Apple_UFS_Untitled_3 281864928 @ 343277504 (134.4G)  HFS
/dev/sdb8              Apple_Free                           16 @ 625142432 (  8.0k)  Free space

Block size=512, Number of Blocks=625142448
DeviceType=0x0, DeviceId=0x0

/dev/hda
        #                    type name                  length   base      ( size )  system
/dev/hda1     Apple_partition_map Apple                     63 @ 1         ( 31.5k)  Partition map
/dev/hda2              Apple_Free                       262144 @ 64        (128.0M)  Free space
/dev/hda3               Apple_HFS Apple_HFS_Untitled_1 125566976 @ 262208    ( 59.9G)  HFS
/dev/hda4              Apple_Free                    194343872 @ 125829184 ( 92.7G)  Free space

Block size=512, Number of Blocks=320173056
DeviceType=0x0, DeviceId=0x0

/dev/hdc
        #                    type name                  length   base      ( size )  system
/dev/hdc1     Apple_partition_map Apple                     63 @ 1         ( 31.5k)  Partition map
/dev/hdc2         Apple_Bootstrap untitled                1954 @ 64        (977.0k)  NewWorld bootblock
/dev/hdc3         Apple_UNIX_SVR2 untitled            25390626 @ 2018      ( 12.1G)  Linux native
/dev/hdc4         Apple_UNIX_SVR2 swap                 3906251 @ 25392644  (  1.9G)  Linux swap
/dev/hdc5         Apple_UNIX_SVR2 icke                58593751 @ 29298895  ( 27.9G)  Linux native
/dev/hdc6               Apple_HFS musik              107421876 @ 87892646  ( 51.2G)  HFS
/dev/hdc7               Apple_HFS data               195407446 @ 195314522 ( 93.2G)  HFS

Block size=512, Number of Blocks=390721968
DeviceType=0x0, DeviceId=0x0
```

I don't know, why my ext-usb-drive isn't shown here. I think its sda. And it's mounted...
I have no idea...
Thanks in advance for your help!

P.S. this is my fstab```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc3
UUID=8174cabb-729b-4d48-a9cf-eabc9daaabd0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdc5
UUID=49113163-0298-45cb-a0ea-c495edebf68f /home           ext3    defaults        0       2
# /dev/hdc7
UUID=BB5C942E1789083E /media/data     hfsplus    rw,user,auto        0       0
# /dev/hdc6
UUID=412541B255721801 /media/musik    hfsplus    rw,user,auto        0       0
# /dev/hdc4
UUID=6243acc9-9bdd-4444-ba03-bf2c296d8b06 none            swap    sw              0       0
/dev/hde        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdf        /media/cdrom1   udf,iso9660 user,noauto     0       0

# /dev/hda3
UUID=FFD002618E914F10   /media/PowerMAC_G4_Dual   hfsplus  ro,user,auto 	0    0

# External Drives
# USB
# /dev/sda1
UUID=24942821-cc0d-4ca3-8528-bcc951f86ce8 /media/ext_data        ext3    rw,users,noauto        0       0
# /dev/sda2
UUID=66E444A632ECD092   /media/ext_ntfs  ntfs-3g  noauto,users,uid=1000,gid=1000,locale=de_DE.utf8    0    0
# 
# FIREWIRE
# /dev/sdb6
UUID=31B1F9FB83C3480B   /media/fiwiboot   hfsplus  ro,users,noauto 	0    0
# /dev/sdb3
UUID=46492E39859A1DEB   /media/OS_X_live   hfsplus  ro,users,noauto 	0    0
# /dev/sdb5
UUID=EC58742925CDF13E   /media/MAC_DATA   hfsplus  ro,users,noauto 	0    0
# /dev/sdb7
UUID=91C11029794170B4   /media/LIN_DATA   hfsplus  rw,users,noauto 	0    0
## End of External Drives
```

---

### Post by stmiller on 2007-09-13
Hm. Looks like you have everything right. The hfsplus utilities Ubuntu provides may not not have 100% write support, possibly. I've always compiled my own kernel, and enabled hfs+ read/write there.  Might try to hunt down the documentation for those hfs utility packages and try to see exactly what they support.

---

### Post by simonn on 2007-09-14
what does dmesg say when you try and mount the partitions?

---

### Post by frog_pilot on 2007-09-14
with ```
dmesg
```every time after adding a volume in hfs+-format (without journaling) there comes this message ```
[   58.279868] hfs: write access to a jounaled filesystem is not supported, use the force option at your own risk, mounting read-only.
```

e.g. when I plug my firewire-drive```
[  254.594142] ieee1394: Node added: ID:BUS[0-00:1023]  GUID[00d04b7610064823]
[  254.598473] scsi1 : SBP-2 IEEE-1394
[  255.605024] ieee1394: sbp2: Logged into SBP-2 device
[  255.605272] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[  255.607381] scsi 1:0:0:0: Direct-Access-RBC ST332082 0A               3.AA PQ: 0 ANSI: 4
[  255.612358] SCSI device sdb: 625142448 512-byte hdwr sectors (320073 MB)
[  255.612920] sdb: Write Protect is off
[  255.612926] sdb: Mode Sense: 11 00 00 00
[  255.614222] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  255.615153] SCSI device sdb: 625142448 512-byte hdwr sectors (320073 MB)
[  255.615717] sdb: Write Protect is off
[  255.615722] sdb: Mode Sense: 11 00 00 00
[  255.617071] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  255.617079]  sdb: [mac] sdb1 sdb2 sdb3 sdb4 sdb5 sdb6 sdb7 sdb8
[  255.630191] sd 1:0:0:0: Attached scsi disk sdb
[  255.630252] sd 1:0:0:0: Attached scsi generic sg1 type 14
[  265.613282] hfs: write access to a jounaled filesystem is not supported, use the force option at your own risk, mounting read-only.
```

and another problem
when I plug my firewire-drive or my usb drive. the drives don't come up to the desktop. I have to mount them manually on a terminal as root ```
sudo mount /media/<drive>
```

my /etc/modules```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

snd-i2c
snd-pcm
snd-seq
snd-powermac
apm_emu
sbp2
therm_windtunnel
fuse
```

---

### Post by simonn on 2007-09-19
> **frog_pilot said:**
> ```

[  265.613282] hfs: write access to a jounaled filesystem is not supported, use the force option at your own risk, mounting read-only.
```

Linux does not support writing to journaled HFS+ volumes, see [http://gentoo-wiki.com/HOWTO_hfsplus#Disable_Journaling](http://gentoo-wiki.com/HOWTO_hfsplus#Disable_Journaling)

---

### Post by frog_pilot on 2007-09-20
I know that... thats why i formatted the hfs-volumes without journal, as I said many times in this very thread... :popcorn:

And now I know the problem. It was an OS X issue: Because of software-problems in OS X I couldn't shut down tidily and had to do a hardreset for turnig the computer off. Now I solved these problems and the volumes will mount in ubuntu again with the rw-option.

It seems, that ubuntu can't mount hfs-volums with the rw-options when OSX didn't shut down or logged off tidily. This behaviour is very frustrating. It took a very long time to find out what is happening here. I think sharing huge amounts of data between ubuntu and OSX isn't such a good deal. I wanted to access my whole music and film library from both OS's, about 150GB. But when there is no possibility from ubuntu to write to the hfs-volumes, then you can't access any data from OS X... Maybe an NFS-solution is the best choice...

I'm looking forward to the day when I can erase my OS X volume :guitar:


btw
I think the dmesg-message on which simonn reflected is a standard message, that comes every time when you mount a hfs-volume.

---

### Post by frog_pilot on 2007-09-20
also with ubuntu there is the problem, when the computer crashs during writing on one hfs+-volume, what is happening frequently. On restart, als the hfs+-Volumes will mount read only. I think, now I have to restart OS X to solve this Problem

aarrrghh

---

### Post by simonn on 2007-09-20
Mate the dmesg error indicates that the volume is journalled - end of story! Did you use diskutil disableJournal volumeName in OSX as the documentation I pointed you towards states?

I can almost guarantee you that OSX is reenabling journalling on a reboot because you have not done the above.

---

### Post by frog_pilot on 2007-09-20
> **frog_pilot said:**
> I know that... thats why i formatted the hfs-volumes without journal, as I said many times in this very thread... :popcorn:

And now I know the problem. It was an OS X issue: Because of software-problems in OS X I couldn't shut down tidily and had to do a hardreset for turnig the computer off. Now I solved these problems and the volumes will mount in ubuntu again with the rw-option.

It seems, that ubuntu can't mount hfs-volums with the rw-options when OSX didn't shut down or logged off tidily. This behaviour is very frustrating. It took a very long time to find out what is happening here. I think sharing huge amounts of data between ubuntu and OSX isn't such a good deal. I wanted to access my whole music and film library from both OS's, about 150GB. But when there is no possibility from ubuntu to write to the hfs-volumes, then you can't access any data from OS X... Maybe an NFS-solution is the best choice...

I'm looking forward to the day when I can erase my OS X volume :guitar:


btw
I think the dmesg-message on which simonn reflected is a standard message, that comes every time when you mount a hfs-volume.

First i used diskutil to turn off the journal.

On my second attempt I formatted with macintosh extended without journal.

Cocktail shows the volumes formatted without journaling as "Journaling disabeled".  And when you only belive in terminal-messages:```
m-puns-power-mac-g4:/Volumes mpunk$ sudo diskutil disableJournal musik 
Journaling was already disabled on the volume
```
Belive me, this was one of the first points I became aware of when starting with ubuntu on mac.  And I made really sure not to write on journaled hfs+-volumes when I didn't even suspect the problems relating java, flash etc.

dmesg shows this message every time. I suppose it is only a warning, similar to the ntfs-3g warning, when you mount a ntfs-drive. "Enter at your own risk" do not mean somebody may not be able to walk there..

Unfortunately I'm working just now in OS X. But soon I will show you the dmesg-output with all possible HFS+Volumes plugged and hopefully writable mounted ;)

---

### Post by frog_pilot on 2007-09-21
> **simonn said:**
> Mate the dmesg error indicates that the volume is journalled - end of story!

Ok and now from ubuntu
```
mpunk@PUNIX-G4:~$ dmesg
[    0.000000] Using PowerMac machine description
[    0.000000] Total memory = 2048MB; using 4096kB for hash table (at cfc00000)
[    0.000000] Linux version 2.6.20-16-powerpc-smp (root@royal) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #3 SMP Thu Aug 30 23:46:34 UTC 2007 (Ubuntu 2.6.20-16.31-powerpc-smp)
[    0.000000] Found initrd at 0xc1900000:0xc2066000
[    0.000000] Found UniNorth memory controller & host bridge @ 0xf8000000 revision: 0x24
[    0.000000] Mapped at 0xfdfc0000
[    0.000000] Found a Keylargo mac-io controller, rev: 3, mapped at 0xfdf40000
[    0.000000] PowerMac motherboard: PowerMac G4 Windtunnel
[    0.000000] Entering add_active_range(0, 0, 524288) 0 entries of 256 used
[    0.000000] Found UniNorth PCI host bridge at 0x00000000f0000000. Firmware bus number: 0->0
[    0.000000] Found UniNorth PCI host bridge at 0x00000000f2000000. Firmware bus number: 0->0
[    0.000000] Found UniNorth PCI host bridge at 0x00000000f4000000. Firmware bus number: 0->0
[    0.000000] via-pmu: Server Mode is disabled
[    0.000000] PMU driver v2 initialized for Core99, firmware: 0c
[    0.000000] nvram: Checking bank 0...
[    0.000000] nvram: gen0=704, gen1=705
[    0.000000] nvram: Active bank is: 1
[    0.000000] nvram: OF partition at 0x410
[    0.000000] nvram: XP partition at 0x1020
[    0.000000] nvram: NR partition at 0x1120
[    0.000000] Top of RAM: 0x80000000, Total RAM: 0x80000000
[    0.000000] Memory hole size: 0MB
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->   196608
[    0.000000]   Normal     196608 ->   196608
[    0.000000]   HighMem    196608 ->   524288
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   524288
[    0.000000] On node 0 totalpages: 524288
[    0.000000]   DMA zone: 1536 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 195072 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   HighMem zone: 2560 pages used for memmap
[    0.000000]   HighMem zone: 325120 pages, LIFO batch:31
[    0.000000] Built 1 zonelists.  Total pages: 520192
[    0.000000] Kernel command line: root=/dev/hdc3 ro quiet splash 
[    0.000000] mpic: Setting up MPIC " MPIC 1   " version 1.2 at 80040000, max 4 CPUs
[    0.000000] mpic: ISU size: 64, shift: 6, mask: 3f
[    0.000000] mpic: Initializing for 64 sources
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] GMT Delta read from XPRAM: 60 minutes, DST: off
[    0.000000] time_init: decrementer frequency = 41.659214 MHz
[    0.000000] time_init: processor frequency   = 1249.999995 MHz
[   47.864738] Console: colour dummy device 80x25
[   47.865463] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   47.866261] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   48.009592] High memory: 1310720k
[   48.009600] Memory: 2062700k/2097152k available (3368k kernel code, 1344036k reserved, 124k data, 286k bss, 204k init)
[   48.009817] Calibrating delay loop... 83.20 BogoMIPS (lpj=166400)
[   48.092581] Security Framework v1.0.0 initialized
[   48.092601] SELinux:  Disabled at boot.
[   48.092630] Mount-cache hash table entries: 512
[   48.092917] device-tree: Duplicate name in /cpus/PowerPC,G4@0/l2-cache, renamed to "l2-cache#1"
[   48.092961] device-tree: Duplicate name in /cpus/PowerPC,G4@0, renamed to "l2-cache#1"
[   48.093017] device-tree: Duplicate name in /cpus/PowerPC,G4@1/l2-cache, renamed to "l2-cache#1"
[   48.093056] device-tree: Duplicate name in /cpus/PowerPC,G4@1, renamed to "l2-cache#1"
[   48.094753] PowerMac SMP probe found 2 cpus
[   48.094850] KeyWest i2c @0xf8001003 irq 42 /uni-n@f8000000/i2c@f8001000
[   48.094859]  channel 0 bus <multibus>
[   48.094863]  channel 1 bus <multibus>
[   48.094883] KeyWest i2c @0x80018000 irq 26 /pci@f2000000/mac-io@17/i2c@18000
[   48.094888]  channel 0 bus <multibus>
[   48.094896] PMU i2c /pci@f2000000/mac-io@17/via-pmu@16000/pmu-i2c
[   48.094902]  channel 1 bus <multibus>
[   48.094905]  channel 2 bus <multibus>
[   48.094917] pmf: no parser for command 17 !
[   48.094947] Processor timebase sync using GPIO 0x73
[   48.094952] mpic: requesting IPIs ... 
[   48.094975] CPU0: L2CR is 80000000
[   48.094978] CPU0: L3CR is 9c030000
[    0.276657] CPU1: L2CR was 0
[    0.276682] CPU1: L2CR set to 80000000
[    0.276686] CPU1: L3CR was 0
[    0.276848] CPU1: L3CR set to 9c030000
[   48.096204] Processor 1 found.
[   48.098237] Brought up 2 CPUs
[   49.816276] migration_cost=21114
[   49.819100] NET: Registered protocol family 16
[   49.819491] PCI: Probing PCI hardware
[   49.823487] NET: Registered protocol family 8
[   49.823493] NET: Registered protocol family 20
[   49.824062] NET: Registered protocol family 2
[   49.860604] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   49.860921] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   49.864731] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   49.866674] TCP: Hash tables configured (established 131072 bind 65536)
[   49.866679] TCP reno registered
[   49.876782] checking if image is initramfs... it is
[   50.765510] Freeing initrd memory: 7576k freed
[   50.766177] Thermal assist unit not available
[   50.766653] audit: initializing netlink socket (disabled)
[   50.766677] audit(1190359564.900:1): initialized
[   50.766785] highmem bounce pool size: 64 pages
[   50.770558] VFS: Disk quotas dquot_6.5.1
[   50.770593] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   50.770694] io scheduler noop registered
[   50.770700] io scheduler anticipatory registered
[   50.770704] io scheduler deadline registered
[   50.770727] io scheduler cfq registered (default)
[   50.771369] PCI: Enabling device 0000:00:10.0 (0086 -> 0087)
[   50.968685] radeonfb: Found Open Firmware ROM Image
[   50.968695] radeonfb: Retrieved PLL infos from Open Firmware
[   50.968700] radeonfb: Reference=27.00 MHz (RefDiv=12) Memory=250.00 Mhz, System=275.00 MHz
[   50.968705] radeonfb: PLL min 12000 max 35000
[   51.232494] radeonfb: Monitor 1 type CRT found
[   51.232499] radeonfb: EDID probed
[   51.232503] radeonfb: Monitor 2 type CRT found
[   51.232506] radeonfb: EDID probed
[   51.250393] Console: switching to colour frame buffer device 90x25
[   51.256222] radeonfb (0000:00:10.0): ATI Radeon If 
[   51.301350] Generic RTC Driver v1.07
[   51.301430] Macintosh non-volatile memory driver v1.1
[   51.301599] mice: PS/2 mouse device common for all mice
[   51.302705] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   51.303176] MacIO PCI driver attached to Keylargo chipset
[   51.304767] input: Macintosh mouse button emulation as /class/input/input0
[   51.305024] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   51.305032] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   51.305127] adb: starting probe task...
[   51.305136] adb: finished probe task...
[   51.305204] PCI: Enabling device 0002:20:0d.0 (0004 -> 0006)
[   52.324489] ide0: Found Apple UniNorth ATA-6 controller, bus ID 3, irq 39
[   52.324507] Probing IDE interface ide0...
[   52.612667] hda: Maxtor 6Y160P0, ATA DISK drive
[   53.284489] hda: Enabling Ultra DMA 5
[   53.285542] ide0 at 0xf1022000-0xf1022007,0xf1022160 on irq 39
[   54.304476] ide1: Found Apple KeyLargo ATA-4 controller, bus ID 2, irq 19
[   54.304489] Probing IDE interface ide1...
[   54.592761] hdc: SAMSUNG SP2014N, ATA DISK drive
[   55.264473] hdc: Enabling Ultra DMA 4
[   55.265512] ide1 at 0xf1012000-0xf1012007,0xf1012160 on irq 19
[   56.284465] ide2: Found Apple KeyLargo ATA-3 controller, bus ID 0, irq 20
[   56.284478] Probing IDE interface ide2...
[   56.684627] hde: TOSHIBA DVD-ROM SD-R1312, ATAPI CD/DVD-ROM drive
[   57.132623] hdf: _NEC DVD_RW ND-1300A, ATAPI CD/DVD-ROM drive
[   57.188464] hde: Enabling MultiWord DMA 2
[   57.189474] hdf: Enabling MultiWord DMA 2
[   57.190509] ide2 at 0xf101e000-0xf101e007,0xf101e160 on irq 20
[   57.190838] PowerMac i2c bus pmu 2 registered
[   57.190910] PowerMac i2c bus pmu 1 registered
[   57.190984] PowerMac i2c bus mac-io 0 registered
[   57.191066] PowerMac i2c bus uni-n 1 registered
[   57.191141] PowerMac i2c bus uni-n 0 registered
[   57.191304] TCP cubic registered
[   57.191321] NET: Registered protocol family 1
[   57.191496] input: PMU as /class/input/input1
[   57.191531] Freeing unused kernel memory: 204k init
[   59.310586] Capability LSM initialized
[   61.009801] ieee1394: Initialized config rom entry `ip1394'
[   61.013923] PCI: Enabling device 0002:20:0e.0 (0000 -> 0002)
[   61.065484] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[40]  MMIO=[f5000000-f50007ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[   61.078585] usbcore: registered new interface driver usbfs
[   61.078629] usbcore: registered new interface driver hub
[   61.078694] usbcore: registered new device driver usb
[   61.080929] PCI: Enabling device 0001:10:15.2 (0004 -> 0006)
[   61.080946] ehci_hcd 0001:10:15.2: EHCI Host Controller
[   61.081142] ehci_hcd 0001:10:15.2: new USB bus registered, assigned bus number 1
[   61.083322] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   61.104021] hda: max request size: 512KiB
[   61.106476] ehci_hcd 0001:10:15.2: irq 58, io mem 0x80080000
[   61.106487] ehci_hcd 0001:10:15.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   61.106701] usb usb1: configuration #1 chosen from 1 choice
[   61.106753] hub 1-0:1.0: USB hub found
[   61.106770] hub 1-0:1.0: 5 ports detected
[   61.135756] hda: 320173056 sectors (163928 MB) w/7936KiB Cache, CHS=19929/255/63, UDMA(100)
[   61.141383] hda: cache flushes supported
[   61.141468]  hda: [mac] hda1 hda2 hda3 hda4
[   61.156603] hdc: max request size: 512KiB
[   61.167481] hdc: 390721968 sectors (200049 MB) w/8192KiB Cache, CHS=24321/255/63, UDMA(66)
[   61.172583] hdc: cache flushes supported
[   61.172655]  hdc: [mac] hdc1 hdc2 hdc3 hdc4 hdc5 hdc6 hdc7
[   61.211414] PCI: Enabling device 0001:10:15.0 (0000 -> 0002)
[   61.211441] ohci_hcd 0001:10:15.0: OHCI Host Controller
[   61.211501] ohci_hcd 0001:10:15.0: new USB bus registered, assigned bus number 2
[   61.211525] ohci_hcd 0001:10:15.0: irq 58, io mem 0x80084000
[   61.258444] hde: ATAPI 32X DVD-ROM CD-R/RW drive, 2048kB Cache, (U)DMA
[   61.258463] Uniform CD-ROM driver Revision: 3.20
[   61.286302] usb usb2: configuration #1 chosen from 1 choice
[   61.286355] hub 2-0:1.0: USB hub found
[   61.286370] hub 2-0:1.0: 3 ports detected
[   61.295707] hdf: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, (U)DMA
[   61.391037] PCI: Enabling device 0001:10:15.1 (0000 -> 0002)
[   61.391067] ohci_hcd 0001:10:15.1: OHCI Host Controller
[   61.391121] ohci_hcd 0001:10:15.1: new USB bus registered, assigned bus number 3
[   61.391148] ohci_hcd 0001:10:15.1: irq 58, io mem 0x80083000
[   61.466170] usb 1-5: new high speed USB device using ehci_hcd and address 2
[   61.469727] usb usb3: configuration #1 chosen from 1 choice
[   61.469793] hub 3-0:1.0: USB hub found
[   61.469812] hub 3-0:1.0: 2 ports detected
[   61.574625] PCI: Enabling device 0001:10:18.0 (0000 -> 0002)
[   61.574654] ohci_hcd 0001:10:18.0: OHCI Host Controller
[   61.574698] ohci_hcd 0001:10:18.0: new USB bus registered, assigned bus number 4
[   61.574731] ohci_hcd 0001:10:18.0: irq 27, io mem 0x80082000
[   61.650334] usb usb4: configuration #1 chosen from 1 choice
[   61.650395] hub 4-0:1.0: USB hub found
[   61.650416] hub 4-0:1.0: 2 ports detected
[   61.703855] usb 1-5: configuration #1 chosen from 1 choice
[   61.738003] kjournald starting.  Commit interval 5 seconds
[   61.738040] EXT3-fs: mounted filesystem with ordered data mode.
[   61.752470] usbcore: registered new interface driver libusual
[   61.754757] PCI: Enabling device 0001:10:19.0 (0000 -> 0002)
[   61.754786] ohci_hcd 0001:10:19.0: OHCI Host Controller
[   61.754833] ohci_hcd 0001:10:19.0: new USB bus registered, assigned bus number 5
[   61.754868] ohci_hcd 0001:10:19.0: irq 28, io mem 0x80081000
[   61.786757] SCSI subsystem initialized
[   61.796141] Initializing USB Mass Storage driver...
[   61.796448] scsi0 : SCSI emulation for USB Mass Storage devices
[   61.800482] usb-storage: device found at 2
[   61.800489] usbcore: registered new interface driver usb-storage
[   61.800496] USB Mass Storage support registered.
[   61.800501] usb-storage: waiting for device to settle before scanning
[   61.830320] usb usb5: configuration #1 chosen from 1 choice
[   61.830381] hub 5-0:1.0: USB hub found
[   61.830399] hub 5-0:1.0: 2 ports detected
[   61.937943] sungem.c:v0.98 8/24/03 David S. Miller (davem@redhat.com)
[   62.006831] PHY ID: 2060e1, addr: 0
[   62.007448] eth0: Sun GEM (PCI) 10/100/1000BaseT Ethernet 00:0a:95:95:01:2e 
[   62.007460] eth0: Found BCM5421 PHY
[   62.236450] usb 5-1: new full speed USB device using ohci_hcd and address 2
[   62.374814] ieee1394: Node added: ID:BUS[0-00:1023]  GUID[00d04b7610064823]
[   62.374989] ieee1394: Host added: ID:BUS[0-01:1023]  GUID[000a95fffe95012e]
[   62.431622] usb 5-1: configuration #1 chosen from 1 choice
[   62.433509] hub 5-1:1.0: USB hub found
[   62.435465] hub 5-1:1.0: 3 ports detected
[   62.753457] usb 5-1.1: new full speed USB device using ohci_hcd and address 3
[   62.863593] usb 5-1.1: configuration #1 chosen from 1 choice
[   63.069452] usb 5-1.2: new low speed USB device using ohci_hcd and address 4
[   63.181565] usb 5-1.2: configuration #1 chosen from 1 choice
[   64.406625] eth0: Link is up at 100 Mbps, full-duplex.
[   66.803133] usb-storage: device scan complete
[   67.524486] scsi 0:0:0:0: Direct-Access     WDC WD25 00JB-00REA0      20.0 PQ: 0 ANSI: 0
[   69.680464] scsi1 : SBP-2 IEEE-1394
[   69.890337] eth0: Link is up at 100 Mbps, full-duplex.
[   69.890347] eth0: Pause is disabled
[   70.432167] NET: Registered protocol family 10
[   70.432367] lo: Disabled Privacy Extensions
[   70.691399] ieee1394: sbp2: Logged into SBP-2 device
[   70.691673] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[   70.694523] scsi 1:0:0:0: Direct-Access-RBC ST332082 0A               3.AA PQ: 0 ANSI: 4
[   72.637158] Linux agpgart interface v0.102 (c) Dave Jones
[   72.639547] agpgart: Detected Apple UniNorth 2 chipset
[   72.639660] agpgart: configuring for size idx: 8
[   72.639732] agpgart: AGP aperture is 32M @ 0x0
[   73.808393] usbcore: registered new interface driver hiddev
[   73.989273] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[   73.991006] sda: Write Protect is off
[   73.991012] sda: Mode Sense: 03 00 00 00
[   73.991015] sda: assuming drive cache: write through
[   74.003745] input: Mitsumi Electric Apple Extended USB Keyboard as /class/input/input2
[   74.003833] input: USB HID v1.10 Keyboard [Mitsumi Electric Apple Extended USB Keyboard] on usb-0001:10:19.0-1.1
[   74.010565] input: Mitsumi Electric Apple Extended USB Keyboard as /class/input/input3
[   74.010635] input: USB HID v1.10 Device [Mitsumi Electric Apple Extended USB Keyboard] on usb-0001:10:19.0-1.1
[   74.068638] input: Logitech USB-PS/2 Optical Mouse as /class/input/input4
[   74.068774] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0001:10:19.0-1.2
[   74.068798] usbcore: registered new interface driver usbhid
[   74.068805] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   74.069818] usbcore: registered new interface driver xpad
[   74.069826] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6
[   74.769746] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[   74.840391] sda: Write Protect is off
[   74.840403] sda: Mode Sense: 03 00 00 00
[   74.840407] sda: assuming drive cache: write through
[   74.840418]  sda:<6>pmac_zilog: 0.6 (Benjamin Herrenschmidt <benh@kernel.crashing.org>)
[   74.883904] ttyS0 at MMIO 0x80013020 (irq = 22) is a Z85c30 ESCC - Serial port
[   74.885028] ttyS1 at MMIO 0x80013000 (irq = 23) is a Z85c30 ESCC - Serial port
[   74.980431]  sda1 sda2
[   74.981801] sd 0:0:0:0: Attached scsi disk sda
[   75.125781] SCSI device sdb: 625142448 512-byte hdwr sectors (320073 MB)
[   75.126457] sdb: Write Protect is off
[   75.126464] sdb: Mode Sense: 11 00 00 00
[   75.138649] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   75.139685] SCSI device sdb: 625142448 512-byte hdwr sectors (320073 MB)
[   75.140222] sdb: Write Protect is off
[   75.140227] sdb: Mode Sense: 11 00 00 00
[   75.200114] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   75.200126]  sdb: [mac] sdb1 sdb2 sdb3 sdb4 sdb5 sdb6 sdb7 sdb8
[   75.205781] sd 1:0:0:0: Attached scsi disk sdb
[   75.241444] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   75.241508] sd 1:0:0:0: Attached scsi generic sg1 type 14
[   76.975102] input: PowerMac Beep as /class/input/input5
[   77.027163] apm_emu: APM Emulation 0.5 initialized.
[   77.085004] DS1775 digital thermometer [@49]
[   77.085011] Temp: 26.0 C  Hyst: 75.0 C  OS: 80.0 C
[   77.086958] ADM1030 fan controller [@2c]
[   77.092688] Reducing overheating limit to 65.0 C (Hyst: 60.0 C)
[   77.284665] fuse init (API version 7.8)
[   77.453481] Adding 1953116k swap on /dev/disk/by-uuid/6243acc9-9bdd-4444-ba03-bf2c296d8b06.  Priority:-1 extents:1 across:1953116k
[   77.917646] EXT3 FS on hdc3, internal journal
[   78.595416] kjournald starting.  Commit interval 5 seconds
[   78.595607] EXT3 FS on hdc5, internal journal
[   78.595622] EXT3-fs: mounted filesystem with ordered data mode.
[COLOR="DarkOrange"][   78.852439] hfs: write access to a jounaled filesystem is not supported, use the force option at your own risk, mounting read-only.[/COLOR]
[   78.921229] kjournald starting.  Commit interval 5 seconds
[   78.921245] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   78.922138] EXT3 FS on sda1, internal journal
[   78.922149] EXT3-fs: mounted filesystem with ordered data mode.
[COLOR="DarkOrange"][   79.187118] hfs: write access to a jounaled filesystem is not supported, use the force option at your own risk, mounting read-only.[/COLOR]
[COLOR="Lime"][   79.241304] hfs: Filesystem was not cleanly unmounted, running fsck.hfsplus is recommended.  mounting read-only.[/COLOR]
[   80.910365] eth0: no IPv6 routers present
[   85.097441] CPU-temp: 27.0 C, Case: 18.8 C,  Fan: 0 (tuned -11)
[   87.461907] [drm] Initialized drm 1.1.0 20060810
[   87.483236] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[   87.833121] lp: driver loaded but no devices found
[   88.009593] ppdev: user-space parallel port driver
[   88.634628] agpgart: Putting AGP V2 device at 0000:00:0b.0 into 4x mode
[   88.638364] agpgart: Putting AGP V2 device at 0000:00:10.0 into 4x mode
[   88.969481] [drm] Setting GART location based on new memory map
[   88.970302] [drm] Loading R200 Microcode
[   88.970361] [drm] writeback test succeeded in 1 usecs
[   90.653341] Bluetooth: Core ver 2.11
[   90.653464] NET: Registered protocol family 31
[   90.653468] Bluetooth: HCI device and connection manager initialized
[   90.653475] Bluetooth: HCI socket layer initialized
[   90.738314] Bluetooth: L2CAP ver 2.8
[   90.738325] Bluetooth: L2CAP socket layer initialized
[   90.958324] Bluetooth: RFCOMM socket layer initialized
[   90.958355] Bluetooth: RFCOMM TTY layer initialized
[   90.958359] Bluetooth: RFCOMM ver 1.8
[   91.394719] input: Mouseemu virtual keyboard as /class/input/input6
[   91.395123] input: Mouseemu virtual mouse as /class/input/input7
mpunk@PUNIX-G4:~$ 

```

I think, the orange marked lines are standart. The green marked shows the problem. But besides of this, there are all volumes with hfs+ without journal on whitch i need writing-access mounted as rw and I did a writing test, to proof this functioning.


To proof this for you, here is my actual mtab
```
/dev/hdc3 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-16-powerpc-smp/volatile tmpfs rw 0 0
/dev/hdc5 /home ext3 rw 0 0
[COLOR="DarkOrange"]/dev/hdc7 /media/data hfsplus rw,noexec,nosuid,nodev,uid=0,gid=46,umask=022,nls=utf8 0 0
/dev/hdc6 /media/musik hfsplus rw,noexec,nosuid,nodev,uid=0,gid=46,umask=022,nls=utf8 0 0[/COLOR]
/dev/hda3 /media/PowerMAC_G4_Dual hfsplus ro,noexec,nosuid,nodev 0 0
/dev/sda1 /media/ext_data ext3 rw,noexec,nosuid,nodev 0 0
/dev/disk/by-uuid/66E444A632ECD092 /media/ext_ntfs fuseblk rw,nosuid,nodev,noexec,noatime,allow_other,default_permissions,blksize=4096 0 0
/dev/sdb3 /media/OS_X_live hfsplus ro,noexec,nosuid,nodev 0 0
/dev/sdb5 /media/MAC_DATA hfsplus ro,noexec,nosuid,nodev 0 0
[COLOR="DarkOrange"]/dev/sdb7 /media/LIN_DATA hfsplus rw,noexec,nosuid,nodev,uid=0,gid=46,umask=022,nls=utf8 0 0[/COLOR]
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
```

---

### Post by simonn on 2007-09-21
A crash will probably cause the following error:

```

hfs: Filesystem was not cleanly unmounted, running fsck.hfsplus is recommended.  mounting read-only.
```

This needs to be repaired using fsck.hfsplus. See [http://gentoo-wiki.com/HOWTO_hfsplus#Manual_Installs](http://gentoo-wiki.com/HOWTO_hfsplus#Manual_Installs) and
[http://gentoo-wiki.com/HOWTO_hfsplus#Repairing_a_HFS.2B_Filesystem_using_Fsck.hfsplus](http://gentoo-wiki.com/HOWTO_hfsplus#Repairing_a_HFS.2B_Filesystem_using_Fsck.hfsplus)

Note the HFS utilities in the Ubuntu respositories do not work, you have to use the ones in the linked article.

What did you type into the terminal on OSX when you used diskutil to turn off the journalling?

---

### Post by frog_pilot on 2007-09-22
In OS X i used ```
sudo diskutil disableJournal <volumename>
``` in Terminal after changing to the Volumes-directory. But for some reasons, I actually do not remember, it was better for me to format the Volumus with OSX-diskutility in "Macintosh extended"-format without the add "Journaled". I thin there were some warnings in Linux when I did it the terminal-way

Thank you for the link to gentoo wiki. I will chek it out. At first it is sufficient for me to boot into OS X and shut down tidily for repairing these problems with the hfs-volumes in Linux. The Problem on my system why reading/writing fails so often on the hfs+-volumes. I have an additional pci-usb2.0-card from "sonnett" (or likewise). On one of these interfaces I plugged an external hd with a ntfs and a ext3-volume. And I want to get about 50gig of music from the ntfs-volume to one of the internal hfs-volumes. after writing about 200 files the system crashes frequently. But I want to import these data from whithin my ubuntu-account, because I want to get the ubuntu-user to have the full ownership of these files...

After all I think it is no good idea to share a hfs-partition between ubuntu and OS X. At least on my system it is too fragile to work with. I will Install the ext2-driver under OS X and then I can read the others Volumes from within one and copy the files I need to work with form one volume to another.

I experienced the ntfs-3g-driver in Linux as much better than the hfs+ one. But hfs+ and the mac seem to be too exotic for linux and there are unfortunately not so many people who are able to develop stuff for it and the progress is much slower than on the x86-platform

---

