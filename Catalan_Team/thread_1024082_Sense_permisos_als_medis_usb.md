---
title: "Sense permisos als medis usb"
date: 2008-12-28
forum: Catalan Team
---

### Post by Daerun on 2008-12-28
Des de fa uns dies m'he adonat que, en connectar un pendrive o la tageta de la càmera, no hi tinc tots els permisos, i em trobo que no puc retallar ni esborrar les fotografies i documents que hi tinc, amb la cual cosa no els puc continuar fent servir per a transferir arxius, perquè se m'omplen y no els puc buidar.
A veure si em doneu un copet de má.

---

### Post by lesergi on 2008-12-29
Hola!

Segons dius sembla que els pots muntar però no tens permís d'escriptura. Podem començar veient amb quins permisos es munta el volum. Després de muntar el pendrive copia l'eixida del fitxer /etc/mtab.

Salut!

---

### Post by elbuit on 2008-12-29
Podries passar-nos l'eixida de l'ordre mount per apropar-nos a identificar el problema.
Es possible que t'ho monte en permissos de sols lectura, podria ser degut a que el filesystem no tinga consistència, i caldria fer un fsck, també pordia ser que no estigueren en FAT, sino en NTFS, encara que la darrera opció em sembla menys probable.
Si tens problemes amb la consistencia del FS el dmesg ho deuria d'escupir.
Altra cosa, poden ser les opcions amb les quals es monten automàticament els dispossitius.
Si executes gconf-editor i vas a:
System->Storage->Default options -> vfat, hauria de posar algo així en la clau mount_options: utf8, umask=077,exec
Ja ens dius com has quedat

---

### Post by Daerun on 2008-12-29
A veure, per començar, aqui esa el /etc/mtab


```
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-22-generic/volatile tmpfs rw 0 0
/dev/sdb1 /media/Documents fuseblk rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/daerun/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=daerun 0 0
/dev/scd0 /media/cdrom0 udf ro,nosuid,nodev,utf8,user=daerun 0 0
/dev/sde1 /media/CAMERA3 vfat ro,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0
```
Es tracta d'una targeta SD formatejada en fat16

Pel què fa al que comentes, elbuit, a la clau vfat hi posa el següent:

shortname=mixed,uid=,utf8,umask=077,exec,flush

i aqui está el dmesg. Gràcies. :D

