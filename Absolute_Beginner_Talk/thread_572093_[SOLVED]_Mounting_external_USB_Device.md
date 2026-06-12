---
title: "[SOLVED] Mounting external USB Device"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by ghandi69_ on 2007-10-10
Hey guys,

I'm using fluxbox, and I'm having trouble mounting an external USB harddrive.  To my knowledge, the Hard drive is ext3.  It used to be connected through sata inside my computer, and it woudl show up under media/disk.  I decided to place it in a case and go through USB so I can carry it around.  I have the volume manager plug in for thunar turned on, but thunar seems unable to handle it.

After plugging the hard drive in through USB, my dmesg | tail looks as follows.

>  usb 2-1: USB disconnect, address 8
[ 2385.219844] usb 2-1: new high speed USB device using ehci_hcd and address 9
[ 2385.371561] usb 2-1: configuration #1 chosen from 1 choice
[ 2385.372207] scsi10 : SCSI emulation for USB Mass Storage devices
[ 2385.372250] usb-storage: device found at 9
[ 2385.372252] usb-storage: waiting for device to settle before scanning
[ 2390.366313] usb-storage: device scan complete
[ 2390.367432] scsi 10:0:0:0: Direct-Access                                    PQ: 0 ANSI: 2 CCS
[ 2390.370331] sd 10:0:0:0: Attached scsi disk sdb
[ 2390.370369] sd 10:0:0:0: Attached scsi generic sg1 type 0


Currently, sda, sda1, sda2, & sda 5 are partitions for for my primary hard drive.

Upon reading my dmesg, and I tried the following commands

mount -t ext3 /dev/sg1 /mnt/WD200 (I already created the directory), and it gives me the following output.

> mount: /dev/sg1 is not a block device


I tried at sdb as well, and I get

> mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


Any ideas?

---

### Post by logos34 on 2007-10-10
try 

**sudo mount -t ext3 /dev/sdb1 /mnt/WD200**

anything?

---

### Post by ghandi69_ on 2007-10-10
Tried that and...

>  sudo mount -t ext3 /dev/sdb1 /mnt/WD200
mount: special device /dev/sdb1 does not exist


---

### Post by ghandi69_ on 2007-10-10
Another thing to note,  is that sudo fdisk -l only returns...

> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30024   241167748+  83  Linux
/dev/sda2           30025       30401     3028252+   5  Extended
/dev/sda5           30025       30401     3028221   82  Linux swap / Solaris


---

### Post by ghandi69_ on 2007-10-10
Hey guys, in turns out my hard drive was in pretty bad condition.  I download gparted, and not even that program could read it to reformat it.  I eventually hooked up the hard drive in my computer as if it was the only hard drive avaiable, and ran the server install disk to reformat it, after doing so, I hooked it back up through USB, and it worked like a charm.

---

