---
title: "Can't get Scan Disk to mount"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by jerrynewt on 2008-02-06
I have a Toshiba Satellite Pro 6100 with Gutsy 7.10. I can't seen to get my SD card to mount at all. It is recognized with lspci but how do I get it to mount automatically when it is inserted ?? Thanks for the help.

jerrynewt@Jerry2:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go] (rev a3)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
02:0a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
02:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
02:0b.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
02:0d.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 03)
05:00.0 Network controller: Broadcom Corporation BCM43xG 802.11b/g (rev 03)
05:00.1 Serial controller: Broadcom Corporation EDGE/GPRS data and 802.11b/g combo cardbus [GC89] (rev 03)
jerrynewt@Jerry2:~$

---

### Post by yabbadabbadont on 2008-02-06
Check your dmesg output (in a terminal window) just after plugging in the card and see if there are any error messages.

---

### Post by jerrynewt on 2008-02-06
Here is my dmesg output. The VJ compression error has to do with my ppp connection via my GC89 broadband card -- which I finally got to work after about three months of trial and error (still working with T-Mobile techs to get the rest of it done).

[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1502 pages used for memmap
[    0.000000]   Normal zone: 190818 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F01B0 checksum 0
[    0.000000] ACPI: RSDP 000F01B0, 0014 (r0 TOSHIB)
[    0.000000] ACPI: RSDT 2FF40000, 002C (r1 TOSHIB 750        970814 TASM  4010000)
[    0.000000] ACPI: FACP 2FF40054, 0084 (r2 TOSHIB 750        970814 TASM  4010000)
[    0.000000] ACPI: DSDT 2FF400D8, 69CC (r1 TOSHIB 6100     20021015 MSFT  100000A)
[    0.000000] ACPI: FACS 000EEE00, 0040
[    0.000000] ACPI: BOOT 2FF4002C, 0028 (r1 TOSHIB 750        970814 TASM  4010000)
[    0.000000] ACPI: PM-Timer IO Port: 0xee08
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 30000000:ceda0000)
[    0.000000] Built 1 zonelists.  Total pages: 194882
[    0.000000] Kernel command line: root=UUID=a41335c6-584c-4bae-80ca-b11335636f78 ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffd000 (0160e000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1794.256 MHz processor.
[   11.585765] Console: colour VGA+ 80x25
[   11.586726] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   11.587668] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   11.612231] Memory: 767244k/785664k available (2015k kernel code, 17884k reserved, 916k data, 364k init, 0k highmem)
[   11.612244] virtual kernel memory layout:
[   11.612246]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   11.612248]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   11.612249]     vmalloc : 0xf0800000 - 0xff7fe000   ( 239 MB)
[   11.612251]     lowmem  : 0xc0000000 - 0xeff40000   ( 767 MB)
[   11.612252]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   11.612254]       .data : 0xc02f7e66 - 0xc03dce84   ( 916 kB)
[   11.612255]       .text : 0xc0100000 - 0xc02f7e66   (2015 kB)
[   11.612260] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   11.612315] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   11.692244] Calibrating delay using timer specific routine.. 3592.20 BogoMIPS (lpj=7184415)
[   11.692279] Security Framework v1.0.0 initialized
[   11.692289] SELinux:  Disabled at boot.
[   11.692308] Mount-cache hash table entries: 512
[   11.692509] CPU: After generic identify, caps: bfebf9ff 00000000 00000000 00000000 00000400 00000000 00000000
[   11.692528] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   11.692532] CPU: L2 cache: 512K
[   11.692535] CPU: Hyper-Threading is disabled
[   11.692539] CPU: After all inits, caps: bfebf9ff 00000000 00000000 0000b080 00000400 00000000 00000000
[   11.692555] Compat vDSO mapped to ffffe000.
[   11.692574] Checking 'hlt' instruction... OK.
[   11.708384] SMP alternatives: switching to UP code
[   11.708640] Freeing SMP alternatives: 11k freed
[   11.709060] Early unpacking initramfs... done
[   12.150919] ACPI: Core revision 20070126
[   12.151017] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   12.153769] ACPI: setting ELCR to 0200 (from 0e00)
[   12.154292] CPU0: Intel Mobile Intel(R) Pentium(R) 4 - M CPU 1.80GHz stepping 07
[   12.154302] SMP motherboard not detected.
[   12.154305] Local APIC not detected. Using dummy APIC emulation.
[   12.154360] Brought up 1 CPUs
[   12.154548] Booting paravirtualized kernel on bare hardware
[   12.154625] Time: 16:05:36  Date: 01/06/108
[   12.154658] NET: Registered protocol family 16
[   12.154805] EISA bus registered
[   12.154821] ACPI: bus type pci registered
[   12.154946] PCI: PCI BIOS revision 2.10 entry at 0xfd5ad, last bus=5
[   12.154950] PCI: Using configuration type 1
[   12.154952] Setting up standard PCI resources
[   12.158404] ACPI: EC: Look up EC in DSDT
[   12.163996] ACPI: Interpreter enabled
[   12.164002] ACPI: (supports S0 S3 S4 S5)
[   12.164028] ACPI: Using PIC for interrupt routing
[   12.174076] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   12.174090] PCI: Probing PCI hardware (bus 00)
[   12.174550] PCI quirk: region ee00-ee7f claimed by ICH4 ACPI/GPIO/TCO
[   12.174555] PCI quirk: region eec0-eeff claimed by ICH4 GPIO
[   12.174986] PCI: Firmware left 0000:02:08.0 e100 interrupts enabled, disabling
[   12.175254] PCI: Transparent bridge - 0000:00:1e.0
[   12.175525] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   12.175581] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   12.175689] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[   12.179416] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *11 12)
[   12.179591] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *11 12)
[   12.179836] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *11 12)
[   12.180006] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *11 12)
[   12.180176] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *11 12)
[   12.180344] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *11 12)
[   12.180515] ACPI: PCI Interrupt Link [LNKG] (IRQs *10)
[   12.180682] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *11 12)
[   12.181028] ACPI: Power Resource [PFAN] (off)
[   12.181045] Linux Plug and Play Support v0.97 (c) Adam Belay
[   12.181072] pnp: PnP ACPI init
[   12.181087] ACPI: bus type pnp registered
[   12.188867] pnp: Device 00:0a activated.
[   12.188878]  00:0a: SMCf010 not responding at SIR 0x100, FIR 0x2f8; auto-configuring
[   12.190408] pnp: Device 00:0a disabled.
[   12.192980] pnp: Device 00:0a activated.
[   12.192990]  00:0a: not responding at SIR 0x100, FIR 0x2f8; swapping SIR/FIR and reconfiguring
[   12.193468] pnp: Device 00:0a disabled.
[   12.196211] pnp: Device 00:0a activated.
[   12.196222]  00:0a: responds at SIR 0x2f8, FIR 0x100
[   12.198234] pnp: PnP ACPI: found 12 devices
[   12.198238] ACPI: ACPI bus type pnp unregistered
[   12.198245] PnPBIOS: Disabled by ACPI PNP
[   12.198329] PCI: Using ACPI for IRQ routing
[   12.198335] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   12.205118] NET: Registered protocol family 8
[   12.205121] NET: Registered protocol family 20
[   12.205226] pnp: 00:00: iomem range 0x0-0x9ffff could not be reserved
[   12.205231] pnp: 00:00: iomem range 0xe0000-0xeffff could not be reserved
[   12.205235] pnp: 00:00: iomem range 0xf0000-0xfffff could not be reserved
[   12.205239] pnp: 00:00: iomem range 0x100000-0x2ff3ffff could not be reserved
[   12.207610] Time: tsc clocksource has been installed.
[   12.235750] PCI: Bridge: 0000:00:01.0
[   12.235753]   IO window: disabled.
[   12.235759]   MEM window: fd000000-fdffffff
[   12.235764]   PREFETCH window: dbf00000-dfffffff
[   12.235795] PCI: Bus 3, cardbus bridge: 0000:02:0a.0
[   12.235799]   IO window: 0000d000-0000d0ff
[   12.235804]   IO window: 0000d400-0000d4ff
[   12.235810]   PREFETCH window: 40000000-43ffffff
[   12.235816]   MEM window: 50000000-53ffffff
[   12.235822] PCI: Bus 5, cardbus bridge: 0000:02:0b.0
[   12.235825]   IO window: 0000d800-0000d8ff
[   12.235831]   IO window: 0000dc00-0000dcff
[   12.235837]   PREFETCH window: 44000000-47ffffff
[   12.235843]   MEM window: 54000000-57ffffff
[   12.235849] PCI: Bus 9, cardbus bridge: 0000:02:0b.1
[   12.235852]   IO window: 00001c00-00001cff
[   12.235858]   IO window: 00002000-000020ff
[   12.235864]   PREFETCH window: 48000000-4bffffff
[   12.235870]   MEM window: 58000000-5bffffff
[   12.235876] PCI: Bridge: 0000:00:1e.0
[   12.235880]   IO window: d000-dfff
[   12.235888]   MEM window: fce00000-fcefffff
[   12.235894]   PREFETCH window: 40000000-4bffffff
[   12.235917] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   12.235937] PCI: Enabling device 0000:02:0a.0 (0000 -> 0003)
[   12.236250] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[   12.236255] PCI: setting IRQ 11 as level-triggered
[   12.236259] ACPI: PCI Interrupt 0000:02:0a.0[A] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
[   12.236284] PCI: Enabling device 0000:02:0b.0 (0000 -> 0003)
[   12.236545] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[   12.236549] ACPI: PCI Interrupt 0000:02:0b.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   12.236573] PCI: Enabling device 0000:02:0b.1 (0000 -> 0003)
[   12.236832] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[   12.236836] ACPI: PCI Interrupt 0000:02:0b.1[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   12.236862] NET: Registered protocol family 2
[   12.275600] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   12.275835] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   12.278180] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   12.279115] TCP: Hash tables configured (established 131072 bind 65536)
[   12.279124] TCP reno registered
[   12.287774] checking if image is initramfs... it is
[   12.738983] Switched to high resolution mode on CPU 0
[   13.166791] Freeing initrd memory: 7061k freed
[   13.166989] Simple Boot Flag at 0x7c set to 0x1
[   13.167283] audit: initializing netlink socket (disabled)
[   13.167304] audit(1202313936.100:1): initialized
[   13.170483] VFS: Disk quotas dquot_6.5.1
[   13.170574] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   13.170717] io scheduler noop registered
[   13.170720] io scheduler anticipatory registered
[   13.170723] io scheduler deadline registered
[   13.170752] io scheduler cfq registered (default)
[   13.170813] Boot video device is 0000:01:00.0
[   13.171059] isapnp: Scanning for PnP cards...
[   13.524046] isapnp: No Plug & Play device found
[   13.565580] Real Time Clock Driver v1.12ac
[   13.565736] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   13.565921] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   13.566222] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   13.567177] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   13.567489] PCI: Enabling device 0000:00:1f.6 (0000 -> 0001)
[   13.567503] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   13.567514] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[   13.568376] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   13.568708] input: Macintosh mouse button emulation as /class/input/input0
[   13.568837] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   13.575221] serio: i8042 KBD port at 0x60,0x64 irq 1
[   13.575232] serio: i8042 AUX port at 0x60,0x64 irq 12
[   13.575530] mice: PS/2 mouse device common for all mice
[   13.575711] EISA: Probing bus 0 at eisa.0
[   13.575722] Cannot allocate resource for EISA slot 1
[   13.575726] Cannot allocate resource for EISA slot 2
[   13.575746] EISA: Detected 0 cards.
[   13.575899] TCP cubic registered
[   13.575917] NET: Registered protocol family 1
[   13.575953] Using IPI No-Shortcut mode
[   13.576240]   Magic number: 12:633:84
[   13.577292] Freeing unused kernel memory: 364k freed
[   13.613891] input: AT Translated Set 2 keyboard as /class/input/input1
[   14.890177] AppArmor: AppArmor initialized<5>audit(1202313938.100:2):  type=1505 info="AppArmor initialized" pid=1201
[   14.900252] fuse init (API version 7.8)
[   14.907486] Failure registering capabilities with primary security module.
[   14.918434] ACPI: Transitioning device [FAN] to D3
[   14.918440] ACPI: Transitioning device [FAN] to D3
[   14.918445] ACPI: Fan [FAN] (off)
[   14.925976] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   14.927526] ACPI: Thermal Zone [THRM] (65 C)
[   15.757806] usbcore: registered new interface driver usbfs
[   15.757843] usbcore: registered new interface driver hub
[   15.757876] usbcore: registered new device driver usb
[   15.759253] USB Universal Host Controller Interface driver v3.0
[   15.759351] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   15.759370] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   15.759375] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   15.759614] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   15.759648] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000efe0
[   15.759819] usb usb1: configuration #1 chosen from 1 choice
[   15.759863] hub 1-0:1.0: USB hub found
[   15.759872] hub 1-0:1.0: 2 ports detected
[   15.863584] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[   15.863592] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   15.863610] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   15.863615] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   15.863652] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   15.863684] uhci_hcd 0000:00:1d.1: irq 11, io base 0x0000ef80
[   15.863837] usb usb2: configuration #1 chosen from 1 choice
[   15.863878] hub 2-0:1.0: USB hub found
[   15.863891] hub 2-0:1.0: 2 ports detected
[   15.871296] SCSI subsystem initialized
[   15.879854] libata version 2.21 loaded.
[   15.898091] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k4-NAPI
[   15.898097] e100: Copyright(c) 1999-2006 Intel Corporation
[   15.966920] PCI: Enabling device 0000:00:1d.2 (0000 -> 0001)
[   15.967267] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[   15.967272] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   15.967290] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   15.967295] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   15.967333] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   15.967363] uhci_hcd 0000:00:1d.2: irq 11, io base 0x000018c0
[   15.967515] usb usb3: configuration #1 chosen from 1 choice
[   15.967556] hub 3-0:1.0: USB hub found
[   15.967567] hub 3-0:1.0: 2 ports detected
[   16.071876] ata_piix 0000:00:1f.1: version 2.11
[   16.071908] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   16.071971] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   16.072178] scsi0 : ata_piix
[   16.072265] scsi1 : ata_piix
[   16.072865] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001cfa0 irq 14
[   16.072870] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001cfa8 irq 15
[   16.102603] usb 1-1: new full speed USB device using uhci_hcd and address 2
[    4.652000] Marking TSC unstable due to: possible TSC halt in C2.
[    4.656000] Time: acpi_pm clocksource has been installed.
[    4.672000] usb 1-1: configuration #1 chosen from 1 choice
[    4.676000] hub 1-1:1.0: USB hub found
[    4.676000] hub 1-1:1.0: 4 ports detected
[    4.680000] ata1.00: ATA-7: WDC WD1200UE-00KVT0, 01.03K01, max UDMA/100
[    4.680000] ata1.00: 234441648 sectors, multi 0: LBA48 
[    4.692000] ata1.00: configured for UDMA/100
[    4.992000] usb 1-1.4: new low speed USB device using uhci_hcd and address 3
[    5.012000] ata2.00: ATAPI: DW-28E, 7.0A, max UDMA/33
[    5.128000] usb 1-1.4: configuration #1 chosen from 1 choice
[    5.148000] usbcore: registered new interface driver hiddev
[    5.168000] input: Logitech USB RECEIVER as /class/input/input2
[    5.168000] input: USB HID v1.11 Mouse [Logitech USB RECEIVER] on usb-0000:00:1d.0-1.4
[    5.168000] usbcore: registered new interface driver usbhid
[    5.168000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[    5.176000] ata2.00: configured for UDMA/33
[    5.184000] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1200UE-00K 01.0 PQ: 0 ANSI: 5
[    5.184000] scsi 1:0:0:0: CD-ROM            TEAC     DW-28E           7.0A PQ: 0 ANSI: 5
[    5.188000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[    5.188000] ACPI: PCI Interrupt 0000:02:08.0[A] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
[    5.212000] e100: eth0: e100_probe: addr 0xfceff000, irq 11, MAC addr 00:00:39:05:BA:E3
[    5.236000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    5.236000] sd 0:0:0:0: [sda] Write Protect is off
[    5.236000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.236000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.236000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    5.236000] sd 0:0:0:0: [sda] Write Protect is off
[    5.236000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.236000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.236000]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    5.312000] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.316000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.316000] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    5.348000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    5.348000] Uniform CD-ROM driver Revision: 3.20
[    5.348000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.700000] Attempting manual resume
[    5.700000] swsusp: Resume From Partition 8:5
[    5.700000] PM: Checking swsusp image.
[    5.700000] PM: Resume from disk failed.
[    5.744000] kjournald starting.  Commit interval 5 seconds
[    5.744000] EXT3-fs: mounted filesystem with ordered data mode.
[   15.108000] Linux agpgart interface v0.102 (c) Dave Jones
[   15.128000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   15.136000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.224000] intel_rng: FWH not detected
[   15.236000] agpgart: Detected an Intel 845G Chipset.
[   15.252000] agpgart: AGP aperture is 256M @ 0xe0000000
[   15.404000] iTCO_vendor_support: vendor-support=0
[   15.404000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   15.404000] iTCO_wdt: Found a ICH3-M TCO device (Version=1, TCOBASE=0xee60)
[   15.404000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   15.740000] Yenta: CardBus bridge found at 0000:02:0a.0 [12a3:ab01]
[   15.740000] Yenta: Enabling burst memory read transactions
[   15.740000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   15.740000] Yenta: Routing CardBus interrupts to PCI
[   15.740000] Yenta TI: socket 0000:02:0a.0, mfunc 0x01000002, devctl 0x60
[   15.972000] Yenta: ISA IRQ mask 0x0000, PCI irq 11
[   15.972000] Socket status: 30000010
[   15.972000] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xdfff
[   15.972000] cs: IO port probe 0xd000-0xdfff: clean.
[   15.972000] pcmcia: parent PCI bridge Memory window: 0xfce00000 - 0xfcefffff
[   15.972000] pcmcia: parent PCI bridge Memory window: 0x40000000 - 0x4bffffff
[   15.972000] Yenta: CardBus bridge found at 0000:02:0b.0 [1179:0001]
[   16.100000] Yenta: ISA IRQ mask 0x04b8, PCI irq 11
[   16.100000] Socket status: 30000020
[   16.100000] Yenta: Raising subordinate bus# of parent bus (#02) from #05 to #08
[   16.100000] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xdfff
[   16.100000] cs: IO port probe 0xd000-0xdfff: clean.
[   16.100000] pcmcia: parent PCI bridge Memory window: 0xfce00000 - 0xfcefffff
[   16.100000] pcmcia: parent PCI bridge Memory window: 0x40000000 - 0x4bffffff
[   16.100000] Yenta: CardBus bridge found at 0000:02:0b.1 [1179:0001]
[   16.228000] Yenta: ISA IRQ mask 0x04b8, PCI irq 11
[   16.228000] Socket status: 30000007
[   16.228000] Yenta: Raising subordinate bus# of parent bus (#02) from #08 to #0c
[   16.228000] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xdfff
[   16.228000] cs: IO port probe 0xd000-0xdfff: clean.
[   16.228000] pcmcia: parent PCI bridge Memory window: 0xfce00000 - 0xfcefffff
[   16.228000] pcmcia: parent PCI bridge Memory window: 0x40000000 - 0x4bffffff
[   16.440000] input: PC Speaker as /class/input/input3
[   16.576000] usbcore: registered new interface driver lmpcm_usb
[   16.576000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/misc/lmpcm_usb.c: v0.5.5:USB Logitech MediaPlay Cordless Mouse driver
[   16.608000] pccard: PCMCIA card inserted into slot 0
[   16.736000] pccard: CardBus card inserted into slot 1
[   16.736000] PCI: Enabling device 0000:05:00.1 (0000 -> 0001)
[   16.736000] ACPI: PCI Interrupt 0000:05:00.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   16.736000] 0000:05:00.1: ttyS2 at I/O 0xd800 (irq = 11) is a 16550A
[   17.124000] input: ImPS/2 Generic Wheel Mouse as /class/input/input4
[   17.136000] pnp: Device 00:0b activated.
[   17.136000] parport_pc 00:0b: reported by Plug and Play ACPI
[   17.136000] pnp: Device 00:0b disabled.
[   17.304000] irda_init()
[   17.304000] NET: Registered protocol family 23
[   17.332000] Detected unconfigured Toshiba laptop with Intel 82801CAM ISA bridge SMSC IrDA chip, pre-configuring device.
[   17.332000] Setting up Intel 82801 controller and SMSC device
[   17.332000] Detected Chip id: 0x5a, setting up registers...
[   17.332000] found SMC SuperIO Chip (devid=0x5a rev=00 base=0x002e): LPC47N227
[   17.332000] smsc_superio_flat(): fir: 0x130, sir: 0x3f8, dma: 03, irq: 3, mode: 0x0e
[   17.332000] smsc_ircc_present: can't get sir_base of 0x3f8
[   17.384000] cs: memory probe 0xfce00000-0xfcefffff: excluding 0xfce00000-0xfce0ffff 0xfcef0000-0xfcefffff
[   17.392000] pcmcia: registering new device pcmcia0.0
[   17.748000] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   17.796000] ieee80211_crypt: registered algorithm 'NULL'
[   17.820000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   17.820000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   17.856000] PCI: Enabling device 0000:00:1f.5 (0000 -> 0001)
[   17.856000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   17.856000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   17.940000] bcm43xx driver
[   17.972000] cs: IO port probe 0x100-0x3af: excluding 0x130-0x137
[   17.972000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   17.972000] cs: IO port probe 0x820-0x8ff: clean.
[   17.972000] cs: IO port probe 0xc00-0xcf7: clean.
[   17.972000] cs: IO port probe 0xa00-0xaff: clean.
[   17.988000] orinoco_cs 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   17.988000] pcmcia: request for exclusive IRQ could not be fulfilled.
[   17.988000] pcmcia: the driver needs updating to supported shared IRQ lines.
[   18.032000] cs: IO port probe 0x100-0x3af: excluding 0x130-0x137
[   18.032000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   18.032000] cs: IO port probe 0x820-0x8ff: clean.
[   18.032000] cs: IO port probe 0xc00-0xcf7: clean.
[   18.036000] cs: IO port probe 0xa00-0xaff: clean.
[   18.036000] cs: IO port probe 0x100-0x3af: excluding 0x130-0x137
[   18.036000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   18.040000] cs: IO port probe 0x820-0x8ff: clean.
[   18.040000] cs: IO port probe 0xc00-0xcf7: clean.
[   18.040000] cs: IO port probe 0xa00-0xaff: clean.
[   18.084000] eth1: Hardware identity 0005:0004:0005:0000
[   18.084000] eth1: Station identity  001f:0001:0008:000a
[   18.084000] eth1: Firmware determined as Lucent/Agere 8.10
[   18.084000] eth1: Ad-hoc demo mode supported
[   18.084000] eth1: IEEE standard IBSS ad-hoc mode supported
[   18.084000] eth1: WEP supported, 104-bit key
[   18.084000] eth1: MAC address 00:02:2D:86:00:49
[   18.084000] eth1: Station name "HERMES I"
[   18.084000] eth1: ready
[   18.084000] eth1: orinoco_cs at 0.0, irq 11, io 0xd100-0xd13f
[   18.428000] intel8x0_measure_ac97_clock: measured 55373 usecs
[   18.428000] intel8x0: clocking to 48000
[   18.428000] PCI: Enabling device 0000:05:00.0 (0000 -> 0002)
[   18.428000] ACPI: PCI Interrupt 0000:05:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   18.428000] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   19.580000] lp: driver loaded but no devices found
[   19.616000] apm: BIOS version 1.2 Flags 0x02 (Driver version 1.16ac)
[   19.616000] apm: overridden by ACPI.
[   19.708000] Adding 2265124k swap on /dev/sda5.  Priority:-1 extents:1 across:2265124k
[   20.180000] EXT3 FS on sda2, internal journal
[   21.008000] kjournald starting.  Commit interval 5 seconds
[   21.008000] EXT3 FS on sda6, internal journal
[   21.008000] EXT3-fs: mounted filesystem with ordered data mode.
[   24.264000] No dock devices found.
[   24.288000] ACPI: Battery Slot [BAT1] (battery present)
[   24.288000] ACPI: Battery Slot [BAT2] (battery absent)
[   24.376000] ACPI: AC Adapter [ADP1] (on-line)
[   24.392000] ACPI: Video Device [VGA] (multi-head: yes  rom: yes  post: no)
[   24.424000] ACPI: \_SB_.PCI0.FNC1.IDE1.HD_1: found ejectable bay
[   24.424000] ACPI: \_SB_.PCI0.FNC1.IDE1.HD_1: Adding notify handler
[   24.424000] ACPI: Error installing bay notify handler
[   24.424000] ACPI: Bay [\_SB_.PCI0.FNC1.IDE1.HD_1] Added
[   24.496000] input: Power Button (FF) as /class/input/input5
[   24.500000] ACPI: Power Button (FF) [PWRF]
[   24.552000] input: Lid Switch as /class/input/input6
[   24.556000] ACPI: Lid Switch [LID]
[   24.572000] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.19a-dev
[   24.572000] toshiba_acpi:     HCI method: \_SB_.VALD.GHCI
[   24.576000] toshiba_acpi: Toshiba hotkeys are sent as ACPI events
[   24.576000] toshiba_acpi: ktoshkeyd will check 2 times per second
[   24.580000] toshiba_acpi: Dropped 0 keys from the queue on startup
[   25.792000] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   25.792000] PCI: Setting latency timer of device 0000:00:1f.6 to 64
[   25.992000] ttyS1: LSR safety check engaged!
[   26.848000] ppdev: user-space parallel port driver
[   27.416000] audit(1202335562.747:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4940 profile="/usr/sbin/cupsd"
[   27.520000] apm: BIOS version 1.2 Flags 0x02 (Driver version 1.16ac)
[   27.520000] apm: disabled on user request.
[   28.436000] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[   28.548000] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   28.564000] NFSD: starting 90-second grace period
[   28.844000] Failure registering capabilities with primary security module.
[   30.128000] Clocksource tsc unstable (delta = -166678848 ns)
[  112.760000] PPP generic driver version 2.4.2
[  130.776000] PPP BSD Compression module registered
[  130.884000] PPP Deflate Compression module registered
[  516.140000] PPP: VJ decompression error
[ 2386.272000] PPP: VJ decompression error
[ 2571.148000] PPP: VJ decompression error
[ 2629.492000] PPP: VJ decompression error
[ 2633.556000] PPP: VJ decompression error
[ 2888.448000] PPP: VJ decompression error
[ 2905.264000] PPP: VJ decompression error
[ 3329.544000] PPP: VJ decompression error
[ 3604.832000] PPP: VJ decompression error
[ 4070.668000] PPP: VJ decompression error
[ 4124.432000] PPP: VJ decompression error
[ 4280.452000] PPP: VJ decompression error

