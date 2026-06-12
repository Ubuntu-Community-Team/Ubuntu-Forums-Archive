---
title: "external drives wont work"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by shikonowa on 2007-10-01
none of my external drives wont work, my ipod, external hard drive, psp... i had them working a few days ago, whats wrong?

---

### Post by shikonowa on 2007-10-01
i looked and saw that it was being seen, used "sudo fdisk -l" and it showed up as an extra drive but i cant see it on the desktop or in any of the folders. also, at startup i get an error, something about HAL not starting.

---

### Post by phidia on 2007-10-01
Open the terminal and type > dmesg
Look throught the output for your drives and related messages or post the output here.
Note: do the dmesg command after plugging in one or all of the drives you're trying to mount.

---

### Post by phidia on 2007-10-01
> **shikonowa said:**
> i looked and saw that it was being seen, used "sudo fdisk -l" and it showed up as an extra drive but i cant see it on the desktop or in any of the folders. also, at startup i get an error, something about HAL not starting.

Yeah that's the issue. Are you using gnome? You can start services from the administration submenu.

---

### Post by shikonowa on 2007-10-01
[ 7120.656389] usb 5-6: new high speed USB device using ehci_hcd and address 3
[ 7120.789157] usb 5-6: configuration #1 chosen from 1 choice
[ 7121.106779] usbcore: registered new interface driver libusual
[ 7121.128204] Initializing USB Mass Storage driver...
[ 7121.128313] scsi0 : SCSI emulation for USB Mass Storage devices
[ 7121.128369] usb-storage: device found at 3
[ 7121.128371] usb-storage: waiting for device to settle before scanning
[ 7121.128374] usbcore: registered new interface driver usb-storage
[ 7121.128377] USB Mass Storage support registered.
[ 7126.129275] usb-storage: device scan complete
[ 7126.129759] scsi 0:0:0:0: Direct-Access     Sony     PSP              1.00 PQ: 0 ANSI: 0 CCS
[ 7126.168216] SCSI device sda: 1963008 512-byte hdwr sectors (1005 MB)
[ 7126.168713] sda: Write Protect is off
[ 7126.168715] sda: Mode Sense: 00 6a 20 00
[ 7126.168717] sda: assuming drive cache: write through
[ 7126.173340] SCSI device sda: 1963008 512-byte hdwr sectors (1005 MB)
[ 7126.173837] sda: Write Protect is off
[ 7126.173838] sda: Mode Sense: 00 6a 20 00
[ 7126.173840] sda: assuming drive cache: write through
[ 7126.173843]  sda: sda1
[ 7126.176290] sd 0:0:0:0: Attached scsi removable disk sda
[ 7126.183906] sd 0:0:0:0: Attached scsi generic sg0 type 0
[ 7171.805095] usb 5-6: USB disconnect, address 3
[23624.284054] usb 5-6: new high speed USB device using ehci_hcd and address 4
[23624.418624] usb 5-6: configuration #1 chosen from 1 choice
[23624.418896] scsi1 : SCSI emulation for USB Mass Storage devices
[23624.418949] usb-storage: device found at 4
[23624.418951] usb-storage: waiting for device to settle before scanning
[23629.417108] usb-storage: device scan complete
[23629.420849] scsi 1:0:0:0: Direct-Access     WDC WD40 0BB-53DEA0       0000 PQ: 0 ANSI: 0
[23629.422324] SCSI device sda: 78165360 512-byte hdwr sectors (40021 MB)
[23629.423194] sda: Write Protect is off
[23629.423196] sda: Mode Sense: 27 00 00 00
[23629.423198] sda: assuming drive cache: write through
[23629.424621] SCSI device sda: 78165360 512-byte hdwr sectors (40021 MB)
[23629.426005] sda: Write Protect is off
[23629.426009] sda: Mode Sense: 27 00 00 00
[23629.426011] sda: assuming drive cache: write through
[23629.426016]  sda: sda1
[23629.455052] sd 1:0:0:0: Attached scsi disk sda
[23629.455110] sd 1:0:0:0: Attached scsi generic sg0 type 0
[24154.759285] usb 5-6: USB disconnect, address 4
[24172.188596] usb 5-6: new high speed USB device using ehci_hcd and address 5
[24172.323248] usb 5-6: configuration #1 chosen from 1 choice
[24172.323551] scsi2 : SCSI emulation for USB Mass Storage devices
[24172.323602] usb-storage: device found at 5
[24172.323605] usb-storage: waiting for device to settle before scanning
[24177.321624] usb-storage: device scan complete
[24177.325492] scsi 2:0:0:0: Direct-Access     WDC WD40 0BB-53DEA0       0000 PQ: 0 ANSI: 0
[24177.326960] SCSI device sda: 78165360 512-byte hdwr sectors (40021 MB)
[24177.327832] sda: Write Protect is off
[24177.327834] sda: Mode Sense: 27 00 00 00
[24177.327836] sda: assuming drive cache: write through
[24177.328707] SCSI device sda: 78165360 512-byte hdwr sectors (40021 MB)
[24177.329585] sda: Write Protect is off
[24177.329587] sda: Mode Sense: 27 00 00 00
[24177.329589] sda: assuming drive cache: write through
[24177.329592]  sda: sda1
[24177.350681] sd 2:0:0:0: Attached scsi disk sda
[24177.350732] sd 2:0:0:0: Attached scsi generic sg0 type 0

---

### Post by shikonowa on 2007-10-01
i think i'm using x terminal

---

### Post by shikonowa on 2007-10-01
i cant get into that section, it says i dont have the rights to. wheres the file for the root?

---

### Post by phidia on 2007-10-01
You aren't using a gui desktop? To access system files (provided you know what you're doing) you need to preface your command(s) with "sudo".

---

### Post by shikonowa on 2007-10-01
i'm actually running xclient and it is graphical, when i go into services it says i cant change the configuration

---

