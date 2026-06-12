---
title: "cdrom won't mount"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by eatloaf on 2007-10-21
hi.
i just fresh installed gutsy and my cdrom doesn't seem to mount.  i'd appreciate help figuring this out.

when i insert a cd, the cd appears on my desktop and sound juicer opens it just fine.
but /media/cdrom0 is empty and trying to "browse folder" just relaunches sound juicer.

if  i try
```
sudo mount -t iso9660 /dev/hdc /media/cdrom0
```
i get
```
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```


my fstab entry:
```
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

dmesg | tail output:
```
[29294.006658] usb 3-6: USB disconnect, address 2
[29697.678219] APIC error on CPU0: 40(40)
[30631.676159] APIC error on CPU0: 40(40)
[31093.671313] APIC error on CPU0: 40(40)
[31152.719454] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[31152.719463] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[31152.719466] ide: failed opcode was: unknown
[31152.719805] hdc: error code: 0x70  sense_key: 0x05  asc: 0x64  ascq: 0x00
[31152.719810] end_request: I/O error, dev hdc, sector 64
[31152.720371] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
```

hdc mentioned in syslog:
```
Oct 20 16:13:10 monstr kernel: [   23.523483]     ide1: BM-DMA at 0xf408-0xf40f, BIOS settings: hdc:DMA, hdd:pio
Oct 20 16:13:10 monstr kernel: [   23.523492] Probing IDE interface ide0...
Oct 20 16:13:10 monstr kernel: [   23.813943] usb 3-6: new high speed USB device using ehci_hcd and address 2
Oct 20 16:13:10 monstr kernel: [   23.814448] hda: ST3200822A, ATA DISK drive
Oct 20 16:13:10 monstr kernel: [   23.950714] usb 3-6: configuration #1 chosen from 1 choice
Oct 20 16:13:10 monstr kernel: [   23.959553] usbcore: registered new interface driver libusual
Oct 20 16:13:10 monstr kernel: [   23.962502] Initializing USB Mass Storage driver...
Oct 20 16:13:10 monstr kernel: [   23.962559] scsi4 : SCSI emulation for USB Mass Storage devices
Oct 20 16:13:10 monstr kernel: [   23.962605] usb-storage: device found at 2
Oct 20 16:13:10 monstr kernel: [   23.962606] usb-storage: waiting for device to settle before scanning
Oct 20 16:13:10 monstr kernel: [   23.962617] usbcore: registered new interface driver usb-storage
Oct 20 16:13:10 monstr kernel: [   23.962620] USB Mass Storage support registered.
Oct 20 16:13:10 monstr kernel: [   24.098056] hdb: MAXTOR STM3320620A, ATA DISK drive
Oct 20 16:13:10 monstr kernel: [   24.157586] hda: selected mode 0x45
Oct 20 16:13:10 monstr kernel: [   24.157956] hdb: selected mode 0x45
Oct 20 16:13:10 monstr kernel: [   24.158243] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Oct 20 16:13:10 monstr kernel: [   24.164341] Probing IDE interface ide1...
[COLOR="Red"]Oct 20 16:13:10 monstr kernel: [   24.901219] hdc: LITE-ON DVDRW SOHW-1693S, ATAPI CD/DVD-ROM drive
Oct 20 16:13:10 monstr kernel: [   25.576059] hdc: selected mode 0x44[/COLOR]
Oct 20 16:13:10 monstr kernel: [   25.576357] ide1 at 0x170-0x177,0x376 on irq 15
Oct 20 16:13:10 monstr kernel: [   25.577374] pata_pdc2027x 0000:02:00.0: version 0.9
Oct 20 16:13:10 monstr kernel: [   25.577425] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 20 (level, low) -> IRQ 20
Oct 20 16:13:10 monstr kernel: [   25.677557] pata_pdc2027x 0000:02:00.0: PLL input clock 16687 kHz
Oct 20 16:13:10 monstr kernel: [   25.708430] scsi5 : pata_pdc2027x
Oct 20 16:13:10 monstr kernel: [   25.708726] scsi6 : pata_pdc2027x
Oct 20 16:13:10 monstr kernel: [   25.708877] ata5: PATA max UDMA/133 cmd 0xffffc200005f17c0 ctl 0xffffc200005f1fda bmdma 0xffffc200005f1000 irq 20
Oct 20 16:13:10 monstr kernel: [   25.708882] ata6: PATA max UDMA/133 cmd 0xffffc200005f15c0 ctl 0xffffc200005f1dda bmdma 0xffffc200005f1008 irq 20
Oct 20 16:13:10 monstr kernel: [   25.713463] hda: max request size: 512KiB
Oct 20 16:13:10 monstr kernel: [   25.723456] hda: 390721968 sectors (200049 MB) w/8192KiB Cache, CHS=24321/255/63, UDMA(100)
Oct 20 16:13:10 monstr kernel: [   25.723780] hda: cache flushes supported
Oct 20 16:13:10 monstr kernel: [   25.723827]  hda: hda1 hda2 < hda5 >
Oct 20 16:13:10 monstr kernel: [   25.769347] hdb: max request size: 512KiB
Oct 20 16:13:10 monstr kernel: [   25.809143] hdb: 625142448 sectors (320072 MB) w/16384KiB Cache, CHS=38913/255/63, UDMA(100)
Oct 20 16:13:10 monstr kernel: [   25.833540] hdb: cache flushes supported
Oct 20 16:13:10 monstr kernel: [   25.833576]  hdb: hdb1
[COLOR="Red"]Oct 20 16:13:10 monstr kernel: [   25.880495] hdc: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(66)
Oct 20 16:13:10 monstr kernel: [   25.880504] Uniform CD-ROM driver Revision: 3.20[/COLOR]

