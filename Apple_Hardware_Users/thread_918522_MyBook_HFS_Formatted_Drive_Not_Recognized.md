---
title: "MyBook HFS Formatted Drive Not Recognized"
date: 2008-09-13
forum: Apple Hardware Users
---

### Post by gamblor87 on 2008-09-13
Hi there,

I'm new to Ubuntu, but quite familiar with how it all works and such.

I have installed Hardy on a 2004 first gen iMac G5, and its all running well except for my external hard drive. It is a WD MyBook 500GB Home edition, and it has two HFS (Journaled) partitions, containing all my media and backups. I can read it fine in both Mac and Windows (using MacDrive).

So far, I have:
[LIST]
[*]Downloaded the various HFS utilities and installed them
[*]Modified /etc/modules to load HFS at boot
[/LIST]

When I plug it in, the drive seems to flash up for a split second in File Browser, before disappearing. when I unplug it, it also flashes up again.

Here is what messages System Log Viewer gives me:
```
Sep 13 15:17:57 jamesSquire kernel: [10920.263100] usb 3-2: new high speed USB device using ehci_hcd and address 5
Sep 13 15:17:58 jamesSquire kernel: [10920.541225] usb 3-2: configuration #1 chosen from 1 choice
Sep 13 15:17:58 jamesSquire kernel: [10920.595966] scsi8 : SCSI emulation for USB Mass Storage devices
Sep 13 15:17:58 jamesSquire kernel: [10920.666778] input: Western Digital My Book as /devices/pci0001:00/0001:00:02.0/0001:01:0b.2/usb3/3-2/3-2:1.1/input/input9
Sep 13 15:17:58 jamesSquire kernel: [10920.675183] input,hidraw3: USB HID v1.11 Device [Western Digital My Book] on usb-0001:01:0b.2-2
Sep 13 15:18:03 jamesSquire kernel: [10925.648296] scsi 8:0:0:0: Direct-Access     WD       My Book          1025 PQ: 0 ANSI: 4
Sep 13 15:18:03 jamesSquire kernel: [10925.669662] sd 8:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
Sep 13 15:18:03 jamesSquire kernel: [10925.682531] sd 8:0:0:0: [sdb] Write Protect is off
Sep 13 15:18:03 jamesSquire kernel: [10925.703522] sd 8:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
Sep 13 15:18:03 jamesSquire kernel: [10925.716416] sd 8:0:0:0: [sdb] Write Protect is off
Sep 13 15:18:03 jamesSquire kernel: [10925.716442]  sdb: sdb1
Sep 13 15:18:03 jamesSquire kernel: [10925.732465] sd 8:0:0:0: [sdb] Attached SCSI disk
Sep 13 15:18:03 jamesSquire kernel: [10925.732542] sd 8:0:0:0: Attached scsi generic sg1 type 0
```

This is using USB - the same things happen with Firewire. It is seeing and detecting the drive, but isn't mounting it.

Any ideas?

Thanks!
PS: My computer is called jamesSquire -very good beer!

---

### Post by pxwpxw on 2008-09-13
> **gamblor87 said:**
> Hi there,

I'm new to Ubuntu, but quite familiar with how it all works and such.

I have installed Hardy on a 2004 first gen iMac G5, and its all running well except for my external hard drive. It is a WD MyBook 500GB Home edition, and it has two HFS (Journaled) partitions, containing all my media and backups. I can read it fine in both Mac and Windows (using MacDrive).

So far, I have:
[LIST]
[*]Downloaded the various HFS utilities and installed them
[*]Modified /etc/modules to load HFS at boot
[/LIST]

When I plug it in, the drive seems to flash up for a split second in File Browser, before disappearing. when I unplug it, it also flashes up again.

