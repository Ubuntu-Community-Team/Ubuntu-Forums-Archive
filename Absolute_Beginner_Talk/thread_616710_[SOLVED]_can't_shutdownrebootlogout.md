---
title: "[SOLVED] can't shutdown/reboot/logout"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by banda on 2007-11-18
i seem to have lost the ability to shutdown/reboot/logout. every time i click on the quit button , the ui hangs.. i can move my mouse but cant click anything. 
i am using gutsy with gnome.
ctrl+alt+del does not work either, i have to ctrl+alt+backspace each time to logout and then sutdown from the welcome screen
i am not using compiz

---

### Post by gabrielgmendonca on 2007-11-19
I have exactly the same problem, but I'm using compiz.

---

### Post by banda on 2007-11-19
bump

---

### Post by jaybombalous on 2007-11-19
Do u get an error when it boots up, something about HAL? Last time I had the UI hang due to the logout button was because HAL was not initialized. Maybe HAL is messed up.


H ardware
A bstract
L ayer

---

### Post by banda on 2007-11-19
these are the messages i get durring boot...

> [    0.000000] Linux version 2.6.22-12-generic (buildd@vernadsky) (gcc version 4.1.3 20070831 (prerelease) (Ubuntu 4.1.2-16ubuntu1)) #1 SMP Sun Sep 23 18:11:30 GMT 2007 (Ubuntu 2.6.22-12.39-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fef0000 (usable)
[    0.000000]  BIOS-e820: 000000001fef0000 - 000000001fef3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001fef3000 - 000000001ff00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 510MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f6060
[    0.000000] Entering add_active_range(0, 0, 130800) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   130800
[    0.000000]   HighMem    130800 ->   130800
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   130800
[    0.000000] On node 0 totalpages: 130800
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 989 pages used for memmap
[    0.000000]   Normal zone: 125715 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP 000F7ED0, 0014 (r0 ATi   )
[    0.000000] ACPI: RSDT 1FEF3040, 0038 (r1 ATi    AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 1FEF30C0, 0074 (r1 ATi    AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 1FEF3180, 3782 (r1 ATI    AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 1FEF0000, 0040
[    0.000000] ACPI: MCFG 1FEF6A80, 003C (r1 ATi    AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: APIC 1FEF6980, 0084 (r1 ATi    AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: SSDT 1FEF6B00, 015C (r1 ATI     Cpu0Ist     3000 INTL 20040311)
[    0.000000] ACPI: SSDT 1FEF6F90, 0275 (r1 ATI       CpuPm     3000 INTL 20040311)
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:4 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:4 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1ff00000:c0100000)
[    0.000000] Built 1 zonelists.  Total pages: 129779
[    0.000000] Kernel command line: root=UUID=30dfb32c-8206-4722-b22c-ba6680834916 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 3000.494 MHz processor.
[   32.059841] Console: colour VGA+ 80x25
[   32.060255] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   32.060547] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   32.070390] Memory: 506892k/523200k available (2017k kernel code, 15768k reserved, 918k data, 364k init, 0k highmem)
[   32.070400] virtual kernel memory layout:
[   32.070401]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   32.070402]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   32.070404]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   32.070405]     lowmem  : 0xc0000000 - 0xdfef0000   ( 510 MB)
[   32.070406]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   32.070407]       .data : 0xc02f8456 - 0xc03ddea4   ( 918 kB)
[   32.070408]       .text : 0xc0100000 - 0xc02f8456   (2017 kB)
[   32.070411] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   32.070450] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   32.150407] Calibrating delay using timer specific routine.. 6007.55 BogoMIPS (lpj=12015113)
[   32.150433] Security Framework v1.0.0 initialized
[   32.150437] SELinux:  Disabled at boot.
[   32.150450] Mount-cache hash table entries: 512
[   32.150574] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000649d 00000000 00000000
[   32.150583] monitor/mwait feature present.
[   32.150585] using mwait in idle threads.
[   32.150592] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   32.150595] CPU: L2 cache: 2048K
[   32.150598] CPU: Physical Processor ID: 0
[   32.150600] CPU: After all inits, caps: bfebfbff 20100000 00000000 0000b180 0000649d 00000000 00000000
[   32.150610] Compat vDSO mapped to ffffe000.
[   32.150625] Checking 'hlt' instruction... OK.
[   32.166493] SMP alternatives: switching to UP code
[   32.166905] Early unpacking initramfs... done
[   32.461251] ACPI: Core revision 20070126
[   32.461313] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   32.486977] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 03
[   32.487004] SMP alternatives: switching to SMP code
[   32.487155] Booting processor 1/1 eip 3000
[   32.497476] Initializing CPU#1
[   32.578026] Calibrating delay using timer specific routine.. 6000.69 BogoMIPS (lpj=12001391)
[   32.578038] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000649d 00000000 00000000
[   32.578045] monitor/mwait feature present.
[   32.578052] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   32.578056] CPU: L2 cache: 2048K
[   32.578058] CPU: Physical Processor ID: 0
[   32.578061] CPU: After all inits, caps: bfebfbff 20100000 00000000 0000b180 0000649d 00000000 00000000
[   32.578594] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 03
[   32.578640] Total of 2 processors activated (12008.25 BogoMIPS).
[   32.578814] ENABLING IO-APIC IRQs
[   32.579017] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   32.726023] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   32.746022] Brought up 2 CPUs
[   33.064358] migration_cost=163
[   33.064557] Booting paravirtualized kernel on bare hardware
[   33.064648] Time: 17:28:02  Date: 10/19/107
[   33.064676] NET: Registered protocol family 16
[   33.064777] EISA bus registered
[   33.064783] ACPI: bus type pci registered
[   33.066662] PCI: PCI BIOS revision 3.00 entry at 0xf1df0, last bus=2
[   33.066665] PCI: Using configuration type 1
[   33.066667] Setting up standard PCI resources
[   33.073079] ACPI: EC: Look up EC in DSDT
[   33.076806] ACPI: Interpreter enabled
[   33.076810] ACPI: (supports S0 S3 S4 S5)
[   33.076830] ACPI: Using IOAPIC for interrupt routing
[   33.081238] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   33.081261] PCI: Probing PCI hardware (bus 00)
[   33.082634] PCI: Transparent bridge - 0000:00:14.4
[   33.082682] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   33.082874] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   33.092269] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   33.092376] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   33.092481] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   33.092585] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   33.092689] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   33.092793] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 10 11)
[   33.092896] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *10 11)
[   33.093000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11)
[   33.093114] Linux Plug and Play Support v0.97 (c) Adam Belay
[   33.093126] pnp: PnP ACPI init
[   33.093135] ACPI: bus type pnp registered
[   33.095641] pnp: PnP ACPI: found 12 devices
[   33.095643] ACPI: ACPI bus type pnp unregistered
[   33.095648] PnPBIOS: Disabled by ACPI PNP
[   33.095711] PCI: Using ACPI for IRQ routing
[   33.095715] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   33.095723] PCI: Cannot allocate resource region 3 of device 0000:00:00.0
[   33.165710] NET: Registered protocol family 8
[   33.165713] NET: Registered protocol family 20
[   33.165780] pnp: 00:01: ioport range 0x228-0x22f has been reserved
[   33.165783] pnp: 00:01: ioport range 0x40b-0x40b has been reserved
[   33.165786] pnp: 00:01: ioport range 0x4d6-0x4d6 has been reserved
[   33.165789] pnp: 00:01: ioport range 0xc00-0xc01 has been reserved
[   33.165791] pnp: 00:01: ioport range 0xc14-0xc14 has been reserved
[   33.165794] pnp: 00:01: ioport range 0xc50-0xc52 has been reserved
[   33.165797] pnp: 00:01: ioport range 0xc6c-0xc6d has been reserved
[   33.165799] pnp: 00:01: ioport range 0xc6f-0xc6f has been reserved
[   33.165812] pnp: 00:0a: iomem range 0xe0000000-0xefffffff could not be reserved
[   33.165820] pnp: 00:0b: iomem range 0xf0000-0xf3fff could not be reserved
[   33.165823] pnp: 00:0b: iomem range 0xf4000-0xf7fff could not be reserved
[   33.165826] pnp: 00:0b: iomem range 0xf8000-0xfbfff could not be reserved
[   33.165828] pnp: 00:0b: iomem range 0xfc000-0xfffff could not be reserved
[   33.169522] Time: tsc clocksource has been installed.
[   33.196193] PCI: Bridge: 0000:00:02.0
[   33.196197]   IO window: e000-efff
[   33.196201]   MEM window: fa000000-fcffffff
[   33.196205]   PREFETCH window: d0000000-dfffffff
[   33.196210] PCI: Bridge: 0000:00:14.4
[   33.196214]   IO window: d000-dfff
[   33.196221]   MEM window: fdd00000-fddfffff
[   33.196227]   PREFETCH window: fde00000-fdefffff
[   33.196245] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   33.196264] NET: Registered protocol family 2
[   33.233506] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   33.233547] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[   33.233668] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   33.233738] TCP: Hash tables configured (established 16384 bind 16384)
[   33.233741] TCP reno registered
[   33.245618] checking if image is initramfs... it is
[   33.693208] Switched to high resolution mode on CPU 1
[   33.697068] Switched to high resolution mode on CPU 0
[   33.827639] Freeing initrd memory: 7359k freed
[   33.828346] audit: initializing netlink socket (disabled)
[   33.828368] audit(1195493281.452:1): initialized
[   33.830913] VFS: Disk quotas dquot_6.5.1
[   33.830980] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   33.831094] io scheduler noop registered
[   33.831097] io scheduler anticipatory registered
[   33.831099] io scheduler deadline registered
[   33.831115] io scheduler cfq registered (default)
[   33.831134] PCI: MSI quirk detected. MSI deactivated.
[   33.908897] Boot video device is 0000:01:00.0
[   33.909007] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   33.909046] assign_interrupt_mode Found MSI capability
[   33.909049] Allocate Port Service[0000:00:02.0:pcie00]
[   33.909271] isapnp: Scanning for PnP cards...
[   34.261054] isapnp: No Plug & Play device found
[   34.289111] Real Time Clock Driver v1.12ac
[   34.289227] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   34.289380] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   34.290110] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   34.290953] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   34.291221] input: Macintosh mouse button emulation as /class/input/input0
[   34.291313] PNP: PS/2 Controller [PNP0f13:PS2M] at 0x60,0x64 irq 12
[   34.291316] PNP: PS/2 controller doesn't have KBD irq; using default 1
[   34.294153] serio: i8042 KBD port at 0x60,0x64 irq 1
[   34.294160] serio: i8042 AUX port at 0x60,0x64 irq 12
[   34.294348] mice: PS/2 mouse device common for all mice
[   34.294481] EISA: Probing bus 0 at eisa.0
[   34.294506] Cannot allocate resource for EISA slot 4
[   34.294529] EISA: Detected 0 cards.
[   34.294631] TCP cubic registered
[   34.294644] NET: Registered protocol family 1
[   34.294668] Using IPI No-Shortcut mode
[   34.294857]   Magic number: 15:188:492
[   34.295434] Freeing unused kernel memory: 364k freed
[   35.494330] AppArmor: AppArmor initialized<5>audit(1195493282.952:2):  type=1505 info="AppArmor initialized" pid=1192
[   35.500605] fuse init (API version 7.8)
[   35.506313] Failure registering capabilities with primary security module.
[   35.530997] ACPI: Fan [FAN] (on)
[   35.535539] ACPI: Processor [CPU0] (supports 8 throttling states)
[   35.535689] ACPI: SSDT 1FEF6F00, 0087 (r1 ATI     Cpu1Ist     3000 INTL 20040311)
[   35.535811] ACPI: Processor [CPU1] (supports 8 throttling states)
[   35.535827] ACPI Exception (processor_core-0781): AE_NOT_FOUND, Processor Device is not present [20070126]
[   35.535840] ACPI Exception (processor_core-0781): AE_NOT_FOUND, Processor Device is not present [20070126]
[   35.539008] ACPI: Thermal Zone [THRM] (40 C)
[   36.027174] usbcore: registered new interface driver usbfs
[   36.027222] usbcore: registered new interface driver hub
[   36.027273] usbcore: registered new device driver usb
[   36.028679] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   36.028765] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 16
[   36.028786] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   36.029018] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   36.029045] ohci_hcd 0000:00:13.0: irq 16, io mem 0xfe02d000
[   36.040032] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   36.040039] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   36.091190] usb usb1: configuration #1 chosen from 1 choice
[   36.091234] hub 1-0:1.0: USB hub found
[   36.091251] hub 1-0:1.0: 4 ports detected
[   36.178294] SCSI subsystem initialized
[   36.191006] libata version 2.21 loaded.
[   36.195412] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 16
[   36.195431] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   36.195626] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   36.195648] ohci_hcd 0000:00:13.1: irq 16, io mem 0xfe02c000
[   36.207998] 8139too Fast Ethernet driver 0.9.28
[   36.254944] usb usb2: configuration #1 chosen from 1 choice
[   36.254989] hub 2-0:1.0: USB hub found
[   36.255004] hub 2-0:1.0: 4 ports detected
[   36.358995] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 16
[   36.359014] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   36.359050] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   36.359119] ehci_hcd 0000:00:13.2: irq 16, io mem 0xfe02b000
[   36.359134] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   36.359241] usb usb3: configuration #1 chosen from 1 choice
[   36.359286] hub 3-0:1.0: USB hub found
[   36.359295] hub 3-0:1.0: 8 ports detected
[   36.462844] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[   36.462886] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 17
[   36.462906] ATIIXP: chipset revision 128
[   36.462910] ATIIXP: not 100% native mode: will probe irqs later
[   36.462924]     ide0: BM-DMA at 0xf400-0xf407, BIOS settings: hda:pio, hdb:pio
[   36.462945]     ide1: BM-DMA at 0xf408-0xf40f, BIOS settings: hdc:pio, hdd:pio
[   36.462960] Probing IDE interface ide0...
[   36.750828] hda: ST3120213A, ATA DISK drive
[   37.030587] hdb: SAMSUNG SV2011H, ATA DISK drive
[   37.086123] hda: selected mode 0x45
[   37.086446] hdb: selected mode 0x45
[   37.086564] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   37.104982] Probing IDE interface ide1...
[   37.473763] usb 3-4: new high speed USB device using ehci_hcd and address 4
[   37.606630] usb 3-4: configuration #1 chosen from 1 choice
[   37.837912] hdc: SONY DVD RW DRU-830A, ATAPI CD/DVD-ROM drive
[   37.909386] usb 1-1: new full speed USB device using ohci_hcd and address 3
[   38.116261] usb 1-1: configuration #1 chosen from 1 choice
[   38.420939] usb 2-1: new low speed USB device using ohci_hcd and address 2
[   38.621216] hdd: HL-DT-ST GCE-8526B, ATAPI CD/DVD-ROM drive
[   38.624746] usb 2-1: configuration #1 chosen from 1 choice
[   38.626954] usbcore: registered new interface driver libusual
[   38.647917] usbcore: registered new interface driver hiddev
[   38.650888] Initializing USB Mass Storage driver...
[   38.651030] scsi0 : SCSI emulation for USB Mass Storage devices
[   38.651097] usb-storage: device found at 4
[   38.651102] usb-storage: waiting for device to settle before scanning
[   38.653855] input: HID 0566:3002 as /class/input/input1
[   38.653875] input: USB HID v1.10 Keyboard [HID 0566:3002] on usb-0000:00:13.1-1
[   38.667646] input: HID 0566:3002 as /class/input/input2
[   38.667706] input,hiddev96: USB HID v1.10 Device [HID 0566:3002] on usb-0000:00:13.1-1
[   38.667735] usbcore: registered new interface driver usb-storage
[   38.667740] USB Mass Storage support registered.
[   38.667873] usbcore: registered new interface driver usbhid
[   38.667878] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   38.676750] hdc: drive side 80-wire cable detection failed, limiting max speed to UDMA33
[   38.676757] hdc: selected mode 0x42
[   38.677502] hdd: selected mode 0x42
[   38.677689] ide1 at 0x170-0x177,0x376 on irq 15
[   38.682886] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 21 (level, low) -> IRQ 18
[   38.683576] eth0: RealTek RTL8139 at 0xe0854000, 00:16:76:18:2f:f1, IRQ 18
[   38.683578] eth0:  Identified 8139 chip type 'RTL-8101'
[   38.686099] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   38.690321] sata_sil 0000:00:11.0: version 2.2
[   38.690383] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 23 (level, low) -> IRQ 19
[   38.690837] scsi1 : sata_sil
[   38.690906] scsi2 : sata_sil
[   38.690965] ata1: SATA max UDMA/100 cmd 0xe0864080 ctl 0xe086408a bmdma 0xe0864000 irq 19
[   38.690974] ata2: SATA max UDMA/100 cmd 0xe08640c0 ctl 0xe08640ca bmdma 0xe0864008 irq 19
[   38.710629] hdc: ATAPI 40X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   38.710644] Uniform CD-ROM driver Revision: 3.20
[   38.713310] hda: max request size: 512KiB
[   38.715701] hdd: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   38.746322] hda: 234441648 sectors (120034 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[   38.770031] hda: cache flushes supported
[   38.770078]  hda: hda1 hda2
[   38.793758] hdb: max request size: 128KiB
[   38.794145] hdb: 39179952 sectors (20060 MB) w/2048KiB Cache, CHS=38869/16/63, UDMA(100)
[   38.794547] hdb: cache flushes supported
[   38.794571]  hdb: hdb1 hdb2 < hdb5 >
[   39.000443] ata1: SATA link down (SStatus 0 SControl 310)
[   39.312179] ata2: SATA link down (SStatus 0 SControl 310)
[   39.312306] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 20
[   39.312383] scsi3 : sata_sil
[   39.312461] scsi4 : sata_sil
[   39.312510] ata3: SATA max UDMA/100 cmd 0xe086a080 ctl 0xe086a08a bmdma 0xe086a000 irq 20
[   39.312518] ata4: SATA max UDMA/100 cmd 0xe086a0c0 ctl 0xe086a0ca bmdma 0xe086a008 irq 20
[   39.431293] Attempting manual resume
[   39.431298] swsusp: Resume From Partition 3:69
[   39.431300] PM: Checking swsusp image.
[   39.431491] PM: Resume from disk failed.
[   39.453383] kjournald starting.  Commit interval 5 seconds
[   39.453398] EXT3-fs: mounted filesystem with ordered data mode.
[   39.623901] ata3: SATA link down (SStatus 0 SControl 310)
[   39.935626] ata4: SATA link down (SStatus 0 SControl 310)
[   43.644554] usb-storage: device scan complete
[   43.646419] scsi 0:0:0:0: Direct-Access     HTS42404 0M9AT00          MA2O PQ: 0 ANSI: 0 CCS
[   51.189088] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   51.207330] Linux agpgart interface v0.102 (c) Dave Jones
[   51.286753] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   51.371477] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   51.531134] input: PC Speaker as /class/input/input3
[   51.856212] usbcore: registered new interface driver xpad
[   51.856219] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[   51.978364] nvidia: module license 'NVIDIA' taints kernel.
[   52.239985] Linux video capture interface: v2.00
[   52.254041] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 18 (level, low) -> IRQ 21
[   52.254055] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   52.254284] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
[   52.278833] /home/name/trunk/ov51x-jpeg-core.c: USB OV519 video device found
[   52.317461] input: ImPS/2 Logitech Wheel Mouse as /class/input/input4
[   52.320502] parport_pc 00:08: reported by Plug and Play ACPI
[   52.320586] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   52.332003] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[   52.332621] sd 0:0:0:0: [sda] Write Protect is off
[   52.332625] sd 0:0:0:0: [sda] Mode Sense: 00 14 00 00
[   52.332629] sd 0:0:0:0: [sda] Assuming drive cache: write through
[   52.425693] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[   52.442736] sd 0:0:0:0: [sda] Write Protect is off
[   52.442743] sd 0:0:0:0: [sda] Mode Sense: 00 14 00 00
[   52.442748] sd 0:0:0:0: [sda] Assuming drive cache: write through
[   52.442758]  sda:<6>ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 17
[   52.691423] /home/name/trunk/ov51x-jpeg-core.c: Sensor is an OV7670
[   52.793287]  sda1 sda2
[   52.793763] sd 0:0:0:0: [sda] Attached SCSI disk
[   52.813924] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   53.948287] /home/name/trunk/ov51x-jpeg-core.c: Device at usb-0000:00:13.0-1 registered to minor 0
[   53.948347] usbcore: registered new interface driver ov51x
[   53.948355] /home/name/trunk/ov51x-jpeg-core.c: 1.5.2+svn : ov51x USB Camera Driver
[   54.101877] lp0: using parport0 (interrupt-driven).
[   54.148742] Adding 859436k swap on /dev/hdb5.  Priority:-1 extents:1 across:859436k
[   54.608232] EXT3 FS on hdb1, internal journal
[   57.748267] Failure registering capabilities with primary security module.
[   58.101518] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  106.794185] hda-intel: Invalid position buffer, using LPIB read method instead.
[  302.004111] NET: Registered protocol family 10
[  302.004443] lo: Disabled Privacy Extensions
[  312.674430] eth0: no IPv6 routers present


---

### Post by rondamato on 2007-11-19
Hello there,

You didn't mention one thing...can you shutdown/reboot from console?  This would help in troubleshooting your problem.

Try:

sudo shutdown now

and see what happens.  Then we can go from there hopefully.

Good luck!

(The Good) DoctorRon
Chicago, IL
<rondamato@gmail.com>
v7.10 Gutsy Gibbon 32-bit/Gnome

---

### Post by badguyanil on 2007-11-19
check this thread out (last page) ! Same problem and solved! (May be your case is diff...check it anyways!)

> [http://ubuntuforums.org/showthread.php?t=608361](http://ubuntuforums.org/showthread.php?t=608361)

---

### Post by banda on 2008-01-29
this problem is sorted out by re-enabling power manager under system>preferences>sessions

---

