---
title: "Can't download pics from dSLR"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by bolsen on 2007-02-07
I just bought a Nikon d70s dSLR and I can't download the images.:confused: 

Dapper doesn't recognize the device on the USB

I tried to mount the USB manually but  /dev/sda does not exist.
There is no /dev/sdb, dev/sdc, or /dev/sd* either.

Also when I plug in the camera and turn it on the internet gets hung and won't load.

When I run dmesg this is what I get: 

[17179580.052000] **** SET: Misaligned resource pointer: dfcf43c2 Type 07 Len 0
[17179580.052000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[17179580.052000] ACPI: PCI Interrupt 0000:00:10.2[C] -> Link [LNKC] -> GSI 11 ( level, low) -> IRQ 11
[17179580.052000] uhci_hcd 0000:00:10.2: UHCI Host Controller
[17179580.052000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus nu mber 3
[17179580.052000] uhci_hcd 0000:00:10.2: irq 11, io base 0x0000ec00
[17179580.052000] hub 3-0:1.0: USB hub found
[17179580.052000] hub 3-0:1.0: 2 ports detected
[17179580.164000] **** SET: Misaligned resource pointer: dfcf40c2 Type 07 Len 0
[17179580.164000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[17179580.164000] ACPI: PCI Interrupt 0000:00:10.3[D] -> Link [LNKD] -> GSI 11 ( level, low) -> IRQ 11

Any help on how to get my USB to mount would be appreciated

Bolsen
Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4. 0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006

---

### Post by punong_bisyonaryo on 2008-01-12
I recently ran into the same problem, except my internet doesn't hang, also with a Nikon. I tried connecting it via USB, no go.

Has anyone had success with this?

---

### Post by philinux on 2008-01-12
try Gthumb it seems to wake up usb stuff.

---

### Post by punong_bisyonaryo on 2008-01-12
gThumb also cannot find my camera.

From dmesg, I get:
[ 3552.124000] usb 1-2: new full speed USB device using ohci_hcd and address 4
[ 3552.336000] usb 1-2: configuration #1 chosen from 1 choice
[ 3552.340000] scsi3 : SCSI emulation for USB Mass Storage devices
[ 3552.340000] usb-storage: device found at 4
[ 3552.340000] usb-storage: waiting for device to settle before scanning
[ 3557.340000] usb-storage: device scan complete
[ 3557.348000] scsi 3:0:0:0: Direct-Access     NIKON    D200             1.00 PQ: 0 ANSI: 2
[ 3557.360000] sd 3:0:0:0: [sdb] 4001761 512-byte hardware sectors (2049 MB)
[ 3557.364000] sd 3:0:0:0: [sdb] Write Protect is off
[ 3557.364000] sd 3:0:0:0: [sdb] Mode Sense: 0f 00 00 00
[ 3557.364000] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 3557.384000] sd 3:0:0:0: [sdb] 4001761 512-byte hardware sectors (2049 MB)
[ 3557.392000] sd 3:0:0:0: [sdb] Write Protect is off
[ 3557.392000] sd 3:0:0:0: [sdb] Mode Sense: 0f 00 00 00
[ 3557.392000] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 3557.392000]  sdb: sdb1
[ 3557.404000] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[ 3557.404000] sd 3:0:0:0: Attached scsi generic sg2 type 0
[ 3557.744000] end_request: I/O error, dev sdb, sector 4001760
[ 3557.744000] printk: 613 messages suppressed.
[ 3557.744000] Buffer I/O error on device sdb, logical block 4001760
[ 3557.760000] end_request: I/O error, dev sdb, sector 4001760
[ 3557.760000] Buffer I/O error on device sdb, logical block 4001760
[ 3557.796000] end_request: I/O error, dev sdb, sector 4001760
[ 3557.796000] Buffer I/O error on device sdb, logical block 4001760
[ 3557.812000] end_request: I/O error, dev sdb, sector 4001760
[ 3557.812000] Buffer I/O error on device sdb, logical block 4001760
[ 3557.828000] end_request: I/O error, dev sdb, sector 4001760
[ 3557.828000] Buffer I/O error on device sdb, logical block 4001760
[ 3557.912000] end_request: I/O error, dev sdb, sector 4001760
[ 3557.912000] Buffer I/O error on device sdb, logical block 4001760
[ 3557.928000] end_request: I/O error, dev sdb, sector 4001760
[ 3557.928000] Buffer I/O error on device sdb, logical block 4001760
[ 3557.944000] end_request: I/O error, dev sdb, sector 40
[ 3557.944000] Buffer I/O error on device sdb, logical block 40
[ 3557.964000] end_request: I/O error, dev sdb, sector 41
[ 3557.964000] Buffer I/O error on device sdb, logical block 41
[ 3557.964000] Buffer I/O error on device sdb, logical block 42
[ 3557.980000] end_request: I/O error, dev sdb, sector 40
[ 3557.996000] end_request: I/O error, dev sdb, sector 40
[ 3558.016000] end_request: I/O error, dev sdb, sector 41
[ 3558.192000] end_request: I/O error, dev sdb, sector 40
...
...

---