```
[   25.222527] ACPI: Fan [FAN] (on)
[   25.230955] ACPI: Thermal Zone [THRM] (36 C)
[   25.413574] usbcore: registered new interface driver usbfs
[   25.413611] usbcore: registered new interface driver hub
[   25.417985] usbcore: registered new device driver usb
[   25.429570] USB Universal Host Controller Interface driver v3.0
[   25.429688] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   25.429708] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   25.429714] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   25.430034] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   25.430067] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000c000
[   25.430276] usb usb1: configuration #1 chosen from 1 choice
[   25.430318] hub 1-0:1.0: USB hub found
[   25.430328] hub 1-0:1.0: 2 ports detected
[   25.533461] ACPI: PCI Interrupt 0000:00:1d.1[b] -> GSI 19 (level, low) -> IRQ 17
[   25.533477] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   25.533482] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   25.533527] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   25.533568] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000c400
[   25.533781] usb usb2: configuration #1 chosen from 1 choice
[   25.533822] hub 2-0:1.0: USB hub found
[   25.533832] hub 2-0:1.0: 2 ports detected
[   25.637284] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   25.637301] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   25.637306] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   25.637358] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   25.637389] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000c800
[   25.637590] usb usb3: configuration #1 chosen from 1 choice
[   25.637634] hub 3-0:1.0: USB hub found
[   25.637651] hub 3-0:1.0: 2 ports detected
[   25.732472] SCSI subsystem initialized
[   25.744042] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 16
[   25.744065] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   25.744070] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   25.744119] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   25.744153] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000cc00
[   25.744347] usb usb4: configuration #1 chosen from 1 choice
[   25.744387] hub 4-0:1.0: USB hub found
[   25.744403] hub 4-0:1.0: 2 ports detected
[   25.764892] libata version 3.00 loaded.
[   25.772871] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   25.848956] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
[   25.848975] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   25.848981] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   25.849020] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   25.852940] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   25.852955] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xfb000000
[   25.900607] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   25.900798] usb usb5: configuration #1 chosen from 1 choice
[   25.900844] hub 5-0:1.0: USB hub found
[   25.900855] hub 5-0:1.0: 8 ports detected
[   25.920743] Floppy drive(s): fd0 is 1.44M
[   25.939327] FDC 0 is a post-1991 82077
[   26.006884] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   26.006965] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   26.006988] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   26.007493] ACPI: PCI Interrupt 0000:02:0e.0[A] -> GSI 18 (level, low) -> IRQ 18
[   26.027411] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x04, vendor 0x4243)
[   26.027422] ssb: Core 1 found: V90 (cc 0x807, rev 0x01, vendor 0x4243)
[   26.027429] ssb: Core 2 found: PCI (cc 0x804, rev 0x02, vendor 0x4243)
[   26.067409] ssb: Sonics Silicon Backplane found on PCI device 0000:02:0e.0
[   26.067451] b44.c:v2.0
[   26.087656] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:10:5c:eb:83:ef
[   26.093273] ata_piix 0000:00:1f.1: version 2.12
[   26.093293] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   26.093335] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   26.093429] scsi0 : ata_piix
[   26.093501] scsi1 : ata_piix
[   26.094098] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[   26.094101] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[   26.303922] usb 1-1: device not accepting address 2, error -71
[   26.312097] ata1.00: ATA-7: ST3160215A, 3.AAD, max UDMA/100
[   26.312103] ata1.00: 312581808 sectors, multi 16: LBA48 
[   26.357851] ata1.01: ATA-7: MAXTOR STM3200820A, 3.AAD, max UDMA/100
[   26.357856] ata1.01: 390721968 sectors, multi 0: LBA48 
[   26.403554] ata1.00: configured for UDMA/100
[   26.449189] ata1.01: configured for UDMA/100
[   26.767295] ata2.01: ATAPI: HL-DT-ST DVDRAM GSA-H42N, RL00, max UDMA/66
[   26.767311] ata2.01: limited to UDMA/33 due to 40-wire cable
[   26.938900] ata2.01: configured for UDMA/33
[   26.939052] scsi 0:0:0:0: Direct-Access     ATA      ST3160215A       3.AA PQ: 0 ANSI: 5
[   26.939249] scsi 0:0:1:0: Direct-Access     ATA      MAXTOR STM320082 3.AA PQ: 0 ANSI: 5
[   26.942377] scsi 1:0:1:0: CD-ROM            HL-DT-ST DVDRAM GSA-H42N  RL00 PQ: 0 ANSI: 5
[   26.955225] Driver 'sd' needs updating - please use bus_type methods
[   26.955376] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   26.955407] sd 0:0:0:0: [sda] Write Protect is off
[   26.955412] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   26.955450] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.955570] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   26.955592] sd 0:0:0:0: [sda] Write Protect is off
[   26.955596] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   26.955635] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.955642]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   26.975228]  sda1 sda2 < sda5 sda6 > sda3
[   27.000546] sd 0:0:0:0: [sda] Attached SCSI disk
[   27.000664] sd 0:0:1:0: [sdb] 390721968 512-byte hardware sectors (200050 MB)
[   27.000686] sd 0:0:1:0: [sdb] Write Protect is off
[   27.000691] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   27.000730] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.000816] sd 0:0:1:0: [sdb] 390721968 512-byte hardware sectors (200050 MB)
[   27.000838] sd 0:0:1:0: [sdb] Write Protect is off
[   27.000842] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   27.000882] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.000889]  sdb: [LDM] sdb1
[   27.080181] sd 0:0:1:0: [sdb] Attached SCSI disk
[   27.086874] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   27.086910] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   27.086940] sr 1:0:1:0: Attached scsi generic sg2 type 5
[   27.102029] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   27.102038] Uniform CD-ROM driver Revision: 3.20
[   27.102127] sr 1:0:1:0: Attached scsi CD-ROM sr0
[   27.149332] usb 1-1: new low speed USB device using uhci_hcd and address 4
[   27.326643] usb 1-1: configuration #1 chosen from 1 choice
[   27.624452] usb 2-2: new full speed USB device using uhci_hcd and address 2
[   27.793336] usb 2-2: configuration #1 chosen from 1 choice
[   27.796247] hub 2-2:1.0: USB hub found
[   27.798205] hub 2-2:1.0: 4 ports detected
[   28.108577] usb 2-2.1: new low speed USB device using uhci_hcd and address 3
[   28.243456] usb 2-2.1: configuration #1 chosen from 1 choice
[   28.251351] usbcore: registered new interface driver hiddev
[   28.263961] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input1
[   28.295294] input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-1
[   28.310519] input: USB-compliant keyboard as /devices/pci0000:00/0000:00:1d.1/usb2/2-2/2-2.1/2-2.1:1.0/input/input2
[   28.331180] input,hidraw1: USB HID v1.10 Keyboard [USB-compliant keyboard] on usb-0000:00:1d.1-2.1
[   28.356550] input: USB-compliant keyboard as /devices/pci0000:00/0000:00:1d.1/usb2/2-2/2-2.1/2-2.1:1.1/input/input3
[   28.383165] input,hiddev96,hidraw2: USB HID v1.10 Mouse [USB-compliant keyboard] on usb-0000:00:1d.1-2.1
[   28.383195] usbcore: registered new interface driver usbhid
[   28.383202] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   28.538232] Attempting manual resume
[   28.538236] swsusp: Resume From Partition 8:6
[   28.538238] PM: Checking swsusp image.
[   28.538450] PM: Resume from disk failed.
[   28.583273] kjournald starting.  Commit interval 5 seconds
[   28.583282] EXT3-fs: mounted filesystem with ordered data mode.
[   36.261652] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   36.314987] Linux agpgart interface v0.102
[   36.422165] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   36.464525] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   36.513172] intel_rng: FWH not detected
[   36.661074] parport_pc 00:09: reported by Plug and Play ACPI
[   36.661123] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   36.691991] agpgart: Detected an Intel 865 Chipset.
[   36.694474] agpgart: AGP aperture is 64M @ 0xf0000000
[   36.750604] parport0: Printer, HEWLETT-PACKARD DESKJET 840C
[   36.925153] input: Power Button (FF) as /devices/virtual/input/input5
[   36.947394] ACPI: Power Button (FF) [PWRF]
[   36.947512] input: Power Button (CM) as /devices/virtual/input/input6
[   36.947665] iTCO_vendor_support: vendor-support=0
[   36.958401] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   36.958536] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x0460)
[   36.958580] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   36.979341] ACPI: Power Button (CM) [PWRB]
[   36.979446] input: Sleep Button (CM) as /devices/virtual/input/input7
[   37.015254] ACPI: Sleep Button (CM) [SLPB]
[   37.275200] nvidia: module license 'NVIDIA' taints kernel.
[   37.962281] Linux video capture interface: v2.00
[   38.337062] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.6 loaded
[   38.337219] cx88[0]: subsystem: 0070:9402, board: Hauppauge WinTV-HVR1100 DVB-T/Hybrid [card=40,autodetected]
[   38.337224] cx88[0]: TV tuner type 63, Radio tuner type -1
[   38.368381] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[   38.494648] tveeprom 0-0050: Hauppauge model 94009, rev C2A0, serial# 119508
[   38.494656] tveeprom 0-0050: MAC address is 00-0D-FE-01-D2-D4
[   38.494661] tveeprom 0-0050: tuner model is Philips FMD1216ME (idx 100, type 63)
[   38.494666] tveeprom 0-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xf4)
[   38.494671] tveeprom 0-0050: audio processor is CX882 (idx 33)
[   38.494676] tveeprom 0-0050: decoder processor is CX882 (idx 25)
[   38.494680] tveeprom 0-0050: has radio, has IR receiver, has no IR transmitter
[   38.494684] cx88[0]: hauppauge eeprom: model=94009
[   38.494809] input: cx88 IR (Hauppauge WinTV-HVR110 as /devices/pci0000:00/0000:00:1e.0/0000:02:0a.2/input/input8
[   38.508525] cx88[0]/2: cx2388x 8802 Driver Manager
[   38.508553] ACPI: PCI Interrupt 0000:02:0a.2[A] -> GSI 22 (level, low) -> IRQ 20
[   38.508566] cx88[0]/2: found at 0000:02:0a.2, rev: 5, irq: 20, latency: 32, mmio: 0xf8000000
[   38.508639] ACPI: PCI Interrupt 0000:02:0a.0[A] -> GSI 22 (level, low) -> IRQ 20
[   38.508651] cx88[0]/0: found at 0000:02:0a.0, rev: 5, irq: 20, latency: 32, mmio: 0xf6000000
[   38.669361] cx2388x alsa driver version 0.0.6 loaded
[   38.981786] tuner 0-0061: chip found @ 0xc2 (cx88[0])
[   38.984447] tuner-simple 0-0061: type set to 63 (Philips FMD1216ME MK3 Hybrid Tuner)
[   38.984454] tuner 0-0061: type set to Philips FMD1216ME M
[   38.987100] tuner-simple 0-0061: type set to 63 (Philips FMD1216ME MK3 Hybrid Tuner)
[   38.987111] tuner 0-0061: type set to Philips FMD1216ME M
[   38.989365] tuner 0-0063: chip found @ 0xc6 (cx88[0])
[   39.000087] cx88[0]/0: registered device video0 [v4l2]
[   39.000134] cx88[0]/0: registered device vbi0
[   39.000174] cx88[0]/0: registered device radio0
[   39.027506] ACPI: PCI Interrupt 0000:02:0a.1[A] -> GSI 22 (level, low) -> IRQ 20
[   39.027551] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[   39.028100] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   39.028378] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   39.085786] ACPI: PCI Interrupt 0000:00:1f.5[b] -> GSI 17 (level, low) -> IRQ 21
[   39.085816] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   39.134888] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[   39.134896] cx88/2: registering cx8802 driver, type: dvb access: shared
[   39.134903] cx88[0]/2: subsystem: 0070:9402, board: Hauppauge WinTV-HVR1100 DVB-T/Hybrid [card=40]
[   39.134910] cx88[0]/2: cx2388x based DVB/ATSC card
[   39.270621] DVB: registering new adapter (cx88[0])
[   39.270640] DVB: registering frontend 0 (Conexant CX22702 DVB-T)...
[   39.406889] intel8x0_measure_ac97_clock: measured 54526 usecs
[   39.406894] intel8x0: clocking to 48000
[   40.963923] lp0: using parport0 (interrupt-driven).
[   41.156798] Adding 2096440k swap on /dev/sda6.  Priority:-1 extents:1 across:2096440k
[   41.737334] EXT3 FS on sda5, internal journal
[   43.558386] ip_tables: (C) 2000-2006 Netfilter Core Team
[   44.068690] No dock devices found.
[   45.460671] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   45.460680] apm: disabled - APM is not SMP safe.
[   46.437822] ppdev: user-space parallel port driver
[   46.639874] audit(1230489019.801:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5360 profile="/usr/sbin/cupsd" namespace="default"
[   49.697574] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   49.697583] vboxdrv: Successfully done.
[   49.697586] vboxdrv: Found 2 processor cores.
[   49.697612] vboxdrv: fAsync=0 u64DiffCores=4420.
[   49.698848] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   49.698860] vboxdrv: Successfully loaded version 1.6.2 (interface 0x00070002).
[   52.221733] Bluetooth: Core ver 2.11
[   52.222289] NET: Registered protocol family 31
[   52.222297] Bluetooth: HCI device and connection manager initialized
[   52.222304] Bluetooth: HCI socket layer initialized
[   52.272865] Bluetooth: L2CAP ver 2.9
[   52.272872] Bluetooth: L2CAP socket layer initialized
[   52.347415] Bluetooth: RFCOMM socket layer initialized
[   52.347860] Bluetooth: RFCOMM TTY layer initialized
[   52.347869] Bluetooth: RFCOMM ver 1.8
[   54.522066] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   54.522083] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   54.522114] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   54.882695] b44: eth0: Link is up at 100 Mbps, full duplex.
[   54.882706] b44: eth0: Flow control is off for TX and off for RX.
[   57.050150] NET: Registered protocol family 17
[   58.695933] NET: Registered protocol family 10
[   58.696430] lo: Disabled Privacy Extensions
[   65.373541] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   65.373569] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   65.373579] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   65.373591] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   65.373602] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   65.373615] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   65.373625] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   65.373638] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   65.373649] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   65.373659] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   65.373670] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   65.373682] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   65.373693] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   65.373703] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   65.373713] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   65.373724] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   65.373734] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   65.373745] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   65.373756] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   65.373769] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   65.373779] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   65.373790] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   65.373801] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   65.373814] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   65.373824] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   65.373838] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   65.373848] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   65.373859] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   65.373870] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   65.373880] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   65.373891] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   65.373902] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   65.373912] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   65.373923] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   65.373935] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   65.373946] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   65.373958] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   65.373970] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   65.373981] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   65.373992] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   65.374003] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   65.374013] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   65.374024] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   65.374035] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   65.374045] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   65.374056] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   65.374068] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   65.374078] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   65.374089] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   65.374099] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   65.374107] cx88[0]/1: IRQ loop detected, disabling interrupts
[   65.378505] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   65.388382] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   69.064555] eth0: no IPv6 routers present
[  107.392904] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[  107.392925] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[  107.392960] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[ 2359.366806] end_request: I/O error, dev sr0, sector 1248
[ 2359.561740] UDF-fs: Partition marked readonly; forcing readonly mount
[ 2359.638475] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'SIMPSONS_SEASON2_DISC2', timestamp 2002/05/22 04:00 (103c)
[11855.050363] usb 5-6: new high speed USB device using ehci_hcd and address 4
[11855.199550] usb 5-6: configuration #1 chosen from 1 choice
[11855.889053] usbcore: registered new interface driver libusual
[11856.206118] Initializing USB Mass Storage driver...
[11856.206554] scsi2 : SCSI emulation for USB Mass Storage devices
[11856.207313] usbcore: registered new interface driver usb-storage
[11856.207322] USB Mass Storage support registered.
[11856.208081] usb-storage: device found at 4
[11856.208088] usb-storage: waiting for device to settle before scanning
[11861.231131] usb-storage: device scan complete
[11861.232015] scsi 2:0:0:0: Direct-Access     Generic  STORAGE DEVICE   9317 PQ: 0 ANSI: 0
[11861.237272] scsi 2:0:0:1: Direct-Access     Generic  STORAGE DEVICE   9317 PQ: 0 ANSI: 0
[11861.238509] scsi 2:0:0:2: Direct-Access     Generic  STORAGE DEVICE   9317 PQ: 0 ANSI: 0
[11861.239635] scsi 2:0:0:3: Direct-Access     Generic  STORAGE DEVICE   9317 PQ: 0 ANSI: 0
[11861.242752] sd 2:0:0:0: [sdc] Attached SCSI removable disk
[11861.242824] sd 2:0:0:0: Attached scsi generic sg3 type 0
[11861.244554] sd 2:0:0:1: [sdd] Attached SCSI removable disk
[11861.244635] sd 2:0:0:1: Attached scsi generic sg4 type 0
[11861.246421] sd 2:0:0:2: [sde] Attached SCSI removable disk
[11861.246506] sd 2:0:0:2: Attached scsi generic sg5 type 0
[11861.248433] sd 2:0:0:3: [sdf] Attached SCSI removable disk
[11861.248504] sd 2:0:0:3: Attached scsi generic sg6 type 0
[11919.473891] sd 2:0:0:2: [sde] 1850368 512-byte hardware sectors (947 MB)
[11919.477123] sd 2:0:0:2: [sde] Write Protect is on
[11919.477132] sd 2:0:0:2: [sde] Mode Sense: 03 00 80 00
[11919.477138] sd 2:0:0:2: [sde] Assuming drive cache: write through
[11919.480235] sd 2:0:0:2: [sde] 1850368 512-byte hardware sectors (947 MB)
[11919.481484] sd 2:0:0:2: [sde] Write Protect is on
[11919.481490] sd 2:0:0:2: [sde] Mode Sense: 03 00 80 00
[11919.481496] sd 2:0:0:2: [sde] Assuming drive cache: write through
[11919.481503]  sde: sde1
[12569.402095] python[7502]: segfault at 00000000 eip b6cf4786 esp bf8946c0 error 4
[12616.199295] sd 2:0:0:2: [sde] 1850368 512-byte hardware sectors (947 MB)
[12616.201547] sd 2:0:0:2: [sde] Write Protect is on
[12616.201554] sd 2:0:0:2: [sde] Mode Sense: 03 00 80 00
[12616.201559] sd 2:0:0:2: [sde] Assuming drive cache: write through
[12616.202909] sd 2:0:0:2: [sde] 1850368 512-byte hardware sectors (947 MB)
[12616.204172] sd 2:0:0:2: [sde] Write Protect is on
[12616.204180] sd 2:0:0:2: [sde] Mode Sense: 03 00 80 00
[12616.204185] sd 2:0:0:2: [sde] Assuming drive cache: write through
[12616.204199]  sde: sde1
[13060.392186] python[7719]: segfault at 00000000 eip b6d2f786 esp bfde8bd0 error 4
[18394.208372] python[6748]: segfault at 00000000 eip b6d87786 esp bfa4afa0 error 4
[20417.054084] usb 5-6: USB disconnect, address 4
[51311.681558] usb 5-6: new high speed USB device using ehci_hcd and address 5
[51311.824388] usb 5-6: configuration #1 chosen from 1 choice
[51311.825060] scsi3 : SCSI emulation for USB Mass Storage devices
[51311.825701] usb-storage: device found at 5
[51311.825707] usb-storage: waiting for device to settle before scanning
[51316.819250] usb-storage: device scan complete
[51316.820234] scsi 3:0:0:0: Direct-Access     Generic  STORAGE DEVICE   9317 PQ: 0 ANSI: 0
[51316.821034] scsi 3:0:0:1: Direct-Access     Generic  STORAGE DEVICE   9317 PQ: 0 ANSI: 0
[51316.821867] scsi 3:0:0:2: Direct-Access     Generic  STORAGE DEVICE   9317 PQ: 0 ANSI: 0
[51316.822586] scsi 3:0:0:3: Direct-Access     Generic  STORAGE DEVICE   9317 PQ: 0 ANSI: 0
[51316.826893] sd 3:0:0:0: [sdc] Attached SCSI removable disk
[51316.826972] sd 3:0:0:0: Attached scsi generic sg3 type 0
[51316.828529] sd 3:0:0:1: [sdd] Attached SCSI removable disk
[51316.828647] sd 3:0:0:1: Attached scsi generic sg4 type 0
[51316.830276] sd 3:0:0:2: [sde] Attached SCSI removable disk
[51316.830341] sd 3:0:0:2: Attached scsi generic sg5 type 0
[51316.831636] sd 3:0:0:3: [sdf] Attached SCSI removable disk
[51316.831702] sd 3:0:0:3: Attached scsi generic sg6 type 0
[51333.316185] sd 3:0:0:2: [sde] 1850368 512-byte hardware sectors (947 MB)
[51333.317687] sd 3:0:0:2: [sde] Write Protect is on
[51333.317697] sd 3:0:0:2: [sde] Mode Sense: 03 00 80 00
[51333.317701] sd 3:0:0:2: [sde] Assuming drive cache: write through
[51333.320375] sd 3:0:0:2: [sde] 1850368 512-byte hardware sectors (947 MB)
[51333.322073] sd 3:0:0:2: [sde] Write Protect is on
[51333.322082] sd 3:0:0:2: [sde] Mode Sense: 03 00 80 00
[51333.322086] sd 3:0:0:2: [sde] Assuming drive cache: write through
[51333.322096]  sde: sde1
[51912.564207] python[8574]: segfault at 00000000 eip b6cff786 esp bf9cff30 error 4
[51916.530015] usb 5-6: USB disconnect, address 5
[65536.155745] end_request: I/O error, dev sr0, sector 1248
[65536.366012] UDF-fs: Partition marked readonly; forcing readonly mount
[65536.445991] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'SIMPSONS_SEASON2_DISC2', timestamp 2002/05/22 04:00 (103c)
[75582.211250] vlc[10424]: segfault at 000000d4 eip b7d99916 esp b34fec90 error 4
[81698.994672] ppdev0: registered pardevice
[81698.994694] ppdev0: unregistered pardevice
[81700.007040] ppdev0: registered pardevice
[81700.137595] ppdev0: unregistered pardevice
[81710.560348] usb 2-2.2: new full speed USB device using uhci_hcd and address 4
[81710.664131] usb 2-2.2: not running at top speed; connect to a high speed hub
[81710.697221] usb 2-2.2: configuration #1 chosen from 1 choice
[81710.701202] scsi4 : SCSI emulation for USB Mass Storage devices
[81710.701492] usb-storage: device found at 4
[81710.701499] usb-storage: waiting for device to settle before scanning
[81715.690856] usb-storage: device scan complete
[81715.693359] scsi 4:0:0:0: Direct-Access     USB      DISK 2.0         1219 PQ: 0 ANSI: 0 CCS
[81715.711305] sd 4:0:0:0: [sdc] 3915776 512-byte hardware sectors (2005 MB)
[81715.714293] sd 4:0:0:0: [sdc] Write Protect is off
[81715.714309] sd 4:0:0:0: [sdc] Mode Sense: 43 00 00 00
[81715.714313] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[81715.726277] sd 4:0:0:0: [sdc] 3915776 512-byte hardware sectors (2005 MB)
[81715.729263] sd 4:0:0:0: [sdc] Write Protect is off
[81715.729274] sd 4:0:0:0: [sdc] Mode Sense: 43 00 00 00
[81715.729279] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[81715.729293]  sdc: sdc1
[81715.771327] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[81715.771406] sd 4:0:0:0: Attached scsi generic sg3 type 0
[82352.759723] python[11305]: segfault at 00000000 eip b6cd4786 esp bfba8b80 error 4
[82357.410485] usb 2-2.2: USB disconnect, address 4
[85219.059136] python[10070]: segfault at 00000000 eip b6d29786 esp bffed750 error 4
[85250.066929] end_request: I/O error, dev sr0, sector 1248
[85250.240699] UDF-fs: Partition marked readonly; forcing readonly mount
[85250.300098] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'SIMPSONS_SEASON2_DISC3', timestamp 2002/05/11 00:31 (103c)
[88084.992210] usb 5-6: new high speed USB device using ehci_hcd and address 6
[88085.134946] usb 5-6: configuration #1 chosen from 1 choice
[88085.136839] scsi5 : SCSI emulation for USB Mass Storage devices
[88085.137110] usb-storage: device found at 6
[88085.137119] usb-storage: waiting for device to settle before scanning
[88090.129821] usb-storage: device scan complete
[88090.130647] scsi 5:0:0:0: Direct-Access     Generic  STORAGE DEVICE   9317 PQ: 0 ANSI: 0
[88090.131393] scsi 5:0:0:1: Direct-Access     Generic  STORAGE DEVICE   9317 PQ: 0 ANSI: 0
[88090.132137] scsi 5:0:0:2: Direct-Access     Generic  STORAGE DEVICE   9317 PQ: 0 ANSI: 0
[88090.132887] scsi 5:0:0:3: Direct-Access     Generic  STORAGE DEVICE   9317 PQ: 0 ANSI: 0
[88090.134713] sd 5:0:0:0: [sdc] Attached SCSI removable disk
[88090.134794] sd 5:0:0:0: Attached scsi generic sg3 type 0
[88090.150988] sd 5:0:0:1: [sdd] Attached SCSI removable disk
[88090.151062] sd 5:0:0:1: Attached scsi generic sg4 type 0
[88090.152554] sd 5:0:0:2: [sde] Attached SCSI removable disk
[88090.152637] sd 5:0:0:2: Attached scsi generic sg5 type 0
[88090.154175] sd 5:0:0:3: [sdf] Attached SCSI removable disk
[88090.154266] sd 5:0:0:3: Attached scsi generic sg6 type 0
[88093.011594] sd 5:0:0:2: [sde] 1850368 512-byte hardware sectors (947 MB)
[88093.017087] sd 5:0:0:2: [sde] Write Protect is on
[88093.017097] sd 5:0:0:2: [sde] Mode Sense: 03 00 80 00
[88093.017101] sd 5:0:0:2: [sde] Assuming drive cache: write through
[88093.028582] sd 5:0:0:2: [sde] 1850368 512-byte hardware sectors (947 MB)
[88093.033199] sd 5:0:0:2: [sde] Write Protect is on
[88093.033208] sd 5:0:0:2: [sde] Mode Sense: 03 00 80 00
[88093.033213] sd 5:0:0:2: [sde] Assuming drive cache: write through
[88093.033223]  sde: sde1

```

