---
title: "KDE (with XGL) not responding after login"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by calvinthomas on 2006-10-02
Hi, I was playing around with kcontrol and making KDE a bit prettier but have now got myself in a mess. I have reversed all my changes (except a cursor theme) and a wallpaper at bootup (I can't see how to reverse that) but am having this odd error.

When I restart my computer (a full restart not ctrl alt backspace) and login to XGL session (my standard) my harddisk doesn't stop flashing and when I try and open something up it just sits there forever. If I then do ctrl alt backpace and login again it works absolutely fine! What can I do?

Calv

---

### Post by calvinthomas on 2006-10-02
I can now confirm it doesn't seem to be any of the changes i've made. It seems that something is running on an endless loop when it first logs in, anyway I can check this?

Calv

---

### Post by calvinthomas on 2006-10-02
(The End Of) my syslog file:

Oct  2 16:57:28 localhost syslogd 1.4.1#17ubuntu7: restart.
Oct  2 16:57:28 localhost kernel: Inspecting /boot/System.map-2.6.15-27-k7
Oct  2 16:57:28 localhost kernel: Loaded 23249 symbols from /boot/System.map-2.6.15-27-k7.
Oct  2 16:57:28 localhost kernel: Symbols match kernel version 2.6.15.
Oct  2 16:57:28 localhost kernel: No module symbols loaded - kernel modules not enabled. 
Oct  2 16:57:28 localhost kernel: [17179569.184000] Linux version 2.6.15-27-k7 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Sat Sep 16 02:35:20 UTC 2006
Oct  2 16:57:28 localhost kernel: [17179569.184000] BIOS-provided physical RAM map:
Oct  2 16:57:28 localhost kernel: [17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Oct  2 16:57:28 localhost kernel: [17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Oct  2 16:57:28 localhost kernel: [17179569.184000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
Oct  2 16:57:28 localhost kernel: [17179569.184000]  BIOS-e820: 0000000000100000 - 000000001fef0000 (usable)
Oct  2 16:57:28 localhost kernel: [17179569.184000]  BIOS-e820: 000000001fef0000 - 000000001fefb000 (ACPI data)
Oct  2 16:57:28 localhost kernel: [17179569.184000]  BIOS-e820: 000000001fefb000 - 000000001ff00000 (ACPI NVS)
Oct  2 16:57:28 localhost kernel: [17179569.184000]  BIOS-e820: 000000001ff00000 - 0000000020000000 (reserved)
Oct  2 16:57:28 localhost kernel: [17179569.184000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Oct  2 16:57:28 localhost kernel: [17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Oct  2 16:57:28 localhost kernel: [17179569.184000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
Oct  2 16:57:28 localhost kernel: [17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Oct  2 16:57:28 localhost kernel: [17179569.184000] 0MB HIGHMEM available.
Oct  2 16:57:28 localhost kernel: [17179569.184000] 510MB LOWMEM available.
Oct  2 16:57:28 localhost kernel: [17179569.184000] found SMP MP-table at 000f6ab0
Oct  2 16:57:28 localhost kernel: [17179569.184000] On node 0 totalpages: 130800
Oct  2 16:57:28 localhost kernel: [17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
Oct  2 16:57:28 localhost kernel: [17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
Oct  2 16:57:28 localhost kernel: [17179569.184000]   Normal zone: 126704 pages, LIFO batch:31
Oct  2 16:57:28 localhost kernel: [17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
Oct  2 16:57:28 localhost kernel: [17179569.184000] DMI present.
Oct  2 16:57:28 localhost kernel: [17179569.184000] ATI board detected. Disabling timer routing over 8254.
Oct  2 16:57:28 localhost kernel: [17179569.184000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6a80
Oct  2 16:57:28 localhost kernel: [17179569.184000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x1fef4961
Oct  2 16:57:28 localhost kernel: [17179569.184000] ACPI: FADT (v001 ATI    Firanha  0x06040000 ATI  0x000f4240) @ 0x1fefae41
Oct  2 16:57:28 localhost kernel: [17179569.184000] ACPI: SSDT (v001 PTLTD  POWERNOW 0x06040000  LTP 0x00000001) @ 0x1fefaeb5
Oct  2 16:57:28 localhost kernel: [17179569.184000] ACPI: MADT (v001 PTLTD  ^I APIC   0x06040000  LTP 0x00000000) @ 0x1fefaf6a
Oct  2 16:57:28 localhost kernel: [17179569.184000] ACPI: MCFG (v001 PTLTD    MCFG   0x06040000  LTP 0x00000000) @ 0x1fefafc4
Oct  2 16:57:28 localhost kernel: [17179569.184000] ACPI: DSDT (v001    ATI    SB400 0x06040000 MSFT 0x0100000e) @ 0x00000000
Oct  2 16:57:28 localhost kernel: [17179569.184000] ACPI: PM-Timer IO Port: 0x8008
Oct  2 16:57:28 localhost kernel: [17179569.184000] ACPI: Local APIC address 0xfee00000
Oct  2 16:57:28 localhost kernel: [17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Oct  2 16:57:28 localhost kernel: [17179569.184000] Processor #0 15:4 APIC version 16
Oct  2 16:57:28 localhost kernel: [17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Oct  2 16:57:28 localhost kernel: [17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Oct  2 16:57:28 localhost kernel: [17179569.184000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
Oct  2 16:57:28 localhost kernel: [17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
Oct  2 16:57:28 localhost kernel: [17179569.184000] ACPI: BIOS IRQ0 pin2 override ignored.
Oct  2 16:57:28 localhost kernel: [17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
Oct  2 16:57:28 localhost kernel: [17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Oct  2 16:57:28 localhost kernel: [17179569.184000] Using ACPI (MADT) for SMP configuration information
Oct  2 16:57:28 localhost kernel: [17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:c0000000)
Oct  2 16:57:28 localhost kernel: [17179569.184000] Built 1 zonelists
Oct  2 16:57:28 localhost kernel: [17179569.184000] Kernel command line: root=/dev/hda4 ro ro quiet splash elevator=cfq
Oct  2 16:57:28 localhost kernel: [17179569.184000] mapped APIC to ffffd000 (fee00000)
Oct  2 16:57:28 localhost kernel: [17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
Oct  2 16:57:28 localhost kernel: [17179569.184000] Initializing CPU#0
Oct  2 16:57:28 localhost kernel: [17179569.184000] PID hash table entries: 2048 (order: 11, 32768 bytes)
Oct  2 16:57:28 localhost kernel: [17179569.184000] Detected 1592.117 MHz processor.
Oct  2 16:57:28 localhost kernel: [17179569.184000] Using pmtmr for high-res timesource
Oct  2 16:57:28 localhost kernel: [17179569.184000] Console: colour VGA+ 80x25
Oct  2 16:57:28 localhost kernel: [17179572.208000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Oct  2 16:57:28 localhost kernel: [17179572.208000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Oct  2 16:57:28 localhost kernel: [17179572.220000] Memory: 507116k/523200k available (2103k kernel code, 15536k reserved, 599k data, 332k init, 0k highmem)
Oct  2 16:57:28 localhost kernel: [17179572.220000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Oct  2 16:57:28 localhost kernel: [17179572.300000] Calibrating delay using timer specific routine.. 3189.05 BogoMIPS (lpj=6378106)
Oct  2 16:57:28 localhost kernel: [17179572.300000] Security Framework v1.0.0 initialized
Oct  2 16:57:28 localhost kernel: [17179572.300000] SELinux:  Disabled at boot.
Oct  2 16:57:28 localhost kernel: [17179572.300000] Mount-cache hash table entries: 512
Oct  2 16:57:28 localhost kernel: [17179572.300000] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
Oct  2 16:57:28 localhost kernel: [17179572.300000] CPU: After vendor identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
Oct  2 16:57:28 localhost kernel: [17179572.300000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Oct  2 16:57:28 localhost kernel: [17179572.300000] CPU: L2 Cache: 1024K (64 bytes/line)
Oct  2 16:57:28 localhost kernel: [17179572.300000] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001
Oct  2 16:57:28 localhost kernel: [17179572.300000] mtrr: v2.0 (20020519)
Oct  2 16:57:28 localhost kernel: [17179572.300000] Enabling fast FPU save and restore... done.
Oct  2 16:57:28 localhost kernel: [17179572.300000] Enabling unmasked SIMD FPU exception support... done.
Oct  2 16:57:28 localhost kernel: [17179572.300000] Checking 'hlt' instruction... OK.
Oct  2 16:57:28 localhost kernel: [17179572.316000] SMP alternatives: switching to UP code
Oct  2 16:57:28 localhost kernel: [17179572.316000] checking if image is initramfs... it is
Oct  2 16:57:28 localhost kernel: [17179572.948000] Freeing initrd memory: 6773k freed
Oct  2 16:57:28 localhost kernel: [17179572.956000] ACPI: Looking for DSDT ... not found!
Oct  2 16:57:28 localhost kernel: [17179573.564000] CPU0: AMD Turion(tm) 64 Mobile Technology ML-30 stepping 02
Oct  2 16:57:28 localhost kernel: [17179573.564000] Total of 1 processors activated (3189.05 BogoMIPS).
Oct  2 16:57:28 localhost kernel: [17179573.564000] ENABLING IO-APIC IRQs
Oct  2 16:57:28 localhost kernel: [17179573.564000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
Oct  2 16:57:28 localhost kernel: [17179573.708000] Brought up 1 CPUs
Oct  2 16:57:28 localhost kernel: [17179573.708000] NET: Registered protocol family 16
Oct  2 16:57:28 localhost kernel: [17179573.708000] EISA bus registered
Oct  2 16:57:28 localhost kernel: [17179573.708000] ACPI: bus type pci registered
Oct  2 16:57:28 localhost kernel: [17179573.708000] PCI: PCI BIOS revision 2.10 entry at 0xfd67c, last bus=7
Oct  2 16:57:28 localhost kernel: [17179573.708000] PCI: Using MMCONFIG
Oct  2 16:57:28 localhost kernel: [17179573.708000] ACPI: Subsystem revision 20051216
Oct  2 16:57:28 localhost kernel: [17179573.776000] ACPI: Interpreter enabled
Oct  2 16:57:28 localhost kernel: [17179573.776000] ACPI: Using IOAPIC for interrupt routing
Oct  2 16:57:28 localhost kernel: [17179573.776000] ACPI: PCI Root Bridge [PCI0] (0000:00)
Oct  2 16:57:28 localhost kernel: [17179573.776000] PCI: Probing PCI hardware (bus 00)
Oct  2 16:57:28 localhost kernel: [17179573.780000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:14.1
Oct  2 16:57:28 localhost kernel: [17179573.780000] Boot video device is 0000:01:00.0
Oct  2 16:57:28 localhost kernel: [17179573.780000] PCI: Transparent bridge - 0000:00:14.4
Oct  2 16:57:28 localhost kernel: [17179573.780000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Oct  2 16:57:28 localhost kernel: [17179573.788000] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
Oct  2 16:57:28 localhost kernel: [17179573.788000] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
Oct  2 16:57:28 localhost kernel: [17179573.788000] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
Oct  2 16:57:28 localhost kernel: [17179573.788000] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
Oct  2 16:57:28 localhost kernel: [17179573.788000] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
Oct  2 16:57:28 localhost kernel: [17179573.788000] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
Oct  2 16:57:28 localhost kernel: [17179573.788000] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
Oct  2 16:57:28 localhost kernel: [17179573.788000] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
Oct  2 16:57:28 localhost kernel: [17179573.792000] ACPI: Embedded Controller [EC0] (gpe 16) interrupt mode.
Oct  2 16:57:28 localhost kernel: [17179573.808000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB2_._PRT]
Oct  2 16:57:28 localhost kernel: [17179573.808000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
Oct  2 16:57:28 localhost kernel: [17179573.808000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
Oct  2 16:57:28 localhost kernel: [17179573.808000] Linux Plug and Play Support v0.97 (c) Adam Belay
Oct  2 16:57:28 localhost kernel: [17179573.808000] pnp: PnP ACPI init
Oct  2 16:57:28 localhost kernel: [17179573.812000] pnp: PnP ACPI: found 12 devices
Oct  2 16:57:28 localhost kernel: [17179573.812000] PnPBIOS: Disabled by ACPI PNP
Oct  2 16:57:28 localhost kernel: [17179573.812000] PCI: Using ACPI for IRQ routing
Oct  2 16:57:28 localhost kernel: [17179573.812000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Oct  2 16:57:28 localhost kernel: [17179573.836000] pnp: 00:06: ioport range 0x1080-0x1080 has been reserved
Oct  2 16:57:28 localhost kernel: [17179573.836000] pnp: 00:06: ioport range 0x87f-0x87f has been reserved
Oct  2 16:57:28 localhost kernel: [17179573.836000] PCI: Bridge: 0000:00:02.0
Oct  2 16:57:28 localhost kernel: [17179573.836000]   IO window: 9000-9fff
Oct  2 16:57:28 localhost kernel: [17179573.836000]   MEM window: c0100000-c01fffff
Oct  2 16:57:28 localhost kernel: [17179573.836000]   PREFETCH window: c8000000-cfffffff
Oct  2 16:57:28 localhost kernel: [17179573.836000] PCI: Bridge: 0000:00:06.0
Oct  2 16:57:28 localhost kernel: [17179573.836000]   IO window: disabled.
Oct  2 16:57:28 localhost kernel: [17179573.836000]   MEM window: c0200000-c02fffff
Oct  2 16:57:28 localhost kernel: [17179573.836000]   PREFETCH window: disabled.
Oct  2 16:57:28 localhost kernel: [17179573.836000] PCI: Bus 7, cardbus bridge: 0000:06:09.0
Oct  2 16:57:28 localhost kernel: [17179573.836000]   IO window: 00002000-000020ff
Oct  2 16:57:28 localhost kernel: [17179573.836000]   IO window: 00002400-000024ff
Oct  2 16:57:28 localhost kernel: [17179573.836000]   PREFETCH window: 30000000-31ffffff
Oct  2 16:57:28 localhost kernel: [17179573.836000]   MEM window: 32000000-33ffffff
Oct  2 16:57:28 localhost kernel: [17179573.836000] PCI: Bridge: 0000:00:14.4
Oct  2 16:57:28 localhost kernel: [17179573.836000]   IO window: 2000-2fff
Oct  2 16:57:28 localhost kernel: [17179573.836000]   MEM window: c0300000-c03fffff
Oct  2 16:57:28 localhost kernel: [17179573.836000]   PREFETCH window: 30000000-31ffffff
Oct  2 16:57:28 localhost kernel: [17179573.836000] PCI: Setting latency timer of device 0000:00:02.0 to 64
Oct  2 16:57:28 localhost kernel: [17179573.836000] PCI: Setting latency timer of device 0000:00:06.0 to 64
Oct  2 16:57:28 localhost kernel: [17179573.836000] PCI: Enabling device 0000:06:09.0 (0004 -> 0007)
Oct  2 16:57:28 localhost kernel: [17179573.836000] ACPI: PCI Interrupt 0000:06:09.0[A] -> GSI 23 (level, low) -> IRQ 185
Oct  2 16:57:28 localhost kernel: [17179573.836000] audit: initializing netlink socket (disabled)
Oct  2 16:57:28 localhost kernel: [17179573.836000] audit(1159808215.832:1): initialized
Oct  2 16:57:28 localhost kernel: [17179573.836000] VFS: Disk quotas dquot_6.5.1
Oct  2 16:57:28 localhost kernel: [17179573.836000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Oct  2 16:57:28 localhost kernel: [17179573.836000] Initializing Cryptographic API
Oct  2 16:57:28 localhost kernel: [17179573.836000] io scheduler noop registered
Oct  2 16:57:28 localhost kernel: [17179573.836000] io scheduler anticipatory registered
Oct  2 16:57:28 localhost kernel: [17179573.836000] io scheduler deadline registered
Oct  2 16:57:28 localhost kernel: [17179573.836000] io scheduler cfq registered (default)
Oct  2 16:57:28 localhost kernel: [17179573.836000] PCI: Setting latency timer of device 0000:00:02.0 to 64
Oct  2 16:57:28 localhost kernel: [17179573.836000] pcie_portdrv_probe->Dev[5a34:1002] has invalid IRQ. Check vendor BIOS
Oct  2 16:57:28 localhost kernel: [17179573.836000] assign_interrupt_mode Found MSI capability
Oct  2 16:57:28 localhost kernel: [17179573.836000] Allocate Port Service[pcie00]
Oct  2 16:57:28 localhost kernel: [17179573.836000] Allocate Port Service[pcie01]
Oct  2 16:57:28 localhost kernel: [17179573.836000] PCI: Setting latency timer of device 0000:00:06.0 to 64
Oct  2 16:57:28 localhost kernel: [17179573.836000] pcie_portdrv_probe->Dev[5a38:1002] has invalid IRQ. Check vendor BIOS
Oct  2 16:57:28 localhost kernel: [17179573.836000] assign_interrupt_mode Found MSI capability
Oct  2 16:57:28 localhost kernel: [17179573.836000] Allocate Port Service[pcie00]
Oct  2 16:57:28 localhost kernel: [17179573.836000] Allocate Port Service[pcie01]
Oct  2 16:57:28 localhost kernel: [17179573.840000] isapnp: Scanning for PnP cards...
Oct  2 16:57:28 localhost kernel: [17179574.752000] isapnp: No Plug & Play device found
Oct  2 16:57:28 localhost kernel: [17179574.768000] Real Time Clock Driver v1.12
Oct  2 16:57:28 localhost kernel: [17179574.768000] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
Oct  2 16:57:28 localhost kernel: [17179574.772000] i8042.c: Detected active multiplexing controller, rev 1.1.
Oct  2 16:57:28 localhost kernel: [17179574.776000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Oct  2 16:57:28 localhost kernel: [17179574.776000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Oct  2 16:57:28 localhost kernel: [17179574.776000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Oct  2 16:57:28 localhost kernel: [17179574.780000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Oct  2 16:57:28 localhost kernel: [17179574.780000] serio: i8042 KBD port at 0x60,0x64 irq 1
Oct  2 16:57:28 localhost kernel: [17179574.780000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
Oct  2 16:57:28 localhost kernel: [17179574.780000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Oct  2 16:57:28 localhost kernel: [17179574.780000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a NS16550A
Oct  2 16:57:28 localhost kernel: [17179574.780000] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Oct  2 16:57:28 localhost kernel: [17179574.780000] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 217
Oct  2 16:57:28 localhost kernel: [17179574.780000] ACPI: PCI interrupt for device 0000:00:14.6 disabled
Oct  2 16:57:28 localhost kernel: [17179574.780000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Oct  2 16:57:28 localhost kernel: [17179574.780000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Oct  2 16:57:28 localhost kernel: [17179574.780000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Oct  2 16:57:28 localhost kernel: [17179574.780000] mice: PS/2 mouse device common for all mice
Oct  2 16:57:28 localhost kernel: [17179574.784000] EISA: Probing bus 0 at eisa.0
Oct  2 16:57:28 localhost kernel: [17179574.784000] Cannot allocate resource for EISA slot 1
Oct  2 16:57:28 localhost kernel: [17179574.784000] Cannot allocate resource for EISA slot 2
Oct  2 16:57:28 localhost kernel: [17179574.784000] Cannot allocate resource for EISA slot 8
Oct  2 16:57:28 localhost kernel: [17179574.784000] EISA: Detected 0 cards.
Oct  2 16:57:28 localhost kernel: [17179574.784000] NET: Registered protocol family 2
Oct  2 16:57:28 localhost kernel: [17179574.824000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
Oct  2 16:57:28 localhost kernel: [17179574.824000] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
Oct  2 16:57:28 localhost kernel: [17179574.824000] TCP bind hash table entries: 16384 (order: 5, 196608 bytes)
Oct  2 16:57:28 localhost kernel: [17179574.824000] TCP: Hash tables configured (established 16384 bind 16384)
Oct  2 16:57:28 localhost kernel: [17179574.824000] TCP reno registered
Oct  2 16:57:28 localhost kernel: [17179574.824000] TCP bic registered
Oct  2 16:57:28 localhost kernel: [17179574.824000] NET: Registered protocol family 1
Oct  2 16:57:28 localhost kernel: [17179574.824000] NET: Registered protocol family 8
Oct  2 16:57:28 localhost kernel: [17179574.824000] NET: Registered protocol family 20
Oct  2 16:57:28 localhost kernel: [17179574.824000] Using IPI No-Shortcut mode
Oct  2 16:57:28 localhost kernel: [17179574.824000] ACPI wakeup devices: 
Oct  2 16:57:28 localhost kernel: [17179574.824000] OHC1 OHC2 EHCI  LAN  P2P AUDO MODM 
Oct  2 16:57:28 localhost kernel: [17179574.824000] ACPI: (supports S0 S3 S4 S5)
Oct  2 16:57:28 localhost kernel: [17179574.824000] Freeing unused kernel memory: 332k freed
Oct  2 16:57:28 localhost kernel: [17179574.880000] vga16fb: initializing
Oct  2 16:57:28 localhost kernel: [17179574.880000] vga16fb: mapped to 0xc00a0000
Oct  2 16:57:28 localhost kernel: [17179575.020000] Console: switching to colour frame buffer device 80x25
Oct  2 16:57:28 localhost kernel: [17179575.020000] fb0: VGA16 VGA frame buffer device
Oct  2 16:57:28 localhost kernel: [17179575.160000] input: AT Translated Set 2 keyboard as /class/input/input0
Oct  2 16:57:28 localhost kernel: [17179576.088000] Capability LSM initialized
Oct  2 16:57:28 localhost kernel: [17179576.256000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Oct  2 16:57:28 localhost kernel: [17179576.256000] ACPI: Processor [CPU0] (supports 8 throttling states)
Oct  2 16:57:28 localhost kernel: [17179576.260000] ACPI: Thermal Zone [THRM] (55 C)
Oct  2 16:57:28 localhost kernel: [17179576.804000] ATIIXP: IDE controller at PCI slot 0000:00:14.1
Oct  2 16:57:28 localhost kernel: [17179576.804000] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 225
Oct  2 16:57:28 localhost kernel: [17179576.804000] ATIIXP: chipset revision 0
Oct  2 16:57:28 localhost kernel: [17179576.804000] ATIIXP: not 100%% native mode: will probe irqs later
Oct  2 16:57:28 localhost kernel: [17179576.804000]     ide0: BM-DMA at 0x8410-0x8417, BIOS settings: hda:DMA, hdb:pio
Oct  2 16:57:28 localhost kernel: [17179576.804000]     ide1: BM-DMA at 0x8418-0x841f, BIOS settings: hdc:DMA, hdd:pio
Oct  2 16:57:28 localhost kernel: [17179576.804000] Probing IDE interface ide0...
Oct  2 16:57:28 localhost kernel: [17179577.096000] hda: HTS541080G9AT00, ATA DISK drive
Oct  2 16:57:28 localhost kernel: [17179577.768000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Oct  2 16:57:28 localhost kernel: [17179577.784000] Probing IDE interface ide1...
Oct  2 16:57:28 localhost kernel: [17179578.520000] hdc: MATSHITADVD-RAM UJ-845S, ATAPI CD/DVD-ROM drive
Oct  2 16:57:28 localhost kernel: [17179578.856000] ide1 at 0x170-0x177,0x376 on irq 15
Oct  2 16:57:28 localhost kernel: [17179578.864000] hda: max request size: 1024KiB
Oct  2 16:57:28 localhost kernel: [17179578.872000] hda: 156301488 sectors (80026 MB) w/7539KiB Cache, CHS=16383/255/63, UDMA(100)
Oct  2 16:57:28 localhost kernel: [17179578.872000] hda: cache flushes supported
Oct  2 16:57:28 localhost kernel: [17179578.872000]  hda: hda1 hda2 hda3 < hda5 hda6 > hda4
Oct  2 16:57:28 localhost kernel: [17179578.940000] hdc: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
Oct  2 16:57:28 localhost kernel: [17179578.940000] Uniform CD-ROM driver Revision: 3.20
Oct  2 16:57:28 localhost kernel: [17179579.392000] usbcore: registered new driver usbfs
Oct  2 16:57:28 localhost kernel: [17179579.392000] usbcore: registered new driver hub
Oct  2 16:57:28 localhost kernel: [17179579.504000] ieee1394: Initialized config rom entry `ip1394'
Oct  2 16:57:28 localhost kernel: [17179579.504000] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
Oct  2 16:57:28 localhost kernel: [17179579.504000] ACPI: PCI Interrupt 0000:06:09.2[C] -> GSI 21 (level, low) -> IRQ 177
Oct  2 16:57:28 localhost kernel: [17179579.520000] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 233
Oct  2 16:57:28 localhost kernel: [17179579.520000] ehci_hcd 0000:00:13.2: EHCI Host Controller
Oct  2 16:57:28 localhost kernel: [17179579.520000] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
Oct  2 16:57:28 localhost kernel: [17179579.520000] ehci_hcd 0000:00:13.2: irq 233, io mem 0xc0002000
Oct  2 16:57:28 localhost kernel: [17179579.520000] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Oct  2 16:57:28 localhost kernel: [17179579.732000] hub 1-0:1.0: USB hub found
Oct  2 16:57:28 localhost kernel: [17179579.732000] hub 1-0:1.0: 8 ports detected
Oct  2 16:57:28 localhost kernel: [17179579.732000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
Oct  2 16:57:28 localhost kernel: [17179579.732000] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 233
Oct  2 16:57:28 localhost kernel: [17179579.732000] ohci_hcd 0000:00:13.0: OHCI Host Controller
Oct  2 16:57:28 localhost kernel: [17179580.068000] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
Oct  2 16:57:28 localhost kernel: [17179580.068000] ohci_hcd 0000:00:13.0: irq 233, io mem 0xc0000000
Oct  2 16:57:28 localhost kernel: [17179580.092000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[177]  MMIO=[c0309000-c03097ff]  Max Packet=[2048]
Oct  2 16:57:28 localhost kernel: [17179580.128000] hub 2-0:1.0: USB hub found
Oct  2 16:57:28 localhost kernel: [17179580.128000] hub 2-0:1.0: 4 ports detected
Oct  2 16:57:28 localhost kernel: [17179580.232000] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 233
Oct  2 16:57:28 localhost kernel: [17179580.232000] ohci_hcd 0000:00:13.1: OHCI Host Controller
Oct  2 16:57:28 localhost kernel: [17179580.564000] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
Oct  2 16:57:28 localhost kernel: [17179580.564000] ohci_hcd 0000:00:13.1: irq 233, io mem 0xc0001000
Oct  2 16:57:28 localhost kernel: [17179580.624000] hub 3-0:1.0: USB hub found
Oct  2 16:57:28 localhost kernel: [17179580.624000] hub 3-0:1.0: 4 ports detected
Oct  2 16:57:28 localhost kernel: [17179580.924000] Attempting manual resume
Oct  2 16:57:28 localhost kernel: [17179580.968000] EXT3-fs: mounted filesystem with ordered data mode.
Oct  2 16:57:28 localhost kernel: [17179580.976000] kjournald starting.  Commit interval 5 seconds
Oct  2 16:57:28 localhost kernel: [17179581.032000] usb 3-3: new low speed USB device using ohci_hcd and address 2
Oct  2 16:57:28 localhost kernel: [17179581.364000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00c09f000074c6a7]
Oct  2 16:57:28 localhost kernel: [17179597.408000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Oct  2 16:57:28 localhost kernel: [17179597.412000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Oct  2 16:57:28 localhost kernel: [17179597.412000] Linux agpgart interface v0.101 (c) Dave Jones
Oct  2 16:57:28 localhost kernel: [17179597.424000] usbcore: registered new driver hiddev
Oct  2 16:57:28 localhost kernel: [17179597.432000] input: Microsoft Microsoft Notebook/Mobile Optical Mouse 2.0 as /class/input/input1
Oct  2 16:57:28 localhost kernel: [17179597.432000] input: USB HID v1.10 Mouse [Microsoft Microsoft Notebook/Mobile Optical Mouse 2.0] on usb-0000:00:13.1-3
Oct  2 16:57:28 localhost kernel: [17179597.432000] usbcore: registered new driver usbhid
Oct  2 16:57:28 localhost kernel: [17179597.432000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
Oct  2 16:57:28 localhost kernel: [17179597.760000] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 217
Oct  2 16:57:28 localhost kernel: [17179597.840000] tg3.c:v3.47 (Dec 28, 2005)
Oct  2 16:57:28 localhost kernel: [17179597.840000] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 50
Oct  2 16:57:28 localhost kernel: [17179597.840000] PCI: Setting latency timer of device 0000:05:00.0 to 64
Oct  2 16:57:28 localhost kernel: [17179597.852000] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 217
Oct  2 16:57:28 localhost kernel: [17179597.876000] eth0: Tigon3 [partno(BCM95789) rev 4101 PHY(5750)] (PCI Express) 10/100/1000BaseT Ethernet 00:c0:9f:f4:69:1b
Oct  2 16:57:28 localhost kernel: [17179597.876000] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] Split[0] WireSpeed[1] TSOcap[1] 
Oct  2 16:57:28 localhost kernel: [17179597.876000] eth0: dma_rwctrl[76180000]
Oct  2 16:57:28 localhost kernel: [17179598.168000] input: PC Speaker as /class/input/input2
Oct  2 16:57:28 localhost kernel: [17179598.384000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x126eb1, caps: 0xa04713/0x4000
Oct  2 16:57:28 localhost kernel: [17179598.432000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
Oct  2 16:57:28 localhost kernel: [17179598.444000] ts: Compaq touchscreen protocol output
Oct  2 16:57:28 localhost kernel: [17179598.688000] ACPI: PCI Interrupt 0000:06:09.0[A] -> GSI 23 (level, low) -> IRQ 185
Oct  2 16:57:28 localhost kernel: [17179598.688000] Yenta: CardBus bridge found at 0000:06:09.0 [1025:007e]
Oct  2 16:57:28 localhost kernel: [17179598.688000] Yenta: Using CSCINT to route CSC interrupts to PCI
Oct  2 16:57:28 localhost kernel: [17179598.688000] Yenta: Routing CardBus interrupts to PCI
Oct  2 16:57:28 localhost kernel: [17179598.688000] Yenta TI: socket 0000:06:09.0, mfunc 0x01721b22, devctl 0x64
Oct  2 16:57:28 localhost kernel: [17179598.724000] parport: PnPBIOS parport detected.
Oct  2 16:57:28 localhost kernel: [17179598.724000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
Oct  2 16:57:28 localhost kernel: [17179598.764000] irda_init()
Oct  2 16:57:28 localhost kernel: [17179598.764000] NET: Registered protocol family 23
Oct  2 16:57:28 localhost kernel: [17179598.788000] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
Oct  2 16:57:28 localhost kernel: [17179598.820000] nsc-ircc, chip->init
Oct  2 16:57:28 localhost kernel: [17179598.820000] nsc-ircc, Found chip at base=0x02e
Oct  2 16:57:28 localhost kernel: [17179598.820000] nsc-ircc, driver loaded (Dag Brattli)
Oct  2 16:57:28 localhost kernel: [17179598.820000] nsc_ircc_open(), can't get iobase of 0x2f8
Oct  2 16:57:28 localhost kernel: [17179598.820000] nsc-ircc, Found chip at base=0x02e
Oct  2 16:57:28 localhost kernel: [17179598.820000] nsc-ircc, driver loaded (Dag Brattli)
Oct  2 16:57:28 localhost kernel: [17179598.820000] nsc_ircc_open(), can't get iobase of 0x2f8
Oct  2 16:57:28 localhost kernel: [17179598.820000] pnp: Device 00:09 disabled.
Oct  2 16:57:28 localhost kernel: [17179598.920000] Yenta: ISA IRQ mask 0x0e70, PCI irq 185
Oct  2 16:57:28 localhost kernel: [17179598.920000] Socket status: 30000006
Oct  2 16:57:28 localhost kernel: [17179598.920000] Yenta: Raising subordinate bus# of parent bus (#06) from #07 to #0a
Oct  2 16:57:28 localhost kernel: [17179598.920000] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
Oct  2 16:57:28 localhost kernel: [17179598.920000] cs: IO port probe 0x2000-0x2fff: clean.
Oct  2 16:57:28 localhost kernel: [17179598.920000] pcmcia: parent PCI bridge Memory window: 0xc0300000 - 0xc03fffff
Oct  2 16:57:28 localhost kernel: [17179598.920000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x31ffffff
Oct  2 16:57:28 localhost kernel: [17179599.244000] cs: IO port probe 0x100-0x3af: clean.
Oct  2 16:57:28 localhost kernel: [17179599.248000] cs: IO port probe 0x3e0-0x4ff: excluding 0x408-0x40f 0x4d0-0x4d7
Oct  2 16:57:28 localhost kernel: [17179599.248000] cs: IO port probe 0x820-0x8ff: clean.
Oct  2 16:57:28 localhost kernel: [17179599.248000] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf
Oct  2 16:57:28 localhost kernel: [17179599.248000] cs: IO port probe 0xa00-0xaff: clean.
Oct  2 16:57:28 localhost kernel: [17179599.632000] lp0: using parport0 (interrupt-driven).
Oct  2 16:57:28 localhost kernel: [17179599.672000] SCSI subsystem initialized
Oct  2 16:57:28 localhost kernel: [17179599.688000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
Oct  2 16:57:28 localhost kernel: [17179599.688000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
Oct  2 16:57:28 localhost kernel: [17179599.688000] ieee1394: sbp2: Try serialize_io=0 for better performance
Oct  2 16:57:28 localhost kernel: [17179599.780000] ndiswrapper version 1.8 loaded (preempt=yes,smp=yes)
Oct  2 16:57:28 localhost kernel: [17179599.884000] ndiswrapper: driver bcmwl5 (Broadcom,02/11/2005, 3.100.64.0) loaded
Oct  2 16:57:28 localhost kernel: [17179599.884000] ACPI: PCI Interrupt 0000:06:02.0[A] -> GSI 21 (level, low) -> IRQ 177
Oct  2 16:57:28 localhost kernel: [17179599.892000] ndiswrapper: using irq 177
Oct  2 16:57:28 localhost kernel: [17179601.056000] wlan0: vendor: ''
Oct  2 16:57:28 localhost kernel: [17179601.056000] wlan0: ndiswrapper ethernet device 00:14:a4:5d:3f:67 using driver bcmwl5, 14E4:4318.5.conf
Oct  2 16:57:28 localhost kernel: [17179601.056000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Oct  2 16:57:28 localhost kernel: [17179601.300000] Adding 417648k swap on /dev/hda6.  Priority:-1 extents:1 across:417648k
Oct  2 16:57:28 localhost kernel: [17179601.484000] EXT3 FS on hda4, internal journal
Oct  2 16:57:28 localhost kernel: [17179601.660000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
Oct  2 16:57:28 localhost kernel: [17179601.660000] md: bitmap version 4.39
Oct  2 16:57:28 localhost kernel: [17179602.248000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
Oct  2 16:57:28 localhost kernel: [17179602.840000] NET: Registered protocol family 17
Oct  2 16:57:28 localhost kernel: [17179602.972000] cdrom: open failed.
Oct  2 16:57:28 localhost kernel: [17179608.884000] ACPI: AC Adapter [ACAD] (on-line)
Oct  2 16:57:28 localhost kernel: [17179608.908000] ACPI: Battery Slot [BAT1] (battery present)
Oct  2 16:57:28 localhost kernel: [17179609.028000] ACPI: Power Button (FF) [PWRF]
Oct  2 16:57:28 localhost kernel: [17179609.028000] ACPI: Lid Switch [LID]
Oct  2 16:57:28 localhost kernel: [17179609.028000] ACPI: Power Button (CM) [PWRB]
Oct  2 16:57:28 localhost kernel: [17179609.028000] ACPI: Sleep Button (CM) [SLPB]
Oct  2 16:57:28 localhost kernel: [17179609.116000] ibm_acpi: ec object not found
Oct  2 16:57:28 localhost kernel: [17179609.144000] pcc_acpi: loading...
Oct  2 16:57:28 localhost kernel: [17179609.232000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Oct  2 16:57:28 localhost kernel: [17179609.596000] NET: Registered protocol family 10
Oct  2 16:57:28 localhost kernel: [17179609.596000] lo: Disabled Privacy Extensions
Oct  2 16:57:28 localhost kernel: [17179609.596000] IPv6 over IPv4 tunneling driver
Oct  2 16:57:28 localhost kernel: [17179609.800000] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.50.4)
Oct  2 16:57:28 localhost kernel: [17179609.800000] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x4 (1450 mV)
Oct  2 16:57:28 localhost kernel: [17179609.800000] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x16 (1000 mV)
Oct  2 16:57:28 localhost kernel: [17179609.800000] cpu_init done, current fid 0x8, vid 0x4
Oct  2 16:57:29 localhost slapd[4284]: @(#) $OpenLDAP: slapd 2.3.27 (Sep  1 2006 14:48:04) $ ^I@build32-dapper:/home/debuild/dapper/openldap/openldap2.3-2.3.27/debian/build/servers/slapd 
Oct  2 16:57:29 localhost atieventsd[4292]: ATI External Events Daemon started... 
Oct  2 16:57:29 localhost atieventsd[4292]: Event daemon control socket created 
Oct  2 16:57:29 localhost atieventsd[4292]: acpid connection established 
Oct  2 16:57:32 localhost kernel: [17179613.924000] ttyS1: LSR safety check engaged!
Oct  2 16:57:33 localhost dhcdbd: Started up.
Oct  2 16:57:33 localhost NetworkManager: <information>^Istarting... 
Oct  2 16:57:33 localhost NetworkManager: <WARNING>^I main (): nm_data_new: Setting up dbus filter 
Oct  2 16:57:33 localhost kernel: [17179615.500000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct  2 16:57:33 localhost NetworkManager: <information>^Ieth0: Device is fully-supported using driver 'tg3'. 
Oct  2 16:57:33 localhost NetworkManager: <information>^Inm_device_init(): waiting for device's worker thread to start 
Oct  2 16:57:33 localhost NetworkManager: <information>^Inm_device_init(): device's worker thread started, continuing. 
Oct  2 16:57:33 localhost NetworkManager: <information>^INow managing wired Ethernet (802.3) device 'eth0'. 
Oct  2 16:57:33 localhost avahi-daemon[4448]: Found user 'avahi' (UID 114) and group 'avahi' (GID 114).
Oct  2 16:57:33 localhost avahi-daemon[4448]: Successfully dropped root privileges.
Oct  2 16:57:33 localhost avahi-daemon[4448]: avahi-daemon 0.6.10 starting up.
Oct  2 16:57:34 localhost avahi-daemon[4448]: Successfully called chroot().
Oct  2 16:57:34 localhost avahi-daemon[4448]: Successfully dropped remaining capabilities.
Oct  2 16:57:34 localhost avahi-daemon[4448]: No service found in /etc/avahi/services.
Oct  2 16:57:34 localhost avahi-daemon[4448]: New relevant interface eth1.IPv4 for mDNS.
Oct  2 16:57:34 localhost avahi-daemon[4448]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.105.
Oct  2 16:57:34 localhost avahi-daemon[4448]: Network interface enumeration completed.
Oct  2 16:57:34 localhost avahi-daemon[4448]: Registering new address record for 192.168.1.105 on eth1.
Oct  2 16:57:34 localhost avahi-daemon[4448]: Registering HINFO record with values 'I686'/'LINUX'.

---

