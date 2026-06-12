---
title: "External hard drive doesn't work with my PCMCIA USB 2.0 Card"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by punong_bisyonaryo on 2008-04-06
My External HDD works fine when connected to the built-in USB1.1 USB ports, but when I plug it in to my PCMCIA, dmesg has the following message:

```
[ 2532.744000] usb 4-1: new high speed USB device using ehci_hcd and address 3
[ 2532.876000] usb 4-1: configuration #1 chosen from 1 choice
[ 2532.876000] scsi5 : SCSI emulation for USB Mass Storage devices
[ 2532.876000] usb-storage: device found at 3
[ 2532.876000] usb-storage: waiting for device to settle before scanning
[ 2537.876000] usb-storage: device scan complete
[ 2543.656000] usb 4-1: USB disconnect, address 3
[ 2543.656000] scsi 5:0:0:0: scsi: Device offlined - not ready after error recovery
```

The PCMCIA card itself is probably working fine. I have my USB mouse and Kingston DiskTraveler working fine with it.

Any ideas?

---

### Post by scrime on 2008-04-06
What file system is the drive using?  Could it be that the device was not safely removed?

---

### Post by punong_bisyonaryo on 2008-04-06
> **scrime said:**
> What file system is the drive using?  Could it be that the device was not safely removed?

The drive is fat32, formatted with gparted. It's removed safely. Works fine when I plug it in the built-in USB1.1 port, but when I plug it into the USB2.0 PCMCIA hub, it never gets mounted at all.

---

