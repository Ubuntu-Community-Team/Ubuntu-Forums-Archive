---
title: "ata slow to respond?  is that bad?"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by encompass on 2007-01-01
```
Jan  1 09:35:17 essence kernel: [17181036.704000] ata2 is slow to respond, please be patient
Jan  1 09:35:42 essence kernel: [17181061.680000] ata2 failed to respond (30 secs)
Jan  1 09:35:42 essence kernel: [17181061.696000] ata2: command 0xa0 timeout, stat 0xd0 host_stat 0x20
Jan  1 09:35:42 essence kernel: [17181061.696000] ata2: translated ATA stat/err 0xd0/00 to SCSI SK/ASC/ASCQ 0xb/47/00
Jan  1 09:41:08 essence kernel: [17181387.220000] ata2 is slow to respond, please be patient
Jan  1 09:41:33 essence kernel: [17181412.196000] ata2 failed to respond (30 secs)
Jan  1 09:41:33 essence kernel: [17181412.208000] ata2: command 0xa0 timeout, stat 0xd0 host_stat 0x0
Jan  1 09:41:33 essence kernel: [17181412.208000] ata2: translated ATA stat/err 0xd0/00 to SCSI SK/ASC/ASCQ 0xb/47/00
Jan  1 09:41:33 essence kernel: [17181412.208000] sr 1:0:0:0: ioctl_internal_command return code = 8000002
Jan  1 09:41:33 essence kernel: [17181412.208000]    : Current [descriptor]: sense key: Aborted Command
Jan  1 09:41:33 essence kernel: [17181412.208000]     Additional sense: Scsi parity error
```
Are these bad at all?  I don't seem to see anything wrong with the computer... everything involved with my sata drives seem fine. CD burning and other what not.  But just wondering if it could be "improved" so that I could MAYBE get my full suspend working.

---

### Post by mlissner on 2007-01-04
I'm getting some of these errors as well on edgy. Does anybody know what it takes to fix them? My system dies momentarily whenever these errors pop up in tty1...

---

### Post by keltren on 2007-01-19
I'm getting the same problem...at first I though I had a faulty sata drive, but it's happened on 2 different drives and apparently it's a known problem:

[http://www.mail-archive.com/debian-kernel@lists.debian.org/msg23880.html](http://www.mail-archive.com/debian-kernel@lists.debian.org/msg23880.html)

and there's apparently already a fix for it:

[http://www.mail-archive.com/debian-kernel@lists.debian.org/msg23221.html](http://www.mail-archive.com/debian-kernel@lists.debian.org/msg23221.html)

Is it possible that a sata dvd-drive might be confusing the driver? Yesterday I unplugged my drive to see if that helps and the system remained stable for the rest of the evening (5-6 hours) (after crashing 3 times in quick succession before)

---

### Post by mlissner on 2007-01-19
Hmmm...I'm not sure where to go from there. Which kernel should I try? I tried one, and it didn't work. It was just 46k of headers or something...I have a dual core intel chip on my laptop (gasp)

Hmmm...

For what it's worth, here's my dmesg, I doubt it's worth much:
```
[17179569.184000] Linux version 2.6.17-10-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Tue Dec 5 22:28:26 UTC 2006 (Ubuntu 2.6.17-10.34-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000007f7b0000 (usable)
[17179569.184000]  BIOS-e820: 000000007f7b0000 - 000000007f7be000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000007f7be000 - 000000007f7f0000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000007f7f0000 - 000000007f800000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[17179569.184000] 1143MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000ff780
[17179569.184000] On node 0 totalpages: 522160
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 292784 pages, LIFO batch:31
[17179569.184000] DMI present.
[17179569.184000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000fb700
[17179569.184000] ACPI: RSDT (v001 A M I  OEMRSDT  0x07000614 MSFT 0x00000097) @ 0x7f7b0000
[17179569.184000] ACPI: FADT (v002 A M I  OEMFACP  0x07000614 MSFT 0x00000097) @ 0x7f7b0200
[17179569.184000] ACPI: MADT (v001 A M I  OEMAPIC  0x07000614 MSFT 0x00000097) @ 0x7f7b0390
[17179569.184000] ACPI: MCFG (v001 A M I  OEMMCFG  0x07000614 MSFT 0x00000097) @ 0x7f7b03f0
[17179569.184000] ACPI: OEMB (v001 A M I  AMI_OEM  0x07000614 MSFT 0x00000097) @ 0x7f7be040
[17179569.184000] ACPI: DSDT (v001  A0544 A0544000 0x00000000 INTL 0x20060113) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x808
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:14 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[17179569.184000] Processor #1 6:14 APIC version 20
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 80000000 (gap: 7f800000:7f600000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=UUID=0be8c279-e19f-43aa-b251-cd1544442eb5 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[17179569.184000] Detected 1995.352 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.676000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179569.676000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.760000] Memory: 2059628k/2088640k available (1910k kernel code, 27728k reserved, 1069k data, 308k init, 1171136k highmem)
[17179569.760000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.840000] Calibrating delay using timer specific routine.. 3996.79 BogoMIPS (lpj=7993584)
[17179569.840000] Security Framework v1.0.0 initialized
[17179569.840000] SELinux:  Disabled at boot.
[17179569.840000] Mount-cache hash table entries: 512
[17179569.840000] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c1a9 00000000 00000000
[17179569.840000] CPU: After vendor identify, caps: bfe9fbff 00100000 00000000 00000000 0000c1a9 00000000 00000000
[17179569.840000] monitor/mwait feature present.
[17179569.840000] using mwait in idle threads.
[17179569.840000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179569.840000] CPU: L2 cache: 2048K
[17179569.840000] CPU: Hyper-Threading is disabled
[17179569.840000] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00000140 0000c1a9 00000000 00000000
[17179569.840000] Checking 'hlt' instruction... OK.
[17179569.856000] SMP alternatives: switching to UP code
[17179569.856000] checking if image is initramfs... it is
[17179570.408000] Freeing initrd memory: 6775k freed
[17179570.408000] ACPI: Core revision 20060707
[17179570.408000] ACPI: Looking for DSDT ... not found!
[17179570.412000] ACPI Warning (utinit-0077): Invalid FADT value PM2_CNT_LEN=0 at offset 5A FADT=dfffa780 [20060707]
[17179570.424000] CPU0: Intel Genuine Intel(R) CPU           T2500  @ 2.00GHz stepping 08
[17179570.424000] SMP alternatives: switching to SMP code
[17179570.424000] Booting processor 1/1 eip 3000
[17179570.432000] Initializing CPU#1
[17179570.516000] Calibrating delay using timer specific routine.. 3990.31 BogoMIPS (lpj=7980638)
[17179570.516000] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c1a9 00000000 00000000
[17179570.516000] CPU: After vendor identify, caps: bfe9fbff 00100000 00000000 00000000 0000c1a9 00000000 00000000
[17179570.516000] monitor/mwait feature present.
[17179570.516000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179570.516000] CPU: L2 cache: 2048K
[17179570.516000] CPU: Hyper-Threading is disabled
[17179570.516000] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00000140 0000c1a9 00000000 00000000
[17179570.516000] CPU1: Intel Genuine Intel(R) CPU           T2500  @ 2.00GHz stepping 08
[17179570.516000] Total of 2 processors activated (7987.11 BogoMIPS).
[17179570.516000] ENABLING IO-APIC IRQs
[17179570.516000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179570.660000] checking TSC synchronization across 2 CPUs: passed.
[17179570.664000] Brought up 2 CPUs
[17179570.932000] migration_cost=8000
[17179570.932000] NET: Registered protocol family 16
[17179570.932000] EISA bus registered
[17179570.932000] ACPI: bus type pci registered
[17179570.932000] PCI: BIOS Bug: MCFG area at e0000000 is not E820-reserved
[17179570.932000] PCI: Not using MMCONFIG.
[17179570.932000] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
[17179570.932000] PCI: Using configuration type 1
[17179570.932000] Setting up standard PCI resources
[17179570.972000] ACPI: Interpreter enabled
[17179570.972000] ACPI: Using IOAPIC for interrupt routing
[17179570.972000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.972000] PCI: Probing PCI hardware (bus 00)
[17179570.976000] Boot video device is 0000:00:02.0
[17179570.976000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.2
[17179570.976000] PCI: Transparent bridge - 0000:00:1e.0
[17179570.976000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.996000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[17179570.996000] ACPI: Embedded Controller [EC0] (gpe 28) interrupt mode.
[17179571.000000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[17179571.000000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[17179571.000000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]
[17179571.004000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179571.004000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[17179571.004000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179571.004000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[17179571.004000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179571.004000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179571.004000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179571.004000] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 10 11 12 14 15)
[17179571.004000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179571.004000] pnp: PnP ACPI init
[17179571.008000] pnp: PnP ACPI: found 12 devices
[17179571.008000] PnPBIOS: Disabled by ACPI PNP
[17179571.008000] PCI: Using ACPI for IRQ routing
[17179571.008000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179571.024000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[17179571.024000] PCI: Bridge: 0000:00:1c.0
[17179571.024000]   IO window: disabled.
[17179571.024000]   MEM window: disabled.
[17179571.024000]   PREFETCH window: disabled.
[17179571.024000] PCI: Bridge: 0000:00:1c.1
[17179571.024000]   IO window: disabled.
[17179571.024000]   MEM window: fe700000-fe7fffff
[17179571.024000]   PREFETCH window: disabled.
[17179571.024000] PCI: Bridge: 0000:00:1c.2
[17179571.024000]   IO window: c000-cfff
[17179571.024000]   MEM window: fdf00000-fe6fffff
[17179571.024000]   PREFETCH window: bdf00000-bfefffff
[17179571.024000] PCI: Bridge: 0000:00:1e.0
[17179571.024000]   IO window: d000-dfff
[17179571.028000]   MEM window: fe800000-fe8fffff
[17179571.028000]   PREFETCH window: 80000000-800fffff
[17179571.028000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179571.028000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179571.028000] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 177
[17179571.028000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[17179571.028000] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 185
[17179571.028000] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[17179571.028000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179571.028000] NET: Registered protocol family 2
[17179571.064000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179571.064000] TCP established hash table entries: 262144 (order: 9, 2097152 bytes)
[17179571.064000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[17179571.064000] TCP: Hash tables configured (established 262144 bind 65536)
[17179571.064000] TCP reno registered
[17179571.064000] audit: initializing netlink socket (disabled)
[17179571.064000] audit(1168927842.064:1): initialized
[17179571.064000] highmem bounce pool size: 64 pages
[17179571.064000] VFS: Disk quotas dquot_6.5.1
[17179571.064000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179571.064000] Initializing Cryptographic API
[17179571.064000] io scheduler noop registered
[17179571.064000] io scheduler anticipatory registered
[17179571.064000] io scheduler deadline registered
[17179571.064000] io scheduler cfq registered (default)
[17179571.064000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179571.064000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179571.064000] assign_interrupt_mode Found MSI capability
[17179571.064000] Allocate Port Service[0000:00:1c.0:pcie00]
[17179571.064000] Allocate Port Service[0000:00:1c.0:pcie02]
[17179571.064000] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 177
[17179571.064000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[17179571.064000] assign_interrupt_mode Found MSI capability
[17179571.064000] Allocate Port Service[0000:00:1c.1:pcie00]
[17179571.064000] Allocate Port Service[0000:00:1c.1:pcie02]
[17179571.064000] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 185
[17179571.064000] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[17179571.064000] assign_interrupt_mode Found MSI capability
[17179571.064000] Allocate Port Service[0000:00:1c.2:pcie00]
[17179571.064000] Allocate Port Service[0000:00:1c.2:pcie02]
[17179571.068000] isapnp: Scanning for PnP cards...
[17179571.432000] isapnp: No Plug & Play device found
[17179571.452000] Real Time Clock Driver v1.12ac
[17179571.452000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179571.452000] mice: PS/2 mouse device common for all mice
[17179571.452000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179571.452000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179571.452000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179571.452000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179571.456000] i8042.c: Detected active multiplexing controller, rev 1.1.
[17179571.456000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[17179571.456000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[17179571.456000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[17179571.456000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[17179571.456000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179571.456000] EISA: Probing bus 0 at eisa.0
[17179571.456000] EISA: Detected 0 cards.
[17179571.456000] TCP bic registered
[17179571.456000] NET: Registered protocol family 1
[17179571.456000] NET: Registered protocol family 8
[17179571.456000] NET: Registered protocol family 20
[17179571.456000] Starting balanced_irq
[17179571.456000] Using IPI No-Shortcut mode
[17179571.456000] ACPI: (supports S0 S1 S3 S4 S5)
[17179571.460000] Freeing unused kernel memory: 308k freed
[17179571.648000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179572.520000] Capability LSM initialized
[17179572.556000] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [   AMI] OemTableId [  CPU1PM] [20060707]
[17179572.556000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[17179572.556000] ACPI: Processor [CPU1] (supports 8 throttling states)
[17179572.556000] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [   AMI] OemTableId [  CPU2PM] [20060707]
[17179572.556000] ACPI: CPU1 (power states: C1[C1] C2[C2])
[17179572.556000] ACPI: Processor [CPU2] (supports 8 throttling states)
[17179572.556000] ACPI: Thermal Zone [TZ00] (53 C)
[17179572.828000] SCSI subsystem initialized
[17179572.832000] libata version 1.20 loaded.
[17179572.832000] ata_piix 0000:00:1f.2: version 1.05
[17179572.832000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 225
[17179572.832000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179572.832000] ata1: SATA max UDMA/133 cmd 0x1F0 ctl 0x3F6 bmdma 0xFFA0 irq 14
[17179572.996000] ata1: disabling port
[17179572.996000] scsi0 : ata_piix
[17179572.996000] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xFFA8 irq 15
[17179573.220000] ata2: dev 0 cfg 49:2f00 82:346b 83:7d09 84:6003 85:3468 86:3c09 87:6003 88:203f
[17179573.220000] ata2: dev 0 ATA-7, max UDMA/100, 195371568 sectors: LBA48
[17179573.220000] ata2(0): applying bridge limits
[17179573.404000] ata2: dev 1 cfg 49:0f00 82:0000 83:4000 84:4000 85:0000 86:0000 87:4000 88:0407
[17179573.404000] ata2: dev 1 ATAPI, max UDMA/33
[17179573.404000] ata2(1): applying bridge limits
[17179573.416000] ata2: dev 0 configured for UDMA/100
[17179573.624000] ata2: dev 1 configured for UDMA/33
[17179573.624000] scsi1 : ata_piix
[17179573.624000]   Vendor: ATA       Model: ST910021A         Rev: 3.04
[17179573.624000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179573.664000]   Vendor: TSSTcorp  Model: CD/DVDW TS-L632D  Rev: AS05
[17179573.664000]   Type:   CD-ROM                             ANSI SCSI revision: 05
[17179573.672000] SCSI device sda: 195371568 512-byte hdwr sectors (100030 MB)
[17179573.672000] sda: Write Protect is off
[17179573.672000] sda: Mode Sense: 00 3a 00 00
[17179573.672000] SCSI device sda: drive cache: write back
[17179573.672000] SCSI device sda: 195371568 512-byte hdwr sectors (100030 MB)
[17179573.672000] sda: Write Protect is off
[17179573.672000] sda: Mode Sense: 00 3a 00 00
[17179573.672000] SCSI device sda: drive cache: write back
[17179573.672000]  sda: sda1 sda2 < sda5 >
[17179573.712000] sd 1:0:0:0: Attached scsi disk sda
[17179573.892000] ide0: I/O resource 0x1F0-0x1F7 not free.
[17179573.892000] ide0: ports already in use, skipping probe
[17179573.892000] ide1: I/O resource 0x170-0x177 not free.
[17179573.892000] ide1: ports already in use, skipping probe
[17179573.904000] usbcore: registered new driver usbfs
[17179573.904000] usbcore: registered new driver hub
[17179573.912000] USB Universal Host Controller Interface driver v3.0
[17179573.912000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 233
[17179573.912000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179573.912000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179573.912000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179573.912000] uhci_hcd 0000:00:1d.0: irq 233, io base 0x0000e400
[17179573.912000] usb usb1: configuration #1 chosen from 1 choice
[17179573.912000] hub 1-0:1.0: USB hub found
[17179573.912000] hub 1-0:1.0: 2 ports detected
[17179573.924000] ieee1394: Initialized config rom entry `ip1394'
[17179574.020000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 225
[17179574.020000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179574.020000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179574.020000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179574.020000] uhci_hcd 0000:00:1d.1: irq 225, io base 0x0000e480
[17179574.020000] usb usb2: configuration #1 chosen from 1 choice
[17179574.020000] hub 2-0:1.0: USB hub found
[17179574.020000] hub 2-0:1.0: 2 ports detected
[17179574.124000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 185
[17179574.124000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179574.124000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179574.124000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179574.124000] uhci_hcd 0000:00:1d.2: irq 185, io base 0x0000e800
[17179574.124000] usb usb3: configuration #1 chosen from 1 choice
[17179574.124000] hub 3-0:1.0: USB hub found
[17179574.124000] hub 3-0:1.0: 2 ports detected
[17179574.228000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 169
[17179574.228000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17179574.228000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[17179574.228000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[17179574.228000] uhci_hcd 0000:00:1d.3: irq 169, io base 0x0000e880
[17179574.228000] usb usb4: configuration #1 chosen from 1 choice
[17179574.228000] hub 4-0:1.0: USB hub found
[17179574.228000] hub 4-0:1.0: 2 ports detected
[17179574.332000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 233
[17179574.332000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179574.332000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179574.332000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[17179574.332000] ehci_hcd 0000:00:1d.7: debug port 1
[17179574.332000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[17179574.332000] ehci_hcd 0000:00:1d.7: irq 233, io mem 0xfeb3fc00
[17179574.336000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179574.348000] usb usb5: configuration #1 chosen from 1 choice
[17179574.348000] hub 5-0:1.0: USB hub found
[17179574.348000] hub 5-0:1.0: 8 ports detected
[17179574.364000] usb 2-1: new full speed USB device using uhci_hcd and address 2
[17179574.452000] ACPI: PCI Interrupt 0000:05:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179574.508000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[169]  MMIO=[fe8fe800-fe8fefff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[17179574.684000] EXT3-fs: INFO: recovery required on readonly filesystem.
[17179574.684000] EXT3-fs: write access will be enabled during recovery.
[17179575.188000] usb 2-1: new full speed USB device using uhci_hcd and address 3
[17179575.368000] usb 2-1: configuration #1 chosen from 1 choice
[17179575.612000] usb 2-2: new full speed USB device using uhci_hcd and address 4
[17179575.784000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e0180003680ccb]
[17179575.796000] usb 2-2: configuration #1 chosen from 1 choice
[17179575.816000] usbcore: registered new driver hiddev
[17179575.816000] input: Logitech USB Receiver as /class/input/input1
[17179575.816000] input: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-2
[17179575.828000] input: Logitech USB Receiver as /class/input/input2
[17179575.828000] input,hiddev96: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.1-2
[17179575.828000] usbcore: registered new driver usbhid
[17179575.828000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179579.144000] kjournald starting.  Commit interval 5 seconds
[17179579.144000] EXT3-fs: sda1: orphan cleanup on readonly fs
[17179579.144000] ext3_orphan_cleanup: deleting unreferenced inode 3784750
[17179579.144000] EXT3-fs: sda1: 1 orphan inode deleted
[17179579.144000] EXT3-fs: recovery complete.
[17179579.184000] EXT3-fs: mounted filesystem with ordered data mode.
[17179588.044000] input: PC Speaker as /class/input/input3
[17179588.360000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179588.384000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179588.440000] hw_random: RNG not detected
[17179588.476000] Linux agpgart interface v0.101 (c) Dave Jones
[17179588.604000] agpgart: Detected an Intel 945GM Chipset.
[17179588.604000] agpgart: Detected 7932K stolen memory.
[17179588.620000] agpgart: AGP aperture is 256M @ 0xd0000000
[17179588.724000] sd 1:0:0:0: Attached scsi generic sg0 type 0
[17179588.728000]  1:0:1:0: Attached scsi generic sg1 type 5
[17179588.780000] sr0: scsi3-mmc drive: 62x/62x writer dvd-ram cd/rw xa/form2 cdda tray
[17179588.780000] Uniform CD-ROM driver Revision: 3.20
[17179588.780000] sr 1:0:1:0: Attached scsi CD-ROM sr0
[17179588.948000] sdhci: Secure Digital Host Controller Interface driver, 0.12
[17179588.948000] sdhci: Copyright(c) Pierre Ossman
[17179588.952000] sdhci: SDHCI controller found at 0000:05:01.1 [1180:0822] (rev 19)
[17179588.952000] ACPI: PCI Interrupt 0000:05:01.1[B] -> GSI 17 (level, low) -> IRQ 177
[17179588.952000] mmc0: SDHCI at 0xfe8ff000 irq 177 DMA
[17179588.976000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x04F9 pid 0x0110
[17179588.976000] usbcore: registered new driver usblp
[17179588.976000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[17179589.004000] ACPI: PCI Interrupt 0000:05:07.0[A] -> GSI 18 (level, low) -> IRQ 185
[17179589.004000] eth0: Identified chip type is 'RTL8169SC/8110SC'.
[17179589.004000] eth0: r10001.02, the Linux device driver for Realtek Ethernet Controllers at 0xd800, 00:18:f3:41:42:b1, IRQ 185
[17179589.004000] eth0: Auto-negotiation Enabled.
[17179589.208000] Synaptics Touchpad, model: 1, fw: 6.1, id: 0xa3a0b3, caps: 0xa04713/0x10008
[17179589.252000] input: SynPS/2 Synaptics TouchPad as /class/input/input4
[17179596.684000] Realtek RTL8169/8110 Family Gigabit Ethernet Network Adapter
[17179596.684000] Driver version:1.02
[17179596.684000] Released date:2006/02/23
[17179596.684000] Link Status:Not Linked
[17179596.684000] I/O Base:0xD800(I/O port)
[17179596.684000] IRQ:185
[17179596.684000] BUG: warning at drivers/scsi/libata-core.c:3266/ata_pio_complete()
[17179596.684000]  <f887d145> ata_pio_task+0x745/0x7c0 [libata]  <c011cdf8> __wake_up+0x38/0x50
[17179596.684000]  <c0132702> run_workqueue+0x72/0xf0  <f887ca00> ata_pio_task+0x0/0x7c0 [libata]
[17179596.684000]  <c01332e7> worker_thread+0x117/0x140  <c011bde0> default_wake_function+0x0/0x10
[17179596.684000]  <c01331d0> worker_thread+0x0/0x140  <c0135f8b> kthread+0xab/0xe0
[17179596.684000]  <c0135ee0> kthread+0x0/0xe0  <c0101005> kernel_thread_helper+0x5/0x10
[17179596.684000] ata2: command 0x58 timeout, stat 0x50 host_stat 0x0
[17179596.756000] ieee80211_crypt: registered algorithm 'NULL'
[17179596.756000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[17179596.756000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17179596.788000] ts: Compaq touchscreen protocol output
[17179596.892000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.1.0mp
[17179596.892000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[17179596.892000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 177
[17179596.892000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[17179596.892000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[17179596.912000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179596.912000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[17179597.296000] hda_codec: Unknown model for ALC882, trying auto-probe from BIOS...
[17179597.996000] lp: driver loaded but no devices found
[17179598.024000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179598.024000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179598.084000] Unable to find swap-space signature
[17179598.172000] EXT3 FS on sda1, internal journal
[17179598.308000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179598.308000] md: bitmap version 4.39
[17179598.460000] device-mapper: 4.6.0-ioctl (2006-02-17) initialised: dm-devel@redhat.com
[17179598.804000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
[17179599.200000] cdrom: sr0: mrw address space DMA selected
[17179599.496000] Unable to find swap-space signature
[17179600.324000] NET: Registered protocol family 17
[17179615.848000] Asus Laptop ACPI Extras version 0.30
[17179615.848000]   Error calling BSTS
[17179615.848000]   unsupported model Z96F, trying default values
[17179615.848000]   send /proc/acpi/dsdt to the developers
[17179615.864000] ACPI: AC Adapter [AC0] (on-line)
[17179615.908000] ACPI: Battery Slot [BAT0] (battery present)
[17179615.920000] ACPI: Power Button (FF) [PWRF]
[17179615.920000] ACPI: Lid Switch [LID]
[17179615.920000] ACPI: Sleep Button (CM) [SLPB]
[17179615.920000] ACPI: Power Button (CM) [PWRB]
[17179616.044000] ibm_acpi: ec object not found
[17179616.084000] pcc_acpi: loading...
[17179616.180000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[17179619.040000] [drm] Initialized drm 1.0.1 20051102
[17179619.044000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179619.044000] [drm] Initialized i915 1.5.0 20060119 on minor 0
[17179619.524000] apm: BIOS not found.
[17179622.288000] cdrom: This disc doesn't have any tracks I recognize!
[17179623.556000] vmmon: module license 'unspecified' taints kernel.
[17179623.560000] /dev/vmmon[4764]: Module vmmon: registered with major=10 minor=165
[17179623.560000] /dev/vmmon[4764]: Module vmmon: initialized
[17179623.688000] /dev/vmnet: open called by PID 4790 (vmnet-bridge)
[17179623.688000] /dev/vmnet: hub 0 does not exist, allocating memory.
[17179623.688000] /dev/vmnet: port on hub 0 successfully opened
[17179623.688000] bridge-eth0: peer interface eth0 not found, will wait for it to come up
[17179623.688000] bridge-eth0: attached
[17179623.732000] /dev/vmnet: open called by PID 4796 (vmnet-netifup)
[17179623.732000] /dev/vmnet: hub 1 does not exist, allocating memory.
[17179623.732000] /dev/vmnet: port on hub 1 successfully opened
[17179623.736000] /dev/vmnet: open called by PID 4804 (vmnet-netifup)
[17179623.736000] /dev/vmnet: hub 8 does not exist, allocating memory.
[17179623.736000] /dev/vmnet: port on hub 8 successfully opened
[17179623.756000] /dev/vmnet: open called by PID 4806 (vmnet-natd)
[17179623.756000] /dev/vmnet: port on hub 8 successfully opened
[17179623.820000] /dev/vmnet: open called by PID 4825 (vmnet-dhcpd)
[17179623.820000] /dev/vmnet: port on hub 8 successfully opened
[17179623.820000] /dev/vmnet: open called by PID 4834 (vmnet-dhcpd)
[17179623.820000] /dev/vmnet: port on hub 1 successfully opened
[17179623.936000] Bluetooth: Core ver 2.8
[17179623.936000] NET: Registered protocol family 31
[17179623.936000] Bluetooth: HCI device and connection manager initialized
[17179623.936000] Bluetooth: HCI socket layer initialized
[17179623.952000] Bluetooth: L2CAP ver 2.8
[17179623.952000] Bluetooth: L2CAP socket layer initialized
[17179623.956000] Bluetooth: HIDP (Human Interface Emulation) ver 1.1-mh1
[17179623.980000] Bluetooth: RFCOMM socket layer initialized
[17179623.980000] Bluetooth: RFCOMM TTY layer initialized
[17179623.980000] Bluetooth: RFCOMM ver 1.7
[17179625.060000] bridge-eth0: enabling the bridge
[17179625.060000] bridge-eth0: up
[17179630.828000] NET: Registered protocol family 10
[17179630.828000] lo: Disabled Privacy Extensions
[17179630.828000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17179630.828000] IPv6 over IPv4 tunneling driver
[17179640.852000] vmnet1: no IPv6 routers present
[17179640.888000] vmnet8: no IPv6 routers present
[17179641.740000] eth0: no IPv6 routers present
[17179647.708000] ieee80211_crypt: registered algorithm 'WEP'
[17179647.968000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[17179662.456000] eth1: no IPv6 routers present
[17271266.380000] ata2 is slow to respond, please be patient
[17271291.380000] ata2 failed to respond (30 secs)
[17271291.392000] ata2: command 0xa0 timeout, stat 0xd0 host_stat 0x0
[17271291.392000] ata2: translated ATA stat/err 0xd0/00 to SCSI SK/ASC/ASCQ 0xb/47/00
[17271291.392000] sr 1:0:1:0: ioctl_internal_command return code = 8000002
[17271291.392000]    : Current [descriptor]: sense key: Aborted Command
[17271291.392000]     Additional sense: Scsi parity error
[17476012.032000] ata2 is slow to respond, please be patient
[17476037.008000] ata2 failed to respond (30 secs)
[17476037.020000] ata2: command 0xa0 timeout, stat 0xd0 host_stat 0x0
[17476037.020000] ata2: translated ATA stat/err 0xd0/00 to SCSI SK/ASC/ASCQ 0xb/47/00

```

Thanks.

---

### Post by encompass on 2007-01-20
thanks for the info guys...

---

### Post by mlissner on 2007-01-20
encompass, if you're going to do this, will you let us know if it works? I'm a bit overwelmed with trying to sort the whole thing out.

---

