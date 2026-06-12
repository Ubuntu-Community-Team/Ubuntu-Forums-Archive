---
title: "can't access tty 1-6"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by mackyman on 2007-03-07
I just bought a new laptop and installed kubuntu.

Now I can't access tty1-6 and get grafic glitches, and as I press ctrl + alt + backspace my computer freeze.

I talked to a friend who said that it was something with kernel framebuffer support, and that I probably have to recompile my kernel. And that lspci and dmesg was good to attach to for debugging.

lspci

```
mackyman@mackytop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Expr
ess Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Expre
ss PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Aud
io Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (r
ev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (r
ev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (r
ev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 
01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 
01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 
01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 
01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Control
ler (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (re
v 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA S
torage Controller IDE (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 71c5
02:06.0 CardBus bridge: Texas Instruments Unknown device 8039
02:06.1 FireWire (IEEE 1394): Texas Instruments Unknown device 803a
02:06.2 Mass storage controller: Texas Instruments Unknown device 803b
02:06.3 Class 0805: Texas Instruments Unknown device 803c
02:06.4 Communication controller: Texas Instruments Unknown device 803d
08:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5753M Gigabit Eth
ernet PCI Express (rev 21)
10:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Conne
ction (rev 02)

```

dmesg:

```

mackyman@mackytop:~$ dmesg
[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000007ffd0000 (usable)
[17179569.184000]  BIOS-e820: 000000007ffd0000 - 000000007ffe5600 (reserved)
[17179569.184000]  BIOS-e820: 000000007ffe5600 - 000000007fff8000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000007fff8000 - 0000000080000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fed20000 - 00000000fed9b000 (reserved)
[17179569.184000]  BIOS-e820: 00000000feda0000 - 00000000fedc0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffb00000 - 00000000ffc00000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[17179569.184000] 1151MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 524240
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 294864 pages, LIFO batch:31
[17179569.184000] DMI 2.4 present.
[17179569.184000] ACPI: RSDP (v002 HP                                    ) @ 0x000f7c00
[17179569.184000] ACPI: XSDT (v001 HPQOEM SLIC-MPC 0x00000001 HP   0x00000001) @ 0x7ffe57bc
[17179569.184000] ACPI: FADT (v004 HP     309F     0x00000003 HP   0x00000001) @ 0x7ffe5684
[17179569.184000] ACPI: SLIC (v001 HPQOEM SLIC-MPC 0x00000001 HP   0x00000001) @ 0x7ffe5820
[17179569.184000] ACPI: MADT (v001 HP     309F     0x00000001 HP   0x00000001) @ 0x7ffe5998
[17179569.184000] ACPI: MCFG (v001 HP     309F     0x00000001 HP   0x00000001) @ 0x7ffe5a00
[17179569.184000] ACPI: TCPA (v002 HP     309F     0x00000001 HP   0x00000001) @ 0x7ffe5a3c
[17179569.184000] ACPI: SSDT (v001 HP       HPQNLP 0x00000001 MSFT 0x0100000e) @ 0x7fff5826
[17179569.184000] ACPI: SSDT (v001 HP       HPQPAT 0x00000001 MSFT 0x0100000e) @ 0x7fff587f
[17179569.184000] ACPI: SSDT (v001 HP        CpuPm 0x00003000 INTL 0x20060317) @ 0x7fff604a
[17179569.184000] ACPI: DSDT (v001 HP       nc9700 0x00010000 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:15 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[17179569.184000] Processor #1 6:15 APIC version 20
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/sda6 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[17179569.184000] Detected 1829.074 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179573.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179573.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179573.068000] Memory: 2069088k/2096960k available (1910k kernel code, 26540k reserved, 1070k data, 308k init, 1179456k highmem)
[17179573.068000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179573.148000] Calibrating delay using timer specific routine.. 3663.93 BogoMIPS (lpj=7327865)
[17179573.148000] Security Framework v1.0.0 initialized
[17179573.148000] SELinux:  Disabled at boot.
[17179573.148000] Mount-cache hash table entries: 512
[17179573.148000] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[17179573.148000] CPU: After vendor identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[17179573.148000] monitor/mwait feature present.
[17179573.148000] using mwait in idle threads.
[17179573.148000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179573.148000] CPU: L2 cache: 2048K
[17179573.148000] CPU: Hyper-Threading is disabled
[17179573.148000] CPU: After all inits, caps: bfebfbff 20100000 00000000 00000140 0000e3bd 00000000 00000001
[17179573.148000] Checking 'hlt' instruction... OK.
[17179573.164000] SMP alternatives: switching to UP code
[17179573.164000] checking if image is initramfs... it is
[17179573.632000] Freeing initrd memory: 5523k freed
[17179573.632000] ACPI: Core revision 20060707
[17179573.632000] ACPI: Looking for DSDT ... not found!
[17179573.708000] CPU0: Intel(R) Core(TM)2 CPU         T5600  @ 1.83GHz stepping 06
[17179573.708000] SMP alternatives: switching to SMP code
[17179573.708000] Booting processor 1/1 eip 3000
[17179573.720000] Initializing CPU#1
[17179573.800000] Calibrating delay using timer specific routine.. 3657.94 BogoMIPS (lpj=7315898)
[17179573.800000] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[17179573.800000] CPU: After vendor identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[17179573.800000] monitor/mwait feature present.
[17179573.800000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179573.800000] CPU: L2 cache: 2048K
[17179573.800000] CPU: Hyper-Threading is disabled
[17179573.800000] CPU: After all inits, caps: bfebfbff 20100000 00000000 00000140 0000e3bd 00000000 00000001
[17179573.800000] CPU1: Intel(R) Core(TM)2 CPU         T5600  @ 1.83GHz stepping 06
[17179573.800000] Total of 2 processors activated (7321.88 BogoMIPS).
[17179573.800000] ENABLING IO-APIC IRQs
[17179573.800000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179573.944000] checking TSC synchronization across 2 CPUs: passed.
[17179573.948000] Brought up 2 CPUs
[17179574.100000] migration_cost=4000
[17179574.100000] HP Compaq Laptop series board detected. Selecting BIOS-method for reboots.
[17179574.100000] NET: Registered protocol family 16
[17179574.100000] EISA bus registered
[17179574.100000] ACPI: bus type pci registered
[17179574.100000] PCI: BIOS Bug: MCFG area at f8000000 is not E820-reserved
[17179574.100000] PCI: Not using MMCONFIG.
[17179574.100000] PCI: PCI BIOS revision 2.10 entry at 0xf0322, last bus=32
[17179574.100000] PCI: Using configuration type 1
[17179574.100000] Setting up standard PCI resources
[17179574.156000] ACPI: Interpreter enabled
[17179574.156000] ACPI: Using IOAPIC for interrupt routing
[17179574.156000] ACPI: PCI Root Bridge [C003] (0000:00)
[17179574.156000] PCI: Probing PCI hardware (bus 00)
[17179574.156000] ACPI: Assume root bridge [\_SB_.C003] bus is 0
[17179574.164000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.2
[17179574.164000] Boot video device is 0000:01:00.0
[17179574.164000] PCI: Transparent bridge - 0000:00:1e.0
[17179574.164000] PCI: Bus #03 (-#06) is hidden behind transparent bridge #02 (-#03) (try 'pci=assign-busses')
[17179574.164000] Please report the result to linux-kernel to fix this permanently
[17179574.164000] ACPI: PCI Interrupt Routing Table [\_SB_.C003._PRT]
[17179574.196000] ACPI: PCI Interrupt Routing Table [\_SB_.C003.C07F._PRT]
[17179574.196000] ACPI: PCI Interrupt Routing Table [\_SB_.C003.C094._PRT]
[17179574.196000] ACPI: Embedded Controller [C006] (gpe 22) interrupt mode.
[17179574.212000] ACPI: Power Resource [C1F4] (on)
[17179574.212000] ACPI: Power Resource [C20D] (on)
[17179574.212000] ACPI: PCI Interrupt Routing Table [\_SB_.C003.C0FB._PRT]
[17179574.212000] ACPI: PCI Interrupt Routing Table [\_SB_.C003.C10B._PRT]
[17179574.216000] ACPI: PCI Interrupt Routing Table [\_SB_.C003.C111._PRT]
[17179574.216000] ACPI: Power Resource [C215] (on)
[17179574.216000] ACPI: PCI Interrupt Link [C107] (IRQs *10 11)
[17179574.216000] ACPI: PCI Interrupt Link [C108] (IRQs *10 11)
[17179574.216000] ACPI: PCI Interrupt Link [C109] (IRQs 10 *11)
[17179574.216000] ACPI: PCI Interrupt Link [C10A] (IRQs 10 11) *5
[17179574.216000] ACPI: PCI Interrupt Link [C11D] (IRQs *10 11)
[17179574.216000] ACPI: PCI Interrupt Link [C11E] (IRQs 10 11) *0, disabled.
[17179574.220000] ACPI: PCI Interrupt Link [C11F] (IRQs 10 *11)
[17179574.220000] ACPI Exception (pci_link-0182): AE_NOT_FOUND, Evaluating _PRS [20060707]
[17179574.220000] ACPI: Power Resource [C318] (off)
[17179574.220000] ACPI: Power Resource [C319] (off)
[17179574.220000] ACPI: Power Resource [C31A] (off)
[17179574.220000] ACPI: Power Resource [C31B] (off)
[17179574.220000] ACPI: Power Resource [C31C] (off)
[17179574.220000] ACPI: Power Resource [C31D] (off)
[17179574.220000] ACPI: Power Resource [C31E] (off)
[17179574.220000] ACPI: Power Resource [C31F] (off)
[17179574.220000] ACPI: Power Resource [C320] (off)
[17179574.220000] ACPI: Power Resource [C321] (off)
[17179574.220000] ACPI: Power Resource [C322] (off)
[17179574.224000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179574.224000] pnp: PnP ACPI init
[17179574.232000] pnp: PnP ACPI: found 14 devices
[17179574.232000] PnPBIOS: Disabled by ACPI PNP
[17179574.232000] PCI: Using ACPI for IRQ routing
[17179574.232000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179574.356000] pnp: 00:0c: ioport range 0x4d0-0x4d1 has been reserved
[17179574.356000] pnp: 00:0c: ioport range 0x1000-0x107f could not be reserved
[17179574.356000] pnp: 00:0c: ioport range 0x1100-0x113f has been reserved
[17179574.356000] pnp: 00:0c: ioport range 0x1200-0x121f has been reserved
[17179574.356000] PCI: Bridge: 0000:00:01.0
[17179574.356000]   IO window: 4000-4fff
[17179574.356000]   MEM window: f4600000-f46fffff
[17179574.356000]   PREFETCH window: e0000000-efffffff
[17179574.356000] PCI: Bridge: 0000:00:1c.0
[17179574.356000]   IO window: disabled.
[17179574.356000]   MEM window: f4100000-f41fffff
[17179574.356000]   PREFETCH window: disabled.
[17179574.356000] PCI: Bridge: 0000:00:1c.1
[17179574.356000]   IO window: disabled.
[17179574.356000]   MEM window: f4000000-f40fffff
[17179574.356000]   PREFETCH window: disabled.
[17179574.356000] PCI: Bridge: 0000:00:1c.3
[17179574.356000]   IO window: 2000-3fff
[17179574.356000]   MEM window: f0000000-f3ffffff
[17179574.356000]   PREFETCH window: disabled.
[17179574.356000] PCI: Bus 3, cardbus bridge: 0000:02:06.0
[17179574.356000]   IO window: 00006000-000060ff
[17179574.356000]   IO window: 00006400-000064ff
[17179574.356000]   PREFETCH window: 88000000-89ffffff
[17179574.356000]   MEM window: 8a000000-8bffffff
[17179574.356000] PCI: Bridge: 0000:00:1e.0
[17179574.356000]   IO window: 6000-6fff
[17179574.356000]   MEM window: f4200000-f45fffff
[17179574.356000]   PREFETCH window: 88000000-89ffffff
[17179574.356000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 177
[17179574.356000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179574.356000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 177
[17179574.356000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179574.356000] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 185
[17179574.356000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[17179574.360000] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 193
[17179574.360000] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[17179574.360000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179574.360000] ACPI: PCI Interrupt 0000:02:06.0[A] -> GSI 18 (level, low) -> IRQ 201
[17179574.360000] NET: Registered protocol family 2
[17179574.396000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179574.396000] TCP established hash table entries: 262144 (order: 9, 2097152 bytes)
[17179574.396000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[17179574.396000] TCP: Hash tables configured (established 262144 bind 65536)
[17179574.396000] TCP reno registered
[17179574.396000] audit: initializing netlink socket (disabled)
[17179574.396000] audit(1173293296.396:1): initialized
[17179574.396000] highmem bounce pool size: 64 pages
[17179574.396000] VFS: Disk quotas dquot_6.5.1
[17179574.396000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179574.396000] Initializing Cryptographic API
[17179574.396000] io scheduler noop registered
[17179574.396000] io scheduler anticipatory registered
[17179574.396000] io scheduler deadline registered
[17179574.396000] io scheduler cfq registered (default)
[17179574.396000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 177
[17179574.396000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179574.396000] assign_interrupt_mode Found MSI capability
[17179574.396000] Allocate Port Service[0000:00:01.0:pcie00]
[17179574.396000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 177
[17179574.396000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179574.396000] assign_interrupt_mode Found MSI capability
[17179574.396000] Allocate Port Service[0000:00:1c.0:pcie00]
[17179574.396000] Allocate Port Service[0000:00:1c.0:pcie02]
[17179574.396000] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 185
[17179574.396000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[17179574.396000] assign_interrupt_mode Found MSI capability
[17179574.396000] Allocate Port Service[0000:00:1c.1:pcie00]
[17179574.396000] Allocate Port Service[0000:00:1c.1:pcie02]
[17179574.396000] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 193
[17179574.396000] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[17179574.396000] assign_interrupt_mode Found MSI capability
[17179574.396000] Allocate Port Service[0000:00:1c.3:pcie00]
[17179574.396000] Allocate Port Service[0000:00:1c.3:pcie02]
[17179574.396000] isapnp: Scanning for PnP cards...
[17179574.752000] isapnp: No Plug & Play device found
[17179574.772000] Real Time Clock Driver v1.12ac
[17179574.772000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179574.772000] mice: PS/2 mouse device common for all mice
[17179574.772000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179574.772000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179574.772000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179574.772000] PNP: PS/2 Controller [PNP0303:C20A,PNP0f13:C20B] at 0x60,0x64 irq 1,12
[17179574.772000] i8042.c: Detected active multiplexing controller, rev 1.1.
[17179574.776000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[17179574.776000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[17179574.776000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[17179574.776000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[17179574.776000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179574.776000] EISA: Probing bus 0 at eisa.0
[17179574.776000] Cannot allocate resource for EISA slot 1
[17179574.776000] Cannot allocate resource for EISA slot 2
[17179574.776000] Cannot allocate resource for EISA slot 3
[17179574.776000] Cannot allocate resource for EISA slot 4
[17179574.776000] Cannot allocate resource for EISA slot 5
[17179574.776000] Cannot allocate resource for EISA slot 6
[17179574.776000] EISA: Detected 0 cards.
[17179574.776000] TCP bic registered
[17179574.776000] NET: Registered protocol family 1
[17179574.776000] NET: Registered protocol family 8
[17179574.776000] NET: Registered protocol family 20
[17179574.776000] Starting balanced_irq
[17179574.776000] Using IPI No-Shortcut mode
[17179574.776000] ACPI: (supports S0 S3 S4 S5)
[17179574.776000] Freeing unused kernel memory: 308k freed
[17179574.808000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179575.848000] Capability LSM initialized
[17179575.876000] ACPI: Transitioning device [C323] to D3
[17179575.876000] ACPI: Transitioning device [C323] to D3
[17179575.876000] ACPI: Fan [C323] (off)
[17179575.876000] ACPI: Transitioning device [C324] to D3
[17179575.876000] ACPI: Transitioning device [C324] to D3
[17179575.876000] ACPI: Fan [C324] (off)
[17179575.876000] ACPI: Transitioning device [C325] to D3
[17179575.876000] ACPI: Transitioning device [C325] to D3
[17179575.876000] ACPI: Fan [C325] (off)
[17179575.876000] ACPI: Transitioning device [C326] to D3
[17179575.876000] ACPI: Transitioning device [C326] to D3
[17179575.876000] ACPI: Fan [C326] (off)
[17179575.876000] ACPI: Transitioning device [C327] to D3
[17179575.876000] ACPI: Transitioning device [C327] to D3
[17179575.876000] ACPI: Fan [C327] (off)
[17179575.876000] ACPI: Transitioning device [C328] to D3
[17179575.876000] ACPI: Transitioning device [C328] to D3
[17179575.876000] ACPI: Fan [C328] (off)
[17179575.876000] ACPI: Transitioning device [C329] to D3
[17179575.876000] ACPI: Transitioning device [C329] to D3
[17179575.876000] ACPI: Fan [C329] (off)
[17179575.876000] ACPI: Transitioning device [C32A] to D3
[17179575.876000] ACPI: Transitioning device [C32A] to D3
[17179575.876000] ACPI: Fan [C32A] (off)
[17179575.876000] ACPI: Transitioning device [C32B] to D3
[17179575.876000] ACPI: Transitioning device [C32B] to D3
[17179575.876000] ACPI: Fan [C32B] (off)
[17179575.876000] ACPI: Transitioning device [C32C] to D3
[17179575.876000] ACPI: Transitioning device [C32C] to D3
[17179575.876000] ACPI: Fan [C32C] (off)
[17179575.876000] ACPI: Transitioning device [C32D] to D3
[17179575.876000] ACPI: Transitioning device [C32D] to D3
[17179575.876000] ACPI: Fan [C32D] (off)
[17179575.880000] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [HP    ] OemTableId [ Cpu0Ist] [20060707]
[17179575.880000] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [HP    ] OemTableId [ Cpu0Cst] [20060707]
[17179575.884000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[17179575.884000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179575.884000] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [HP    ] OemTableId [ Cpu1Ist] [20060707]
[17179575.884000] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [HP    ] OemTableId [ Cpu1Cst] [20060707]
[17179575.884000] ACPI: CPU1 (power states: C1[C1] C2[C2])
[17179575.884000] ACPI: Processor [CPU1] (supports 8 throttling states)
[17179575.928000] ACPI: Thermal Zone [TZ0] (44 C)
[17179575.944000] ACPI: Thermal Zone [TZ1] (46 C)
[17179575.960000] ACPI: Thermal Zone [TZ2] (51 C)
[17179575.972000] ACPI: Thermal Zone [TZ3] (41 C)
[17179575.984000] ACPI: Thermal Zone [TZ4] (33 C)
[17179575.988000] ACPI: Thermal Zone [TZ5] (69 C)
[17179576.296000] SCSI subsystem initialized
[17179576.300000] libata version 1.20 loaded.
[17179576.300000] ata_piix 0000:00:1f.2: version 1.05
[17179576.300000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 21 (level, low) -> IRQ 58
[17179576.300000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179576.300000] ata1: SATA max UDMA/133 cmd 0x1F0 ctl 0x3F6 bmdma 0x5080 irq 14
[17179576.464000] ata1: dev 0 cfg 49:0f00 82:706b 83:7c09 84:6023 85:7069 86:3c09 87:6023 88:203f
[17179576.464000] ata1: dev 0 ATA-7, max UDMA/100, 195371568 sectors: LBA48
[17179576.472000] ata1: dev 0 configured for UDMA/100
[17179576.472000] scsi0 : ata_piix
[17179576.472000]   Vendor: ATA       Model: HTS541010G9SA00   Rev: MBZO
[17179576.472000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179576.472000] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x5088 irq 15
[17179576.796000] ata2: dev 0 cfg 49:0f00 82:421c 83:0000 84:0000 85:0000 86:0000 87:0000 88:0000
[17179576.796000] ata2: dev 0 ATAPI, max MWDMA2
[17179576.796000] ata2(0): applying bridge limits
[17179576.960000] ata2: dev 0 configured for MWDMA2
[17179576.960000] scsi1 : ata_piix
[17179576.964000]   Vendor: HL-DT-ST  Model: DVDRAM GMA-4082N  Rev: HQ04
[17179576.964000]   Type:   CD-ROM                             ANSI SCSI revision: 05
[17179576.972000] SCSI device sda: 195371568 512-byte hdwr sectors (100030 MB)
[17179576.972000] sda: Write Protect is off
[17179576.972000] sda: Mode Sense: 00 3a 00 00
[17179576.972000] SCSI device sda: drive cache: write back
[17179576.972000] SCSI device sda: 195371568 512-byte hdwr sectors (100030 MB)
[17179576.972000] sda: Write Protect is off
[17179576.972000] sda: Mode Sense: 00 3a 00 00
[17179576.972000] SCSI device sda: drive cache: write back
[17179576.972000]  sda: sda1 sda2 < sda5 sda6 >
[17179577.016000] sd 0:0:0:0: Attached scsi disk sda
[17179577.100000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[17179577.104000] Uniform CD-ROM driver Revision: 3.20
[17179577.104000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[17179577.452000] ide0: I/O resource 0x1F0-0x1F7 not free.
[17179577.452000] ide0: ports already in use, skipping probe
[17179577.452000] ide1: I/O resource 0x170-0x177 not free.
[17179577.452000] ide1: ports already in use, skipping probe
[17179577.476000] usbcore: registered new driver usbfs
[17179577.476000] usbcore: registered new driver hub
[17179577.476000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 66
[17179577.476000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179577.476000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179577.476000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[17179577.476000] ehci_hcd 0000:00:1d.7: debug port 1
[17179577.476000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[17179577.476000] ehci_hcd 0000:00:1d.7: irq 66, io mem 0xf4704000
[17179577.480000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179577.484000] usb usb1: configuration #1 chosen from 1 choice
[17179577.484000] hub 1-0:1.0: USB hub found
[17179577.484000] hub 1-0:1.0: 8 ports detected
[17179577.484000] USB Universal Host Controller Interface driver v3.0
[17179577.504000] ieee1394: Initialized config rom entry `ip1394'
[17179577.588000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 66
[17179577.588000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179577.588000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179577.588000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[17179577.588000] uhci_hcd 0000:00:1d.0: irq 66, io base 0x00005000
[17179577.588000] usb usb2: configuration #1 chosen from 1 choice
[17179577.588000] hub 2-0:1.0: USB hub found
[17179577.588000] hub 2-0:1.0: 2 ports detected
[17179577.692000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 22 (level, low) -> IRQ 74
[17179577.692000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179577.692000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179577.692000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[17179577.692000] uhci_hcd 0000:00:1d.1: irq 74, io base 0x00005020
[17179577.692000] usb usb3: configuration #1 chosen from 1 choice
[17179577.692000] hub 3-0:1.0: USB hub found
[17179577.692000] hub 3-0:1.0: 2 ports detected
[17179577.796000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 201
[17179577.796000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179577.796000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179577.796000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[17179577.796000] uhci_hcd 0000:00:1d.2: irq 201, io base 0x00005040
[17179577.800000] usb usb4: configuration #1 chosen from 1 choice
[17179577.800000] hub 4-0:1.0: USB hub found
[17179577.800000] hub 4-0:1.0: 2 ports detected
[17179577.904000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 193
[17179577.904000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17179577.904000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[17179577.904000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[17179577.904000] uhci_hcd 0000:00:1d.3: irq 193, io base 0x00005060
[17179577.904000] usb usb5: configuration #1 chosen from 1 choice
[17179577.904000] hub 5-0:1.0: USB hub found
[17179577.904000] hub 5-0:1.0: 2 ports detected
[17179578.008000] ACPI: PCI Interrupt 0000:02:06.1[B] -> GSI 19 (level, low) -> IRQ 193
[17179578.016000] usb 2-1: new full speed USB device using uhci_hcd and address 2
[17179578.056000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[193]  MMIO=[f4201000-f42017ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[17179578.104000] Attempting manual resume
[17179578.112000] EXT3-fs: INFO: recovery required on readonly filesystem.
[17179578.112000] EXT3-fs: write access will be enabled during recovery.
[17179578.196000] usb 2-1: configuration #1 chosen from 1 choice
[17179581.080000] kjournald starting.  Commit interval 5 seconds
[17179581.080000] EXT3-fs: recovery complete.
[17179581.084000] EXT3-fs: mounted filesystem with ordered data mode.
[17179589.628000] hw_random hardware driver 1.0.0 loaded
[17179589.640000] input: PC Speaker as /class/input/input1
[17179589.752000] parport: PnPBIOS parport detected.
[17179589.752000] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[17179589.908000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179589.920000] Linux agpgart interface v0.101 (c) Dave Jones
[17179589.920000] agpgart: Detected an Intel 945GM Chipset.
[17179589.940000] agpgart: AGP aperture is 256M @ 0x0
[17179590.264000] tpm_inf_pnp 00:03: Found C1F6 with ID IFX0102
[17179590.264000] tpm_inf_pnp 00:03: TPM found: config base 0x560, io base 0x570, chip version 0x000b, vendor id 0x15d1 (Infineon), product id 0x000b (SLB 9635 TT 1.2)
[17179590.300000] ACPI: PCI Interrupt 0000:02:06.2[A] -> GSI 18 (level, low) -> IRQ 201
[17179590.320000] synaptics reset failed
[17179590.320000] synaptics reset failed
[17179590.324000] synaptics reset failed
[17179590.336000] Bluetooth: Core ver 2.8
[17179590.336000] NET: Registered protocol family 31
[17179590.336000] Bluetooth: HCI device and connection manager initialized
[17179590.336000] Bluetooth: HCI socket layer initialized
[17179590.364000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179590.412000] ACPI: PCI Interrupt 0000:02:06.0[A] -> GSI 18 (level, low) -> IRQ 201
[17179590.412000] Yenta: CardBus bridge found at 0000:02:06.0 [103c:309f]
[17179590.412000] Yenta: Enabling burst memory read transactions
[17179590.412000] Yenta: Using INTVAL to route CSC interrupts to PCI
[17179590.412000] Yenta: Routing CardBus interrupts to PCI
[17179590.412000] Yenta TI: socket 0000:02:06.0, mfunc 0x01aa1b22, devctl 0x64
[17179590.420000] sdhci: Secure Digital Host Controller Interface driver, 0.12
[17179590.420000] sdhci: Copyright(c) Pierre Ossman
[17179590.444000] Bluetooth: HCI USB driver ver 2.9
[17179590.444000] usbcore: registered new driver hci_usb
[17179590.460000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179590.460000] sr 1:0:0:0: Attached scsi generic sg1 type 5
[17179590.492000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x25a0b1, caps: 0xa04793/0x300000
[17179590.492000] serio: Synaptics pass-through port at isa0060/serio4/input0
[17179590.528000] ieee80211_crypt: registered algorithm 'NULL'
[17179590.532000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[17179590.532000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17179590.536000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[17179590.564000] ts: Compaq touchscreen protocol output
[17179590.644000] Yenta: ISA IRQ mask 0x0c78, PCI irq 201
[17179590.644000] Socket status: 30000006
[17179590.644000] Yenta: Raising subordinate bus# of parent bus (#02) from #03 to #06
[17179590.644000] pcmcia: parent PCI bridge I/O window: 0x6000 - 0x6fff
[17179590.644000] cs: IO port probe 0x6000-0x6fff: clean.
[17179590.644000] pcmcia: parent PCI bridge Memory window: 0xf4200000 - 0xf45fffff
[17179590.644000] pcmcia: parent PCI bridge Memory window: 0x88000000 - 0x89ffffff
[17179590.644000] sdhci: SDHCI controller found at 0000:02:06.3 [104c:803c] (rev 0)
[17179590.644000] ACPI: PCI Interrupt 0000:02:06.3[C] -> GSI 22 (level, low) -> IRQ 74
[17179590.644000] mmc0: SDHCI at 0xf4209000 irq 74 PIO
[17179590.644000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 177
[17179590.644000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[17179590.716000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.1.0mp
[17179590.716000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[17179591.044000] cs: IO port probe 0x100-0x3af: excluding 0x370-0x37f
[17179591.044000] cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3f7
[17179591.044000] cs: IO port probe 0x820-0x8ff: clean.
[17179591.044000] cs: IO port probe 0xc00-0xcf7: clean.
[17179591.048000] cs: IO port probe 0xa00-0xaff: clean.
[17179591.212000] tg3.c:v3.59.1 (August 25, 2006)
[17179591.212000] ACPI: PCI Interrupt 0000:08:00.0[A] -> GSI 16 (level, low) -> IRQ 177
[17179591.212000] PCI: Setting latency timer of device 0000:08:00.0 to 64
[17179591.248000] eth0: Tigon3 [partno(BCM95751M) rev 4201 PHY(5750)] (PCI Express) 10/100/1000BaseT Ethernet 00:16:d4:a0:5b:a1
[17179573.948000] Brought up 2 CPUs
[17179574.100000] migration_cost=4000
[17179574.100000] HP Compaq Laptop series board detected. Selecting BIOS-method for reboots.
[17179574.100000] NET: Registered protocol family 16
[17179574.100000] EISA bus registered
[17179574.100000] ACPI: bus type pci registered
[17179574.100000] PCI: BIOS Bug: MCFG area at f8000000 is not E820-reserved
[17179574.100000] PCI: Not using MMCONFIG.
[17179574.100000] PCI: PCI BIOS revision 2.10 entry at 0xf0322, last bus=32
[17179574.100000] PCI: Using configuration type 1
[17179574.100000] Setting up standard PCI resources
[17179574.156000] ACPI: Interpreter enabled
[17179574.156000] ACPI: Using IOAPIC for interrupt routing
[17179574.156000] ACPI: PCI Root Bridge [C003] (0000:00)
[17179574.156000] PCI: Probing PCI hardware (bus 00)
[17179574.156000] ACPI: Assume root bridge [\_SB_.C003] bus is 0
[17179574.164000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.2
[17179574.164000] Boot video device is 0000:01:00.0
[17179574.164000] PCI: Transparent bridge - 0000:00:1e.0
[17179574.164000] PCI: Bus #03 (-#06) is hidden behind transparent bridge #02 (-#03) (try 'pci=assign-busses')
[17179574.164000] Please report the result to linux-kernel to fix this permanently
[17179574.164000] ACPI: PCI Interrupt Routing Table [\_SB_.C003._PRT]
[17179574.196000] ACPI: PCI Interrupt Routing Table [\_SB_.C003.C07F._PRT]
[17179574.196000] ACPI: PCI Interrupt Routing Table [\_SB_.C003.C094._PRT]
[17179574.196000] ACPI: Embedded Controller [C006] (gpe 22) interrupt mode.
[17179574.212000] ACPI: Power Resource [C1F4] (on)
[17179574.212000] ACPI: Power Resource [C20D] (on)
[17179574.212000] ACPI: PCI Interrupt Routing Table [\_SB_.C003.C0FB._PRT]
[17179574.212000] ACPI: PCI Interrupt Routing Table [\_SB_.C003.C10B._PRT]
[17179574.216000] ACPI: PCI Interrupt Routing Table [\_SB_.C003.C111._PRT]
[17179574.216000] ACPI: Power Resource [C215] (on)
[17179574.216000] ACPI: PCI Interrupt Link [C107] (IRQs *10 11)
[17179574.216000] ACPI: PCI Interrupt Link [C108] (IRQs *10 11)
[17179574.216000] ACPI: PCI Interrupt Link [C109] (IRQs 10 *11)
[17179574.216000] ACPI: PCI Interrupt Link [C10A] (IRQs 10 11) *5
[17179574.216000] ACPI: PCI Interrupt Link [C11D] (IRQs *10 11)
[17179574.216000] ACPI: PCI Interrupt Link [C11E] (IRQs 10 11) *0, disabled.
[17179574.220000] ACPI: PCI Interrupt Link [C11F] (IRQs 10 *11)
[17179574.220000] ACPI Exception (pci_link-0182): AE_NOT_FOUND, Evaluating _PRS [20060707]

```

Any idea how to solve this?

---

### Post by mackyman on 2007-03-07
Found the solution... Got it of the [http://www.ubuntuforums.org/showthread.php?p=1541970](http://www.ubuntuforums.org/showthread.php?p=1541970) thread... Thought I had checked through the section of the forums, but aparently not...

---

### Post by bcollignon on 2007-03-08
I have booted into Gnome which, from what I can tell is NOT on TTY7.  Then CTRL+ALT+F1 brings me to TTY1, from which I can't escape without issuing the command sudo reboot.  Any thoughts would be appreciated!

---

### Post by mackyman on 2007-03-09
Try ctrl + alt + f7?

Or start the xserver  with 
startx
and it will send you to the graphical interface.

If the xserver crashes with some error message, try,
sudo dpkg-reconfigure -phigh xserver-xorg

Hope this solves things for you, if not, post again, and descripe your problem a bit better.

---

