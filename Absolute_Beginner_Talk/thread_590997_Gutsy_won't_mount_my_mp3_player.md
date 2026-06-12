---
title: "Gutsy won't mount my mp3 player"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by GoldBuggie on 2007-10-25
After doing a clean install of Gutsy I cannot get my mp3 player to work. I've searched the forum but no luck in a solution for this.

dmesg gives the following output:
```
[60618.936000] usb 1-1: new full speed USB device using ohci_hcd and address 4
[60619.148000] usb 1-1: configuration #1 chosen from 1 choice
[60619.152000] scsi1 : SCSI emulation for USB Mass Storage devices
[60619.152000] usb-storage: device found at 4
[60619.152000] usb-storage: waiting for device to settle before scanning
[60624.152000] usb-storage: device scan complete
[60624.160000] scsi 1:0:0:0: Direct-Access     EXATEL   i-BEAD100        0001 PQ: 0 ANSI: 4
[60624.172000] sd 1:0:0:0: [sda] 505857 512-byte hardware sectors (259 MB)
[60624.180000] sd 1:0:0:0: [sda] Write Protect is off
[60624.180000] sd 1:0:0:0: [sda] Mode Sense: 03 00 00 04
[60624.180000] sd 1:0:0:0: [sda] Assuming drive cache: write through
[60624.196000] sd 1:0:0:0: [sda] 505857 512-byte hardware sectors (259 MB)
[60624.204000] sd 1:0:0:0: [sda] Write Protect is off
[60624.204000] sd 1:0:0:0: [sda] Mode Sense: 03 00 00 04
[60624.204000] sd 1:0:0:0: [sda] Assuming drive cache: write through
[60624.204000]  sda: sda1
[60624.220000] sd 1:0:0:0: [sda] Attached SCSI removable disk
[60624.220000] sd 1:0:0:0: Attached scsi generic sg0 type 0
[60624.904000] end_request: I/O error, dev sda, sector 505856
[60624.904000] Buffer I/O error on device sda, logical block 505856
[60655.080000] usb 1-1: reset full speed USB device using ohci_hcd and address 4
[60655.664000] usb 1-1: device not accepting address 4, error -62
[60655.840000] usb 1-1: reset full speed USB device using ohci_hcd and address 4
[60656.020000] usb 1-1: device descriptor read/64, error -62
[60656.304000] usb 1-1: device descriptor read/64, error -62
[60656.584000] usb 1-1: reset full speed USB device using ohci_hcd and address 4
[60656.992000] usb 1-1: device not accepting address 4, error -62
[60657.156000] usb 1-1: reset full speed USB device using ohci_hcd and address 4
[60657.564000] usb 1-1: device not accepting address 4, error -62
[60657.564000] usb 1-1: USB disconnect, address 4
[60657.564000] scsi 1:0:0:0: scsi: Device offlined - not ready after error recovery
[60657.568000] scsi 1:0:0:0: [sda] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[60657.568000] end_request: I/O error, dev sda, sector 505856
[60657.568000] Buffer I/O error on device sda, logical block 505856
[60657.640000] scsi 1:0:0:0: rejecting I/O to dead device
[60657.640000] Buffer I/O error on device sda, logical block 505848
[60657.640000] Buffer I/O error on device sda, logical block 505849
[60657.640000] Buffer I/O error on device sda, logical block 505850
[60657.640000] Buffer I/O error on device sda, logical block 505851
[60657.640000] Buffer I/O error on device sda, logical block 505852
[60657.640000] Buffer I/O error on device sda, logical block 505853
[60657.640000] Buffer I/O error on device sda, logical block 505854
[60657.640000] Buffer I/O error on device sda, logical block 505855
[60657.648000] scsi 1:0:0:0: rejecting I/O to dead device
[60657.648000] Buffer I/O error on device sda, logical block 505848
[60657.648000] scsi 1:0:0:0: rejecting I/O to dead device
[60657.648000] scsi 1:0:0:0: rejecting I/O to dead device
[60657.648000] scsi 1:0:0:0: rejecting I/O to dead device
[60657.648000] scsi 1:0:0:0: rejecting I/O to dead device
[60657.648000] scsi 1:0:0:0: rejecting I/O to dead device
...
[60657.684000] scsi 1:0:0:0: rejecting I/O to dead device
[60657.688000] scsi 1:0:0:0: rejecting I/O to dead device
[60657.740000] usb 1-1: new full speed USB device using ohci_hcd and address 5
[60657.920000] usb 1-1: device descriptor read/64, error -62
[60658.204000] usb 1-1: device descriptor read/64, error -62
[60658.484000] usb 1-1: new full speed USB device using ohci_hcd and address 6
[60658.664000] usb 1-1: device descriptor read/64, error -62
[60658.948000] usb 1-1: device descriptor read/64, error -62
[60659.228000] usb 1-1: new full speed USB device using ohci_hcd and address 7
[60659.636000] usb 1-1: device not accepting address 7, error -62
[60659.812000] usb 1-1: new full speed USB device using ohci_hcd and address 8
[60660.220000] usb 1-1: device not accepting address 8, error -62
```

Since my mp3 player works and I can mount it on windows and it worked with 6.10 which was what I used before the installation I will assume it isn't the mp3 players fault.

Any help is greatly appreciated!

---

### Post by ghantoos on 2007-10-25
I had the same problem with a USB key. I had to reboot under UbuntuStudio to get the information I needed from my key.

I'm waiting for the new kernel hoping it will fix this.

Anyways, I'm interested in any suggestion about this too. 

cheers,

Ghantoos

---

### Post by simyonov on 2007-12-06
Same here. I'm brand new to Ubuntu and Linux and have been trying out Gutsy Gibbon 7.10 and Dapper Drake 6.06 from Live CD's and installs. Dapper recognizes my Utlra Hydra MP3 player and mounts it automatically. Gutsy seems to recognize it in the Hardware Information list, but I can't get it to appear on the desktop or in a window so I can throw files on it. Both fstab files look identical (I think that file has something to do with mounting these things, but I'm fresh off the boat).

I'd just use Dapper, but I can't get my wireless to work and Gutsy recognizes it right away. Actually, that's likely because Dapper doesn't show a WAP wireless encrytion option, which my network has - only WEP. If it's not one thing, it's another, but I'm excited to learn about Linux and make it work. 

I'm running a Dell Optiplex GX2400, and I know there are some issues with Dells. Any help is much appreciated! Just getting the MP3 player to work like it does on Gutsy would be great.

---

