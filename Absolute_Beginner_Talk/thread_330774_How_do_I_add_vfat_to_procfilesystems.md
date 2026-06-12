---
title: "How do I add vfat to /proc/filesystems"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by JayRoe on 2007-01-03
I can't get my Maxtor One Touch external hard drive to work with Ubuntu, [_this_]("http://www.ubuntuforums.org/showthread.php?t=64728&highlight=maxtor+one+touch") has led me to believe that it's due to a bug in /proc/filesystems. So can someone please tell me how I add and save vfat to /proc/filesystems.

---

### Post by bodhi.zazen on 2007-01-03
In a terminal:```
gksudo gedit /etc/filesystem
```

Add vfat as instructed.

---

### Post by tageiru on 2007-01-03
> **JayRoe said:**
> I can't get my Maxtor One Touch external hard drive to work with Ubuntu, [_this_]("http://www.ubuntuforums.org/showthread.php?t=64728&highlight=maxtor+one+touch") has led me to believe that it's due to a bug in /proc/filesystems. So can someone please tell me how I add and save vfat to /proc/filesystems.

You can't edit /proc/filesystem, it is generated from the filesystems which have been loaded into the kernel.

vfat should be loaded if mount requires it, have you tried -t vfat as the other thread suggested?

---

### Post by JayRoe on 2007-01-03
I started using linux yesterday so I have no idea if posting this makes any sense, but can someone tell me the problem from this?

before unplugging Maxtor One Touch```

root@ubuntu:~# dmesg | tail
[   98.745612] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   99.021952] ts: Compaq touchscreen protocol output
[  283.747848] ISO 9660 Extensions: Microsoft Joliet Level 3
[  284.619301] ISO 9660 Extensions: RRIP_1991A
[  463.259448] gaim[5278] general protection rip:2b31070e8600 rsp:7fffa53f5be0 error:0
[ 7114.107651] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 7114.162331] ISO 9660 Extensions: RRIP_1991A
[11702.703684] usb 2-1: new high speed USB device using ehci_hcd and address 15
[11702.836535] usb 2-1: configuration #1 chosen from 1 choice
[11707.831745] usb 2-1: can't set config #1, error -110
```

After unplugging Maxtor One Touch```
root@ubuntu:~# dmesg | tail
[   99.021952] ts: Compaq touchscreen protocol output
[  283.747848] ISO 9660 Extensions: Microsoft Joliet Level 3
[  284.619301] ISO 9660 Extensions: RRIP_1991A
[  463.259448] gaim[5278] general protection rip:2b31070e8600 rsp:7fffa53f5be0 error:0
[ 7114.107651] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 7114.162331] ISO 9660 Extensions: RRIP_1991A
[11702.703684] usb 2-1: new high speed USB device using ehci_hcd and address 15
[11702.836535] usb 2-1: configuration #1 chosen from 1 choice
[11707.831745] usb 2-1: can't set config #1, error -110
[11766.431670] usb 2-1: USB disconnect, address 15

```

After plugging it back in```
root@ubuntu:~# dmesg | tail
[12273.163808] usbcore: registered new driver libusual
[12273.446503] Initializing USB Mass Storage driver...
[12273.447433] scsi4 : SCSI emulation for USB Mass Storage devices
[12273.447518] usb-storage: device found at 17
[12273.447520] usb-storage: waiting for device to settle before scanning
[12273.447532] usbcore: registered new driver usb-storage
[12273.447536] USB Mass Storage support registered.
[12278.443243] usb-storage: device scan complete
[12284.050066] usb 2-1: reset high speed USB device using ehci_hcd and address 17
[12290.425268] usb 2-1: reset high speed USB device using ehci_hcd and address 17
```


I'm off to bed now, but I'll check up on this thread tomorrow.

---