---

### Post by yabbadabbadont on 2008-02-06
Did you have the SD card inserted when you ran dmesg and produced that output?  If so, it appears that the kernel doesn't see it.  In which case, good luck.  ;)

If you didn't have it inserted, plug it in, run the command again, but only post the last 30 lines or so.  :D

---

### Post by jerrynewt on 2008-02-06
Ok after inserting the card this is dmesg output.

[   17.972000] eth1: orinoco_cs at 0.0, irq 11, io 0xd100-0xd13f
[   18.244000] PCI: Enabling device 0000:00:1f.5 (0000 -> 0001)
[   18.244000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   18.244000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   18.816000] intel8x0_measure_ac97_clock: measured 55394 usecs
[   18.816000] intel8x0: clocking to 48000
[   19.816000] lp: driver loaded but no devices found
[   19.848000] apm: BIOS version 1.2 Flags 0x02 (Driver version 1.16ac)
[   19.848000] apm: overridden by ACPI.
[   19.940000] Adding 2265124k swap on /dev/sda5.  Priority:-1 extents:1 across:2265124k
[   20.416000] EXT3 FS on sda2, internal journal
[   21.256000] kjournald starting.  Commit interval 5 seconds
[   21.256000] EXT3 FS on sda6, internal journal
[   21.256000] EXT3-fs: mounted filesystem with ordered data mode.
[   24.476000] No dock devices found.
[   24.500000] ACPI: Battery Slot [BAT1] (battery present)
[   24.500000] ACPI: Battery Slot [BAT2] (battery absent)
[   24.588000] ACPI: AC Adapter [ADP1] (on-line)
[   24.604000] ACPI: Video Device [VGA] (multi-head: yes  rom: yes  post: no)
[   24.636000] ACPI: \_SB_.PCI0.FNC1.IDE1.HD_1: found ejectable bay
[   24.636000] ACPI: \_SB_.PCI0.FNC1.IDE1.HD_1: Adding notify handler
[   24.636000] ACPI: Error installing bay notify handler
[   24.636000] ACPI: Bay [\_SB_.PCI0.FNC1.IDE1.HD_1] Added
[   24.708000] input: Power Button (FF) as /class/input/input5
[   24.712000] ACPI: Power Button (FF) [PWRF]
[   24.764000] input: Lid Switch as /class/input/input6
[   24.772000] ACPI: Lid Switch [LID]
[   24.784000] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.19a-dev
[   24.784000] toshiba_acpi:     HCI method: \_SB_.VALD.GHCI
[   24.792000] toshiba_acpi: Toshiba hotkeys are sent as ACPI events
[   24.792000] toshiba_acpi: ktoshkeyd will check 2 times per second
[   24.792000] toshiba_acpi: Dropped 0 keys from the queue on startup
[   25.944000] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   25.944000] PCI: Setting latency timer of device 0000:00:1f.6 to 64
[   26.552000] ttyS1: LSR safety check engaged!
[   26.948000] ppdev: user-space parallel port driver
[   27.540000] audit(1202344143.620:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4933 profile="/usr/sbin/cupsd"
[   27.644000] apm: BIOS version 1.2 Flags 0x02 (Driver version 1.16ac)
[   27.644000] apm: disabled on user request.
[   28.592000] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[   28.716000] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   28.732000] NFSD: starting 90-second grace period
[   29.036000] Failure registering capabilities with primary security module.
[   29.628000] Clocksource tsc unstable (delta = -77598458 ns)
[  122.268000] PPP generic driver version 2.4.2
[  139.976000] PPP BSD Compression module registered
[  140.172000] PPP Deflate Compression module registered
[  179.580000] PPP: VJ decompression error
[  179.880000] PPP: VJ decompression error
[  180.208000] PPP: VJ decompression error
[  283.412000] PPP: VJ decompression error
[  293.016000] PPP: VJ decompression error
[  446.436000] PPP: VJ decompression error
[  490.136000] PPP: VJ decompression error
[  504.476000] PPP: VJ decompression error
[  625.948000] PPP: VJ decompression error
jerrynewt@Jerry2:~$

---

### Post by yabbadabbadont on 2008-02-07
Doesn't look to me like the kernel sees it.  Looks like it is time to start wading through google results.  Sorry.

---

