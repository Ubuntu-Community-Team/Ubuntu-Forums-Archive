---
title: "How do I find CDROM"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2008-03-08
How do I find out what my DVD drive is called?
I somehow disabled polling through powertop and now I cant mount it and the pc cant find it.

It should be on /dev/scd0 but it keeps saying "cant find device"..

The enable polling command also returns this error..  

Can anyone help me remount this drive permently again.

Im setting this computer op for a guy who cant hear and he never used a PC before! :)

Any help?

---

### Post by glennric on 2008-03-08
Try the device "/dev/sdc0".  /dev/scd0 is not a valid device name.

---

### Post by taurus on 2008-03-08
You can look at the dmesg to see if your machine even detects your CDROM.

```
dmesg | more
```
Hit the space bar for the next 24 lines.

---

### Post by aktiwers on 2008-03-08
Here is the output:
```
jesper@Jesper-laptop:~$ dmesg | more
[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4
.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 
UTC 2008 (Ubuntu 2.6.22-14.52-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f6d0000 (usable)
[    0.000000]  BIOS-e820: 000000003f6d0000 - 000000003f6df000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f6df000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 118MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f7d60
[    0.000000] Entering add_active_range(0, 0, 259792) 0 entries of 256 used
[    0.000000] Zone PFN ranges:

```

Any ideas?

---

### Post by glennric on 2008-03-08
Try typing
```
ls /dev/sd*
```
in a terminal and see what output you get.

---