---

### Post by papapep on 2008-12-29
Diria que tens la protecció de les targetes posada:

> [88093.017087] sd 5:0:0:2: [sde] Write Protect is on


---

### Post by lesergi on 2008-12-29
Com diu papapep, sembla que tens la protecció de la targeta posada. A més a més, ho confirma el fet que al mtab apareix:
> /dev/sde1 /media/CAMERA3 vfat **ro**,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0
ro significa que s'ha muntat com Read-Only, o siga, sols lectura. Seria interesant que copiares les mateixes sortides però amb el pendrive, ja que el tema de la protecció crec que no seria possible.

Au!

---

### Post by Daerun on 2008-12-30
Si fos això de la protecció voldria que se m'empassés la terra! :oops: Però he mogut la palanqueta de la tarja a l'altra posició y no, segueixo sense poder retallar les fotografies.

En el cas del pendrive, val a dir que no el connecto al mateix port usb, tot i que això suposo que no afecta per res; ara l'he connectat i veig que sí que hi tinc plens permisos, i al mntab hi surt això:

/dev/sdg1 /media/Pendrive vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0


I aqui el dmesg (ho sento, aqui no sé quina línia cal mirar... )

```
[   26.226380] ata1.01: configured for UDMA/100
[   26.542891] ata2.01: ATAPI: HL-DT-ST DVDRAM GSA-H42N, RL00, max UDMA/66
[   26.542908] ata2.01: limited to UDMA/33 due to 40-wire cable
[   26.718507] ata2.01: configured for UDMA/33
[   26.718665] scsi 0:0:0:0: Direct-Access     ATA      ST3160215A       3.AA PQ: 0 ANSI: 5
[   26.718868] scsi 0:0:1:0: Direct-Access     ATA      MAXTOR STM320082 3.AA PQ: 0 ANSI: 5
[   26.721982] scsi 1:0:1:0: CD-ROM            HL-DT-ST DVDRAM GSA-H42N  RL00 PQ: 0 ANSI: 5
[   26.722321] ACPI: PCI Interrupt 0000:02:0e.0[A] -> GSI 18 (level, low) -> IRQ 18
[   26.735072] Driver 'sd' needs updating - please use bus_type methods
[   26.735215] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   26.735239] sd 0:0:0:0: [sda] Write Protect is off
[   26.735244] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   26.735279] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.735374] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   26.735403] sd 0:0:0:0: [sda] Write Protect is off
[   26.735410] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   26.735458] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.735464]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   26.746266] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x04, vendor 0x4243)
[   26.746273] ssb: Core 1 found: V90 (cc 0x807, rev 0x01, vendor 0x4243)
[   26.746279] ssb: Core 2 found: PCI (cc 0x804, rev 0x02, vendor 0x4243)
[   26.752156]  sda1 sda2 < sda5 sda6 > sda3
[   26.777477] sd 0:0:0:0: [sda] Attached SCSI disk
[   26.777588] sd 0:0:1:0: [sdb] 390721968 512-byte hardware sectors (200050 MB)
[   26.777610] sd 0:0:1:0: [sdb] Write Protect is off
[   26.777616] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   26.777655] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.777748] sd 0:0:1:0: [sdb] 390721968 512-byte hardware sectors (200050 MB)
[   26.777769] sd 0:0:1:0: [sdb] Write Protect is off
[   26.777773] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   26.777813] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.777819]  sdb:<6>ssb: Sonics Silicon Backplane found on PCI device 0000:02:0e.0
[   26.786287] b44.c:v2.0
[   26.806590] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:10:5c:eb:83:ef
[   26.856697]  [LDM] sdb1
[   26.857123] sd 0:0:1:0: [sdb] Attached SCSI disk
[   26.863487] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   26.863527] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   26.863565] sr 1:0:1:0: Attached scsi generic sg2 type 5
[   26.879843] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   26.879853] Uniform CD-ROM driver Revision: 3.20
[   26.879959] sr 1:0:1:0: Attached scsi CD-ROM sr0
[   26.998838] usb 1-1: new low speed USB device using uhci_hcd and address 4
[   27.178022] usb 1-1: configuration #1 chosen from 1 choice
[   27.417074] usb 2-2: new full speed USB device using uhci_hcd and address 2
[   27.586803] usb 2-2: configuration #1 chosen from 1 choice
[   27.589711] hub 2-2:1.0: USB hub found
[   27.591671] hub 2-2:1.0: 4 ports detected
[   27.906034] usb 2-2.1: new low speed USB device using uhci_hcd and address 3
[   28.040908] usb 2-2.1: configuration #1 chosen from 1 choice
[   28.048795] usbcore: registered new interface driver hiddev
[   28.061524] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input1
[   28.091927] input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-1
[   28.106981] input: USB-compliant keyboard as /devices/pci0000:00/0000:00:1d.1/usb2/2-2/2-2.1/2-2.1:1.0/input/input2
[   28.127823] input,hidraw1: USB HID v1.10 Keyboard [USB-compliant keyboard] on usb-0000:00:1d.1-2.1
[   28.153023] input: USB-compliant keyboard as /devices/pci0000:00/0000:00:1d.1/usb2/2-2/2-2.1/2-2.1:1.1/input/input3
[   28.179795] input,hiddev96,hidraw2: USB HID v1.10 Mouse [USB-compliant keyboard] on usb-0000:00:1d.1-2.1
[   28.179825] usbcore: registered new interface driver usbhid
[   28.179832] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   28.348406] Attempting manual resume
[   28.348410] swsusp: Resume From Partition 8:6
[   28.348412] PM: Checking swsusp image.
[   28.348617] PM: Resume from disk failed.
[   28.393414] kjournald starting.  Commit interval 5 seconds
[   28.393423] EXT3-fs: mounted filesystem with ordered data mode.
[   35.748279] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   36.458328] parport_pc 00:09: reported by Plug and Play ACPI
[   36.458377] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   36.465931] parport0: Printer, HEWLETT-PACKARD DESKJET 840C
[   36.498314] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   36.518054] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   36.547599] intel_rng: FWH not detected
[   36.582262] Linux agpgart interface v0.102
[   36.742185] agpgart: Detected an Intel 865 Chipset.
[   36.744667] agpgart: AGP aperture is 64M @ 0xf0000000
[   36.786863] input: Power Button (FF) as /devices/virtual/input/input5
[   36.805310] ACPI: Power Button (FF) [PWRF]
[   36.805430] input: Power Button (CM) as /devices/virtual/input/input6
[   36.805575] iTCO_vendor_support: vendor-support=0
[   36.837263] ACPI: Power Button (CM) [PWRB]
[   36.837378] input: Sleep Button (CM) as /devices/virtual/input/input7
[   36.838589] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   36.838717] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x0460)
[   36.838761] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   36.857232] ACPI: Sleep Button (CM) [SLPB]
[   37.279504] ACPI: PCI Interrupt 0000:00:1f.5[b] -> GSI 17 (level, low) -> IRQ 20
[   37.279534] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   37.602900] intel8x0_measure_ac97_clock: measured 54641 usecs
[   37.602906] intel8x0: clocking to 48000
[   38.022799] nvidia: module license 'NVIDIA' taints kernel.
[   38.407790] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   38.408082] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   38.517998] Linux video capture interface: v2.00
[   38.676985] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[   38.677082] ACPI: PCI Interrupt 0000:02:0a.0[A] -> GSI 22 (level, low) -> IRQ 21
[   38.677164] cx88[0]: subsystem: 0070:9402, board: Hauppauge WinTV-HVR1100 DVB-T/Hybrid [card=40,autodetected]
[   38.677168] cx88[0]: TV tuner type 63, Radio tuner type -1
[   38.763180] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.6 loaded
[   38.792877] cx2388x alsa driver version 0.0.6 loaded
[   38.842778] tveeprom 0-0050: Hauppauge model 94009, rev C2A0, serial# 119508
[   38.842786] tveeprom 0-0050: MAC address is 00-0D-FE-01-D2-D4
[   38.842791] tveeprom 0-0050: tuner model is Philips FMD1216ME (idx 100, type 63)
[   38.842797] tveeprom 0-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xf4)
[   38.842803] tveeprom 0-0050: audio processor is CX882 (idx 33)
[   38.842808] tveeprom 0-0050: decoder processor is CX882 (idx 25)
[   38.842813] tveeprom 0-0050: has radio, has IR receiver, has no IR transmitter
[   38.842818] cx88[0]: hauppauge eeprom: model=94009
[   38.843033] input: cx88 IR (Hauppauge WinTV-HVR110 as /devices/pci0000:00/0000:00:1e.0/0000:02:0a.0/input/input8
[   38.896659] cx88[0]/0: found at 0000:02:0a.0, rev: 5, irq: 21, latency: 32, mmio: 0xf6000000
[   39.059666] tuner 0-0061: chip found @ 0xc2 (cx88[0])
[   39.062353] tuner-simple 0-0061: type set to 63 (Philips FMD1216ME MK3 Hybrid Tuner)
[   39.062359] tuner 0-0061: type set to Philips FMD1216ME M
[   39.064983] tuner-simple 0-0061: type set to 63 (Philips FMD1216ME MK3 Hybrid Tuner)
[   39.064992] tuner 0-0061: type set to Philips FMD1216ME M
[   39.066066] tuner 0-0063: chip found @ 0xc6 (cx88[0])
[   39.098801] cx88[0]/0: registered device video0 [v4l2]
[   39.098843] cx88[0]/0: registered device vbi0
[   39.098875] cx88[0]/0: registered device radio0
[   39.110596] cx88[0]/2: cx2388x 8802 Driver Manager
[   39.110627] ACPI: PCI Interrupt 0000:02:0a.2[A] -> GSI 22 (level, low) -> IRQ 21
[   39.110641] cx88[0]/2: found at 0000:02:0a.2, rev: 5, irq: 21, latency: 32, mmio: 0xf8000000
[   39.110708] ACPI: PCI Interrupt 0000:02:0a.1[A] -> GSI 22 (level, low) -> IRQ 21
[   39.110743] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[   39.169955] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[   39.169961] cx88/2: registering cx8802 driver, type: dvb access: shared
[   39.169967] cx88[0]/2: subsystem: 0070:9402, board: Hauppauge WinTV-HVR1100 DVB-T/Hybrid [card=40]
[   39.169971] cx88[0]/2: cx2388x based DVB/ATSC card
[   39.259846] DVB: registering new adapter (cx88[0])
[   39.259854] DVB: registering frontend 0 (Conexant CX22702 DVB-T)...
[   40.615781] lp0: using parport0 (interrupt-driven).
[   40.808759] Adding 2096440k swap on /dev/sda6.  Priority:-1 extents:1 across:2096440k
[   41.389153] EXT3 FS on sda5, internal journal
[   43.260005] ip_tables: (C) 2000-2006 Netfilter Core Team
[   43.754611] No dock devices found.
[   45.170317] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   45.170325] apm: disabled - APM is not SMP safe.
[   46.480071] ppdev: user-space parallel port driver
[   46.682097] audit(1230637815.195:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5359 profile="/usr/sbin/cupsd" namespace="default"
[   49.706459] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   49.706469] vboxdrv: Successfully done.
[   49.706472] vboxdrv: Found 2 processor cores.
[   49.706498] vboxdrv: fAsync=0 u64DiffCores=4572.
[   49.707743] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   49.707755] vboxdrv: Successfully loaded version 1.6.2 (interface 0x00070002).
[   52.238755] Bluetooth: Core ver 2.11
[   52.239307] NET: Registered protocol family 31
[   52.239315] Bluetooth: HCI device and connection manager initialized
[   52.239328] Bluetooth: HCI socket layer initialized
[   52.289829] Bluetooth: L2CAP ver 2.9
[   52.289837] Bluetooth: L2CAP socket layer initialized
[   52.347495] Bluetooth: RFCOMM socket layer initialized
[   52.347518] Bluetooth: RFCOMM TTY layer initialized
[   52.347521] Bluetooth: RFCOMM ver 1.8
[   54.522592] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   54.522609] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   54.522640] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   55.734664] b44: eth0: Link is up at 100 Mbps, full duplex.
[   55.734672] b44: eth0: Flow control is off for TX and off for RX.
[   57.989813] NET: Registered protocol family 17
[   64.656167] NET: Registered protocol family 10
[   64.656694] lo: Disabled Privacy Extensions
[   74.716639] eth0: no IPv6 routers present
[ 1892.835655] usb 3-2: new full speed USB device using uhci_hcd and address 2
[ 1907.928715] usb 3-2: device descriptor read/64, error -110
[ 1923.113615] usb 3-2: device descriptor read/64, error -110
[ 1923.329244] usb 3-2: new full speed USB device using uhci_hcd and address 3
[ 1926.303923] usb 5-6: new high speed USB device using ehci_hcd and address 5
[ 1926.446555] usb 5-6: configuration #1 chosen from 1 choice
[ 1926.518006] usbcore: registered new interface driver libusual
[ 1926.548970] Initializing USB Mass Storage driver...
[ 1926.550950] scsi2 : SCSI emulation for USB Mass Storage devices
[ 1926.552764] usbcore: registered new interface driver usb-storage
[ 1926.552784] USB Mass Storage support registered.
[ 1926.552994] usb-storage: device found at 5
[ 1926.552998] usb-storage: waiting for device to settle before scanning
[ 1931.544050] usb-storage: device scan complete
[ 1931.544795] scsi 2:0:0:0: Direct-Access     Generic  STORAGE DEVICE   9317 PQ: 0 ANSI: 0
[ 1931.545538] scsi 2:0:0:1: Direct-Access     Generic  STORAGE DEVICE   9317 PQ: 0 ANSI: 0
[ 1931.546409] scsi 2:0:0:2: Direct-Access     Generic  STORAGE DEVICE   9317 PQ: 0 ANSI: 0
[ 1931.547156] scsi 2:0:0:3: Direct-Access     Generic  STORAGE DEVICE   9317 PQ: 0 ANSI: 0
[ 1931.549680] sd 2:0:0:0: [sdc] Attached SCSI removable disk
[ 1931.549750] sd 2:0:0:0: Attached scsi generic sg3 type 0
[ 1931.551379] sd 2:0:0:1: [sdd] Attached SCSI removable disk
[ 1931.551453] sd 2:0:0:1: Attached scsi generic sg4 type 0
[ 1931.552978] sd 2:0:0:2: [sde] Attached SCSI removable disk
[ 1931.553045] sd 2:0:0:2: Attached scsi generic sg5 type 0
[ 1931.554850] sd 2:0:0:3: [sdf] Attached SCSI removable disk
[ 1931.554921] sd 2:0:0:3: Attached scsi generic sg6 type 0
[ 1988.026740] sd 2:0:0:2: [sde] 1850368 512-byte hardware sectors (947 MB)
[ 1988.027987] sd 2:0:0:2: [sde] Write Protect is on
[ 1988.027994] sd 2:0:0:2: [sde] Mode Sense: 03 00 80 00
[ 1988.028001] sd 2:0:0:2: [sde] Assuming drive cache: write through
[ 1988.030352] sd 2:0:0:2: [sde] 1850368 512-byte hardware sectors (947 MB)
[ 1988.031611] sd 2:0:0:2: [sde] Write Protect is on
[ 1988.031617] sd 2:0:0:2: [sde] Mode Sense: 03 00 80 00
[ 1988.031622] sd 2:0:0:2: [sde] Assuming drive cache: write through
[ 1988.031629]  sde: sde1
[ 2892.633013] python[6605]: segfault at 00000000 eip b6d75786 esp bfc639d0 error 4
[ 2906.392210] sd 2:0:0:2: [sde] 1850368 512-byte hardware sectors (947 MB)
[ 2906.393552] sd 2:0:0:2: [sde] Write Protect is on
[ 2906.393561] sd 2:0:0:2: [sde] Mode Sense: 03 00 80 00
[ 2906.393567] sd 2:0:0:2: [sde] Assuming drive cache: write through
[ 2906.394677] sd 2:0:0:2: [sde] 1850368 512-byte hardware sectors (947 MB)
[ 2906.395912] sd 2:0:0:2: [sde] Write Protect is on
[ 2906.395918] sd 2:0:0:2: [sde] Mode Sense: 03 00 80 00
[ 2906.395923] sd 2:0:0:2: [sde] Assuming drive cache: write through
[ 2906.395932]  sde: sde1
[ 3730.479834] usb 5-7: new high speed USB device using ehci_hcd and address 6
[ 3730.621848] usb 5-7: configuration #1 chosen from 1 choice
[ 3730.622634] scsi3 : SCSI emulation for USB Mass Storage devices
[ 3730.623218] usb-storage: device found at 6
[ 3730.623224] usb-storage: waiting for device to settle before scanning
[ 3731.023858] usb 5-6: reset high speed USB device using ehci_hcd and address 5
[ 3731.545675] usb 5-6: device not accepting address 5, error -71
[ 3731.654732] usb 5-6: reset high speed USB device using ehci_hcd and address 5
[ 3732.174143] usb 5-6: device not accepting address 5, error -71
[ 3732.285602] usb 5-6: reset high speed USB device using ehci_hcd and address 5
[ 3732.511238] usb 5-6: device descriptor read/all, error -71
[ 3732.626599] usb 5-6: reset high speed USB device using ehci_hcd and address 5
[ 3733.035257] usb 5-6: device not accepting address 5, error -71
[ 3733.035296] usb 5-6: USB disconnect, address 5
[ 3733.036696] sd 2:0:0:2: [sde] READ CAPACITY failed
[ 3733.036702] sd 2:0:0:2: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3733.036709] sd 2:0:0:2: [sde] Sense not available.
[ 3733.036730] sd 2:0:0:2: [sde] Write Protect is off
[ 3733.036734] sd 2:0:0:2: [sde] Mode Sense: 00 00 00 00
[ 3733.036737] sd 2:0:0:2: [sde] Assuming drive cache: write through
[ 3733.041547] scsi 2:0:0:0: rejecting I/O to dead device
[ 3733.041571] scsi 2:0:0:0: rejecting I/O to dead device
[ 3733.041581] scsi 2:0:0:0: rejecting I/O to dead device
[ 3733.041590] scsi 2:0:0:0: rejecting I/O to dead device
[ 3733.041596] scsi 2:0:0:0: [sdc] READ CAPACITY failed
[ 3733.041598] scsi 2:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3733.041604] scsi 2:0:0:0: [sdc] Sense not available.
[ 3733.041613] scsi 2:0:0:0: rejecting I/O to dead device
[ 3733.041620] scsi 2:0:0:0: [sdc] Write Protect is off
[ 3733.041624] scsi 2:0:0:0: [sdc] Mode Sense: 00 00 00 00
[ 3733.041628] scsi 2:0:0:0: [sdc] Assuming drive cache: write through
[ 3733.041636] scsi 2:0:0:0: rejecting I/O to dead device
[ 3733.041649] scsi 2:0:0:0: rejecting I/O to dead device
[ 3733.041658] scsi 2:0:0:0: rejecting I/O to dead device
[ 3733.041667] scsi 2:0:0:0: rejecting I/O to dead device
[ 3733.041676] scsi 2:0:0:0: rejecting I/O to dead device
[ 3733.041681] scsi 2:0:0:0: [sdc] READ CAPACITY failed
[ 3733.041684] scsi 2:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3733.041690] scsi 2:0:0:0: [sdc] Sense not available.
[ 3733.041698] scsi 2:0:0:0: rejecting I/O to dead device
[ 3733.041704] scsi 2:0:0:0: [sdc] Write Protect is off
[ 3733.041707] scsi 2:0:0:0: [sdc] Mode Sense: 00 00 00 00
[ 3733.041711] scsi 2:0:0:0: [sdc] Assuming drive cache: write through
[ 3733.041727] scsi 2:0:0:0: rejecting I/O to dead device
[ 3733.042874] scsi 2:0:0:1: rejecting I/O to dead device
[ 3733.042900] scsi 2:0:0:1: rejecting I/O to dead device
[ 3733.042910] scsi 2:0:0:1: rejecting I/O to dead device
[ 3733.042920] scsi 2:0:0:1: rejecting I/O to dead device
[ 3733.042926] scsi 2:0:0:1: [sdd] READ CAPACITY failed
[ 3733.042929] scsi 2:0:0:1: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3733.042936] scsi 2:0:0:1: [sdd] Sense not available.
[ 3733.042943] scsi 2:0:0:1: rejecting I/O to dead device
[ 3733.042949] scsi 2:0:0:1: [sdd] Write Protect is off
[ 3733.042953] scsi 2:0:0:1: [sdd] Mode Sense: 00 00 00 00
[ 3733.042956] scsi 2:0:0:1: [sdd] Assuming drive cache: write through
[ 3733.042963] scsi 2:0:0:1: rejecting I/O to dead device
[ 3733.042977] scsi 2:0:0:1: rejecting I/O to dead device
[ 3733.042985] scsi 2:0:0:1: rejecting I/O to dead device
[ 3733.042994] scsi 2:0:0:1: rejecting I/O to dead device
[ 3733.043003] scsi 2:0:0:1: rejecting I/O to dead device
[ 3733.043009] scsi 2:0:0:1: [sdd] READ CAPACITY failed
[ 3733.043013] scsi 2:0:0:1: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3733.043018] scsi 2:0:0:1: [sdd] Sense not available.
[ 3733.043025] scsi 2:0:0:1: rejecting I/O to dead device
[ 3733.043030] scsi 2:0:0:1: [sdd] Write Protect is off
[ 3733.043034] scsi 2:0:0:1: [sdd] Mode Sense: 00 00 00 00
[ 3733.043036] scsi 2:0:0:1: [sdd] Assuming drive cache: write through
[ 3733.043053] scsi 2:0:0:1: rejecting I/O to dead device
[ 3733.043308] scsi 2:0:0:3: rejecting I/O to dead device
[ 3733.043321] scsi 2:0:0:3: rejecting I/O to dead device
[ 3733.043331] scsi 2:0:0:3: rejecting I/O to dead device
[ 3733.043339] scsi 2:0:0:3: rejecting I/O to dead device
[ 3733.043347] scsi 2:0:0:3: [sdf] READ CAPACITY failed
[ 3733.043350] scsi 2:0:0:3: [sdf] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3733.043355] scsi 2:0:0:3: [sdf] Sense not available.
[ 3733.043362] scsi 2:0:0:3: rejecting I/O to dead device
[ 3733.043368] scsi 2:0:0:3: [sdf] Write Protect is off
[ 3733.043372] scsi 2:0:0:3: [sdf] Mode Sense: 00 00 00 00
[ 3733.043375] scsi 2:0:0:3: [sdf] Assuming drive cache: write through
[ 3733.043381] scsi 2:0:0:3: rejecting I/O to dead device
[ 3733.043395] scsi 2:0:0:3: rejecting I/O to dead device
[ 3733.043403] scsi 2:0:0:3: rejecting I/O to dead device
[ 3733.043412] scsi 2:0:0:3: rejecting I/O to dead device
[ 3733.043421] scsi 2:0:0:3: rejecting I/O to dead device
[ 3733.043427] scsi 2:0:0:3: [sdf] READ CAPACITY failed
[ 3733.043430] scsi 2:0:0:3: [sdf] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3733.043436] scsi 2:0:0:3: [sdf] Sense not available.
[ 3733.043442] scsi 2:0:0:3: rejecting I/O to dead device
[ 3733.043448] scsi 2:0:0:3: [sdf] Write Protect is off
[ 3733.043452] scsi 2:0:0:3: [sdf] Mode Sense: 00 00 00 00
[ 3733.043455] scsi 2:0:0:3: [sdf] Assuming drive cache: write through
[ 3733.043471] scsi 2:0:0:3: rejecting I/O to dead device
[ 3733.391660] usb 3-2: new full speed USB device using uhci_hcd and address 4
[ 3733.535854] usb 3-2: not running at top speed; connect to a high speed hub
[ 3733.556721] python[6704]: segfault at 00000000 eip b6ccc786 esp bfcab210 error 4
[ 3733.568979] usb 3-2: configuration #1 chosen from 1 choice
[ 3733.580278] scsi4 : SCSI emulation for USB Mass Storage devices
[ 3733.581629] usb-storage: device found at 4
[ 3733.581650] usb-storage: waiting for device to settle before scanning
[ 3735.611337] usb-storage: device scan complete
[ 3735.612454] scsi 3:0:0:0: Direct-Access     USB      DISK 2.0         1219 PQ: 0 ANSI: 0 CCS
[ 3735.615930] sd 3:0:0:0: [sdc] 3915776 512-byte hardware sectors (2005 MB)
[ 3735.617185] sd 3:0:0:0: [sdc] Write Protect is off
[ 3735.617194] sd 3:0:0:0: [sdc] Mode Sense: 43 00 00 00
[ 3735.617198] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[ 3735.620289] sd 3:0:0:0: [sdc] 3915776 512-byte hardware sectors (2005 MB)
[ 3735.621042] sd 3:0:0:0: [sdc] Write Protect is off
[ 3735.621050] sd 3:0:0:0: [sdc] Mode Sense: 43 00 00 00
[ 3735.621054] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[ 3735.621062]  sdc:<6>usb 5-7: reset high speed USB device using ehci_hcd and address 6
[ 3735.874199] usb 5-7: device descriptor read/64, error -71
[ 3736.089811] usb 5-7: device descriptor read/64, error -71
[ 3736.305429] usb 5-7: reset high speed USB device using ehci_hcd and address 6
[ 3736.429207] usb 5-7: device descriptor read/64, error -71
[ 3736.652815] usb 5-7: device descriptor read/64, error -71
[ 3736.868427] usb 5-7: reset high speed USB device using ehci_hcd and address 6
[ 3738.571033] usb-storage: device scan complete
[ 3738.574017] scsi 4:0:0:0: Direct-Access     Generic  STORAGE DEVICE   9317 PQ: 0 ANSI: 0
[ 3738.704774] scsi 4:0:0:1: Direct-Access     Generic  STORAGE DEVICE   9317 PQ: 0 ANSI: 0
[ 3738.707751] scsi 4:0:0:2: Direct-Access     Generic  STORAGE DEVICE   9317 PQ: 0 ANSI: 0
[ 3738.710747] scsi 4:0:0:3: Direct-Access     Generic  STORAGE DEVICE   9317 PQ: 0 ANSI: 0
[ 3739.851093] usb 5-7: device not accepting address 6, error -71
[ 3739.907286] usb 5-7: USB disconnect, address 6
[ 3739.907340] sd 3:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 3739.907347] end_request: I/O error, dev sdc, sector 0
[ 3739.907353] Buffer I/O error on device sdc, logical block 0
[ 3739.907450] sd 3:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 3739.907456] end_request: I/O error, dev sdc, sector 0
[ 3739.907460] Buffer I/O error on device sdc, logical block 0
[ 3739.907525] sd 3:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3739.907531] end_request: I/O error, dev sdc, sector 0
[ 3739.907535] Buffer I/O error on device sdc, logical block 0
[ 3739.907563] sd 3:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3739.907570] end_request: I/O error, dev sdc, sector 0
[ 3739.907574] Buffer I/O error on device sdc, logical block 0
[ 3739.907599] sd 3:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3739.907606] end_request: I/O error, dev sdc, sector 0
[ 3739.907610] Buffer I/O error on device sdc, logical block 0
[ 3739.907622] ldm_validate_partition_table(): Disk read failed.
[ 3739.907640] sd 3:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3739.907646] end_request: I/O error, dev sdc, sector 0
[ 3739.907650] Buffer I/O error on device sdc, logical block 0
[ 3739.907674] sd 3:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3739.907680] end_request: I/O error, dev sdc, sector 0
[ 3739.907685] Buffer I/O error on device sdc, logical block 0
[ 3739.907709] sd 3:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3739.907716] end_request: I/O error, dev sdc, sector 0
[ 3739.907720] Buffer I/O error on device sdc, logical block 0
[ 3739.907744] sd 3:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3739.907751] end_request: I/O error, dev sdc, sector 0
[ 3739.907755] Buffer I/O error on device sdc, logical block 0
[ 3739.907766] Dev sdc: unable to read RDB block 0
[ 3739.907783] sd 3:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3739.907789] end_request: I/O error, dev sdc, sector 0
[ 3739.907794] Buffer I/O error on device sdc, logical block 0
[ 3739.907818] sd 3:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3739.907825] end_request: I/O error, dev sdc, sector 0
[ 3739.907858] sd 3:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3739.907865] end_request: I/O error, dev sdc, sector 24
[ 3739.907889] sd 3:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3739.907895] end_request: I/O error, dev sdc, sector 24
[ 3739.907920] sd 3:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3739.907926] end_request: I/O error, dev sdc, sector 0
[ 3739.907951] sd 3:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3739.907957] end_request: I/O error, dev sdc, sector 0
[ 3739.907969]  unable to read partition table
[ 3739.908055] sd 3:0:0:0: [sdc] Attached SCSI removable disk
[ 3739.908140] sd 3:0:0:0: Attached scsi generic sg3 type 0
[ 3739.926489] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[ 3739.926575] sd 4:0:0:0: Attached scsi generic sg3 type 0
[ 3739.933692] sd 4:0:0:1: [sdd] Attached SCSI removable disk
[ 3739.933762] sd 4:0:0:1: Attached scsi generic sg4 type 0
[ 3739.942508] sd 4:0:0:2: [sde] 1850368 512-byte hardware sectors (947 MB)
[ 3739.954349] sd 4:0:0:2: [sde] Write Protect is on
[ 3739.954359] sd 4:0:0:2: [sde] Mode Sense: 03 00 80 00
[ 3739.954364] sd 4:0:0:2: [sde] Assuming drive cache: write through
[ 3739.968332] sd 4:0:0:2: [sde] 1850368 512-byte hardware sectors (947 MB)
[ 3739.973288] sd 4:0:0:2: [sde] Write Protect is on
[ 3739.973298] sd 4:0:0:2: [sde] Mode Sense: 03 00 80 00
[ 3739.973302] sd 4:0:0:2: [sde] Assuming drive cache: write through
[ 3739.973310]  sde: sde1
[ 3739.979395] sd 4:0:0:2: [sde] Attached SCSI removable disk
[ 3739.979464] sd 4:0:0:2: Attached scsi generic sg5 type 0
[ 3739.984353] sd 4:0:0:3: [sdf] Attached SCSI removable disk
[ 3739.984433] sd 4:0:0:3: Attached scsi generic sg6 type 0
[ 3768.368301] usb 5-8: new high speed USB device using ehci_hcd and address 8
[ 3768.480003] usb 5-8: device descriptor read/64, error -71
[ 3768.695615] usb 5-8: device descriptor read/64, error -71
[ 3768.915226] usb 5-8: new high speed USB device using ehci_hcd and address 9
[ 3769.027026] usb 5-8: device descriptor read/64, error -71
[ 3769.242640] usb 5-8: device descriptor read/64, error -32
[ 3769.458262] usb 5-8: new high speed USB device using ehci_hcd and address 10
[ 3769.865528] usb 5-8: device not accepting address 10, error -32
[ 3769.977351] usb 5-8: new high speed USB device using ehci_hcd and address 11
[ 3770.384599] usb 5-8: device not accepting address 11, error -32
[ 3814.211440] usb 2-2.2: new full speed USB device using uhci_hcd and address 4
[ 3814.315230] usb 2-2.2: not running at top speed; connect to a high speed hub
[ 3814.349336] usb 2-2.2: configuration #1 chosen from 1 choice
[ 3814.353335] scsi5 : SCSI emulation for USB Mass Storage devices
[ 3814.353900] usb-storage: device found at 4
[ 3814.353906] usb-storage: waiting for device to settle before scanning
[ 3819.342438] usb-storage: device scan complete
[ 3819.345423] scsi 5:0:0:0: Direct-Access     USB      DISK 2.0         1219 PQ: 0 ANSI: 0 CCS
[ 3819.355418] sd 5:0:0:0: [sdg] 3915776 512-byte hardware sectors (2005 MB)
[ 3819.358392] sd 5:0:0:0: [sdg] Write Protect is off
[ 3819.358402] sd 5:0:0:0: [sdg] Mode Sense: 43 00 00 00
[ 3819.358407] sd 5:0:0:0: [sdg] Assuming drive cache: write through
[ 3819.370354] sd 5:0:0:0: [sdg] 3915776 512-byte hardware sectors (2005 MB)
[ 3819.373350] sd 5:0:0:0: [sdg] Write Protect is off
[ 3819.373358] sd 5:0:0:0: [sdg] Mode Sense: 43 00 00 00
[ 3819.373362] sd 5:0:0:0: [sdg] Assuming drive cache: write through
[ 3819.373372]  sdg: sdg1
[ 3819.428455] sd 5:0:0:0: [sdg] Attached SCSI removable disk
[ 3819.428533] sd 5:0:0:0: Attached scsi generic sg7 type 0
[ 3900.522707] printk: 5 messages suppressed.
[ 3900.522718] python[6976]: segfault at 00000000 eip b6cd4786 esp bfcb6a20 error 4

```

---

### Post by lesergi on 2008-12-30
El pendrive sembla anar bé. Si tornes a tindre problemes amb ell ja ens contes.

Respecte a la targeta, et diria que provares en un altre equip per si és cosa del teu lector, però ho dubte. A mi m'ha passat al mòbil algun cop que sense tenir la targeta protecció contra l'escriptura s'ha muntat amb la protecció. Prova desconnectar-la estant apagada la càmera i sinó estant encesa, tant amb la protecció manual activada i desactivada, potser la protecció l'aplique la pròpia càmera.

Ja ens contes.

---

### Post by Daerun on 2009-01-06
He d'aclarir que la targeta la trec de la càmera i la conecto al lector de targetes del PC.

I res, la càmera no té cap control per a posar la targeta en protecció, de manera que... no sé...

---

### Post by Daerun on 2009-02-19
Al final vaig "tirar pel dret": sudo chmod 777 /media/disk :roll:

Jo, que li tinc tanta alèrgia al terminal :P

(ara no recordo com es posava un tema en solved )

---

