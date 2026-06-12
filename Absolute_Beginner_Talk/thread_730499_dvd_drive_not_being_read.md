---
title: "dvd drive not being read"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by pdan on 2008-03-20
help please -- my internal dvd drive has stopped working.  the drive used to work but now it just spins and i get error messages saying there is probably no media loaded.  the drive has always worked in the past.  i am running feisty

can someone point me to the steps of troubleshooting this problem

---

### Post by unutbu on 2008-03-20
Please post output to
```

sudo lshw -C disk

```

---

### Post by pdan on 2008-03-20
*-disk                  
       description: SCSI Disk
       product: ST3400832AS
       vendor: ATA
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 3.03
       serial: 4NF0PB21
       size: 372GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
     *-volume:0
          description: HPFS/NTFS partition
          physical id: 1
          bus info: scsi@0:0.0.0,1
          logical name: /dev/sda1
          capacity: 78GB
          capabilities: primary bootable
     *-volume:1
          description: Extended partition
          physical id: 2
          bus info: scsi@0:0.0.0,2
          logical name: /dev/sda2
          size: 294GB
          capacity: 294GB
          capabilities: primary extended partitioned partitioned:extended
        *-logicalvolume:0
             description: Linux filesystem partition
             physical id: 5
             logical name: /dev/sda5
             capacity: 268GB
        *-logicalvolume:1
             description: Linux filesystem partition
             physical id: 6
             logical name: /dev/sda6
             capacity: 22GB
        *-logicalvolume:2
             description: Linux swap / Solaris partition
             physical id: 7
             logical name: /dev/sda7
             capacity: 3545MB
             capabilities: nofs
  *-disk:0
       description: SCSI Disk
       product: Flash HS-CF
       vendor: ASUS
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sdb
       version: 3.95
       capabilities: removable
     *-disc
          physical id: 0
          logical name: /dev/sdb
  *-disk:1
       description: SCSI Disk
       product: Flash HS-COMBO
       vendor: ASUS
       physical id: 0.0.1
       bus info: scsi@2:0.0.1
       logical name: /dev/sdc
       version: 3.95
       capabilities: removable
     *-disc
          physical id: 0
          logical name: /dev/sdc
  *-cdrom
       description: DVD writer
       product: _NEC DVD_RW ND-3550A
       physical id: 0
       bus info: ide@0.0
       logical name: /dev/hda
       version: 1.05
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r
       configuration: mode=udma2
     *-disc
          physical id: 0
          logical name: /dev/hda

---

### Post by unutbu on 2008-03-20
Look in /var/log/messages. Do you see any errors related to the DVD?

---

### Post by pdan on 2008-03-20
yes

Mar 20 23:26:38 pauldanis-desktop -- MARK --
Mar 20 23:28:46 pauldanis-desktop kernel: [ 2625.660142] hda: tray open
Mar 20 23:28:46 pauldanis-desktop kernel: [ 2625.660566] end_request: I/O error, dev hda, sector 0
Mar 20 23:28:46 pauldanis-desktop kernel: [ 2625.660848] hda: tray open
Mar 20 23:28:46 pauldanis-desktop kernel: [ 2625.661305] end_request: I/O error, dev hda, sector 0
Mar 20 23:28:46 pauldanis-desktop kernel: [ 2625.661517] hda: tray open
Mar 20 23:28:46 pauldanis-desktop kernel: [ 2625.661942] end_request: I/O error, dev hda, sector 4
Mar 20 23:28:46 pauldanis-desktop kernel: [ 2625.662212] hda: tray open
Mar 20 23:28:46 pauldanis-desktop kernel: [ 2625.662811] end_request: I/O error, dev hda, sector 0
Mar 20 23:28:46 pauldanis-desktop kernel: [ 2625.663068] hda: tray open
Mar 20 23:28:46 pauldanis-desktop kernel: [ 2625.663467] end_request: I/O error, dev hda, sector 4
Mar 20 23:28:46 pauldanis-desktop kernel: [ 2625.663702] hda: tray open
Mar 20 23:28:46 pauldanis-desktop kernel: [ 2625.664136] end_request: I/O error, dev hda, sector 0
Mar 20 23:28:46 pauldanis-desktop kernel: [ 2625.664371] hda: tray open
Mar 20 23:28:46 pauldanis-desktop kernel: [ 2625.664796] end_request: I/O error, dev hda, sector 4
Mar 20 23:28:46 pauldanis-desktop kernel: [ 2625.665199] hda: tray open
Mar 20 23:28:46 pauldanis-desktop kernel: [ 2625.665623] end_request: I/O error, dev hda, sector 0
Mar 20 23:28:46 pauldanis-desktop kernel: [ 2625.665857] hda: tray open
Mar 20 23:28:46 pauldanis-desktop kernel: [ 2625.666296] end_request: I/O error, dev hda, sector 4
Mar 20 23:28:46 pauldanis-desktop kernel: [ 2625.666600] hda: tray open
Mar 20 23:28:46 pauldanis-desktop kernel: [ 2625.667107] end_request: I/O error, dev hda, sector 0
Mar 20 23:28:46 pauldanis-desktop kernel: [ 2625.667450] hda: tray open
Mar 20 23:28:46 pauldanis-desktop kernel: [ 2625.667995] end_request: I/O error, dev hda, sector 4

---

### Post by unutbu on 2008-03-21
Would you please post
```

sudo fdisk -l
cat /etc/fstab

```

---

### Post by pdan on 2008-03-21
Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10199    81923436    7  HPFS/NTFS
/dev/sda2           10200       48641   308785365    5  Extended
/dev/sda5           10200       45257   281603353+  83  Linux
/dev/sda6           45258       48189    23551258+  83  Linux
/dev/sda7           48190       48641     3630658+  82  Linux swap / Solaris


:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=c1e81847-e7a8-4408-8149-5617be85dd3d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=5b8316a7-91a9-4b1a-ab7e-ead94a5c396b /home           ext3    defaults        0       2
# /dev/sda1
UUID=0A442B43442B313D /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=62930a90-2fdc-4288-84a8-dce55d923752 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/fd1        /media/floppy1  auto    rw,user,noauto  0       0
#mount maxtor storage device (maxdrive) music library (MusicLib) ==> changed from smbfs to cifs due to many samba timeouts
//192.168.1.210/Public          /media/maxdrive         cifs            credentials=/root/.smbcredentials,uid=1000,gid=1000,file_mode=0777,dir_mode=0777   00

---

### Post by unutbu on 2008-03-21
If you boot from a LiveCD, is the problem still there?

Can you give more detail about 

1) when it spins (constantly, or only when you put in a DVD?), 

2) what program (if any) are you using when you get the error message "no media loaded". 

3) Is there any new software that you've installed, or any updates that you've downloaded recently? (These are probably obvious things you've already considered, but I thought I'd ask.)

---

### Post by pdan on 2008-04-06
Thanks for your help.  I swapped the drive out and now my system is ok.  I guess the old drive just died.

---