Here is what messages System Log Viewer gives me:
```
Sep 13 15:17:57 jamesSquire kernel: [10920.263100] usb 3-2: new high speed USB device using ehci_hcd and address 5
Sep 13 15:17:58 jamesSquire kernel: [10920.541225] usb 3-2: configuration #1 chosen from 1 choice
Sep 13 15:17:58 jamesSquire kernel: [10920.595966] scsi8 : SCSI emulation for USB Mass Storage devices
Sep 13 15:17:58 jamesSquire kernel: [10920.666778] input: Western Digital My Book as /devices/pci0001:00/0001:00:02.0/0001:01:0b.2/usb3/3-2/3-2:1.1/input/input9
Sep 13 15:17:58 jamesSquire kernel: [10920.675183] input,hidraw3: USB HID v1.11 Device [Western Digital My Book] on usb-0001:01:0b.2-2
Sep 13 15:18:03 jamesSquire kernel: [10925.648296] scsi 8:0:0:0: Direct-Access     WD       My Book          1025 PQ: 0 ANSI: 4
Sep 13 15:18:03 jamesSquire kernel: [10925.669662] sd 8:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
Sep 13 15:18:03 jamesSquire kernel: [10925.682531] sd 8:0:0:0: [sdb] Write Protect is off
Sep 13 15:18:03 jamesSquire kernel: [10925.703522] sd 8:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
Sep 13 15:18:03 jamesSquire kernel: [10925.716416] sd 8:0:0:0: [sdb] Write Protect is off
Sep 13 15:18:03 jamesSquire kernel: [10925.716442]  sdb: sdb1
Sep 13 15:18:03 jamesSquire kernel: [10925.732465] sd 8:0:0:0: [sdb] Attached SCSI disk
Sep 13 15:18:03 jamesSquire kernel: [10925.732542] sd 8:0:0:0: Attached scsi generic sg1 type 0
```

This is using USB - the same things happen with Firewire. It is seeing and detecting the drive, but isn't mounting it.

Any ideas?

Thanks!
PS: My computer is called jamesSquire -very good beer!

There should be a System preferences menu setting to mount removable drives, it is in Setting Manager in xubuntu, somewhere similar in other ubuntus.

Otherwise you can mount it manually, or using /etc/fstab.

Your log shows only the sdb1 partition, you refer to 2 partitions.

If you run the linux partition editor (gparted package) you can inspect the drive partition map and partition details, and also can do this from macosx Disk Utility.

You will not have write access from ubuntu to journalled macos extended, have to disable journalling in macosx.

My external looks like this:
```

[    8.340105] scsi 4:0:0:0: Direct-Access-RBC WDC WD16 00JB-00GVC0      08.0 PQ: 0 ANSI: 4
[    8.373722] sd 1:0:0:0: [sdb] Attached SCSI disk
[    8.392001] sd 4:0:0:0: [sdc] 312581808 512-byte hardware sectors (160042 MB)
[    8.392443] sd 4:0:0:0: [sdc] Write Protect is off
[    8.396010] sd 4:0:0:0: [sdc] Mode Sense: 11 00 00 00
[    8.396831] sd 4:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.401636] sd 4:0:0:0: [sdc] 312581808 512-byte hardware sectors (160042 MB)
[    8.405100] sd 4:0:0:0: [sdc] Write Protect is off
[    8.408011] sd 4:0:0:0: [sdc] Mode Sense: 11 00 00 00
[    8.408832] sd 4:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.412012]  sdc: [mac] sdc1 sdc2 sdc3 sdc4 sdc5 sdc6 sdc7 sdc8 sdc9
[    8.431488] sd 4:0:0:0: [sdc] Attached SCSI disk

```

No problems here with intrepid, or hardy, firewire or usb.
But it may be necessary to have the external running before startup.

---

### Post by cyberdork33 on 2008-09-13
it sounds like the system is seeing the drive fine, it is just not being mounted for some reason.

---

### Post by gamblor87 on 2008-09-14
Thanks for the suggestions! When I opened GParted, it showed my entire disk as "unallocated", which would suggest something is not quite right and would explain why it isn't being mounted.

My MacBook has been stuck at work over the weekend, but I get it back today so I'll be able to repair the drive and turn off journaling. Then maybe it'll work! Fingers crossed.

Will keep you updated, thanks again.

---

