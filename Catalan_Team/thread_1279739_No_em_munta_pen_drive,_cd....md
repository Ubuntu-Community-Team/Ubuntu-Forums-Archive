---
title: "No em munta pen drive, cd..."
date: 2009-10-01
forum: Catalan Team
---

### Post by tanreb20 on 2009-10-01
Hola! Desde fa uns dies em passa una cosa extranya, quan conecto al pc alguns pen-drive no m'els munta, i aixi amb el cdrom tambe, he provat a posar un de Ubuntu, un dels sims i molts d'altres, no hi ha manera no m'ho troba, a Ordinador desapareix...

el resultst del dmesg quan els conecto es el seguent:

```
[ 6715.491563] sd 10:0:0:0: Attached scsi generic sg2 type 0
[ 6715.720850] sd 10:0:0:0: [sdb] 1990656 512-byte logical blocks: (1.01 GB/972 MiB)
[ 6715.721332] sd 10:0:0:0: [sdb] Write Protect is off
[ 6715.721342] sd 10:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 6715.721349] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[ 6715.723947] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[ 6715.723959]  sdb: sdb1
[ 6715.728078] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[ 6715.728092] sd 10:0:0:0: [sdb] Attached SCSI removable disk
[ 6752.861934] usb 1-7: USB disconnect, address 11
[ 6877.060066] usb 1-7: new high speed USB device using ehci_hcd and address 12
[ 6877.202998] usb 1-7: configuration #1 chosen from 1 choice
[ 6877.221341] scsi11 : SCSI emulation for USB Mass Storage devices
[ 6877.229094] usb-storage: device found at 12
[ 6877.229104] usb-storage: waiting for device to settle before scanning
[ 6882.228442] usb-storage: device scan complete
[ 6882.229726] scsi 11:0:0:0: Direct-Access              USB DISK 2.0     PMAP PQ: 0 ANSI: 0 CCS
[ 6882.236951] sd 11:0:0:0: Attached scsi generic sg2 type 0
[ 6882.460494] sd 11:0:0:0: [sdb] 1990656 512-byte logical blocks: (1.01 GB/972 MiB)
[ 6882.461095] sd 11:0:0:0: [sdb] Write Protect is off
[ 6882.461105] sd 11:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 6882.461112] sd 11:0:0:0: [sdb] Assuming drive cache: write through
[ 6882.465089] sd 11:0:0:0: [sdb] Assuming drive cache: write through
[ 6882.465104]  sdb: sdb1
[ 6882.470329] sd 11:0:0:0: [sdb] Assuming drive cache: write through
[ 6882.470347] sd 11:0:0:0: [sdb] Attached SCSI removable disk
```

Alguna idea de que pot ser? O com solucionar-ho?

---

### Post by oriolsbd on 2009-10-01
Podria ser alguna actualització del Kernel. Prova d'engegar l'ordinador amb una versió antiga del Kernel i, si et funciona, posa-la com a versió d'arranc predeterminat.

Salut!

---

