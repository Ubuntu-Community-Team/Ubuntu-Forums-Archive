---
title: "Acer Aspire T660 es penja de forma aleatòria"
date: 2007-07-28
forum: Catalan Team
---

### Post by pepus on 2007-07-28
Hola a tothom.

Fa poc vaig adquirir un Acer Apire T660, amb Linux preinstal·lat.
Vaig instal·lar Ubuntu Fesity 7.04 i vaig actualitzar el Kernel al 2.6.20-16.
Es penja de forma aleatòria i no aconsegueixo trobar-hi cap patró.

A grans trets l'ordinador és un Pentium D925, 1GB RAM DDR2, 250GB HD S-ATA, nVidia GeForce 7300SE.

Faig un copy-paste de la informació important que pot ajudar a resoldre el tema:

Uname : Linux Pepone 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux

dmesg
[HTML]
    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e5000 size: 000000000001b000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003fec0000 end: 000000003ffc0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000003ffc0000 size: 000000000000e000 end: 000000003ffce000 type: 3
[    0.000000] copy_e820_map() start: 000000003ffce000 size: 0000000000022000 end: 000000003fff0000 type: 4
[    0.000000] copy_e820_map() start: 000000003fff0000 size: 0000000000010000 end: 0000000040000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000ff780000 size: 0000000000880000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e5000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ffc0000 (usable)
[    0.000000]  BIOS-e820: 000000003ffc0000 - 000000003ffce000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ffce000 - 000000003fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fff0000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 262080) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   262080
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   262080
[    0.000000] On node 0 totalpages: 262080
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 255 pages used for memmap
[    0.000000]   HighMem zone: 32449 pages, LIFO batch:7
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000f88a0
[    0.000000] ACPI: RSDT (v001 A M I  OEMRSDT  0x08000616 MSFT 0x00000097) @ 0x3ffc0000
[    0.000000] ACPI: FADT (v002 A M I  OEMFACP  0x08000616 MSFT 0x00000097) @ 0x3ffc0200
[    0.000000] ACPI: MADT (v001 A M I  OEMAPIC  0x08000616 MSFT 0x00000097) @ 0x3ffc0390
[    0.000000] ACPI: MCFG (v001 A M I  OEMMCFG  0x08000616 MSFT 0x00000097) @ 0x3ffc0400
[    0.000000] ACPI: WDRT (v001 A M I  OEMWDRT  0x08000616 MSFT 0x00000097) @ 0x3ffc0440
[    0.000000] ACPI: OEMB (v001 A M I  AMI_OEM  0x08000616 MSFT 0x00000097) @ 0x3ffce040
[    0.000000] ACPI: HPET (v001 A M I  OEMHPET  0x08000616 MSFT 0x00000097) @ 0x3ffc4b30
[    0.000000] ACPI: DSDT (v001   Acer  Acer415 0x00000000 INTL 0x20051117) @ 0x00000000
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:6 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:6 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8000 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bee00000)
[    0.000000] Detected 2992.848 MHz processor.
[   26.817073] Built 1 zonelists.  Total pages: 260033
[   26.817078] Kernel command line: root=UUID=b05ac1bd-c126-4ea6-9371-a4cfd9e48388 ro quiet splash
[   26.817244] mapped APIC to ffffd000 (fee00000)
[   26.817247] mapped IOAPIC to ffffc000 (fec00000)
[   26.817250] Enabling fast FPU save and restore... done.
[   26.817253] Enabling unmasked SIMD FPU exception support... done.
[   26.817266] Initializing CPU#0
[   26.817359] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   26.819863] Console: colour VGA+ 80x25
[   26.820529] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   26.821074] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   26.843879] Memory: 1028140k/1048320k available (1992k kernel code, 19508k reserved, 900k data, 328k init, 130816k highmem)
[   26.843889] virtual kernel memory layout:
[   26.843890]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   26.843891]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   26.843892]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   26.843893]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   26.843894]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   26.843896]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[   26.843897]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[   26.843900] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   26.844070] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[   26.844077] hpet0: 4 32-bit timers, 14318180 Hz
[   26.845085] Using HPET for base-timer
[   26.924027] Calibrating delay using timer specific routine.. 5991.20 BogoMIPS (lpj=11982419)
[   26.924074] Security Framework v1.0.0 initialized
[   26.924080] SELinux:  Disabled at boot.
[   26.924095] Mount-cache hash table entries: 512
[   26.924228] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e49d 00000000 00000001
[   26.924237] monitor/mwait feature present.
[   26.924239] using mwait in idle threads.
[   26.924246] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   26.924249] CPU: L2 cache: 2048K
[   26.924251] CPU: Physical Processor ID: 0
[   26.924253] CPU: Processor Core ID: 0
[   26.924255] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003180 0000e49d 00000000 00000001
[   26.924267] Compat vDSO mapped to ffffe000.
[   26.924270] Remapping vsyscall page to ffffe000
[   26.924285] Checking 'hlt' instruction... OK.
[   26.940125] SMP alternatives: switching to UP code
[   26.940496] Early unpacking initramfs... done
[   27.217726] ACPI: Core revision 20060707
[   27.217879] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   27.221098] CPU0: Intel(R) Pentium(R) D CPU 3.00GHz stepping 05
[   27.221122] SMP alternatives: switching to SMP code
[   27.221266] Booting processor 1/1 eip 3000
[   27.231811] Initializing CPU#1
[   27.311812] Calibrating delay using timer specific routine.. 5985.27 BogoMIPS (lpj=11970554)
[   27.311822] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e49d 00000000 00000001
[   27.311828] monitor/mwait feature present.
[   27.311834] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   27.311836] CPU: L2 cache: 2048K
[   27.311839] CPU: Physical Processor ID: 0
[   27.311840] CPU: Processor Core ID: 1
[   27.311842] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003180 0000e49d 00000000 00000001
[   27.312351] CPU1: Intel(R) Pentium(R) D CPU 3.00GHz stepping 05
[   27.312387] Total of 2 processors activated (11976.48 BogoMIPS).
[   27.312553] ENABLING IO-APIC IRQs
[   27.312747] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   27.459731] checking TSC synchronization across 2 CPUs: passed.
[    0.004007] Brought up 2 CPUs
[    0.256881] migration_cost=3559
[    0.257184] Booting paravirtualized kernel on bare hardware
[    0.257279] Time:  9:44:35  Date: 06/28/107
[    0.257314] NET: Registered protocol family 16
[    0.257411] EISA bus registered
[    0.257417] ACPI: bus type pci registered
[    0.257534] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=3
[    0.257536] PCI: Using configuration type 1
[    0.257538] Setting up standard PCI resources
[    0.308746] ACPI: Interpreter enabled
[    0.308750] ACPI: Using IOAPIC for interrupt routing
[    0.309245] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.309250] PCI: Probing PCI hardware (bus 00)
[    0.310638] Boot video device is 0000:01:00.0
[    0.311192] PCI: Transparent bridge - 0000:00:14.4
[    0.311245] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.331703] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[    0.332935] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE7._PRT]
[    0.341306] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[    0.345397] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 7 10 11 12 14 15)
[    0.345660] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *10 11 12 14 15)
[    0.345926] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *10 11 12 14 15)
[    0.346190] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *10 11 12 14 15)
[    0.346451] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 *11 12 14 15)
[    0.346715] ACPI: PCI Interrupt Link [LNKF] (IRQs 9) *0, disabled.
[    0.346972] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 *11 12 14 15)
[    0.347236] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 7 10 11 12 14 15)
[    0.347407] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.347418] pnp: PnP ACPI init
[    0.355455] pnp: PnP ACPI: found 16 devices
[    0.355460] PnPBIOS: Disabled by ACPI PNP
[    0.355508] PCI: Using ACPI for IRQ routing
[    0.355511] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.355519] PCI: Cannot allocate resource region 3 of device 0000:00:00.0
[    0.355543] PCI: Cannot allocate resource region 1 of device 0000:00:14.0
[    0.367618] NET: Registered protocol family 8
[    0.367621] NET: Registered protocol family 20
[    0.368778] pnp: 00:09: ioport range 0xa00-0xa0f has been reserved
[    0.368781] pnp: 00:09: ioport range 0xa10-0xa1f has been reserved
[    0.368784] pnp: 00:09: ioport range 0xa20-0xa2f has been reserved
[    0.368787] pnp: 00:09: ioport range 0xa30-0xa3f has been reserved
[    0.369125] PCI: Bridge: 0000:00:02.0
[    0.369127]   IO window: disabled.
[    0.369131]   MEM window: fa800000-fe8fffff
[    0.369136]   PREFETCH window: bff00000-dfefffff
[    0.369141] PCI: Bridge: 0000:00:07.0
[    0.369145]   IO window: b000-bfff
[    0.369149]   MEM window: fe900000-fe9fffff
[    0.369153]   PREFETCH window: disabled.
[    0.369158] PCI: Bridge: 0000:00:14.4
[    0.369161]   IO window: disabled.
[    0.369168]   MEM window: fea00000-feafffff
[    0.369174]   PREFETCH window: disabled.
[    0.369194] PCI: Setting latency timer of device 0000:00:02.0 to 64
[    0.369207] PCI: Setting latency timer of device 0000:00:07.0 to 64
[    0.369253] NET: Registered protocol family 2
[    0.408657] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.408823] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.409414] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.409753] TCP: Hash tables configured (established 131072 bind 65536)
[    0.409757] TCP reno registered
[    0.420896] checking if image is initramfs... it is
[    0.964742] Freeing initrd memory: 6786k freed
[    0.965617] audit: initializing netlink socket (disabled)
[    0.965635] audit(1185615875.664:1): initialized
[    0.965831] highmem bounce pool size: 64 pages
[    0.965974] VFS: Disk quotas dquot_6.5.1
[    0.965999] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.966058] io scheduler noop registered
[    0.966062] io scheduler anticipatory registered
[    0.966065] io scheduler deadline registered
[    0.966084] io scheduler cfq registered (default)
[    1.080214] PCI: Setting latency timer of device 0000:00:02.0 to 64
[    1.080260] assign_interrupt_mode Found MSI capability
[    1.080264] Allocate Port Service[0000:00:02.0:pcie00]
[    1.080393] PCI: Setting latency timer of device 0000:00:07.0 to 64
[    1.080438] assign_interrupt_mode Found MSI capability
[    1.080442] Allocate Port Service[0000:00:07.0:pcie00]
[    1.080673] isapnp: Scanning for PnP cards...
[    1.432176] isapnp: No Plug & Play device found
[    1.470057] Real Time Clock Driver v1.12ac
[    1.470226] hpet_resources: 0xfed00000 is busy
[    1.470253] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.470428] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.470636] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.471439] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.471740] 00:0d: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.471994] mice: PS/2 mouse device common for all mice
[    1.472946] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.473154] input: Macintosh mouse button emulation as /class/input/input0
[    1.473212] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.473217] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.473544] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.473941] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.473950] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.474098] EISA: Probing bus 0 at eisa.0
[    1.474146] EISA: Detected 0 cards.
[    1.504239] TCP cubic registered
[    1.504249] NET: Registered protocol family 1
[    1.504283] Starting balanced_irq
[    1.504290] Using IPI No-Shortcut mode
[    1.504365] input: AT Translated Set 2 keyboard as /class/input/input1
[    1.504439] ACPI: (supports S0 S1 S3 S4 S5)
[    1.504630]   Magic number: 15:746:728
[    1.505197] Freeing unused kernel memory: 328k freed
[    1.507170] Time: tsc clocksource has been installed.
[    2.736130] Capability LSM initialized
[    2.778283] ACPI: duty_cycle spans bit 4
[    2.778602] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [   AMI] OemTableId [  CPU1PM] [20060707]
[    2.778684] ACPI: duty_cycle spans bit 4
[    2.778884] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [   AMI] OemTableId [  CPU2PM] [20060707]
[    2.778940] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    2.778949] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    2.779907] ACPI: Thermal Zone [THRM] (-270 C)
[    3.181805] usbcore: registered new interface driver usbfs
[    3.181830] usbcore: registered new interface driver hub
[    3.181857] usbcore: registered new device driver usb
[    3.182591] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.182634] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 16 (level, low) -> IRQ 16
[    3.182649] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    3.182771] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[    3.182789] ohci_hcd 0000:00:13.0: irq 16, io mem 0xfebfe000
[    3.214134] SCSI subsystem initialized
[    3.259096] usb usb1: configuration #1 chosen from 1 choice
[    3.259128] hub 1-0:1.0: USB hub found
[    3.259141] hub 1-0:1.0: 2 ports detected
[    3.318063] libata version 2.20 loaded.
[    3.325891] ieee1394: Initialized config rom entry `ip1394'
[    3.362790] ACPI: PCI Interrupt 0000:00:13.1[B] -> GSI 17 (level, low) -> IRQ 17
[    3.362810] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    3.362926] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[    3.362947] ohci_hcd 0000:00:13.1: irq 17, io mem 0xfebfd000
[    3.422498] usb usb2: configuration #1 chosen from 1 choice
[    3.422527] hub 2-0:1.0: USB hub found
[    3.422538] hub 2-0:1.0: 2 ports detected
[    3.526374] ACPI: PCI Interrupt 0000:00:13.2[C] -> GSI 18 (level, low) -> IRQ 18
[    3.526388] ohci_hcd 0000:00:13.2: OHCI Host Controller
[    3.526415] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[    3.526432] ohci_hcd 0000:00:13.2: irq 18, io mem 0xfebfc000
[    3.586511] usb usb3: configuration #1 chosen from 1 choice
[    3.586539] hub 3-0:1.0: USB hub found
[    3.586550] hub 3-0:1.0: 2 ports detected
[    3.678298] usb 1-1: new low speed USB device using ohci_hcd and address 2
[    3.690406] ACPI: PCI Interrupt 0000:00:13.3[B] -> GSI 17 (level, low) -> IRQ 17
[    3.690420] ohci_hcd 0000:00:13.3: OHCI Host Controller
[    3.690443] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 4
[    3.690456] ohci_hcd 0000:00:13.3: irq 17, io mem 0xfebfb000
[    3.750374] usb usb4: configuration #1 chosen from 1 choice
[    3.750403] hub 4-0:1.0: USB hub found
[    3.750415] hub 4-0:1.0: 2 ports detected
[    3.854408] ACPI: PCI Interrupt 0000:00:13.4[C] -> GSI 18 (level, low) -> IRQ 18
[    3.854421] ohci_hcd 0000:00:13.4: OHCI Host Controller
[    3.854444] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 5
[    3.854458] ohci_hcd 0000:00:13.4: irq 18, io mem 0xfebfa000
[    3.899497] usb 1-1: configuration #1 chosen from 1 choice
[    3.914592] usb usb5: configuration #1 chosen from 1 choice
[    3.914625] hub 5-0:1.0: USB hub found
[    3.914637] hub 5-0:1.0: 2 ports detected
[    4.018626] ACPI: PCI Interrupt 0000:03:04.0[A] -> GSI 23 (level, low) -> IRQ 19
[    4.068437] SB600_PATA: IDE controller at PCI slot 0000:00:14.1
[    4.068457] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[    4.068471] SB600_PATA: chipset revision 0
[    4.068473] SB600_PATA: not 100% native mode: will probe irqs later
[    4.068484]     ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:DMA, hdb:pio
[    4.068498] Probing IDE interface ide0...
[    4.068658] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[feaf7800-feaf7fff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    4.254373] usb 4-1: new full speed USB device using ohci_hcd and address 2
[    4.475014] usb 4-1: configuration #1 chosen from 1 choice
[    4.804650] hda: HL-DT-STDVD+-RW GSA-H21N, ATAPI CD/DVD-ROM drive
[    5.140417] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    5.143031] ahci 0000:00:12.0: version 2.1
[    5.143058] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 20
[    5.346761] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00000ae6ff6dba07]
[    6.147745] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    6.147751] ahci 0000:00:12.0: flags: 64bit ncq ilck pm led clo pmp pio slum part 
[    6.147913] ata1: SATA max UDMA/133 cmd 0xf8868d00 ctl 0x00000000 bmdma 0x00000000 irq 20
[    6.148028] ata2: SATA max UDMA/133 cmd 0xf8868d80 ctl 0x00000000 bmdma 0x00000000 irq 20
[    6.148152] ata3: SATA max UDMA/133 cmd 0xf8868e00 ctl 0x00000000 bmdma 0x00000000 irq 20
[    6.148297] ata4: SATA max UDMA/133 cmd 0xf8868e80 ctl 0x00000000 bmdma 0x00000000 irq 20
[    6.148313] scsi0 : ahci
[    6.630652] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    6.671576] ata1.00: ata_hpa_resize 1: sectors = 488397168, hpa_sectors = 488397168
[    6.671583] ata1.00: ATA-7: ST3250824AS, 3.AAE, max UDMA/133
[    6.671586] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    6.729841] ata1.00: ata_hpa_resize 1: sectors = 488397168, hpa_sectors = 488397168
[    6.729847] ata1.00: configured for UDMA/133
[    6.729862] scsi1 : ahci
[    7.042682] ata2: SATA link down (SStatus 0 SControl 300)
[    7.042702] scsi2 : ahci
[    7.354734] ata3: SATA link down (SStatus 0 SControl 300)
[    7.354753] scsi3 : ahci
[    7.666853] ata4: SATA link down (SStatus 0 SControl 300)
[    7.667011] scsi 0:0:0:0: Direct-Access     ATA      ST3250824AS      3.AA PQ: 0 ANSI: 5
[    7.667504] ACPI: PCI Interrupt 0000:00:13.5[D] -> GSI 19 (level, low) -> IRQ 21
[    7.667520] ehci_hcd 0000:00:13.5: EHCI Host Controller
[    7.667664] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 6
[    7.667709] ehci_hcd 0000:00:13.5: debug port 1
[    7.667727] ehci_hcd 0000:00:13.5: irq 21, io mem 0xfebff800
[    7.667739] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    7.668823] usb usb6: configuration #1 chosen from 1 choice
[    7.668981] hub 6-0:1.0: USB hub found
[    7.668989] hub 6-0:1.0: 10 ports detected
[    7.704884] usbcore: registered new interface driver hiddev
[    7.705246] usb 1-1: USB disconnect, address 2
[    7.709459] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[    7.709478] sda: Write Protect is off
[    7.709481] sda: Mode Sense: 00 3a 00 00
[    7.709501] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.709560] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[    7.709574] sda: Write Protect is off
[    7.709577] sda: Mode Sense: 00 3a 00 00
[    7.709596] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.709602]  sda: sda1 sda2 sda3
[    7.735201] sd 0:0:0:0: Attached scsi disk sda
[    7.739267] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    7.789005] hda: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[    7.789018] Uniform CD-ROM driver Revision: 3.20
[    7.835209] usb 4-1: USB disconnect, address 2
[    7.836574] usbcore: registered new interface driver usbhid
[    7.836578] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[    7.918019] Attempting manual resume
[    7.918024] swsusp: Resume From Partition 8:2
[    7.918026] PM: Checking swsusp image.
[    7.918176] PM: Resume from disk failed.
[    7.950932] kjournald starting.  Commit interval 5 seconds
[    7.950957] EXT3-fs: mounted filesystem with ordered data mode.
[    8.328020] usbcore: registered new interface driver libusual
[    8.644250] usb 1-1: new low speed USB device using ohci_hcd and address 3
[    8.865772] usb 1-1: configuration #1 chosen from 1 choice
[    8.873771] input: Logitech USB-PS/2 Optical Mouse as /class/input/input2
[    8.873794] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:13.0-1
[    9.188347] usb 4-1: new full speed USB device using ohci_hcd and address 3
[    9.409276] usb 4-1: configuration #1 chosen from 1 choice
[    9.700968] Initializing USB Mass Storage driver...
[    9.701073] scsi4 : SCSI emulation for USB Mass Storage devices
[    9.701139] usb-storage: device found at 3
[    9.701144] usbcore: registered new interface driver usb-storage
[    9.701150] USB Mass Storage support registered.
[    9.701156] usb-storage: waiting for device to settle before scanning
[   14.697313] usb-storage: device scan complete
[   14.703971] scsi 4:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[   14.710302] scsi 4:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[   14.715302] scsi 4:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[   14.721295] scsi 4:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[   14.731598] sd 4:0:0:0: Attached scsi removable disk sdb
[   14.731653] sd 4:0:0:0: Attached scsi generic sg1 type 0
[   14.741311] sd 4:0:0:1: Attached scsi removable disk sdc
[   14.741355] sd 4:0:0:1: Attached scsi generic sg2 type 0
[   14.751295] sd 4:0:0:2: Attached scsi removable disk sdd
[   14.751335] sd 4:0:0:2: Attached scsi generic sg3 type 0
[   14.761294] sd 4:0:0:3: Attached scsi removable disk sde
[   14.761338] sd 4:0:0:3: Attached scsi generic sg4 type 0
[   16.441941] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   16.472448] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.501975] Linux agpgart interface v0.102 (c) Dave Jones
[   16.872188] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 19 (level, low) -> IRQ 21
[   16.872205] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   16.872242] sky2 0000:02:00.0: v1.13 addr 0xfe9fc000 irq 21 Yukon-EC Ultra (0xb4) rev 2
[   16.872371] sky2 eth0: addr 00:19:21:ab:9f:40
[   16.890016] input: PC Speaker as /class/input/input3
[   16.971822] parport: PnPBIOS parport detected.
[   16.971927] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   16.989493] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 20 (level, low) -> IRQ 22
[   16.989500] rt61 1.1.0 CVS CVS http://rt2x00.serialmonkey.com
[   16.989508] RT61: Vendor = 0x1814, Product = 0x0301 
[   17.044199] RT61: RfIcType= 3
[   17.070197] nvidia: module license 'NVIDIA' taints kernel.
[   17.323330] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   17.323343] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   17.323636] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
[   17.413105] NET: Registered protocol family 10
[   17.413209] lo: Disabled Privacy Extensions
[   17.516805] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16
[   17.715476] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   20.481965] lp0: using parport0 (interrupt-driven).
[   20.532456] Adding 4000176k swap on /dev/disk/by-uuid/e62482c7-b966-4fea-8d36-88e39cc138c0.  Priority:-1 extents:1 across:4000176k
[   20.636126] EXT3 FS on sda1, internal journal
[   20.853711] kjournald starting.  Commit interval 5 seconds
[   20.854016] EXT3 FS on sda3, internal journal
[   20.854025] EXT3-fs: mounted filesystem with ordered data mode.
[   21.306912] Using specific hotkey driver
[   21.366635] No dock devices found.
[   21.437013] ibm_acpi: ec object not found
[   21.480669] input: Power Button (FF) as /class/input/input4
[   21.480704] ACPI: Power Button (FF) [PWRF]
[   21.480774] input: Power Button (CM) as /class/input/input5
[   21.480798] ACPI: Power Button (CM) [PWRB]
[   21.535207] pcc_acpi: loading...
[   22.816334] sky2 eth0: enabling interface
[   22.819566] sky2 eth0: ram buffer 0K
[   22.819889] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.129389] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   26.129397] apm: disabled - APM is not SMP safe.
[   27.777933] ra0: no IPv6 routers present
[   30.251116] hda-intel: Invalid position buffer, using LPIB read method instead.
[/HTML]

dmesg
[HTML]00:00.0 Host bridge [0600]: ATI Technologies Inc Radeon Xpress 200 Host Bridge [1002:5a33] (rev 01)
	Subsystem: Elitegroup Computer Systems Unknown device [1019:2182]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
	Latency: 64
	Region 3: Memory at <ignored> (64-bit, non-prefetchable)

00:02.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI-X Root Port [1002:5a34] (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Memory behind bridge: fa800000-fe8fffff
	Prefetchable memory behind bridge: 00000000bff00000-00000000dfefffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity+ SERR+ NoISA- VGA+ MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:07.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a39] (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: fe900000-fe9fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity+ SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:12.0 SATA controller [0106]: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380] (prog-if 01 [AHCI 1.0])
	Subsystem: Elitegroup Computer Systems Unknown device [1019:4380]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 20
	Region 0: I/O ports at e800 [size=8]
	Region 1: I/O ports at e400 [size=4]
	Region 2: I/O ports at e000 [size=8]
	Region 3: I/O ports at dc00 [size=4]
	Region 4: I/O ports at d800 [size=16]
	Region 5: Memory at febffc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:13.0 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI0) [1002:4387] (prog-if 10 [OHCI])
	Subsystem: Elitegroup Computer Systems Unknown device [1019:2182]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at febfe000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:13.1 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI1) [1002:4388] (prog-if 10 [OHCI])
	Subsystem: Elitegroup Computer Systems Unknown device [1019:2182]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 17
	Region 0: Memory at febfd000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:13.2 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI2) [1002:4389] (prog-if 10 [OHCI])
	Subsystem: Elitegroup Computer Systems Unknown device [1019:2182]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin C routed to IRQ 18
	Region 0: Memory at febfc000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:13.3 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI3) [1002:438a] (prog-if 10 [OHCI])
	Subsystem: Elitegroup Computer Systems Unknown device [1019:2182]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 17
	Region 0: Memory at febfb000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:13.4 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI4) [1002:438b] (prog-if 10 [OHCI])
	Subsystem: Elitegroup Computer Systems Unknown device [1019:2182]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin C routed to IRQ 18
	Region 0: Memory at febfa000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:13.5 USB Controller [0c03]: ATI Technologies Inc SB600 USB Controller (EHCI) [1002:4386] (prog-if 20 [EHCI])
	Subsystem: Elitegroup Computer Systems Unknown device [1019:2182]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64, Cache Line Size: 128 bytes
	Interrupt: pin D routed to IRQ 21
	Region 0: Memory at febff800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:14.0 SMBus [0c05]: ATI Technologies Inc SB600 SMBus [1002:4385] (rev 13)
	Subsystem: Elitegroup Computer Systems Unknown device [1019:2182]
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Region 0: I/O ports at 0b00 [size=16]
	Region 1: Memory at 50000000 (32-bit, non-prefetchable) [size=1K]

00:14.1 IDE interface [0101]: ATI Technologies Inc SB600 IDE [1002:438c] (prog-if 8a [Master SecP PriP])
	Subsystem: Elitegroup Computer Systems Unknown device [1019:2182]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: I/O ports at 01f0 [size=8]
	Region 1: I/O ports at 03f4 [size=1]
	Region 2: I/O ports at 0170 [size=8]
	Region 3: I/O ports at 0374 [size=1]
	Region 4: I/O ports at ff00 [size=16]
	Capabilities: <access denied>

00:14.2 Audio device [0403]: ATI Technologies Inc SB600 Azalia [1002:4383]
	Subsystem: Elitegroup Computer Systems Unknown device [1019:2182]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin ? routed to IRQ 16
	Region 0: Memory at febf4000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:14.3 ISA bridge [0601]: ATI Technologies Inc SB600 PCI to LPC Bridge [1002:438d]
	Subsystem: Elitegroup Computer Systems Unknown device [1019:2182]
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0

00:14.4 PCI bridge [0604]: ATI Technologies Inc SB600 PCI to PCI Bridge [1002:4384] (prog-if 01 [Subtractive decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=64
	Memory behind bridge: fea00000-feafffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity+ SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-

01:00.0 VGA compatible controller [0300]: nVidia Corporation Unknown device [10de:01d3] (rev a1) (prog-if 00 [VGA])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Region 1: Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Region 3: Memory at fc000000 (64-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at fe8e0000 [disabled] [size=128K]
	Capabilities: <access denied>

02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Unknown device [11ab:4364] (rev 12)
	Subsystem: Elitegroup Computer Systems Unknown device [1019:8056]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 21
	Region 0: Memory at fe9fc000 (64-bit, non-prefetchable) [size=16K]
	Region 2: I/O ports at b800 [size=256]
	Expansion ROM at fe9c0000 [disabled] [size=128K]
	Capabilities: <access denied>

03:01.0 Network controller [0280]: RaLink RT2561/RT61 802.11g PCI [1814:0301]
	Subsystem: Linksys WMP54G ver 4.1 [1737:0055]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 22
	Region 0: Memory at feaf8000 (32-bit, non-prefetchable) [size=32K]
	Capabilities: <access denied>

03:04.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) [104c:8024] (prog-if 10 [OHCI])
	Subsystem: Elitegroup Computer Systems Unknown device [1019:2182]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64 (500ns min, 1000ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 19
	Region 0: Memory at feaf7800 (32-bit, non-prefetchable) [size=2K]
	Region 1: Memory at feaf0000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
[/HTML]

lsmod
[HTML]Module                  Size  Used by
binfmt_misc            12680  1 
acpi_cpufreq           10056  0 
cpufreq_conservative     8200  0 
cpufreq_stats           7360  0 
cpufreq_ondemand        9228  2 
cpufreq_userspace       5408  0 
cpufreq_powersave       2688  0 
freq_table              5792  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
dev_acpi               12292  0 
pcc_acpi               13184  0 
sony_acpi               6284  0 
tc1100_wmi              8068  0 
button                  8720  0 
ac                      6020  0 
container               5248  0 
dock                   10268  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
battery                10756  0 
video                  16388  0 
sbs                    15652  0 
i2c_ec                  6016  1 sbs
sbp2                   23812  0 
lp                     12452  0 
snd_hda_intel          21912  1 
snd_hda_codec         205056  1 snd_hda_intel
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  2 snd_pcm_oss
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
ipv6                  268960  10 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
nvidia               4713780  22 
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
rt61                  245128  1 
parport_pc             36388  1 
parport                36936  2 lp,parport_pc
serio_raw               7940  0 
psmouse                38920  0 
i2c_core               22656  2 i2c_ec,nvidia
pcspkr                  4224  0 
snd                    54020  10 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sky2                   43528  0 
soundcore               8672  2 snd
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
ati_agp                10124  0 
agpgart                35400  2 nvidia,ati_agp
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
tsdev                   8768  0 
evdev                  11008  3 
usb_storage            72256  0 
ext3                  133128  2 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
ide_cd                 32672  0 
cdrom                  37664  1 ide_cd
ata_generic             9092  0 
sg                     36252  0 
libusual               17936  1 usb_storage
sd_mod                 23428  4 
usbhid                 26592  0 
hid                    27392  1 usbhid
atiixp                  7440  0 [permanent]
ahci                   22020  3 
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
ehci_hcd               34188  0 
generic                 5124  0 [permanent]
libata                125720  2 ata_generic,ahci
scsi_mod              142348  5 sbp2,usb_storage,sg,sd_mod,libata
ohci_hcd               22532  0 
usbcore               134280  6 usb_storage,libusual,usbhid,ehci_hcd,ohci_hcd
thermal                14856  0 
processor              31048  2 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability[/HTML]

Gràcies per avançat a qualsevol ajuda!

He postejat en aquest forum donat que el pc és una compra de PcGreen i potser hi ha més gent de la zona interessats.

Salut!

---

### Post by papapep on 2007-07-28
I amb el kernel 2.6.20-15 també et passava?? Per què l'has actualitzat?

---

### Post by patrickfromspain on 2007-07-28
l'ha actualitzat perque es una actualitzacio de seguretat i, si no toques res, s'actualitza automaticament.

Omple un bug al launchap i, si el 2.6.20-15 no to feia, torna'l a fer servir.

salut!

---

### Post by pepus on 2007-07-29
Hola gent, merci per les respostes!

He actualitzat el kernel perquè estava disponible quan vaig instal·lar-hi Ubuntu ara farà cosa d'un mes. No he funcionat mai amb el kernel 2.6.20-15, però 

Si de cas, provaré una temporada el 2.6.20-15 a veure com actua.

Per cert, una amiga amb el mateix ordinador també li passa exactament el mateix (també té el nou kernel) així que almenys podem descartar un error de Hardware.

Salutacions!

---

### Post by pepus on 2007-08-10
Sembla ser que tot té a veure amb aquest fil de discussió!

[http://www.nvnews.net/vbulletin/showthread.php?t=87918](http://www.nvnews.net/vbulletin/showthread.php?t=87918)

El problema sembla estar amb la combinació de la tarja gràfica nvidia 7300 i el chipset ATI rs480.


Aquesta tarda provaré a aplicar el patch als drivers de nvidia i a veure què passa.

Salut i merci per les respostes!

---

