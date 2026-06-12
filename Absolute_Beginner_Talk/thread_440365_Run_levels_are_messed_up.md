---
title: "Run levels are messed up"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by k1001001 on 2007-05-11
Whenever I switch from the GUI (run level 6) to the command prompt (run level 1), my computer never quite makes it there for some reason. After using the Ctrl-Alt-F1 combo or typing 'sudo init 1' in the terminal, the screen just goes to a jumbled mess and never goes to the runlevel. It used to, but now it no longer does. Any clue as to what the problem could be?

---

### Post by deepwave on 2007-05-11
Err... you really should not be changing runlevels...  I think you mean changing virtual terminals, cause thats what CTRL+ALT+F1 does.  Do I understand you right?

---

### Post by k1001001 on 2007-05-11
Yes. I guess the correct term is virtual terminals. Anyways, I used to be able to do this, but now I can't.

---

### Post by Nekiruhs on 2007-05-11
Try using virtual terminal 2 through 5.

---

### Post by k1001001 on 2007-05-13
Using virtual terminals 2-5 has the same effect as using virtual terminal 1. Something is obviously messed up.

---

### Post by deepwave on 2007-05-18
Hmm... I don't know if this will help but: see if dmesg gives any hints to want might be happening.
Additonally you could check /var/log/messages to see if something odd is occuring.

Also if you do CTRL+ALT+F1 and then CTRL+ALT+F7 (at least thats the default for my system) will it go back to the GUI?

---

