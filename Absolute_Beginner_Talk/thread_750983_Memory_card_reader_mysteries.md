---
title: "Memory card reader mysteries"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by Sunships on 2008-04-10
Hello! 

I am using Gutsy on a Sony Vaio FS550. I reinstalled Gutsy, and the memory card reader, which previously worked perfectly well, now doesn't. On plugging in a memory stick, it used to automatically mount, and I could access/read/write files without any problem. Now nothing happens, and I don't know why. The memory card reader still works fine in Windows. I have looked at other threads, and am a bit baffled, so a little bit of assistance from someone who knows their stuff would be greatly appreciated. 

Thank you!

---

### Post by smurphy_it on 2008-04-10
After you plug in the card, jump into a terminal and type dmesg.

The last few lines should hopefully give some clue as to why it didn't read the card.

---

### Post by Sunships on 2008-04-11
Hi smurphy_it, thanks for your response!

The output from dmesg is as follows. There is a lot, and in my n00bishness I am unable to view it all, but I am guessing the penultimate line "[  284.424000] tifm_core: MemoryStick card detected in socket 0:1" is the most important.

```

[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001f6e0000 (usable)
[    0.000000]  BIOS-e820: 000000001f6e0000 - 000000001f6ea000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001f6ea000 - 000000001f700000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001f700000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0006000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 502MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 128736) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   128736
[    0.000000]   HighMem    128736 ->   128736
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   128736
[    0.000000] On node 0 totalpages: 128736
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 973 pages used for memmap
[    0.000000]   Normal zone: 123667 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7530 checksum 0
[    0.000000] ACPI: RSDP 000F7530, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 1F6E5A12, 0044 (r1   Sony       J0 20041219 PTL         0)
[    0.000000] ACPI: APIC 1F6E9E78, 0068 (r1   Sony       J0 20041219 PTL        5F)
[    0.000000] ACPI: FACP 1F6E9EE0, 0084 (r2   Sony       J0 20041219 PTL        5F)
[    0.000000] ACPI: DSDT 1F6E64A7, 39D1 (r1   Sony       J0 20041219 PTL  20030224)
[    0.000000] ACPI: FACS 1F6FAFC0, 0040
[    0.000000] ACPI: BOOT 1F6E9FD8, 0028 (r1   Sony       J0 20041219 PTL         1)
[    0.000000] ACPI: MCFG 1F6E9F9C, 003C (r1   Sony       J0 20041219 PTL        5F)
[    0.000000] ACPI: SSDT 1F6E62CF, 01D4 (r1   Sony       J0 20041219 PTL  20030224)
[    0.000000] ACPI: SSDT 1F6E5E8A, 0235 (r1   Sony       J0 20041219 PTL  20030224)
[    0.000000] ACPI: SSDT 1F6E5C6F, 021B (r1   Sony       J0 20041219 PTL  20030224)
[    0.000000] ACPI: SSDT 1F6E5A56, 0219 (r1   Sony       J0 20041219 PTL  20030224)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:13 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:c0000000)
[    0.000000] Built 1 zonelists.  Total pages: 127731
[    0.000000] Kernel command line: root=UUID=87fbcb65-2004-474a-a853-830ff14aa9db ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1596.294 MHz processor.
[    7.575232] Console: colour VGA+ 80x25
[    7.575415] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    7.575639] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    7.589398] Memory: 498828k/514944k available (2015k kernel code, 15660k reserved, 916k data, 364k init, 0k highmem)
[    7.589408] virtual kernel memory layout:
[    7.589409]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[    7.589411]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    7.589412]     vmalloc : 0xe0000000 - 0xff7fe000   ( 503 MB)
[    7.589414]     lowmem  : 0xc0000000 - 0xdf6e0000   ( 502 MB)
[    7.589415]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[    7.589416]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[    7.589418]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[    7.589422] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    7.589463] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[    7.669427] Calibrating delay using timer specific routine.. 3195.99 BogoMIPS (lpj=6391996)
[    7.669454] Security Framework v1.0.0 initialized
[    7.669462] SELinux:  Disabled at boot.
[    7.669478] Mount-cache hash table entries: 512
[    7.669618] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 00000180 00000000 00000000
[    7.669632] CPU: L1 I cache: 32K, L1 D cache: 32K
[    7.669635] CPU: L2 cache: 2048K
[    7.669638] CPU: After all inits, caps: afe9fbff 00100000 00000000 00002040 00000180 00000000 00000000
[    7.669652] Compat vDSO mapped to ffffe000.
[    7.669664] Checking 'hlt' instruction... OK.
[    7.685525] SMP alternatives: switching to UP code
[    7.685718] Freeing SMP alternatives: 11k freed
[    7.686001] Early unpacking initramfs... done
[    8.060397] ACPI: Core revision 20070126
[    8.060460] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    8.086094] CPU0: Intel(R) Pentium(R) M processor 1.60GHz stepping 08
[    8.086125] Total of 1 processors activated (3195.99 BogoMIPS).
[    8.086322] ENABLING IO-APIC IRQs
[    8.086529] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    8.233034] Brought up 1 CPUs
[    8.233152] Booting paravirtualized kernel on bare hardware
[    8.233227] Time: 22:53:32  Date: 03/11/108
[    8.233251] NET: Registered protocol family 16
[    8.233333] EISA bus registered
[    8.233349] ACPI: bus type pci registered
[    8.233752] PCI: PCI BIOS revision 2.10 entry at 0xfd905, last bus=8
[    8.233755] PCI: Using configuration type 1
[    8.233756] Setting up standard PCI resources
[    8.243086] ACPI: EC: Look up EC in DSDT
[    8.246203] ACPI: EC: GPE=0x17, ports=0x66, 0x62
[    8.349775] ACPI: Interpreter enabled
[    8.349778] ACPI: (supports S0 S3 S4 S5)
[    8.349795] ACPI: Using IOAPIC for interrupt routing
[    8.354852] ACPI: EC: GPE=0x17, ports=0x66, 0x62
[    8.354897] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    8.354911] PCI: Probing PCI hardware (bus 00)
[    8.355502] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    8.355507] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[    8.356046] PCI: Firmware left 0000:06:08.0 e100 interrupts enabled, disabling
[    8.356164] PCI: Transparent bridge - 0000:00:1e.0
[    8.356258] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    8.356615] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    8.361252] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    8.361342] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 *4 5 6 7 11 12 14 15)
[    8.361429] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 *3 4 5 6 7 10 12 14 15)
[    8.361516] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    8.361603] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[    8.361689] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    8.361776] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    8.361864] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    8.361952] Linux Plug and Play Support v0.97 (c) Adam Belay
[    8.361961] pnp: PnP ACPI init
[    8.361968] ACPI: bus type pnp registered
[    8.363882] pnp: PnP ACPI: found 8 devices
[    8.363884] ACPI: ACPI bus type pnp unregistered
[    8.363888] PnPBIOS: Disabled by ACPI PNP
[    8.363923] PCI: Using ACPI for IRQ routing
[    8.363926] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    8.383674] NET: Registered protocol family 8
[    8.383676] NET: Registered protocol family 20
[    8.383722] pnp: 00:04: iomem range 0xf0008000-0xf000bfff could not be reserved
[    8.383726] pnp: 00:04: iomem range 0xf0000000-0xf0003fff could not be reserved
[    8.383730] pnp: 00:04: iomem range 0xf0005000-0xf0005fff could not be reserved
[    8.383733] pnp: 00:04: iomem range 0xf0004000-0xf0004fff could not be reserved
[    8.384882] Time: tsc clocksource has been installed.
[    8.413993] PCI: Bus 7, cardbus bridge: 0000:06:03.0
[    8.413996]   IO window: 00002400-000024ff
[    8.414002]   IO window: 00002800-000028ff
[    8.414008]   PREFETCH window: 30000000-33ffffff
[    8.414014]   MEM window: 38000000-3bffffff
[    8.414020] PCI: Bridge: 0000:00:1e.0
[    8.414024]   IO window: 2000-2fff
[    8.414030]   MEM window: b0100000-b01fffff
[    8.414035]   PREFETCH window: 30000000-33ffffff
[    8.414052] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    8.414073] PCI: Enabling device 0000:06:03.0 (0000 -> 0003)
[    8.414080] ACPI: PCI Interrupt 0000:06:03.0[A] -> GSI 16 (level, low) -> IRQ 16
[    8.414098] NET: Registered protocol family 2
[    8.452855] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    8.452890] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[    8.453047] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    8.453156] TCP: Hash tables configured (established 16384 bind 16384)
[    8.453159] TCP reno registered
[    8.464930] checking if image is initramfs... it is
[    8.916483] Switched to high resolution mode on CPU 0
[    9.211884] Freeing initrd memory: 7355k freed
[    9.212043] Simple Boot Flag at 0x36 set to 0x1
[    9.212314] audit: initializing netlink socket (disabled)
[    9.212329] audit(1207954412.172:1): initialized
[    9.214240] VFS: Disk quotas dquot_6.5.1
[    9.214288] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    9.214381] io scheduler noop registered
[    9.214384] io scheduler anticipatory registered
[    9.214386] io scheduler deadline registered
[    9.214402] io scheduler cfq registered (default)
[    9.214417] Boot video device is 0000:00:02.0
[    9.214734] isapnp: Scanning for PnP cards...
[    9.569368] isapnp: No Plug & Play device found
[    9.595285] Real Time Clock Driver v1.12ac
[    9.595397] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    9.596585] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    9.596783] input: Macintosh mouse button emulation as /class/input/input0
[    9.596855] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    9.600537] i8042.c: Detected active multiplexing controller, rev 1.1.
[    9.605157] serio: i8042 KBD port at 0x60,0x64 irq 1
[    9.605163] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    9.605166] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    9.605169] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    9.605171] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    9.605354] mice: PS/2 mouse device common for all mice
[    9.605668] EISA: Probing bus 0 at eisa.0
[    9.605677] Cannot allocate resource for EISA slot 1
[    9.605680] Cannot allocate resource for EISA slot 2
[    9.605709] EISA: Detected 0 cards.
[    9.605813] TCP cubic registered
[    9.605831] NET: Registered protocol family 1
[    9.605856] Using IPI No-Shortcut mode
[    9.606041]   Magic number: 4:487:906
[    9.606106]   hash matches device ptyz2
[    9.606378] Freeing unused kernel memory: 364k freed
[    9.643906] input: AT Translated Set 2 keyboard as /class/input/input1
[   10.801623] AppArmor: AppArmor initialized<5>audit(1207954413.672:2):  type=1505 info="AppArmor initialized" pid=1194
[   10.806971] fuse init (API version 7.8)
[   10.810648] Failure registering capabilities with primary security module.
[   11.818173] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   11.818178] ACPI: Processor [CPU0] (supports 8 throttling states)
[   11.818190] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   11.820956] ACPI: Thermal Zone [THRM] (27 C)
[   12.211939] usbcore: registered new interface driver usbfs
[   12.211968] usbcore: registered new interface driver hub
[   12.211986] usbcore: registered new device driver usb
[   12.212764] USB Universal Host Controller Interface driver v3.0
[   12.212833] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 17
[   12.212845] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   12.212849] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   12.213026] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   12.213057] uhci_hcd 0000:00:1d.0: irq 17, io base 0x00001820
[   12.213167] usb usb1: configuration #1 chosen from 1 choice
[   12.213190] hub 1-0:1.0: USB hub found
[   12.213196] hub 1-0:1.0: 2 ports detected
[   12.279433] SCSI subsystem initialized
[   12.284793] libata version 2.21 loaded.
[   12.313812] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 18
[   12.313826] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   12.313831] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   12.313854] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   12.313885] uhci_hcd 0000:00:1d.1: irq 18, io base 0x00001840
[   12.313985] usb usb2: configuration #1 chosen from 1 choice
[   12.314010] hub 2-0:1.0: USB hub found
[   12.314016] hub 2-0:1.0: 2 ports detected
[   12.400295] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k4-NAPI
[   12.400299] e100: Copyright(c) 1999-2006 Intel Corporation
[   12.417743] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
[   12.417756] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   12.417761] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   12.417784] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   12.417817] uhci_hcd 0000:00:1d.2: irq 19, io base 0x00001860
[   12.417914] usb usb3: configuration #1 chosen from 1 choice
[   12.417940] hub 3-0:1.0: USB hub found
[   12.417946] hub 3-0:1.0: 2 ports detected
[   12.521644] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[   12.521658] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   12.521662] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   12.521686] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   12.521720] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
[   12.521819] usb usb4: configuration #1 chosen from 1 choice
[   12.521846] hub 4-0:1.0: USB hub found
[   12.521852] hub 4-0:1.0: 2 ports detected
[    4.816000] Marking TSC unstable due to: possible TSC halt in C2.
[    4.820000] Time: acpi_pm clocksource has been installed.
[    4.916000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 17
[    4.916000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    4.916000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.916000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    4.916000] ehci_hcd 0000:00:1d.7: debug port 1
[    4.916000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    4.916000] ehci_hcd 0000:00:1d.7: irq 17, io mem 0xb0004000
[    4.920000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.920000] usb usb5: configuration #1 chosen from 1 choice
[    4.920000] hub 5-0:1.0: USB hub found
[    4.920000] hub 5-0:1.0: 8 ports detected
[    5.024000] ata_piix 0000:00:1f.1: version 2.11
[    5.024000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 19
[    5.024000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    5.024000] scsi0 : ata_piix
[    5.024000] scsi1 : ata_piix
[    5.024000] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011810 irq 14
[    5.024000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011818 irq 15
[    5.200000] Clocksource tsc unstable (delta = -491181835 ns)
[    5.308000] usb 5-1: new high speed USB device using ehci_hcd and address 2
[    5.352000] ata1.00: ATA-5: HITACHI_DK23FA-80, 00M3A0A2, max UDMA/100
[    5.352000] ata1.00: 156301488 sectors, multi 16: LBA 
[    5.352000] ata1.01: ATAPI: MATSHITAUJ-831Da, 1.00, max UDMA/33
[    5.360000] ata1.00: configured for UDMA/100
[    5.452000] usb 5-1: configuration #1 chosen from 1 choice
[    5.532000] ata1.01: configured for UDMA/33
[    5.532000] ata2: port disabled. ignoring.
[    5.532000] scsi 0:0:0:0: Direct-Access     ATA      HITACHI_DK23FA-8 00M3 PQ: 0 ANSI: 5
[    5.532000] scsi 0:0:1:0: CD-ROM            MATSHITA UJ-831Da         1.00 PQ: 0 ANSI: 5
[    5.536000] ACPI: PCI Interrupt 0000:06:03.2[C] -> GSI 18 (level, low) -> IRQ 19
[    5.584000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[b0104000-b01047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    5.584000] ACPI: PCI Interrupt 0000:06:08.0[A] -> GSI 20 (level, low) -> IRQ 20
[    5.616000] e100: eth0: e100_probe: addr 0xb0107000, irq 20, MAC addr 00:01:4A:16:A0:83
[    5.628000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    5.628000] sd 0:0:0:0: [sda] Write Protect is off
[    5.628000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.628000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.628000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    5.628000] sd 0:0:0:0: [sda] Write Protect is off
[    5.628000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.628000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.628000]  sda:<6>usbcore: registered new interface driver libusual
[    5.676000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    5.676000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    5.680000] Initializing USB Mass Storage driver...
[    5.688000]  sda1 sda2 sda3 sda4
[    5.708000] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.712000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.712000] scsi 0:0:1:0: Attached scsi generic sg1 type 5
[    5.764000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    5.764000] Uniform CD-ROM driver Revision: 3.20
[    5.764000] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    5.800000] scsi2 : SCSI emulation for USB Mass Storage devices
[    5.800000] usb-storage: device found at 2
[    5.800000] usb-storage: waiting for device to settle before scanning
[    5.800000] usbcore: registered new interface driver usb-storage
[    5.800000] USB Mass Storage support registered.
[    6.060000] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    6.204000] Attempting manual resume
[    6.204000] swsusp: Resume From Partition 8:4
[    6.204000] PM: Checking swsusp image.
[    6.204000] PM: Resume from disk failed.
[    6.244000] kjournald starting.  Commit interval 5 seconds
[    6.244000] EXT3-fs: mounted filesystem with ordered data mode.
[    6.256000] usb 3-1: configuration #1 chosen from 1 choice
[    6.856000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0800460301cf2475]
[   10.800000] usb-storage: device scan complete
[   10.800000] scsi 2:0:0:0: Direct-Access     Seagate  FreeAgentDesktop 100F PQ: 0 ANSI: 4
[   10.804000] sd 2:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   10.804000] sd 2:0:0:0: [sdb] Write Protect is off
[   10.804000] sd 2:0:0:0: [sdb] Mode Sense: 1c 00 00 00
[   10.804000] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   10.808000] sd 2:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   10.808000] sd 2:0:0:0: [sdb] Write Protect is off
[   10.808000] sd 2:0:0:0: [sdb] Mode Sense: 1c 00 00 00
[   10.808000] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   10.808000]  sdb: sdb1
[   10.836000] sd 2:0:0:0: [sdb] Attached SCSI disk
[   10.836000] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   15.020000] Linux agpgart interface v0.102 (c) Dave Jones
[   15.132000] agpgart: Detected an Intel 915GM Chipset.
[   15.132000] agpgart: Detected 7932K stolen memory.
[   15.148000] agpgart: AGP aperture is 256M @ 0xc0000000
[   15.440000] iTCO_vendor_support: vendor-support=0
[   15.440000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   15.440000] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   15.440000] iTCO_wdt: No card detected
[   15.452000] intel_rng: FWH not detected
[   16.096000] usbcore: registered new interface driver hiddev
[   16.116000] Yenta: CardBus bridge found at 0000:06:03.0 [104d:818f]
[   16.116000] Yenta: Enabling burst memory read transactions
[   16.116000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   16.116000] Yenta: Routing CardBus interrupts to PCI
[   16.116000] Yenta TI: socket 0000:06:03.0, mfunc 0x01001b22, devctl 0x64
[   16.136000] input: HID 1241:1166 as /class/input/input2
[   16.136000] input: USB HID v1.10 Mouse [HID 1241:1166] on usb-0000:00:1d.2-1
[   16.136000] usbcore: registered new interface driver usbhid
[   16.136000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   16.348000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 16
[   16.348000] Socket status: 30000006
[   16.348000] Yenta: Raising subordinate bus# of parent bus (#06) from #07 to #0a
[   16.348000] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   16.348000] cs: IO port probe 0x2000-0x2fff: clean.
[   16.348000] pcmcia: parent PCI bridge Memory window: 0xb0100000 - 0xb01fffff
[   16.348000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[   16.348000] ACPI: PCI Interrupt 0000:06:03.3[B] -> GSI 17 (level, low) -> IRQ 21
[   16.352000] ieee80211_crypt: registered algorithm 'NULL'
[   16.356000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   16.356000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   16.372000] tifm_core: MMC/SD card detected in socket 0:0
[   16.392000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[   16.392000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   16.392000] ACPI: PCI Interrupt 0000:06:04.0[A] -> GSI 22 (level, low) -> IRQ 22
[   16.392000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   16.404000] input: PS/2 Mouse as /class/input/input3
[   16.420000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input4
[   16.824000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   16.824000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   17.192000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   17.232000] cs: IO port probe 0x100-0x3af: clean.
[   17.236000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   17.236000] cs: IO port probe 0x820-0x8ff: clean.
[   17.236000] cs: IO port probe 0xc00-0xcf7: clean.
[   17.240000] cs: IO port probe 0xa00-0xaff: clean.
[   17.328000] ieee80211_crypt: registered algorithm 'WEP'
[   17.848000] lp: driver loaded but no devices found
[   17.912000] Adding 409648k swap on /dev/sda4.  Priority:-1 extents:1 across:409648k
[   18.476000] EXT3 FS on sda3, internal journal
[   18.988000] NET: Registered protocol family 17
[   20.340000] No dock devices found.
[   20.348000] ACPI: AC Adapter [ADP1] (on-line)
[   20.424000] input: Power Button (FF) as /class/input/input5
[   20.428000] ACPI: Power Button (FF) [PWRF]
[   20.464000] input: Lid Switch as /class/input/input6
[   20.468000] ACPI: Lid Switch [LID0]
[   20.508000] input: Power Button (CM) as /class/input/input7
[   20.512000] ACPI: Power Button (CM) [PWRB]
[   20.520000] ACPI: Video Device [NGFX] (multi-head: yes  rom: no  post: no)
[   20.524000] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[   20.580000] ACPI: Battery Slot [BAT0] (battery present)
[   21.808000] ppdev: user-space parallel port driver
[   22.004000] audit(1207950834.136:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4808 profile="/usr/sbin/cupsd"
[   22.140000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   22.140000] apm: overridden by ACPI.
[   22.392000] sonypi: Sony Programmable I/O Controller Driver v1.26.
[   22.392000] sonypi: please try the sony-laptop module instead and report failures, see also http://www.linux.it/~malattia/wiki/index.php/Sony_drivers
[   22.396000] sonypi: detected type3 model, verbose = 0, fnkeyinit = off, camera = off, compat = off, mask = 0xffffffff, useinput = on, acpi = on
[   22.396000] sonypi: enabled at irq=11, port1=0x1080, port2=0x1084
[   22.396000] sonypi: device allocated minor is 63
[   22.448000] input: Sony Vaio Jogdial as /class/input/input8
[   22.496000] input: Sony Vaio Keys as /class/input/input9
[   22.556000] sonypi command failed at /build/buildd/linux-source-2.6.22-2.6.22/drivers/char/sonypi.c : sonypi_call1 (line 652)
[   22.604000] sonypi command failed at /build/buildd/linux-source-2.6.22-2.6.22/drivers/char/sonypi.c : sonypi_call2 (line 663)
[   22.652000] sonypi command failed at /build/buildd/linux-source-2.6.22-2.6.22/drivers/char/sonypi.c : sonypi_call2 (line 665)
[   22.700000] sonypi command failed at /build/buildd/linux-source-2.6.22-2.6.22/drivers/char/sonypi.c : sonypi_call1 (line 652)
[   22.736000] sony-laptop: Sony Notebook Control Driver v0.5.
[   22.776000] input: Sony Vaio Keys as /class/input/input10
[   22.780000] input: Sony Vaio Jogdial as /class/input/input11
[   22.920000] Failure registering capabilities with primary security module.
[   23.976000] NET: Registered protocol family 10
[   23.976000] lo: Disabled Privacy Extensions
[   23.976000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.708000] [drm] Initialized drm 1.1.0 20060810
[   26.712000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   26.716000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   34.856000] eth1: no IPv6 routers present
[  284.424000] tifm_core: MemoryStick card detected in socket 0:1
[  284.464000] tifm_ms: Unknown symbol tifm_has_ms_pif

```

