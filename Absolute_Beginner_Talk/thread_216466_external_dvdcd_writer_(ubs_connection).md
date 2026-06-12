---
title: "external dvd/cd writer (ubs connection)"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by lex1 on 2006-07-15
I want to know how to install the drivers that come with the external dvd/cd writer. how does ubuntu detect it is there any BIOS settings that need to be changed?

i in fluxbox.

lex1

PS

the available lines in BIOS are

cd-rom/dvd drive( i think this may refer to internael drive?

network boot

floppy drive

hard drive (there is a + sign next to this when extnded it says HFS424040M9AT00-(PM)

---

### Post by lamego on 2006-07-15
The USB devices are not configured at the BIOS (except for the USB support itself).
Plug the device and chedk the log with the command:
```
dmesg
```
This should show you if the device was reconigzed.

---

### Post by lex1 on 2006-07-15
Is this it or is this something else?

lex1


[4294677.708000] usb 2-2: new full speed USB device using ohci_hcd and address 2
[4294677.841000] usb 2-2: not running at top speed; connect to a high speed hub
[4294677.865000] Attempting manual resume
[4294677.882000] SCSI subsystem initialized
[4294677.884000] Initializing USB Mass Storage driver...
[4294677.885000] scsi0 : SCSI emulation for USB Mass Storage devices
[4294677.885000] usb-storage: device found at 2
[4294677.885000] usb-storage: waiting for device to settle before scanning
[4294677.885000] usbcore: registered new driver usb-storage
[4294677.885000] USB Mass Storage support registered.
[4294677.945000] EXT3-fs: mounted filesystem with ordered data mode.
[4294677.973000] kjournald starting.  Commit interval 5 seconds
[4294682.923000]   Vendor: HL-DT-ST  Model: DVDRRW GSA-2164D  Rev: 1.01
[4294682.923000]   Type:   CD-ROM                             ANSI SCSI revision: 00
[4294682.923000] usb-storage: device scan complete

---

