---
title: "eeebox EB1501 USB 3 slow transfer"
date: 2012-01-31
forum: Asus Ubuntu Support (CLOSED)
---

### Post by johnnyfleet on 2012-01-31
Hi,

I don't know if anyone else has experienced this problem but hope you can help. I've got an eeebox EB1501 with Ubuntu 10.04 on it. 

On the front are 2 USB 3 sockets. I'm trying to transfer some data off a mybook 2TB drive onto a seagate 3tb drive. Both of them are USB 3 units and both formatted to ext4.

However, when I try and copy the data over, either via grsync or nautilus copy/paste I end up with only ~12MB/sec xfer speeds. This seems like USB 2 speeds. 

Checking ```
lsusb
``` I can see that the drives **are** connected and that sockets recognised as usb 3.

```
Bus 005 Device 003: ID 1058:1140 Western Digital Technologies, Inc. 
Bus 005 Device 002: ID 0bc2:3332 Seagate RSS LLC 
Bus 005 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 1020:0106 Labtec Wireless Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

Can anyone help me understand why the transfer speeds are so low? Is there a way to speed up?

Many Thanks

---

### Post by johnnyfleet on 2012-01-31
To help further...

This is output of **sudo lspci -v**

```
06:00.0 USB Controller: NEC Corporation Device 0194 (rev 03) (prog-if 30)
	Subsystem: ASUSTeK Computer Inc. Device 8413
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at fbffe000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: [50] Power Management version 3
	Capabilities: [70] Message Signalled Interrupts: Mask- 64bit+ Queue=0/3 Enable-
	Capabilities: [90] MSI-X: Enable- Mask- TabSize=8
	Capabilities: [a0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Device Serial Number ff-ff-ff-ff-ff-ff-ff-ff
	Capabilities: [150] #18
	Kernel driver in use: xhci_hcd
	Kernel modules: xhci

```

and output of **dmesg | grep usb**


```
[   24.197717] usb usb5: config 1 interface 0 altsetting 0 endpoint 0x81 has no SuperSpeed companion descriptor
[   24.198020] usb usb5: configuration #1 chosen from 1 choice
[   24.402270] usb 5-1: new SuperSpeed USB device using xhci_hcd and address 2
[   24.422301] usb 5-1: configuration #1 chosen from 1 choice
[   24.440269] usb-storage: device found at 2
[   24.440277] usb-storage: waiting for device to settle before scanning
[   24.441851] usb 5-2: new SuperSpeed USB device using xhci_hcd and address 3
[   24.460293] usb 5-2: configuration #1 chosen from 1 choice
[   24.462332] usb-storage: device found at 3
[   24.462340] usb-storage: waiting for device to settle before scanning
```

---