---

### Post by Sunships on 2008-04-13
*bump*

---

### Post by Sunships on 2008-04-14
*bump*

---

### Post by Sunships on 2008-04-16
*bump*

---

### Post by qamelian on 2008-04-16
> **Sunships said:**
> Hi smurphy_it, thanks for your response!

The output from dmesg is as follows. There is a lot, and in my n00bishness I am unable to view it all, but I am guessing the penultimate line "[  284.424000] tifm_core: MemoryStick card detected in socket 0:1" is the most important.

```
[  284.424000] tifm_core: MemoryStick card detected in socket 0:1
[  284.464000] tifm_ms: Unknown symbol tifm_has_ms_pif

```
The problem is that you need to update the driver and memorystick subsystem. You can find some brief instruction on how to do this here:
[http://www.micropctalk.com/forums/showthread.php?t=3026](http://www.micropctalk.com/forums/showthread.php?t=3026)

Find the section labelled Note II a little more than half way down the page. 

It appears that this is a known bug as I found many references to this problem via a quick Google search of the last line of your dmesg output. On Launchpad:
[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/159951](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/159951), for example.

---

### Post by Sunships on 2008-04-16
> **qamelian said:**
> The problem is that you need to update the driver and memorystick subsystem. You can find some brief instruction on how to do this here:
[http://www.micropctalk.com/forums/showthread.php?t=3026](http://www.micropctalk.com/forums/showthread.php?t=3026)

Find the section labelled Note II a little more than half way down the page. 

It appears that this is a known bug as I found many references to this problem via a quick Google search of the last line of your dmesg output. On Launchpad:
[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/159951](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/159951), for example.

Thanks qamelian, I'll give it a try!

---

### Post by Sunships on 2008-04-16
OK, I don't think it worked completely. When I did "sudo make install" I was shown the following:

```


mkdir -p /lib/modules/2.6.22-14-generic
rm -f /lib/modules/2.6.22-14-generic/kernel/drivers/misc/tifm_core.ko
rm -f /lib/modules/2.6.22-14-generic/kernel/drivers/misc/tifm_7xx1.ko
rm -f /lib/modules/2.6.22-14-generic/kernel/drivers/mmc/tifm_sd.ko
install -c -m 644 tifm_core.ko tifm_7xx1.ko /lib/modules/2.6.22-14-generic/kernel/drivers/misc/
install: cannot stat `tifm_core.ko': No such file or directory
install: cannot stat `tifm_7xx1.ko': No such file or directory
make: *** [install] Error 1

```

However when I now do "dmesg" the output ends at:

```

[   34.856000] eth1: no IPv6 routers present

```

"Note II" in the guide ends with "restart your UX" - I assumed this meant restart the computer, or that restarting the computer would achieve the required effect.

---

### Post by qamelian on 2008-04-16
Were there any errors during the "make" stage?

---

### Post by Sunships on 2008-04-16
> **qamelian said:**
> Were there any errors during the "make" stage?

Hmm, I didn't save all the outputs last time, so I repeated the commands to get them saved, and turned off my computer....on booting up to reply to your post it seems that the card reader is now working properly, thanks a lot qamelian!!

---

### Post by qamelian on 2008-04-16
> **Sunships said:**
> Hmm, I didn't save all the outputs last time, so I repeated the commands to get them saved, and turned off my computer....on booting up to reply to your post it seems that the card reader is now working properly, thanks a lot qamelian!!
Cool! I'm glad it worked for you. 
Cheers!

---

