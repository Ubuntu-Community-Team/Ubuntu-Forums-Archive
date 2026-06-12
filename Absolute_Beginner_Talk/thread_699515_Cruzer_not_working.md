---
title: "Cruzer not working"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by Rezistik on 2008-02-17
Okay i just got a Sandisk 1GB cruzer and when I plug it in it is recognized, but when I attempt to enter it it says no media...so how do I mount it or enter it whatever :(?

I wanna put some stuff on it and read it but I can't :( :(

I want to be able to put it in both a windows box and this ubuntu box please help.

---

### Post by Rezistik on 2008-02-17
Help please. :(

---

### Post by MIDkid on 2008-02-17
Does it have a U3 logo? I would either stick it in a windows box and use the U3 removal tool or create a new partition on it and format it as NTFS

---

### Post by Rezistik on 2008-02-17
It has a U3 logo, is there any way to do that on this box?

---

### Post by asmoore82 on 2008-02-17
you need to know what device file ID is being assigned to the drive,
in a terminal "Applications -> Accessories -> Terminal," check the output of
```
dmesg
```
right after plugging in the Cruzer, it will probably be either ``/dev/sda'' or ``/dev/sdb''

after you know what it is, use GParted to manage the partitions/filesystems on it...
```
gksu gparted /dev/sda
```
you may need to install GParted if you don't have it already:
```
sudo apt-get install gparted
```

---

### Post by Rezistik on 2008-02-20
```
[62368.976000] usb 1-6: new high speed USB device using ehci_hcd and address 3
[62369.108000] usb 1-6: configuration #1 chosen from 1 choice
[62370.084000] usbcore: registered new interface driver libusual
[62370.208000] Initializing USB Mass Storage driver...
[62370.208000] scsi2 : SCSI emulation for USB Mass Storage devices
[62370.208000] usb-storage: device found at 3
[62370.208000] usb-storage: waiting for device to settle before scanning
[62370.208000] usbcore: registered new interface driver usb-storage
[62370.208000] USB Mass Storage support registered.
[62375.208000] usb-storage: device scan complete
[62375.208000] scsi 2:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  3.21 PQ: 0 ANSI: 2
[62375.208000] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[62375.208000] sd 2:0:0:0: Attached scsi generic sg2 type 0
 
```

Thats what it says...what do I do from here?

---