### Post by k1001001 on 2007-05-20
dmesg
```

keith@keith-laptop:~$ dmesg
[17179569.184000] Linux version 2.6.15-28-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue Mar 13 20:49:31 UTC 2007
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000d8000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000003ef70000 (usable)
[17179569.184000]  BIOS-e820: 000000003ef70000 - 000000003ef7b000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000003ef7b000 - 000000003ef80000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000003ef80000 - 0000000040000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fffe0000 - 0000000100000000 (reserved)
[17179569.184000] 111MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f7f30
[17179569.184000] On node 0 totalpages: 257904
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 28528 pages, LIFO batch:7
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f7f90
[17179569.184000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x3ef7626b
[17179569.184000] ACPI: FADT (v001 AMDK8  PTLTW    0x06040000 PTL_ 0x000f4240) @ 0x3ef7ae87
[17179569.184000] ACPI: SSDT (v001 PTLTD  POWERNOW 0x06040000  LTP 0x00000001) @ 0x3ef7aefb
[17179569.184000] ACPI: MADT (v001 PTLTD         APIC   0x06040000  LTP 0x00000000) @ 0x3ef7afb0
[17179569.184000] ACPI: DSDT (v001  VIA   PTL_ACPI 0x06040000 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x4008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:12 APIC version 16
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 3, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ10 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 50000000 (gap: 40000000:bffe0000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda2 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[17179569.184000] Detected 1603.983 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179572.204000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179572.208000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)[17179572.228000] Memory: 1012060k/1031616k available (1977k kernel code, 18804k reserved, 605k data, 288k init, 114112k highmem)
[17179572.228000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179572.308000] Calibrating delay using timer specific routine.. 3210.89 BogoMIPS (lpj=6421782)
[17179572.308000] Security Framework v1.0.0 initialized
[17179572.308000] SELinux:  Disabled at boot.
[17179572.308000] Mount-cache hash table entries: 512
[17179572.308000] CPU: After generic identify, caps: 078bfbff c1d3fbff 00000000 00000000 00000000 00000000 00000000
[17179572.308000] CPU: After vendor identify, caps: 078bfbff c1d3fbff 00000000 00000000 00000000 00000000 00000000
[17179572.308000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179572.308000] CPU: L2 Cache: 128K (64 bytes/line)
[17179572.308000] CPU: After all inits, caps: 078bfbff c1d3fbff 00000000 00000410 00000000 00000000 00000000
[17179572.308000] mtrr: v2.0 (20020519)
[17179572.308000] CPU: AMD Opteron(tm) Processor Dublin 2800+    stepping 00
[17179572.308000] Enabling fast FPU save and restore... done.
[17179572.308000] Enabling unmasked SIMD FPU exception support... done.
[17179572.308000] Checking 'hlt' instruction... OK.
[17179572.324000] checking if image is initramfs... it is
[17179572.932000] Freeing initrd memory: 6619k freed
[17179572.940000] ACPI: Looking for DSDT ... not found!
[17179572.964000] ENABLING IO-APIC IRQs
[17179572.968000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179573.108000] NET: Registered protocol family 16
[17179573.108000] EISA bus registered
[17179573.108000] ACPI: bus type pci registered
[17179573.108000] PCI: PCI BIOS revision 2.10 entry at 0xfd8bc, last bus=1
[17179573.108000] PCI: Using configuration type 1
[17179573.108000] ACPI: Subsystem revision 20051216
[17179573.312000] ACPI: Interpreter enabled
[17179573.312000] ACPI: Using IOAPIC for interrupt routing
[17179573.312000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179573.312000] PCI: Probing PCI hardware (bus 00)
[17179573.312000] PCI quirk: region 4000-407f claimed by vt8235 PM
[17179573.312000] PCI quirk: region 8100-810f claimed by vt8235 SMB
[17179573.312000] Boot video device is 0000:01:00.0
[17179573.312000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179573.324000] ACPI: PCI Interrupt Link [ALKA] (IRQs 16 17 18 19 20 21 22 23) *9, disabled.
[17179573.324000] ACPI: PCI Interrupt Link [ALKB] (IRQs 16 17 18 19 20 21 22 23) *11, disabled.
[17179573.324000] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *10, disabled.
[17179573.324000] ACPI: PCI Interrupt Link [ALKD] (IRQs 21) *7, disabled.
[17179573.324000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 *9 12 14 15)
[17179573.324000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 12 14 15) *11[17179573.324000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 11 12 14 15) *10[17179573.324000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 *7 9 10 11 12 14 15)
[17179573.328000] ACPI: Power Resource [FN10] (off)
[17179573.328000] ACPI: Power Resource [FN11] (off)
[17179573.328000] ACPI: Power Resource [FN12] (off)
[17179573.328000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179573.328000] pnp: PnP ACPI init
[17179573.332000] pnp: PnP ACPI: found 8 devices
[17179573.332000] PnPBIOS: Disabled by ACPI PNP
[17179573.332000] PCI: Using ACPI for IRQ routing
[17179573.332000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179573.336000] pnp: 00:05: ioport range 0x4d0-0x4d1 has been reserved
[17179573.336000] pnp: 00:05: ioport range 0xfe10-0xfe11 could not be reserved
[17179573.336000] pnp: 00:05: ioport range 0xfe00-0xfe00 has been reserved
[17179573.336000] pnp: 00:05: ioport range 0x4000-0x407f could not be reserved
[17179573.336000] pnp: 00:05: ioport range 0x8100-0x811f could not be reserved
[17179573.336000] PCI: Failed to allocate mem resource #6:10000@fc000000 for 0000:01:00.0
[17179573.336000] PCI: Bridge: 0000:00:01.0
[17179573.336000]   IO window: disabled.
[17179573.336000]   MEM window: e9000000-e9ffffff
[17179573.336000]   PREFETCH window: f8000000-fbffffff
[17179573.336000] PCI: Bus 2, cardbus bridge: 0000:00:09.0
[17179573.336000]   IO window: 00001c00-00001cff
[17179573.336000]   IO window: 00002000-000020ff
[17179573.336000]   PREFETCH window: 50000000-51ffffff
[17179573.336000]   MEM window: 52000000-53ffffff
[17179573.336000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179573.336000] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 169
[17179573.336000] audit: initializing netlink socket (disabled)
[17179573.336000] audit(1179701823.336:1): initialized
[17179573.336000] highmem bounce pool size: 64 pages
[17179573.336000] VFS: Disk quotas dquot_6.5.1
[17179573.336000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179573.336000] Initializing Cryptographic API
[17179573.336000] io scheduler noop registered
[17179573.336000] io scheduler anticipatory registered
[17179573.336000] io scheduler deadline registered
[17179573.336000] io scheduler cfq registered
[17179573.336000] isapnp: Scanning for PnP cards...
[17179573.688000] isapnp: No Plug & Play device found
[17179573.704000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179573.704000] i8042.c: Detected active multiplexing controller, rev 1.1.
[17179573.704000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[17179573.704000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[17179573.704000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[17179573.704000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[17179573.704000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179573.704000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179573.708000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179573.708000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179573.708000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179573.708000] mice: PS/2 mouse device common for all mice
[17179573.708000] EISA: Probing bus 0 at eisa.0
[17179573.708000] Cannot allocate resource for EISA slot 1
[17179573.708000] Cannot allocate resource for EISA slot 2
[17179573.708000] Cannot allocate resource for EISA slot 4
[17179573.708000] EISA: Detected 0 cards.
[17179573.708000] NET: Registered protocol family 2
[17179573.748000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179573.748000] TCP established hash table entries: 131072 (order: 7, 524288 bytes)
[17179573.748000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[17179573.748000] TCP: Hash tables configured (established 131072 bind 65536)
[17179573.748000] TCP reno registered
[17179573.748000] TCP bic registered
[17179573.748000] NET: Registered protocol family 1
[17179573.748000] NET: Registered protocol family 8
[17179573.748000] NET: Registered protocol family 20
[17179573.748000] Using IPI Shortcut mode
[17179573.748000] ACPI wakeup devices:
[17179573.748000] PCI0 USB1 USB2 USB3 USB4 Z003 Z00B  LID
[17179573.748000] ACPI: (supports S0 S3 S4 S5)
[17179573.748000] Freeing unused kernel memory: 288k freed
[17179573.808000] vga16fb: initializing
[17179573.808000] vga16fb: mapped to 0xc00a0000
[17179573.960000] Console: switching to colour frame buffer device 80x25
[17179573.960000] fb0: VGA16 VGA frame buffer device
[17179574.316000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179575.060000] Capability LSM initialized
[17179575.100000] ACPI: Fan [FN1] (off)
[17179575.100000] ACPI: Fan [FN2] (off)
[17179575.100000] ACPI: Fan [FN3] (off)
[17179575.120000] ACPI: Thermal Zone [THRM] (56 C)
[17179575.820000] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[17179575.820000] **** SET: Misaligned resource pointer: df82c0c2 Type 07 Len 0
[17179575.820000] ACPI: PCI Interrupt Link [ALKA] disabled and referenced, BIOS bug.
[17179575.820000] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 23
[17179575.820000] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 23
[17179575.820000] ACPI: PCI Interrupt 0000:00:11.1[A] -> Link [ALKA] -> GSI 23 (level, low) -> IRQ 177
[17179575.820000] PCI: Via IRQ fixup for 0000:00:11.1, from 0 to 1
[17179575.820000] VP_IDE: chipset revision 6
[17179575.820000] VP_IDE: not 100% native mode: will probe irqs later
[17179575.820000] VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
[17179575.820000]     ide0: BM-DMA at 0x1860-0x1867, BIOS settings: hda:DMA, hdb:pio
[17179575.820000]     ide1: BM-DMA at 0x1868-0x186f, BIOS settings: hdc:DMA, hdd:pio
[17179575.820000] Probing IDE interface ide0...
[17179576.236000] hda: IC25N040ATMR04-0, ATA DISK drive
[17179576.908000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179576.928000] Probing IDE interface ide1...
[17179577.796000] hdc: Slimtype DVDRW SOSW-852S, ATAPI CD/DVD-ROM drive
[17179578.468000] ide1 at 0x170-0x177,0x376 on irq 15
[17179578.476000] hda: max request size: 1024KiB
[17179578.484000] hda: 78140160 sectors (40007 MB) w/1740KiB Cache, CHS=16383/255/63, UDMA(100)
[17179578.484000] hda: cache flushes supported
[17179578.484000]  hda: hda1 hda2 hda3 hda4 < hda5 hda6 >
[17179578.636000] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179578.636000] Uniform CD-ROM driver Revision: 3.20
[17179580.736000] usbcore: registered new driver usbfs
[17179580.736000] usbcore: registered new driver hub
[17179580.736000] USB Universal Host Controller Interface driver v2.3
[17179580.736000] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 185
[17179580.736000] uhci_hcd 0000:00:10.0: UHCI Host Controller
[17179580.740000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[17179580.740000] uhci_hcd 0000:00:10.0: irq 185, io base 0x00001800
[17179580.740000] hub 1-0:1.0: USB hub found
[17179580.740000] hub 1-0:1.0: 2 ports detected
[17179580.844000] ACPI: PCI Interrupt 0000:00:10.1[B] -> GSI 21 (level, low) -> IRQ 185
[17179580.844000] PCI: Via IRQ fixup for 0000:00:10.1, from 11 to 9
[17179580.844000] uhci_hcd 0000:00:10.1: UHCI Host Controller
[17179580.844000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[17179580.844000] uhci_hcd 0000:00:10.1: irq 185, io base 0x00001820
[17179580.844000] hub 2-0:1.0: USB hub found
[17179580.844000] hub 2-0:1.0: 2 ports detected
[17179580.948000] ACPI: PCI Interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> IRQ 185
[17179580.948000] PCI: Via IRQ fixup for 0000:00:10.2, from 10 to 9
[17179580.948000] uhci_hcd 0000:00:10.2: UHCI Host Controller
[17179580.948000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[17179580.948000] uhci_hcd 0000:00:10.2: irq 185, io base 0x00001840
[17179580.948000] hub 3-0:1.0: USB hub found
[17179580.948000] hub 3-0:1.0: 2 ports detected
[17179581.052000] ACPI: PCI Interrupt 0000:00:10.3[D] -> GSI 21 (level, low) -> IRQ 185
[17179581.052000] PCI: Via IRQ fixup for 0000:00:10.3, from 7 to 9
[17179581.052000] ehci_hcd 0000:00:10.3: EHCI Host Controller
[17179581.052000] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[17179581.052000] ehci_hcd 0000:00:10.3: irq 185, io mem 0xe8002000
[17179581.052000] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179581.052000] hub 4-0:1.0: USB hub found
[17179581.052000] hub 4-0:1.0: 6 ports detected
[17179581.416000] Attempting manual resume
[17179581.472000] EXT3-fs: mounted filesystem with ordered data mode.
[17179581.472000] kjournald starting.  Commit interval 5 seconds
[17179600.112000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179600.160000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179600.404000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 19 (level, low) -> IRQ 193
[17179600.404000] rt2500 1.1.0 CVS 2005/07/10 http://rt2x00.serialmonkey.com
[17179600.760000] rt2500 EEPROM:  1  2  3  4  5  6  7  8  9 10 11 12 13 14  Channel
[17179600.760000] rt2500 EEPROM:  6  6  6  6  6  6  7  7  7  7  7  7  7  7  dBm Maximum
[17179600.828000] rt2500 EEPROM:  1  2  3  4  5  6  7  8  9 10 11 12 13 14  Channel
[17179600.828000] rt2500 EEPROM:  6  6  6  6  6  6  7  7  7  7  7  7  7  7  dBm Maximum
[17179600.856000] Linux agpgart interface v0.101 (c) Dave Jones
[17179600.880000] agpgart: Detected AGP bridge 0
[17179600.888000] agpgart: AGP aperture is 128M @ 0xf0000000
[17179601.036000] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 169
[17179601.036000] Yenta: CardBus bridge found at 0000:00:09.0 [1509:2750]
[17179601.036000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179601.036000] Yenta: Routing CardBus interrupts to PCI
[17179601.036000] Yenta TI: socket 0000:00:09.0, mfunc 0x01021002, devctl 0x44
[17179601.268000] Yenta: ISA IRQ mask 0x0020, PCI irq 169
[17179601.268000] Socket status: 30000006
[17179601.292000] Real Time Clock Driver v1.12
[17179601.452000] input: PC Speaker as /class/input/input1
[17179601.660000] input: PS/2 Mouse as /class/input/input2
[17179601.676000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input3
[17179601.900000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[17179601.904000] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 177
[17179601.904000] PCI: Via IRQ fixup for 0000:00:12.0, from 9 to 1
[17179602.000000] irda_init()
[17179602.000000] NET: Registered protocol family 23
[17179602.172000] rt2500 EEPROM:  1  2  3  4  5  6  7  8  9 10 11 12 13 14  Channel
[17179602.172000] rt2500 EEPROM:  6  6  6  6  6  6  7  7  7  7  7  7  7  7  dBm Maximum
[17179602.176000] eth0: VIA Rhine II at 0x11400, 00:40:ca:ce:df:29, IRQ 177.
[17179602.176000] eth0: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[17179602.512000] ts: Compaq touchscreen protocol output
[17179603.188000] PCI: Enabling device 0000:00:11.6 (0000 -> 0001)
[17179603.188000] **** SET: Misaligned resource pointer: f7dd52c2 Type 07 Len 0
[17179603.188000] ACPI: PCI Interrupt Link [ALKC] disabled and referenced, BIOS bug.
[17179603.188000] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
[17179603.188000] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[17179603.188000] ACPI: PCI Interrupt 0000:00:11.6[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 201
[17179603.188000] PCI: Via IRQ fixup for 0000:00:11.6, from 0 to 9
[17179603.192000] PCI: Setting latency timer of device 0000:00:11.6 to 64
[17179603.204000] cs: IO port probe 0x100-0x3af: clean.
[17179603.208000] cs: IO port probe 0x3e0-0x4ff: clean.
[17179603.208000] cs: IO port probe 0x820-0x8ff: clean.
[17179603.208000] cs: IO port probe 0xc00-0xcf7: clean.
[17179603.208000] cs: IO port probe 0xa00-0xaff: clean.
[17179603.448000] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 201
[17179603.448000] PCI: Via IRQ fixup for 0000:00:11.5, from 10 to 9
[17179603.448000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[17179603.456000] NET: Registered protocol family 17
[17179604.756000] lp: driver loaded but no devices found
[17179604.836000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[17179604.868000] usbcore: registered new driver ndiswrapper
[17179604.920000] Adding 1076308k swap on /dev/hda1.  Priority:-1 extents:1 across:1076308k
[17179605.060000] EXT3 FS on hda2, internal journal
[17179605.280000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179605.280000] md: bitmap version 4.39
[17179606.076000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[17179607.456000] cdrom: open failed.
[17179609.332000] kjournald starting.  Commit interval 5 seconds
[17179609.352000] EXT3 FS on hda5, internal journal
[17179609.352000] EXT3-fs: mounted filesystem with ordered data mode.
[17179612.648000] ACPI: AC Adapter [ACAD] (on-line)
[17179612.692000] ACPI: Battery Slot [BAT0] (battery present)
[17179612.768000] ACPI: Power Button (FF) [PWRF]
[17179612.768000] ACPI: Power Button (CM) [PWRB]
[17179612.768000] ACPI: Lid Switch [LID]
[17179612.876000] ibm_acpi: ec object not found
[17179612.916000] pcc_acpi: loading...
[17179613.084000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[17179613.640000] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.50.4)
[17179613.640000] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x6 (1400 mV)
[17179613.640000] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x18 (950 mV)
[17179613.640000] cpu_init done, current fid 0x8, vid 0x6
[17179619.176000] eth0: link down
[17179624.684000] [drm] Initialized drm 1.0.1 20051102
[17179624.724000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 209
[17179624.724000] PCI: Via IRQ fixup for 0000:01:00.0, from 9 to 1
[17179624.724000] [drm] Initialized via 2.7.4 20051116 on minor 0
[17179624.724000] [drm] Initialized via 2.7.4 20051116 on minor 1
[17179624.804000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[17179624.804000] agpgart: Device is in legacy mode, falling back to 2.x
[17179624.804000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[17179624.804000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[17179625.264000] irq 209: nobody cared (try booting with the "irqpoll" option)
[17179625.264000]  [<c013ee82>] __report_bad_irq+0x22/0x80
[17179625.264000]  [<c013ef78>] note_interrupt+0x68/0xc0
[17179625.264000]  [<c013e83c>] __do_IRQ+0xbc/0xe0
[17179625.264000]  [<c010596a>] do_IRQ+0x1a/0x30
[17179625.264000]  [<c01040aa>] common_interrupt+0x1a/0x20
[17179625.264000]  [<c014febe>] do_wp_page+0xde/0x350
[17179625.264000]  [<c013e813>] __do_IRQ+0x93/0xe0
[17179625.264000]  [<c0151025>] __handle_mm_fault+0x1d5/0x210
[17179625.264000]  [<c0116a36>] do_page_fault+0x216/0x61a
[17179625.264000]  [<c0116820>] do_page_fault+0x0/0x61a
[17179625.264000]  [<c010419f>] error_code+0x4f/0x60
[17179625.264000] handlers:
[17179625.264000] [<f8ced030>] (via_driver_irq_handler+0x0/0x1a0 [via])
[17179625.264000] Disabling IRQ #209
[17179625.680000] ppdev: user-space parallel port driver
[17179626.880000] apm: BIOS not found.
[17179628.528000] Bluetooth: Core ver 2.8
[17179628.528000] NET: Registered protocol family 31
[17179628.528000] Bluetooth: HCI device and connection manager initialized
[17179628.528000] Bluetooth: HCI socket layer initialized
[17179628.576000] Bluetooth: L2CAP ver 2.8
[17179628.576000] Bluetooth: L2CAP socket layer initialized
[17179628.732000] Bluetooth: RFCOMM socket layer initialized
[17179628.732000] Bluetooth: RFCOMM TTY layer initialized
[17179628.732000] Bluetooth: RFCOMM ver 1.7
[17179849.756000] psmouse.c: GlidePoint at isa0060/serio4/input0 lost synchronization, throwing 1 bytes away.
[17185797.664000] usb 2-1: new full speed USB device using uhci_hcd and address 2
[17185798.160000] usbcore: registered new driver snd-usb-audio
[17188807.816000] usb 2-1: USB disconnect, address 2
```

