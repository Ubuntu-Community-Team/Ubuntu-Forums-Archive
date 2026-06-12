---
title: "k3b"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by lex1 on 2006-11-30
just installed k3b but it cannot find writer which is on a usb port did a reboot

this is some output from dmesg file


[4294674.922000] hdc: Slimtype DVDRW SOSW-852S, ATAPI CD/DVD-ROM drive
[4294675.534000] ide1 at 0x170-0x177,0x376 on irq 15
[4294675.637000] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)









[4294675.973000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[4294675.974000] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 201
[4294675.974000] ohci_hcd 0000:00:13.0: OHCI Host Controller
[4294676.241000] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[4294676.241000] ohci_hcd 0000:00:13.0: irq 201, io mem 0xe8001000
[4294676.296000] hub 1-0:1.0: USB hub found
[4294676.296000] hub 1-0:1.0: 3 ports detected
[4294676.397000] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 201
[4294676.397000] ohci_hcd 0000:00:13.1: OHCI Host Controller
[4294676.655000] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[4294676.655000] ohci_hcd 0000:00:13.1: irq 201, io mem 0xe8002000
[4294676.710000] hub 2-0:1.0: USB hub found


[4294686.941000] usbcore: registered new driver usb-storage
[4294686.941000] USB Mass Storage support registered.





[4294691.942000]   Vendor: DVDRW     Model: USB H16X          Rev: B02T
[4294691.942000]   Type:   CD-ROM                             ANSI SCSI revision: 00
[4294691.945000] usb-storage: device scan complete
[4294692.036000] sr0: scsi3-mmc drive: 62x/62x writer dvd-ram cd/rw xa/form2 cdda tray
[4294692.037000] sr 0:0:0:0: Attached scsi CD-ROM sr0
[4294692.059000] sr 0:0:0:0: Attached scsi generic sg0 type 5

---

