---
title: "No Audio with Ubuntu 6.10"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by moebiu.x on 2006-12-17
Problem like title.
NO sound from my PC.

I've tried to search solutions in my official italian forum, but with no results.
Please, someone have the solution to this problem?

PS: I'm a very very very very "Absolute Beginner".

bye

---

### Post by CAN-CAN on 2006-12-17
What's your soundcard?

---

### Post by mordox on 2006-12-17
try to check out the kernel messages by using dmesg | less and see if your sound card is being detected. 

If it is detected then check whether you are having the correct plugins. The examples folder in you home folder has a bunch of video / audio files. Go ahead and try to play them using totem. By default that sort of files are supported by ubuntu 6.10 .  You can also install mplayer / vlc to play these other set of files that your system is not able to play ..

---

### Post by moebiu.x on 2006-12-17
> **CAN-CAN said:**
> What's your soundcard?

I don't know. I thing an integrated card.
with:

```
 lspci -v
```

the result is:

```
moebius@joshua:~$ lspci -v
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 651 Host (rev 01)
        Subsystem: Silicon Integrated Systems [SiS] 651 Host
        Flags: bus master, medium devsel, latency 32
        Memory at e8000000 (32-bit, non-prefetchable) [size=64M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: ec000000-ec0fffff
        Prefetchable memory behind bridge: e0000000-e7ffffff

00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 04)
        Flags: bus master, medium devsel, latency 0

00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
        Flags: medium devsel
        I/O ports at 10c0 [size=32]

00:02.3 FireWire (IEEE 1394): Silicon Integrated Systems [SiS] FireWire Controller (prog-if 10 [OHCI])
        Flags: bus master, medium devsel, latency 32, IRQ 177
        Memory at ec134000 (32-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at 30000000 [disabled] [size=128K]
        Capabilities: <access denied>

00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (prog-if 80 [Master])
        Subsystem: Acer Incorporated [ALI] Unknown device 0018
        Flags: bus master, medium devsel, latency 128, IRQ 169
        I/O ports at 4000 [size=16]
        Capabilities: <access denied>

00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
        Subsystem: Acer Incorporated [ALI] Unknown device 0018
        Flags: bus master, medium devsel, latency 32, IRQ 217
        I/O ports at b400 [size=256]
        I/O ports at b800 [size=128]
        Capabilities: <access denied>

00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 0018
        Flags: bus master, medium devsel, latency 32, IRQ 185
        Memory at ec130000 (32-bit, non-prefetchable) [size=4K]

00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 0018
        Flags: bus master, medium devsel, latency 32, IRQ 193
        Memory at ec131000 (32-bit, non-prefetchable) [size=4K]

00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 0018
        Flags: bus master, medium devsel, latency 32, IRQ 201
        Memory at ec132000 (32-bit, non-prefetchable) [size=4K]

00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller (prog-if 20 [EHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 0018
        Flags: bus master, medium devsel, latency 32, IRQ 209
        Memory at ec133000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:07.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
        Subsystem: U.S. Robotics Unknown device 2013
        Flags: bus master, medium devsel, latency 32, IRQ 5
        Memory at ec120000 (32-bit, non-prefetchable) [size=64K]
        I/O ports at bc00 [size=8]
        Capabilities: <access denied>

00:0f.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Realtek Semiconductor Co., Ltd. RT8139
        Flags: bus master, medium devsel, latency 32, IRQ 217
        I/O ports at c000 [size=256]
        Memory at ec135000 (32-bit, non-prefetchable) [size=256]
        [virtual] Expansion ROM at 30020000 [disabled] [size=64K]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV200 QW [Radeon 7500] (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc Unknown device 0f2a
        Flags: bus master, stepping, 66MHz, medium devsel, latency 32, IRQ 169
        Memory at e0000000 (32-bit, prefetchable) [size=128M]
        I/O ports at 9000 [size=256]
        Memory at ec020000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at ec000000 [disabled] [size=128K]
        Capabilities: <access denied>

moebius@joshua:~$ 

```

> **mordox said:**
> try to check out the kernel messages by using dmesg | less and see if your sound card is being detected. 


I've tried the comand but i don't know how read the result. :oops:

---

### Post by kilou on 2006-12-17
Same problem here: no sound since yesterday :mad: Probably due to an update but I don't know which one.

---

### Post by moebiu.x on 2006-12-17
Mine problem isn't due an update. I've just installed ubuntu!

