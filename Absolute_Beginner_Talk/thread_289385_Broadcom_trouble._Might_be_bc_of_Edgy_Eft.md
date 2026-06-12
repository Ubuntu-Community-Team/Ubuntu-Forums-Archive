---
title: "Broadcom trouble. Might be b/c of Edgy Eft?"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by kbsuperstar on 2006-10-30
Yeah, so I just installed Edgy Eft, and now I just did this tutorial:

[http://www.ubuntuforums.org/showthread.php?t=193350&highlight=4311](http://www.ubuntuforums.org/showthread.php?t=193350&highlight=4311)

I've done this before when I had Dapper, and it worked fine, but for some reason it's not working. I do it all, and once I use "dmesg" this is what comes up:

```
[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001f680000 (usable)
[17179569.184000]  BIOS-e820: 000000001f680000 - 000000001f700000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000001f700000 - 0000000020000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[17179569.184000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 502MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f65b0
[17179569.184000] On node 0 totalpages: 128640
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 124544 pages, LIFO batch:31
[17179569.184000] DMI present.
[17179569.184000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6580
[17179569.184000] ACPI: RSDT (v001 PTLTD  Capell00 0x06040000  LTP 0x00000000) @ 0x1f68d18a
[17179569.184000] ACPI: FADT (v001 HP     NISSAN   0x06040000 LOHR 0x0000005a) @ 0x1f693dfc
[17179569.184000] ACPI: MADT (v001 HP     NISSAN   0x06040000 LOHR 0x0000005a) @ 0x1f693e70
[17179569.184000] ACPI: HPET (v001 HP     NISSAN   0x06040000 LOHR 0x0000005a) @ 0x1f693ed8
[17179569.184000] ACPI: MCFG (v001 HP     NISSAN   0x06040000 LOHR 0x0000005a) @ 0x1f693f10
[17179569.184000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x1f693fd8
[17179569.184000] ACPI: MADT (v001 PTLTD         APIC   0x06040000  LTP 0x00000000) @ 0x1f693f7e
[17179569.184000] ACPI: SSDT (v001 SataRe SataAhci 0x00001000 INTL 0x20060217) @ 0x1f68d8a4
[17179569.184000] ACPI: SSDT (v001  PmRef  Cpu0Cst 0x00003001 INTL 0x20060217) @ 0x1f68d6c8
[17179569.184000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20060217) @ 0x1f68d1d2
[17179569.184000] ACPI: DSDT (v001 HP     NISSAN   0x06040000 INTL 0x20060217) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: 2 duplicate APIC table ignored.
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:14 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:c0000000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/sda1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[17179569.184000] Console: colour VGA+ 80x25
[17179569.184000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.184000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179569.184000] Memory: 500328k/514560k available (1910k kernel code, 13772k reserved, 1070k data, 308k init, 0k highmem)
[17179569.184000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.184000] hpet0: at MMIO 0xfed00000 (virtual 0xe0000000), IRQs 2, 8, 0
[17179569.184000] hpet0: 3 64-bit timers, 14318180 Hz
[17179569.184000] Using HPET for base-timer
[17179569.184000] Using HPET for gettimeofday
[17179569.184000] Detected 1463.004 MHz processor.
[17179569.184000] Using hpet for high-res timesource
[17179569.268000] Calibrating delay using timer specific routine.. 2929.74 BogoMIPS (lpj=5859498)
[17179569.268000] Security Framework v1.0.0 initialized
[17179569.268000] SELinux:  Disabled at boot.
[17179569.268000] Mount-cache hash table entries: 512
[17179569.268000] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 0000c109 00000000 00000000
[17179569.268000] CPU: After vendor identify, caps: afe9fbff 00100000 00000000 00000000 0000c109 00000000 00000000
[17179569.268000] monitor/mwait feature present.
[17179569.268000] using mwait in idle threads.
[17179569.268000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179569.268000] CPU: L2 cache: 1024K
[17179569.268000] CPU: After all inits, caps: afe9fbff 00100000 00000000 00000140 0000c109 00000000 00000000
[17179569.268000] Checking 'hlt' instruction... OK.
[17179569.284000] SMP alternatives: switching to UP code
[17179569.284000] Freeing SMP alternatives: 16k freed
[17179569.284000] checking if image is initramfs... it is
[17179569.912000] Freeing initrd memory: 5563k freed
[17179569.912000] ACPI: Core revision 20060707
[17179569.912000] ACPI: Looking for DSDT ... not found!
[17179569.944000] CPU0: Intel(R) Celeron(R) M CPU        410  @ 1.46GHz stepping 08
[17179569.944000] Total of 1 processors activated (2929.74 BogoMIPS).
[17179569.944000] ENABLING IO-APIC IRQs
[17179569.944000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179570.096000] Brought up 1 CPUs
[17179570.096000] migration_cost=0
[17179570.096000] NET: Registered protocol family 16
[17179570.096000] EISA bus registered
[17179570.096000] ACPI: bus type pci registered
[17179570.096000] PCI: Using MMCONFIG
[17179570.096000] Setting up standard PCI resources
[17179570.100000] ACPI: Interpreter enabled
[17179570.100000] ACPI: Using IOAPIC for interrupt routing
[17179570.100000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.100000] PCI: Probing PCI hardware (bus 00)
[17179570.120000] Boot video device is 0000:00:02.0
[17179570.120000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179570.120000] PCI: Transparent bridge - 0000:00:1e.0
[17179570.120000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.124000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[17179570.124000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[17179570.124000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[17179570.124000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[17179570.124000] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[17179570.124000] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 *4 5 6 7 11 12 14 15)
[17179570.124000] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 *3 4 5 6 7 10 12 14 15)
[17179570.128000] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[17179570.128000] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 *6 7 10 12 14 15)
[17179570.128000] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[17179570.128000] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[17179570.128000] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[17179570.128000] ACPI: Embedded Controller [EC0] (gpe 25) interrupt mode.
[17179570.180000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.180000] pnp: PnP ACPI init
[17179570.204000] pnp: PnP ACPI: found 10 devices
[17179570.204000] PnPBIOS: Disabled by ACPI PNP
[17179570.204000] PCI: Using ACPI for IRQ routing
[17179570.204000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.204000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[17179570.204000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[17179570.204000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.1
[17179570.204000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1
[17179570.204000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.2
[17179570.204000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.2
[17179570.204000] PCI: Cannot allocate resource region 0 of device 0000:06:00.0
[17179570.204000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[17179570.204000] PCI: Bridge: 0000:00:1c.0
[17179570.204000]   IO window: disabled.
[17179570.204000]   MEM window: disabled.
[17179570.204000]   PREFETCH window: disabled.
[17179570.204000] PCI: Bridge: 0000:00:1c.1
[17179570.204000]   IO window: disabled.
[17179570.204000]   MEM window: disabled.
[17179570.204000]   PREFETCH window: disabled.
[17179570.204000] PCI: Bridge: 0000:00:1c.2
[17179570.204000]   IO window: disabled.
[17179570.204000]   MEM window: 30000000-300fffff
[17179570.204000]   PREFETCH window: disabled.
[17179570.204000] PCI: Bridge: 0000:00:1e.0
[17179570.204000]   IO window: 2000-2fff
[17179570.204000]   MEM window: d0100000-d01fffff
[17179570.204000]   PREFETCH window: disabled.
[17179570.204000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 169
[17179570.204000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179570.204000] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 177
[17179570.204000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[17179570.204000] PCI: Enabling device 0000:00:1c.2 (0100 -> 0102)
[17179570.204000] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 185
[17179570.204000] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[17179570.204000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179570.204000] NET: Registered protocol family 2
[17179570.240000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179570.240000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[17179570.240000] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[17179570.240000] TCP: Hash tables configured (established 16384 bind 8192)
[17179570.240000] TCP reno registered
[17179570.240000] Simple Boot Flag at 0x36 set to 0x1
[17179570.240000] audit: initializing netlink socket (disabled)
[17179570.240000] audit(1162264430.240:1): initialized
[17179570.240000] VFS: Disk quotas dquot_6.5.1
[17179570.240000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.240000] Initializing Cryptographic API
[17179570.240000] io scheduler noop registered
[17179570.240000] io scheduler anticipatory registered
[17179570.240000] io scheduler deadline registered
[17179570.240000] io scheduler cfq registered (default)
[17179578.324000] 0000:00:1d.7 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
[17179578.328000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 169
[17179578.328000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179578.328000] assign_interrupt_mode Found MSI capability
[17179578.328000] Allocate Port Service[0000:00:1c.0:pcie00]
[17179578.328000] Allocate Port Service[0000:00:1c.0:pcie02]
[17179578.328000] Allocate Port Service[0000:00:1c.0:pcie03]
[17179578.328000] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 177
[17179578.328000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[17179578.328000] assign_interrupt_mode Found MSI capability
[17179578.328000] Allocate Port Service[0000:00:1c.1:pcie00]
[17179578.328000] Allocate Port Service[0000:00:1c.1:pcie02]
[17179578.328000] Allocate Port Service[0000:00:1c.1:pcie03]
[17179578.328000] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 185
[17179578.328000] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[17179578.328000] assign_interrupt_mode Found MSI capability
[17179578.328000] Allocate Port Service[0000:00:1c.2:pcie00]
[17179578.328000] Allocate Port Service[0000:00:1c.2:pcie02]
[17179578.328000] Allocate Port Service[0000:00:1c.2:pcie03]
[17179578.328000] isapnp: Scanning for PnP cards...
[17179578.684000] isapnp: No Plug & Play device found
[17179578.708000] Real Time Clock Driver v1.12ac
[17179578.708000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179578.708000] mice: PS/2 mouse device common for all mice
[17179578.708000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179578.708000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179578.708000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179578.708000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179578.724000] i8042.c: Detected active multiplexing controller, rev 1.1.
[17179578.736000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[17179578.740000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[17179578.744000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[17179578.744000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[17179578.748000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179578.752000] EISA: Probing bus 0 at eisa.0
[17179578.752000] Cannot allocate resource for EISA slot 1
[17179578.752000] Cannot allocate resource for EISA slot 2
[17179578.752000] EISA: Detected 0 cards.
[17179578.752000] TCP bic registered
[17179578.752000] NET: Registered protocol family 1
[17179578.752000] NET: Registered protocol family 8
[17179578.752000] NET: Registered protocol family 20
[17179578.752000] Using IPI No-Shortcut mode
[17179578.752000] ACPI: (supports S0 S3 S4 S5)
[17179578.752000] Freeing unused kernel memory: 308k freed
[17179578.828000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179579.908000] Capability LSM initialized
[17179579.940000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[17179579.940000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179579.940000] ACPI Exception (acpi_processor-0693): AE_NOT_FOUND, Processor Device is not present [20060707]
[17179579.940000] ACPI: Getting cpuindex for acpiid 0x1
[17179579.952000] ACPI: Thermal Zone [TZ01] (48 C)
[17179579.952000] ACPI: Thermal Zone [TZ02] (27 C)
[17179580.272000] ICH7: IDE controller at PCI slot 0000:00:1f.1
[17179580.272000] ACPI: PCI Interrupt 0000:00:1f.1[B] -> GSI 19 (level, low) -> IRQ 225
[17179580.272000] ICH7: chipset revision 1
[17179580.272000] ICH7: not 100% native mode: will probe irqs later
[17179580.272000]     ide0: BM-DMA at 0x1810-0x1817, BIOS settings: hda:DMA, hdb:pio
[17179580.272000] Probing IDE interface ide0...
[17179581.008000] hda: PIONEER DVDRW DVR-K16, ATAPI CD/DVD-ROM drive
[17179581.680000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179581.700000] hda: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2000kB Cache, DMA
[17179581.700000] Uniform CD-ROM driver Revision: 3.20
[17179581.804000] SCSI subsystem initialized
[17179581.808000] libata version 1.20 loaded.
[17179581.808000] ahci 0000:00:1f.2: version 1.2
[17179581.808000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 225
[17179587.628000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179587.628000] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0x5 impl SATA mode
[17179587.628000] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[17179587.628000] ata1: SATA max UDMA/133 cmd 0xE0046500 ctl 0x0 bmdma 0x0 irq 233
[17179587.628000] ata2: SATA max UDMA/133 cmd 0xE0046580 ctl 0x0 bmdma 0x0 irq 233
[17179587.628000] ata3: SATA max UDMA/133 cmd 0xE0046600 ctl 0x0 bmdma 0x0 irq 233
[17179587.628000] ata4: SATA max UDMA/133 cmd 0xE0046680 ctl 0x0 bmdma 0x0 irq 233
[17179588.004000] ata1: SATA link up 1.5 Gbps (SStatus 113)
[17179588.004000] ata1: dev 0 cfg 49:2f00 82:3069 83:7c09 84:6003 85:3069 86:3c09 87:6003 88:203f
[17179588.004000] ata1: dev 0 ATA-7, max UDMA/100, 117231408 sectors: LBA48
[17179588.004000] ata1: dev 0 configured for UDMA/100
[17179588.004000] scsi0 : ahci
[17179588.372000] ata2: SATA link down (SStatus 0)
[17179588.372000] scsi1 : ahci
[17179589.292000] ata3: SATA link down (SStatus 0)
[17179589.292000] scsi2 : ahci
[17179589.660000] ata4: SATA link down (SStatus 0)
[17179589.660000] scsi3 : ahci
[17179589.660000]   Vendor: ATA       Model: ST96812AS         Rev: 3.05
[17179589.660000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179589.664000] SCSI device sda: 117231408 512-byte hdwr sectors (60022 MB)
[17179589.664000] sda: Write Protect is off
[17179589.664000] sda: Mode Sense: 00 3a 00 00
[17179589.664000] SCSI device sda: drive cache: write back
[17179589.664000] SCSI device sda: 117231408 512-byte hdwr sectors (60022 MB)
[17179589.664000] sda: Write Protect is off
[17179589.664000] sda: Mode Sense: 00 3a 00 00
[17179589.664000] SCSI device sda: drive cache: write back
[17179589.664000]  sda: sda1 sda2 < sda5 >
[17179589.944000] sd 0:0:0:0: Attached scsi disk sda
[17179590.116000] Probing IDE interface ide1...
[17179590.160000] usbcore: registered new driver usbfs
[17179590.164000] usbcore: registered new driver hub
[17179590.164000] USB Universal Host Controller Interface driver v3.0
[17179590.164000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 50
[17179590.164000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179590.164000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179590.164000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179590.164000] uhci_hcd 0000:00:1d.0: irq 50, io base 0x00001820
[17179590.168000] usb usb1: configuration #1 chosen from 1 choice
[17179590.168000] hub 1-0:1.0: USB hub found
[17179590.168000] hub 1-0:1.0: 2 ports detected
[17179590.272000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 225
[17179590.272000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179590.272000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179590.272000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179590.272000] uhci_hcd 0000:00:1d.1: irq 225, io base 0x00001840
[17179590.272000] usb usb2: configuration #1 chosen from 1 choice
[17179590.272000] hub 2-0:1.0: USB hub found
[17179590.272000] hub 2-0:1.0: 2 ports detected
[17179590.376000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 185
[17179590.376000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179590.376000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179590.376000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179590.376000] uhci_hcd 0000:00:1d.2: irq 185, io base 0x00001860
[17179590.376000] usb usb3: configuration #1 chosen from 1 choice
[17179590.376000] hub 3-0:1.0: USB hub found
[17179590.376000] hub 3-0:1.0: 2 ports detected
[17179590.480000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 177
[17179590.480000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17179590.480000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[17179590.480000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[17179590.480000] uhci_hcd 0000:00:1d.3: irq 177, io base 0x00001880
[17179590.480000] usb usb4: configuration #1 chosen from 1 choice
[17179590.480000] hub 4-0:1.0: USB hub found
[17179590.480000] hub 4-0:1.0: 2 ports detected
[17179590.584000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 50
[17179590.584000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179590.584000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179590.584000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[17179590.584000] ehci_hcd 0000:00:1d.7: debug port 1
[17179590.584000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[17179590.584000] ehci_hcd 0000:00:1d.7: irq 50, io mem 0xd0544000
[17179590.588000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179590.588000] usb usb5: configuration #1 chosen from 1 choice
[17179590.588000] hub 5-0:1.0: USB hub found
[17179590.588000] hub 5-0:1.0: 8 ports detected
[17179590.744000] Attempting manual resume
[17179590.776000] kjournald starting.  Commit interval 5 seconds
[17179590.776000] EXT3-fs: mounted filesystem with ordered data mode.
[17179600.676000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179600.680000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179600.696000] hw_random hardware driver 1.0.0 loaded
[17179601.220000] Linux agpgart interface v0.101 (c) Dave Jones
[17179601.336000] agpgart: Detected an Intel 945GM Chipset.
[17179601.336000] agpgart: Detected 7932K stolen memory.
[17179601.356000] agpgart: AGP aperture is 256M @ 0xc0000000
[17179601.364000] ieee80211_crypt: registered algorithm 'NULL'
[17179601.364000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[17179601.364000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17179601.444000] bcm43xx driver
[17179601.444000] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 18 (level, low) -> IRQ 185
[17179601.444000] PCI: Setting latency timer of device 0000:06:00.0 to 64
[17179601.708000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000
[17179601.780000] input: SynPS/2 Synaptics TouchPad as /class/input/input1
[17179601.872000] e100: Intel(R) PRO/100 Network Driver, 3.5.10-k2-NAPI
[17179601.872000] e100: Copyright(c) 1999-2005 Intel Corporation
[17179601.872000] ACPI: PCI Interrupt 0000:08:08.0[A] -> GSI 20 (level, low) -> IRQ 58
[17179601.904000] e100: eth1: e100_probe: addr 0xd0100000, irq 58, MAC addr 00:16:D4:0B:8D:3A
[17179602.064000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179602.076000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 66
[17179602.076000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[17179602.268000] ts: Compaq touchscreen protocol output
[17179602.580000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[17179602.596000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[17179603.000000] lp: driver loaded but no devices found
[17179603.020000] Adding 1477940k swap on /dev/disk/by-uuid/1fc9575f-9eb1-4c0d-a9b1-7bbdacba998e.  Priority:-1 extents:1 across:1477940k
[17179603.080000] EXT3 FS on sda1, internal journal
[17179603.632000] NET: Registered protocol family 17
[17179605.772000] ndiswrapper version 1.17 loaded (preempt=no,smp=yes)
[17179607.844000] ACPI: AC Adapter [ACAD] (on-line)
[17179607.920000] ACPI: Battery Slot [BAT1] (battery present)
[17179607.936000] ACPI: Power Button (FF) [PWRF]
[17179607.936000] ACPI Error (evxfevnt-0189): Could not enable SleepButton event [20060707]
[17179607.936000] ACPI Warning (evxface-0146): Could not enable fixed event 3 [20060707]
[17179607.936000] ACPI: Lid Switch [LID]
[17179607.936000] ACPI: Power Button (CM) [PWRB]
[17179608.116000] ibm_acpi: ec object not found
[17179608.144000] pcc_acpi: loading...
[17179608.272000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[17179608.272000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[17179610.796000] [drm] Initialized drm 1.0.1 20051102
[17179610.800000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 177
[17179610.800000] [drm] Initialized i915 1.5.0 20060119 on minor 0
[17179611.548000] apm: BIOS not found.
[17179615.236000] Bluetooth: Core ver 2.8
[17179615.236000] NET: Registered protocol family 31
[17179615.236000] Bluetooth: HCI device and connection manager initialized
[17179615.236000] Bluetooth: HCI socket layer initialized
[17179615.252000] Bluetooth: L2CAP ver 2.8
[17179615.252000] Bluetooth: L2CAP socket layer initialized
[17179615.256000] Bluetooth: RFCOMM socket layer initialized
[17179615.256000] Bluetooth: RFCOMM TTY layer initialized
[17179615.256000] Bluetooth: RFCOMM ver 1.7
[17179637.704000] NET: Registered protocol family 10
[17179637.704000] lo: Disabled Privacy Extensions
[17179637.704000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179637.704000] IPv6 over IPv4 tunneling driver
[17179796.332000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[17179796.348000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[17179914.868000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179914.872000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[17179914.872000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[17179925.384000] eth0: no IPv6 routers present
[17180351.244000] ndiswrapper version 1.17 loaded (preempt=no,smp=yes)
[17180351.244000] ndiswrapper (wrapper_init:134): loadndiswrapper failed (1792); check system log for messages from 'loadndisdriver'
[17180351.244000] ndiswrapper (wrapper_init:141): ndiswrapper: initialization failed
[17180555.344000] ndiswrapper version 1.17 loaded (preempt=no,smp=yes)

```

I tried restarting, but no luck. I also tried the following commands and then redoing the tutorial:

```
sudo modprobe -r bcmwl5
sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sdo rm -r /etc/modprobe.d/ndiswrapper

```

Anyone have any ideas? Thanks

---

### Post by ishift on 2006-10-30
i'm a linux newbie, but i thought i'd share this...

i had a similar problem and my friend and i, after almost an hour's worth of fooling around with it, found that using ndiswrapper-utils 1.8 worked wonderfully.

i don't know how helpful that is for you, but maybe you can try it and let us know.

---

### Post by kbsuperstar on 2006-10-30
I tried it, but it didn't work.

Could you give me a guide on how to uninstall and remove ndiswrapper-1.17 and how to install and set up my wifi with ndiswrapper-1.18 ?

Thanks

---