```

really bad looking portion of syslog:
```
Oct 21 00:36:48 monstr kernel: [28571.897889] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Oct 21 00:36:48 monstr kernel: [28571.897898] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Oct 21 00:36:48 monstr kernel: [28571.897901] ide: failed opcode was: unknown
Oct 21 00:36:48 monstr kernel: [28571.898234] hdc: error code: 0x70  sense_key: 0x05  asc: 0x64  ascq: 0x00
Oct 21 00:36:48 monstr kernel: [28571.898238] end_request: I/O error, dev hdc, sector 817920
Oct 21 00:36:48 monstr kernel: [28571.898242] Buffer I/O error on device hdc, logical block 204480
Oct 21 00:36:48 monstr kernel: [28571.898247] Buffer I/O error on device hdc, logical block 204481
Oct 21 00:36:48 monstr kernel: [28571.899126] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Oct 21 00:36:48 monstr kernel: [28571.899131] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Oct 21 00:36:48 monstr kernel: [28571.899133] ide: failed opcode was: unknown
Oct 21 00:36:48 monstr kernel: [28571.899466] hdc: error code: 0x70  sense_key: 0x05  asc: 0x64  ascq: 0x00
Oct 21 00:36:48 monstr kernel: [28571.899469] end_request: I/O error, dev hdc, sector 817920
Oct 21 00:36:48 monstr kernel: [28571.899471] Buffer I/O error on device hdc, logical block 204480
Oct 21 00:36:48 monstr kernel: [28571.900038] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Oct 21 00:36:48 monstr kernel: [28571.900043] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Oct 21 00:36:48 monstr kernel: [28571.900046] ide: failed opcode was: unknown
Oct 21 00:36:48 monstr kernel: [28571.900378] hdc: error code: 0x70  sense_key: 0x05  asc: 0x64  ascq: 0x00
Oct 21 00:36:48 monstr kernel: [28571.900381] end_request: I/O error, dev hdc, sector 817924
Oct 21 00:36:48 monstr kernel: [28571.900384] Buffer I/O error on device hdc, logical block 204481
Oct 21 00:36:48 monstr kernel: [28571.901083] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Oct 21 00:36:48 monstr kernel: [28571.901089] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Oct 21 00:36:48 monstr kernel: [28571.901091] ide: failed opcode was: unknown
Oct 21 00:36:48 monstr kernel: [28571.901421] hdc: error code: 0x70  sense_key: 0x05  asc: 0x64  ascq: 0x00
Oct 21 00:36:48 monstr kernel: [28571.901424] end_request: I/O error, dev hdc, sector 818048
Oct 21 00:36:48 monstr kernel: [28571.901426] Buffer I/O error on device hdc, logical block 204512
Oct 21 00:36:48 monstr kernel: [28571.901990] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Oct 21 00:36:48 monstr kernel: [28571.901995] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }

```

---

### Post by dave-5B on 2007-10-21
they amalgamated the pata and sata drivers in gutsy so all drives are now referred to as sda sdb etc... my cdrom for eg is scd0

EDIT: upon actually reading your post i dont actually know if this will solve your problem

---

### Post by eatloaf on 2007-10-21
ok. so turns out that data discs mount just fine.  It's music CDs that won't mount.

any ideas?

---

### Post by eatloaf on 2007-10-22
ok.  in linux land music cds don't get / need to be mounted.

problem solved.

---

