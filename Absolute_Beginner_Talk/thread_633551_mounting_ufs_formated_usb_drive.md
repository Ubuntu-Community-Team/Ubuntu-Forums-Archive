---
title: "mounting ufs formated usb drive?"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by tyto_alba on 2007-12-06
Hi,

I have a some old  hard drives (two of them where configured as software raid1) I'd like to reactivate.   The plan is to copy the files to my internal harddrive, then format the old disks with a more suitable file system (by the way- what fs would you recommend if I"m going to use the disks for backups).  But so far I have not been able to mount any of them.

As I am really new to Linux, and not good with computers anyway,  I just paste some console output:

tr@big-picture:~$ dmesg |tail -20
[  768.915089] Initializing USB Mass Storage driver...
[  768.915126] scsi6 : SCSI emulation for USB Mass Storage devices
[  768.915157] usb-storage: device found at 3
[  768.915158] usb-storage: waiting for device to settle before scanning
[  768.915165] usbcore: registered new interface driver usb-storage
[  768.915167] USB Mass Storage support registered.
[  773.906266] usb-storage: device scan complete
[  773.906947] scsi 6:0:0:0: Direct-Access     Hitachi  HDT725025VLAT80  V5DO PQ: 0 ANSI: 0
[  773.908253] sd 6:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[  773.909127] sd 6:0:0:0: [sdb] Write Protect is off
[  773.909130] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  773.909131] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  773.909999] sd 6:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[  773.910811] sd 6:0:0:0: [sdb] Write Protect is off
[  773.910814] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  773.910815] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  773.910817]  sdb:
[  773.930247] sd 6:0:0:0: [sdb] Attached SCSI disk
[  773.930274] sd 6:0:0:0: Attached scsi generic sg2 type 0
[  774.131998] ufs was compiled with read-only support, can't be mounted as read-write

tr@big-picture:~$ sudo mount -r -t ufs -o ufstype=44bsd /dev/sdb /media/usb
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

tr@big-picture:~$ dmesg|tail
[  773.909131] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  773.909999] sd 6:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[  773.910811] sd 6:0:0:0: [sdb] Write Protect is off
[  773.910814] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  773.910815] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  773.910817]  sdb:
[  773.930247] sd 6:0:0:0: [sdb] Attached SCSI disk
[  773.930274] sd 6:0:0:0: Attached scsi generic sg2 type 0
[  774.131998] ufs was compiled with read-only support, can't be mounted as read-write
[  932.246444] ufs_read_super: bad magic number

Is that enough for you guys to send me off in the right direction?

---

### Post by ajmorris on 2007-12-06
can you post the output of sudo fdisk -l please?

---

### Post by tyto_alba on 2007-12-07
sure,  here we go:

tr@big-picture:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004f231

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37777   303443721   83  Linux
/dev/sda2           37778       38913     9124920    5  Extended
/dev/sda5           37778       38913     9124888+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System

---

### Post by kidders on 2007-12-07
Hi there,

Your USB hard drive doesn't seem to have a partition table on it, which is odd ... and your Linux seems to recognise the entire block device as a UFS filesystem, which is even odder. (The "bad magic number" message suggest that it may not be UFS at all.) How was the RAID array created in the first place?

If it's not a software RAID array, then you probably won't be able to access it without the hardware that originally created it.

---

### Post by tyto_alba on 2007-12-07
I just tried one of the other disks. Here is what it looks like:

tr@big-picture:~$ dmesg |tail -20
[ 1293.900256] usb-storage: device found at 4
[ 1293.900257] usb-storage: waiting for device to settle before scanning
[ 1298.890715] usb-storage: device scan complete
[ 1298.891336] scsi 7:0:0:0: Direct-Access     Hitachi  HDT725025VLAT80  V5DO PQ: 0 ANSI: 0
[ 1298.892448] sd 7:0:0:0: [sdc] 488397168 512-byte hardware sectors (250059 MB)
[ 1298.893337] sd 7:0:0:0: [sdc] Write Protect is off
[ 1298.893339] sd 7:0:0:0: [sdc] Mode Sense: 03 00 00 00
[ 1298.893340] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[ 1298.894195] sd 7:0:0:0: [sdc] 488397168 512-byte hardware sectors (250059 MB)
[ 1298.895071] sd 7:0:0:0: [sdc] Write Protect is off
[ 1298.895073] sd 7:0:0:0: [sdc] Mode Sense: 03 00 00 00
[ 1298.895075] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[ 1298.895076]  sdc: sdc1
[ 1298.914417]  sdc1: <bsd: >
[ 1298.914447] sd 7:0:0:0: [sdc] Attached SCSI disk
[ 1298.914470] sd 7:0:0:0: Attached scsi generic sg2 type 0
[ 1299.021306] md: md0 stopped.
[ 1299.021315] md: unbind<sdb>
[ 1299.021318] md: export_rdev(sdb)
[ 1299.053218] md: bind<sdc>