### Post by aktiwers on 2008-03-08
```
jesper@Jesper-laptop:~$ ls /dev/sd*
/dev/sda  /dev/sda1  /dev/sda2
```
Also sorry about the "half" output from the other command.. here is the whole:
```

[    8.344000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ
 22
[    8.344000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    8.344000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    8.344000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus numbe
r 3
[    8.344000] uhci_hcd 0000:00:1d.0: irq 22, io base 0x00001860
[    8.344000] usb usb3: configuration #1 chosen from 1 choice
[    8.344000] hub 3-0:1.0: USB hub found
[    8.344000] hub 3-0:1.0: 2 ports detected
[    8.448000] ACPI: PCI Interrupt 0000:00:1d.1[b] -> GSI 17 (level, low) -> IRQ
 17
[    8.448000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    8.448000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    8.448000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus numbe
r 4
[    8.448000] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00001880
[    8.448000] usb usb4: configuration #1 chosen from 1 choice
[    8.448000] hub 4-0:1.0: USB hub found
[    8.448000] hub 4-0:1.0: 2 ports detected
[    8.500000] Clocksource tsc unstable (delta = -130376993 ns)
[    8.552000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ
 18
[    8.552000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    8.552000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    8.552000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus numbe
r 5
[    8.552000] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
[    8.552000] usb usb5: configuration #1 chosen from 1 choice
[    8.552000] hub 5-0:1.0: USB hub found
[    8.552000] hub 5-0:1.0: 2 ports detected
[    8.676000] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 20 (level, low) -> IRQ
 20
[    8.676000] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[    8.676000] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    8.676000] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus numbe
r 6
[    8.676000] ehci_hcd 0000:00:1a.7: debug port 1
[    8.676000] PCI: cache line size of 32 is not supported by device 0000:00:1a.
7
[    8.676000] ehci_hcd 0000:00:1a.7: irq 20, io mem 0xfc504800
[    8.680000] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 
2004
[    8.680000] usb usb6: configuration #1 chosen from 1 choice
[    8.680000] hub 6-0:1.0: USB hub found
[    8.680000] hub 6-0:1.0: 4 ports detected
[    8.784000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ
 22
[    8.784000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    8.784000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    8.784000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus numbe
r 7
[    8.784000] ehci_hcd 0000:00:1d.7: debug port 1
[    8.784000] PCI: cache line size of 32 is not supported by device 0000:00:1d.
7
[    8.784000] ehci_hcd 0000:00:1d.7: irq 22, io mem 0xfc504c00
[    8.788000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 
2004
[    8.788000] usb usb7: configuration #1 chosen from 1 choice
[    8.788000] hub 7-0:1.0: USB hub found
[    8.788000] hub 7-0:1.0: 6 ports detected
[    8.892000] ahci 0000:00:1f.2: version 2.2
[    8.892000] ACPI: PCI Interrupt 0000:00:1f.2[b] -> GSI 19 (level, low) -> IRQ
 23
[    9.596000] usb 4-1: new low speed USB device using uhci_hcd and address 2
[    9.776000] usb 4-1: configuration #1 chosen from 1 choice
[    9.788000] usbcore: registered new interface driver hiddev
[    9.800000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input2
[    9.800000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on u
sb-0000:00:1d.1-1
[    9.800000] usbcore: registered new interface driver usbhid
[    9.800000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-c
ore.c: v2.6:USB HID core driver
[    9.896000] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 imp
l SATA mode
[    9.896000] ahci 0000:00:1f.2: flags: 64bit ncq led clo pio slum part 
[    9.896000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    9.896000] scsi0 : ahci
[    9.896000] scsi1 : ahci
[    9.896000] scsi2 : ahci
[    9.896000] ata1: SATA max UDMA/133 cmd 0xf8876100 ctl 0x00000000 bmdma 0x000
00000 irq 23
[    9.896000] ata2: SATA max UDMA/133 cmd 0xf8876180 ctl 0x00000000 bmdma 0x000
00000 irq 23
[    9.896000] ata3: SATA max UDMA/133 cmd 0xf8876200 ctl 0x00000000 bmdma 0x000
00000 irq 23
[   10.380000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   10.812000] ata1.00: ATA-8: TOSHIBA MK1646GSX, LB113J, max UDMA/100
[   10.812000] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   10.816000] ata1.00: configured for UDMA/100
[   11.132000] ata2: SATA link down (SStatus 0 SControl 300)
[   11.444000] ata3: SATA link down (SStatus 0 SControl 300)
[   11.444000] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK1646GS LB11 PQ
: 0 ANSI: 5
[   11.444000] tg3.c:v3.77 (May 31, 2007)
[   11.444000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ
 16
[   11.444000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   11.448000] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   11.448000] sd 0:0:0:0: [sda] Write Protect is off
[   11.448000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   11.448000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, does
n't support DPO or FUA
[   11.448000] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   11.448000] sd 0:0:0:0: [sda] Write Protect is off
[   11.448000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   11.448000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, does
n't support DPO or FUA
[   11.448000]  sda:<6>eth0: Tigon3 [partno(BCM95787m) rev b002 PHY(5787)] (PCI 
Express) 10/100/1000Base-T Ethernet 00:1d:72:19:f2:f6
[   11.464000] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOca
p[1]
[   11.464000] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   11.468000] ACPI: PCI Interrupt 0000:0f:06.1[A] -> GSI 22 (level, low) -> IRQ
 19
[   11.516000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[fc206000
-fc2067ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   11.516000] ata_piix 0000:00:1f.1: version 2.11
[   11.516000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 19 (level, low) -> IRQ
 23
[   11.516000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   11.516000] scsi3 : ata_piix
[   11.516000] scsi4 : ata_piix
[   11.516000] ata4: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x000
11810 irq 14
[   11.516000] ata5: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x000
11818 irq 15
[   11.520000]  sda1 sda2
[   11.520000] sd 0:0:0:0: [sda] Attached SCSI disk
[   11.524000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   11.776000] Attempting manual resume
[   11.776000] swsusp: Resume From Partition 8:1
[   11.776000] PM: Checking swsusp image.
[   11.776000] PM: Resume from disk failed.
[   11.824000] kjournald starting.  Commit interval 5 seconds
[   11.824000] EXT3-fs: mounted filesystem with ordered data mode.
[   12.792000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001d72ffff19f2f6]
[   17.972000] Linux agpgart interface v0.102 (c) Dave Jones
[   18.032000] agpgart: Detected an Intel 965GM Chipset.
[   18.032000] agpgart: Detected 7676K stolen memory.
[   18.068000] agpgart: AGP aperture is 256M @ 0xd0000000
[   18.116000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   18.132000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   18.336000] Yenta: CardBus bridge found at 0000:0f:06.0 [1025:011f]
[   18.336000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   18.336000] Yenta: Routing CardBus interrupts to PCI
[   18.336000] Yenta TI: socket 0000:0f:06.0, mfunc 0x01aa1b22, devctl 0x64
[   18.500000] sdhci: Secure Digital Host Controller Interface driver
[   18.500000] sdhci: Copyright(c) Pierre Ossman
[   18.568000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 19
[   18.568000] Socket status: 30000006
[   18.568000] Yenta: Raising subordinate bus# of parent bus (#0f) from #10 to #
13
[   18.568000] pcmcia: parent PCI bridge I/O window: 0x5000 - 0x5fff
[   18.568000] cs: IO port probe 0x5000-0x5fff: clean.
[   18.568000] pcmcia: parent PCI bridge Memory window: 0xfc200000 - 0xfc2fffff
[   18.568000] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
[   18.568000] sdhci: SDHCI controller found at 0000:0f:06.3 [104c:803c] (rev 0)
[   18.568000] ACPI: PCI Interrupt 0000:0f:06.3[A] -> GSI 22 (level, low) -> IRQ
 19
[   18.568000] mmc0: SDHCI at 0xfc206800 irq 19 PIO
[   18.576000] ACPI: PCI Interrupt 0000:0f:06.2[A] -> GSI 22 (level, low) -> IRQ
 19
[   18.640000] ieee80211_crypt: registered algorithm 'NULL'
[   18.644000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   18.644000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@li
nux.intel.com>
[   18.708000] irda_init()
[   18.708000] NET: Registered protocol family 23
[   18.772000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for
 Linux, 1.2.2mp.ubuntu1
[   18.772000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   18.772000] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 17 (level, low) -> IRQ
 17
[   18.772000] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   18.776000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   18.968000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ
 21
[   18.968000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   19.028000] cs: IO port probe 0x100-0x3af: clean.
[   19.028000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   19.032000] cs: IO port probe 0x820-0x8ff: clean.
[   19.032000] cs: IO port probe 0xc00-0xcf7: clean.
[   19.032000] cs: IO port probe 0xa00-0xaff: clean.
[   19.388000] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x12a0b1, caps: 0xa047
13/0x204000
[   19.440000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   19.568000] pnp: Device 00:0a activated.
[   19.568000] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dm
a 3.
[   19.568000] nsc-ircc, chip->init
[   19.568000] nsc-ircc, Found chip at base=0x02e
[   19.568000] nsc-ircc, driver loaded (Dag Brattli)
[   19.568000] IrDA: Registered device irda0
[   19.568000] nsc-ircc, Found dongle: Supports SIR Mode only
[   19.568000] nsc-ircc, chip->init
[   19.568000] nsc-ircc, Found chip at base=0x02e
[   19.568000] nsc-ircc, driver loaded (Dag Brattli)
[   19.568000] nsc_ircc_open(), can't get iobase of 0x2f8
[   20.004000] lp: driver loaded but no devices found
[   20.068000] Adding 1172704k swap on /dev/sda1.  Priority:-1 extents:1 across:
1172704k
[   20.388000] EXT3 FS on sda2, internal journal
[   20.672000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a
 channels)
[   21.628000] No dock devices found.
[   21.984000] ACPI: Battery Slot [BAT0] (battery present)
[   22.012000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   22.064000] input: Power Button (FF) as /class/input/input4
[   22.064000] ACPI: Power Button (FF) [PWRF]
[   22.064000] input: Lid Switch as /class/input/input5
[   22.064000] ACPI: Lid Switch [LID0]
[   22.064000] input: Sleep Button (CM) as /class/input/input6
[   22.064000] ACPI: Sleep Button (CM) [SLPB]
[   22.132000] ACPI: AC Adapter [ADP1] (off-line)
[   23.400000] ppdev: user-space parallel port driver
[   23.572000] audit(1204984413.403:3):  type=1503 operation="inode_permission" 
requested_mask="a" denied_mask="a" name="/dev/tty" pid=5076 profile="/usr/sbin/c
upsd"
[   23.624000] apm: BIOS not found.
[   23.808000] PM: Writing back config space on device 0000:02:00.0 at offset c 
(was 82020000, writing 0)
[   23.952000] Failure registering capabilities with primary security module.
[   24.188000] Bluetooth: Core ver 2.11
[   24.188000] NET: Registered protocol family 31
[   24.188000] Bluetooth: HCI device and connection manager initialized
[   24.188000] Bluetooth: HCI socket layer initialized
[   24.224000] Bluetooth: L2CAP ver 2.8
[   24.224000] Bluetooth: L2CAP socket layer initialized
[   24.288000] Bluetooth: RFCOMM socket layer initialized
[   24.288000] Bluetooth: RFCOMM TTY layer initialized
[   24.288000] Bluetooth: RFCOMM ver 1.8
[   29.436000] [drm] Initialized drm 1.1.0 20060810
[   29.492000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ
 16
[   29.492000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[ 1049.776000] NET: Registered protocol family 10
[ 1049.776000] lo: Disabled Privacy Extensions
[ 1049.776000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1049.776000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 1086.004000] NET: Registered protocol family 17
[ 1089.124000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 1105.888000] eth1: no IPv6 routers present
[ 2295.224000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 2296.820000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 2307.004000] eth1: no IPv6 routers present
[ 2307.200000] ipw3945: association process canceled
[ 2318.176000] ipw3945: association process canceled
[ 2320.784000] ipw3945: association process canceled
[ 2336.640000] ipw3945: association process canceled
[ 2344.556000] ipw3945: association process canceled
[ 2347.228000] ipw3945: association process canceled
[ 2347.228000] ipw3945: association process canceled
[ 2398.444000] ipw3945: association process canceled
[ 2401.080000] ipw3945: association process canceled
[ 2411.448000] ipw3945: association process canceled
[ 2411.448000] ipw3945: association process canceled
[ 2420.016000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 2422.612000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 2430.480000] ipw3945: association process canceled
[ 2433.592000] eth1: no IPv6 routers present
[ 2435.704000] ipw3945: association process canceled
[ 2443.504000] ipw3945: association process canceled
[ 2466.964000] ipw3945: association process canceled
[ 2534.952000] ipw3945: association process canceled
[ 2560.688000] eth1: no IPv6 routers present
[ 3256.028000] ata1.00: exception Emask 0x2 SAct 0x387 SErr 0x0 action 0x2 froze
n
[ 3256.028000] ata1.00: (spurious completions during NCQ issue=0x0 SAct=0x387 FI
S=004040a1:00000040)
[ 3256.028000] ata1.00: cmd 61/08:00:1a:cb:df/00:00:04:00:00/40 tag 0 cdb 0x0 da
ta 4096 out
[ 3256.028000]          res 40/00:10:3a:0a:2f/00:00:10:00:00/40 Emask 0x2 (HSM v
iolation)
[ 3256.028000] ata1.00: cmd 61/08:08:8a:5f:2e/00:00:10:00:00/40 tag 1 cdb 0x0 da
ta 4096 out
[ 3256.028000]          res 40/00:10:3a:0a:2f/00:00:10:00:00/40 Emask 0x2 (HSM v
iolation)
[ 3256.028000] ata1.00: cmd 61/08:10:3a:0a:2f/00:00:10:00:00/40 tag 2 cdb 0x0 da
ta 4096 out
[ 3256.028000]          res 40/00:10:3a:0a:2f/00:00:10:00:00/40 Emask 0x2 (HSM v
iolation)
[ 3256.028000] ata1.00: cmd 61/08:38:f2:ca:df/00:00:04:00:00/40 tag 7 cdb 0x0 da
ta 4096 out
[ 3256.028000]          res 40/00:10:3a:0a:2f/00:00:10:00:00/40 Emask 0x2 (HSM v
iolation)
[ 3256.028000] ata1.00: cmd 61/38:40:2a:cb:df/00:00:04:00:00/40 tag 8 cdb 0x0 da
ta 28672 out
[ 3256.028000]          res 40/00:10:3a:0a:2f/00:00:10:00:00/40 Emask 0x2 (HSM v
iolation)
[ 3256.028000] ata1.00: cmd 61/10:48:1a:cb:f7/00:00:07:00:00/40 tag 9 cdb 0x0 da
ta 8192 out
[ 3256.028000]          res 40/00:10:3a:0a:2f/00:00:10:00:00/40 Emask 0x2 (HSM v
iolation)
[ 3256.340000] ata1: soft resetting port
[ 3256.512000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 3256.512000] ata1.00: configured for UDMA/100
[ 3256.512000] ata1: EH complete
[ 3256.512000] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[ 3256.512000] sd 0:0:0:0: [sda] Write Protect is off
[ 3256.512000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 3256.512000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, does
n't support DPO or FUA
[ 3298.948000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 3309.772000] eth1: no IPv6 routers present
[ 3427.532000] eth1: no IPv6 routers present
[ 3512.920000] eth1: no IPv6 routers present
[ 3558.680000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 3560.792000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 3571.736000] eth1: no IPv6 routers present
[ 3575.576000] ieee80211_crypt: registered algorithm 'TKIP'
[ 3591.140000] eth1: no IPv6 routers present
[ 3967.004000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 4103.776000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 4109.716000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 4120.544000] eth1: no IPv6 routers present
[ 4146.052000] eth1: no IPv6 routers present
[ 4412.224000] atkbd.c: Unknown key pressed (translated set 2, code 0xb4 on isa0
060/serio0).
[ 4412.224000] atkbd.c: Use 'setkeycodes e034 <keycode>' to make it known.
[ 4412.252000] atkbd.c: Unknown key released (translated set 2, code 0xb4 on isa
0060/serio0).
[ 4412.252000] atkbd.c: Use 'setkeycodes e034 <keycode>' to make it known.
[ 7933.516000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 7935.476000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 7946.284000] eth1: no IPv6 routers present
[ 7958.292000] eth1: no IPv6 routers present
[ 7972.656000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 8107.860000] ipw3945: association process canceled
[ 8117.740000] eth1: no IPv6 routers present
[ 8277.224000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a
 channels)
[ 8343.620000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 8361.440000] eth1: no IPv6 routers present
[ 8399.176000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 8533.316000] ipw3945: association process canceled
[ 8593.160000] eth1: no IPv6 routers present
[ 8595.792000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a
 channels)
[ 8631.772000] ipw3945: association process canceled
[ 8671.164000] ata1.00: exception Emask 0x2 SAct 0x100 SErr 0x0 action 0x2 froze
n
[ 8671.164000] ata1.00: (spurious completions during NCQ issue=0x0 SAct=0x100 FI
S=004040a1:00000001)
[ 8671.164000] ata1.00: cmd 61/08:40:12:8a:2f/00:00:10:00:00/40 tag 8 cdb 0x0 da
ta 4096 out
[ 8671.164000]          res 40/00:40:12:8a:2f/00:00:10:00:00/40 Emask 0x2 (HSM v
iolation)
[ 8671.476000] ata1: soft resetting port
[ 8671.648000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 8671.648000] ata1.00: configured for UDMA/100
[ 8671.648000] ata1: EH complete
[ 8671.648000] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[ 8671.648000] sd 0:0:0:0: [sda] Write Protect is off
[ 8671.648000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 8671.648000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, does
n't support DPO or FUA
[ 9363.120000] ipw3945: association process canceled
[ 9402.224000] ipw3945: association process canceled
[ 9719.444000] ipw3945: association process canceled
[ 9767.616000] ipw3945: association process canceled
[ 9892.108000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a
 channels)
[10090.048000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[10109.096000] eth1: no IPv6 routers present
[10575.432000] usb 7-5: new high speed USB device using ehci_hcd and address 3
[10575.564000] usb 7-5: configuration #1 chosen from 1 choice
[10575.960000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.
c: usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x03F0 pid 0x5
711
[10575.960000] usbcore: registered new interface driver usblp
[10575.960000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.
c: v0.13: USB Printer Device Class driver
[10576.000000] usbcore: registered new interface driver libusual
[10576.088000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[10576.088000] ide: Assuming 33MHz system bus speed for PIO modes; override with
 idebus=xx
[10576.148000] Initializing USB Mass Storage driver...
[10576.148000] scsi5 : SCSI emulation for USB Mass Storage devices
[10576.164000] usb-storage: device found at 3
[10576.164000] usb-storage: waiting for device to settle before scanning
[10576.164000] usbcore: registered new interface driver usb-storage
[10576.164000] USB Mass Storage support registered.
[10581.164000] usb-storage: device scan complete
[10581.164000] scsi 5:0:0:0: Direct-Access     HP       Photosmart C4180 1.00 PQ
: 0 ANSI: 2
[10581.164000] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[10581.164000] sd 5:0:0:0: Attached scsi generic sg1 type 0
[11225.472000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.
c: usblp0: removed
[11225.560000] audit(1204995618.993:4):  type=1503 operation="inode_permission" 
requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=8565 profile="/usr/sbin
/cupsd"
[11225.596000] audit(1204995618.993:5):  type=1503 operation="inode_permission" 
requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=8569 profile="/usr/sbin
/cupsd"
[12376.536000] ata1.00: exception Emask 0x2 SAct 0x7ffe1 SErr 0x0 action 0x2 fro
zen
[12376.536000] ata1.00: (spurious completions during NCQ issue=0x0 SAct=0x7ffe1 
FIS=004040a1:00000010)
[12376.536000] ata1.00: cmd 61/08:00:22:ca:f3/00:00:01:00:00/40 tag 0 cdb 0x0 da
ta 4096 out
[12376.536000]          res 40/00:90:a2:0e:d2/00:00:0b:00:00/40 Emask 0x2 (HSM v
iolation)
[12376.536000] ata1.00: cmd 61/08:28:92:cb:bf/00:00:01:00:00/40 tag 5 cdb 0x0 da
ta 4096 out
[12376.536000]          res 40/00:90:a2:0e:d2/00:00:0b:00:00/40 Emask 0x2 (HSM v
iolation)
[12376.536000] ata1.00: cmd 61/10:30:a2:cb:bf/00:00:01:00:00/40 tag 6 cdb 0x0 da
ta 8192 out
[12376.536000]          res 40/00:90:a2:0e:d2/00:00:0b:00:00/40 Emask 0x2 (HSM v
iolation)
[12376.536000] ata1.00: cmd 61/08:38:2a:cd:bf/00:00:01:00:00/40 tag 7 cdb 0x0 da
ta 4096 out
[12376.536000]          res 40/00:90:a2:0e:d2/00:00:0b:00:00/40 Emask 0x2 (HSM v
iolation)
[12376.536000] ata1.00: cmd 61/08:40:42:ce:bf/00:00:01:00:00/40 tag 8 cdb 0x0 da
ta 4096 out
[12376.536000]          res 40/00:90:a2:0e:d2/00:00:0b:00:00/40 Emask 0x2 (HSM v
iolation)
[12376.536000] ata1.00: cmd 61/18:48:72:ca:df/00:00:04:00:00/40 tag 9 cdb 0x0 da
ta 12288 out
[12376.536000]          res 40/00:90:a2:0e:d2/00:00:0b:00:00/40 Emask 0x2 (HSM v
iolation)
[12376.536000] ata1.00: cmd 61/08:50:ba:ca:df/00:00:04:00:00/40 tag 10 cdb 0x0 d
ata 4096 out
[12376.536000]          res 40/00:90:a2:0e:d2/00:00:0b:00:00/40 Emask 0x2 (HSM v
iolation)
[12376.536000] ata1.00: cmd 61/08:58:12:cb:df/00:00:04:00:00/40 tag 11 cdb 0x0 d
ata 4096 out
[12376.536000]          res 40/00:90:a2:0e:d2/00:00:0b:00:00/40 Emask 0x2 (HSM v
iolation)
[12376.536000] ata1.00: cmd 61/08:60:22:cb:df/00:00:04:00:00/40 tag 12 cdb 0x0 d
ata 4096 out
[12376.536000]          res 40/00:90:a2:0e:d2/00:00:0b:00:00/40 Emask 0x2 (HSM v
iolation)
[12376.536000] ata1.00: cmd 61/08:68:62:ca:c7/00:00:07:00:00/40 tag 13 cdb 0x0 d
ata 4096 out
[12376.536000]          res 40/00:90:a2:0e:d2/00:00:0b:00:00/40 Emask 0x2 (HSM v
iolation)
[12376.536000] ata1.00: cmd 61/08:70:a2:ca:f7/00:00:07:00:00/40 tag 14 cdb 0x0 d
ata 4096 out
[12376.536000]          res 40/00:90:a2:0e:d2/00:00:0b:00:00/40 Emask 0x2 (HSM v
iolation)
[12376.536000] ata1.00: cmd 61/08:78:ba:ca:f7/00:00:07:00:00/40 tag 15 cdb 0x0 d
ata 4096 out
[12376.536000]          res 40/00:90:a2:0e:d2/00:00:0b:00:00/40 Emask 0x2 (HSM v
iolation)
[12376.536000] ata1.00: cmd 61/10:80:12:ca:cf/00:00:0b:00:00/40 tag 16 cdb 0x0 d
ata 8192 out
[12376.536000]          res 40/00:90:a2:0e:d2/00:00:0b:00:00/40 Emask 0x2 (HSM v
iolation)
[12376.536000] ata1.00: cmd 61/10:88:42:ca:cf/00:00:0b:00:00/40 tag 17 cdb 0x0 d
ata 8192 out
[12376.536000]          res 40/00:90:a2:0e:d2/00:00:0b:00:00/40 Emask 0x2 (HSM v
iolation)
[12376.536000] ata1.00: cmd 61/08:90:a2:0e:d2/00:00:0b:00:00/40 tag 18 cdb 0x0 d
ata 4096 out
[12376.536000]          res 40/00:90:a2:0e:d2/00:00:0b:00:00/40 Emask 0x2 (HSM v
iolation)
[12376.852000] ata1: soft resetting port
[12377.024000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[12377.024000] ata1.00: configured for UDMA/100
[12377.024000] ata1: EH complete
[12377.024000] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[12377.024000] sd 0:0:0:0: [sda] Write Protect is off
[12377.024000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[12377.024000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, does
n't support DPO or FUA
[12457.244000] usb 7-5: USB disconnect, address 3
[12471.440000] usb 7-5: new high speed USB device using ehci_hcd and address 4
[12471.612000] usb 7-5: configuration #1 chosen from 1 choice
[12471.612000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.
c: usblp0: USB Bidirectional printer dev 4 if 1 alt 0 proto 2 vid 0x03F0 pid 0x5
711
[12471.612000] scsi6 : SCSI emulation for USB Mass Storage devices
[12471.612000] usb-storage: device found at 4
[12471.612000] usb-storage: waiting for device to settle before scanning
[12476.612000] usb-storage: device scan complete
[12476.612000] scsi 6:0:0:0: Direct-Access     HP       Photosmart C4180 1.00 PQ
: 0 ANSI: 2
[12476.612000] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[12476.612000] sd 6:0:0:0: Attached scsi generic sg1 type 0
[12561.708000] usb 7-5: USB disconnect, address 4
[12561.712000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.
c: usblp0: removed


```

Im desperate to get this to work..  if anybody knows what to do, please help :)

---

