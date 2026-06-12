---
title: "1min 20sec boot time"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by Enalia on 2007-02-01
Well, I've been using Ubuntu (first Linux distro) for about 6 months now- since then I've picked up a lot and would dare say I've just about switched completely from windows.

I do have one issue, though.  The RIDICULOUSLY long boot time.  It used to be 1minute 45seconds and i posted about it and it was suggested that i go here:  [HowTo: Speed up Ubuntu boot time]("http://ubuntuforums.org/showthread.php?t=89491")  and I tweaked a bunch of stuff and got it down to 1minute and 20 seconds.

This is starting the my timer from hitting enter at GRUB, not from from when i hit the power button and it really really bugs me.  I checked the forums for a past solution and saw someone get help by posting their /var/logs/message thing. so I'll do the same and hope to get some help.

I also noticed that I don't get a loading bar when i hit enter at GRUB instead i get a wierd string of text... something like:

[Linux bzImage setup= 1x1c00 sm=0x17e838]
initrd /boot initrd.im-2.6.17-10-86
Linux-initrd@01xf91d000, 0x6d2f79 bytes
savedefault
boot

related? unrelated? who knows please help.

```


Feb  1 16:19:30 localhost syslogd 1.4.1#18ubuntu6: restart.
Feb  1 16:19:32 localhost kernel: Inspecting /boot/System.map-2.6.17-10-386
Feb  1 16:19:32 localhost kernel: Loaded 22426 symbols from /boot/System.map-2.6.17-10-386.
Feb  1 16:19:32 localhost kernel: Symbols match kernel version 2.6.17.
Feb  1 16:19:32 localhost kernel: No module symbols loaded - kernel modules not enabled. 
Feb  1 16:19:32 localhost kernel: [17179569.184000] Linux version 2.6.17-10-386 (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 Tue Dec 5 22:26:18 UTC 2006 (Ubuntu 2.6.17-10.34-386)
Feb  1 16:19:32 localhost kernel: [17179569.184000] BIOS-provided physical RAM map:
Feb  1 16:19:32 localhost kernel: [17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Feb  1 16:19:32 localhost kernel: [17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Feb  1 16:19:32 localhost kernel: [17179569.184000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
Feb  1 16:19:32 localhost kernel: [17179569.184000]  BIOS-e820: 0000000000100000 - 000000003fe90000 (usable)
Feb  1 16:19:32 localhost kernel: [17179569.184000]  BIOS-e820: 000000003fe90000 - 000000003fe9b000 (ACPI data)
Feb  1 16:19:32 localhost kernel: [17179569.184000]  BIOS-e820: 000000003fe9b000 - 000000003ff00000 (ACPI NVS)
Feb  1 16:19:32 localhost kernel: [17179569.184000]  BIOS-e820: 000000003ff00000 - 0000000040000000 (reserved)
Feb  1 16:19:32 localhost kernel: [17179569.184000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Feb  1 16:19:32 localhost kernel: [17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Feb  1 16:19:32 localhost kernel: [17179569.184000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
Feb  1 16:19:32 localhost kernel: [17179569.184000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
Feb  1 16:19:32 localhost kernel: [17179569.184000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
Feb  1 16:19:32 localhost kernel: [17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Feb  1 16:19:32 localhost kernel: [17179569.184000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
Feb  1 16:19:32 localhost kernel: [17179569.184000] 126MB HIGHMEM available.
Feb  1 16:19:32 localhost kernel: [17179569.184000] 896MB LOWMEM available.
Feb  1 16:19:32 localhost kernel: [17179569.184000] found SMP MP-table at 000f7960
Feb  1 16:19:32 localhost kernel: [17179569.184000] DMI present.
Feb  1 16:19:32 localhost kernel: [17179569.184000] ACPI: PM-Timer IO Port: 0x1008
Feb  1 16:19:32 localhost kernel: [17179569.184000] ACPI: 2 duplicate APIC table ignored.
Feb  1 16:19:32 localhost kernel: [17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Feb  1 16:19:32 localhost kernel: [17179569.184000] Processor #0 6:14 APIC version 20
Feb  1 16:19:32 localhost kernel: [17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Feb  1 16:19:32 localhost kernel: [17179569.184000] Processor #1 6:14 APIC version 20
Feb  1 16:19:32 localhost kernel: [17179569.184000] WARNING: NR_CPUS limit of 1 reached.  Processor ignored.
Feb  1 16:19:32 localhost kernel: [17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Feb  1 16:19:32 localhost kernel: [17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Feb  1 16:19:32 localhost kernel: [17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Feb  1 16:19:32 localhost kernel: [17179569.184000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Feb  1 16:19:32 localhost kernel: [17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Feb  1 16:19:32 localhost kernel: [17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Feb  1 16:19:32 localhost kernel: [17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Feb  1 16:19:32 localhost kernel: [17179569.184000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Feb  1 16:19:32 localhost kernel: [17179569.184000] Using ACPI (MADT) for SMP configuration information
Feb  1 16:19:32 localhost kernel: [17179569.184000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
Feb  1 16:19:32 localhost kernel: [17179569.184000] Built 1 zonelists
Feb  1 16:19:32 localhost kernel: [17179569.184000] Kernel command line: root=UUID=1349abda-d102-4cce-8183-46b8c617bcd4 ro quiet splash
Feb  1 16:19:32 localhost kernel: [17179569.184000] Enabling fast FPU save and restore... done.
Feb  1 16:19:32 localhost kernel: [17179569.184000] Enabling unmasked SIMD FPU exception support... done.
Feb  1 16:19:32 localhost kernel: [17179569.184000] Initializing CPU#0
Feb  1 16:19:32 localhost kernel: [17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Feb  1 16:19:32 localhost kernel: [17179569.184000] Console: colour VGA+ 80x25
Feb  1 16:19:32 localhost kernel: [17179569.184000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Feb  1 16:19:32 localhost kernel: [17179569.184000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Feb  1 16:19:32 localhost kernel: [17179569.184000] Memory: 1026744k/1047104k available (1829k kernel code, 19548k reserved, 1038k data, 288k init, 129600k highmem)
Feb  1 16:19:32 localhost kernel: [17179569.184000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Feb  1 16:19:32 localhost kernel: [17179569.184000] hpet0: at MMIO 0xfed00000 (virtual 0xf8800000), IRQs 2, 8, 0
Feb  1 16:19:32 localhost kernel: [17179569.184000] hpet0: 3 64-bit timers, 14318180 Hz
Feb  1 16:19:32 localhost kernel: [17179569.184000] Using HPET for base-timer
Feb  1 16:19:32 localhost kernel: [17179569.184000] Using HPET for gettimeofday
Feb  1 16:19:32 localhost kernel: [17179569.184000] Detected 1662.525 MHz processor.
Feb  1 16:19:32 localhost kernel: [17179569.184000] Using hpet for high-res timesource
Feb  1 16:19:32 localhost kernel: [17179569.268000] Calibrating delay using timer specific routine.. 3328.86 BogoMIPS (lpj=6657739)
Feb  1 16:19:32 localhost kernel: [17179569.268000] Security Framework v1.0.0 initialized
Feb  1 16:19:32 localhost kernel: [17179569.268000] SELinux:  Disabled at boot.
Feb  1 16:19:32 localhost kernel: [17179569.268000] Mount-cache hash table entries: 512
Feb  1 16:19:32 localhost kernel: [17179569.268000] monitor/mwait feature present.
Feb  1 16:19:32 localhost kernel: [17179569.268000] using mwait in idle threads.
Feb  1 16:19:32 localhost kernel: [17179569.268000] CPU: L1 I cache: 32K, L1 D cache: 32K
Feb  1 16:19:32 localhost kernel: [17179569.268000] CPU: L2 cache: 2048K
Feb  1 16:19:32 localhost kernel: [17179569.268000] CPU: Intel Genuine Intel(R) CPU           T2300  @ 1.66GHz stepping 08
Feb  1 16:19:32 localhost kernel: [17179569.268000] Checking 'hlt' instruction... OK.
Feb  1 16:19:32 localhost kernel: [17179569.284000] SMP alternatives: switching to UP code
Feb  1 16:19:32 localhost kernel: [17179569.284000] Freeing SMP alternatives: 0k freed
Feb  1 16:19:32 localhost kernel: [17179569.284000] checking if image is initramfs... it is
Feb  1 16:19:32 localhost kernel: [17179569.960000] Freeing initrd memory: 6987k freed
Feb  1 16:19:32 localhost kernel: [17179569.960000] ACPI: Core revision 20060707
Feb  1 16:19:32 localhost kernel: [17179569.996000] ACPI: Looking for DSDT ... not found!
Feb  1 16:19:32 localhost kernel: [17179570.000000] ENABLING IO-APIC IRQs
Feb  1 16:19:32 localhost kernel: [17179570.000000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Feb  1 16:19:32 localhost kernel: [17179570.148000] NET: Registered protocol family 16
Feb  1 16:19:32 localhost kernel: [17179570.148000] EISA bus registered
Feb  1 16:19:32 localhost kernel: [17179570.148000] ACPI: bus type pci registered
Feb  1 16:19:32 localhost kernel: [17179570.148000] PCI: Using MMCONFIG
Feb  1 16:19:32 localhost kernel: [17179570.148000] Setting up standard PCI resources
Feb  1 16:19:32 localhost kernel: [17179570.152000] ACPI: Interpreter enabled
Feb  1 16:19:32 localhost kernel: [17179570.152000] ACPI: Using IOAPIC for interrupt routing
Feb  1 16:19:32 localhost kernel: [17179570.152000] ACPI: PCI Root Bridge [PCI0] (0000:00)
Feb  1 16:19:32 localhost kernel: [17179570.156000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
Feb  1 16:19:32 localhost kernel: [17179570.156000] PCI: Transparent bridge - 0000:00:1e.0
Feb  1 16:19:32 localhost kernel: [17179570.160000] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
Feb  1 16:19:32 localhost kernel: [17179570.164000] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
Feb  1 16:19:32 localhost kernel: [17179570.164000] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 *3 4 5 6 7 10 12 14 15)
Feb  1 16:19:32 localhost kernel: [17179570.164000] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
Feb  1 16:19:32 localhost kernel: [17179570.164000] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
Feb  1 16:19:32 localhost kernel: [17179570.164000] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
Feb  1 16:19:32 localhost kernel: [17179570.164000] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 *7 10 12 14 15)
Feb  1 16:19:32 localhost kernel: [17179570.164000] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 *5 6 7 11 12 14 15)
Feb  1 16:19:32 localhost kernel: [17179570.164000] ACPI: Embedded Controller [EC0] (gpe 25) interrupt mode.
Feb  1 16:19:32 localhost kernel: [17179588.164000] Linux Plug and Play Support v0.97 (c) Adam Belay
Feb  1 16:19:32 localhost kernel: [17179588.164000] pnp: PnP ACPI init
Feb  1 16:19:32 localhost kernel: [17179588.164000] pnp: PnP ACPI: found 11 devices
Feb  1 16:19:32 localhost kernel: [17179588.164000] PnPBIOS: Disabled by ACPI PNP
Feb  1 16:19:32 localhost kernel: [17179588.164000] PCI: Using ACPI for IRQ routing
Feb  1 16:19:32 localhost kernel: [17179588.164000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Feb  1 16:19:32 localhost kernel: [17179588.164000] pnp: 00:07: ioport range 0x6a0-0x6af has been reserved
Feb  1 16:19:32 localhost kernel: [17179588.164000] pnp: 00:07: ioport range 0x6b0-0x6ff has been reserved
Feb  1 16:19:32 localhost kernel: [17179588.164000] PCI: Bridge: 0000:00:01.0
Feb  1 16:19:32 localhost kernel: [17179588.164000]   IO window: 2000-2fff
Feb  1 16:19:32 localhost kernel: [17179588.164000]   MEM window: b0100000-b01fffff
Feb  1 16:19:32 localhost kernel: [17179588.164000]   PREFETCH window: c0000000-cfffffff
Feb  1 16:19:32 localhost kernel: [17179588.164000] PCI: Bridge: 0000:00:1c.0
Feb  1 16:19:32 localhost kernel: [17179588.164000]   IO window: disabled.
Feb  1 16:19:32 localhost kernel: [17179588.164000]   MEM window: fac00000-febfffff
Feb  1 16:19:32 localhost kernel: [17179588.164000]   PREFETCH window: disabled.
Feb  1 16:19:32 localhost kernel: [17179588.164000] PCI: Bridge: 0000:00:1c.2
Feb  1 16:19:32 localhost kernel: [17179588.164000]   IO window: disabled.
Feb  1 16:19:32 localhost kernel: [17179588.164000]   MEM window: b0200000-b02fffff
Feb  1 16:19:32 localhost kernel: [17179588.164000]   PREFETCH window: disabled.
Feb  1 16:19:32 localhost kernel: [17179588.164000] PCI: Bridge: 0000:00:1e.0
Feb  1 16:19:32 localhost kernel: [17179588.164000]   IO window: 3000-3fff
Feb  1 16:19:32 localhost kernel: [17179588.164000]   MEM window: b0300000-b03fffff
Feb  1 16:19:32 localhost kernel: [17179588.164000]   PREFETCH window: 50000000-500fffff
Feb  1 16:19:32 localhost kernel: [17179588.164000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
Feb  1 16:19:32 localhost kernel: [17179588.164000] PCI: Enabling device 0000:00:1c.0 (0000 -> 0002)
Feb  1 16:19:32 localhost kernel: [17179588.164000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 177
Feb  1 16:19:32 localhost kernel: [17179588.164000] PCI: Enabling device 0000:00:1c.2 (0000 -> 0002)
Feb  1 16:19:32 localhost kernel: [17179588.164000] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 185
Feb  1 16:19:32 localhost kernel: [17179588.164000] NET: Registered protocol family 2
Feb  1 16:19:32 localhost kernel: [17179588.200000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Feb  1 16:19:32 localhost kernel: [17179588.200000] TCP established hash table entries: 131072 (order: 7, 524288 bytes)
Feb  1 16:19:32 localhost kernel: [17179588.200000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
Feb  1 16:19:32 localhost kernel: [17179588.200000] TCP: Hash tables configured (established 131072 bind 65536)
Feb  1 16:19:32 localhost kernel: [17179588.200000] TCP reno registered
Feb  1 16:19:32 localhost kernel: [17179588.200000] Simple Boot Flag at 0x36 set to 0x1
Feb  1 16:19:32 localhost kernel: [17179588.200000] audit: initializing netlink socket (disabled)
Feb  1 16:19:32 localhost kernel: [17179588.200000] audit(1170346681.201:1): initialized
Feb  1 16:19:32 localhost kernel: [17179588.200000] highmem bounce pool size: 64 pages
Feb  1 16:19:32 localhost kernel: [17179588.200000] VFS: Disk quotas dquot_6.5.1
Feb  1 16:19:32 localhost kernel: [17179588.200000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Feb  1 16:19:32 localhost kernel: [17179588.200000] Initializing Cryptographic API
Feb  1 16:19:32 localhost kernel: [17179588.200000] io scheduler noop registered
Feb  1 16:19:32 localhost kernel: [17179588.200000] io scheduler anticipatory registered
Feb  1 16:19:32 localhost kernel: [17179588.200000] io scheduler deadline registered
Feb  1 16:19:32 localhost kernel: [17179588.200000] io scheduler cfq registered (default)
Feb  1 16:19:32 localhost kernel: [17179588.200000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
Feb  1 16:19:32 localhost kernel: [17179588.200000] assign_interrupt_mode Found MSI capability
Feb  1 16:19:32 localhost kernel: [17179588.200000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 177
Feb  1 16:19:32 localhost kernel: [17179588.200000] assign_interrupt_mode Found MSI capability
Feb  1 16:19:32 localhost kernel: [17179588.200000] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 185
Feb  1 16:19:32 localhost kernel: [17179588.200000] assign_interrupt_mode Found MSI capability
Feb  1 16:19:32 localhost kernel: [17179588.200000] isapnp: Scanning for PnP cards...
Feb  1 16:19:32 localhost kernel: [17179588.556000] isapnp: No Plug & Play device found
Feb  1 16:19:32 localhost kernel: [17179588.576000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Feb  1 16:19:32 localhost kernel: [17179588.576000] mice: PS/2 mouse device common for all mice
Feb  1 16:19:32 localhost kernel: [17179588.576000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Feb  1 16:19:32 localhost kernel: [17179588.576000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Feb  1 16:19:32 localhost kernel: [17179588.576000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Feb  1 16:19:32 localhost kernel: [17179588.576000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Feb  1 16:19:32 localhost kernel: [17179588.584000] i8042.c: Detected active multiplexing controller, rev 1.1.
Feb  1 16:19:32 localhost kernel: [17179588.588000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Feb  1 16:19:32 localhost kernel: [17179588.588000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Feb  1 16:19:32 localhost kernel: [17179588.588000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Feb  1 16:19:32 localhost kernel: [17179588.588000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Feb  1 16:19:32 localhost kernel: [17179588.588000] serio: i8042 KBD port at 0x60,0x64 irq 1
Feb  1 16:19:32 localhost kernel: [17179588.592000] EISA: Probing bus 0 at eisa.0
Feb  1 16:19:32 localhost kernel: [17179588.592000] Cannot allocate resource for EISA slot 1
Feb  1 16:19:32 localhost kernel: [17179588.592000] Cannot allocate resource for EISA slot 2
Feb  1 16:19:32 localhost kernel: [17179588.592000] Cannot allocate resource for EISA slot 3
Feb  1 16:19:32 localhost kernel: [17179588.592000] EISA: Detected 0 cards.
Feb  1 16:19:32 localhost kernel: [17179588.592000] TCP bic registered
Feb  1 16:19:32 localhost kernel: [17179588.592000] NET: Registered protocol family 1
Feb  1 16:19:32 localhost kernel: [17179588.592000] NET: Registered protocol family 8
Feb  1 16:19:32 localhost kernel: [17179588.592000] NET: Registered protocol family 20
Feb  1 16:19:32 localhost kernel: [17179588.592000] Using IPI Shortcut mode
Feb  1 16:19:32 localhost kernel: [17179588.592000] ACPI: (supports S0 S3 S4 S5)
Feb  1 16:19:32 localhost kernel: [17179588.592000] Freeing unused kernel memory: 288k freed
Feb  1 16:19:32 localhost kernel: [17179588.772000] input: AT Translated Set 2 keyboard as /class/input/input0
Feb  1 16:19:32 localhost kernel: [17179589.720000] Capability LSM initialized
Feb  1 16:19:32 localhost kernel: [17179590.048000] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Ist] [20060707]
Feb  1 16:19:32 localhost kernel: [17179590.048000] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Cst] [20060707]
Feb  1 16:19:32 localhost kernel: [17179590.048000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Feb  1 16:19:32 localhost kernel: [17179590.048000] ACPI: Processor [CPU0] (supports 8 throttling states)
Feb  1 16:19:32 localhost kernel: [17179590.448000] ACPI: Thermal Zone [THRM] (61 C)
Feb  1 16:19:32 localhost kernel: [17179590.840000] ICH7: IDE controller at PCI slot 0000:00:1f.1
Feb  1 16:19:32 localhost kernel: [17179590.840000] ACPI: PCI Interrupt 0000:00:1f.1[B] -> GSI 19 (level, low) -> IRQ 225
Feb  1 16:19:32 localhost kernel: [17179590.840000] ICH7: chipset revision 2
Feb  1 16:19:32 localhost kernel: [17179590.840000] ICH7: not 100%% native mode: will probe irqs later
Feb  1 16:19:32 localhost kernel: [17179590.840000]     ide0: BM-DMA at 0x1880-0x1887, BIOS settings: hda:DMA, hdb:pio
Feb  1 16:19:32 localhost kernel: [17179591.576000] hda: Slimtype COMBO SOSC-2483K, ATAPI CD/DVD-ROM drive
Feb  1 16:19:32 localhost kernel: [17179592.248000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Feb  1 16:19:32 localhost kernel: [17179592.252000] hda: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
Feb  1 16:19:32 localhost kernel: [17179592.252000] Uniform CD-ROM driver Revision: 3.20
Feb  1 16:19:32 localhost kernel: [17179592.312000] SCSI subsystem initialized
Feb  1 16:19:32 localhost kernel: [17179592.316000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 225
Feb  1 16:19:32 localhost kernel: [17179592.316000] ata1: SATA max UDMA/133 cmd 0x18C8 ctl 0x18AE bmdma 0x18B0 irq 225
Feb  1 16:19:32 localhost kernel: [17179592.316000] ata2: SATA max UDMA/133 cmd 0x18C0 ctl 0x18AA bmdma 0x18B8 irq 225
Feb  1 16:19:32 localhost kernel: [17179592.484000] ata1: dev 0 ATA-7, max UDMA/100, 117210240 sectors: LBA48
Feb  1 16:19:32 localhost kernel: [17179592.492000] ata1: dev 0 configured for UDMA/100
Feb  1 16:19:32 localhost kernel: [17179592.492000] scsi0 : ata_piix
Feb  1 16:19:32 localhost kernel: [17179592.660000] scsi1 : ata_piix
Feb  1 16:19:32 localhost kernel: [17179592.664000]   Vendor: ATA       Model: FUJITSU MHV2060B  Rev: 0000
Feb  1 16:19:32 localhost kernel: [17179592.664000]   Type:   Direct-Access                      ANSI SCSI revision: 05
Feb  1 16:19:32 localhost kernel: [17179592.672000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
Feb  1 16:19:32 localhost kernel: [17179592.672000] sda: Write Protect is off
Feb  1 16:19:32 localhost kernel: [17179592.676000] SCSI device sda: drive cache: write back
Feb  1 16:19:32 localhost kernel: [17179592.680000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
Feb  1 16:19:32 localhost kernel: [17179592.684000] sda: Write Protect is off
Feb  1 16:19:32 localhost kernel: [17179592.688000] SCSI device sda: drive cache: write back
Feb  1 16:19:32 localhost kernel: [17179592.688000]  sda: sda1 sda2 sda3
Feb  1 16:19:32 localhost kernel: [17179593.080000] sd 0:0:0:0: Attached scsi disk sda
Feb  1 16:19:32 localhost kernel: [17179593.444000] usbcore: registered new driver usbfs
Feb  1 16:19:32 localhost kernel: [17179593.444000] usbcore: registered new driver hub
Feb  1 16:19:32 localhost kernel: [17179593.444000] USB Universal Host Controller Interface driver v3.0
Feb  1 16:19:32 localhost kernel: [17179593.448000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 233
Feb  1 16:19:32 localhost kernel: [17179593.448000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Feb  1 16:19:32 localhost kernel: [17179593.448000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Feb  1 16:19:32 localhost kernel: [17179593.448000] uhci_hcd 0000:00:1d.0: irq 233, io base 0x00001800
Feb  1 16:19:32 localhost kernel: [17179593.448000] usb usb1: configuration #1 chosen from 1 choice
Feb  1 16:19:32 localhost kernel: [17179593.448000] hub 1-0:1.0: USB hub found
Feb  1 16:19:32 localhost kernel: [17179593.448000] hub 1-0:1.0: 2 ports detected
Feb  1 16:19:32 localhost kernel: [17179593.552000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 225
Feb  1 16:19:32 localhost kernel: [17179593.552000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Feb  1 16:19:32 localhost kernel: [17179593.552000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Feb  1 16:19:32 localhost kernel: [17179593.552000] uhci_hcd 0000:00:1d.1: irq 225, io base 0x00001820
Feb  1 16:19:32 localhost kernel: [17179593.552000] usb usb2: configuration #1 chosen from 1 choice
Feb  1 16:19:32 localhost kernel: [17179593.552000] hub 2-0:1.0: USB hub found
Feb  1 16:19:32 localhost kernel: [17179593.552000] hub 2-0:1.0: 2 ports detected
Feb  1 16:19:32 localhost kernel: [17179593.656000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 185
Feb  1 16:19:32 localhost kernel: [17179593.656000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Feb  1 16:19:32 localhost kernel: [17179593.656000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Feb  1 16:19:32 localhost kernel: [17179593.656000] uhci_hcd 0000:00:1d.2: irq 185, io base 0x00001840
Feb  1 16:19:32 localhost kernel: [17179593.656000] usb usb3: configuration #1 chosen from 1 choice
Feb  1 16:19:32 localhost kernel: [17179593.656000] hub 3-0:1.0: USB hub found
Feb  1 16:19:32 localhost kernel: [17179593.656000] hub 3-0:1.0: 2 ports detected
Feb  1 16:19:32 localhost kernel: [17179593.760000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 169
Feb  1 16:19:32 localhost kernel: [17179593.760000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Feb  1 16:19:32 localhost kernel: [17179593.760000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
Feb  1 16:19:32 localhost kernel: [17179593.760000] uhci_hcd 0000:00:1d.3: irq 169, io base 0x00001860
Feb  1 16:19:32 localhost kernel: [17179593.760000] usb usb4: configuration #1 chosen from 1 choice
Feb  1 16:19:32 localhost kernel: [17179593.760000] hub 4-0:1.0: USB hub found
Feb  1 16:19:32 localhost kernel: [17179593.760000] hub 4-0:1.0: 2 ports detected
Feb  1 16:19:32 localhost kernel: [17179593.864000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 233
Feb  1 16:19:32 localhost kernel: [17179593.864000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Feb  1 16:19:32 localhost kernel: [17179593.864000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
Feb  1 16:19:32 localhost kernel: [17179593.864000] ehci_hcd 0000:00:1d.7: debug port 1
Feb  1 16:19:32 localhost kernel: [17179593.864000] ehci_hcd 0000:00:1d.7: irq 233, io mem 0xb0004000
Feb  1 16:19:32 localhost kernel: [17179593.868000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Feb  1 16:19:32 localhost kernel: [17179593.868000] usb usb5: configuration #1 chosen from 1 choice
Feb  1 16:19:32 localhost kernel: [17179593.868000] hub 5-0:1.0: USB hub found
Feb  1 16:19:32 localhost kernel: [17179593.868000] hub 5-0:1.0: 8 ports detected
Feb  1 16:19:32 localhost kernel: [17179593.972000] ACPI: PCI Interrupt 0000:05:04.0[A] -> GSI 18 (level, low) -> IRQ 185
Feb  1 16:19:32 localhost kernel: [17179594.020000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[185]  MMIO=[b0304000-b03047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Feb  1 16:19:32 localhost kernel: [17179597.048000] kjournald starting.  Commit interval 5 seconds
Feb  1 16:19:32 localhost kernel: [17179597.048000] EXT3-fs: mounted filesystem with ordered data mode.
Feb  1 16:19:32 localhost kernel: [17179615.648000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Feb  1 16:19:32 localhost kernel: [17179615.680000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Feb  1 16:19:32 localhost kernel: [17179615.792000] hw_random: RNG not detected
Feb  1 16:19:32 localhost kernel: [17179615.980000] Linux agpgart interface v0.101 (c) Dave Jones
Feb  1 16:19:32 localhost kernel: [17179616.016000] agpgart: Detected an Intel 945GM Chipset.
Feb  1 16:19:32 localhost kernel: [17179616.032000] agpgart: AGP aperture is 256M @ 0x0
Feb  1 16:19:32 localhost kernel: [17179616.268000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 50
Feb  1 16:19:32 localhost kernel: [17179616.400000] ieee80211: 802.11 data/management/control stack, git-1.1.13
Feb  1 16:19:32 localhost kernel: [17179616.400000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Feb  1 16:19:32 localhost kernel: [17179616.564000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.1.0mp
Feb  1 16:19:32 localhost kernel: [17179616.564000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
Feb  1 16:19:32 localhost kernel: [17179616.752000] Real Time Clock Driver v1.12ac
Feb  1 16:19:32 localhost kernel: [17179616.956000] hda_codec: Unknown model for ALC880, trying auto-probe from BIOS...
Feb  1 16:19:32 localhost kernel: [17179617.204000] PCI: Enabling device 0000:04:00.0 (0000 -> 0002)
Feb  1 16:19:32 localhost kernel: [17179617.204000] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 18 (level, low) -> IRQ 185
Feb  1 16:19:32 localhost kernel: [17179617.204000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
Feb  1 16:19:32 localhost kernel: [17179617.864000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xa0b1, caps: 0xa04713/0x20040a
Feb  1 16:19:32 localhost kernel: [17179617.904000] input: SynPS/2 Synaptics TouchPad as /class/input/input1
Feb  1 16:19:32 localhost kernel: [17179617.964000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Feb  1 16:19:32 localhost kernel: [17179618.148000] ts: Compaq touchscreen protocol output
Feb  1 16:19:32 localhost kernel: [17179618.256000] r8169 Gigabit Ethernet driver 2.2LK loaded
Feb  1 16:19:32 localhost kernel: [17179618.256000] ACPI: PCI Interrupt 0000:05:05.0[A] -> GSI 19 (level, low) -> IRQ 225
Feb  1 16:19:32 localhost kernel: [17179618.256000] eth0: RTL8169 at 0xf89ce800, 00:03:0d:43:41:c5, IRQ 225
Feb  1 16:19:32 localhost kernel: [17179619.176000] r8169: eth0: link down
Feb  1 16:19:32 localhost kernel: [17179620.124000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Feb  1 16:19:32 localhost kernel: [17179620.228000] NET: Registered protocol family 17
Feb  1 16:19:32 localhost kernel: [17179622.880000] NET: Registered protocol family 10
Feb  1 16:19:32 localhost kernel: [17179622.880000] lo: Disabled Privacy Extensions
Feb  1 16:19:32 localhost kernel: [17179622.880000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Feb  1 16:19:32 localhost kernel: [17179622.880000] IPv6 over IPv4 tunneling driver
Feb  1 16:19:32 localhost kernel: [17179623.912000] lp: driver loaded but no devices found
Feb  1 16:19:32 localhost kernel: [17179624.108000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
Feb  1 16:19:32 localhost kernel: [17179624.108000] ieee1394: sbp2: Try serialize_io=0 for better performance
Feb  1 16:19:32 localhost kernel: [17179628.076000] EXT3 FS on sda2, internal journal
Feb  1 16:19:32 localhost kernel: [17179629.664000] device-mapper: 4.6.0-ioctl (2006-02-17) initialised: dm-devel@redhat.com
Feb  1 16:19:32 localhost kernel: [17179632.496000] NTFS driver 2.1.27 [Flags: R/O MODULE].
Feb  1 16:19:32 localhost kernel: [17179632.560000] NTFS volume version 3.1.
Feb  1 16:19:32 localhost kernel: [17179646.000000] ACPI: AC Adapter [AC0] (on-line)
Feb  1 16:19:32 localhost kernel: [17179649.432000] ACPI: Battery Slot [BAT0] (battery present)
Feb  1 16:19:32 localhost kernel: [17179649.444000] ACPI: Power Button (FF) [PWRF]
Feb  1 16:19:32 localhost kernel: [17179649.444000] ACPI: Lid Switch [LID0]
Feb  1 16:19:32 localhost kernel: [17179649.444000] ACPI: Power Button (CM) [PWRB]
Feb  1 16:19:32 localhost kernel: [17179649.444000] ACPI: Sleep Button (CM) [SLPB]
Feb  1 16:19:32 localhost kernel: [17179650.736000] pcc_acpi: loading...
Feb  1 16:19:32 localhost kernel: [17179651.504000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Feb  1 16:19:32 localhost kernel: [17179651.504000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Feb  1 16:19:44 localhost kernel: [17179669.624000] apm: BIOS not found.
Feb  1 16:19:46 localhost kernel: [17179671.856000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Feb  1 16:19:46 localhost kernel: [17179671.860000] [fglrx] Maximum main memory to use for locked dma buffers: 928 MBytes.
Feb  1 16:19:46 localhost kernel: [17179671.860000] [fglrx] module loaded - fglrx 8.28.8 [Aug 17 2006] on minor 0
Feb  1 16:19:46 localhost kernel: [17179671.884000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 169
Feb  1 16:19:49 localhost kernel: [17179675.056000] mtrr: no more MTRRs available
Feb  1 16:19:49 localhost last message repeated 3 times
Feb  1 16:19:53 localhost kernel: [17179678.368000] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
Feb  1 16:20:07 localhost gconfd (enalios-4849): starting (version 2.16.0), pid 4849 user 'enalios'
Feb  1 16:20:08 localhost gconfd (enalios-4849): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Feb  1 16:20:08 localhost gconfd (enalios-4849): Resolved address "xml:readwrite:/home/enalios/.gconf" to a writable configuration source at position 1
Feb  1 16:20:08 localhost gconfd (enalios-4849): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Feb  1 16:20:08 localhost gconfd (enalios-4849): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Feb  1 16:20:08 localhost gconfd (enalios-4849): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Feb  1 16:20:15 localhost gconfd (enalios-4849): Resolved address "xml:readwrite:/home/enalios/.gconf" to a writable configuration source at position 0


```

gosh i hope that's not too much for you to fish through. thanks for any help.

---

### Post by Brunellus on 2007-02-01
did you disable usplash?  because all you're seeing are init messages. . .

---

### Post by Enalia on 2007-02-01
I don't believe i did....

If I did however where would i re-enable it?

---

### Post by zielak on 2007-03-29
I have the same boot time (1:16) BUT when i use my laptop in a place where there is no wifi network and I'm also not using wired one the boot time drops to 38 secs!! And it is done without any service turned off, just like it is after the installation.

There are couple of things You could do to at least have better diagnostics:

1. Install bootchart

this is stuff for visualizing boot process. 
After every boot it generates a PNG flowchart in /var/log/bootchart attach it to Your post.

2. Post Your specs and distro flavour

I can see that You've got similar hardware to mine, so it gets even more interesting ;)
I'm running Ubuntu 7.04 Beta on a Dell Inspiron E1405 with:
Core Duo T2300E on Intel i945 mainboard, 
1GB 533 Dual Channel RAM 
120 GB Seagate SATA HD
Integrated sound and graphics

I suppose that in my case scanning of the avaliable wifi channels takes so much time, but from Your log it seems to me that it's not the case on Your system... but with bootchart it should be fairly easy to deduce it.

---

