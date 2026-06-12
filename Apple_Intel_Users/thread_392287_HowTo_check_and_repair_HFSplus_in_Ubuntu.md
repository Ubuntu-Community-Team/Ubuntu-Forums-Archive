---
title: "HowTo check and repair HFSplus in Ubuntu"
date: 2007-03-24
forum: Apple Intel Users
---

### Post by Gen2ly on 2007-03-24
HFS+ read and write support is part of many standard pre-built kernels today in many distros including Ubuntu's kernel.  HFS+ is the standard file system on all new Macs and a good number of iPods.  The HFS+ driver in the Linux kernel is considered stable and reliable for daily use (not as reliable as to use it for a root filesystem but a good filesystem and driver nonetheless).  

If [building a kernel](http://ubuntuforums.org/showthread.php?t=442941) be sure to add HFS+ support in the filesystems section if you have or plan to connect to any HFS+ drives or partitions.    Tools for HFS+ support are not built in the 

This howto describes how to add HFS+ filesystem tools to check and repair, and create HFS+ filesystem within Linux.

**[COLOR="DarkRed"][SIZE="4"]A Note About Journaled HFS+[/SIZE][/COLOR]**

The Linux HFS+ kernel driver has support to read and write to HFS+ non-journaled drives/parititions but only has read support of journaled HFS+.  Journaling ability got added to HFSplus when OSX came out and is by default on for OS X installations.  Journaling is a redundant behavior of a filesystem that helps protect data loss (useful for occasions like power outages).  If planning to write to an HFS+ parition or drive journaling must be turned off in OS X.

To turn off journaling, boot into OSX.   Select Disk Utility in the Utilities Folder and select the drive to have journaling turned off on.  A green button on top will allow you with switch Journaling on and off.   

Due to a bug in Disk Utility, this button may be disabled for some users so also do this in the command line.  First, list the hard drives then disable it's journal:

```
diskuilt list
diskutil disableJournal <device>
```

Or use /Volumes/<device>.  

Another bug may also prevent disabling journaling and we have to enable Journaling first [FONT="Courier New"]diskutil enableJournal <device>[/FONT] before being able to disable it.

**[COLOR="DarkRed"][SIZE="4"]Mounting HFS+ in Ubuntu[/SIZE][/COLOR]**

Once journaling has been decided, mounting is pretty straight forward.

First of all make a directory that will hold the mounted disk.

```
sudo mkdir /mnt/Shared-Disk
```

The directory can be named to your choosing.  Some people do this in [FONT="Courier New"]/media[/FONT] where gnome-volume-manager mounts the partitions.

To manually mount the drive/partition find the Linux device name for the drive/partition:

```
sudo parted /dev/sda print
```

For PPC Macs:

```
sudo mac-fdisk -l
```

Then mount it:

```
sudo mount /dev/sda4 -t hfsplus -o rw /mnt/Shared-Disk
```

Replace sda4 with your **dev**ice and hard disk partition(**#**).  My USB drive is /sda, my clamshell iBook is hda, etc.  "df -h" might also give a good idea what the Linux name of the device is.

To have the HFSplus drive/partition mounted everytime on boot, the fstab file must be edited:

```
sudo gedit /etc/fstab
```

Add:

```
/dev/sda4 /mnt/Shared_Disk hfsplus rw,exec,auto,users 0 0
```

**[COLOR="DarkRed"][SIZE="4"]HFSplus Partitions With Errors[/SIZE][/COLOR]**

Occasionally a drive/partition can get errors.  Usually this occurs when a drive hasn't been unmounted cleanly.  The Kernel HFS+ driver is picky about it's HFSplus drives, but this is a good thing.  If it ever occurs where your system is locked up and and force reboot is needed, then the HFSplus disk will not be cleanly unmounted.  Look in the syslog (System > Administration > System Log), punch ctrl-F, then type "mount" in the filter.  If you see this:

```
hfs: Filesystem was not cleanly unmounted, running fsck.hfsplus is recommended.  mounting read-only
```

then either reboot OS X and check the hard drive or install the Darwin utilities to do this in Linux.

**[COLOR="DarkRed"][SIZE="4"]Building DiskDev Commands[/SIZE][/COLOR]**

Building the Darwin tools is a basic compile.

Requirements:

```
sudo apt-get install build-essential
```

Download the source and compile it:

```
sudo bash
cd /usr/src
mkdir hfsplus_support
wget http://gentoo.osuosl.org/distfiles/diskdev_cmds-332.14.tar.gz
wget http://www.ecl.udel.edu/~mcgee/diskdev_cmds/diskdev_cmds-332.14.patch.bz2
tar zxf diskdev_cmds-332.14.tar.gz
bunzip2 -c diskdev_cmds-332.14.patch.bz2 | patch -p0
cd diskdev_cmds-332.14
make -f Makefile.lnx
cp fsck_hfs.tproj/fsck_hfs /sbin/fsck.hfsplus
cd /sbin
ln -s mkfs.hfsplus mkfs.hfs
ln -s fsck.hfsplus fsck.hfs
```

File system check for hfsplus is now installed.  Type "fsck.hfsplus" to see the list of arguments - there is no man page.

To check a hfsplus drive/partition make sure it's unmounted first:

```
umount /dev/sda4
```

And check it:

```
fsck.hfsplus -r /dev/sda4
```

The Darwin DiskDev commands include mkfs.hfsplus too for the ability to format paritions from within Linux.

**[COLOR="DarkRed"][SIZE="4"]Notes:[/SIZE][/COLOR]**

[LIST]
[*]In Efty Edge the compiler failed to compile newfs_hfs for me.  I'm not really sure why, but works fine in Feisty Fawn.
[*]math45 has [found a way](http://ubuntuforums.org/showthread.php?p=4591297#post4591297) to get diskdev commands to work on 64 bit systems.  I have not tried this method though.  Use at your own risk.
[*][Original Gentoo piece](http://gentoo-wiki.com/HOWTO_hfsplus)
[*][Debian derived piece](http://www.debian-administration.org/users/lee/weblog/21)
[/LIST]

---

### Post by cyberdork33 on 2007-03-24
Thanks, great info!

---

### Post by Gen2ly on 2007-03-24
Thank you.

I always thought it useful.  I kept having issues writing to my HFS-partition and I luckily found out why one day.  It makes sense they are mounted read only if it wasn't umounted cleanly.

---

### Post by genti on 2007-03-27
Thanks man!

---

### Post by Gen2ly on 2007-04-24
Just tried to install on my Fiesty Fawn installation and it still works.

---

### Post by ZodiacfreaK on 2007-05-12
hey man great post! Took me two tries to make it wrk though, and also this link seems to be down at the moment
```
wget http://darwinsource.opendarwin.org/tarballs/apsl/diskdev_cmds-332.14.tar.gz
```
Use this one instead
```

wget http://ftp.leg.uct.ac.za/pub/stuff/tmp/diskdev_cmds-332.14.tar.gz
```

---

### Post by Gen2ly on 2007-05-12
Appreciate the info ZodiacfreaK, I justly corrected.

---

### Post by ronocdh on 2007-05-13
Very, very cool post! Thanks Dirk!

---

### Post by MatthewACT on 2007-05-24
Hi.  Thank you for your informative post about repairing hfsplus partiotions.  Unfortuantely, I received and error while following your directions (as shown below).  Can you help me?

root@ec-desktop:/usr/src# tar zxf diskdev_cmds-332.14.tar.gz
root@ec-desktop:/usr/src# man tar
Reformatting tar(1), please wait...
root@ec-desktop:/usr/src# bunzip2 -c diskdev_cmds-332.14.patch.bz2 | patch -p0
patching file diskdev_cmds-332.14/Makefile.lnx
patching file diskdev_cmds-332.14/fsck_hfs.tproj/Makefile.lnx
patching file diskdev_cmds-332.14/fsck_hfs.tproj/cache.c
patching file diskdev_cmds-332.14/fsck_hfs.tproj/dfalib/BTree.c
patching file diskdev_cmds-332.14/fsck_hfs.tproj/dfalib/BTreeTreeOps.c
patching file diskdev_cmds-332.14/fsck_hfs.tproj/dfalib/BlockCache.c
patching file diskdev_cmds-332.14/fsck_hfs.tproj/dfalib/Makefile.lnx
patching file diskdev_cmds-332.14/fsck_hfs.tproj/dfalib/SBTree.c
patching file diskdev_cmds-332.14/fsck_hfs.tproj/dfalib/SControl.c
patching file diskdev_cmds-332.14/fsck_hfs.tproj/dfalib/SDevice.c
patching file diskdev_cmds-332.14/fsck_hfs.tproj/dfalib/SKeyCompare.c
patching file diskdev_cmds-332.14/fsck_hfs.tproj/dfalib/SRepair.c
patching file diskdev_cmds-332.14/fsck_hfs.tproj/dfalib/SRuntime.h
patching file diskdev_cmds-332.14/fsck_hfs.tproj/dfalib/SUtils.c
patching file diskdev_cmds-332.14/fsck_hfs.tproj/dfalib/SVerify2.c
patching file diskdev_cmds-332.14/fsck_hfs.tproj/dfalib/Scavenger.h
patching file diskdev_cmds-332.14/fsck_hfs.tproj/dfalib/hfs_endian.c
patching file diskdev_cmds-332.14/fsck_hfs.tproj/dfalib/hfs_endian.h
patching file diskdev_cmds-332.14/fsck_hfs.tproj/fsck_hfs.c
patching file diskdev_cmds-332.14/fsck_hfs.tproj/utilities.c
patching file diskdev_cmds-332.14/include/bitstring.h
patching file diskdev_cmds-332.14/include/hfs/hfs_format.h
patching file diskdev_cmds-332.14/include/hfs/hfs_mount.h
patching file diskdev_cmds-332.14/include/missing.h
patching file diskdev_cmds-332.14/include/sys/appleapiopts.h
patching file diskdev_cmds-332.14/newfs_hfs.tproj/Makefile.lnx
patching file diskdev_cmds-332.14/newfs_hfs.tproj/hfs_endian.c
patching file diskdev_cmds-332.14/newfs_hfs.tproj/hfs_endian.h
patching file diskdev_cmds-332.14/newfs_hfs.tproj/makehfs.c
patching file diskdev_cmds-332.14/newfs_hfs.tproj/newfs_hfs.c
patching file diskdev_cmds-332.14/newfs_hfs.tproj/newfs_hfs.h
root@ec-desktop:/usr/src# cd diskdev_cmds-332.14
root@ec-desktop:/usr/src/diskdev_cmds-332.14# make -f Makefile.lnx
for d in newfs_hfs.tproj fsck_hfs.tproj; do make -C $d -f Makefile.lnx all; done
make[1]: Entering directory `/usr/src/diskdev_cmds-332.14/newfs_hfs.tproj'
gcc -g3 -Wall -I/usr/src/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o hfs_endian.o hfs_endian.c
hfs_endian.c:30:23: error: sys/types.h: No such file or directory
hfs_endian.c:31:22: error: sys/stat.h: No such file or directory
In file included from hfs_endian.c:34:
/usr/src/diskdev_cmds-332.14/include/missing.h:4:20: error: endian.h: No such file or directory
/usr/src/diskdev_cmds-332.14/include/missing.h:5:22: error: byteswap.h: No such file or directory
/usr/src/diskdev_cmds-332.14/include/missing.h:6:19: error: errno.h: No such file or directory
/usr/src/diskdev_cmds-332.14/include/missing.h:7:20: error: stdint.h: No such file or directory
In file included from hfs_endian.c:39:
/usr/src/diskdev_cmds-332.14/include/hfs/hfs_format.h:99: error: expected specifier-qualifier-list before ‘uint16_t’
/usr/src/diskdev_cmds-332.14/include/hfs/hfs_format.h:117: error: expected specifier-qualifier-list before ‘uint8_t’
/usr/src/diskdev_cmds-332.14/include/hfs/hfs_format.h:126: error: expected specifier-qualifier-list before ‘uint16_t’
/usr/src/diskdev_cmds-332.14/include/hfs/hfs_format.h:142: error: expected specifier-qualifier-list before ‘uint16_t’
/usr/src/diskdev_cmds-332.14/include/hfs/hfs_format.h:149: error: expected specifier-qualifier-list before ‘uint32_t’
/usr/src/diskdev_cmds-332.14/include/hfs/hfs_format.h:163: error: expected specifier-qualifier-list before ‘uint32_t’
/usr/src/diskdev_cmds-332.14/include/hfs/hfs_format.h:176: error: expected specifier-qualifier-list before ‘int16_t’
/usr/src/diskdev_cmds-332.14/include/hfs/hfs_format.h:183: error: expected specifier-qualifier-list before ‘uint16_t’
/usr/src/diskdev_cmds-332.14/include/hfs/hfs_format.h:186: error: expected specifier-qualifier-list before ‘int16_t’
/usr/src/diskdev_cmds-332.14/include/hfs/hfs_format.h:191: error: expected specifier-qualifier-list before ‘int8_t’
/usr/src/diskdev_cmds-332.14/include/hfs/hfs_format.h:198: error: expected specifier-qualifier-list before ‘uint64_t’
/usr/src/diskdev_cmds-332.14/include/hfs/hfs_format.h:212: error: expected specifier-qualifier-list before ‘uint32_t’
/usr/src/diskdev_cmds-332.14/include/hfs/hfs_format.h:244: error: expected specifier-qualifier-list before ‘uint8_t’
/usr/src/diskdev_cmds-332.14/include/hfs/hfs_format.h:253: error: expected specifier-qualifier-list before ‘uint16_t’
/usr/src/diskdev_cmds-332.14/include/hfs/hfs_format.h:293: error: expected specifier-qualifier-list before ‘int16_t’
/usr/src/diskdev_cmds-332.14/include/hfs/hfs_format.h:308: error: expected specifier-qualifier-list before ‘int16_t’
/usr/src/diskdev_cmds-332.14/include/hfs/hfs_format.h:327: error: expected specifier-qualifier-list before ‘int16_t’
/usr/src/diskdev_cmds-332.14/include/hfs/hfs_format.h:351: error: expected specifier-qualifier-list before ‘int16_t’
/usr/src/diskdev_cmds-332.14/include/hfs/hfs_format.h:374: error: expected specifier-qualifier-list before ‘int16_t’
/usr/src/diskdev_cmds-332.14/include/hfs/hfs_format.h:383: error: expected specifier-qualifier-list before ‘int16_t’
/usr/src/diskdev_cmds-332.14/include/hfs/hfs_format.h:409: error: expected specifier-qualifier-list before ‘uint32_t’
/usr/src/diskdev_cmds-332.14/include/hfs/hfs_format.h:421: error: expected specifier-qualifier-list before ‘uint32_t’
/usr/src/diskdev_cmds-332.14/include/hfs/hfs_format.h:434: error: expected specifier-qualifier-list before ‘uint32_t’
/usr/src/diskdev_cmds-332.14/include/hfs/hfs_format.h:444: error: expected specifier-qualifier-list before ‘uint32_t’
/usr/src/diskdev_cmds-332.14/include/hfs/hfs_format.h:454: error: expected specifier-qualifier-list before ‘uint32_t’
/usr/src/diskdev_cmds-332.14/include/hfs/hfs_format.h:465: error: expected specifier-qualifier-list before ‘uint16_t’
/usr/src/diskdev_cmds-332.14/include/hfs/hfs_format.h:482: error: ‘uint16_t’ undeclared here (not in a function)
/usr/src/diskdev_cmds-332.14/include/hfs/hfs_format.h:483: error: ‘uint8_t’ undeclared here (not in a function)
/usr/src/diskdev_cmds-332.14/include/hfs/hfs_format.h:522: error: expected specifier-qualifier-list before ‘uint16_t’
/usr/src/diskdev_cmds-332.14/include/hfs/hfs_format.h:566: error: expected specifier-qualifier-list before ‘uint16_t’
/usr/src/diskdev_cmds-332.14/include/hfs/hfs_format.h:610: error: expected specifier-qualifier-list before ‘uint8_t’
/usr/src/diskdev_cmds-332.14/include/hfs/hfs_format.h:618: error: expected specifier-qualifier-list before ‘uint32_t’
/usr/src/diskdev_cmds-332.14/include/hfs/hfs_format.h:637: error: expected specifier-qualifier-list before ‘uint16_t’
/usr/src/diskdev_cmds-332.14/include/hfs/hfs_format.h:671: error: expected specifier-qualifier-list before ‘uint32_t’
hfs_endian.c: In function ‘hfs_swap_HFSMasterDirectoryBlock’:
hfs_endian.c:64: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drSigWord’
hfs_endian.c:64: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drSigWord’
hfs_endian.c:65: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drCrDate’
hfs_endian.c:65: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drCrDate’
hfs_endian.c:66: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drLsMod’
hfs_endian.c:66: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drLsMod’
hfs_endian.c:67: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drAtrb’
hfs_endian.c:67: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drAtrb’
hfs_endian.c:68: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drNmFls’
hfs_endian.c:68: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drNmFls’
hfs_endian.c:69: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drVBMSt’
hfs_endian.c:69: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drVBMSt’
hfs_endian.c:70: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drAllocPtr’
hfs_endian.c:70: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drAllocPtr’
hfs_endian.c:71: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drNmAlBlks’
hfs_endian.c:71: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drNmAlBlks’
hfs_endian.c:72: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drAlBlkSiz’
hfs_endian.c:72: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drAlBlkSiz’
hfs_endian.c:73: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drClpSiz’
hfs_endian.c:73: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drClpSiz’
hfs_endian.c:74: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drAlBlSt’
hfs_endian.c:74: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drAlBlSt’
hfs_endian.c:75: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drNxtCNID’
hfs_endian.c:75: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drNxtCNID’
hfs_endian.c:76: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drFreeBks’
hfs_endian.c:76: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drFreeBks’
hfs_endian.c:80: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drVolBkUp’
hfs_endian.c:80: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drVolBkUp’
hfs_endian.c:81: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drVSeqNum’
hfs_endian.c:81: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drVSeqNum’
hfs_endian.c:82: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drWrCnt’
hfs_endian.c:82: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drWrCnt’
hfs_endian.c:83: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drXTClpSiz’
hfs_endian.c:83: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drXTClpSiz’
hfs_endian.c:84: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drCTClpSiz’
hfs_endian.c:84: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drCTClpSiz’
hfs_endian.c:85: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drNmRtDirs’
hfs_endian.c:85: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drNmRtDirs’
hfs_endian.c:86: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drFilCnt’
hfs_endian.c:86: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drFilCnt’
hfs_endian.c:87: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drDirCnt’
hfs_endian.c:87: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drDirCnt’
hfs_endian.c:90: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drFndrInfo’
hfs_endian.c:90: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drFndrInfo’
hfs_endian.c:92: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drEmbedSigWord’
hfs_endian.c:92: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drEmbedSigWord’
hfs_endian.c:93: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drEmbedExtent’
hfs_endian.c:93: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drEmbedExtent’
hfs_endian.c:94: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drEmbedExtent’
hfs_endian.c:94: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drEmbedExtent’
hfs_endian.c:96: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drXTFlSize’
hfs_endian.c:96: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drXTFlSize’
hfs_endian.c:97: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drXTExtRec’
hfs_endian.c:97: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drXTExtRec’
hfs_endian.c:98: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drXTExtRec’
hfs_endian.c:98: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drXTExtRec’
hfs_endian.c:99: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drXTExtRec’
hfs_endian.c:99: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drXTExtRec’
hfs_endian.c:100: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drXTExtRec’
hfs_endian.c:100: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drXTExtRec’
hfs_endian.c:101: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drXTExtRec’
hfs_endian.c:101: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drXTExtRec’
hfs_endian.c:102: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drXTExtRec’
hfs_endian.c:102: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drXTExtRec’
hfs_endian.c:104: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drCTFlSize’
hfs_endian.c:104: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drCTFlSize’
hfs_endian.c:105: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drCTExtRec’
hfs_endian.c:105: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drCTExtRec’
hfs_endian.c:106: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drCTExtRec’
hfs_endian.c:106: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drCTExtRec’
hfs_endian.c:107: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drCTExtRec’
hfs_endian.c:107: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drCTExtRec’
hfs_endian.c:108: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drCTExtRec’
hfs_endian.c:108: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drCTExtRec’
hfs_endian.c:109: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drCTExtRec’
hfs_endian.c:109: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drCTExtRec’
hfs_endian.c:110: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drCTExtRec’
hfs_endian.c:110: error: ‘HFSMasterDirectoryBlock’ has no member named ‘drCTExtRec’
hfs_endian.c: In function ‘hfs_swap_HFSPlusVolumeHeader’:
hfs_endian.c:123: error: ‘HFSPlusVolumeHeader’ has no member named ‘signature’
hfs_endian.c:123: error: ‘HFSPlusVolumeHeader’ has no member named ‘signature’
hfs_endian.c:124: error: ‘HFSPlusVolumeHeader’ has no member named ‘version’
hfs_endian.c:124: error: ‘HFSPlusVolumeHeader’ has no member named ‘version’
hfs_endian.c:125: error: ‘HFSPlusVolumeHeader’ has no member named ‘attributes’
hfs_endian.c:125: error: ‘HFSPlusVolumeHeader’ has no member named ‘attributes’
hfs_endian.c:126: error: ‘HFSPlusVolumeHeader’ has no member named ‘lastMountedVersion’
hfs_endian.c:126: error: ‘HFSPlusVolumeHeader’ has no member named ‘lastMountedVersion’
hfs_endian.c:128: error: ‘HFSPlusVolumeHeader’ has no member named ‘journalInfoBlock’
hfs_endian.c:128: error: ‘HFSPlusVolumeHeader’ has no member named ‘journalInfoBlock’
hfs_endian.c:130: error: ‘HFSPlusVolumeHeader’ has no member named ‘createDate’
hfs_endian.c:130: error: ‘HFSPlusVolumeHeader’ has no member named ‘createDate’
hfs_endian.c:131: error: ‘HFSPlusVolumeHeader’ has no member named ‘modifyDate’
hfs_endian.c:131: error: ‘HFSPlusVolumeHeader’ has no member named ‘modifyDate’
hfs_endian.c:132: error: ‘HFSPlusVolumeHeader’ has no member named ‘backupDate’
hfs_endian.c:132: error: ‘HFSPlusVolumeHeader’ has no member named ‘backupDate’
hfs_endian.c:133: error: ‘HFSPlusVolumeHeader’ has no member named ‘checkedDate’
hfs_endian.c:133: error: ‘HFSPlusVolumeHeader’ has no member named ‘checkedDate’
hfs_endian.c:134: error: ‘HFSPlusVolumeHeader’ has no member named ‘fileCount’
hfs_endian.c:134: error: ‘HFSPlusVolumeHeader’ has no member named ‘fileCount’
hfs_endian.c:135: error: ‘HFSPlusVolumeHeader’ has no member named ‘folderCount’
hfs_endian.c:135: error: ‘HFSPlusVolumeHeader’ has no member named ‘folderCount’
hfs_endian.c:136: error: ‘HFSPlusVolumeHeader’ has no member named ‘blockSize’
hfs_endian.c:136: error: ‘HFSPlusVolumeHeader’ has no member named ‘blockSize’
hfs_endian.c:137: error: ‘HFSPlusVolumeHeader’ has no member named ‘totalBlocks’
hfs_endian.c:137: error: ‘HFSPlusVolumeHeader’ has no member named ‘totalBlocks’
hfs_endian.c:138: error: ‘HFSPlusVolumeHeader’ has no member named ‘freeBlocks’
hfs_endian.c:138: error: ‘HFSPlusVolumeHeader’ has no member named ‘freeBlocks’
hfs_endian.c:139: error: ‘HFSPlusVolumeHeader’ has no member named ‘nextAllocation’
hfs_endian.c:139: error: ‘HFSPlusVolumeHeader’ has no member named ‘nextAllocation’
hfs_endian.c:140: error: ‘HFSPlusVolumeHeader’ has no member named ‘rsrcClumpSize’
hfs_endian.c:140: error: ‘HFSPlusVolumeHeader’ has no member named ‘rsrcClumpSize’
hfs_endian.c:141: error: ‘HFSPlusVolumeHeader’ has no member named ‘dataClumpSize’
hfs_endian.c:141: error: ‘HFSPlusVolumeHeader’ has no member named ‘dataClumpSize’
hfs_endian.c:142: error: ‘HFSPlusVolumeHeader’ has no member named ‘nextCatalogID’
hfs_endian.c:142: error: ‘HFSPlusVolumeHeader’ has no member named ‘nextCatalogID’
hfs_endian.c:143: error: ‘HFSPlusVolumeHeader’ has no member named ‘writeCount’
hfs_endian.c:143: error: ‘HFSPlusVolumeHeader’ has no member named ‘writeCount’
hfs_endian.c:144: error: ‘HFSPlusVolumeHeader’ has no member named ‘encodingsBitmap’
hfs_endian.c:144: error: ‘HFSPlusVolumeHeader’ has no member named ‘encodingsBitmap’
hfs_endian.c:148: error: ‘HFSPlusVolumeHeader’ has no member named ‘allocationFile’
hfs_endian.c:149: error: ‘HFSPlusVolumeHeader’ has no member named ‘extentsFile’
hfs_endian.c:150: error: ‘HFSPlusVolumeHeader’ has no member named ‘catalogFile’
hfs_endian.c:151: error: ‘HFSPlusVolumeHeader’ has no member named ‘attributesFile’
hfs_endian.c:152: error: ‘HFSPlusVolumeHeader’ has no member named ‘startupFile’
hfs_endian.c: In function ‘hfs_swap_HFSPlusForkData’:
hfs_endian.c:167: error: ‘HFSPlusForkData’ has no member named ‘logicalSize’
hfs_endian.c:167: error: ‘HFSPlusForkData’ has no member named ‘logicalSize’
hfs_endian.c:169: error: ‘HFSPlusForkData’ has no member named ‘clumpSize’
hfs_endian.c:169: error: ‘HFSPlusForkData’ has no member named ‘clumpSize’
hfs_endian.c:170: error: ‘HFSPlusForkData’ has no member named ‘totalBlocks’
hfs_endian.c:170: error: ‘HFSPlusForkData’ has no member named ‘totalBlocks’
hfs_endian.c:173: error: ‘HFSPlusForkData’ has no member named ‘extents’
hfs_endian.c:173: error: ‘HFSPlusForkData’ has no member named ‘extents’
hfs_endian.c:174: error: ‘HFSPlusForkData’ has no member named ‘extents’
hfs_endian.c:174: error: ‘HFSPlusForkData’ has no member named ‘extents’
make[1]: *** [hfs_endian.o] Error 1
make[1]: Leaving directory `/usr/src/diskdev_cmds-332.14/newfs_hfs.tproj'
make[1]: Entering directory `/usr/src/diskdev_cmds-332.14/fsck_hfs.tproj'
gcc -g3 -Wall -I/usr/src/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o fsck_hfs.o fsck_hfs.c
fsck_hfs.c:24:23: error: sys/types.h: No such file or directory
fsck_hfs.c:25:22: error: sys/stat.h: No such file or directory
fsck_hfs.c:26:23: error: sys/param.h: No such file or directory
fsck_hfs.c:30:23: error: sys/mount.h: No such file or directory
fsck_hfs.c:31:23: error: sys/ioctl.h: No such file or directory
In file included from fsck_hfs.c:36:
/usr/src/diskdev_cmds-332.14/include/hfs/hfs_mount.h:33:22: error: sys/time.h: No such file or directory
In file included from fsck_hfs.c:36:
/usr/src/diskdev_cmds-332.14/include/hfs/hfs_mount.h:50: error: expected specifier-qualifier-list before ‘uid_t’
fsck_hfs.c:38:19: error: errno.h: No such file or directory
fsck_hfs.c:39:19: error: fcntl.h: No such file or directory
fsck_hfs.c:40:19: error: stdio.h: No such file or directory
fsck_hfs.c:41:20: error: string.h: No such file or directory
fsck_hfs.c:42:20: error: unistd.h: No such file or directory
fsck_hfs.c:43:20: error: stdlib.h: No such file or directory
In file included from fsck_hfs.h:25,
                 from fsck_hfs.c:45:
cache.h:30:20: error: stdint.h: No such file or directory
In file included from fsck_hfs.h:25,
                 from fsck_hfs.c:45:
cache.h:65: error: expected specifier-qualifier-list before ‘uint32_t’
cache.h:89: error: expected specifier-qualifier-list before ‘uint32_t’
cache.h:117: error: expected specifier-qualifier-list before ‘uint32_t’
cache.h:144: error: expected declaration specifiers or ‘...’ before ‘uint32_t’
cache.h:145: error: expected declaration specifiers or ‘...’ before ‘uint32_t’
cache.h:145: error: expected declaration specifiers or ‘...’ before ‘uint32_t’
cache.h:145: error: expected declaration specifiers or ‘...’ before ‘uint32_t’
cache.h:164: error: expected declaration specifiers or ‘...’ before ‘uint64_t’
cache.h:164: error: expected declaration specifiers or ‘...’ before ‘uint32_t’
cache.h:171: error: expected declaration specifiers or ‘...’ before ‘uint32_t’
cache.h:210: error: expected declaration specifiers or ‘...’ before ‘uint64_t’
cache.h:210: error: expected declaration specifiers or ‘...’ before ‘uint64_t’
In file included from fsck_hfs.c:45:
fsck_hfs.h:50: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__P’
fsck_hfs.h:51: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__P’
fsck_hfs.h:52: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__P’
fsck_hfs.h:53: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__P’
fsck_hfs.h:54: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__P’
fsck_hfs.h:55: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__P’
fsck_hfs.c:91: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__P’
fsck_hfs.c:92: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__P’
fsck_hfs.c:93: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__P’
fsck_hfs.c:94: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__P’
fsck_hfs.c:95: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__P’
fsck_hfs.c: In function ‘main’:
fsck_hfs.c:107: warning: implicit declaration of function ‘strrchr’
fsck_hfs.c:107: warning: incompatible implicit declaration of built-in function ‘strrchr’
fsck_hfs.c:112: warning: implicit declaration of function ‘getopt’
fsck_hfs.c:112: error: ‘EOF’ undeclared (first use in this function)
fsck_hfs.c:112: error: (Each undeclared identifier is reported only once
fsck_hfs.c:112: error: for each function it appears in.)
fsck_hfs.c:135: warning: implicit declaration of function ‘strtol’
fsck_hfs.c:135: error: ‘NULL’ undeclared (first use in this function)
fsck_hfs.c:138: warning: implicit declaration of function ‘fprintf’
fsck_hfs.c:138: warning: incompatible implicit declaration of built-in function ‘fprintf’
fsck_hfs.c:138: error: ‘stderr’ undeclared (first use in this function)
fsck_hfs.c:139: warning: implicit declaration of function ‘usage’
fsck_hfs.c:184: warning: incompatible implicit declaration of built-in function ‘fprintf’
fsck_hfs.c:190: warning: implicit declaration of function ‘checkfilesys’
fsck_hfs.c:190: warning: implicit declaration of function ‘blockcheck’
fsck_hfs.c:192: warning: implicit declaration of function ‘exit’
fsck_hfs.c:192: warning: incompatible implicit declaration of built-in function ‘exit’
fsck_hfs.c: At top level:
fsck_hfs.c:197: error: static declaration of ‘checkfilesys’ follows non-static declaration
fsck_hfs.c:190: error: previous implicit declaration of ‘checkfilesys’ was here
fsck_hfs.c: In function ‘checkfilesys’:
fsck_hfs.c:212: error: ‘NULL’ undeclared (first use in this function)
fsck_hfs.c:248: warning: implicit declaration of function ‘pwarn’
fsck_hfs.c:250: warning: implicit declaration of function ‘setup’
fsck_hfs.c:252: warning: implicit declaration of function ‘pfatal’
fsck_hfs.c:259: warning: implicit declaration of function ‘printf’
fsck_hfs.c:259: warning: incompatible implicit declaration of built-in function ‘printf’
fsck_hfs.c:299: warning: implicit declaration of function ‘ckfini’
fsck_hfs.c:345: warning: incompatible implicit declaration of built-in function ‘printf’
fsck_hfs.c:360: warning: implicit declaration of function ‘sync’
fsck_hfs.c:369: warning: implicit declaration of function ‘fcntl’
fsck_hfs.c:370: warning: implicit declaration of function ‘close’
fsck_hfs.c:371: warning: implicit declaration of function ‘free’
fsck_hfs.c: At top level:
fsck_hfs.c:391: error: static declaration of ‘setup’ follows non-static declaration
fsck_hfs.c:250: error: previous implicit declaration of ‘setup’ was here
fsck_hfs.c: In function ‘setup’:
fsck_hfs.c:392: error: storage size of ‘statb’ isn’t known
fsck_hfs.c:399: warning: implicit declaration of function ‘stat’
fsck_hfs.c:400: warning: incompatible implicit declaration of built-in function ‘printf’
fsck_hfs.c:400: warning: implicit declaration of function ‘strerror’
fsck_hfs.c:400: error: ‘errno’ undeclared (first use in this function)
fsck_hfs.c:400: warning: format ‘%s’ expects type ‘char *’, but argument 3 has type ‘int’
fsck_hfs.c:410: warning: implicit declaration of function ‘open’
fsck_hfs.c:410: error: ‘O_RDONLY’ undeclared (first use in this function)
fsck_hfs.c:411: warning: incompatible implicit declaration of built-in function ‘printf’
fsck_hfs.c:411: warning: format ‘%s’ expects type ‘char *’, but argument 3 has type ‘int’
fsck_hfs.c:417: warning: implicit declaration of function ‘getWriteAccess’
fsck_hfs.c:420: warning: incompatible implicit declaration of built-in function ‘printf’
fsck_hfs.c:421: error: ‘O_WRONLY’ undeclared (first use in this function)
fsck_hfs.c:442: error: too many arguments to function ‘CacheInit’
fsck_hfs.c:392: warning: unused variable ‘statb’
fsck_hfs.c: At top level:
fsck_hfs.c:459: warning: conflicting types for ‘getWriteAccess’
fsck_hfs.c:459: error: static declaration of ‘getWriteAccess’ follows non-static declaration
fsck_hfs.c:417: error: previous implicit declaration of ‘getWriteAccess’ was here
fsck_hfs.c: In function ‘getWriteAccess’:
fsck_hfs.c:471: error: ‘NULL’ undeclared (first use in this function)
fsck_hfs.c:472: warning: implicit declaration of function ‘malloc’
fsck_hfs.c:472: warning: incompatible implicit declaration of built-in function ‘malloc’
fsck_hfs.c:472: warning: implicit declaration of function ‘strlen’
fsck_hfs.c:472: warning: incompatible implicit declaration of built-in function ‘strlen’
fsck_hfs.c:476: warning: implicit declaration of function ‘strcpy’
fsck_hfs.c:476: warning: incompatible implicit declaration of built-in function ‘strcpy’
fsck_hfs.c:477: warning: incompatible implicit declaration of built-in function ‘strrchr’
fsck_hfs.c:480: error: ‘O_WRONLY’ undeclared (first use in this function)
fsck_hfs.c: At top level:
fsck_hfs.c:531: warning: conflicting types for ‘usage’
fsck_hfs.c:531: error: static declaration of ‘usage’ follows non-static declaration
fsck_hfs.c:139: error: previous implicit declaration of ‘usage’ was here
fsck_hfs.c: In function ‘usage’:
fsck_hfs.c:532: warning: incompatible implicit declaration of built-in function ‘fprintf’
fsck_hfs.c:532: error: ‘stderr’ undeclared (first use in this function)
fsck_hfs.c:544: warning: incompatible implicit declaration of built-in function ‘exit’
make[1]: *** [fsck_hfs.o] Error 1
make[1]: Leaving directory `/usr/src/diskdev_cmds-332.14/fsck_hfs.tproj'
make: *** [all] Error 2
root@ec-desktop:/usr/src/diskdev_cmds-332.14# cp fsck_hfs.tproj/fsck_hfs /sbin/fsck.hfsplus
cp: cannot stat `fsck_hfs.tproj/fsck_hfs': No such file or directory

---

### Post by Seamyst on 2007-05-24
> **Dirk.R.Gently said:**
> If you want to be able to read and write from and HFSplus drive, be sure journaling is off.  To see if your disk/partition is, head to: System > Administration > System Log and click on syslog.  Now, do the ctrl+f key-combo and type in "mount".  If the above partition that we mounted is journaled, there will be a warning here.  To turn off journaling, restart with the OSX install CD, select Disk Utility from the drop down menu, click the drive you want to have journaling shutoff of and use the button Journaling disable.

I tried to do this to my external hard drive, which was Journaled.  Everything went fine until I got into Disk Utility on the Install DVD and tried to find that button.  I couldn't find it.... looked all over the place, but no luck, so finally I had to erase the external drive.  After that I had to boot into regular OS X, select the drive, went into Get Info, and changed Other: to be read/write.

---

### Post by Gen2ly on 2007-05-25
> **Seamyst said:**
> I tried to do this to my external hard drive, which was Journaled.  Everything went fine until I got into Disk Utility on the Install DVD and tried to find that button.  I couldn't find it.... looked all over the place, but no luck, so finally I had to erase the external drive.  After that I had to boot into regular OS X, select the drive, went into Get Info, and changed Other: to be read/write.

Journaling and read/write are entirely different things.  Journaling is pretty much a log of file system so data isnt lost.  I'm bouht my MacBook with 10.4.6 installed, perhaps this version of "Disk Utility" and above have the button for Journaled?  I found a image of this (the button's on the top):

---

### Post by Seamyst on 2007-05-25
No, I have that button too.  When I was in Disk Utility, however, it was still set to Enable Journaling and it was grayed out.  So.... oh well.  At least I can write to my external hard drive from Feisty now, which is what I wanted to do anyway.

---

### Post by Gen2ly on 2007-05-25
I've heard of this sometimes happening, thanks for the information.  I think Disk Utility has a bug for some of us.  I found an alternate method and posted in in the Howto.

---

### Post by ivesjd on 2007-06-21
You shouldn't have to use the boot disc to turn off journaling on an external drive. The reason you need it for you internal drive is because you are booted from it and it has to unmount said drive. That may have been your problem when you were trying to turn it off.

---

### Post by Gen2ly on 2007-06-21
Nice point.  I don't have and external drive but since OS X has the same underpinnings the Linux does this makes definite sense.

---

### Post by ivesjd on 2007-06-21
I don't have one either, but that is what I understand.

---

### Post by Ubivetz on 2007-06-25
Nice try, but:

```

sudo fsck.hfsplus  -r /dev/sda2
** /dev/sda2
** Checking HFS Plus volume.
Segmentation fault (core dumped)

```
And I can't locate core file.

---

### Post by Gen2ly on 2007-06-26
> **Ubivetz said:**
> Nice try, but:

```

sudo fsck.hfsplus  -r /dev/sda2
** /dev/sda2
** Checking HFS Plus volume.
Segmentation fault (core dumped)

```
And I can't locate core file.

Uum.  Getting segmentation-faults are errors in the run enviroment, when a message is recieved that it is dumping the core is just another way of saying it's ditching the app.  I'm not using Ubuntu at the momemnt but maybe someone would be kind enough to produce a deb for you.  It might be a bad idea to sync it to the ubuntu tree?

---

### Post by tgoose on 2007-09-10
I don't suppose there's any way to remove journaling without having OS X, is there? Darn.

---

### Post by cyberdork33 on 2007-09-10
> **tgoose said:**
> I don't suppose there's any way to remove journaling without having OS X, is there? Darn.
No, but if you don't have OSX, then why do you have an HFS+ partition?

---

### Post by oysterpog on 2007-09-28
i cannot get this thing to work. my external hfs+ drive is occasionally removed uncleanly, and won't let me write to it when i reboot. i'm trying to get this fsck working but on the 'make' step it baulks and i don't know what to do.

root@zoltron:/usr/src# cd diskdev_cmds-332.14
root@zoltron:/usr/src/diskdev_cmds-332.14# make -f Makefile.lnx
for d in newfs_hfs.tproj fsck_hfs.tproj; do make -C $d -f Makefile.lnx all; done
make[1]: Entering directory `/usr/src/diskdev_cmds-332.14/newfs_hfs.tproj'
gcc -g3 -Wall -I/usr/src/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o hfs_endian.o hfs_endian.c
hfs_endian.c:30:23: error: sys/types.h: No such file or directory
hfs_endian.c:31:22: error: sys/stat.h: No such file or directory
In file included from hfs_endian.c:34:
/usr/src/diskdev_cmds-332.14/include/missing.h:4:20: error: endian.h: No such file or directory
/usr/src/diskdev_cmds-332.14/include/missing.h:5:22: error: byteswap.h: No such file or directory
/usr/src/diskdev_cmds-332.14/include/missing.h:6:19: error: errno.h: No such file or directory


plus about a thousand more lines of the same thing. anyone know what the problem is?? i'm new to linux, its so frustrating!!!!

edit: i should mention i'm running 7.04 feisty fawn. i've gone so far as to fresh install Feisty, but when trying to go through the steps outlined by Dirk.R.Gently at the beginning of this thread, it always hangs up at the 'make' part. i dont even know what 'make' does... anyway please help, i'm about to start crying.

---

### Post by Ubivetz on 2007-09-28
I know only one way to check and repair HFS+ partition: just load OS X (don't login to save time) and then reboot to Linux back.

P.S. I tried to gain user access to /Users/  at  HFS partition but I haven't succeded.
```

$ sudo  bash
# cd /mnt/Macintosh_HD/Users
# find ./ -type d | xargs chmod a+rx
# find ./ -type f | xargs chmod a+rw

```

---

### Post by oysterpog on 2007-09-28
my osx machine stopped working, i only have a linux box now.

have you tried using the fsck.hfsplus detailed at the beginning of this thread?

---

### Post by Ubivetz on 2007-09-28
> **oysterpog said:**
> my osx machine stopped working, i only have a linux box now.

have you tried using the fsck.hfsplus detailed at the beginning of this thread?
Yes, I tried. This damn buggy utility falls in core, i.e. stops working unexpectedly.

---

### Post by cyberdork33 on 2007-09-28
make is the command used to compile something. The error messages sound like there are some header files missing that need to be compiled against.

Make sure you have installed the build-essential package before trying to compile:
```
sudo apt-get install build-essential
```

---

### Post by oysterpog on 2007-09-28
> **cyberdork33 said:**
> make is the command used to compile something. The error messages sound like there are some header files missing that need to be compiled against.

Make sure you have installed the build-essential package before trying to compile:
```
sudo apt-get install build-essential
```

dork buddy you have solved all my problems. many thanks

---

### Post by matth45 on 2008-03-26
I also get

```
** /dev/sda2
** Checking HFS Plus volume.
Segmentation fault

```

In fact, anyone running a 64-bit build environment will get this. Notice the warnings like:

```
warning: cast to pointer from integer of different size
```

Whoever wrote this code assumed it was only going to be compiled on 32 bit systems (they assume that pointer sizes will be the same as ints).

So you need to pass -m32 to the compiler everywhere to build it as a 32 bit executable. Since the make system is a total hack job here, it's not really easy. Run a make -f Makefile.lnx clean, then add -m32 to the CFLAGS line in in Makefile.lnx in the top level dir. Execute a make -f Makefile.lnx. It will fail after building all the .o files. Then go to diskdev_cmds-332.14/fsck_hfs.tproj and run

```
gcc   fsck_hfs.o strings.o utilities.o cache.o dfalib/libdfa.a   -o fsck_hfs -m32
```

You should end up with the fsck_hfs that you need, which seems to work on my 64 bit system.

This whole thing seems like a total hack. So it's probably safer to boot into OSX and fix it from there if you can.

---

### Post by cyberdork33 on 2008-03-26
> **matth45 said:**
> This whole thing seems like a total hack. So it's probably safer to boot into OSX and fix it from there if you can.I think that is actually the major concensus.

---

### Post by Gen2ly on 2008-03-26
Nice job math45.  This has been a major trip-up for 64bit users for a bit now. :)

I added a link to the tutorial to your post as well as cleaned the tutorial a bit.

Does "fdisk -l" show GPT parition tables?  I don't have my macbook at the time.

Also this doesn't make sense to me:

```
ln -s mkfs.hfsplus mkfs.hfs
```

As there is no "make install" so mkfs.hfsplus shouldn't even be in /sbin.

Since, I don't have the macBook I'd appreciate anyone that could test this for me.

I've also added this tutorial to Apple Intel Users FAQ, please PM me with any ideas/suggestions.

---

### Post by cyberdork33 on 2008-03-26
> **Dirk.R.Gently said:**
> Does "fdisk -l" show GPT parition tables?
no use parted something like:
```
 sudo parted /dev/sda print
```

---

### Post by dwalk on 2008-04-21
I've run into a problem when attempting to get the mkfs.hfsplus command to work....

Following the instructions posted initially everything goes well until I attempt to do this:

```
cp newfs_hfs.tproj/newfs_hfs /sbin/mkfs.hfsplus
```

poking around in newfs_hfs.tproj reveals why, I don't have a newfs_hfs to copy. I do have a newfs_hfs.8, .c and .h though, which really confuses me.

I've tried restarting the process twice with the same result. I used the same source ([http://gentoo.osuosl.org/distfiles/diskdev_cmds-332.14.tar.gz](http://gentoo.osuosl.org/distfiles/diskdev_cmds-332.14.tar.gz)) as was originally posted, however I used a different patch ([http://www.mythic-beasts.com/resources/appletv/mb_boot_tv/diskdev_cmds-332.14.patch.bz2](http://www.mythic-beasts.com/resources/appletv/mb_boot_tv/diskdev_cmds-332.14.patch.bz2)      ) because the one posted was not working.

Could that be the source of the problem? Otherwise what else could it be? 

The fsck.hfsplus seems to be working... when I call it however a comment "missing special-device" pops up, but the usage appears underneath anyway.

---

### Post by xevix on 2008-05-01
Thanks matth45 for the hack, it works beautifully for me.  I have linked back to this post on the gentoo wiki.

---

### Post by flaggh on 2008-05-03
Thank you Dirk and matth45!  I was having trouble with this and did not find it acceptable to have to boot into OSX to check the disk.  I just wanted to run through a few problems I had to hopefully save someone some time, especially those of us, myself included, who are not very proficient at compiling.  Although I'm very comfortable with the command line I really jumped into deep water when I decided to buy a macbook (my last computer was a P3 1.13GHz) and install 64-bit ubuntu on it as my primary operating system.

I won't repeat the portion that Dirk has so clearly layed out but I did want to add that I was unable to download the patch from the address he listed.  Instead I got it from [wget http://www.mythic-beasts.com/resources/appletv/mb_boot_tv/diskdev_cmds-332.14.patch.bz2]("wget http://www.mythic-beasts.com/resources/appletv/mb_boot_tv/diskdev_cmds-332.14.patch.bz2")

Besides adding -m32 to the end of the CFLAGS line, to make and compile successfully I also needed a couple extra libraries I did not have installed:
```
sudo apt-get install libc6-dev-i386 ia32-libs gcc-multilib
```

Hope this helps.

---

### Post by babgolis on 2008-06-18
I'm having permissions problems with my two hfs+ (not journaled) data drives. I'm able to mount them, butr I'm not able to see the contents. 

This is the error I get:

The folder contents can not be displayed 
You do not have the permissions necessary to view the contents of "sdb2".

How do I change the permissions to make this work? When I check the permissions for any of my mac disks in /media it says that they are group 501 and I am not the owner and cannot change the permissions.

Here's my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                           0  0  
# /dev/sda3
UUID=7219195a-679e-41ef-9ef9-b60301fc007e  /              ext3         relatime,errors=remount-ro         0  1  
# /dev/sda4
UUID=615ea36f-7bbd-47e9-814a-efd2e3ce7e3c  none           swap         sw                                 0  0  
/dev/scd1                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8              0  0  
/dev/scd0                                  /media/cdrom1  udf,iso9660  user,noauto,exec,utf8              0  0  
/dev/sda1                                  /media/sda1    ntfs         nls=iso8859-1,noauto,umask=000,ro  0  0  
/dev/sde1                                  /media/sde1    hfsplus      rw,exec,noauto,users               0  0  
/dev/sdb1                                  /media/sdb1    hfsplus      rw,exec,noauto,users               0  0  
/dev/sdb2                                  /media/sdb2    hfsplus      rw,exec,auto,users                 0  0  
/dev/sdc1                                  /media/sdc1    hfsplus      rw,exec,noauto,users               0  0  
/dev/sda2                                  /media/sda2    hfsplus      rw,exec,auto,users                 0  0  
/dev/sdd1                                  /media/sdd1    hfsplus      rw,exec,noauto,users               0  0

---

### Post by flaggh on 2008-06-19
Sounds like a permissions problem.  Post the output of the following command when booted in ubuntu.
```

id

```

---

### Post by babgolis on 2008-06-19
Thanks for your quick reply. Any help is much appreciated!

acubuntu@acubuntu:~$ id
uid=1000(acubuntu) gid=1000(acubuntu) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),107(fuse),109(lpadmin),115(admin),1000(acubuntu)

---

### Post by flaggh on 2008-06-19
Your user must have the same uid (and gid I think) as your mac profile if you wish to have read/write access unless you change the permissions on all the files to be modifiable by users other than the owner (which is not the recommended solution).  You can see from the output you've posted that your ubuntu account user and group id is 1000.  Your mac id is probably 501 but you can find out for sure by booting into OS X and running the same command in the terminal there.  

If this is a fresh installation, I would suggest creating a new user with a user and group id of 501.  If you've already done a lot of user customization that you don't want to repeat it is possible to change the user and group id, you just have to make sure you also change all the files and sudo permissions as well.  There are plenty of posts on the forum regarding how to do this.  Hope this helps.

---

### Post by babgolis on 2008-06-20
Thanks flaggh. I'll give it a whirl this weekend.

---

