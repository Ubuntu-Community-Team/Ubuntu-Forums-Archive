---
title: "ubuntu wont detect my Memory stick"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by Pabx on 2007-12-27
Thats my problem, it wont detect my memory stick can you help please?

:grin:

---

### Post by taurus on 2007-12-27
It doesn't automount when you plug it in or it doesn't even "see" it?  Can you post the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```
That is a lower case letter L.

---

### Post by jas0 on 2007-12-27
Here's another thing you can do to help us diagnose the problem. Plug in your USB stick into a port, wait 10 seconds and run:

```
dmesg
```

Copy and paste the last 25 or so lines here.

---

### Post by Pabx on 2007-12-27
> **taurus said:**
> It doesn't automount when you plug it in or it doesn't even "see" it?  Can you post the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```
That is a lower case letter L.

Well it doesn't even see it... look:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3e5cf245

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3952    31744408+   b  W95 FAT32
/dev/sda2            3953        7582    29157975   83  Linux
/dev/sda3            7583        9729    17245777+  83  Linux

Disk /dev/sdb: 30.0 GB, 30020272128 bytes
240 heads, 63 sectors/track, 3877 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x9800481f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3499    26452408+   c  W95 FAT32 (LBA)
/dev/sdb2            3500        3877     2857680    f  W95 Ext'd (LBA)
/dev/sdb5            3500        3877     2857648+   7  HPFS/NTFS

---

### Post by Pabx on 2007-12-27
> **jas0 said:**
> Here's another thing you can do to help us diagnose the problem. Plug in your USB stick into a port, wait 10 seconds and run:

```
dmesg
```

Copy and paste the last 25 or so lines here.

Here it is:

[  131.256000] ISO 9660 Extensions: Microsoft Joliet Level 3
[  131.256000] ISOFS: changing to secondary root
[  142.556000] program gparted is using a deprecated SCSI ioctl, please convert it to SG_IO
[  145.788000] end_request: I/O error, dev fd0, sector 0
[  149.000000] end_request: I/O error, dev fd0, sector 0
[  178.024000] NET: Registered protocol family 10
[  178.024000] lo: Disabled Privacy Extensions
[  178.024000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  219.076000] usb 5-7: USB disconnect, address 3
[  241.120000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  241.120000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  243.276000] NET: Registered protocol family 17
[  245.344000] eth0: link down
[  247.044000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  247.044000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  268.368000] eth0: no IPv6 routers present
[  922.404000] usb 5-7: new high speed USB device using ehci_hcd and address 4
[  922.536000] usb 5-7: configuration #1 chosen from 1 choice
[  922.536000] scsi3 : SCSI emulation for USB Mass Storage devices
[  922.536000] usb-storage: device found at 4
[  922.536000] usb-storage: waiting for device to settle before scanning
[  927.536000] usb-storage: device scan complete
[  927.540000] scsi 3:0:0:0: Direct-Access     Sony     PSP              1.00 PQ: 0 ANSI: 0 CCS
[  927.544000] sd 3:0:0:0: [sdc] Attached SCSI removable disk
[  927.544000] sd 3:0:0:0: Attached scsi generic sg3 type 0

---

### Post by jas0 on 2007-12-27
From the looks of it, to me if seems like the USB memory stick is unformatted. Try the following (**ONLY IF YOU DO NOT HAVE DATA ON THE USB STICK!**):

```

sudo fdisk /dev/sdc
n
p
select the default starting and ending numbers
t
1 (select the W95FAT32 option)
sudo mkfs.vfat -I -n USB /dev/sdc1
sudo mkdir /media/USB
sudo mount /dev/sdc1 /media/USB
```

---

### Post by Pabx on 2007-12-27
> **jas0 said:**
> From the looks of it, to me if seems like the USB memory stick is unformatted. Try the following (**ONLY IF YOU DO NOT HAVE DATA ON THE USB STICK!**):

```

sudo fdisk /dev/sdc
n
p
select the default starting and ending numbers
t
1 (select the W95FAT32 option)
sudo mkfs.vfat -I -n USB /dev/sdc1
sudo mkdir /media/USB
sudo mount /dev/sdc1 /media/USB
```

Yes i think is unformatted but here is what happened:

pablo@pabx-desktop:~$ sudo fdisk /dev/sdc

Unable to open /dev/sdc
pablo@pabx-desktop:~$ n
bash: n: command not found
pablo@pabx-desktop:~$ p
bash: p: command not found
pablo@pabx-desktop:~$ select the default starting and ending numbers
bash: syntax error near unexpected token `default'
pablo@pabx-desktop:~$ t
bash: t: command not found
pablo@pabx-desktop:~$ 1 (select the W95FAT32 option)
bash: syntax error near unexpected token `select'
pablo@pabx-desktop:~$ sudo mkfs.vfat -I -n USB /dev/sdc1
mkfs.vfat 2.11 (12 Mar 2005)
/dev/sdc1: No such file or directory
pablo@pabx-desktop:~$ sudo mkdir /media/USB
pablo@pabx-desktop:~$ mount /dev/sdc1 /media/USB

---

### Post by lswest on 2007-12-27
the letters were supposed to be typed into fdisk, and since it didnt open, they were kind of useless, so the main part of that post tells us that the drive couldnt be opened.  are you sure the stick is sdc?  or you might want to try gparted, just to check if it can be recognized at all.

---

### Post by Pabx on 2007-12-27
> **lswest said:**
> the letters were supposed to be typed into fdisk, and since it didnt open, they were kind of useless, so the main part of that post tells us that the drive couldnt be opened.  are you sure the stick is sdc?  or you might want to try gparted, just to check if it can be recognized at all.

Gparted wont recognize it I've already tried

---

### Post by taurus on 2007-12-27
Why don't you boot into windows and format your USB drive from there then.

---

### Post by jas0 on 2007-12-27
Gah, I assumed that the name of the device should be /dev/sdc since you already had sdb  and sda. You can try /dev/sdd and sde. If that doesn't work then go with what lswest said. When you know the name of the device, you will be able to follow the instructions.

---

### Post by spiderbatdad on 2007-12-27
[http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html](http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html) ack wrong thread! 3rd time recently

---