I really have no idea what to look for in all that. /var/log/messages looked similar but was much longer.

---

### Post by deepwave on 2007-05-21
Look at this:

```
[17179624.804000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[17179624.804000] agpgart: Device is in legacy mode, falling back to 2.x
[17179624.804000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[17179624.804000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[17179625.264000] irq 209: nobody cared (try booting with the "irqpoll" option)
[17179625.264000]  [<c013ee82>] __report_bad_irq+0x22/0x80
[17179625.264000]  [<c013ef78>] note_interrupt+0x68/0xc0
[17179625.264000]  [<c013e83c>] __do_IRQ+0xbc/0xe0
[17179625.264000]  [<c010596a>] do_IRQ+0x1a/0x30
[17179625.264000]  [<c01040aa>] common_interrupt+0x1a/0x20
[17179625.264000]  [<c014febe>] do_wp_page+0xde/0x350
[17179625.264000]  [<c013e813>] __do_IRQ+0x93/0xe0
[17179625.264000]  [<c0151025>] __handle_mm_fault+0x1d5/0x210
[17179625.264000]  [<c0116a36>] do_page_fault+0x216/0x61a
[17179625.264000]  [<c0116820>] do_page_fault+0x0/0x61a
[17179625.264000]  [<c010419f>] error_code+0x4f/0x60
[17179625.264000] handlers:
[17179625.264000] [<f8ced030>] (via_driver_irq_handler+0x0/0x1a0 [via])
```

I am guessing your graphics cards is erroring out when it tries to enter into the graphic mode of the virtual terminal.  What kind of graphics card do you have?  Maybe when you updated your kernel, something broke or your graphics card is not configured right.

---

