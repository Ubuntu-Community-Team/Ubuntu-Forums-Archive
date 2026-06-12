---
title: "cd burner not showing up!"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by -Soul_Reaper- on 2007-07-09
The cables are plugged in, but it just calls it 'cd-rom1', and it won't burn cds!
Do i need drivers?
Help is appreciated, thanks.

---

### Post by Cypher on 2007-07-09
Open a terminal and show us the output of
```

dmesg

```

---

### Post by -Soul_Reaper- on 2007-07-09
> **Cypher said:**
> Open a terminal and show us the output of
```

dmesg

```

This is REALLY long.

Here:
```

[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e0000 size: 0000000000020000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003fed0000 end: 000000003ffd0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000003ffd0000 size: 000000000000f000 end: 000000003ffdf000 type: 3
[    0.000000] copy_e820_map() start: 000000003ffdf000 size: 0000000000021000 end: 0000000040000000 type: 4
[    0.000000] copy_e820_map() start: 00000000ffb80000 size: 0000000000480000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ffd0000 (usable)
[    0.000000]  BIOS-e820: 000000003ffd0000 - 000000003ffdf000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ffdf000 - 0000000040000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 262096) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   262096
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   262096
[    0.000000] On node 0 totalpages: 262096
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 255 pages used for memmap
[    0.000000]   HighMem zone: 32465 pages, LIFO batch:7
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000f5460
[    0.000000] ACPI: RSDT (v001 A M I  OEMRSDT  0x06000327 MSFT 0x00000097) @ 0x3ffd0000
[    0.000000] ACPI: FADT (v002 A M I  OEMFACP  0x06000327 MSFT 0x00000097) @ 0x3ffd0200
[    0.000000] ACPI: MADT (v001 A M I  OEMAPIC  0x06000327 MSFT 0x00000097) @ 0x3ffd0390
[    0.000000] ACPI: OEMB (v001 A M I  OEMBIOS  0x06000327 MSFT 0x00000097) @ 0x3ffdf040
[    0.000000] ACPI: DSDT (v001  PSLA1 PSLA1059 0x00000059 INTL 0x02002026) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:2 APIC version 20
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bfb80000)
[    0.000000] Detected 2800.191 MHz processor.
[   12.739853] Built 1 zonelists.  Total pages: 260049
[   12.739857] Kernel command line: root=UUID=75fa9507-7a05-4609-b177-c80b890b25ac ro quiet splash
[   12.740003] mapped APIC to ffffd000 (fee00000)
[   12.740006] mapped IOAPIC to ffffc000 (fec00000)
[   12.740009] Enabling fast FPU save and restore... done.
[   12.740012] Enabling unmasked SIMD FPU exception support... done.
[   12.740020] Initializing CPU#0
[   12.740086] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   12.741438] Console: colour VGA+ 80x25
[   12.741821] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   12.742223] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   12.765107] Memory: 1028196k/1048384k available (1992k kernel code, 19512k reserved, 900k data, 328k init, 130880k highmem)
[   12.765117] virtual kernel memory layout:
[   12.765118]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   12.765119]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   12.765120]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   12.765121]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   12.765122]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   12.765123]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[   12.765124]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[   12.765127] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   12.843898] Calibrating delay using timer specific routine.. 5604.66 BogoMIPS (lpj=11209323)
[   12.843942] Security Framework v1.0.0 initialized
[   12.843949] SELinux:  Disabled at boot.
[   12.843966] Mount-cache hash table entries: 512
[   12.844118] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[   12.844130] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   12.844133] CPU: L2 cache: 512K
[   12.844135] CPU: Physical Processor ID: 0
[   12.844137] CPU: After all inits, caps: bfebfbff 00000000 00000000 00003080 00004400 00000000 00000000
[   12.844147] Compat vDSO mapped to ffffe000.
[   12.844151] Remapping vsyscall page to ffffe000
[   12.844163] Checking 'hlt' instruction... OK.
[   12.859960] SMP alternatives: switching to UP code
[   12.860310] Early unpacking initramfs... done
[   13.139714] ACPI: Core revision 20060707
[   13.139854] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   13.141516] CPU0: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 09
[   13.141537] SMP alternatives: switching to SMP code
[   13.141662] Booting processor 1/1 eip 3000
[   13.151887] Initializing CPU#1
[   13.231174] Calibrating delay using timer specific routine.. 5600.57 BogoMIPS (lpj=11201145)
[   13.231183] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[   13.231194] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   13.231196] CPU: L2 cache: 512K
[   13.231198] CPU: Physical Processor ID: 0
[   13.231201] CPU: After all inits, caps: bfebfbff 00000000 00000000 00003080 00004400 00000000 00000000
[   13.231359] CPU1: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 09
[   13.231399] Total of 2 processors activated (11205.23 BogoMIPS).
[   13.231524] ENABLING IO-APIC IRQs
[   13.231705] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   13.378907] checking TSC synchronization across 2 CPUs: passed.
[    0.003994] Brought up 2 CPUs
[    0.049876] migration_cost=125
[    0.050183] Booting paravirtualized kernel on bare hardware
[    0.050271] Time: 21:58:47  Date: 06/09/107
[    0.050302] NET: Registered protocol family 16
[    0.050407] EISA bus registered
[    0.050412] ACPI: bus type pci registered
[    0.050481] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=2
[    0.050483] PCI: Using configuration type 1
[    0.050484] Setting up standard PCI resources
[    0.064999] ACPI: Interpreter enabled
[    0.065003] ACPI: Using IOAPIC for interrupt routing
[    0.066025] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.066032] PCI: Probing PCI hardware (bus 00)
[    0.066607] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[    0.066611] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
[    0.066798] Boot video device is 0000:01:00.0
[    0.067054] PCI: Transparent bridge - 0000:00:1e.0
[    0.067080] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.074799] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.081332] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.081567] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.081802] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.082036] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.082269] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.082505] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.082737] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.082973] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.083083] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.083100] pnp: PnP ACPI init
[    0.087437] pnp: PnP ACPI: found 13 devices
[    0.087442] PnPBIOS: Disabled by ACPI PNP
[    0.087517] PCI: Using ACPI for IRQ routing
[    0.087521] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.091099] NET: Registered protocol family 8
[    0.091102] NET: Registered protocol family 20
[    0.091766] pnp: 00:09: ioport range 0x680-0x6ff has been reserved
[    0.092195] PCI: Bridge: 0000:00:01.0
[    0.092198]   IO window: disabled.
[    0.092203]   MEM window: fc900000-fe9fffff
[    0.092207]   PREFETCH window: d7f00000-f7efffff
[    0.092213] PCI: Bridge: 0000:00:1e.0
[    0.092216]   IO window: b000-bfff
[    0.092222]   MEM window: fea00000-feafffff
[    0.092226]   PREFETCH window: disabled.
[    0.092243] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.092280] NET: Registered protocol family 2
[    0.147793] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.147945] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.148480] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.148785] TCP: Hash tables configured (established 131072 bind 65536)
[    0.148789] TCP reno registered
[    0.163844] checking if image is initramfs... it is
[    0.706318] Freeing initrd memory: 6788k freed
[    0.706765] audit: initializing netlink socket (disabled)
[    0.706777] audit(1184018327.428:1): initialized
[    0.706911] highmem bounce pool size: 64 pages
[    0.707015] VFS: Disk quotas dquot_6.5.1
[    0.707035] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.707090] io scheduler noop registered
[    0.707093] io scheduler anticipatory registered
[    0.707095] io scheduler deadline registered
[    0.707108] io scheduler cfq registered (default)
[    8.692032] 0000:00:1d.7 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
[    8.692381] isapnp: Scanning for PnP cards...
[    9.045324] isapnp: No Plug & Play device found
[    9.075132] Real Time Clock Driver v1.12ac
[    9.075193] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    9.075313] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    9.076373] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    9.076653] mice: PS/2 mouse device common for all mice
[    9.077362] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    9.077530] input: Macintosh mouse button emulation as /class/input/input0
[    9.077573] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    9.077577] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    9.077832] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    9.077834] PNP: PS/2 controller doesn't have AUX irq; using default 12
[    9.080707] serio: i8042 KBD port at 0x60,0x64 irq 1
[    9.080713] serio: i8042 AUX port at 0x60,0x64 irq 12
[    9.080831] EISA: Probing bus 0 at eisa.0
[    9.080871] EISA: Detected 0 cards.
[    9.110915] TCP cubic registered
[    9.110925] NET: Registered protocol family 1
[    9.110952] Starting balanced_irq
[    9.110962] Using IPI No-Shortcut mode
[    9.111002] Time: tsc clocksource has been installed.
[    9.111065] input: AT Translated Set 2 keyboard as /class/input/input1
[    9.111166] ACPI: (supports S0 S1 S3 S4 S5)
[    9.111223]   Magic number: 15:352:1005
[    9.111232]   hash matches device ttye4
[    9.111397]   hash matches device 00:07
[    9.111619] Freeing unused kernel memory: 328k freed
[   10.357877] Capability LSM initialized
[   11.041048] usbcore: registered new interface driver usbfs
[   11.041081] usbcore: registered new interface driver hub
[   11.043757] usbcore: registered new device driver usb
[   11.066418] SCSI subsystem initialized
[   11.073665] libata version 2.20 loaded.
[   11.078057] ata_piix 0000:00:1f.1: version 2.10ac1
[   11.078073] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[   11.078086] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 16
[   11.078109] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   11.078176] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001fc00 irq 14
[   11.082732] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001fc08 irq 15
[   11.082784] scsi0 : ata_piix
[   11.084277] Floppy drive(s): fd0 is 1.44M
[   11.089306] USB Universal Host Controller Interface driver v3.0
[   11.109058] FDC 0 is a post-1991 82077
[   11.159487] ieee1394: Initialized config rom entry `ip1394'
[   11.165502] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   11.243733] ata1.00: ata_hpa_resize 1: sectors = 320173056, hpa_sectors = 320173056
[   11.243738] ata1.00: ATA-7: Maxtor 6Y160P0, YAR41BW0, max UDMA/133
[   11.243740] ata1.00: 320173056 sectors, multi 16: LBA48 
[   11.251696] ata1.00: ata_hpa_resize 1: sectors = 320173056, hpa_sectors = 320173056
[   11.251699] ata1.00: configured for UDMA/133
[   11.251710] scsi1 : ata_piix
[   11.726650] ata2.00: ATAPI, max UDMA/33
[   11.726654] ata2.01: ATAPI, max UDMA/33
[   11.890351] ata2.00: configured for UDMA/33
[   41.835177] ata2.01: qc timeout (cmd 0xef)
[   41.835185] ata2.01: failed to set xfermode (err_mask=0x4)
[   41.835189] ata2: failed to recover some devices, retrying in 5 secs
[   47.469001] ata2.00: configured for UDMA/33
[   77.413829] ata2.01: qc timeout (cmd 0xef)
[   77.413836] ata2.01: failed to set xfermode (err_mask=0x4)
[   77.413842] ata2.01: limiting speed to UDMA/33:PIO3
[   77.413845] ata2: failed to recover some devices, retrying in 5 secs
[   83.047653] ata2.00: configured for UDMA/33
[  112.992481] ata2.01: qc timeout (cmd 0xef)
[  112.992489] ata2.01: failed to set xfermode (err_mask=0x4)
[  112.992493] ata2.01: disabled
[  112.992496] ata2: failed to recover some devices, retrying in 5 secs
[  117.987309] ata2.00: failed to set xfermode (err_mask=0x40)
[  117.987314] ata2: failed to recover some devices, retrying in 5 secs
[  123.465417] ata2.00: configured for UDMA/33
[  123.465563] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6Y160P0   YAR4 PQ: 0 ANSI: 5
[  123.466492] scsi 1:0:0:0: CD-ROM            JLMS     XJ-HD166S        DPS7 PQ: 0 ANSI: 5
[  123.467150] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 17
[  123.467166] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[  123.467172] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[  123.467482] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[  123.467516] uhci_hcd 0000:00:1d.0: irq 17, io base 0x0000e000
[  123.468317] usb usb1: configuration #1 chosen from 1 choice
[  123.469454] hub 1-0:1.0: USB hub found
[  123.469468] hub 1-0:1.0: 2 ports detected
[  123.573179] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 18
[  123.573195] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[  123.573201] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[  123.573241] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[  123.573270] uhci_hcd 0000:00:1d.1: irq 18, io base 0x0000e400
[  123.573402] usb usb2: configuration #1 chosen from 1 choice
[  123.573453] hub 2-0:1.0: USB hub found
[  123.573466] hub 2-0:1.0: 2 ports detected
[  123.676983] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 16
[  123.677001] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[  123.677007] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[  123.677042] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[  123.677073] uhci_hcd 0000:00:1d.2: irq 16, io base 0x0000e800
[  123.677205] usb usb3: configuration #1 chosen from 1 choice
[  123.677259] hub 3-0:1.0: USB hub found
[  123.677273] hub 3-0:1.0: 2 ports detected
[  123.780794] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 17
[  123.780810] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[  123.780816] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[  123.780852] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[  123.780877] uhci_hcd 0000:00:1d.3: irq 17, io base 0x0000ec00
[  123.781013] usb usb4: configuration #1 chosen from 1 choice
[  123.781070] hub 4-0:1.0: USB hub found
[  123.781084] hub 4-0:1.0: 2 ports detected
[  123.884752] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
[  123.884772] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[  123.884777] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[  123.884820] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[  123.884869] ehci_hcd 0000:00:1d.7: debug port 1
[  123.884880] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[  123.884895] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xfebffc00
[  123.888788] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[  123.888963] usb usb5: configuration #1 chosen from 1 choice
[  123.889008] hub 5-0:1.0: USB hub found
[  123.889020] hub 5-0:1.0: 8 ports detected
[  123.916452] usb 2-2: new low speed USB device using uhci_hcd and address 2
[  123.996542] ACPI: PCI Interrupt 0000:02:0e.0[A] -> GSI 21 (level, low) -> IRQ 20
[  124.046354] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[feaef000-feaef7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[  124.046598] 8139cp 0000:02:0f.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[  124.046603] 8139cp 0000:02:0f.0: Try the "8139too" driver instead.
[  124.049114] 8139too Fast Ethernet driver 0.9.28
[  124.049186] ACPI: PCI Interrupt 0000:02:0f.0[A] -> GSI 19 (level, low) -> IRQ 18
[  124.049549] eth0: RealTek RTL8139 at 0xf889e800, 00:0c:6e:a9:86:fc, IRQ 18
[  124.049553] eth0:  Identified 8139 chip type 'RTL-8101'
[  124.060375] SCSI device sda: 320173056 512-byte hdwr sectors (163929 MB)
[  124.060395] sda: Write Protect is off
[  124.060400] sda: Mode Sense: 00 3a 00 00
[  124.060427] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  124.060503] SCSI device sda: 320173056 512-byte hdwr sectors (163929 MB)
[  124.060521] sda: Write Protect is off
[  124.060525] sda: Mode Sense: 00 3a 00 00
[  124.060562] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  124.060569]  sda: sda1 sda2 < sda5 >
[  124.089072] sd 0:0:0:0: Attached scsi disk sda
[  124.094371] sd 0:0:0:0: Attached scsi generic sg0 type 0
[  124.094403] sr 1:0:0:0: Attached scsi generic sg1 type 5
[  124.096954] sr0: scsi3-mmc drive: 40x/40x cd/rw xa/form2 cdda tray
[  124.096959] Uniform CD-ROM driver Revision: 3.20
[  124.097024] sr 1:0:0:0: Attached scsi CD-ROM sr0
[  124.300798] Attempting manual resume
[  124.300803] swsusp: Resume From Partition 8:5
[  124.300805] PM: Checking swsusp image.
[  124.301021] PM: Resume from disk failed.
[  124.335467] kjournald starting.  Commit interval 5 seconds
[  124.335481] EXT3-fs: mounted filesystem with ordered data mode.
[  124.419488] usb 2-2: new low speed USB device using uhci_hcd and address 3
[  124.599281] usb 2-2: configuration #1 chosen from 1 choice
[  125.318017] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e018000030cf4c]
[  132.690830] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  134.073857] NET: Registered protocol family 17
[  134.098266] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  134.101118] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  134.675479] Linux agpgart interface v0.102 (c) Dave Jones
[  134.676953] input: PC Speaker as /class/input/input2
[  134.717998] iTCO_vendor_support: vendor-support=0
[  134.741657] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[  134.741776] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[  134.741786] iTCO_wdt: No card detected
[  134.772196] intel_rng: FWH not detected
[  134.810381] agpgart: Detected an Intel 865 Chipset.
[  134.813382] agpgart: AGP aperture is 64M @ 0xf8000000
[  135.038661] parport: PnPBIOS parport detected.
[  135.038715] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[  135.081897] nvidia: module license 'NVIDIA' taints kernel.
[  135.336738] usbcore: registered new interface driver hiddev
[  135.340964] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 17
[  135.341168] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
[  135.450402] input: Logitech USB-PS/2 Optical Mouse as /class/input/input3
[  135.450484] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.1-2
[  135.450507] usbcore: registered new interface driver usbhid
[  135.450513] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[  135.617523] ACPI: PCI Interrupt 0000:02:0b.0[A] -> GSI 23 (level, low) -> IRQ 19
[  135.621403] Installing spdif_bug patch: Audigy 2 [Unknown]
[  135.818609] fuse init (API version 7.8)
[  135.850633] lp0: using parport0 (interrupt-driven).
[  135.910259] Adding 3028212k swap on /dev/disk/by-uuid/28fd529f-fdfb-4af6-a95a-33240e619ab7.  Priority:-1 extents:1 across:3028212k
[  136.045651] EXT3 FS on sda1, internal journal
[  141.567303] ibm_acpi: ec object not found
[  141.612815] input: Power Button (FF) as /class/input/input4
[  141.612854] ACPI: Power Button (FF) [PWRF]
[  141.612932] input: Power Button (CM) as /class/input/input5
[  141.612968] ACPI: Power Button (CM) [PWRB]
[  141.728183] No dock devices found.
[  141.767748] Using specific hotkey driver
[  141.926652] pcc_acpi: loading...
[  147.321643] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[  147.321668] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[  147.321706] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[  147.982773] ppdev: user-space parallel port driver
[  148.616899] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  148.616907] apm: disabled - APM is not SMP safe.
[  148.901636] Bluetooth: Core ver 2.11
[  148.901719] NET: Registered protocol family 31
[  148.901722] Bluetooth: HCI device and connection manager initialized
[  148.901727] Bluetooth: HCI socket layer initialized
[  148.944077] Bluetooth: L2CAP ver 2.8
[  148.944084] Bluetooth: L2CAP socket layer initialized
[  149.023020] Bluetooth: RFCOMM socket layer initialized
[  149.023036] Bluetooth: RFCOMM TTY layer initialized
[  149.023039] Bluetooth: RFCOMM ver 1.8
[  152.887458] NET: Registered protocol family 10
[  152.887600] lo: Disabled Privacy Extensions
```

---

### Post by Inxsible on 2007-07-11
> **-Soul_Reaper- said:**
> The cables are plugged in, but it just calls it 'cd-rom1', and it won't burn cds!
Do i need drivers?
Help is appreciated, thanks.
 
If you upgraded the kernel from -15 to -16, then CD-ROM 1 is just a phantom drive. Do you see another cd or dvd drive or just this one?
 
If you remove the entry for the cd from the fstab, that will get rid of the phantom drive for you.
 
if you dont see any other, then you might have a problem. There are solutions on the forums try searching for them.

---

### Post by -Soul_Reaper- on 2007-07-12
By the way i have 2 disc drives, one dvd-rom. the other the cd burner.

All i need to know is if unplugging the dvd one, then plug the cd burner with it's cables, will it work.
edit: oh well, i'll just do it and hope it works.

---

