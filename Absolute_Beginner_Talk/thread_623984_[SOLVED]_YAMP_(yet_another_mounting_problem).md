---
title: "[SOLVED] YAMP (yet another mounting problem)"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by Xiong Chiamiov on 2007-11-26
So, I'm converting this old pc into a samba fileserver for some windows machines.  The original hard drive that the OS is on (Kubuntu gutsy) is rather small, so I added another hard drive to store all the files.  I used gparted to partition it, and if I mount it manually, it mounts just fine.  However, I would like it to mount automatically, so I added it into fstab:
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=57bf8ec2-1c2b-4b6c-a480-3b83106ace71 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=2049b0f9-1ad1-45fd-8942-7729ecc28a54 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sdb1    /media/samba   fat32    rw,users,owner,share,unmask=0000   0    0


and also,
> 
noname@serverness:~$ sudo lshw -C disk
[sudo] password for noname:
  *-disk:0
       description: SCSI Disk
       product: IC35L020AVVN07-0
       vendor: ATA
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: VA1O
       serial: VNP110B1G5JB9B
       size: 19GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
  *-disk:1
       description: SCSI Disk
       product: ST3160815A
       vendor: ATA
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/sdb
       version: 3.AA
       serial: 9RA2NFQY
       size: 149GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
  *-cdrom
       description: SCSI CD-ROM
       product: CD-ROM CRD-8483B
       vendor: LG
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.05
       capabilities: removable audio
       configuration: ansiversion=5 status=open
noname@serverness:~$     


So, as you can see, it is sdb that is the larger one, as well as what I'm attempting to mount.  However, when I start up, my media folder shows that only the first hard drive is mounted, and when I check /media/samba, it is 18gigs with 27% used, which matches my first hard drive as well.

[EDIT]
and here is fstab as well:
> 
noname@serverness:~$ sudo fdisk -l
[sudo] password for noname:

Disk /dev/sda: 20.5 GB, 20576747520 bytes
255 heads, 63 sectors/track, 2501 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x971b971b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2392    19213708+  83  Linux
/dev/sda2            2393        2501      875542+   5  Extended
/dev/sda5            2393        2501      875511   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007ead6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19457   156288321    b  W95 FAT32
noname@serverness:~$  


---

### Post by Xiong Chiamiov on 2007-11-27
bump

---

### Post by Xiong Chiamiov on 2007-11-29
bump

---

### Post by Xiong Chiamiov on 2007-11-29
Ok, so more experimenting found that fstab wasn't mounting *anything* to /media/samba.  Everything's fine (well, not permissions) when I mount the drive manually:
> 
noname@serverness:/media$ sudo mount /dev/sdb1 /media/samba
noname@serverness:/media$

I've also updated my fstab, though it didn't seem to do anything.
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=57bf8ec2-1c2b-4b6c-a480-3b83106ace71 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=2049b0f9-1ad1-45fd-8942-7729ecc28a54 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sdb1    /media/samba   auto    rw,user,unmask=0000   0    0

Will do more experimenting tonight, but I'm really just floundering around in man pages, since I don't really know what I'm doing.

---

### Post by Xiong Chiamiov on 2007-11-29
/sigh
While I was reading some man pages or the other, I noticed that in my fstab I was using unmask, while it's supposed to be umask (look carefully).  That was it, and now it's fixed.  I really only noticed because I tried unmount-ing earlier, and found out it was umount.  Well, the end is achieved.

---

