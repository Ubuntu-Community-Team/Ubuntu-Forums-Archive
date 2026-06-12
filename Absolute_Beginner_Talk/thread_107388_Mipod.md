---
title: "Mipod"
date: 2005-12-22
forum: Absolute Beginner Talk
---

### Post by Todd_Z on 2005-12-22
Im trying to get gtkpod or amarok to interact with my ipod...

Heres the output of dmesg when i unplug and plug in the pod:
```

[4383502.520000]   Vendor: Apple     Model: iPod              Rev: 1.62
[4383502.520000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4383502.524000] SCSI device sda: 58605119 512-byte hdwr sectors (30006 MB)
[4383502.526000] sda: Write Protect is off
[4383502.526000] sda: Mode Sense: 64 00 00 08
[4383502.526000] sda: assuming drive cache: write through
[4383502.528000] SCSI device sda: 58605119 512-byte hdwr sectors (30006 MB)
[4383502.529000] sda: Write Protect is off
[4383502.529000] sda: Mode Sense: 64 00 00 08
[4383502.529000] sda: assuming drive cache: write through
[4383502.529000]  /dev/scsi/host28/bus0/target0/lun0: [mac] p1 p2 p3
[4383502.607000] Attached scsi removable disk sda at scsi28, channel 0, id 0, lun 0
[4383502.609000] usb-storage: device scan complete
[4383503.381000] HFS+-fs warning: Filesystem was not cleanly unmounted, running fsck.hfsplus is recommended.  mounting read-only.
[4383519.517000] usb 5-1: USB disconnect, address 29
[4383519.836000] scsi28 (0:0): rejecting I/O to dead device
[4383521.434000] usb 5-1: new high speed USB device using ehci_hcd and address 30

```

When i plug in the pod, I get the file manager popup with the folder directory in it for the ipod, but amarok say that it cannot find the device.  It is mounted on /media/ipod with a symbolic link to /mnt/ipod.... anyone have any ideas?

---

