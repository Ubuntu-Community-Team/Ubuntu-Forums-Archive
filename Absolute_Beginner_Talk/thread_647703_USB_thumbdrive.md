---
title: "USB thumbdrive"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by misterz on 2007-12-22
When I plug the thumbrive into any USB port, nothing happens. I see a single flash on the drive. What's up?

---

### Post by lgambett on 2007-12-22
From a terminal window give the [COLOR="Black"]lsusb[/COLOR] command and post the result to the forum.

---

### Post by misterz on 2007-12-22
mark@mark-desktop:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by dcstar on 2007-12-22
> **misterz said:**
> When I plug the thumbrive into any USB port, nothing happens. I see a single flash on the drive. What's up?

Open a terminal, enter this after you plug the drive in and post the results:

```
dmesg
```

---

### Post by misterz on 2007-12-22
mark@mark-desktop:~$ dmesg
[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Dec 18 08:02:57 UTC 2007 (Ubuntu 2.6.22-14.47-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009c000 (usable)
[    0.000000]  BIOS-e820: 000000000009c000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000005bef0000 (usable)
[    0.000000]  BIOS-e820: 000000005bef0000 - 000000005bef3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000005bef3000 - 000000005bf00000 (ACPI data)
[    0.000000]  BIOS-e820: 000000005c000000 - 0000000060000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fefffc00 - 00000000ff000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 574MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f3bc0
[    0.000000] Entering add_active_range(0, 0, 376560) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   376560
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   376560
[    0.000000] On node 0 totalpages: 376560
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 1149 pages used for memmap
[    0.000000]   HighMem zone: 146035 pages, LIFO batch:31
[    0.000000] DMI 2.2 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7D40 checksum 0
[    0.000000] ACPI: RSDP 000F7D40, 0014 (r0 Nvidia)
[    0.000000] ACPI: RSDT 5BEF3040, 0030 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 5BEF30C0, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 5BEF3180, 63AC (r1 NVIDIA AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 5BEF0000, 0040
[    0.000000] ACPI: MCFG 5BEF9640, 003C (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: APIC 5BEF9580, 0064 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:12 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 68000000 (gap: 60000000:80000000)
[    0.000000] Built 1 zonelists.  Total pages: 373619
[    0.000000] Kernel command line: root=UUID=23ce20aa-0eb5-47aa-b72f-67b0901af57c ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1607.313 MHz processor.
[   14.683925] spurious 8259A interrupt: IRQ7.
[   14.686956] Console: colour VGA+ 80x25
[   14.687552] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   14.688586] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   14.741648] Memory: 1481448k/1506240k available (2015k kernel code, 23524k reserved, 916k data, 364k init, 588736k highmem)
[   14.741660] virtual kernel memory layout:
[   14.741662]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   14.741663]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   14.741665]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   14.741666]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   14.741668]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   14.741669]       .data : 0xc02f7de6 - 0xc03dce84   ( 916 kB)
[   14.741671]       .text : 0xc0100000 - 0xc02f7de6   (2015 kB)
[   14.741674] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   14.741724] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   14.821742] Calibrating delay using timer specific routine.. 3217.67 BogoMIPS (lpj=6435347)
[   14.821780] Security Framework v1.0.0 initialized
[   14.821788] SELinux:  Disabled at boot.
[   14.821803] Mount-cache hash table entries: 512
[   14.821961] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[   14.821970] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   14.821973] CPU: L2 Cache: 256K (64 bytes/line)
[   14.821977] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001
[   14.821989] Compat vDSO mapped to ffffe000.
[   14.822004] Checking 'hlt' instruction... OK.
[   14.837922] SMP alternatives: switching to UP code
[   14.838194] Freeing SMP alternatives: 11k freed
[   14.838552] Early unpacking initramfs... done
[   15.199022] ACPI: Core revision 20070126
[   15.199113] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   15.203083] CPU0: AMD Sempron(tm) Processor 2800+ stepping 02
[   15.203104] Total of 1 processors activated (3217.67 BogoMIPS).
[   15.203407] ENABLING IO-APIC IRQs
[   15.203656] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[   15.349757] Brought up 1 CPUs
[   15.349900] Booting paravirtualized kernel on bare hardware
[   15.349961] Time: 17:34:53  Date: 11/22/107
[   15.349985] NET: Registered protocol family 16
[   15.350070] EISA bus registered
[   15.350082] ACPI: bus type pci registered
[   15.356748] PCI: PCI BIOS revision 3.00 entry at 0xfa810, last bus=4
[   15.356750] PCI: Using configuration type 1
[   15.356752] Setting up standard PCI resources
[   15.360576] ACPI: EC: Look up EC in DSDT
[   15.367735] ACPI: Interpreter enabled
[   15.367738] ACPI: (supports S0 S1 S4 S5)
[   15.367755] ACPI: Using IOAPIC for interrupt routing
[   15.379640] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   15.379647] PCI: Probing PCI hardware (bus 00)
[   15.380643] PCI: Transparent bridge - 0000:00:10.0
[   15.380688] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   15.381012] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   15.503611] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   15.503825] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   15.504037] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   15.504247] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   15.504458] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   15.504668] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   15.504881] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 *10 11 14 15)
[   15.505091] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   15.505303] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 10 *11 14 15)
[   15.505513] ACPI: PCI Interrupt Link [LUBB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   15.505733] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 *11 14 15)
[   15.505946] ACPI: PCI Interrupt Link [LACI] (IRQs *5 7 9 10 11 14 15)
[   15.506156] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   15.506370] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 *10 11 14 15)
[   15.506581] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   15.506793] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 *10 11 14 15)
[   15.507013] ACPI: PCI Interrupt Link [LUB2] (IRQs *5 7 9 10 11 14 15)
[   15.507229] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   15.507442] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[   15.507699] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[   15.507942] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[   15.508183] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[   15.508424] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[   15.508665] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[   15.508906] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[   15.509147] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0
[   15.509388] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[   15.509629] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[   15.509875] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[   15.510119] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[   15.510361] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0
[   15.510604] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0
[   15.510847] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0, disabled.
[   15.511089] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[   15.511338] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[   15.511581] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[   15.511826] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[   15.512069] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[   15.512315] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[   15.512449] Linux Plug and Play Support v0.97 (c) Adam Belay
[   15.512465] pnp: PnP ACPI init
[   15.512478] ACPI: bus type pnp registered
[   15.519228] pnp: PnP ACPI: found 14 devices
[   15.519232] ACPI: ACPI bus type pnp unregistered
[   15.519237] PnPBIOS: Disabled by ACPI PNP
[   15.519299] PCI: Using ACPI for IRQ routing
[   15.519305] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   15.605116] NET: Registered protocol family 8
[   15.605119] NET: Registered protocol family 20
[   15.605189] pnp: 00:01: ioport range 0x1000-0x107f has been reserved
[   15.605193] pnp: 00:01: ioport range 0x1080-0x10ff has been reserved
[   15.605196] pnp: 00:01: ioport range 0x1400-0x147f has been reserved
[   15.605199] pnp: 00:01: ioport range 0x1480-0x14ff has been reserved
[   15.605203] pnp: 00:01: ioport range 0x1800-0x187f has been reserved
[   15.605206] pnp: 00:01: ioport range 0x1880-0x18ff has been reserved
[   15.605209] pnp: 00:01: ioport range 0x2000-0x207f has been reserved
[   15.605212] pnp: 00:01: ioport range 0x2080-0x20ff has been reserved
[   15.605217] pnp: 00:01: iomem range 0xfefe0000-0xfefe01ff has been reserved
[   15.605220] pnp: 00:01: iomem range 0x5c000000-0x5fffffff could not be reserved
[   15.605234] pnp: 00:0c: iomem range 0xe0000000-0xefffffff could not be reserved
[   15.605237] pnp: 00:0c: iomem range 0xbf00000-0xbffffff could not be reserved
[   15.605241] pnp: 00:0c: iomem range 0x1bf00000-0x1bffffff could not be reserved
[   15.605245] pnp: 00:0c: iomem range 0x2bf00000-0x2bffffff could not be reserved
[   15.605250] pnp: 00:0d: iomem range 0xcde00-0xcffff has been reserved
[   15.605253] pnp: 00:0d: iomem range 0xf0000-0xf7fff could not be reserved
[   15.605257] pnp: 00:0d: iomem range 0xf8000-0xfbfff could not be reserved
[   15.605260] pnp: 00:0d: iomem range 0xfc000-0xfffff could not be reserved
[   15.605693] Time: tsc clocksource has been installed.
[   15.635531] PCI: Bridge: 0000:00:02.0
[   15.635534]   IO window: a000-afff
[   15.635538]   MEM window: fd700000-fd7fffff
[   15.635541]   PREFETCH window: fde00000-fdefffff
[   15.635544] PCI: Bridge: 0000:00:03.0

