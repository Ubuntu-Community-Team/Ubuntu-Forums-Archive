---
title: "fstab conflict?"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-08-21
I'm very confused about my dvd player. It doesn't work, but is found  in  /etc/fstab. However, System/Preferences/Hardware Information shows the floppy but I can't find the CD-RW or the dvd.

I looked at these, but found nothing significant

[http://ubuntuforums.org/showthread.php?t=425610](http://ubuntuforums.org/showthread.php?t=425610)

[http://ubuntuforums.org/showthread.php?t=167015](http://ubuntuforums.org/showthread.php?t=167015)

mark@Lexington:~$ dmesg | tail
[   78.801292] Bluetooth: L2CAP socket layer initialized
[   78.811609] Bluetooth: RFCOMM socket layer initialized
[   78.811641] Bluetooth: RFCOMM TTY layer initialized
[   78.811648] Bluetooth: RFCOMM ver 1.8
[   83.845417] NET: Registered protocol family 10
[   83.845731] lo: Disabled Privacy Extensions
[   94.516234] ath0: no IPv6 routers present
[  118.130560] ath0: no IPv6 routers present
[ 5673.903154] sr1: disc change detected.
[ 5709.915199] sr1: disc change detected.
mark@Lexington:~$ 

fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9dea8cc1-82db-49a6-85fe-cf8d41d5f398 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=82ad16ec-a20d-406e-ba15-becd1f1e6342 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

/dev/sdb1 /mnt/Drive2	ext3	defaults	0	2
#above line added by mp on july 25, 2007
======================
Trying to mount what Places/Computer calls CD-ROM 2

mount: special device /dev/scd1 does not exist

How can that be? fstab shows /dev/scd1!

---

### Post by kevstar31 on 2007-08-22
> mount: special device /dev/scd1 does not exist

How can that be? fstab shows /dev/scd1!
Fstab does not create devices it only stores to options for mounting them. Post the output of: fdisk -l

---

### Post by igknighted on 2007-08-22
Are those scsi drives?  That device location looks awful odd... usually it is /dev/sdc or /dev/hdc or something along those lines...

---

### Post by Mark_in_Hollywood on 2007-08-22
I have as part of my signature, and I think everyone should do the same:

Dell Dimension 4100 730 Meg CPU, 384 Meg RAM, 40Gig HDD, D-Link WDA2320 wireless adapter, Brother HL-1440 printer, 
[B]
Samsung DVD-rom SD-612, 	EIDE/ATAPI

Sony CD-RW CRX-225E, [/B]      IDE/EIDE

As far as I can tell, these are ATA devices. The cable/connectors from the m/b to the devices isn't a scsi cable. 

and per Kevdog's command:

mark@Lexington:~$ fdisk -l

Disk /dev/sdc: 257 MB, 257949696 bytes
16 heads, 32 sectors/track, 984 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         984      251888    e  W95 FAT16 (LBA)

---

### Post by kevstar31 on 2007-08-22
Sorry I forgot fdisk -l only lists hard drives. Try: ls /dev |grep hd

---

### Post by Mark_in_Hollywood on 2007-08-22
mark@Lexington:~$ ls /dev |grep hd
watchdog


Huhh?

---

### Post by annda on 2007-08-22
> **Mark_in_Hollywood said:**
> 

mark@Lexington:~$ dmesg | tail
[   78.801292] Bluetooth: L2CAP socket layer initialized
[   78.811609] Bluetooth: RFCOMM socket layer initialized
[   78.811641] Bluetooth: RFCOMM TTY layer initialized
[   78.811648] Bluetooth: RFCOMM ver 1.8
[   83.845417] NET: Registered protocol family 10
[   83.845731] lo: Disabled Privacy Extensions
[   94.516234] ath0: no IPv6 routers present
[  118.130560] ath0: no IPv6 routers present
[B][ 5673.903154] sr1: disc change detected.
[ 5709.915199] sr1: disc change detected.[/B]
mark@Lexington:~$ 

---snip---

Trying to mount what Places/Computer calls CD-ROM 2

mount: special device /dev/scd1 does not exist



so your cdrom is /dev/sr1. /dev/scd1 should be linked to it but for some reason it isn't. the other drive is probably sr0 - you can check that by

```
dmesg | egrep sr[0-9]
```

you can either try to create a symlink from sr1 to scd1 (i'm not 100% sure if it will work), or change fstab to include sr1. i hope this helps.

---

### Post by Mark_in_Hollywood on 2007-08-22
Ergh . . . no . . .

The output of dmesg | tail was done immediately after Places/Computer/CD-ROM/DVD-RW was asked to run (double click).

I'm not even sure I'm understanding your post what-so-ever. I need to rename the fstab line(s) according to that output?

could you please give me an example line?

mark@Lexington:~$ dmesg | egrep sr1
[   38.961167] sr1: scsi3-mmc drive: 4x/32x cd/rw xa/form2 cdda tray
[   38.961781] sr 1:0:1:0: Attached scsi CD-ROM sr1

mark@Lexington:~$ dmesg | egrep sr0
[   38.936280] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   38.936766] sr 1:0:0:0: Attached scsi CD-ROM sr0
mark@Lexington:~$

---

### Post by igknighted on 2007-08-22
> **Mark_in_Hollywood said:**
> Ergh . . . no . . .

The output of dmesg | tail was done immediately after Places/Computer/CD-ROM/DVD-RW was asked to run (double click).

I'm not even sure I'm understanding your post what-so-ever. I need to rename the fstab line(s) according to that output?

could you please give me an example line?

mark@Lexington:~$ dmesg | egrep sr1
[   38.961167] sr1: scsi3-mmc drive: 4x/32x cd/rw xa/form2 cdda tray
[   38.961781] sr 1:0:1:0: **Attached scsi CD-ROM **sr1

mark@Lexington:~$ dmesg | egrep sr0
[   38.936280] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   38.936766] sr 1:0:0:0: **Attached scsi CD-ROM **sr0
mark@Lexington:~$

I KNEW I wasn't going crazy!

Change the scd's in the fstab file to the sr's and reboot... you should be all set.

---

### Post by annda on 2007-08-22
sorry if i was too cryptic. it looks like you drives are actually sr0 and sr1 - your dmesg output confirms that.

please **do backup** your fstab first! you can do it by running nautilus as root (ALT+F2>gksudo nautilus) or in the terminal:

```
sudo cp /etc/fstab /etc/fstab.bak
```

then modify the original fstab. ALT+F2> gksudo gedit /etc/fstab

replace those lines:
> /dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto 0 0

with
> /dev/sr0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/sr1 /media/cdrom1 udf,iso9660 user,noauto 0 0

now the safest thing is to reboot.

if this doesn't work, restore the backup in the terminal:

```
sudo cp /etc/fstab.bak /etc/fstab
```

---

### Post by Mark_in_Hollywood on 2007-08-22
> **annda said:**
> sorry if i was too cryptic. it looks like you drives are actually sr0 and sr1 - your dmesg output confirms that.

please **do backup** your fstab first! you can do it by running nautilus as root (ALT+F2>gksudo nautilus) or in the terminal:

```
sudo cp /etc/fstab /etc/fstab.bak
```

then modify the original fstab. ALT+F2> gksudo gedit /etc/fstab

now the safest thing is to reboot.

if this doesn't work, restore the backup in the terminal:

```
sudo cp /etc/fstab.bak /etc/fstab
```

OK -- Done and done, but no change as yet, DVD still says not mounted and upon commanding mount -- unable to mount, probably no media in the drive -- which ain't true.

As for IgKnighted's I KNEW I wasn't going crazy! -- but I AM!

Also, after attempting sudo mount -a, and dmesg | tail

mark@Lexington:~$ dmesg | tail
[  269.933127] Bluetooth: L2CAP ver 2.8
[  269.933140] Bluetooth: L2CAP socket layer initialized
[  269.946561] Bluetooth: RFCOMM socket layer initialized
[  269.946601] Bluetooth: RFCOMM TTY layer initialized
[  269.946608] Bluetooth: RFCOMM ver 1.8
[  269.992928] usb 1-1.3: configuration #1 chosen from 1 choice
[  274.765706] NET: Registered protocol family 10
[  274.765965] lo: Disabled Privacy Extensions
[  285.090837] ath0: no IPv6 routers present
[  322.570163] ath0: no IPv6 routers present

So at least the system isn't as confused as before . . . I wish I werent.

---

