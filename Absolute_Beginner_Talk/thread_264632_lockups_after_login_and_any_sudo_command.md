---
title: "lockups after login and any sudo command"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2006-09-24
right after i sign in, it stays on the brown screen for a good 2 minutes. then once it's up and running, it runs very nice with no problems until i try to open something that requires sudo action and it then locks for awhile again. here's my dmesg output.

```
[17179569.184000] Linux version 2.6.15-27-686 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Sat Sep 16 02:13:27 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e0000 - 00000000000eee00 (reserved)
[17179569.184000]  BIOS-e820: 00000000000eee00 - 00000000000ef000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000000ef000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001ff40000 (usable)
[17179569.184000]  BIOS-e820: 000000001ff40000 - 000000001ff50000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000001ff50000 - 0000000020000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000feda0000 - 00000000fedc0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffb80000 - 00000000ffc00000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 511MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 130880
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 126784 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 TOSHIB                                ) @ 0x000f01b0
[17179569.184000] ACPI: RSDT (v001 TOSHIB 750      0x00970814 TASM 0x04010000) @ 0x1ff40000
[17179569.184000] ACPI: FADT (v002 TOSHIB 750      0x00970814 TASM 0x04010000) @ 0x1ff40054
[17179569.184000] ACPI: BOOT (v001 TOSHIB 750      0x00970814 TASM 0x04010000) @ 0x1ff4002c
[17179569.184000] ACPI: DSDT (v001 TOSHIB 6100     0x20020411 MSFT 0x0100000a) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0xee08
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:deda0000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda2 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (014c1000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[17179569.184000] Detected 1495.410 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179570.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179570.008000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179570.028000] Memory: 506984k/523520k available (2115k kernel code, 15968k reserved, 595k data, 332k init, 0k highmem)
[17179570.028000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179570.108000] Calibrating delay using timer specific routine.. 2994.86 BogoMIPS (lpj=5989726)
[17179570.108000] Security Framework v1.0.0 initialized
[17179570.108000] SELinux:  Disabled at boot.
[17179570.108000] Mount-cache hash table entries: 512
[17179570.108000] CPU: After generic identify, caps: 3febf9ff 00000000 00000000 00000000 00000000 00000000 00000000
[17179570.108000] CPU: After vendor identify, caps: 3febf9ff 00000000 00000000 00000000 00000000 00000000 00000000
[17179570.108000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[17179570.108000] CPU: L2 cache: 512K
[17179570.108000] CPU: Hyper-Threading is disabled
[17179570.108000] CPU: After all inits, caps: 3febf9ff 00000000 00000000 00000080 00000000 00000000 00000000
[17179570.108000] mtrr: v2.0 (20020519)
[17179570.108000] Enabling fast FPU save and restore... done.
[17179570.108000] Enabling unmasked SIMD FPU exception support... done.
[17179570.108000] Checking 'hlt' instruction... OK.
[17179570.124000] SMP alternatives: switching to UP code
[17179570.124000] checking if image is initramfs... it is
[17179571.080000] Freeing initrd memory: 6809k freed
[17179571.096000] ACPI: Looking for DSDT ... not found!
[17179571.100000] ACPI: setting ELCR to 0200 (from 0e00)
[17179571.100000] CPU0: Intel(R) Pentium(R) 4 Mobile CPU 1.50GHz stepping 04
[17179571.100000] SMP motherboard not detected.
[17179571.100000] Local APIC not detected. Using dummy APIC emulation.
[17179571.100000] Brought up 1 CPUs
[17179571.100000] NET: Registered protocol family 16
[17179571.100000] EISA bus registered
[17179571.100000] ACPI: bus type pci registered
[17179571.100000] PCI: PCI BIOS revision 2.10 entry at 0xfd5ad, last bus=5
[17179571.100000] PCI: Using configuration type 1
[17179571.100000] ACPI: Subsystem revision 20051216
[17179571.108000] ACPI: Interpreter enabled
[17179571.108000] ACPI: Using PIC for interrupt routing
[17179571.108000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *11 12)
[17179571.108000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *11 12)
[17179571.108000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *11 12)
[17179571.108000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *11 12)
[17179571.112000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *11 12)
[17179571.112000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *11 12)
[17179571.112000] ACPI: PCI Interrupt Link [LNKG] (IRQs *10)
[17179571.112000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *11 12)
[17179571.112000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179571.112000] PCI: Probing PCI hardware (bus 00)
[17179571.112000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179571.116000] PCI quirk: region ee00-ee7f claimed by ICH4 ACPI/GPIO/TCO
[17179571.116000] PCI quirk: region eec0-eeff claimed by ICH4 GPIO
[17179571.116000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179571.116000] Boot video device is 0000:01:00.0
[17179571.116000] PCI: Transparent bridge - 0000:00:1e.0
[17179571.116000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179571.124000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[17179571.128000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[17179571.132000] ACPI: Power Resource [PFAN] (off)
[17179571.132000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179571.132000] pnp: PnP ACPI init
[17179571.144000] pnp: PnP ACPI: found 13 devices
[17179571.144000] PnPBIOS: Disabled by ACPI PNP
[17179571.144000] PCI: Using ACPI for IRQ routing
[17179571.144000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179571.152000] PCI: Bridge: 0000:00:01.0
[17179571.152000]   IO window: disabled.
[17179571.152000]   MEM window: fd000000-fdffffff
[17179571.152000]   PREFETCH window: dbf00000-dfffffff
[17179571.152000] PCI: Bus 3, cardbus bridge: 0000:02:0b.0
[17179571.152000]   IO window: 0000d000-0000d0ff
[17179571.152000]   IO window: 0000d400-0000d4ff
[17179571.152000]   PREFETCH window: 30000000-31ffffff
[17179571.152000]   MEM window: 36000000-37ffffff
[17179571.152000] PCI: Bus 7, cardbus bridge: 0000:02:0b.1
[17179571.152000]   IO window: 0000d800-0000d8ff
[17179571.152000]   IO window: 0000dc00-0000dcff
[17179571.152000]   PREFETCH window: 32000000-33ffffff
[17179571.152000]   MEM window: 38000000-39ffffff
[17179571.152000] PCI: Bridge: 0000:00:1e.0
[17179571.152000]   IO window: d000-dfff
[17179571.152000]   MEM window: fce00000-fcefffff
[17179571.152000]   PREFETCH window: 30000000-33ffffff
[17179571.152000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179571.152000] PCI: Enabling device 0000:02:0b.0 (0000 -> 0003)
[17179571.152000] **** SET: Misaligned resource pointer: df98adc2 Type 07 Len 0
[17179571.152000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[17179571.152000] PCI: setting IRQ 11 as level-triggered
[17179571.152000] ACPI: PCI Interrupt 0000:02:0b.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179571.152000] PCI: Enabling device 0000:02:0b.1 (0000 -> 0003)
[17179571.152000] **** SET: Misaligned resource pointer: df98adc2 Type 07 Len 0
[17179571.152000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[17179571.152000] ACPI: PCI Interrupt 0000:02:0b.1[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[17179571.152000] Simple Boot Flag at 0x7c set to 0x1
[17179571.152000] audit: initializing netlink socket (disabled)
[17179571.152000] audit(1159136382.148:1): initialized
[17179571.152000] VFS: Disk quotas dquot_6.5.1
[17179571.152000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179571.152000] Initializing Cryptographic API
[17179571.152000] io scheduler noop registered
[17179571.152000] io scheduler anticipatory registered
[17179571.152000] io scheduler deadline registered
[17179571.152000] io scheduler cfq registered
[17179571.152000] isapnp: Scanning for PnP cards...
[17179571.508000] isapnp: No Plug & Play device found
[17179571.540000] Real Time Clock Driver v1.12
[17179571.540000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179571.544000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179571.544000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179571.544000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179571.544000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.548000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.548000] PCI: Enabling device 0000:00:1f.6 (0000 -> 0001)
[17179571.548000] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[17179571.548000] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[17179571.548000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179571.548000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179571.548000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179571.548000] mice: PS/2 mouse device common for all mice
[17179571.552000] EISA: Probing bus 0 at eisa.0
[17179571.552000] Cannot allocate resource for EISA slot 1
[17179571.552000] EISA: Detected 0 cards.
[17179571.552000] NET: Registered protocol family 2
[17179571.580000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179571.592000] IP route cache hash table entries: 8192 (order: 3, 32768 bytes)
[17179571.592000] TCP established hash table entries: 32768 (order: 6, 393216 bytes)
[17179571.592000] TCP bind hash table entries: 32768 (order: 6, 393216 bytes)
[17179571.592000] TCP: Hash tables configured (established 32768 bind 32768)
[17179571.592000] TCP reno registered
[17179571.592000] TCP bic registered
[17179571.592000] NET: Registered protocol family 1
[17179571.592000] NET: Registered protocol family 8
[17179571.592000] NET: Registered protocol family 20
[17179571.592000] Using IPI No-Shortcut mode
[17179571.592000] ACPI wakeup devices: 
[17179571.592000] MPC0 MPC1  LAN VIY0 VIY1  COM USB1 USB2 USB3 AMDM  LID 
[17179571.592000] ACPI: (supports S0 S3 S4 S5)
[17179571.592000] Freeing unused kernel memory: 332k freed
[17179571.676000] vga16fb: initializing
[17179571.676000] vga16fb: mapped to 0xc00a0000
[17179571.836000] Console: switching to colour frame buffer device 80x25
[17179571.836000] fb0: VGA16 VGA frame buffer device
[17179572.920000] Capability LSM initialized
[17179573.104000] ACPI: Fan [FAN] (off)
[17179573.112000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[17179573.116000] ACPI: Thermal Zone [THRM] (68 C)
[17179574.164000] ICH3M: IDE controller at PCI slot 0000:00:1f.1
[17179574.164000] **** SET: Misaligned resource pointer: dfcc6d02 Type 07 Len 0
[17179574.164000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[17179574.164000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179574.164000] ICH3M: chipset revision 2
[17179574.164000] ICH3M: not 100% native mode: will probe irqs later
[17179574.164000]     ide0: BM-DMA at 0xcfa0-0xcfa7, BIOS settings: hda:DMA, hdb:pio
[17179574.164000]     ide1: BM-DMA at 0xcfa8-0xcfaf, BIOS settings: hdc:DMA, hdd:pio
[17179574.164000] Probing IDE interface ide0...
[17179574.452000] hda: IC25N030ATCS04-0, ATA DISK drive
[17179575.124000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179575.144000] Probing IDE interface ide1...
[17179575.880000] hdc: TOSHIBA DVD-ROM SD-R2102, ATAPI CD/DVD-ROM drive
[17179576.216000] ide1 at 0x170-0x177,0x376 on irq 15
[17179576.228000] hda: max request size: 128KiB
[17179576.244000] hda: 58605120 sectors (30005 MB) w/1768KiB Cache, CHS=58140/16/63, UDMA(100)
[17179576.244000] hda: cache flushes not supported
[17179576.244000]  hda: hda1 hda2 hda3 < hda5 >
[17179576.304000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179576.304000] Uniform CD-ROM driver Revision: 3.20
[17179576.700000] usbcore: registered new driver usbfs
[17179576.700000] usbcore: registered new driver hub
[17179576.704000] USB Universal Host Controller Interface driver v2.3
[17179576.704000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179576.704000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179576.704000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179576.704000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179576.704000] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000efe0
[17179576.708000] hub 1-0:1.0: USB hub found
[17179576.708000] hub 1-0:1.0: 2 ports detected
[17179576.812000] **** SET: Misaligned resource pointer: dfcc67c2 Type 07 Len 0
[17179576.812000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[17179576.812000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179576.812000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179576.812000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179576.812000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179576.812000] uhci_hcd 0000:00:1d.1: irq 11, io base 0x0000ef80
[17179576.812000] hub 2-0:1.0: USB hub found
[17179576.812000] hub 2-0:1.0: 2 ports detected
[17179576.916000] PCI: Enabling device 0000:00:1d.2 (0000 -> 0001)
[17179576.916000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179576.916000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179576.916000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179576.916000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179576.916000] uhci_hcd 0000:00:1d.2: irq 11, io base 0x000018c0
[17179576.916000] hub 3-0:1.0: USB hub found
[17179576.916000] hub 3-0:1.0: 2 ports detected
[17179577.052000] usb 1-1: new low speed USB device using uhci_hcd and address 2
[17179577.200000] Attempting manual resume
[17179577.248000] usbcore: registered new driver hiddev
[17179577.252000] EXT3-fs: mounted filesystem with ordered data mode.
[17179577.268000] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /class/input/input1
[17179577.268000] input: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.0-1
[17179577.268000] usbcore: registered new driver usbhid
[17179577.268000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179577.288000] kjournald starting.  Commit interval 5 seconds
[17179593.664000] ts: Compaq touchscreen protocol output
[17179596.644000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179596.652000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179596.704000] hw_random: RNG not detected
[17179596.712000] Linux agpgart interface v0.101 (c) Dave Jones
[17179596.720000] agpgart: Detected an Intel i845 Chipset.
[17179596.736000] agpgart: AGP aperture is 256M @ 0xe0000000
[17179596.980000] nvidia: module license 'NVIDIA' taints kernel.
[17179596.984000] nvidia: Unknown parameter `NVreg_SoftEDIDS'
[17179597.172000] **** SET: Misaligned resource pointer: dfa03a82 Type 07 Len 0
[17179597.172000] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 10
[17179597.172000] PCI: setting IRQ 10 as level-triggered
[17179597.172000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKG] -> GSI 10 (level, low) -> IRQ 10
[17179597.172000] NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module  1.0-7174  Tue Mar 22 06:44:39 PST 2005
[17179597.172000] NVRM: PAT index 1 already configured for Write-Combining!
[17179597.172000] NVRM: Aborting, due to PAT already being configured
[17179597.880000] ACPI: PCI Interrupt 0000:02:0b.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179597.880000] Yenta: CardBus bridge found at 0000:02:0b.0 [1179:0001]
[17179597.916000] input: PC Speaker as /class/input/input2
[17179598.032000] Yenta: ISA IRQ mask 0x00b8, PCI irq 11
[17179598.032000] Socket status: 30000020
[17179598.032000] Yenta: Raising subordinate bus# of parent bus (#02) from #05 to #06
[17179598.032000] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xdfff
[17179598.032000] cs: IO port probe 0xd000-0xdfff: clean.
[17179598.032000] pcmcia: parent PCI bridge Memory window: 0xfce00000 - 0xfcefffff
[17179598.032000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[17179598.036000] e100: Intel(R) PRO/100 Network Driver, 3.4.14-k4-NAPI
[17179598.036000] e100: Copyright(c) 1999-2005 Intel Corporation
[17179598.036000] **** SET: Misaligned resource pointer: dfa03782 Type 07 Len 0
[17179598.052000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[17179598.052000] ACPI: PCI Interrupt 0000:02:08.0[A] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
[17179598.076000] e100: eth0: e100_probe: addr 0xfceff000, irq 11, MAC addr 00:00:39:0E:F3:DE
[17179598.076000] ACPI: PCI Interrupt 0000:02:0b.1[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[17179598.076000] Yenta: CardBus bridge found at 0000:02:0b.1 [1179:0001]
[17179598.148000] PCI: Enabling device 0000:00:1f.5 (0000 -> 0001)
[17179598.148000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[17179598.148000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[17179598.160000] logips2pp: Detected unknown logitech mouse model 0
[17179598.204000] Yenta: ISA IRQ mask 0x00b8, PCI irq 11
[17179598.204000] Socket status: 30000007
[17179598.204000] Yenta: Raising subordinate bus# of parent bus (#02) from #06 to #0a
[17179598.204000] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xdfff
[17179598.204000] cs: IO port probe 0xd000-0xdfff: clean.
[17179598.204000] pcmcia: parent PCI bridge Memory window: 0xfce00000 - 0xfcefffff
[17179598.204000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[17179598.656000] input: ImPS/2 Logitech Wheel Mouse as /class/input/input3
[17179598.716000] intel8x0_measure_ac97_clock: measured 55386 usecs
[17179598.716000] intel8x0: clocking to 48000
[17179598.816000] pccard: CardBus card inserted into slot 0
[17179599.064000] **** SET: Misaligned resource pointer: daec0242 Type 04 Len 42
[17179599.064000] **** SET: Misaligned resource pointer: daec02c6 Type 01 Len 42
[17179599.068000] pnp: Device 00:0a activated.
[17179599.068000] parport: PnPBIOS parport detected.
[17179599.068000] pnp: Device 00:0a disabled.
[17179599.324000] rtl_ieee80211_crypt: registered algorithm 'NULL'
[17179599.324000] rtl_ieee80211_crypt: registered algorithm 'TKIP'
[17179599.324000] rtl_ieee80211_crypt: registered algorithm 'WEP'
[17179599.324000] rtl_ieee80211_crypt: registered algorithm 'CCMP'
[17179599.344000] 
[17179599.344000] Linux kernel driver for RTL8180 / RTL8185 based WLAN cards
[17179599.344000] Copyright (c) 2004-2005, Andrea Merello
[17179599.344000] rtl8180: Initializing module
[17179599.344000] rtl8180: Wireless extensions version 19
[17179599.344000] rtl8180: Initializing proc filesystem
[17179599.344000] rtl8180: Configuring chip resources
[17179599.344000] PCI: Enabling device 0000:03:00.0 (0000 -> 0003)
[17179599.344000] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179599.344000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[17179599.344000] rtl8180: Memory mapped space @ 0x36000000 
[17179599.344000] rtl8180: MAC controller is a RTL8180
[17179599.344000] rtl8180: This is a CARDBUS NIC
[17179599.344000] rtl8180: Reported EEPROM chip is a 93c56 (2Kbit)
[17179599.352000] rtl8180: Card MAC address is 00:30:bd:4e:16:02
[17179599.360000] rtl8180: EEPROM version 102
[17179599.360000] rtl8180: RfParam: 5
[17179599.364000] rtl8180: Card reports RF frontend by Philips.
[17179599.364000] rtl8180: OK! Philips SA2400 radio chipset is supported.
[17179599.364000] rtl8180: Analog PHY found
[17179599.364000] rtl8180: Energy threshold: b
[17179599.364000] rtl8180: PAPE from CONFIG2: 6
[17179599.364000] rtl8180: Antenna A is default antenna
[17179599.364000] rtl8180: Antenna diversity is enabled
[17179599.364000] rtl8180: Carrier sense 1
[17179599.364000] rtl8180: 40-bit WEP is NOT supported in hardware
[17179599.364000] rtl8180: 104-bit WEP is NOT supported in hardware
[17179599.364000] rtl8180: IRQ 11
[17179599.364000] rtl8180: Driver probe completed
[17179599.364000] 
[17179599.524000] cs: IO port probe 0x100-0x3af: clean.
[17179599.524000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179599.524000] cs: IO port probe 0x820-0x8ff: clean.
[17179599.524000] cs: IO port probe 0xc00-0xcf7: clean.
[17179599.524000] cs: IO port probe 0xa00-0xaff: clean.
[17179599.528000] rtl8180: Bringing up iface
[17179599.540000] cs: IO port probe 0x100-0x3af: clean.
[17179599.540000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179599.544000] cs: IO port probe 0x820-0x8ff: clean.
[17179599.544000] cs: IO port probe 0xc00-0xcf7: clean.
[17179599.544000] cs: IO port probe 0xa00-0xaff: clean.
[17179599.752000] rtl8180: Card successfully reset
[17179600.512000] Linking with sweethome
[17179600.532000] Associated successfully
[17179600.532000] Using B rates
[17179600.588000] lp: driver loaded but no devices found
[17179600.680000] Adding 666656k swap on /dev/hda5.  Priority:-1 extents:1 across:666656k
[17179602.108000] NET: Registered protocol family 10
[17179602.108000] lo: Disabled Privacy Extensions
[17179602.108000] IPv6 over IPv4 tunneling driver
[17179612.724000] wlan0: no IPv6 routers present
[17179711.156000] EXT3 FS on hda2, internal journal
[17179711.380000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179711.380000] md: bitmap version 4.39
[17179712.128000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[17179712.860000] cdrom: open failed.
[17179714.088000] fuse init (API version 7.3)

```

---

### Post by shanepardue on 2006-09-25
sheesh! i figured it out. it was my router being retarded. no need to respond to this. it was only a defective router.

---