---

### Post by misterz on 2007-12-22
[   15.635547]   IO window: 9000-9fff
[   15.635550]   MEM window: fdd00000-fddfffff
[   15.635553]   PREFETCH window: fdc00000-fdcfffff
[   15.635556] PCI: Bridge: 0000:00:04.0
[   15.635558]   IO window: b000-bfff
[   15.635562]   MEM window: fd900000-fd9fffff
[   15.635565]   PREFETCH window: fd800000-fd8fffff
[   15.635568] PCI: Bridge: 0000:00:10.0
[   15.635570]   IO window: c000-cfff
[   15.635574]   MEM window: fdb00000-fdbfffff
[   15.635578]   PREFETCH window: fda00000-fdafffff
[   15.635592] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   15.635600] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   15.635607] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   15.635615] PCI: Setting latency timer of device 0000:00:10.0 to 64
[   15.635631] NET: Registered protocol family 2
[   15.673737] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   15.673898] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   15.675967] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   15.676666] TCP: Hash tables configured (established 131072 bind 65536)
[   15.676671] TCP reno registered
[   15.685838] checking if image is initramfs... it is
[   16.137660] Switched to high resolution mode on CPU 0
[   16.391414] Freeing initrd memory: 7060k freed
[   16.391840] audit: initializing netlink socket (disabled)
[   16.391855] audit(1198344893.264:1): initialized
[   16.391924] highmem bounce pool size: 64 pages
[   16.393706] VFS: Disk quotas dquot_6.5.1
[   16.393760] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   16.393867] io scheduler noop registered
[   16.393869] io scheduler anticipatory registered
[   16.393871] io scheduler deadline registered
[   16.393887] io scheduler cfq registered (default)
[   16.393910] Boot video device is 0000:00:05.0
[   24.407961] 0000:00:0b.1 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
[   24.408071] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   24.408097] assign_interrupt_mode Found MSI capability
[   24.408100] Allocate Port Service[0000:00:02.0:pcie00]
[   24.408164] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   24.408189] assign_interrupt_mode Found MSI capability
[   24.408191] Allocate Port Service[0000:00:03.0:pcie00]
[   24.408246] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   24.408270] assign_interrupt_mode Found MSI capability
[   24.408272] Allocate Port Service[0000:00:04.0:pcie00]
[   24.408393] isapnp: Scanning for PnP cards...
[   24.761585] isapnp: No Plug & Play device found
[   24.790561] Real Time Clock Driver v1.12ac
[   24.790669] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   24.790784] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   24.791695] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   24.792474] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   24.792685] input: Macintosh mouse button emulation as /class/input/input0
[   24.792770] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   24.795688] serio: i8042 KBD port at 0x60,0x64 irq 1
[   24.795695] serio: i8042 AUX port at 0x60,0x64 irq 12
[   24.795903] mice: PS/2 mouse device common for all mice
[   24.796020] EISA: Probing bus 0 at eisa.0
[   24.796028] Cannot allocate resource for EISA slot 1
[   24.796031] Cannot allocate resource for EISA slot 2
[   24.796050] EISA: Detected 0 cards.
[   24.796159] TCP cubic registered
[   24.796173] NET: Registered protocol family 1
[   24.796198] Using IPI No-Shortcut mode
[   24.796405]   Magic number: 3:523:593
[   24.796886] Freeing unused kernel memory: 364k freed
[   24.839965] input: AT Translated Set 2 keyboard as /class/input/input1
[   26.061490] AppArmor: AppArmor initialized<5>audit(1198344902.764:2):  type=1505 info="AppArmor initialized" pid=1249
[   26.069392] fuse init (API version 7.8)
[   26.076745] Failure registering capabilities with primary security module.
[   26.088941] ACPI: Fan [FAN] (on)
[   26.095259] ACPI: Processor [CPU0] (supports 8 throttling states)
[   26.096912] ACPI: Thermal Zone [THRM] (40 C)
[   27.038717] usbcore: registered new interface driver usbfs
[   27.038750] usbcore: registered new interface driver hub
[   27.038773] usbcore: registered new device driver usb
[   27.039638] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   27.040114] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
[   27.040127] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [APCF] -> GSI 23 (level, low) -> IRQ 16
[   27.040142] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   27.040146] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[   27.040338] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[   27.040362] ohci_hcd 0000:00:0b.0: irq 16, io mem 0xfe02f000
[   27.061840] SCSI subsystem initialized
[   27.067098] libata version 2.21 loaded.
[   27.097393] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
[   27.109871] usb usb1: configuration #1 chosen from 1 choice
[   27.109901] hub 1-0:1.0: USB hub found
[   27.109913] hub 1-0:1.0: 8 ports detected
[   27.212141] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[   27.212156] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [APCL] -> GSI 22 (level, low) -> IRQ 17
[   27.212170] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[   27.212174] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[   27.212206] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[   27.212240] ehci_hcd 0000:00:0b.1: debug port 1
[   27.212245] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
[   27.212258] ehci_hcd 0000:00:0b.1: irq 17, io mem 0xfe02e000
[   27.212267] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   27.212352] usb usb2: configuration #1 chosen from 1 choice
[   27.212384] hub 2-0:1.0: USB hub found
[   27.212392] hub 2-0:1.0: 8 ports detected
[   27.315673] sata_nv 0000:00:0e.0: version 3.4
[   27.316145] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 21
[   27.316158] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [APSI] -> GSI 21 (level, low) -> IRQ 18
[   27.316213] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   27.316313] scsi0 : sata_nv
[   27.316376] scsi1 : sata_nv
[   27.316449] ata1: SATA max UDMA/133 cmd 0x000109f0 ctl 0x00010bf2 bmdma 0x0001e000 irq 18
[   27.316453] ata2: SATA max UDMA/133 cmd 0x00010970 ctl 0x00010b72 bmdma 0x0001e008 irq 18
[   27.327686] FDC 0 is a post-1991 82077
[   27.627338] ata1: SATA link down (SStatus 0 SControl 300)
[   27.947275] ata2: SATA link down (SStatus 0 SControl 300)
[   27.958817] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 20
[   27.958831] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [APCH] -> GSI 20 (level, low) -> IRQ 19
[   27.958839] PCI: Setting latency timer of device 0000:00:14.0 to 64
[   27.958849] forcedeth: using HIGHDMA
[   28.475735] eth0: forcedeth.c: subsystem: 01565:2501 bound to 0000:00:14.0
[   28.481013] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   28.481021] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   28.483410] NFORCE-MCP51: IDE controller at PCI slot 0000:00:0d.0
[   28.483437] NFORCE-MCP51: chipset revision 161
[   28.483440] NFORCE-MCP51: not 100% native mode: will probe irqs later
[   28.483445] NFORCE-MCP51: BIOS didn't set cable bits correctly. Enabling workaround.
[   28.483451] NFORCE-MCP51: 0000:00:0d.0 (rev a1) UDMA133 controller
[   28.483463]     ide0: BM-DMA at 0xf400-0xf407, BIOS settings: hda:DMA, hdb:DMA
[   28.483475]     ide1: BM-DMA at 0xf408-0xf40f, BIOS settings: hdc:DMA, hdd:DMA
[   28.483485] Probing IDE interface ide0...
[   28.771216] hda: WDC WD400BB-22JHC0, ATA DISK drive
[   29.443118] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   29.452549] Probing IDE interface ide1...
[   30.466888] hdd: LITE-ON COMBO SOHC-5236V, ATAPI CD/DVD-ROM drive
[   30.523335] ide1 at 0x170-0x177,0x376 on irq 15
[   30.540108] hda: max request size: 128KiB
[   30.550020] hda: 78165360 sectors (40020 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[   30.550827] hda: cache flushes supported
[   30.550884]  hda: hda1 hda2 hda3 < hda5 hda6 > hda4
[   30.595424] hdd: ATAPI 52X DVD-ROM CD-R/RW drive, 1536kB Cache, UDMA(44)
[   30.595434] Uniform CD-ROM driver Revision: 3.20
[   31.086398] Attempting manual resume
[   31.086403] swsusp: Resume From Partition 3:6
[   31.086406] PM: Checking swsusp image.
[   31.086601] PM: Resume from disk failed.
[   31.117624] kjournald starting.  Commit interval 5 seconds
[   31.117638] EXT3-fs: mounted filesystem with ordered data mode.
[   38.493253] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   38.498307] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   39.368095] Linux agpgart interface v0.102 (c) Dave Jones
[   39.440134] nvidia: module license 'NVIDIA' taints kernel.
[   39.839718] ACPI: PCI Interrupt Link [APC7] enabled at IRQ 16
[   39.839734] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [APC7] -> GSI 16 (level, low) -> IRQ 20
[   39.839744] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   39.840058] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
[   40.311884] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   40.311915] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x1c40
[   40.317290] input: PC Speaker as /class/input/input2
[   40.776368] input: PS2++ Logitech MX Mouse as /class/input/input3
[   40.781109] parport_pc 00:09: reported by Plug and Play ACPI
[   40.781165] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   40.825228] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 23
[   40.825235] ACPI: PCI Interrupt 0000:00:10.2[C] -> Link [APCJ] -> GSI 23 (level, low) -> IRQ 16
[   40.825259] PCI: Setting latency timer of device 0000:00:10.2 to 64
[   41.148694] intel8x0_measure_ac97_clock: measured 54761 usecs
[   41.148699] intel8x0: clocking to 46938
[   41.435046] lp0: using parport0 (interrupt-driven).
[   41.491322] Adding 321228k swap on /dev/hda6.  Priority:-1 extents:1 across:321228k
[   41.687616] EXT3 FS on hda4, internal journal
[   42.865228] input: Power Button (FF) as /class/input/input4
[   42.870832] ACPI: Power Button (FF) [PWRF]
[   42.913544] input: Power Button (CM) as /class/input/input5
[   42.919146] ACPI: Power Button (CM) [PWRB]
[   42.962467] input: Sleep Button (CM) as /class/input/input6
[   42.968045] ACPI: Sleep Button (CM) [SLPB]
[   43.073340] No dock devices found.
[   43.452931] powernow-k8: Power state transitions not supported
[   43.500463] ACPI Exception (processor_perflib-0234): AE_NOT_FOUND, Evaluating _PSS [20070126]
[   44.769237] ppdev: user-space parallel port driver
[   44.954027] audit(1198362922.297:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4761 profile="/usr/sbin/cupsd"
[   45.143404] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   45.143410] apm: overridden by ACPI.
[   45.391697] Failure registering capabilities with primary security module.
[   45.658787] Bluetooth: Core ver 2.11
[   45.658955] NET: Registered protocol family 31
[   45.658958] Bluetooth: HCI device and connection manager initialized
[   45.658963] Bluetooth: HCI socket layer initialized
[   45.693342] Bluetooth: L2CAP ver 2.8
[   45.693347] Bluetooth: L2CAP socket layer initialized
[   45.804316] Bluetooth: RFCOMM socket layer initialized
[   45.804478] Bluetooth: RFCOMM TTY layer initialized
[   45.804481] Bluetooth: RFCOMM ver 1.8
[   50.173275] NET: Registered protocol family 17
[   52.198714] NET: Registered protocol family 10
[   52.198988] lo: Disabled Privacy Extensions
[   62.472462] eth0: no IPv6 routers present
[ 5698.465697] usb 2-6: new high speed USB device using ehci_hcd and address 2
[ 5699.337772] hub 2-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[ 5699.449505] usb 2-6: new high speed USB device using ehci_hcd and address 3
[ 5700.321563] hub 2-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[ 5700.433314] usb 2-6: new high speed USB device using ehci_hcd and address 4
[ 5700.841234] usb 2-6: device not accepting address 4, error -71
[ 5700.953211] usb 2-6: new high speed USB device using ehci_hcd and address 5
[ 5701.361128] usb 2-6: device not accepting address 5, error -71

---

### Post by Ptero-4 on 2007-12-22
Looks like one of your USB ports went kaput, try the thumbdrive in another one of the ports or in another computer.

---

### Post by misterz on 2007-12-22
Tried in all USB ports. Same outcome. The unit is a dual boot w/. Vista. No problem under Vista.

---

### Post by muskratmx on 2007-12-23
I'm having similar problem, except one thumb drive just blinks and blinks noting more.

hub_port_status failed (err =-32)

The same disk works fine on windows XP.

I can't figure whats the problem.

---