tr@big-picture:~$ sudo fdisk -l

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
16 heads, 63 sectors/track, 484521 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1      484521   244198072+  a5  FreeBSD


Does that mean the drive was mounted properly? But then it should show up in the file manager shouldn't it?
Anyway  I still can't  access the drive  and when I try to mount the drive manually I get the following message: "mount: /dev/sdc already mounted or /media/usb busy".

---

### Post by tyto_alba on 2007-12-07
I don't know hoe the raid was created. The disk where used in a FreeNAS fileserver. Does that help?

---

### Post by kidders on 2007-12-07
Aha... that's more like it. :-) Perhaps the other disk was just damaged.

I don't have an Ubuntu box handy just now, so I can't check for you, but you might want to just make certain your Linux has the necessary supports built into it (BSD disk labels & UFS filesystem support). You *should* find something like the following...```
$ grep BSD_DISKLABEL /boot/config-`uname -r`
CONFIG_BSD_DISKLABEL=y
$ grep UFS /boot/config-`uname -r`
CONFIG_UFS_FS=m
```

That way, if you run into trouble, you can be sure it's not Ubuntu's fault. I would suggest playing around with mdadm, just to see if it sees your array. If you can establish that it can, *then* it's time to wonder about mounting the filesystem on it. Ideally, something simple like "sudo mount /dev/md0 /mnt/somewhere" would work for you ... ie Ubuntu *should* be able to autodetect the right filesystem without the help of "-t ufs" and so on.

Could you check whether /dev/md0 (or something with a similar name) exists? If it does, please post the output of **sudo mdadm --detail /dev/md0** and **cat /proc/mdstat**. With some luck, you will see Ubuntu describe your array as "clean" and "degraded". If you can't make mdadm spit out those words, I wouldn't expect you to be able to access the filesystem on the array.

---

### Post by kidders on 2007-12-07
> **tyto_alba said:**
> I don't know hoe the raid was created. The disk where used in a FreeNAS fileserver. Does that help?Yep... that helps. :-) I'll have to do some reading to be sure, but at first glance, it appears likely the array is software-based.

Sorry for replying to myself btw.

---

### Post by tyto_alba on 2007-12-07
Thanks, Here is what I got:

tr@big-picture:~$ grep BSD_DISKLABEL /boot/config-`uname -r` CONFIG_BSD_DISKLABEL=y
/boot/config-2.6.22-14-generic:CONFIG_BSD_DISKLABEL=y
grep: CONFIG_BSD_DISKLABEL=y: No such file or directory

tr@big-picture:~$ grep UFS /boot/config-`uname -r`CONFIG_UFS_FS=m
grep: /boot/config-2.6.22-14-genericCONFIG_UFS_FS=m: No such file or directory

And /dev/md0 does not exist. Should I create an empty folder with that name?

---

### Post by kidders on 2007-12-07
No, but it might be worth checking /dev/sdc & /dev/sdc1 out though.

By the way, have you checked out the FreeNAS support documentation? There may be some hints in it about what exactly is on your disks.

---

### Post by tyto_alba on 2007-12-14
Sorry for my long absence, had to go on an urgent business trip.

Anyway I think I found the problem:
in  /etc/mdadm/mdadm.conf  there is this line:
ARRAY /dev/md0 level=raid5 num-devices=3 UUID=7ed8cc03:d28f65b6:814a2913:a1b73fdf
which is definitely wrong. Two of the disks where configured as RAID1 (mirror) and one was used as a plain single drive.
As I have a DVD backup of everything that was on the RAID, and just finished copying the stuff back   to my PC I do not mind about keeping _that_ data intact. But I still need to access the stuff on the single drive...

Any suggestions how to figure out which drive is which and how to mount the right one?

Thanks

---

