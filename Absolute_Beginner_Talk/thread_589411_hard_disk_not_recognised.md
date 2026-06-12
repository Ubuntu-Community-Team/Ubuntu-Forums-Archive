---
title: "hard disk not recognised"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by themis on 2007-10-24
Hello everyone,

all of a sudden I opened my pc, and my NTFS external drive is not recognised.
I searched a bit the threads but couldn;t find soemething useful.
I also had ntfs configuration tool launched for the drive.


```
embryo@pollux:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1435e13b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7108    57094978+  83  Linux
/dev/sda2            7109        7296     1510110    5  Extended
/dev/sda5            7109        7296     1510078+  82  Linux swap / Solaris 
```

sda is the internal disk.
What can I do?
Thanks :)

---

### Post by realvz on 2007-10-24
same issue is being worked on in 
[http://ubuntuforums.org/showthread.php?t=588691](http://ubuntuforums.org/showthread.php?t=588691)

---

### Post by themis on 2007-10-24
No no, the disk wasn't recognised before upgrading!

---

### Post by realvz on 2007-10-24
oh sorry...is it a usb disk...
can you try this...
plug in the disk and then reboot ubuntu and see if the disk is installed now.

just give it a try

---

### Post by themis on 2007-10-24
Still not recognised! :(

---

### Post by realvz on 2007-10-24
Power on the USB disk, and do a routine

dmesg | grep usb
If the disk is recognized you should see somewhere a line like
usbcore: registered new interface driver usb-storage

---

### Post by themis on 2007-10-24
```
embryo@pollux:~$ dmesg | grep usb
[   11.389377] usbcore: registered new interface driver usbfs
[   11.389419] usbcore: registered new interface driver hub
[   11.389454] usbcore: registered new device driver usb
[   11.391269] usb usb1: configuration #1 chosen from 1 choice
[   11.674203] usb usb2: configuration #1 chosen from 1 choice
[   11.800022] usb usb3: configuration #1 chosen from 1 choice
[    4.520000] usb usb4: configuration #1 chosen from 1 choice
[    5.040000] usb 2-3: new full speed USB device using ohci_hcd and address 2
[    5.252000] usb 2-3: configuration #1 chosen from 1 choice
[    5.272000] usbcore: registered new interface driver hiddev
[    5.280000] input: USB HID v1.00 Mouse [Synaptics Inc. Synaptics cPad] on usb-0000:02:06.0-3
[    5.280000] usbcore: registered new interface driver usbhid
[    5.280000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[  270.772000] usb 3-1: new high speed USB device using ehci_hcd and address 3
[  270.908000] usb 3-1: configuration #1 chosen from 1 choice
[  271.076000] usbcore: registered new interface driver libusual
[  271.164000] usb-storage: device found at 3
[  271.164000] usb-storage: waiting for device to settle before scanning
[  271.164000] usbcore: registered new interface driver usb-storage
[  276.164000] usb-storage: device scan complete

```
```

embryo@pollux:~$ sudo fdisk -l
[sudo] password for embryo:

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1435e13b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7108    57094978+  83  Linux
/dev/sda2            7109        7296     1510110    5  Extended
/dev/sda5            7109        7296     1510078+  82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0edd5cbc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       14593   117210240    f  W95 Ext'd (LBA)
/dev/sdb5               2       14593   117210208+   7  HPFS/NTFS



```

So, my disk now is detected, but shouldn't it be in /media ??
Tthere is only the mount point I created for the ntfs configuration tool to work.
Shall I install the ntfs configuration tool again??

---

### Post by realvz on 2007-10-24
sure give it a  try

---

### Post by themis on 2007-10-24
> **realvz said:**
> sure give it a  try

Thanks for everything,
the disk works fine! I think it just needed a sudo mount -a.

Thanks a lot again! \\:D/

---

### Post by realvz on 2007-10-24
hmm i will keep that in mind...

congrats

---

