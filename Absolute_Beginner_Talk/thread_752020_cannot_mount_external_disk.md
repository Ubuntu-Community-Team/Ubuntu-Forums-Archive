---
title: "cannot mount external disk"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by oliviacond on 2008-04-11
it is a ntfs hard disk.
nothing happen after I plugged in, no error message appeared.
the led light of the hard disk is light up.

my fdisk
```
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00007b79

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6992    56163208+  83  Linux
/dev/sda2            6993        7296     2441880    5  Extended
/dev/sda5            6993        7296     2441848+  82  Linux swap / Solaris

```

---

### Post by chewearn on 2008-04-11
After you plug in the drive, run:
```
dmesg | tail -n 20
```
Post the output.

---

### Post by kesman on 2008-04-11
It's probably a USB disk? With command **lsusb** you can view the plugged devices. Also it should create something under /dev, probably /dev/sda[something] or /dev/hda[something]. Mount that into /media/extdisk or whatever you want.

EDIT: damn AstalaVista, fast as light.

---

### Post by mick8985 on 2008-04-11
Hmm doesn't appear to recognise the device at all, paste the results for "lsusb"

edit - damn too slow...

---

### Post by oliviacond on 2008-05-01
> **AstalaVista said:**
> After you plug in the drive, run:
```
dmesg | tail -n 20
```
Post the output.

```
[  223.200685] eth1: associated
[  223.200775] eth1: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[  223.200781] eth1: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[  223.200787] eth1: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[  223.200792] eth1: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[  223.204038] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  225.197169] padlock: VIA PadLock not detected.
[  242.194363] eth1: no IPv6 routers present
[  256.780602] usb 5-5: new high speed USB device using ehci_hcd and address 2
[  256.914068] usb 5-5: configuration #1 chosen from 1 choice
[  257.104899] usbcore: registered new interface driver libusual
[  257.155429] Initializing USB Mass Storage driver...
[  257.155499] scsi2 : SCSI emulation for USB Mass Storage devices
[  257.155565] usbcore: registered new interface driver usb-storage
[  257.155569] USB Mass Storage support registered.
[  257.155686] usb-storage: device found at 2
[  257.155688] usb-storage: waiting for device to settle before scanning
[  262.144817] usb-storage: device scan complete
[  267.748262] usb 5-5: USB disconnect, address 2
[  267.748473] scsi 2:0:0:0: Device offlined - not ready after error recovery

```

lsusb
```

Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```


EDIT : it seems that the hard disk need DC to operate. ubuntu is able to detect it after I plug in the power plug. i thought the hard disk (USB) is able to operate with the power from usb connection.

---

### Post by persianprez on 2008-05-01
you need to format it into a format that ubuntu understand(i forget what the format is called =p).  I backed up all my stuff on my ext hd, and reformatted it. Now it works fine.

---

### Post by vmalep on 2008-05-01
I recently had problem to mount an USB drive formatted in NTFS and it was because the drive had not been properly unmounted (from the windows computer). I just reconnected it to a windows computer, safely removed it and i could mount it again on the linux box... (just in case this helps);

---

