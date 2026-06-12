---
title: "Auto update and firefox won't launch and a billion other problems"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by Darkstar0082 on 2007-02-04
1.I am running xubuntu edgy on my vaio laptop on a dual boot with XP and recently installed updates and now firefox won't launch. I click the shotcut and nothing happens at all. I am not sure why that is happening and I am completely new to linux. 

2.Also sometimes when running xarchiver the program just freezes. It stays on my desktop and doesn't let me close the program at all. 

3.I was trying to figure out how to run dreamweaver, fireworks, and flash 8 on xubuntu but I hear that is extremely complicated. Anyway I tried to install VMware player because I want to run windows applications but it gives me errors and I don't know exactly what they mean. I am using XP right now so I can access this forum for help so I can't tell you exactly what those errors are. Anyone know anything about VMware server and VMware player and how they work? I also tried wine by the way and installed dreamweaver, but it crashes before it can even load.

Any help would be appreciated and if you have any other advice for a newbie you can add in your reply. THANKS IN ADVANCE!

---

### Post by amohanty on 2007-02-04
after you try something that doesnt work. 
Post the output of:

dmesg | tail -n 50

AM

---

### Post by Darkstar0082 on 2007-02-04
Like I said, I am extremely new so how do I get such information?

---

### Post by amohanty on 2007-02-04
After something doesnt work.

Goto:
Applications->Accessories->Terminal

In there type:

dmesg | tail -n 100 | tee ~/Desktop/dmesg.log

This will create a dmesg.log file on your desktop. Copy/paste the contents.

To see what the command mean/do lookup on google.

HTH
AM

---

### Post by Darkstar0082 on 2007-02-04
OKay I installed Galeon for the mean time.

I'm not sure if this is what you needed.
Thanks for your help by the way.

