---
title: "help with usb hard drive"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by ljpm on 2006-10-16
Hi,

HELP!

I wife has an older Mac G4. Recently we picked up a ACOMDATA 80.0 gig Proton 2.5 USB drive. She is using the drive as an archive. She has transfered, among other things, all our digital pictures. When she logged on this morning the usb drive icon started replicating on the desk top. She tried to unmount, dragged the icon to the trash, the drive. She has since been unable to initialize the drive on her MAC.

I would like to mount the drive on my computer so that I can transfer the files, unfortunately the drive does not mount on boot and, being a noob, I have no idea what to do. 

I can see the drive in the device manager.

Please respond. Wife going crazy about the possibility of losing 5 years of kids pictures.

Thanks in advance.

---

### Post by grim918 on 2006-10-16
You can try to mount the drive by right clicking the device icon and then clicking on mount. if you get an error then you can try to mount it manually.

> sudo mount /dev/<device name> /mnt/macusb

macusb should first be created as a directory inside of your /mnt directory.

---

### Post by ljpm on 2006-10-16
Hi again,

This may sound like a dumb question, but what is the <device name>?

Is that the name my wife labeled her hard drive with, or something like hda1, or is it an arbitrary name I call it to mount?

---

### Post by grim918 on 2006-10-16
It's something like hda1. It could be something else though. Depends on what other drives and partitions are already mounted on your system.

---

### Post by K.Mandla on 2006-10-16
If you enter 

```
sudo fdisk -l
```
you should be able to see the drive's device name. It will look like /dev/sda1 or something like that. If you need help finding it in the list, post the results of that command here and someone will help you pick it out. ;)

---

### Post by ljpm on 2006-10-16
OK guys/gals here is the output.

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *         295       17346   136970190    7  HPFS/NTFS
/dev/hda2               1         294     2361523+  12  Compaq diagnostics
/dev/hda3           17347       18621    10241437+  83  Linux
/dev/hda4           18622       30401    94622850    5  Extended
/dev/hda5           18622       30222    93185001   83  Linux
/dev/hda6           30223       30401     1437786   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sda doesn't contain a valid partition table
******@******-desktop:~$ sudo mount /dev/sda /mnt/macusb
mount: you must specify the filesystem type

1.  It looks like the initial problem might have been with partition table of usb drive. /dev/sda doesn't contain a valid partition table. Please correct me if I am wrong. Possible solution?

2.  how do I specify the filesystem (and what is the filesystem, MAC OSX format).


we're getting close. 

Thanks

---

### Post by K.Mandla on 2006-10-16
Has the drive been partitioned and formatted before? or is it completely blank? 

Either way, *mount* usually likes a -t <file system type> flag afterward. I'm in unfamiliar territory with Mac filesystems, but I'm guessing it's HFS+, so your command might be something like 

```
sudo mount -t hfsplus /dev/sda /mnt/macusb
```
but that's only if it has already been partitioned and formatted as HFS+. Judging by the fdisk output, it might not.

If not, I believe you can partition the drive with 

```
sudo cfdisk /dev/sda
```
You'll have to check the available file systems to find the HFS+ file type. When you're done you can format it with 

```
sudo mkfs.hfsplus /dev/sda1
```
Note the sda1 at the end. Unless I'm mistaken, partitioning the drive should assign sda1 to it. 

Again, I'm in new ground here with Mac file systems, so we're both learning ... ;)

---

### Post by ljpm on 2006-10-16
I just tried to mount and got the following.

******@******-desktop:~# sudo mount -t hfsplus /dev/sda /mnt/usbmac
mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


from dmesg

[17179592.808000] usb-storage: device scan complete
[17179592.828000] Driver 'sd' needs updating - please use bus_type methods
[17179592.828000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[17179592.828000] sda: assuming drive cache: write through
[17179592.832000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[17179592.832000] sda: assuming drive cache: write through
[17179592.832000]  sda: [mac] sda1 sda2 sda3 sda4 sda5 sda6 sda7 sda8 sda9 sda10 sda11
[17179593.220000] sd 4:0:0:0: Attached scsi disk sda
[17179593.224000] sd 5:0:0:0: Attached scsi removable disk sdb
[17179593.248000] sd 5:0:0:1: Attached scsi removable disk sdc
[17179593.260000] sd 5:0:0:2: Attached scsi removable disk sdd
[17179593.268000] sd 5:0:0:3: Attached scsi removable disk sde
[17179593.288000] sd 4:0:0:0: Attached scsi generic sg0 type 0
[17179593.288000] sd 5:0:0:0: Attached scsi generic sg1 type 0
[17179593.288000] sd 5:0:0:1: Attached scsi generic sg2 type 0
[17179593.288000] sd 5:0:0:2: Attached scsi generic sg3 type 0
[17179593.288000] sd 5:0:0:3: Attached scsi generic sg4 type 0



This is not looking good....

---

### Post by ljpm on 2006-10-17
This is looking like a problem with the hard drive itself, most likely the partition tables.

If any one can help out it would be greatly appreciated.

---

