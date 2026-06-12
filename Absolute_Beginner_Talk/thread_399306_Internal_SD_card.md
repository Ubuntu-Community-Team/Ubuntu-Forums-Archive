---
title: "Internal SD card"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by ushills on 2007-04-02
I have a Genesys internal multicard reader (connected to USB headers) in my computer running Ubuntu 6.10.

The card is seen and mounts Sony Memorysticks and Smartmedia cards correctly and automatically; however, the reader will not read MMC or SD cards.

Is there something missing from my installation that I need to activate SD & MMC cards.

What more information is required to diagnose my problems.

---

### Post by teaker1s on 2007-04-02
okay this is a suggestion, I'm not sure if it will work but it may give you something to work with-but it's worth a go and your card reader will be called something different
[https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29?highlight=%28dv6000%29%7C%28hp%29#head-0b198b90ec3b7cc470b197a54622354457513e6c]("https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29?highlight=%28dv6000%29%7C%28hp%29#head-0b198b90ec3b7cc470b197a54622354457513e6c")
if you have 
pci connected
```
lspci
```
usb 
```
lsusb
```

---

### Post by ushills on 2007-04-04
Hi

The internal card reader I have is not a PCI type, it connected to the internal USB headers on my motherboard.

I have posted the contents of dmesg below, I think the device is the sdd one at the end but I cannot mount it.

I have posted the full contents in case I am missing anything.

[INDENT][I][17179569.184000] Linux version 2.6.17-11-generic (root@terranova) (gcc 
version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Thu 
Feb 1 19:52:28 UTC 2007 (Ubuntu 2.6.17-11.35-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e8000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000003ffb0000 (usable)
[17179569.184000]  BIOS-e820: 000000003ffb0000 - 000000003ffc0000 (ACPI 
data)
[17179569.184000]  BIOS-e820: 000000003ffc0000 - 000000003fff0000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000003fff0000 - 0000000040000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffba0000 - 0000000100000000 (reserved)
[17179569.184000] 127MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000ff780
[17179569.184000] On node 0 totalpages: 262064
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 32688 pages, LIFO batch:7
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 ACPIAM                                
) @ 0x000fad90
[17179569.184000] ACPI: RSDT (v001 A M I  OEMRSDT  0x09000425 MSFT 
0x00000097) @ 0x3ffb0000
[17179569.184000] ACPI: FADT (v002 A M I  OEMFACP  0x09000425 MSFT 
0x00000097) @ 0x3ffb0200
[17179569.184000] ACPI: MADT (v001 A M I  OEMAPIC  0x09000425 MSFT 
0x00000097) @ 0x3ffb0390
[17179569.184000] ACPI: OEMB (v001 A M I  OEMBIOS  0x09000425 MSFT 
0x00000097) @ 0x3ffc0040
[17179569.184000] ACPI: DSDT (v001  AH002 AH002001 0x00000001 INTL 
0x02002026) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x808
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:2 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, 
GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high 
level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 50000000 (gap: 
40000000:bfba0000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/sda1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[17179569.184000] Detected 2406.798 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.488000] Dentry cache hash table entries: 131072 (order: 7, 
524288 bytes)
[17179569.488000] Inode-cache hash table entries: 65536 (order: 6, 
262144 bytes)
[17179569.520000] Memory: 1029376k/1048256k available (1911k kernel 
code, 18108k reserved, 1073k data, 308k init, 130752k highmem)
[17179569.520000] Checking if this processor honours the WP bit even in 
supervisor mode... Ok.
[17179569.600000] Calibrating delay using timer specific routine.. 
4818.54 BogoMIPS (lpj=9637099)
[17179569.600000] Security Framework v1.0.0 initialized
[17179569.600000] SELinux:  Disabled at boot.
[17179569.600000] Mount-cache hash table entries: 512
[17179569.600000] CPU: After generic identify, caps: bfebfbff 00000000 
00000000 00000000 00004400 00000000 00000000
[17179569.600000] CPU: After vendor identify, caps: bfebfbff 00000000 
00000000 00000000 00004400 00000000 00000000
[17179569.600000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[17179569.600000] CPU: L2 cache: 128K
[17179569.600000] CPU: Hyper-Threading is disabled
[17179569.600000] CPU: After all inits, caps: bfebfbff 00000000 00000000 
00000080 00004400 00000000 00000000
[17179569.600000] Checking 'hlt' instruction... OK.
[17179569.616000] SMP alternatives: switching to UP code
[17179569.616000] Freeing SMP alternatives: 16k freed
[17179569.616000] checking if image is initramfs... it is
[17179570.148000] Freeing initrd memory: 5326k freed
[17179570.148000] ACPI: Core revision 20060707
[17179570.148000] ACPI: Looking for DSDT ... not found!
[17179570.148000] CPU0: Intel(R) Celeron(R) CPU 2.40GHz stepping 07
[17179570.148000] Total of 1 processors activated (4818.54 BogoMIPS).
[17179570.148000] ENABLING IO-APIC IRQs
[17179570.148000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179570.292000] Brought up 1 CPUs
[17179570.292000] migration_cost=0
[17179570.292000] NET: Registered protocol family 16
[17179570.292000] EISA bus registered
[17179570.292000] ACPI: bus type pci registered
[17179570.292000] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=2
[17179570.292000] PCI: Using configuration type 1
[17179570.292000] Setting up standard PCI resources
[17179570.304000] ACPI: Interpreter enabled
[17179570.304000] ACPI: Using IOAPIC for interrupt routing
[17179570.304000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.304000] PCI: Probing PCI hardware (bus 00)
[17179570.308000] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[17179570.308000] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
[17179570.308000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179570.308000] Boot video device is 0000:01:00.0
[17179570.312000] PCI: Transparent bridge - 0000:00:1e.0
[17179570.312000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.320000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[17179570.332000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 
12 14 15)
[17179570.332000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 
12 14 15)
[17179570.332000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 
12 14 15)
[17179570.332000] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 10 11 
12 14 15)
[17179570.332000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 
12 14 15) *0, disabled.
[17179570.332000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 10 11 
12 14 15)
[17179570.332000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *10 11 
12 14 15)
[17179570.336000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 11 
12 14 15)
[17179570.336000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.336000] pnp: PnP ACPI init
[17179570.340000] pnp: PnP ACPI: found 12 devices
[17179570.340000] PnPBIOS: Disabled by ACPI PNP
[17179570.340000] PCI: Using ACPI for IRQ routing
[17179570.340000] PCI: If a device doesn't work, try "pci=routeirq".  If 
it helps, post a report
[17179570.348000] pnp: 00:06: ioport range 0x680-0x6ff has been reserved
[17179570.348000] pnp: 00:06: ioport range 0x290-0x297 has been reserved
[17179570.348000] PCI: Bridge: 0000:00:01.0
[17179570.348000]   IO window: c000-cfff
[17179570.348000]   MEM window: ff800000-ff8fffff
[17179570.348000]   PREFETCH window: e7f00000-f7efffff
[17179570.348000] PCI: Bridge: 0000:00:1e.0
[17179570.348000]   IO window: d000-dfff
[17179570.348000]   MEM window: ff900000-ff9fffff
[17179570.348000]   PREFETCH window: disabled.
[17179570.348000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179570.348000] NET: Registered protocol family 2
[17179570.388000] IP route cache hash table entries: 32768 (order: 5, 
131072 bytes)
[17179570.388000] TCP established hash table entries: 131072 (order: 8, 
1048576 bytes)
[17179570.388000] TCP bind hash table entries: 65536 (order: 7, 524288 
bytes)
[17179570.388000] TCP: Hash tables configured (established 131072 bind 
65536)
[17179570.388000] TCP reno registered
[17179570.392000] audit: initializing netlink socket (disabled)
[17179570.392000] audit(1175667384.392:1): initialized
[17179570.392000] highmem bounce pool size: 64 pages
[17179570.392000] VFS: Disk quotas dquot_6.5.1
[17179570.392000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.392000] Initializing Cryptographic API
[17179570.392000] io scheduler noop registered
[17179570.392000] io scheduler anticipatory registered
[17179570.392000] io scheduler deadline registered
[17179570.392000] io scheduler cfq registered (default)
[17179578.420000] 0000:00:1d.7 EHCI: BIOS handoff failed (BIOS bug ?) 
01010001
[17179578.424000] isapnp: Scanning for PnP cards...
[17179578.776000] isapnp: No Plug & Play device found
[17179578.880000] Real Time Clock Driver v1.12ac
[17179578.880000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, 
IRQ sharing enabled
[17179578.880000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179578.880000] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179578.884000] mice: PS/2 mouse device common for all mice
[17179578.884000] RAMDISK driver initialized: 16 RAM disks of 65536K 
size 1024 blocksize
[17179578.884000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179578.884000] ide: Assuming 33MHz system bus speed for PIO modes; 
override with idebus=xx
[17179578.884000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[17179578.884000] PNP: PS/2 controller doesn't have AUX irq; using 
default 12
[17179578.888000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179578.888000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179578.888000] EISA: Probing bus 0 at eisa.0
[17179578.888000] EISA: Detected 0 cards.
[17179578.888000] TCP bic registered
[17179578.888000] NET: Registered protocol family 1
[17179578.888000] NET: Registered protocol family 8
[17179578.888000] NET: Registered protocol family 20
[17179578.888000] Using IPI No-Shortcut mode
[17179578.888000] ACPI: (supports S0 S1 S3 S4 S5)
[17179578.888000] Freeing unused kernel memory: 308k freed
[17179579.076000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179580.076000] Capability LSM initialized
[17179580.144000] ACPI Exception (acpi_processor-0693): AE_NOT_FOUND, 
Processor Device is not present [20060707]
[17179580.144000] ACPI: Getting cpuindex for acpiid 0x2
[17179581.036000] ICH5: IDE controller at PCI slot 0000:00:1f.1
[17179581.036000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[17179581.036000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, 
low) -> IRQ 169
[17179581.036000] ICH5: chipset revision 2
[17179581.036000] ICH5: not 100% native mode: will probe irqs later
[17179581.036000]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: 
hda:DMA, hdb:pio
[17179581.036000]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: 
hdc:DMA, hdd:pio
[17179581.036000] Probing IDE interface ide0...
[17179581.772000] hda: HL-DT-ST DVDRAM GSA-4160B, ATAPI CD/DVD-ROM drive
[17179582.108000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179582.112000] Probing IDE interface ide1...
[17179582.404000] hdc: Maxtor 4R080L0, ATA DISK drive
[17179583.076000] ide1 at 0x170-0x177,0x376 on irq 15
[17179583.116000] hda: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB 
Cache, UDMA(66)
[17179583.116000] Uniform CD-ROM driver Revision: 3.20
[17179583.144000] hdc: max request size: 128KiB
[17179583.144000] hdc: 160086528 sectors (81964 MB) w/2048KiB Cache, 
CHS=65535/16/63, UDMA(100)
[17179583.144000] hdc: cache flushes supported
[17179583.144000]  hdc: hdc1
[17179583.316000] SCSI subsystem initialized
[17179583.320000] libata version 1.20 loaded.
[17179583.320000] ata_piix 0000:00:1f.2: version 1.05
[17179583.320000] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 18 (level, 
low) -> IRQ 169
[17179583.320000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179583.320000] ata1: SATA max UDMA/133 cmd 0xEFF0 ctl 0xEFE6 bmdma 
0xEF60 irq 169
[17179583.320000] ata2: SATA max UDMA/133 cmd 0xEFA8 ctl 0xEFE2 bmdma 
0xEF68 irq 169
[17179583.484000] ata1: dev 0 cfg 49:2f00 82:346b 83:7fe9 84:4773 
85:3469 86:bc01 87:4763 88:207f
[17179583.484000] ata1: dev 0 ATA-7, max UDMA/133, 488397168 sectors: LBA48
[17179583.496000] ata1: dev 0 configured for UDMA/133
[17179583.496000] scsi0 : ata_piix
[17179583.668000] scsi1 : ata_piix
[17179583.668000]   Vendor: ATA       Model: Hitachi HDT72502  Rev: V5DO
[17179583.668000]   Type:   Direct-Access                      ANSI SCSI 
revision: 05
[17179583.684000] SCSI device sda: 488397168 512-byte hdwr sectors 
(250059 MB)
[17179583.684000] sda: Write Protect is off
[17179583.684000] sda: Mode Sense: 00 3a 00 00
[17179583.684000] SCSI device sda: drive cache: write back
[17179583.684000] SCSI device sda: 488397168 512-byte hdwr sectors 
(250059 MB)
[17179583.684000] sda: Write Protect is off
[17179583.684000] sda: Mode Sense: 00 3a 00 00
[17179583.684000] SCSI device sda: drive cache: write back
[17179583.684000]  sda: sda1 sda2 < sda5 >
[17179583.724000] sd 0:0:0:0: Attached scsi disk sda
[17179583.908000] usbcore: registered new driver usbfs
[17179583.908000] usbcore: registered new driver hub
[17179583.908000] USB Universal Host Controller Interface driver v3.0
[17179583.908000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, 
low) -> IRQ 177
[17179583.908000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179583.908000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179583.908000] uhci_hcd 0000:00:1d.0: new USB bus registered, 
assigned bus number 1
[17179583.908000] uhci_hcd 0000:00:1d.0: irq 177, io base 0x0000ef00
[17179583.908000] usb usb1: configuration #1 chosen from 1 choice
[17179583.908000] hub 1-0:1.0: USB hub found
[17179583.908000] hub 1-0:1.0: 2 ports detected
[17179583.992000] ieee1394: Initialized config rom entry `ip1394'
[17179584.012000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, 
low) -> IRQ 185
[17179584.016000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179584.016000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179584.016000] uhci_hcd 0000:00:1d.1: new USB bus registered, 
assigned bus number 2
[17179584.016000] uhci_hcd 0000:00:1d.1: irq 185, io base 0x0000ef20
[17179584.016000] usb usb2: configuration #1 chosen from 1 choice
[17179584.016000] hub 2-0:1.0: USB hub found
[17179584.016000] hub 2-0:1.0: 2 ports detected
[17179584.120000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, 
low) -> IRQ 169
[17179584.120000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179584.120000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179584.124000] uhci_hcd 0000:00:1d.2: new USB bus registered, 
assigned bus number 3
[17179584.124000] uhci_hcd 0000:00:1d.2: irq 169, io base 0x0000ef40
[17179584.124000] usb usb3: configuration #1 chosen from 1 choice
[17179584.124000] hub 3-0:1.0: USB hub found
[17179584.124000] hub 3-0:1.0: 2 ports detected
[17179584.228000] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, 
low) -> IRQ 177
[17179584.228000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17179584.228000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[17179584.232000] uhci_hcd 0000:00:1d.3: new USB bus registered, 
assigned bus number 4
[17179584.232000] uhci_hcd 0000:00:1d.3: irq 177, io base 0x0000ef80
[17179584.232000] usb usb4: configuration #1 chosen from 1 choice
[17179584.232000] hub 4-0:1.0: USB hub found
[17179584.232000] hub 4-0:1.0: 2 ports detected
[17179584.252000] usb 1-1: new low speed USB device using uhci_hcd and 
address 2
[17179584.388000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, 
low) -> IRQ 193
[17179584.388000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179584.388000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179584.388000] ehci_hcd 0000:00:1d.7: new USB bus registered, 
assigned bus number 5
[17179584.388000] ehci_hcd 0000:00:1d.7: debug port 1
[17179584.388000] PCI: cache line size of 128 is not supported by device 
0000:00:1d.7
[17179584.388000] ehci_hcd 0000:00:1d.7: irq 193, io mem 0xffaffc00
[17179584.392000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, 
driver 10 Dec 2004
[17179584.392000] usb usb5: configuration #1 chosen from 1 choice
[17179584.392000] hub 5-0:1.0: USB hub found
[17179584.392000] hub 5-0:1.0: 8 ports detected
[17179584.400000] usb 1-1: device descriptor read/all, error -71
[17179584.500000] ACPI: PCI Interrupt 0000:02:0a.0[A] -> GSI 22 (level, 
low) -> IRQ 201
[17179584.552000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[201]  
MMIO=[ff9fe000-ff9fe7ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[17179584.636000] Attempting manual resume
[17179584.672000] kjournald starting.  Commit interval 5 seconds
[17179584.672000] EXT3-fs: mounted filesystem with ordered data mode.
[17179585.036000] usb 5-6: new high speed USB device using ehci_hcd and 
address 3
[17179585.180000] usb 5-6: configuration #1 chosen from 1 choice
[17179585.424000] usb 1-1: new low speed USB device using uhci_hcd and 
address 4
[17179585.616000] usb 1-1: configuration #1 chosen from 1 choice
[17179585.832000] ieee1394: Host added: ID:BUS[0-00:1023]  
GUID[00004c010000001e]
[17179594.400000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179594.400000] shpchp: Standard Hot Plug PCI Controller Driver 
version: 0.4
[17179594.436000] Linux agpgart interface v0.101 (c) Dave Jones
[17179594.492000] agpgart: Detected an Intel 865 Chipset.
[17179594.496000] agpgart: AGP aperture is 64M @ 0xf8000000
[17179594.596000] hw_random: RNG not detected
[17179594.624000] input: PC Speaker as /class/input/input1
[17179595.064000] parport: PnPBIOS parport detected.
[17179595.064000] parport0: PC-style at 0x378, irq 7 [PCSPP]
[17179595.288000] ACPI: PCI Interrupt 0000:02:09.0[A] -> GSI 21 (level, 
low) -> IRQ 209
[17179595.288000] RT61: Vendor = 0x1814, Product = 0x0301
[17179595.404000] usbcore: registered new driver hiddev
[17179595.436000] input: Microsoft Microsoft 3-Button Mouse with 
IntelliEye(TM) as /class/input/input2
[17179595.436000] input: USB HID v1.10 Mouse [Microsoft Microsoft 
3-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.0-1
[17179595.436000] usbcore: registered new driver usbhid
[17179595.436000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179595.460000] usbcore: registered new driver libusual
[17179595.688000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179595.692000] Initializing USB Mass Storage driver...
[17179595.700000] ra0 (WE) : Driver using old /proc/net/wireless 
support, please fix driver !
[17179595.736000] scsi2 : SCSI emulation for USB Mass Storage devices
[17179595.736000] usbcore: registered new driver usb-storage
[17179595.736000] USB Mass Storage support registered.
[17179595.736000] 8139too Fast Ethernet driver 0.9.27
[17179595.736000] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 22 (level, 
low) -> IRQ 201
[17179595.736000] eth0: RealTek RTL8139 at 0xf89f4c00, 
00:11:2f:ca:be:88, IRQ 201
[17179595.736000] eth0:  Identified 8139 chip type 'RTL-8101'
[17179595.744000] usb-storage: device found at 3
[17179595.744000] usb-storage: waiting for device to settle before scanning
[17179595.744000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179595.816000] ts: Compaq touchscreen protocol output
[17179595.916000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, 
low) -> IRQ 217
[17179595.916000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[17179596.120000] RT61: RfIcType= 3
[17179596.164000] eth0: link down
[17179596.344000] intel8x0_measure_ac97_clock: measured 55966 usecs
[17179596.344000] intel8x0: clocking to 48000
[17179596.532000] lp0: using parport0 (interrupt-driven).
[17179596.556000] ieee1394: sbp2: Driver forced to serialize I/O 
(serialize_io=1)
[17179596.556000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179596.624000] fuse init (API version 7.6)
[17179596.684000] Adding 3028212k swap on 
/dev/disk/by-uuid/4eddbdcb-e94a-49bf-879f-244ba6ba596d.  Priority:-1 
extents:1 across:3028212k
[17179596.752000] EXT3 FS on sda1, internal journal
[17179597.244000] NET: Registered protocol family 17
[17179600.744000] usb-storage: device scan complete
[17179600.748000]   Vendor: Generic   Model: STORAGE DEVICE    Rev: 9601
[17179600.748000]   Type:   Direct-Access                      ANSI SCSI 
revision: 00
[17179600.748000]   Vendor: Generic   Model: STORAGE DEVICE    Rev: 9601
[17179600.748000]   Type:   Direct-Access                      ANSI SCSI 
revision: 00
[17179600.748000]   Vendor: Generic   Model: STORAGE DEVICE    Rev: 9601
[17179600.748000]   Type:   Direct-Access                      ANSI SCSI 
revision: 00
[17179600.748000]   Vendor: Generic   Model: STORAGE DEVICE    Rev: 9601
[17179600.748000]   Type:   Direct-Access                      ANSI SCSI 
revision: 00
[17179600.752000] sd 2:0:0:0: Attached scsi removable disk sdb
[17179600.752000] sd 2:0:0:0: Attached scsi generic sg1 type 0
[17179600.756000] sd 2:0:0:1: Attached scsi removable disk sdc
[17179600.756000] sd 2:0:0:1: Attached scsi generic sg2 type 0
[17179600.760000] sd 2:0:0:2: Attached scsi removable disk sdd
[17179600.760000] sd 2:0:0:2: Attached scsi generic sg3 type 0
[17179600.764000] sd 2:0:0:3: Attached scsi removable disk sde
[17179600.764000] sd 2:0:0:3: Attached scsi generic sg4 type 0
[17179600.828000] 98:28:c7:e8:51:b2:41:de:06:38:4b:3c:3a:fb:4f:d8:
[17179600.828000] e4:c1:4d:06:0e:7e:4a:03:
[17179600.828000] 98:95:64:a1:3b:ec:b7:7f:
[17179600.832000] f5:81:c5:59:82:9b:24:76:61:7e:a7:9f:39:59:23:9f:
[17179600.832000] 4e:a0:49:c5:4e:00:eb:94:
[17179600.832000] 20:87:50:4d:ad:3c:f2:ad:
[17179603.636000] ACPI: Power Button (FF) [PWRF]
[17179603.636000] ACPI: Power Button (CM) [PWRB]
[17179603.800000] ibm_acpi: ec object not found
[17179603.832000] pcc_acpi: loading...
[17179606.528000] [drm] Initialized drm 1.0.1 20051102
[17179606.536000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, 
low) -> IRQ 177
[17179606.536000] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[17179607.212000] agpgart: Found an AGP 3.0 compliant device at 
0000:00:00.0.
[17179607.212000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 4x 
mode
[17179607.212000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 4x 
mode
[17179607.512000] [drm] Setting GART location based on new memory map
[17179607.512000] [drm] Loading R200 Microcode
[17179607.512000] [drm] writeback test succeeded in 1 usecs
[17179607.856000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179607.856000] apm: overridden by ACPI.
[17179613.280000] ip_tables: (C) 2000-2006 Netfilter Core Team
[17179613.364000] Netfilter messages via NETLINK v0.30.
[17179613.376000] ip_conntrack version 2.4 (8189 buckets, 65512 max) - 
224 bytes per conntrack
[17179614.272000] pktcdvd: writer pktcdvd0 mapped to hda
[17179614.600000] Bluetooth: Core ver 2.8
[17179614.600000] NET: Registered protocol family 31
[17179614.600000] Bluetooth: HCI device and connection manager initialized
[17179614.600000] Bluetooth: HCI socket layer initialized
[17179614.652000] Bluetooth: L2CAP ver 2.8
[17179614.652000] Bluetooth: L2CAP socket layer initialized
[17179614.656000] Bluetooth: RFCOMM socket layer initialized
[17179614.656000] Bluetooth: RFCOMM TTY layer initialized
[17179614.656000] Bluetooth: RFCOMM ver 1.7
[17179868.164000] a5:71:34:dd:8d:be:ff:1d:95:06:5f:76:b7:79:30:2f:
[17179868.164000] 1a:81:b0:31:a8:61:12:1f:
[17179868.164000] d0:ae:af:bc:f5:c0:9d:61:
[17179868.172000] f5:81:c5:59:82:9b:24:76:61:7e:a7:9f:39:59:23:9f:
[17179868.172000] 4e:a0:49:c5:4e:00:eb:94:
[17179868.172000] 20:87:50:4d:ad:3c:f2:ad:
[17179871.236000] ab:f5:33:72:13:e7:55:d9:55:16:4d:17:8d:e0:2e:ff:
[17179871.236000] a4:b8:1d:72:28:b4:d5:eb:
[17179871.236000] 39:65:d2:e0:97:54:75:33:
[17179871.244000] f5:81:c5:59:82:9b:24:76:61:7e:a7:9f:39:59:23:9f:
[17179871.244000] 4e:a0:49:c5:4e:00:eb:94:
[17179871.244000] 20:87:50:4d:ad:3c:f2:ad:
[17181095.564000] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 
'LinuxUDF', timestamp 2007/03/30 22:05 (103c)
[17181104.020000] usb 2-2: new full speed USB device using uhci_hcd and 
address 2
[17181104.196000] usb 2-2: configuration #1 chosen from 1 choice
[17181104.200000] scsi3 : SCSI emulation for USB Mass Storage devices
[17181104.200000] usb-storage: device found at 2
[17181104.200000] usb-storage: waiting for device to settle before scanning
[17181109.200000] usb-storage: device scan complete
[17181109.720000]   Vendor: Softick   Model: Card Export       Rev: 0001
[17181109.720000]   Type:   Direct-Access                      ANSI SCSI 
revision: 00
[17181109.768000] SCSI device sdf: 7993344 512-byte hdwr sectors (4093 MB)
[17181109.772000] sdf: Write Protect is off
[17181109.772000] sdf: Mode Sense: 00 00 00 00
[17181109.772000] sdf: assuming drive cache: write through
[17181109.780000] SCSI device sdf: 7993344 512-byte hdwr sectors (4093 MB)
[17181109.784000] sdf: Write Protect is off
[17181109.784000] sdf: Mode Sense: 00 00 00 00
[17181109.784000] sdf: assuming drive cache: write through
[17181109.784000]  sdf: sdf1
[17181109.796000] sd 3:0:0:0: Attached scsi removable disk sdf
[17181109.796000] sd 3:0:0:0: Attached scsi generic sg5 type 0
[17181113.524000] FAT: utf8 is not a recommended IO charset for FAT 
filesystems, filesystem will be case sensitive!
[17182323.008000] SCSI device sdd: 498176 512-byte hdwr sectors (255 MB)
[17182323.012000] sdd: Write Protect is on
[17182323.012000] sdd: Mode Sense: 03 00 80 00
[17182323.012000] sdd: assuming drive cache: write through
[17182323.012000] SCSI device sdd: 498176 512-byte hdwr sectors (255 MB)
[17182323.016000] sdd: Write Protect is on
[17182323.016000] sdd: Mode Sense: 03 00 80 00
[17182323.016000] sdd: assuming drive cache: write through
[17182323.016000]  sdd:[/I][/INDENT]

---

### Post by teaker1s on 2007-04-04
please can you post output of
```
lsusb
```

---

### Post by ushills on 2007-04-04
Output from lsusb
```

Bus 005 Device 003: ID 05e3:070e Genesys Logic, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 001: ID 0000:0000
```

---

### Post by teaker1s on 2007-04-04
05e3:070e appears supported from link below, could it be that it's not auto mounting
[http://www.qbik.ch/usb/devices/search_res.php?pattern=card+reader]("http://www.qbik.ch/usb/devices/search_res.php?pattern=card+reader")

have you tried with and without a memory card in reader
```
sudo fdisk -l
``` to list partitions

---

### Post by ushills on 2007-04-05
Strange behavior here:

I downloaded and ran Fiesty Fawn as a Live CD, FF recognised it straight away (and my wireless card incidently).

However, I re-booted into Edgy to backup my files prior to upgrading to FF and the card was recognised.

Don't know why this happened as I thought the Live CD does'nt affect anything, unless it triggered anything in the hardware or BIOS.

---

### Post by ushills on 2007-05-01
I have now re-installed Feisty Fawn on my machine and the internal SD card reader no longer works.

This is the result of dmesg

```
[ 2892.489950] usb 5-6: USB disconnect, address 3
[ 2892.501300] scsi 4:0:0:0: rejecting I/O to dead device
[ 2892.501321] scsi 4:0:0:0: rejecting I/O to dead device
[ 2892.501329] scsi 4:0:0:0: rejecting I/O to dead device
[ 2892.501335] scsi 4:0:0:0: rejecting I/O to dead device
[ 2892.501341] sdb : READ CAPACITY failed.
[ 2892.501342] sdb : status=0, message=00, host=1, driver=00
[ 2892.501345] sdb : sense not available.
[ 2892.501350] scsi 4:0:0:0: rejecting I/O to dead device
[ 2892.501356] sdb: Write Protect is off
[ 2892.501359] sdb: Mode Sense: 00 00 00 00
[ 2892.501362] sdb: assuming drive cache: write through
[ 2892.501370] scsi 4:0:0:0: rejecting I/O to dead device
[ 2892.501386] scsi 4:0:0:0: rejecting I/O to dead device
[ 2892.501393] scsi 4:0:0:0: rejecting I/O to dead device
[ 2892.501398] scsi 4:0:0:0: rejecting I/O to dead device
[ 2892.501403] scsi 4:0:0:0: rejecting I/O to dead device
[ 2892.501407] sdb : READ CAPACITY failed.
[ 2892.501408] sdb : status=0, message=00, host=1, driver=00
[ 2892.501410] sdb : sense not available.
[ 2892.501415] scsi 4:0:0:0: rejecting I/O to dead device
[ 2892.501419] sdb: Write Protect is off
[ 2892.501422] sdb: Mode Sense: 00 00 00 00
[ 2892.501424] sdb: assuming drive cache: write through
[ 2892.501447] scsi 4:0:0:0: rejecting I/O to dead device
[ 2892.531671] scsi 4:0:0:1: rejecting I/O to dead device
[ 2892.531694] scsi 4:0:0:1: rejecting I/O to dead device
[ 2892.531702] scsi 4:0:0:1: rejecting I/O to dead device
[ 2892.531707] scsi 4:0:0:1: rejecting I/O to dead device
[ 2892.531712] sdc : READ CAPACITY failed.
[ 2892.531714] sdc : status=0, message=00, host=1, driver=00
[ 2892.531716] sdc : sense not available.
[ 2892.531722] scsi 4:0:0:1: rejecting I/O to dead device
[ 2892.531727] sdc: Write Protect is off
[ 2892.531730] sdc: Mode Sense: 00 00 00 00
[ 2892.531733] sdc: assuming drive cache: write through
[ 2892.531739] scsi 4:0:0:1: rejecting I/O to dead device
[ 2892.531754] scsi 4:0:0:1: rejecting I/O to dead device
[ 2892.531760] scsi 4:0:0:1: rejecting I/O to dead device
[ 2892.531766] scsi 4:0:0:1: rejecting I/O to dead device
[ 2892.531771] scsi 4:0:0:1: rejecting I/O to dead device
[ 2892.531775] sdc : READ CAPACITY failed.
[ 2892.531776] sdc : status=0, message=00, host=1, driver=00
[ 2892.531778] sdc : sense not available.
[ 2892.531783] scsi 4:0:0:1: rejecting I/O to dead device
[ 2892.531786] sdc: Write Protect is off
[ 2892.531789] sdc: Mode Sense: 00 00 00 00
[ 2892.531791] sdc: assuming drive cache: write through
[ 2892.531811] scsi 4:0:0:1: rejecting I/O to dead device
[ 2892.533676] scsi 4:0:0:2: rejecting I/O to dead device
[ 2892.533695] scsi 4:0:0:2: rejecting I/O to dead device
[ 2892.533703] scsi 4:0:0:2: rejecting I/O to dead device
[ 2892.533709] scsi 4:0:0:2: rejecting I/O to dead device
[ 2892.533714] sdd : READ CAPACITY failed.
[ 2892.533716] sdd : status=0, message=00, host=1, driver=00
[ 2892.533719] sdd : sense not available.
[ 2892.533724] scsi 4:0:0:2: rejecting I/O to dead device
[ 2892.533729] sdd: Write Protect is off
[ 2892.533732] sdd: Mode Sense: 00 00 00 00
[ 2892.533734] sdd: assuming drive cache: write through
[ 2892.533741] scsi 4:0:0:2: rejecting I/O to dead device
[ 2892.533756] scsi 4:0:0:2: rejecting I/O to dead device
[ 2892.533763] scsi 4:0:0:2: rejecting I/O to dead device
[ 2892.533768] scsi 4:0:0:2: rejecting I/O to dead device
[ 2892.533773] scsi 4:0:0:2: rejecting I/O to dead device
[ 2892.533777] sdd : READ CAPACITY failed.
[ 2892.533778] sdd : status=0, message=00, host=1, driver=00
[ 2892.533780] sdd : sense not available.
[ 2892.533785] scsi 4:0:0:2: rejecting I/O to dead device
[ 2892.533789] sdd: Write Protect is off
[ 2892.533791] sdd: Mode Sense: 00 00 00 00
[ 2892.533794] sdd: assuming drive cache: write through
[ 2892.533813] scsi 4:0:0:2: rejecting I/O to dead device
[ 2892.553323] scsi 4:0:0:3: rejecting I/O to dead device
[ 2892.553343] scsi 4:0:0:3: rejecting I/O to dead device
[ 2892.553350] scsi 4:0:0:3: rejecting I/O to dead device
[ 2892.553356] scsi 4:0:0:3: rejecting I/O to dead device
[ 2892.553361] sde : READ CAPACITY failed.
[ 2892.553363] sde : status=0, message=00, host=1, driver=00
[ 2892.553366] sde : sense not available.
[ 2892.553371] scsi 4:0:0:3: rejecting I/O to dead device
[ 2892.553376] sde: Write Protect is off
[ 2892.553379] sde: Mode Sense: 00 00 00 00
[ 2892.553382] sde: assuming drive cache: write through
[ 2892.553388] scsi 4:0:0:3: rejecting I/O to dead device
[ 2892.553404] scsi 4:0:0:3: rejecting I/O to dead device
[ 2892.553411] scsi 4:0:0:3: rejecting I/O to dead device
[ 2892.553416] scsi 4:0:0:3: rejecting I/O to dead device
[ 2892.553420] scsi 4:0:0:3: rejecting I/O to dead device
[ 2892.553425] sde : READ CAPACITY failed.
[ 2892.553426] sde : status=0, message=00, host=1, driver=00
[ 2892.553428] sde : sense not available.
[ 2892.553432] scsi 4:0:0:3: rejecting I/O to dead device
[ 2892.553436] sde: Write Protect is off
[ 2892.553438] sde: Mode Sense: 00 00 00 00
[ 2892.553441] sde: assuming drive cache: write through
[ 2892.553460] scsi 4:0:0:3: rejecting I/O to dead device


```

The device is still the same and worked under Edgy, although not initially.

Any ideas how to resolve?:confused:

---