pilot@Gamble:~$ dmesg tail -n 100 tee ~/Desktop/dmesg.log
Usage: dmesg [-c] [-n level] [-s bufsize]
pilot@Gamble:~$ dmesg
[17179569.184000] Linux version 2.6.17-10-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Tue Dec 5 22:28:26 UTC 2006 (Ubuntu 2.6.17-10.34-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[17179569.184000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000dc000 - 00000000000e0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001fdf0000 (usable)
[17179569.184000]  BIOS-e820: 000000001fdf0000 - 000000001fdfb000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000001fdfb000 - 000000001fe00000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000001fe00000 - 0000000020000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 509MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f7b10
[17179569.184000] On node 0 totalpages: 130544
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 126448 pages, LIFO batch:31
[17179569.184000] DMI present.
[17179569.184000] ACPI: RSDP (v000 SONY                                  ) @ 0x000f7ae0
[17179569.184000] ACPI: RSDT (v001   SONY       F0 0x20040119 PTL  0x00000000) @ 0x1fdf6d58
[17179569.184000] ACPI: FADT (v001   SONY       F0 0x20040119 PTL  0x01000000) @ 0x1fdfaf3c
[17179569.184000] ACPI: MADT (v001   SONY       F0 0x20040119 PTL  0x00000000) @ 0x1fdfafb0
[17179569.184000] ACPI: DSDT (v001   SONY       F0 0x20040119 PTL  0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x8008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:2 APIC version 20
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 16 low level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda3 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[17179569.184000] Detected 2673.005 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179571.124000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179571.124000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179571.136000] Memory: 507880k/522176k available (1910k kernel code, 13664k reserved, 1069k data, 308k init, 0k highmem)
[17179571.136000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179571.216000] Calibrating delay using timer specific routine.. 5350.66 BogoMIPS (lpj=10701326)
[17179571.216000] Security Framework v1.0.0 initialized
[17179571.216000] SELinux:  Disabled at boot.
[17179571.216000] Mount-cache hash table entries: 512
[17179571.216000] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[17179571.216000] CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[17179571.216000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[17179571.216000] CPU: L2 cache: 512K
[17179571.216000] CPU: Hyper-Threading is disabled
[17179571.216000] CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 00004400 00000000 00000000
[17179571.216000] Checking 'hlt' instruction... OK.
[17179571.232000] SMP alternatives: switching to UP code
[17179571.232000] Freeing SMP alternatives: 16k freed
[17179571.232000] checking if image is initramfs... it is
[17179571.700000] Freeing initrd memory: 5390k freed
[17179571.700000] ACPI: Core revision 20060707
[17179571.700000] ACPI: Looking for DSDT ... not found!
[17179571.704000] CPU0: Intel(R) Pentium(R) 4 CPU 2.66GHz stepping 09
[17179571.704000] Total of 1 processors activated (5350.66 BogoMIPS).
[17179571.704000] ENABLING IO-APIC IRQs
[17179571.704000] ..TIMER: vector=0x31 apic1=0 pin1=16 apic2=-1 pin2=-1
[17179571.704000] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[17179571.704000] ...trying to set up timer (IRQ0) through the 8259A ...  failed.
[17179571.704000] ...trying to set up timer as Virtual Wire IRQ... works.
[17179571.888000] Brought up 1 CPUs
[17179571.888000] migration_cost=0
[17179571.888000] NET: Registered protocol family 16
[17179571.888000] EISA bus registered
[17179571.888000] ACPI: bus type pci registered
[17179571.888000] PCI: PCI BIOS revision 2.10 entry at 0xfd996, last bus=1
[17179571.888000] PCI: Using configuration type 1
[17179571.888000] Setting up standard PCI resources
[17179571.908000] ACPI: Interpreter enabled
[17179571.908000] ACPI: Using IOAPIC for interrupt routing
[17179571.912000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179571.912000] PCI: Probing PCI hardware (bus 00)
[17179571.936000] Uncovering SIS963 that hid as a SIS503 (compatible=1)
[17179571.936000] Enabling SiS 96x SMBus.
[17179571.936000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:02.5
[17179571.936000] Boot video device is 0000:01:00.0
[17179571.936000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179571.948000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 *10 11)
[17179571.948000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *9 10 11)
[17179571.948000] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 7 9 10 11)
[17179571.952000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11)
[17179571.952000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 *9 10 11)
[17179571.952000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11)
[17179571.952000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11) *0, disabled.
[17179571.952000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11) *0, disabled.
[17179571.952000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[17179571.976000] ACPI: Embedded Controller [EC0] (gpe 21) interrupt mode.
[17179571.980000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179571.980000] pnp: PnP ACPI init
[17179572.020000] pnp: PnP ACPI: found 11 devices
[17179572.020000] PnPBIOS: Disabled by ACPI PNP
[17179572.020000] PCI: Using ACPI for IRQ routing
[17179572.020000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179572.024000] pnp: 00:04: ioport range 0x8000-0x808f could not be reserved
[17179572.024000] pnp: 00:04: ioport range 0x8090-0x80ff has been reserved
[17179572.024000] pnp: 00:04: ioport range 0x8100-0x811f has been reserved
[17179572.024000] pnp: 00:04: ioport range 0x4d0-0x4d1 has been reserved
[17179572.024000] pnp: 00:04: ioport range 0xfe00-0xfe00 has been reserved
[17179572.024000] PCI: Bridge: 0000:00:01.0
[17179572.024000]   IO window: disabled.
[17179572.024000]   MEM window: ed000000-edffffff
[17179572.024000]   PREFETCH window: f4000000-fbffffff
[17179572.024000] PCI: Bus 2, cardbus bridge: 0000:00:0a.0
[17179572.024000]   IO window: 00002400-000024ff
[17179572.024000]   IO window: 00002800-000028ff
[17179572.024000]   PREFETCH window: 30000000-31ffffff
[17179572.024000]   MEM window: 32000000-33ffffff
[17179572.024000] PCI: Bus 6, cardbus bridge: 0000:00:0a.1
[17179572.024000]   IO window: 00002c00-00002cff
[17179572.024000]   IO window: 00003000-000030ff
[17179572.024000]   PREFETCH window: 34000000-35ffffff
[17179572.024000]   MEM window: 36000000-37ffffff
[17179572.024000] PCI: Enabling device 0000:00:0a.0 (0000 -> 0003)
[17179572.024000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 17 (level, low) -> IRQ 177
[17179572.024000] PCI: Enabling device 0000:00:0a.1 (0000 -> 0003)
[17179572.024000] ACPI: PCI Interrupt 0000:00:0a.1[A] -> GSI 17 (level, low) -> IRQ 177
[17179572.024000] NET: Registered protocol family 2
[17179572.064000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179572.064000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[17179572.064000] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[17179572.064000] TCP: Hash tables configured (established 16384 bind 8192)
[17179572.064000] TCP reno registered
[17179572.064000] audit: initializing netlink socket (disabled)
[17179572.064000] audit(1170616550.064:1): initialized
[17179572.064000] VFS: Disk quotas dquot_6.5.1
[17179572.064000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179572.064000] Initializing Cryptographic API
[17179572.064000] io scheduler noop registered
[17179572.064000] io scheduler anticipatory registered
[17179572.064000] io scheduler deadline registered
[17179572.064000] io scheduler cfq registered (default)
[17179572.064000] isapnp: Scanning for PnP cards...
[17179572.416000] isapnp: No Plug & Play device found
[17179572.444000] Real Time Clock Driver v1.12ac
[17179572.444000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179572.444000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179572.444000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179572.444000] PCI: Enabling device 0000:00:02.6 (0000 -> 0001)
[17179572.444000] ACPI: PCI Interrupt 0000:00:02.6[C] -> GSI 18 (level, low) -> IRQ 185
[17179572.444000] ACPI: PCI interrupt for device 0000:00:02.6 disabled
[17179572.444000] mice: PS/2 mouse device common for all mice
[17179572.444000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179572.444000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179572.444000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179572.444000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUE] at 0x60,0x64 irq 1,12
[17179572.448000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179572.448000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179572.448000] EISA: Probing bus 0 at eisa.0
[17179572.448000] Cannot allocate resource for EISA slot 1
[17179572.448000] Cannot allocate resource for EISA slot 2
[17179572.448000] Cannot allocate resource for EISA slot 3
[17179572.448000] Cannot allocate resource for EISA slot 8
[17179572.448000] EISA: Detected 0 cards.
[17179572.448000] TCP bic registered
[17179572.448000] NET: Registered protocol family 1
[17179572.448000] NET: Registered protocol family 8
[17179572.448000] NET: Registered protocol family 20
[17179572.448000] Using IPI No-Shortcut mode
[17179572.448000] ACPI: (supports S0 S3 S4 S5)
[17179572.448000] Freeing unused kernel memory: 308k freed
[17179572.476000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179573.580000] Capability LSM initialized
[17179573.620000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C2])
[17179573.620000] ACPI: Thermal Zone [ATF0] (67 C)
[17179574.092000] SIS5513: IDE controller at PCI slot 0000:00:02.5
[17179574.092000] SIS5513: chipset revision 0
[17179574.092000] SIS5513: not 100% native mode: will probe irqs later
[17179574.092000] SIS5513: SiS 962/963 MuTIOL IDE UDMA133 controller
[17179574.092000]     ide0: BM-DMA at 0x1000-0x1007, BIOS settings: hda:DMA, hdb:pio
[17179574.092000]     ide1: BM-DMA at 0x1008-0x100f, BIOS settings: hdc:DMA, hdd:pio
[17179574.092000] Probing IDE interface ide0...
[17179574.384000] hda: IC25N060ATMR04-0, ATA DISK drive
[17179575.060000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179575.080000] Probing IDE interface ide1...
[17179575.820000] hdc: SONY DVD RW DW-U50A, ATAPI CD/DVD-ROM drive
[17179576.496000] ide1 at 0x170-0x177,0x376 on irq 15
[17179576.508000] hda: max request size: 512KiB
[17179576.512000] hda: 117210240 sectors (60011 MB) w/7884KiB Cache, CHS=16383/255/63, UDMA(100)
[17179576.512000] hda: cache flushes supported
[17179576.512000]  hda: hda1 hda2 < hda5 hda6 > hda3
[17179576.584000] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 8192kB Cache, UDMA(33)
[17179576.584000] Uniform CD-ROM driver Revision: 3.20
[17179577.072000] usbcore: registered new driver usbfs
[17179577.072000] usbcore: registered new driver hub
[17179577.076000] PCI: Enabling device 0000:00:03.3 (0000 -> 0002)
[17179577.076000] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 23 (level, low) -> IRQ 193
[17179577.076000] ehci_hcd 0000:00:03.3: EHCI Host Controller
[17179577.080000] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 1
[17179577.080000] PCI: cache line size of 128 is not supported by device 0000:00:03.3
[17179577.080000] ehci_hcd 0000:00:03.3: irq 193, io mem 0xec003000
[17179577.080000] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179577.080000] usb usb1: configuration #1 chosen from 1 choice
[17179577.080000] hub 1-0:1.0: USB hub found
[17179577.080000] hub 1-0:1.0: 6 ports detected
[17179577.108000] ieee1394: Initialized config rom entry `ip1394'
[17179577.116000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179577.188000] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 201
[17179577.188000] ohci_hcd 0000:00:03.0: OHCI Host Controller
[17179577.188000] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 2
[17179577.188000] ohci_hcd 0000:00:03.0: irq 201, io mem 0xec000000
[17179577.252000] usb usb2: configuration #1 chosen from 1 choice
[17179577.252000] hub 2-0:1.0: USB hub found
[17179577.252000] hub 2-0:1.0: 2 ports detected
[17179577.356000] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 209
[17179577.356000] ohci_hcd 0000:00:03.1: OHCI Host Controller
[17179577.356000] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 3
[17179577.356000] ohci_hcd 0000:00:03.1: irq 209, io mem 0xec001000
[17179577.420000] usb usb3: configuration #1 chosen from 1 choice
[17179577.420000] hub 3-0:1.0: USB hub found
[17179577.420000] hub 3-0:1.0: 2 ports detected
[17179577.524000] PCI: Enabling device 0000:00:03.2 (0010 -> 0012)
[17179577.524000] ACPI: PCI Interrupt 0000:00:03.2[C] -> GSI 22 (level, low) -> IRQ 217
[17179577.524000] ohci_hcd 0000:00:03.2: OHCI Host Controller
[17179577.524000] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 4
[17179577.524000] ohci_hcd 0000:00:03.2: irq 217, io mem 0xec002000
[17179577.588000] usb usb4: configuration #1 chosen from 1 choice
[17179577.588000] hub 4-0:1.0: USB hub found
[17179577.588000] hub 4-0:1.0: 2 ports detected
[17179577.696000] ACPI: PCI Interrupt 0000:00:0a.2[A] -> GSI 17 (level, low) -> IRQ 177
[17179577.748000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[177]  MMIO=[ec005000-ec0057ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[17179577.852000] Attempting manual resume
[17179577.860000] usb 2-1: new full speed USB device using ohci_hcd and address 2
[17179577.908000] kjournald starting.  Commit interval 5 seconds
[17179577.908000] EXT3-fs: mounted filesystem with ordered data mode.
[17179578.072000] usb 2-1: configuration #1 chosen from 1 choice
[17179578.072000] hub 2-1:1.0: USB hub found
[17179578.076000] hub 2-1:1.0: 4 ports detected
[17179578.504000] usb 4-2: new full speed USB device using ohci_hcd and address 2
[17179578.712000] usb 4-2: configuration #1 chosen from 1 choice
[17179578.948000] usb 2-1.1: new low speed USB device using ohci_hcd and address 3
[17179579.032000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[08004603018cd138]
[17179579.068000] usb 2-1.1: configuration #1 chosen from 1 choice
[17179579.308000] usb 2-1.3: new low speed USB device using ohci_hcd and address 4
[17179579.432000] usb 2-1.3: configuration #1 chosen from 1 choice
[17179590.636000] Linux agpgart interface v0.101 (c) Dave Jones
[17179590.644000] agpgart: Detected SiS 648 chipset
[17179590.648000] agpgart: AGP aperture is 64M @ 0xe8000000
[17179590.672000] ath_hal: module license 'Proprietary' taints kernel.
[17179590.672000] ath_hal: 0.9.17.2 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[17179590.736000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 17 (level, low) -> IRQ 177
[17179590.736000] Yenta: CardBus bridge found at 0000:00:0a.0 [104d:814e]
[17179590.900000] Yenta: ISA IRQ mask 0x04b8, PCI irq 177
[17179590.900000] Socket status: 30000006
[17179590.900000] ACPI: PCI Interrupt 0000:00:0a.1[A] -> GSI 17 (level, low) -> IRQ 177
[17179590.900000] Yenta: CardBus bridge found at 0000:00:0a.1 [104d:814e]
[17179590.900000] wlan: 0.8.4.2 (0.9.2.1)
[17179590.976000] ath_rate_sample: 1.2 (0.9.2.1)
[17179591.016000] ath_pci: 0.9.4.5 (0.9.2.1)
[17179591.044000] Yenta: ISA IRQ mask 0x04b8, PCI irq 177
[17179591.044000] Socket status: 30000006
[17179591.060000] PCI: Enabling device 0000:00:07.0 (0014 -> 0016)
[17179591.060000] ACPI: PCI Interrupt 0000:00:07.0[A] -> GSI 18 (level, low) -> IRQ 185
[17179591.340000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[17179591.340000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17179591.340000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[17179591.340000] wifi0: mac 5.6 phy 4.1 radio 1.7
[17179591.340000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[17179591.340000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[17179591.340000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[17179591.340000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[17179591.340000] wifi0: Use hw queue 8 for CAB traffic
[17179591.340000] wifi0: Use hw queue 9 for beacons
[17179591.400000] wifi0: Atheros 5212: mem=0xec010000, irq=185
[17179591.416000] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x8100
[17179591.852000] usbcore: registered new driver hiddev
[17179591.924000] input: HID 1241:1166 as /class/input/input1
[17179591.924000] input: USB HID v1.10 Mouse [HID 1241:1166] on usb-0000:00:03.0-1.1
[17179591.940000] input: Sony Sony IR Receiver as /class/input/input2
[17179591.940000] input,hiddev96: USB HID v1.10 Keyboard [Sony Sony IR Receiver] on usb-0000:00:03.0-1.3
[17179591.940000] usbcore: registered new driver usbhid
[17179591.940000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179592.108000] parport: PnPBIOS parport detected.
[17179592.108000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[17179592.152000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179592.156000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179592.588000] input: PC Speaker as /class/input/input3
[17179592.604000] sis900.c: v1.08.09 Sep. 19 2005
[17179592.604000] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 225
[17179592.608000] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 1.
[17179592.616000] 0000:00:04.0: Using transceiver found at address 1 as default
[17179592.620000] eth0: SiS 900 PCI Fast Ethernet at 0x2000, IRQ 225, 08:00:46:c4:b1:81.
[17179592.768000] usbcore: registered new driver libusual
[17179592.824000] cs: IO port probe 0x100-0x3af: clean.
[17179592.828000] cs: IO port probe 0x3e0-0x4ff: excluding 0x480-0x48f
[17179592.828000] cs: IO port probe 0x820-0x8ff: clean.
[17179592.828000] cs: IO port probe 0xc00-0xcf7: clean.
[17179592.828000] cs: IO port probe 0xa00-0xaff: clean.
[17179592.832000] cs: IO port probe 0x100-0x3af: clean.
[17179592.832000] cs: IO port probe 0x3e0-0x4ff: excluding 0x480-0x48f
[17179592.840000] cs: IO port probe 0x820-0x8ff: clean.
[17179592.840000] cs: IO port probe 0xc00-0xcf7: clean.
[17179592.840000] cs: IO port probe 0xa00-0xaff: clean.
[17179592.936000] eth0: Media Link Off
[17179592.996000] ts: Compaq touchscreen protocol output
[17179593.084000] SCSI subsystem initialized
[17179593.088000] Initializing USB Mass Storage driver...
[17179593.088000] scsi0 : SCSI emulation for USB Mass Storage devices
[17179593.088000] usbcore: registered new driver usb-storage
[17179593.088000] USB Mass Storage support registered.
[17179593.088000] usb-storage: device found at 2
[17179593.088000] usb-storage: waiting for device to settle before scanning
[17179593.100000] input: PS/2 Mouse as /class/input/input4
[17179593.120000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input5
[17179593.184000] NET: Registered protocol family 17
[17179593.520000] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 185
[17179594.344000] intel8x0_measure_ac97_clock: measured 55461 usecs
[17179594.344000] intel8x0: clocking to 48000
[17179594.496000] lp0: using parport0 (interrupt-driven).
[17179594.508000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179594.508000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179594.544000] Adding 1044152k swap on /dev/disk/by-uuid/c5307bfa-134b-4f4c-808d-84c540e77932.  Priority:-1 extents:1 across:1044152k
[17179594.596000] EXT3 FS on hda3, internal journal
[17179598.088000] usb-storage: device scan complete
[17179598.092000]   Vendor: Sony      Model: MSC-U03           Rev: 2.00
[17179598.092000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179598.148000] SCSI device sda: 1963008 512-byte hdwr sectors (1005 MB)
[17179598.152000] sda: Write Protect is off
[17179598.152000] sda: Mode Sense: 00 6a 20 00
[17179598.152000] sda: assuming drive cache: write through
[17179598.184000] SCSI device sda: 1963008 512-byte hdwr sectors (1005 MB)
[17179598.192000] sda: Write Protect is off
[17179598.192000] sda: Mode Sense: 00 6a 20 00
[17179598.192000] sda: assuming drive cache: write through
[17179598.192000]  sda: sda1
[17179598.200000] sd 0:0:0:0: Attached scsi removable disk sda
[17179598.220000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179600.128000] ACPI: AC Adapter [ACAD] (on-line)
[17179600.160000] ACPI: Battery Slot [BAT1] (battery present)
[17179600.160000] ACPI: Battery Slot [BAT2] (battery absent)
[17179600.176000] ACPI: Lid Switch [LID]
[17179600.176000] ACPI: Power Button (CM) [PWRB]
[17179600.312000] ibm_acpi: ec object not found
[17179600.340000] pcc_acpi: loading...
[17179600.376000] ACPI Sony Notebook Control Driver v0.2 successfully installed
[17179600.452000] ACPI: Video Device [VID0] (multi-head: yes  rom: no  post: no)
[17179603.820000] apm: BIOS not found.
[17179608.076000] sonypi: Sony Programmable I/O Controller Driver v1.26.
[17179608.084000] sonypi: detected type2 model, verbose = 0, fnkeyinit = off, camera = off, compat = off, mask = 0xffffffff, useinput = on, acpi = on
[17179608.084000] sonypi: enabled at irq=11, port1=0x1080, port2=0x1084
[17179608.084000] sonypi: device allocated minor is 62
[17179608.140000] input: Sony Vaio Jogdial as /class/input/input6
[17179608.172000] input: Sony Vaio Keys as /class/input/input7
[17179608.516000] /dev/vmmon[4333]: Module vmmon: registered with major=10 minor=165
[17179608.516000] /dev/vmmon[4333]: Module vmmon: initialized
[17179608.604000] /dev/vmnet: open called by PID 4357 (vmnet-bridge)
[17179608.604000] /dev/vmnet: hub 0 does not exist, allocating memory.
[17179608.604000] /dev/vmnet: port on hub 0 successfully opened
[17179608.604000] bridge-ath0: enabling the bridge
[17179608.604000] bridge-ath0: can't bridge with ath0, bad header length 88
[17179608.604000] bridge-ath0: interface ath0 is not a valid Ethernet interface
[17179608.604000] bridge-ath0: can't bridge with ath0, bad header length 88
[17179608.672000] /dev/vmnet: open called by PID 4368 (vmnet-netifup)
[17179608.672000] /dev/vmnet: hub 8 does not exist, allocating memory.
[17179608.676000] /dev/vmnet: port on hub 8 successfully opened
[17179608.680000] /dev/vmnet: open called by PID 4362 (vmnet-netifup)
[17179608.680000] /dev/vmnet: hub 1 does not exist, allocating memory.
[17179608.680000] /dev/vmnet: port on hub 1 successfully opened
[17179608.724000] /dev/vmnet: open called by PID 4372 (vmnet-natd)
[17179608.724000] /dev/vmnet: port on hub 8 successfully opened
[17179608.804000] /dev/vmnet: open called by PID 4392 (vmnet-dhcpd)
[17179608.804000] /dev/vmnet: port on hub 1 successfully opened
[17179608.836000] /dev/vmnet: open called by PID 4398 (vmnet-dhcpd)
[17179608.836000] /dev/vmnet: port on hub 8 successfully opened
[17179619.716000] NET: Registered protocol family 10
[17179619.716000] lo: Disabled Privacy Extensions
[17179619.716000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179619.716000] IPv6 over IPv4 tunneling driver
[17179629.828000] vmnet8: no IPv6 routers present
[17179630.472000] ath0: no IPv6 routers present
[17179630.700000] vmnet1: no IPv6 routers present
[17180122.084000] /dev/vmnet: open called by PID 5018 (vmnet-bridge)
[17180122.084000] /dev/vmnet: hub 0 does not exist, allocating memory.
[17180122.084000] /dev/vmnet: port on hub 0 successfully opened
[17180122.084000] bridge-ath0: enabling the bridge
[17180122.084000] bridge-ath0: can't bridge with ath0, bad header length 88
[17180122.084000] bridge-ath0: interface ath0 is not a valid Ethernet interface
[17180122.084000] bridge-ath0: can't bridge with ath0, bad header length 88
[17180122.108000] /dev/vmnet: open called by PID 5029 (vmnet-natd)
[17180122.108000] /dev/vmnet: port on hub 8 successfully opened
[17180132.168000] /dev/vmnet: open called by PID 5108 (vmnet-netifup)
[17180132.168000] /dev/vmnet: port on hub 8 successfully opened
[17180132.184000] /dev/vmnet: open called by PID 5107 (vmnet-netifup)
[17180132.188000] /dev/vmnet: port on hub 1 successfully opened
[17180194.272000] /dev/vmnet: open called by PID 5170 (vmnet-bridge)
[17180194.272000] /dev/vmnet: hub 0 does not exist, allocating memory.
[17180194.272000] /dev/vmnet: port on hub 0 successfully opened
[17180194.272000] bridge-ath0: enabling the bridge
[17180194.272000] bridge-ath0: can't bridge with ath0, bad header length 88
[17180194.272000] bridge-ath0: interface ath0 is not a valid Ethernet interface
[17180194.272000] bridge-ath0: can't bridge with ath0, bad header length 88
[17180194.296000] /dev/vmnet: open called by PID 5181 (vmnet-natd)
[17180194.296000] /dev/vmnet: port on hub 8 successfully opened
[17180204.304000] /dev/vmnet: open called by PID 5184 (vmnet-netifup)
[17180204.304000] /dev/vmnet: port on hub 8 successfully opened
[17180204.340000] /dev/vmnet: open called by PID 5185 (vmnet-netifup)
[17180204.340000] /dev/vmnet: port on hub 1 successfully opened

---

### Post by riven0 on 2007-02-04
For Vmware server, have you tried following [this guide]("http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware+server")? It's the best one out there. Where exactly did you get stuck?

---

### Post by seshomaru samma on 2007-02-04
I know this is not much help but I personaly think Xubuntu is not the best choice for a Linux newbie. Gnome (=Ubuntu) is SO much easier.
In order to help you solve these problem you have to run firefox from the terminal and paste the output
(same with VMware)
in the meanwhile you can install another browser like opera or konqueror to surf the net
```
sudo apt-get install opera 
```

---

### Post by btolle on 2007-02-04
As a newbie (and I still am) I tried several flavors and versions of Linux in the first couple of weeks then I bought the book "Ubuntu Unleashed" which has a DVD with it that has Ubuntu 6.06LTS. The LTS means 'long term support' so that I know that version will be supported for 5 years from the release date.

Bottom line for me is that is the version I am happiest with. Seems more stable and does everything I have wanted it to do.

After a few years on computers I decided I had enough of the bleeding edge stuff and started looking to more stable versions of software. Newer is not necessarily better.

---

### Post by closetpirate on 2007-02-04
I agree your frustrations will continue unless you have the product that suites you ubuntu 6.06 would be better. Another thing that I can help with is that I run Dreamweaver with wine and it works great

Dreamweaver 8 that is

---

### Post by amohanty on 2007-02-05
There doesnt seem to be any issues in the dmesg output. BTW, I put the **|** character in there intentionally, thats how its supposed to be typed out :)

Goto System->ADministration->Synaptic Package Manager
Enter your password, 
Goto File->History and see what were the new things that were installed and post all of them, till just prioir to the update, if you remember.

Also open a terminal and type in 
firefox

and see if you can find any error messages

AM

---

### Post by seshomaru samma on 2007-02-05
> **amohanty said:**
> 
Goto System->ADministration->Synaptic Package Manager
Enter your password, 
Goto File->History and see what were the new things that were installed and post all of them, till just prioir to the update, if you remember.
AM

dont want to highjack the thread or anything but i didnt realise it had this function, can i get apt's history through the terminal?

---

### Post by amohanty on 2007-02-05
afaik (I could be off on this) neither apt-get or dpkg provide history info. This is a feature for synaptic.

AM

---

### Post by Spr0k3t on 2007-02-05
Not on my computer right now, but doesn't aptitude keep a changelog?

---

### Post by Darkstar0082 on 2007-02-05
I thank you all for your helpful advice! I installed swiftfox and now firefox works again for some reason as swiftfox. I guess that's the closest and easiest way that could fix a problem like mine. Long term support is a good idea and maybe I should consider switching. I'm still trying to figure out how to install dreamweaver because it still crashes before it could open. I found [this thread]("http://bkcreation.info/Blog_Macromedia8OnWine.html") that seems to be the popular solution to running DW8 with wine.

Here is my history about the time I think things got messed up.

Commit Log for Sun Feb  4 01:41:59 2007


Upgraded the following packages:
app-install-data-commercial (6) to 6.3
avahi-daemon (0.6.13-2ubuntu2) to 0.6.13-2ubuntu2.4
dbus (0.93-0ubuntu3) to 0.93-0ubuntu3.1
dbus-1-utils (0.93-0ubuntu3) to 0.93-0ubuntu3.1
evince-gtk (0.5.2-0ubuntu4) to 0.5.2-0ubuntu4.1
firefox (2.0+0dfsg-0ubuntu3) to 2.0.0.1+0dfsg-0ubuntu0.6.10
gdm (2.16.1-0ubuntu4) to 2.16.1-0ubuntu4.1
gimp (2.2.13-1ubuntu1) to 2.2.13-1ubuntu3
gimp-data (2.2.13-1ubuntu1) to 2.2.13-1ubuntu3
gnupg (1.4.3-2ubuntu3) to 1.4.3-2ubuntu3.2
info (4.8.dfsg.1-1) to 4.8.dfsg.1-1ubuntu0.1
language-pack-en (1:6.10+20061019) to 1:6.10+20061130
libavahi-common-data (0.6.13-2ubuntu2) to 0.6.13-2ubuntu2.4
libavahi-common3 (0.6.13-2ubuntu2) to 0.6.13-2ubuntu2.4
libavahi-core4 (0.6.13-2ubuntu2) to 0.6.13-2ubuntu2.4
libdbus-1-3 (0.93-0ubuntu3) to 0.93-0ubuntu3.1
libgimp2.0 (2.2.13-1ubuntu1) to 2.2.13-1ubuntu3
libgnomeprintui2.2-0 (2.12.1-4) to 2.12.1-4ubuntu2
libgnomeprintui2.2-common (2.12.1-4) to 2.12.1-4ubuntu2
libgsf-1-114 (1.14.1-2ubuntu1) to 1.14.1-2ubuntu1.1
libgsf-1-common (1.14.1-2ubuntu1) to 1.14.1-2ubuntu1.1
libgtk2.0-0 (2.10.6-0ubuntu1) to 2.10.6-0ubuntu3.1
libgtk2.0-bin (2.10.6-0ubuntu1) to 2.10.6-0ubuntu3.1
libgtk2.0-common (2.10.6-0ubuntu1) to 2.10.6-0ubuntu3.1
libgtop2-7 (2.14.4-0ubuntu1) to 2.14.4-0ubuntu1.1
libgtop2-common (2.14.4-0ubuntu1) to 2.14.4-0ubuntu1.1
libkrb53 (1.4.3-9ubuntu1) to 1.4.3-9ubuntu1.1
libnspr4 (2:1.firefox2.0+0dfsg-0ubuntu3) to 2:1.firefox2.0.0.1+0dfsg-0ubuntu0.6.10
libnss3 (2:1.firefox2.0+0dfsg-0ubuntu3) to 2:1.firefox2.0.0.1+0dfsg-0ubuntu0.6.10
libpng12-0 (1.2.8rel-5.1) to 1.2.8rel-5.1ubuntu0.1
libpoppler1 (0.5.4-0ubuntu4) to 0.5.4-0ubuntu4.1
libpoppler1-glib (0.5.4-0ubuntu4) to 0.5.4-0ubuntu4.1
libvolumeid0 (093-0ubuntu18) to 093-0ubuntu18.0edgy2
libwxbase2.6-0 (2.6.3.2.1.5) to 2.6.3.2.1.5ubuntu0.1
libwxgtk2.6-0 (2.6.3.2.1.5) to 2.6.3.2.1.5ubuntu0.1
libxine1 (1.1.2+repacked1-0ubuntu3) to 1.1.2+repacked1-0ubuntu3.2
linux-headers-2.6.17-10 (2.6.17-10.33) to 2.6.17.1-10.34
linux-headers-2.6.17-10-generic (2.6.17-10.33) to 2.6.17.1-10.34
linux-image-2.6.17-10-generic (2.6.17-10.33) to 2.6.17.1-10.34
linux-restricted-modules-2.6.17-10-generic (2.6.17.5-11) to 2.6.17.7-10.1
linux-restricted-modules-common (2.6.17.5-11) to 2.6.17.7-10.1
mozilla-thunderbird (1.5.0.7-0ubuntu1) to 1.5.0.9-0ubuntu0.6.10
poppler-utils (0.5.4-0ubuntu4) to 0.5.4-0ubuntu4.1
screen (4.0.2-4.1ubuntu5) to 4.0.2-4.1ubuntu5.6.10
system-tools-backends (1.9.7-0ubuntu4) to 1.9.7-0ubuntu5
tar (1.15.91-2) to 1.15.91-2ubuntu0.3
tzdata (2006m-1ubuntu1) to 2006p-0ubuntu6.10
udev (093-0ubuntu18) to 093-0ubuntu18.0edgy2
volumeid (093-0ubuntu18) to 093-0ubuntu18.0edgy2
w3m (0.5.1-4ubuntu2) to 0.5.1-4ubuntu2.6.10
x11-common (1:7.1.1ubuntu6) to 1:7.1.1ubuntu6.2
xbase-clients (1:7.1.1ubuntu6) to 1:7.1.1ubuntu6.2
xorg (1:7.1.1ubuntu6) to 1:7.1.1ubuntu6.2
xserver-xorg (1:7.1.1ubuntu6) to 1:7.1.1ubuntu6.2
xserver-xorg-core (1:1.1.1-0ubuntu12) to 1:1.1.1-0ubuntu12.1
xserver-xorg-input-all (1:7.1.1ubuntu6) to 1:7.1.1ubuntu6.2
xserver-xorg-video-all (1:7.1.1ubuntu6) to 1:7.1.1ubuntu6.2
xubuntu-system-tools (2.15.5-0ubuntu1) to 2.15.5-0ubuntu2
xutils (1:7.1.1ubuntu6) to 1:7.1.1ubuntu6.2

Commit Log for Sat Feb  3 01:48:58 2007


Removed the following packages:
audacity

Upgraded the following packages:
libc6 (2.4-1ubuntu12) to 2.4-1ubuntu12.3
libc6-i686 (2.4-1ubuntu12) to 2.4-1ubuntu12.3
sun-java5-bin (1.5.0-08-0ubuntu1) to 1.5.0-08-0ubuntu1

Installed the following packages:
bittorrent (3.4.2-6ubuntu3)
blender (2.42a-1ubuntu1)
evolution (2.8.1-0ubuntu4)
evolution-data-server (1.8.1-0ubuntu3)
evolution-data-server-common (1.8.1-0ubuntu3)
g-wrap (1.9.6-3.1)
gnome-btdownload (0.0.24-0ubuntu1)
gnucash (2.0.1-3ubuntu3)
gnucash-common (2.0.1-3ubuntu3)
gtkhtml3.8 (3.12.1-0ubuntu1)
guile-1.6 (1.6.8-3)
guile-1.6-dev (1.6.8-3)
guile-1.6-libs (1.6.8-3)
guile-1.6-slib (1.6.8-3)
guile-g-wrap (1.9.6-3.1)
guile-library (0.1.2-1)
inkscape (0.44-1ubuntu2)
ksnapshot (4:3.5.5-0ubuntu2)
libc6-dev (2.4-1ubuntu12.3)
libcairomm-1.0-1 (1.2.0-0ubuntu1)
libcamel1.2-8 (1.8.1-0ubuntu3)
libcrypt-ssleay-perl (0.51-5)
libdate-manip-perl (5.44-3)
libebook1.2-9 (1.8.1-0ubuntu3)
libecal1.2-7 (1.8.1-0ubuntu3)
libedata-book1.2-2 (1.8.1-0ubuntu3)
libedata-cal1.2-6 (1.8.1-0ubuntu3)
libedataserver1.2-7 (1.8.1-0ubuntu3)
libedataserverui1.2-8 (1.8.1-0ubuntu3)
libegroupwise1.2-12 (1.8.1-0ubuntu3)
libexchange-storage1.2-2 (1.8.1-0ubuntu3)
libffi4 (4.1.1-13ubuntu5)
libffi4-dev (4.1.1-13ubuntu5)
libfinance-quote-perl (1.11-0.1)
libglibmm-2.4-1c2a (2.12.2-0ubuntu1)
libgnome-pilot2 (2.0.14-0ubuntu2)
libgsf-gnome-1-114 (1.14.1-2ubuntu1.1)
libgtkhtml3.8-15 (3.12.1-0ubuntu1)
libgtkmm-2.4-1c2a (1:2.10.2-0ubuntu1)
libguile-ltdl-1 (1.6.8-3)
libgwrap-runtime0 (1.9.6-3.1)
libgwrap-runtime0-dev (1.9.6-3.1)
libhtml-tableextract-perl (2.07-0.1)
liblpint-bonobo0 (0.1.4.3)
libmysqlclient15off (5.0.24a-9)
libncurses5-dev (5.5-2ubuntu1)
libofx2c2a (1:0.8.0-12)
libosp5 (1.5.2-3)
libpisock9 (0.12.1-5)
libpisync0 (0.12.1-5)
libqthreads-12 (1.6.8-3)
libreadline5-dev (5.1-7build1)
libsdl-mixer1.2 (1.2.6-1.1)
libsmpeg0 (0.4.5+cvs20030824-1.8)
libzvbi-common (0.2.22-1)
libzvbi0 (0.2.22-1)
linux-libc-dev (2.6.17.1-10.34)
mgetty (1.1.35-2ubuntu1)
mgetty-fax (1.1.35-2ubuntu1)
mysql-admin (1.1.10-1)
mysql-admin-common (1.1.10-1)
mysql-common (5.0.24a-9)
pia (3.95-4ubuntu1)
psfontmgr (0.11.10)
qtparted (0.4.5-2ubuntu11)
scantv (3.95-4ubuntu1)
slib (3a3-2)
sound-juicer (2.16.1-0ubuntu1)
sun-java5-jre (1.5.0-08-0ubuntu1)
tuxtype (1.0-5ubuntu1)
v4l-conf (3.95-4ubuntu1)
wifi-radar (1.9.7-0ubuntu2)
xawtv (3.95-4ubuntu1)
xawtv-plugins (3.95-4ubuntu1)
xsane (0.99+0.991-1ubuntu2)
xsane-common (0.99+0.991-1ubuntu2)

---

