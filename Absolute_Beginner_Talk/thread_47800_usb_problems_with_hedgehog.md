---
title: "usb problems with hedgehog"
date: 2005-07-10
forum: Absolute Beginner Talk
---

### Post by merrittr on 2005-07-10
I have HH installed on a IBM ThinkPad 600E where my usb mouse will not work.
here is a dmesg dump any idea whats up?

USB Universal Host Controller Interface driver v2.2
ACPI: PCI Interrupt Link [LNKD] disabled and referenced, BIOS bug.
ACPI: PCI Interrupt Link [LNKD] BIOS reported IRQ 0, using IRQ 9
ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 9
ACPI: PCI interrupt 0000:00:07.2[D] -> GSI 9 (level, low) -> IRQ 9
uhci_hcd 0000:00:07.2: Intel Corp. 82371AB/EB/MB PIIX4 USB
uhci_hcd 0000:00:07.2: irq 9, io base 0x8400
uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
usb 1-1: new low speed USB device using uhci_hcd and address 2
uhci_hcd 0000:00:07.2: Unlink after no-IRQ?  Different ACPI or APIC settings may help.
usb 1-1: khubd timed out on ep0in
piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
piix4_smbus 0000:00:07.3: IBM Laptop detected; this module may corrupt your serial eeprom! Refusing to load module!
piix4_smbus: probe of 0000:00:07.3 failed with error -1
usb 1-1: khubd timed out on ep0out
usb 1-1: khubd timed out on ep0out
usb 1-1: device not accepting address 2, error -110
usb 1-1: new low speed USB device using uhci_hcd and address 3
usb 1-1: khubd timed out on ep0in
usb 1-1: khubd timed out on ep0out
usb 1-1: khubd timed out on ep0out

---