---

### Post by mordox on 2006-12-17
post the dmesg output

---

### Post by kilou on 2006-12-17
Yes but probably the update ran at the end of the install. The sound was working fine until yesterday on my system and then for no reason (and I don't really noticed when) it stopped working. But my soundcard is detected...and the volume is not muted!

---

### Post by mordox on 2006-12-17
if u have mplayer try and check if its console output tells you abt some error message like unable to open /dev/***

---

### Post by moebiu.x on 2006-12-17
> **mordox said:**
> post the dmesg output

```
moebius@joshua:~$ dmesg
[17179569.184000] Linux version 2.6.17-10-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Tue Dec 5 22:28:26 UTC 2006 (Ubuntu 2.6.17-10.34-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[17179569.184000]  BIOS-e820: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000001fff3000 - 0000000020000000 (ACPI data)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 511MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f50e0
[17179569.184000] On node 0 totalpages: 131056
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 126960 pages, LIFO batch:31
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 AWARD                                 ) @ 0x000f6f60
[17179569.184000] ACPI: RSDT (v001 AWARD  AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff3000
[17179569.184000] ACPI: FADT (v001 AWARD  AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff3040
[17179569.184000] ACPI: MADT (v001 AWARD  AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff6e00
[17179569.184000] ACPI: DSDT (v001 AWARD  AWRDACPI 0x00001000 MSFT 0x0100000d) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:2 APIC version 20
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 20, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 dfl dfl)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda2 ro quiet splash locale=it_IT
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[17179569.184000] Detected 2390.708 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.392000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.392000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179569.404000] Memory: 510056k/524224k available (1910k kernel code, 13596k reserved, 1069k data, 308k init, 0k highmem)
[17179569.404000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.484000] Calibrating delay using timer specific routine.. 4785.72 BogoMIPS (lpj=9571457)
[17179569.484000] Security Framework v1.0.0 initialized
[17179569.484000] SELinux:  Disabled at boot.
[17179569.484000] Mount-cache hash table entries: 512
[17179569.484000] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00000400 00000000 00000000
[17179569.484000] CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 00000400 00000000 00000000
[17179569.484000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[17179569.484000] CPU: L2 cache: 512K
[17179569.484000] CPU: Hyper-Threading is disabled
[17179569.484000] CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 00000400 00000000 00000000
[17179569.484000] Checking 'hlt' instruction... OK.
[17179569.500000] SMP alternatives: switching to UP code
[17179569.500000] Freeing SMP alternatives: 16k freed
[17179569.500000] checking if image is initramfs... it is
[17179570.020000] Freeing initrd memory: 5323k freed
[17179570.020000] ACPI: Core revision 20060707
[17179570.028000] ACPI: Looking for DSDT ... not found!
[17179570.040000] CPU0: Intel(R) Pentium(R) 4 CPU 2.40GHz stepping 07
[17179570.040000] Total of 1 processors activated (4785.72 BogoMIPS).
[17179570.040000] ENABLING IO-APIC IRQs
[17179570.040000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179570.184000] Brought up 1 CPUs
[17179570.184000] migration_cost=0
[17179570.184000] NET: Registered protocol family 16
[17179570.184000] EISA bus registered
[17179570.184000] ACPI: bus type pci registered
[17179570.204000] PCI: PCI BIOS revision 2.10 entry at 0xfbb60, last bus=1
[17179570.204000] PCI: Using configuration type 1
[17179570.204000] Setting up standard PCI resources
[17179570.228000] ACPI: Interpreter enabled
[17179570.228000] ACPI: Using IOAPIC for interrupt routing
[17179570.228000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.228000] PCI: Probing PCI hardware (bus 00)
[17179570.228000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179570.232000] Uncovering SIS962 that hid as a SIS503 (compatible=1)
[17179570.232000] Enabling SiS 96x SMBus.
[17179570.232000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:02.5
[17179570.232000] Boot video device is 0000:01:00.0
[17179570.232000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.260000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 14 15)
[17179570.260000] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 14 15)
[17179570.260000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 14 15)
[17179570.260000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
[17179570.260000] ACPI: PCI Interrupt Link [LNKE] (IRQs *3 4 5 6 7 9 10 11 14 15)
[17179570.264000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 9 10 11 14 15)
[17179570.264000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11 14 15)
[17179570.264000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 14 15)
[17179570.264000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.264000] pnp: PnP ACPI init
[17179570.268000] pnp: PnP ACPI: found 13 devices
[17179570.268000] PnPBIOS: Disabled by ACPI PNP
[17179570.272000] PCI: Using ACPI for IRQ routing
[17179570.272000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.280000] PCI: Bridge: 0000:00:01.0
[17179570.280000]   IO window: 9000-9fff
[17179570.280000]   MEM window: ec000000-ec0fffff
[17179570.280000]   PREFETCH window: e0000000-e7ffffff
[17179570.280000] NET: Registered protocol family 2
[17179570.312000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179570.312000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[17179570.312000] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[17179570.312000] TCP: Hash tables configured (established 16384 bind 8192)
[17179570.312000] TCP reno registered
[17179570.312000] audit: initializing netlink socket (disabled)
[17179570.312000] audit(1166353342.312:1): initialized
[17179570.312000] VFS: Disk quotas dquot_6.5.1
[17179570.312000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.312000] Initializing Cryptographic API
[17179570.312000] io scheduler noop registered
[17179570.312000] io scheduler anticipatory registered
[17179570.312000] io scheduler deadline registered
[17179570.312000] io scheduler cfq registered (default)
[17179570.312000] isapnp: Scanning for PnP cards...
[17179570.668000] isapnp: No Plug & Play device found
[17179570.692000] Real Time Clock Driver v1.12ac
[17179570.692000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179570.692000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179570.692000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179570.692000] mice: PS/2 mouse device common for all mice
[17179570.696000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179570.696000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179570.696000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179570.696000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[17179570.696000] PNP: PS/2 controller doesn't have AUX irq; using default 12
[17179571.764000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179571.764000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179571.796000] EISA: Probing bus 0 at eisa.0
[17179571.796000] Cannot allocate resource for EISA slot 1
[17179571.796000] Cannot allocate resource for EISA slot 4
[17179571.796000] EISA: Detected 0 cards.
[17179571.796000] TCP bic registered
[17179571.796000] NET: Registered protocol family 1
[17179571.796000] NET: Registered protocol family 8
[17179571.796000] NET: Registered protocol family 20
[17179571.796000] Using IPI No-Shortcut mode
[17179571.796000] ACPI: (supports S0 S3 S4 S5)
[17179571.796000] Freeing unused kernel memory: 308k freed
[17179571.980000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179572.028000] atkbd.c: Spurious ACK on isa0060/serio0. Some program, like XFree86, might be trying access hardware directly.
[17179572.076000] atkbd.c: Spurious ACK on isa0060/serio0. Some program, like XFree86, might be trying access hardware directly.
[17179572.124000] atkbd.c: Spurious ACK on isa0060/serio0. Some program, like XFree86, might be trying access hardware directly.
[17179572.172000] atkbd.c: Spurious ACK on isa0060/serio0. Some program, like XFree86, might be trying access hardware directly.
[17179572.220000] atkbd.c: Spurious ACK on isa0060/serio0. Some program, like XFree86, might be trying access hardware directly.
[17179573.008000] Capability LSM initialized
[17179573.044000] ACPI: Fan [FAN] (on)
[17179573.052000] ACPI: Thermal Zone [THRM] (21 C)
[17179573.580000] SIS5513: IDE controller at PCI slot 0000:00:02.5
[17179573.580000] ACPI: PCI Interrupt 0000:00:02.5[A] -> GSI 16 (level, low) -> IRQ 169
[17179573.580000] SIS5513: chipset revision 0
[17179573.580000] SIS5513: not 100% native mode: will probe irqs later
[17179573.580000] SIS5513: SiS 962/963 MuTIOL IDE UDMA133 controller
[17179573.580000]     ide0: BM-DMA at 0x4000-0x4007, BIOS settings: hda:DMA, hdb:pio
[17179573.580000]     ide1: BM-DMA at 0x4008-0x400f, BIOS settings: hdc:DMA, hdd:DMA
[17179573.580000] Probing IDE interface ide0...
[17179573.872000] hda: ST340810A, ATA DISK drive
[17179574.548000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179574.552000] Probing IDE interface ide1...
[17179575.292000] hdc: LITE-ON LTR-40125S, ATAPI CD/DVD-ROM drive
[17179576.080000] hdd: DVD-ROM BDV316C, ATAPI CD/DVD-ROM drive
[17179576.140000] ide1 at 0x170-0x177,0x376 on irq 15
[17179576.148000] hda: max request size: 128KiB
[17179576.160000] hda: 78165360 sectors (40020 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[17179576.160000] hda: cache flushes not supported
[17179576.160000]  hda: hda1 hda2 hda3 < hda5 >
[17179576.260000] hdc: ATAPI 48X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179576.260000] Uniform CD-ROM driver Revision: 3.20
[17179576.272000] hdd: ATAPI 48X DVD-ROM drive, 512kB Cache, (U)DMA
[17179577.380000] ieee1394: Initialized config rom entry `ip1394'
[17179577.380000] ACPI: PCI Interrupt 0000:00:02.3[B] -> GSI 17 (level, low) -> IRQ 177
[17179577.432000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[177]  MMIO=[ec134000-ec1347ff]  Max Packet=[2048]  IR/IT contexts=[4/6]
[17179577.452000] usbcore: registered new driver usbfs
[17179577.452000] usbcore: registered new driver hub
[17179577.456000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179577.456000] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 185
[17179577.456000] ohci_hcd 0000:00:03.0: OHCI Host Controller
[17179577.456000] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[17179577.488000] ohci_hcd 0000:00:03.0: irq 185, io mem 0xec130000
[17179577.548000] usb usb1: configuration #1 chosen from 1 choice
[17179577.548000] hub 1-0:1.0: USB hub found
[17179577.548000] hub 1-0:1.0: 2 ports detected
[17179577.656000] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 193
[17179577.656000] ohci_hcd 0000:00:03.1: OHCI Host Controller
[17179577.656000] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[17179577.684000] ohci_hcd 0000:00:03.1: irq 193, io mem 0xec131000
[17179577.744000] usb usb2: configuration #1 chosen from 1 choice
[17179577.744000] hub 2-0:1.0: USB hub found
[17179577.744000] hub 2-0:1.0: 2 ports detected
[17179577.852000] ACPI: PCI Interrupt 0000:00:03.2[C] -> GSI 22 (level, low) -> IRQ 201
[17179577.852000] ohci_hcd 0000:00:03.2: OHCI Host Controller
[17179577.852000] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
[17179577.880000] ohci_hcd 0000:00:03.2: irq 201, io mem 0xec132000
[17179577.940000] usb usb3: configuration #1 chosen from 1 choice
[17179577.940000] hub 3-0:1.0: USB hub found
[17179577.940000] hub 3-0:1.0: 2 ports detected
[17179577.960000] usb 1-1: new low speed USB device using ohci_hcd and address 2
[17179578.048000] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 23 (level, low) -> IRQ 209
[17179578.048000] ehci_hcd 0000:00:03.3: EHCI Host Controller
[17179578.048000] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 4
[17179578.048000] PCI: cache line size of 128 is not supported by device 0000:00:03.3
[17179578.048000] ehci_hcd 0000:00:03.3: irq 209, io mem 0xec133000
[17179578.048000] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179578.048000] usb usb4: configuration #1 chosen from 1 choice
[17179578.048000] hub 4-0:1.0: USB hub found
[17179578.048000] hub 4-0:1.0: 6 ports detected
[17179578.200000] Attempting manual resume
[17179578.248000] kjournald starting.  Commit interval 5 seconds
[17179578.248000] EXT3-fs: mounted filesystem with ordered data mode.
[17179578.716000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000010dc00043b62]
[17179579.064000] usb 4-5: new high speed USB device using ehci_hcd and address 4
[17179579.212000] usb 4-5: configuration #1 chosen from 1 choice
[17179579.520000] usb 1-1: new low speed USB device using ohci_hcd and address 3
[17179579.728000] usb 1-1: configuration #1 chosen from 1 choice
[17179579.732000] ohci_hcd 0000:00:03.1: wakeup
[17179580.116000] usb 2-1: new full speed USB device using ohci_hcd and address 2
[17179580.320000] usb 2-1: configuration #1 chosen from 1 choice
[17179590.012000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179590.120000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179590.212000] Linux agpgart interface v0.101 (c) Dave Jones
[17179590.252000] agpgart: Detected SiS 651 chipset
[17179590.256000] agpgart: AGP aperture is 64M @ 0xe8000000
[17179590.492000] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x10c0
[17179590.532000] Floppy drive(s): fd0 is 1.44M
[17179590.552000] FDC 0 is a post-1991 82077
[17179590.564000] input: PC Speaker as /class/input/input1
[17179590.648000] 8139too Fast Ethernet driver 0.9.27
[17179590.648000] ACPI: PCI Interrupt 0000:00:0f.0[A] -> GSI 18 (level, low) -> IRQ 217
[17179590.648000] eth0: RealTek RTL8139 at 0xe09bc000, 00:10:dc:86:d2:59, IRQ 217
[17179590.648000] eth0:  Identified 8139 chip type 'RTL-8101'
[17179590.716000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179591.124000] parport: PnPBIOS parport detected.
[17179591.124000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[17179591.212000] eth0: link up, 10Mbps, half-duplex, lpa 0x4021
[17179591.744000] usbcore: registered new driver libusual
[17179591.888000] usbcore: registered new driver hiddev
[17179591.900000] input: Logitech USB Optical Mouse as /class/input/input2
[17179591.900000] input: USB HID v1.10 Mouse [Logitech USB Optical Mouse] on usb-0000:00:03.0-1
[17179591.900000] usbcore: registered new driver usbhid
[17179591.900000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179592.688000] NET: Registered protocol family 17
[17179592.704000] SCSI subsystem initialized
[17179592.724000] Initializing USB Mass Storage driver...
[17179592.724000] scsi0 : SCSI emulation for USB Mass Storage devices
[17179592.724000] usb-storage: device found at 4
[17179592.724000] usb-storage: waiting for device to settle before scanning
[17179592.724000] scsi1 : SCSI emulation for USB Mass Storage devices
[17179592.724000] usb-storage: device found at 2
[17179592.724000] usb-storage: waiting for device to settle before scanning
[17179592.724000] scsi2 : SCSI emulation for USB Mass Storage devices
[17179592.724000] usbcore: registered new driver usb-storage
[17179592.724000] USB Mass Storage support registered.
[17179592.724000] usb-storage: device found at 2
[17179592.724000] usb-storage: waiting for device to settle before scanning
[17179592.824000] ts: Compaq touchscreen protocol output
[17179593.020000] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 217
[17179593.340000] intel8x0_measure_ac97_clock: measured 59547 usecs
[17179593.340000] intel8x0: clocking to 48000
[17179593.528000] lp0: using parport0 (interrupt-driven).
[17179593.552000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179593.552000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179593.592000] Adding 522072k swap on /dev/disk/by-uuid/6b0980c3-a579-481e-a80c-0e1ec59f5d9f.  Priority:-1 extents:1 across:522072k
[17179593.776000] EXT3 FS on hda2, internal journal
[17179596.588000] NET: Registered protocol family 10
[17179596.588000] lo: Disabled Privacy Extensions
[17179596.588000] IPv6 over IPv4 tunneling driver
[17179597.724000] usb-storage: device scan complete
[17179597.724000] usb-storage: device scan complete
[17179597.724000] usb-storage: device scan complete
[17179597.728000]   Vendor:           Model: USB Flash Memory  Rev: 5.00
[17179597.728000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179597.732000]   Vendor: General   Model: USB Disk Drive    Rev: 1.00
[17179597.732000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179597.732000]   Vendor: General   Model: USB Disk Drive    Rev: 1.00
[17179597.732000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179597.816000] sd 1:0:0:0: Attached scsi removable disk sda
[17179597.848000] sd 2:0:0:0: Attached scsi removable disk sdb
[17179598.824000] SCSI device sdc: 2013184 512-byte hdwr sectors (1031 MB)
[17179598.824000] sdc: Write Protect is off
[17179598.824000] sdc: Mode Sense: 23 00 00 00
[17179598.824000] sdc: assuming drive cache: write through
[17179598.828000] SCSI device sdc: 2013184 512-byte hdwr sectors (1031 MB)
[17179598.828000] sdc: Write Protect is off
[17179598.828000] sdc: Mode Sense: 23 00 00 00
[17179598.828000] sdc: assuming drive cache: write through
[17179598.828000]  sdc: sdc1
[17179598.828000] sd 0:0:0:0: Attached scsi removable disk sdc
[17179598.884000] sd 1:0:0:0: Attached scsi generic sg0 type 0
[17179598.884000] sd 2:0:0:0: Attached scsi generic sg1 type 0
[17179598.884000] sd 0:0:0:0: Attached scsi generic sg2 type 0
[17179607.460000] eth0: no IPv6 routers present
[17179633.520000] ACPI: Power Button (FF) [PWRF]
[17179633.520000] ACPI: Power Button (CM) [PWRB]
[17179633.520000] ACPI: Sleep Button (CM) [FUTS]
[17179633.656000] ibm_acpi: ec object not found
[17179633.692000] pcc_acpi: loading...
[17179635.804000] [drm] Initialized drm 1.0.1 20051102
[17179635.816000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179635.820000] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[17179636.568000] mtrr: 0xe0000000,0x8000000 overlaps existing 0xe0000000,0x4000000
[17179636.568000] mtrr: 0xe0000000,0x8000000 overlaps existing 0xe0000000,0x4000000
[17179636.568000] mtrr: 0xe0000000,0x8000000 overlaps existing 0xe0000000,0x4000000
[17179636.568000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17179636.568000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[17179636.568000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[17179636.872000] [drm] Setting GART location based on new memory map
[17179636.872000] [drm] writeback test succeeded in 1 usecs
[17179640.240000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179640.240000] apm: overridden by ACPI.
[17179645.992000] Bluetooth: Core ver 2.8
[17179645.992000] NET: Registered protocol family 31
[17179645.992000] Bluetooth: HCI device and connection manager initialized
[17179645.992000] Bluetooth: HCI socket layer initialized
[17179646.032000] Bluetooth: L2CAP ver 2.8
[17179646.032000] Bluetooth: L2CAP socket layer initialized
[17179646.044000] Bluetooth: RFCOMM socket layer initialized
[17179646.044000] Bluetooth: RFCOMM TTY layer initialized
[17179646.044000] Bluetooth: RFCOMM ver 1.7
[17179770.008000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17179788.148000] APIC error on CPU0: 00(40)
[17179934.212000] hdd: lost interrupt
[17180482.856000] APIC error on CPU0: 40(40)
[17181053.956000] APIC error on CPU0: 40(40)
[17181593.856000] APIC error on CPU0: 40(40)
[17181669.000000] APIC error on CPU0: 40(40)
[17181767.924000] APIC error on CPU0: 40(40)
[17182437.400000] APIC error on CPU0: 40(40)
[17182570.440000] APIC error on CPU0: 40(40)
[17182576.704000] APIC error on CPU0: 40(40)
[17182580.676000] APIC error on CPU0: 40(40)
[17182598.724000] APIC error on CPU0: 40(40)
[17182630.832000] APIC error on CPU0: 40(40)
[17182832.728000] APIC error on CPU0: 40(40)
[17183250.952000] APIC error on CPU0: 40(40)
[17183327.416000] APIC error on CPU0: 40(40)
[17183366.296000] APIC error on CPU0: 40(40)
[17183427.312000] APIC error on CPU0: 40(40)
[17183523.636000] APIC error on CPU0: 40(40)
[17183581.480000] APIC error on CPU0: 40(40)
[17183655.172000] APIC error on CPU0: 40(40)
[17183670.004000] APIC error on CPU0: 40(40)
[17183748.816000] APIC error on CPU0: 40(40)
[17184521.944000] APIC error on CPU0: 40(40)
[17184539.696000] APIC error on CPU0: 40(40)
[17184977.368000] APIC error on CPU0: 40(40)
[17185008.252000] APIC error on CPU0: 40(40)
[17185022.272000] APIC error on CPU0: 40(40)
[17185077.816000] hdd: lost interrupt
[17185082.816000] hdd: lost interrupt
[17185087.816000] hdd: lost interrupt
[17185092.816000] hdd: lost interrupt
[17185225.448000] APIC error on CPU0: 40(40)
[17185226.180000] APIC error on CPU0: 40(40)
[17185647.460000] APIC error on CPU0: 40(40)
[17185793.164000] APIC error on CPU0: 40(40)
[17185837.812000] APIC error on CPU0: 40(40)
[17185845.544000] APIC error on CPU0: 40(40)
[17186226.464000] APIC error on CPU0: 40(40)
[17186803.280000] APIC error on CPU0: 40(40)
[17187027.888000] APIC error on CPU0: 40(40)
[17187127.688000] APIC error on CPU0: 40(40)
[17187292.572000] APIC error on CPU0: 40(40)
[17187303.688000] APIC error on CPU0: 40(40)
[17187780.572000] APIC error on CPU0: 40(40)
[17187998.540000] APIC error on CPU0: 40(40)
[17188944.340000] APIC error on CPU0: 40(40)
[17188957.548000] APIC error on CPU0: 40(40)
[17189031.320000] APIC error on CPU0: 40(40)
[17189105.636000] APIC error on CPU0: 40(40)
[17189435.604000] APIC error on CPU0: 40(40)
[17189678.908000] APIC error on CPU0: 40(40)
[17190193.352000] APIC error on CPU0: 40(40)
[17190266.752000] APIC error on CPU0: 40(40)
[17190337.548000] APIC error on CPU0: 40(40)
[17190338.828000] APIC error on CPU0: 40(40)
[17193724.116000] APIC error on CPU0: 40(40)
[17193995.532000] APIC error on CPU0: 40(40)
[17195167.988000] APIC error on CPU0: 40(40)
[17195207.416000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17195207.416000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[17195207.416000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[17195434.244000] mtrr: 0xe0000000,0x8000000 overlaps existing 0xe0000000,0x4000000
[17195434.244000] mtrr: 0xe0000000,0x8000000 overlaps existing 0xe0000000,0x4000000
[17195434.248000] mtrr: 0xe0000000,0x8000000 overlaps existing 0xe0000000,0x4000000
[17195434.248000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17195434.248000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[17195434.248000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[17195434.528000] [drm] Setting GART location based on new memory map
[17195434.528000] [drm] writeback test succeeded in 1 usecs
[17195447.320000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17195517.308000] APIC error on CPU0: 40(40)
[17195586.708000] APIC error on CPU0: 40(40)
[17195605.072000] APIC error on CPU0: 40(40)
[17196053.116000] APIC error on CPU0: 40(40)
moebius@joshua:~$ 

```

---

### Post by kilou on 2006-12-17
moebiu.x you could try to reinstall the kernel. I heard it worked for some people:

sudo aptitude reinstall linux-image-`uname -r` (and reboot)

I tried but it didn't work for me though.

---

### Post by moebiu.x on 2006-12-17
But if i reinstall the kernel, ubuntu should come back to initial status.
And to initial status sound was alredy OFF.

Is it wrong?

---

### Post by mordox on 2006-12-17
did u try and play the files in the example folder on your desktop / home folder ?

---

### Post by moebiu.x on 2006-12-17
Do u want to know if i've tried to play a file in example folder? Obviously! :)

Or i've not understand your question?

---

### Post by kilou on 2006-12-17
> **moebiu.x said:**
> But if i reinstall the kernel, ubuntu should come back to initial status.
And to initial status sound was alredy OFF.

Is it wrong?

My understanding is it won't come to initial status because you'll get the last Ubuntu kernel for Edgy with all the last updates. But for me it didn't work.....possibly because one of the update may have broken the sound. Maybe the update manager ran at the end of your install and you didn't have a chance to try the "initial" kernel anyway???

---

### Post by moebiu.x on 2006-12-17
> **kilou said:**
> moebiu.x you could try to reinstall the kernel. I heard it worked for some people:

sudo aptitude reinstall linux-image-`uname -r` (and reboot)

I tried but it didn't work for me though.

> **kilou said:**
> My understanding is it won't come to initial status because you'll get the last Ubuntu kernel for Edgy with all the last updates. But for me it didn't work.....possibly because one of the update may have broken the sound. Maybe the update manager ran at the end of your install and you didn't have a chance to try the "initial" kernel anyway???

I've reinstalled the kernel.
I've rebooted.

But my PC plays no sound! :( 

](*,) 

(...and since monday I hear no sound)

---

### Post by kilou on 2006-12-17
OK for me it works again :)  Check the following:
- right click on the volume icon in the taskbar
- choose Open Volume Control
- Verify that BOTH Master and PCM are not muted (no red cross)

For some reason PCM was muted on my system. Unmuting it and the sound is back.

---

### Post by short69 on 2006-12-17
I am having a simular problem with my Edgy6.10.I have sound on my pc except for when I try to use Enemy Territory and Team Speak at the same time.Hopefully some  one can help me out with this problem.

---

### Post by mordox on 2006-12-17
Go through this document and maybe your problem may get fixed !

[http://lau.linuxaudio.org/Sound-HOWTO-4.html](http://lau.linuxaudio.org/Sound-HOWTO-4.html)

---

### Post by moebiu.x on 2006-12-17
**_Reassumed_**

I've installed Ubuntu 6.10 on my PC. Acer Aspire.
From then it's mute.

The Volume controls are not mutes.
With 

```
alsamixer
```

i've deleted every MM replacing with 00.
With:

```
lspci
```

obtain

```
moebius@joshua:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 651 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 04)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.3 FireWire (IEEE 1394): Silicon Integrated Systems [SiS] FireWire Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
[COLOR="Red"]00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)[/COLOR]
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:07.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
00:0f.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV200 QW [Radeon 7500]
moebius@joshua:~$ 
```

with

```
lspci -v
```

obtain

```
moebius@joshua:~$ lspci -v
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 651 Host (rev 01)
        Subsystem: Silicon Integrated Systems [SiS] 651 Host
        Flags: bus master, medium devsel, latency 32
        Memory at e8000000 (32-bit, non-prefetchable) [size=64M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: ec000000-ec0fffff
        Prefetchable memory behind bridge: e0000000-e7ffffff

00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 04)
        Flags: bus master, medium devsel, latency 0

00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
        Flags: medium devsel
        I/O ports at 10c0 [size=32]

00:02.3 FireWire (IEEE 1394): Silicon Integrated Systems [SiS] FireWire Controller (prog-if 10 [OHCI])
        Flags: bus master, medium devsel, latency 32, IRQ 177
        Memory at ec134000 (32-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at 30000000 [disabled] [size=128K]
        Capabilities: <access denied>

00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (prog-if 80 [Master])
        Subsystem: Acer Incorporated [ALI] Unknown device 0018
        Flags: bus master, medium devsel, latency 128, IRQ 169
        I/O ports at 4000 [size=16]
        Capabilities: <access denied>

[COLOR="Red"]00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
        Subsystem: Acer Incorporated [ALI] Unknown device 0018
        Flags: bus master, medium devsel, latency 32, IRQ 217
        I/O ports at b400 [size=256]
        I/O ports at b800 [size=128]
        Capabilities: <access denied>[/COLOR]

00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 0018
        Flags: bus master, medium devsel, latency 32, IRQ 185
        Memory at ec130000 (32-bit, non-prefetchable) [size=4K]

00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 0018
        Flags: bus master, medium devsel, latency 32, IRQ 193
        Memory at ec131000 (32-bit, non-prefetchable) [size=4K]

00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 0018
        Flags: bus master, medium devsel, latency 32, IRQ 201
        Memory at ec132000 (32-bit, non-prefetchable) [size=4K]

00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller (prog-if 20 [EHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 0018
        Flags: bus master, medium devsel, latency 32, IRQ 209
        Memory at ec133000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:07.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
        Subsystem: U.S. Robotics Unknown device 2013
        Flags: bus master, medium devsel, latency 32, IRQ 5
        Memory at ec120000 (32-bit, non-prefetchable) [size=64K]
        I/O ports at bc00 [size=8]
        Capabilities: <access denied>

00:0f.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Realtek Semiconductor Co., Ltd. RT8139
        Flags: bus master, medium devsel, latency 32, IRQ 217
        I/O ports at c000 [size=256]
        Memory at ec135000 (32-bit, non-prefetchable) [size=256]
        [virtual] Expansion ROM at 30020000 [disabled] [size=64K]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV200 QW [Radeon 7500] (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc Unknown device 0f2a
        Flags: bus master, stepping, 66MHz, medium devsel, latency 32, IRQ 169
        Memory at e0000000 (32-bit, prefetchable) [size=128M]
        I/O ports at 9000 [size=256]
        Memory at ec020000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at ec000000 [disabled] [size=128K]
        Capabilities: <access denied>

moebius@joshua:~$
```

From the menu

***System>Administration>Device Manager***

this is the result

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=21225&stc=1&d=1166384074[/IMG]

Do I see two sound cards?
**AC'97 Sound Controller** and **SiS962 MuTIOL [Media IO]**
Am I wrong?

That's all, folks!
What do I do?
](*,)

---

### Post by Pobega on 2006-12-17
If you've got an Athlon processor, install the newest K7 kernel.

If you've got an Intel, downgrade to 386 (686 doesn't work for me, I use Intel)

If you've got anything else for a processor, someone else here can point you in the right direction for a kernel.

---

### Post by moebiu.x on 2006-12-17
Processor is Intel...
can you guide me for the downgrade?

---

### Post by moebiu.x on 2006-12-18
No one new idea about my problem?
:-k

---

### Post by moebiu.x on 2006-12-18
What do I do? Change Operative system? ](*,) 
I don't want return to Windows!

Please, help me to find a solution! [-o<

---

