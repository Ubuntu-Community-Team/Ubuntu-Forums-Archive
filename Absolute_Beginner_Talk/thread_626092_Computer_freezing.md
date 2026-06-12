---
title: "Computer freezing"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by TheOrangePeanut on 2007-11-28
My computer has frozen, as in a dead stop with no mouse or keyboard support, 3 times today.  It's frozen before but I've not been able to track down why.  Someone told me to look at my kern.log and see if anything was weird, but I wouldn't know if it was or not.  I've only been using Ubuntu for about a month, maybe a month and a half.  Does anything look weird in my log for today?

```

Nov 28 01:19:34 alpha-pc kernel: [90927.230669] Assertion failure in journal_unmap_buffer() at /build/buildd/linux-source-2.6.22-2.6.22/fs/jbd/transaction.c:1886: "!buffer_jbddirty(bh)"
Nov 28 01:19:34 alpha-pc kernel: [90927.230729] ------------[ cut here ]------------
Nov 28 01:19:34 alpha-pc kernel: [90927.230732] kernel BUG at /build/buildd/linux-source-2.6.22-2.6.22/fs/jbd/transaction.c:1886!
Nov 28 01:19:34 alpha-pc kernel: [90927.230735] invalid opcode: 0000 [#1]
Nov 28 01:19:34 alpha-pc kernel: [90927.230737] SMP 
Nov 28 01:19:34 alpha-pc kernel: [90927.230739] Modules linked in: snd_rtctimer ipv6 af_packet fglrx(P) vboxdrv cpufreq_ondemand cpufreq_conservative cpufreq_stats freq_table cpufreq_userspace cpufreq_powersave container sbs ac dock video button battery lp loop snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi parport_pc parport snd_seq_midi_event snd_seq snd_timer snd_seq_device pcspkr serio_raw psmouse i2c_nforce2 snd soundcore snd_page_alloc shpchp pci_hotplug i2c_core nvidia_agp agpgart evdev ext3 jbd mbcache ide_cd cdrom ide_disk amd74xx ide_core sata_nv floppy ata_generic libata scsi_mod forcedeth ehci_hcd ohci_hcd usbcore thermal processor fan fuse apparmor commoncap
Nov 28 01:19:34 alpha-pc kernel: [90927.230777] CPU:    0
Nov 28 01:19:34 alpha-pc kernel: [90927.230778] EIP:    0060:[<f895e39f>]    Tainted: P       VLI
Nov 28 01:19:34 alpha-pc kernel: [90927.230779] EFLAGS: 00210282   (2.6.22-14-generic #1)
Nov 28 01:19:34 alpha-pc kernel: [90927.230795] EIP is at journal_invalidatepage+0x17f/0x3a0 [jbd]
Nov 28 01:19:34 alpha-pc kernel: [90927.230798] eax: 0000009c   ebx: f6d03300   ecx: 00200092   edx: 00000000
Nov 28 01:19:34 alpha-pc kernel: [90927.230801] esi: dfeb9000   edi: 00000006   ebp: 00000001   esp: ee2b7e50
Nov 28 01:19:34 alpha-pc kernel: [90927.230804] ds: 007b   es: 007b   fs: 00d8  gs: 0033  ss: 0068
Nov 28 01:19:34 alpha-pc kernel: [90927.230807] Process firefox-bin (pid: 7513, ti=ee2b6000 task=ea3c39f0 task.ti=ee2b6000)
Nov 28 01:19:34 alpha-pc kernel: [90927.230809] Stack: f8964c30 f89643ca f8964bf0 0000075e f8964838 00000000 c1595fe0 f6d03310 
Nov 28 01:19:34 alpha-pc kernel: [90927.230815]        00000001 f6d04300 00000001 c1595f40 00000005 f6d03310 c1595fe0 00000b91 
Nov 28 01:19:34 alpha-pc kernel: [90927.230821]        00000006 ffffffff c01663c4 c1595fe0 c0166705 c1595fe0 c01667fa 0000000e 
Nov 28 01:19:34 alpha-pc kernel: [90927.230826] Call Trace:
Nov 28 01:19:34 alpha-pc kernel: [90927.230836]  [do_invalidatepage+20/48] do_invalidatepage+0x14/0x30
Nov 28 01:19:34 alpha-pc kernel: [90927.230845]  [truncate_complete_page+69/80] truncate_complete_page+0x45/0x50
Nov 28 01:19:34 alpha-pc kernel: [90927.230850]  [truncate_inode_pages_range+234/736] truncate_inode_pages_range+0xea/0x2e0
Nov 28 01:19:34 alpha-pc kernel: [90927.230864]  [<f899b7a0>] ext3_delete_inode+0x0/0xd0 [ext3]
Nov 28 01:19:34 alpha-pc kernel: [90927.230883]  [truncate_inode_pages+23/32] truncate_inode_pages+0x17/0x20
Nov 28 01:19:34 alpha-pc kernel: [90927.230888]  [<f899b7b3>] ext3_delete_inode+0x13/0xd0 [ext3]
Nov 28 01:19:34 alpha-pc kernel: [90927.230896]  [<f899b7a0>] ext3_delete_inode+0x0/0xd0 [ext3]
Nov 28 01:19:34 alpha-pc kernel: [90927.230904]  [generic_delete_inode+127/288] generic_delete_inode+0x7f/0x120
Nov 28 01:19:34 alpha-pc kernel: [90927.230912]  [iput+86/112] iput+0x56/0x70
Nov 28 01:19:34 alpha-pc kernel: [90927.230916]  [do_unlinkat+243/336] do_unlinkat+0xf3/0x150
Nov 28 01:19:34 alpha-pc kernel: [90927.230932]  [sysenter_past_esp+107/169] sysenter_past_esp+0x6b/0xa9
Nov 28 01:19:34 alpha-pc kernel: [90927.230943]  =======================
Nov 28 01:19:34 alpha-pc kernel: [90927.230944] Code: 44 24 10 38 48 96 f8 c7 44 24 0c 5e 07 00 00 c7 44 24 08 f0 4b 96 f8 c7 44 24 04 ca 43 96 f8 c7 04 24 30 4c 96 f8 e8 91 a8 7c c7 <0f> 0b eb fe 8d 46 14 e8 a5 5a 99 c7 90 0f ba 2b 15 19 c0 85 c0 
Nov 28 01:19:34 alpha-pc kernel: [90927.230967] EIP: [<f895e39f>] journal_invalidatepage+0x17f/0x3a0 [jbd] SS:ESP 0068:ee2b7e50
Nov 28 07:58:58 alpha-pc kernel: [114865.666697] [fglrx] Internal AGP support requested, but kernel AGP support active.
Nov 28 07:58:58 alpha-pc kernel: [114865.666704] [fglrx] Have to use kernel AGP support to avoid conflicts.
Nov 28 07:58:58 alpha-pc kernel: [114865.666709] [fglrx] AGP detected, AgpState   = 0x1f00420b (hardware caps of chipset)
Nov 28 07:58:58 alpha-pc kernel: [114865.667383] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
Nov 28 07:58:58 alpha-pc kernel: [114865.667571] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Nov 28 07:58:58 alpha-pc kernel: [114865.667789] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
Nov 28 07:58:58 alpha-pc kernel: [114865.667972] [fglrx] AGP enabled,  AgpCommand = 0x1f004302 (selected caps)
Nov 28 07:58:58 alpha-pc kernel: [114865.678773] [fglrx] total      GART = 67108864
Nov 28 07:58:58 alpha-pc kernel: [114865.678784] [fglrx] free       GART = 51113984
Nov 28 07:58:58 alpha-pc kernel: [114865.678786] [fglrx] max single GART = 51113984
Nov 28 07:58:58 alpha-pc kernel: [114865.678789] [fglrx] total      LFB  = 134217728
Nov 28 07:58:58 alpha-pc kernel: [114865.678791] [fglrx] free       LFB  = 108974080
Nov 28 07:58:58 alpha-pc kernel: [114865.678793] [fglrx] max single LFB  = 108974080
Nov 28 07:58:58 alpha-pc kernel: [114865.678794] [fglrx] total      Inv  = 0
Nov 28 07:58:58 alpha-pc kernel: [114865.678796] [fglrx] free       Inv  = 0
Nov 28 07:58:58 alpha-pc kernel: [114865.678798] [fglrx] max single Inv  = 0
Nov 28 07:58:58 alpha-pc kernel: [114865.678800] [fglrx] total      TIM  = 0
Nov 28 14:06:09 alpha-pc kernel: Inspecting /boot/System.map-2.6.22-14-generic
Nov 28 14:06:09 alpha-pc kernel: Loaded 25445 symbols from /boot/System.map-2.6.22-14-generic.
Nov 28 14:06:09 alpha-pc kernel: Symbols match kernel version 2.6.22.
Nov 28 14:06:09 alpha-pc kernel: No module symbols loaded - kernel modules not enabled. 
Nov 28 14:06:09 alpha-pc kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
Nov 28 14:06:09 alpha-pc kernel: [    0.000000] BIOS-provided physical RAM map:
Nov 28 14:06:09 alpha-pc kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Nov 28 14:06:09 alpha-pc kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Nov 28 14:06:09 alpha-pc kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Nov 28 14:06:09 alpha-pc kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
Nov 28 14:06:09 alpha-pc kernel: [    0.000000]  BIOS-e820: 000000003fff0000 - 000000003fff3000 (ACPI NVS)
Nov 28 14:06:09 alpha-pc kernel: [    0.000000]  BIOS-e820: 000000003fff3000 - 0000000040000000 (ACPI data)
Nov 28 14:06:09 alpha-pc kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Nov 28 14:06:09 alpha-pc kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Nov 28 14:06:09 alpha-pc kernel: [    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
Nov 28 14:06:09 alpha-pc kernel: [    0.000000] 127MB HIGHMEM available.
Nov 28 14:06:09 alpha-pc kernel: [    0.000000] 896MB LOWMEM available.
Nov 28 14:06:09 alpha-pc kernel: [    0.000000] found SMP MP-table at 000f5bf0
Nov 28 14:06:09 alpha-pc kernel: [    0.000000] Entering add_active_range(0, 0, 262128) 0 entries of 256 used
Nov 28 14:06:09 alpha-pc kernel: [    0.000000] Zone PFN ranges:
Nov 28 14:06:09 alpha-pc kernel: [    0.000000]   DMA             0 ->     4096
Nov 28 14:06:09 alpha-pc kernel: [    0.000000]   Normal       4096 ->   229376
Nov 28 14:06:09 alpha-pc kernel: [    0.000000]   HighMem    229376 ->   262128
Nov 28 14:06:09 alpha-pc kernel: [    0.000000] early_node_map[1] active PFN ranges
Nov 28 14:06:09 alpha-pc kernel: [    0.000000]     0:        0 ->   262128
Nov 28 14:06:09 alpha-pc kernel: [    0.000000] On node 0 totalpages: 262128
Nov 28 14:06:09 alpha-pc kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Nov 28 14:06:09 alpha-pc kernel: [    0.000000]   DMA zone: 0 pages reserved
Nov 28 14:06:09 alpha-pc kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Nov 28 14:06:09 alpha-pc kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Nov 28 14:06:09 alpha-pc kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Nov 28 14:06:09 alpha-pc kernel: [    0.000000]   HighMem zone: 255 pages used for memmap
Nov 28 14:06:09 alpha-pc kernel: [    0.000000]   HighMem zone: 32497 pages, LIFO batch:7
Nov 28 14:06:09 alpha-pc kernel: [    0.000000] DMI 2.2 present.
Nov 28 14:06:09 alpha-pc kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F7620 checksum 0
Nov 28 14:06:09 alpha-pc kernel: [    0.000000] ACPI: RSDP 000F7620, 0014 (r0 Nvidia)
Nov 28 14:06:09 alpha-pc kernel: [    0.000000] ACPI: RSDT 3FFF3000, 002C (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
Nov 28 14:06:09 alpha-pc kernel: [    0.000000] ACPI: FACP 3FFF3040, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
Nov 28 14:06:09 alpha-pc kernel: [    0.000000] ACPI: DSDT 3FFF30C0, 4E50 (r1 NVIDIA AWRDACPI     1000 MSFT  100000E)
Nov 28 14:06:09 alpha-pc kernel: [    0.000000] ACPI: FACS 3FFF0000, 0040
Nov 28 14:06:09 alpha-pc kernel: [    0.000000] ACPI: APIC 3FFF7F40, 006E (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
Nov 28 14:06:09 alpha-pc kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.
Nov 28 14:06:09 alpha-pc kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override
Nov 28 14:06:09 alpha-pc kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Nov 28 14:06:09 alpha-pc kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Nov 28 14:06:09 alpha-pc kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Nov 28 14:06:09 alpha-pc kernel: [    0.000000] Processor #0 6:10 APIC version 16
Nov 28 14:06:09 alpha-pc kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Nov 28 14:06:09 alpha-pc kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Nov 28 14:06:09 alpha-pc kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
Nov 28 14:06:09 alpha-pc kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Nov 28 14:06:09 alpha-pc kernel: [    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
Nov 28 14:06:09 alpha-pc kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Nov 28 14:06:09 alpha-pc kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
Nov 28 14:06:09 alpha-pc kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
Nov 28 14:06:09 alpha-pc kernel: [    0.000000] ACPI: IRQ9 used by override.
Nov 28 14:06:09 alpha-pc kernel: [    0.000000] ACPI: IRQ14 used by override.
Nov 28 14:06:09 alpha-pc kernel: [    0.000000] ACPI: IRQ15 used by override.
Nov 28 14:06:09 alpha-pc kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Nov 28 14:06:09 alpha-pc kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Nov 28 14:06:09 alpha-pc kernel: [    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
Nov 28 14:06:09 alpha-pc kernel: [    0.000000] Built 1 zonelists.  Total pages: 260081
Nov 28 14:06:09 alpha-pc kernel: [    0.000000] Kernel command line: root=UUID=7cf890f6-1437-407b-9f45-d233d3a80826 ro quiet splash
Nov 28 14:06:09 alpha-pc kernel: [    0.000000] mapped APIC to ffffd000 (fee00000)
Nov 28 14:06:09 alpha-pc kernel: [    0.000000] mapped IOAPIC to ffffc000 (fec00000)
Nov 28 14:06:09 alpha-pc kernel: [    0.000000] Enabling fast FPU save and restore... done.
Nov 28 14:06:09 alpha-pc kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Nov 28 14:06:09 alpha-pc kernel: [    0.000000] Initializing CPU#0
Nov 28 14:06:09 alpha-pc kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Nov 28 14:06:09 alpha-pc kernel: [    0.000000] Detected 2074.815 MHz processor.
Nov 28 14:06:09 alpha-pc kernel: [   16.552007] Console: colour VGA+ 80x25
Nov 28 14:06:09 alpha-pc kernel: [   16.552578] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Nov 28 14:06:09 alpha-pc kernel: [   16.553055] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Nov 28 14:06:09 alpha-pc kernel: [   16.581127] Memory: 1027880k/1048512k available (2015k kernel code, 19928k reserved, 916k data, 364k init, 131008k highmem)
Nov 28 14:06:09 alpha-pc kernel: [   16.581137] virtual kernel memory layout:
Nov 28 14:06:09 alpha-pc kernel: [   16.581138]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
Nov 28 14:06:09 alpha-pc kernel: [   16.581139]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Nov 28 14:06:09 alpha-pc kernel: [   16.581141]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Nov 28 14:06:09 alpha-pc kernel: [   16.581142]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Nov 28 14:06:09 alpha-pc kernel: [   16.581143]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
Nov 28 14:06:09 alpha-pc kernel: [   16.581144]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
Nov 28 14:06:09 alpha-pc kernel: [   16.581146]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
Nov 28 14:06:09 alpha-pc kernel: [   16.581149] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Nov 28 14:06:09 alpha-pc kernel: [   16.581193] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Nov 28 14:06:09 alpha-pc kernel: [   16.661132] Calibrating delay using timer specific routine.. 4152.96 BogoMIPS (lpj=8305938)
Nov 28 14:06:09 alpha-pc kernel: [   16.661167] Security Framework v1.0.0 initialized
Nov 28 14:06:09 alpha-pc kernel: [   16.661174] SELinux:  Disabled at boot.
Nov 28 14:06:09 alpha-pc kernel: [   16.661190] Mount-cache hash table entries: 512
Nov 28 14:06:09 alpha-pc kernel: [   16.661341] CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
Nov 28 14:06:09 alpha-pc kernel: [   16.661350] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Nov 28 14:06:09 alpha-pc kernel: [   16.661352] CPU: L2 Cache: 512K (64 bytes/line)
Nov 28 14:06:09 alpha-pc kernel: [   16.661355] CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000420 00000000 00000000 00000000
Nov 28 14:06:09 alpha-pc kernel: [   16.661367] Compat vDSO mapped to ffffe000.
Nov 28 14:06:09 alpha-pc kernel: [   16.661380] Checking 'hlt' instruction... OK.
Nov 28 14:06:09 alpha-pc kernel: [   16.677262] SMP alternatives: switching to UP code
Nov 28 14:06:09 alpha-pc kernel: [   16.677541] Freeing SMP alternatives: 11k freed
Nov 28 14:06:09 alpha-pc kernel: [   16.677868] Early unpacking initramfs... done
Nov 28 14:06:09 alpha-pc kernel: [   16.972396] ACPI: Core revision 20070126
Nov 28 14:06:09 alpha-pc kernel: [   16.972491] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Nov 28 14:06:09 alpha-pc kernel: [   16.975425] CPU0: AMD Athlon(tm) XP 2800+ stepping 00
Nov 28 14:06:09 alpha-pc kernel: [   16.975446] Total of 1 processors activated (4152.96 BogoMIPS).
Nov 28 14:06:09 alpha-pc kernel: [   16.975641] ENABLING IO-APIC IRQs
Nov 28 14:06:09 alpha-pc kernel: [   16.975833] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
Nov 28 14:06:09 alpha-pc kernel: [   17.120725] Brought up 1 CPUs
Nov 28 14:06:09 alpha-pc kernel: [   17.120852] Booting paravirtualized kernel on bare hardware
Nov 28 14:06:09 alpha-pc kernel: [   17.120919] Time: 20:05:39  Date: 10/28/107
Nov 28 14:06:09 alpha-pc kernel: [   17.120943] NET: Registered protocol family 16
Nov 28 14:06:09 alpha-pc kernel: [   17.121041] EISA bus registered
Nov 28 14:06:09 alpha-pc kernel: [   17.121053] ACPI: bus type pci registered
Nov 28 14:06:09 alpha-pc kernel: [   17.153028] PCI: PCI BIOS revision 2.10 entry at 0xfbe50, last bus=2
Nov 28 14:06:09 alpha-pc kernel: [   17.153030] PCI: Using configuration type 1
Nov 28 14:06:09 alpha-pc kernel: [   17.153032] Setting up standard PCI resources
Nov 28 14:06:09 alpha-pc kernel: [   17.158056] ACPI: EC: Look up EC in DSDT
Nov 28 14:06:09 alpha-pc kernel: [   17.162869] ACPI: Interpreter enabled
Nov 28 14:06:09 alpha-pc kernel: [   17.162872] ACPI: (supports S0 S1 S4 S5)
Nov 28 14:06:09 alpha-pc kernel: [   17.162887] ACPI: Using IOAPIC for interrupt routing
Nov 28 14:06:09 alpha-pc kernel: [   17.171995] ACPI: PCI Root Bridge [PCI0] (0000:00)
Nov 28 14:06:09 alpha-pc kernel: [   17.172001] PCI: Probing PCI hardware (bus 00)
Nov 28 14:06:09 alpha-pc kernel: [   17.172829] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Nov 28 14:06:09 alpha-pc kernel: [   17.172984] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
Nov 28 14:06:09 alpha-pc kernel: [   17.173235] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
Nov 28 14:06:09 alpha-pc kernel: [   17.221999] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Nov 28 14:06:09 alpha-pc kernel: [   17.222161] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Nov 28 14:06:09 alpha-pc kernel: [   17.222321] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Nov 28 14:06:09 alpha-pc kernel: [   17.222480] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Nov 28 14:06:09 alpha-pc kernel: [   17.222638] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Nov 28 14:06:09 alpha-pc kernel: [   17.222798] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Nov 28 14:06:09 alpha-pc kernel: [   17.222966] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Nov 28 14:06:09 alpha-pc kernel: [   17.223131] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Nov 28 14:06:09 alpha-pc kernel: [   17.223289] ACPI: PCI Interrupt Link [LAPU] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Nov 28 14:06:09 alpha-pc kernel: [   17.223449] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Nov 28 14:06:09 alpha-pc kernel: [   17.223607] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Nov 28 14:06:09 alpha-pc kernel: [   17.223767] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Nov 28 14:06:09 alpha-pc kernel: [   17.223927] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Nov 28 14:06:09 alpha-pc kernel: [   17.224088] ACPI: PCI Interrupt Link [LFIR] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Nov 28 14:06:09 alpha-pc kernel: [   17.224247] ACPI: PCI Interrupt Link [L3CM] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Nov 28 14:06:09 alpha-pc kernel: [   17.224406] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Nov 28 14:06:09 alpha-pc kernel: [   17.224574] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Nov 28 14:06:09 alpha-pc kernel: [   17.224720] ACPI: PCI Interrupt Link [APC1] (IRQs *16)
Nov 28 14:06:09 alpha-pc kernel: [   17.224843] ACPI: PCI Interrupt Link [APC2] (IRQs *17), disabled.
Nov 28 14:06:09 alpha-pc kernel: [   17.224965] ACPI: PCI Interrupt Link [APC3] (IRQs *18), disabled.
Nov 28 14:06:09 alpha-pc kernel: [   17.225087] ACPI: PCI Interrupt Link [APC4] (IRQs *19), disabled.
Nov 28 14:06:09 alpha-pc kernel: [   17.225209] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
Nov 28 14:06:09 alpha-pc kernel: [   17.225386] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21) *0
Nov 28 14:06:09 alpha-pc kernel: [   17.225561] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21) *0
Nov 28 14:06:09 alpha-pc kernel: [   17.225735] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21) *0
Nov 28 14:06:09 alpha-pc kernel: [   17.225908] ACPI: PCI Interrupt Link [APCI] (IRQs 20 21) *0, disabled.
Nov 28 14:06:09 alpha-pc kernel: [   17.226083] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21) *0
Nov 28 14:06:09 alpha-pc kernel: [   17.226256] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21) *0, disabled.
Nov 28 14:06:09 alpha-pc kernel: [   17.226381] ACPI: PCI Interrupt Link [APCS] (IRQs *23)
Nov 28 14:06:09 alpha-pc kernel: [   17.226554] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21) *0
Nov 28 14:06:09 alpha-pc kernel: [   17.226728] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21) *0, disabled.
Nov 28 14:06:09 alpha-pc kernel: [   17.226901] ACPI: PCI Interrupt Link [AP3C] (IRQs 20 21) *0, disabled.
Nov 28 14:06:09 alpha-pc kernel: [   17.227075] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21) *0, disabled.
Nov 28 14:06:09 alpha-pc kernel: [   17.227257] ACPI: PCI Interrupt Link [APSI] (IRQs 22) *0
Nov 28 14:06:09 alpha-pc kernel: [   17.227393] ACPI: Power Resource [ISAV] (on)
Nov 28 14:06:09 alpha-pc kernel: [   17.227410] Linux Plug and Play Support v0.97 (c) Adam Belay
Nov 28 14:06:09 alpha-pc kernel: [   17.227422] pnp: PnP ACPI init
Nov 28 14:06:09 alpha-pc kernel: [   17.227430] ACPI: bus type pnp registered
Nov 28 14:06:09 alpha-pc kernel: [   17.231953] pnp: PnP ACPI: found 15 devices
Nov 28 14:06:09 alpha-pc kernel: [   17.231955] ACPI: ACPI bus type pnp unregistered
Nov 28 14:06:09 alpha-pc kernel: [   17.231960] PnPBIOS: Disabled by ACPI PNP
Nov 28 14:06:09 alpha-pc kernel: [   17.232014] PCI: Using ACPI for IRQ routing
Nov 28 14:06:09 alpha-pc kernel: [   17.232018] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Nov 28 14:06:09 alpha-pc kernel: [   17.269475] NET: Registered protocol family 8
Nov 28 14:06:09 alpha-pc kernel: [   17.269477] NET: Registered protocol family 20
Nov 28 14:06:09 alpha-pc kernel: [   17.269545] pnp: 00:00: ioport range 0x4000-0x407f has been reserved
Nov 28 14:06:09 alpha-pc kernel: [   17.269549] pnp: 00:00: ioport range 0x4080-0x40ff has been reserved
Nov 28 14:06:09 alpha-pc kernel: [   17.269551] pnp: 00:00: ioport range 0x4400-0x447f has been reserved
Nov 28 14:06:09 alpha-pc kernel: [   17.269554] pnp: 00:00: ioport range 0x4480-0x44ff has been reserved
Nov 28 14:06:09 alpha-pc kernel: [   17.269557] pnp: 00:00: ioport range 0x4200-0x427f has been reserved
Nov 28 14:06:09 alpha-pc kernel: [   17.269559] pnp: 00:00: ioport range 0x4280-0x42ff has been reserved
Nov 28 14:06:09 alpha-pc kernel: [   17.269564] pnp: 00:01: ioport range 0x5000-0x503f has been reserved
Nov 28 14:06:09 alpha-pc kernel: [   17.269566] pnp: 00:01: ioport range 0x5100-0x513f has been reserved
Nov 28 14:06:09 alpha-pc kernel: [   17.269571] pnp: 00:02: iomem range 0xd5800-0xd7fff has been reserved
Nov 28 14:06:09 alpha-pc kernel: [   17.269574] pnp: 00:02: iomem range 0xf0000-0xf7fff could not be reserved
Nov 28 14:06:09 alpha-pc kernel: [   17.269577] pnp: 00:02: iomem range 0xf8000-0xfbfff could not be reserved
Nov 28 14:06:09 alpha-pc kernel: [   17.269580] pnp: 00:02: iomem range 0xfc000-0xfffff could not be reserved
Nov 28 14:06:09 alpha-pc kernel: [   17.272529] Time: tsc clocksource has been installed.
Nov 28 14:06:09 alpha-pc kernel: [   17.299862] PCI: Bridge: 0000:00:08.0
Nov 28 14:06:09 alpha-pc kernel: [   17.299864]   IO window: disabled.
Nov 28 14:06:09 alpha-pc kernel: [   17.299868]   MEM window: disabled.
Nov 28 14:06:09 alpha-pc kernel: [   17.299872]   PREFETCH window: disabled.
Nov 28 14:06:09 alpha-pc kernel: [   17.299879] PCI: Bridge: 0000:00:1e.0
Nov 28 14:06:09 alpha-pc kernel: [   17.299881]   IO window: 9000-9fff
Nov 28 14:06:09 alpha-pc kernel: [   17.299885]   MEM window: e4000000-e5ffffff
Nov 28 14:06:09 alpha-pc kernel: [   17.299889]   PREFETCH window: d0000000-dfffffff
Nov 28 14:06:09 alpha-pc kernel: [   17.299900] PCI: Setting latency timer of device 0000:00:08.0 to 64
Nov 28 14:06:09 alpha-pc kernel: [   17.299914] NET: Registered protocol family 2
Nov 28 14:06:09 alpha-pc kernel: [   17.336512] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Nov 28 14:06:09 alpha-pc kernel: [   17.336686] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
Nov 28 14:06:09 alpha-pc kernel: [   17.338655] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Nov 28 14:06:09 alpha-pc kernel: [   17.339409] TCP: Hash tables configured (established 131072 bind 65536)
Nov 28 14:06:09 alpha-pc kernel: [   17.339412] TCP reno registered
Nov 28 14:06:09 alpha-pc kernel: [   17.348589] checking if image is initramfs... it is
Nov 28 14:06:09 alpha-pc kernel: [   17.800009] Switched to high resolution mode on CPU 0
Nov 28 14:06:09 alpha-pc kernel: [   17.909279] Freeing initrd memory: 7061k freed
Nov 28 14:06:09 alpha-pc kernel: [   17.909708] audit: initializing netlink socket (disabled)
Nov 28 14:06:09 alpha-pc kernel: [   17.909722] audit(1196280339.088:1): initialized
Nov 28 14:06:09 alpha-pc kernel: [   17.909787] highmem bounce pool size: 64 pages
Nov 28 14:06:09 alpha-pc kernel: [   17.911534] VFS: Disk quotas dquot_6.5.1
Nov 28 14:06:09 alpha-pc kernel: [   17.911589] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Nov 28 14:06:09 alpha-pc kernel: [   17.911683] io scheduler noop registered
Nov 28 14:06:09 alpha-pc kernel: [   17.911685] io scheduler anticipatory registered
Nov 28 14:06:09 alpha-pc kernel: [   17.911687] io scheduler deadline registered
Nov 28 14:06:09 alpha-pc kernel: [   17.911701] io scheduler cfq registered (default)
Nov 28 14:06:09 alpha-pc kernel: [   17.943774] Boot video device is 0000:01:00.0
Nov 28 14:06:09 alpha-pc kernel: [   17.943935] isapnp: Scanning for PnP cards...
Nov 28 14:06:09 alpha-pc kernel: [   18.298032] isapnp: No Plug & Play device found
Nov 28 14:06:09 alpha-pc kernel: [   18.320808] Real Time Clock Driver v1.12ac
Nov 28 14:06:09 alpha-pc kernel: [   18.320916] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Nov 28 14:06:09 alpha-pc kernel: [   18.321023] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Nov 28 14:06:09 alpha-pc kernel: [   18.321175] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Nov 28 14:06:09 alpha-pc kernel: [   18.321687] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Nov 28 14:06:09 alpha-pc kernel: [   18.321909] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Nov 28 14:06:09 alpha-pc kernel: [   18.322595] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Nov 28 14:06:09 alpha-pc kernel: [   18.322809] input: Macintosh mouse button emulation as /class/input/input0
Nov 28 14:06:09 alpha-pc kernel: [   18.322882] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Nov 28 14:06:09 alpha-pc kernel: [   18.325666] serio: i8042 KBD port at 0x60,0x64 irq 1
Nov 28 14:06:09 alpha-pc kernel: [   18.325672] serio: i8042 AUX port at 0x60,0x64 irq 12
Nov 28 14:06:09 alpha-pc kernel: [   18.325851] mice: PS/2 mouse device common for all mice
Nov 28 14:06:09 alpha-pc kernel: [   18.325961] EISA: Probing bus 0 at eisa.0
Nov 28 14:06:09 alpha-pc kernel: [   18.325985] Cannot allocate resource for EISA slot 4
Nov 28 14:06:09 alpha-pc kernel: [   18.325988] Cannot allocate resource for EISA slot 5
Nov 28 14:06:09 alpha-pc kernel: [   18.326003] EISA: Detected 0 cards.
Nov 28 14:06:09 alpha-pc kernel: [   18.326102] TCP cubic registered
Nov 28 14:06:09 alpha-pc kernel: [   18.326111] NET: Registered protocol family 1
Nov 28 14:06:09 alpha-pc kernel: [   18.326131] Using IPI No-Shortcut mode
Nov 28 14:06:09 alpha-pc kernel: [   18.326302]   Magic number: 15:769:94
Nov 28 14:06:09 alpha-pc kernel: [   18.326906] Freeing unused kernel memory: 364k freed
Nov 28 14:06:09 alpha-pc kernel: [   18.367337] input: AT Translated Set 2 keyboard as /class/input/input1
Nov 28 14:06:09 alpha-pc kernel: [   19.514702] AppArmor: AppArmor initialized<5>audit(1196280340.588:2):  type=1505 info="AppArmor initialized" pid=1231
Nov 28 14:06:09 alpha-pc kernel: [   19.536665] fuse init (API version 7.8)
Nov 28 14:06:09 alpha-pc kernel: [   19.637204] Failure registering capabilities with primary security module.
Nov 28 14:06:09 alpha-pc kernel: [   20.501080] usbcore: registered new interface driver usbfs
Nov 28 14:06:09 alpha-pc kernel: [   20.501107] usbcore: registered new interface driver hub
Nov 28 14:06:09 alpha-pc kernel: [   20.501130] usbcore: registered new device driver usb
Nov 28 14:06:09 alpha-pc kernel: [   20.501816] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Nov 28 14:06:09 alpha-pc kernel: [   20.502182] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
Nov 28 14:06:09 alpha-pc kernel: [   20.502191] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 21 (level, high) -> IRQ 16
Nov 28 14:06:09 alpha-pc kernel: [   20.502206] PCI: Setting latency timer of device 0000:00:02.0 to 64
Nov 28 14:06:09 alpha-pc kernel: [   20.502209] ohci_hcd 0000:00:02.0: OHCI Host Controller
Nov 28 14:06:09 alpha-pc kernel: [   20.502410] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
Nov 28 14:06:09 alpha-pc kernel: [   20.502428] ohci_hcd 0000:00:02.0: irq 16, io mem 0xe6001000
Nov 28 14:06:09 alpha-pc kernel: [   20.529500] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
Nov 28 14:06:09 alpha-pc kernel: [   20.566689] SCSI subsystem initialized
Nov 28 14:06:09 alpha-pc kernel: [   20.571435] libata version 2.21 loaded.
Nov 28 14:06:09 alpha-pc kernel: [   20.607230] usb usb1: configuration #1 chosen from 1 choice
Nov 28 14:06:09 alpha-pc kernel: [   20.607261] hub 1-0:1.0: USB hub found
Nov 28 14:06:09 alpha-pc kernel: [   20.607273] hub 1-0:1.0: 4 ports detected
Nov 28 14:06:09 alpha-pc kernel: [   20.693823] Floppy drive(s): fd0 is 1.44M
Nov 28 14:06:09 alpha-pc kernel: [   20.709072] ACPI: PCI Interrupt Link [APCG] enabled at IRQ 20
Nov 28 14:06:09 alpha-pc kernel: [   20.709082] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCG] -> GSI 20 (level, high) -> IRQ 17
Nov 28 14:06:09 alpha-pc kernel: [   20.709099] PCI: Setting latency timer of device 0000:00:02.1 to 64
Nov 28 14:06:09 alpha-pc kernel: [   20.709103] ohci_hcd 0000:00:02.1: OHCI Host Controller
Nov 28 14:06:09 alpha-pc kernel: [   20.709129] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
Nov 28 14:06:09 alpha-pc kernel: [   20.709147] ohci_hcd 0000:00:02.1: irq 17, io mem 0xe6002000
Nov 28 14:06:09 alpha-pc kernel: [   20.735259] FDC 0 is a post-1991 82077
Nov 28 14:06:09 alpha-pc kernel: [   20.766634] usb usb2: configuration #1 chosen from 1 choice
Nov 28 14:06:09 alpha-pc kernel: [   20.766663] hub 2-0:1.0: USB hub found
Nov 28 14:06:09 alpha-pc kernel: [   20.766676] hub 2-0:1.0: 4 ports detected
Nov 28 14:06:09 alpha-pc kernel: [   20.869187] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 21
Nov 28 14:06:09 alpha-pc kernel: [   20.869193] ACPI: PCI Interrupt 0000:00:02.2[C] -> Link [APCL] -> GSI 21 (level, high) -> IRQ 16
Nov 28 14:06:09 alpha-pc kernel: [   20.869206] PCI: Setting latency timer of device 0000:00:02.2 to 64
Nov 28 14:06:09 alpha-pc kernel: [   20.869210] ehci_hcd 0000:00:02.2: EHCI Host Controller
Nov 28 14:06:09 alpha-pc kernel: [   20.869236] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
Nov 28 14:06:09 alpha-pc kernel: [   20.869274] ehci_hcd 0000:00:02.2: debug port 1
Nov 28 14:06:09 alpha-pc kernel: [   20.869279] PCI: cache line size of 64 is not supported by device 0000:00:02.2
Nov 28 14:06:09 alpha-pc kernel: [   20.869286] ehci_hcd 0000:00:02.2: irq 16, io mem 0xe6003000
Nov 28 14:06:09 alpha-pc kernel: [   20.869293] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Nov 28 14:06:09 alpha-pc kernel: [   20.869373] usb usb3: configuration #1 chosen from 1 choice
Nov 28 14:06:09 alpha-pc kernel: [   20.869407] hub 3-0:1.0: USB hub found
Nov 28 14:06:09 alpha-pc kernel: [   20.869416] hub 3-0:1.0: 8 ports detected
Nov 28 14:06:09 alpha-pc kernel: [   20.972842] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 20
Nov 28 14:06:09 alpha-pc kernel: [   20.972848] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCH] -> GSI 20 (level, high) -> IRQ 17
Nov 28 14:06:09 alpha-pc kernel: [   20.972855] PCI: Setting latency timer of device 0000:00:04.0 to 64
Nov 28 14:06:09 alpha-pc kernel: [   21.492098] eth0: forcedeth.c: subsystem: 01462:570c bound to 0000:00:04.0
Nov 28 14:06:09 alpha-pc kernel: [   21.495229] sata_nv 0000:00:0b.0: version 3.4
Nov 28 14:06:09 alpha-pc kernel: [   21.495633] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 22
Nov 28 14:06:09 alpha-pc kernel: [   21.495642] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [APSI] -> GSI 22 (level, high) -> IRQ 18
Nov 28 14:06:09 alpha-pc kernel: [   21.495710] PCI: Setting latency timer of device 0000:00:0b.0 to 64
Nov 28 14:06:09 alpha-pc kernel: [   21.496173] scsi0 : sata_nv
Nov 28 14:06:09 alpha-pc kernel: [   21.496374] scsi1 : sata_nv
Nov 28 14:06:09 alpha-pc kernel: [   21.496545] ata1: SATA max UDMA/133 cmd 0x000109f0 ctl 0x00010bf2 bmdma 0x0001b000 irq 18
Nov 28 14:06:09 alpha-pc kernel: [   21.496550] ata2: SATA max UDMA/133 cmd 0x00010970 ctl 0x00010b72 bmdma 0x0001b008 irq 18
Nov 28 14:06:09 alpha-pc kernel: [   21.502064] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Nov 28 14:06:09 alpha-pc kernel: [   21.502070] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Nov 28 14:06:09 alpha-pc kernel: [   21.807324] ata1: SATA link down (SStatus 0 SControl 300)
Nov 28 14:06:09 alpha-pc kernel: [   22.118964] ata2: SATA link down (SStatus 0 SControl 300)
Nov 28 14:06:09 alpha-pc kernel: [   22.119085] NFORCE2-U400R: IDE controller at PCI slot 0000:00:09.0
Nov 28 14:06:09 alpha-pc kernel: [   22.119195] NFORCE2-U400R: chipset revision 163
Nov 28 14:06:09 alpha-pc kernel: [   22.119198] NFORCE2-U400R: not 100%% native mode: will probe irqs later
Nov 28 14:06:09 alpha-pc kernel: [   22.119202] NFORCE2-U400R: BIOS didn't set cable bits correctly. Enabling workaround.
Nov 28 14:06:09 alpha-pc kernel: [   22.119205] NFORCE2-U400R: BIOS didn't set cable bits correctly. Enabling workaround.
Nov 28 14:06:09 alpha-pc kernel: [   22.119211] NFORCE2-U400R: 0000:00:09.0 (rev a3) UDMA133 controller
Nov 28 14:06:09 alpha-pc kernel: [   22.119222]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
Nov 28 14:06:09 alpha-pc kernel: [   22.119233]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
Nov 28 14:06:09 alpha-pc kernel: [   22.119243] Probing IDE interface ide0...
Nov 28 14:06:09 alpha-pc kernel: [   22.406753] hda: Maxtor 4D040H2, ATA DISK drive
Nov 28 14:06:09 alpha-pc kernel: [   23.078332] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Nov 28 14:06:09 alpha-pc kernel: [   23.095668] Probing IDE interface ide1...
Nov 28 14:06:09 alpha-pc kernel: [   23.829118] hdc: LITE-ON DVDRW SOHW-1633S, ATAPI CD/DVD-ROM drive
Nov 28 14:06:09 alpha-pc kernel: [   24.500769] ide1 at 0x170-0x177,0x376 on irq 15
Nov 28 14:06:09 alpha-pc kernel: [   24.507938] hda: max request size: 128KiB
Nov 28 14:06:09 alpha-pc kernel: [   24.516593] hda: 80043264 sectors (40982 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
Nov 28 14:06:09 alpha-pc kernel: [   24.516602] hda: cache flushes not supported
Nov 28 14:06:09 alpha-pc kernel: [   24.516655]  hda: hda1 hda2 < hda5 >
Nov 28 14:06:09 alpha-pc kernel: [   24.570389] hdc: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(66)
Nov 28 14:06:09 alpha-pc kernel: [   24.570399] Uniform CD-ROM driver Revision: 3.20
Nov 28 14:06:09 alpha-pc kernel: [   24.830510] Attempting manual resume
Nov 28 14:06:09 alpha-pc kernel: [   24.830514] swsusp: Resume From Partition 3:5
Nov 28 14:06:09 alpha-pc kernel: [   24.830516] PM: Checking swsusp image.
Nov 28 14:06:09 alpha-pc kernel: [   24.830693] PM: Resume from disk failed.
Nov 28 14:06:09 alpha-pc kernel: [   24.845691] EXT3-fs: INFO: recovery required on readonly filesystem.
Nov 28 14:06:09 alpha-pc kernel: [   24.845696] EXT3-fs: write access will be enabled during recovery.
Nov 28 14:06:09 alpha-pc kernel: [   33.329326] kjournald starting.  Commit interval 5 seconds
Nov 28 14:06:09 alpha-pc kernel: [   33.329348] EXT3-fs: hda1: orphan cleanup on readonly fs
Nov 28 14:06:09 alpha-pc kernel: [   33.365175] ext3_orphan_cleanup: deleting unreferenced inode 3457354
Nov 28 14:06:09 alpha-pc kernel: [   33.365226] ext3_orphan_cleanup: deleting unreferenced inode 3457355
Nov 28 14:06:09 alpha-pc kernel: [   33.365239] ext3_orphan_cleanup: deleting unreferenced inode 1540153
Nov 28 14:06:09 alpha-pc kernel: [   33.365270] ext3_orphan_cleanup: deleting unreferenced inode 1540797
Nov 28 14:06:09 alpha-pc kernel: [   33.493708] EXT3-fs: hda1: 4 orphan inodes deleted
Nov 28 14:06:09 alpha-pc kernel: [   33.493710] EXT3-fs: recovery complete.
Nov 28 14:06:09 alpha-pc kernel: [   33.699643] EXT3-fs: mounted filesystem with ordered data mode.
Nov 28 14:06:09 alpha-pc kernel: [   42.542271] Linux agpgart interface v0.102 (c) Dave Jones
Nov 28 14:06:09 alpha-pc kernel: [   42.624459] agpgart: Detected NVIDIA nForce2 chipset
Nov 28 14:06:09 alpha-pc kernel: [   42.628661] agpgart: AGP aperture is 64M @ 0xe0000000
Nov 28 14:06:09 alpha-pc kernel: [   42.745656] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x5000
Nov 28 14:06:09 alpha-pc kernel: [   42.745689] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x5100
Nov 28 14:06:09 alpha-pc kernel: [   43.588939] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Nov 28 14:06:09 alpha-pc kernel: [   43.593246] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Nov 28 14:06:09 alpha-pc kernel: [   43.764647] logips2pp: Detected unknown logitech mouse model 89
Nov 28 14:06:09 alpha-pc kernel: [   44.089523] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 21
Nov 28 14:06:09 alpha-pc kernel: [   44.089530] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [APCJ] -> GSI 21 (level, high) -> IRQ 16
Nov 28 14:06:09 alpha-pc kernel: [   44.089555] PCI: Setting latency timer of device 0000:00:06.0 to 64
Nov 28 14:06:09 alpha-pc kernel: [   44.238370] input: ImExPS/2 Logitech Explorer Mouse as /class/input/input2
Nov 28 14:06:09 alpha-pc kernel: [   44.241435] parport_pc 00:0c: reported by Plug and Play ACPI
Nov 28 14:06:09 alpha-pc kernel: [   44.241493] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Nov 28 14:06:09 alpha-pc kernel: [   44.242050] input: PC Speaker as /class/input/input3
Nov 28 14:06:09 alpha-pc kernel: [   44.409363] intel8x0_measure_ac97_clock: measured 54706 usecs
Nov 28 14:06:09 alpha-pc kernel: [   44.409367] intel8x0: clocking to 47456
Nov 28 14:06:09 alpha-pc kernel: [   45.024220] loop: module loaded
Nov 28 14:06:09 alpha-pc kernel: [   45.043379] lp0: using parport0 (interrupt-driven).
Nov 28 14:06:09 alpha-pc kernel: [   45.131031] Adding 1686784k swap on /dev/hda5.  Priority:-1 extents:1 across:1686784k
Nov 28 14:06:09 alpha-pc kernel: [   45.442744] EXT3 FS on hda1, internal journal
Nov 28 14:06:09 alpha-pc kernel: [   46.497793] input: Power Button (FF) as /class/input/input4
Nov 28 14:06:09 alpha-pc kernel: [   46.502013] ACPI: Power Button (FF) [PWRF]
Nov 28 14:06:09 alpha-pc kernel: [   46.538924] input: Power Button (CM) as /class/input/input5
Nov 28 14:06:09 alpha-pc kernel: [   46.543069] ACPI: Power Button (CM) [PWRB]
Nov 28 14:06:09 alpha-pc kernel: [   46.594819] No dock devices found.
Nov 28 14:06:10 alpha-pc kernel: [   48.016383] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Nov 28 14:06:10 alpha-pc kernel: [   48.016389] apm: overridden by ACPI.
Nov 28 14:06:10 alpha-pc kernel: [   48.298126] vboxdrv: Trying to deactivate the NMI watchdog permanently...
Nov 28 14:06:10 alpha-pc kernel: [   48.298132] vboxdrv: Successfully done.
Nov 28 14:06:10 alpha-pc kernel: [   48.623099] Failure registering capabilities with primary security module.
Nov 28 14:06:13 alpha-pc kernel: [   51.177411] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Nov 28 14:06:13 alpha-pc kernel: [   51.182018] [fglrx] Maximum main memory to use for locked dma buffers: 929 MBytes.
Nov 28 14:06:13 alpha-pc kernel: [   51.182334] [fglrx] module loaded - fglrx 8.37.6 [May 25 2007] on minor 0
Nov 28 14:06:13 alpha-pc kernel: [   51.566673] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
Nov 28 14:06:13 alpha-pc kernel: [   51.566684] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 19
Nov 28 14:06:17 alpha-pc kernel: [   54.975483] NET: Registered protocol family 17
Nov 28 14:06:18 alpha-pc kernel: [   55.977000] [fglrx] Internal AGP support requested, but kernel AGP support active.
Nov 28 14:06:18 alpha-pc kernel: [   55.977007] [fglrx] Have to use kernel AGP support to avoid conflicts.
Nov 28 14:06:18 alpha-pc kernel: [   55.977012] [fglrx] AGP detected, AgpState   = 0x1f00420b (hardware caps of chipset)
Nov 28 14:06:18 alpha-pc kernel: [   55.977772] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
Nov 28 14:06:18 alpha-pc kernel: [   55.977973] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Nov 28 14:06:18 alpha-pc kernel: [   55.978193] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
Nov 28 14:06:18 alpha-pc kernel: [   55.978392] [fglrx] AGP enabled,  AgpCommand = 0x1f004302 (selected caps)
Nov 28 14:06:18 alpha-pc kernel: [   55.986605] [fglrx] total      GART = 67108864
Nov 28 14:06:18 alpha-pc kernel: [   55.986614] [fglrx] free       GART = 51113984
Nov 28 14:06:18 alpha-pc kernel: [   55.986616] [fglrx] max single GART = 51113984
Nov 28 14:06:18 alpha-pc kernel: [   55.986618] [fglrx] total      LFB  = 134217728
Nov 28 14:06:18 alpha-pc kernel: [   55.986620] [fglrx] free       LFB  = 108974080
Nov 28 14:06:18 alpha-pc kernel: [   55.986622] [fglrx] max single LFB  = 108974080
Nov 28 14:06:18 alpha-pc kernel: [   55.986623] [fglrx] total      Inv  = 0
Nov 28 14:06:18 alpha-pc kernel: [   55.986625] [fglrx] free       Inv  = 0
Nov 28 14:06:18 alpha-pc kernel: [   55.986627] [fglrx] max single Inv  = 0
Nov 28 14:06:18 alpha-pc kernel: [   55.986628] [fglrx] total      TIM  = 0
Nov 28 14:06:20 alpha-pc kernel: [   58.616622] NET: Registered protocol family 10
Nov 28 14:06:20 alpha-pc kernel: [   58.616783] lo: Disabled Privacy Extensions
Nov 28 14:06:30 alpha-pc kernel: [   68.694732] eth0: no IPv6 routers present
Nov 28 15:12:50 alpha-pc kernel: [ 4043.725259] VM: killing process Xorg
Nov 28 15:12:55 alpha-pc kernel: [ 4048.921449] [fglrx] Internal AGP support requested, but kernel AGP support active.
Nov 28 15:12:55 alpha-pc kernel: [ 4048.921456] [fglrx] Have to use kernel AGP support to avoid conflicts.
Nov 28 15:12:55 alpha-pc kernel: [ 4048.921461] [fglrx] AGP detected, AgpState   = 0x1f00420b (hardware caps of chipset)
Nov 28 15:12:55 alpha-pc kernel: [ 4048.922365] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
Nov 28 15:12:55 alpha-pc kernel: [ 4048.922564] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Nov 28 15:12:55 alpha-pc kernel: [ 4048.922822] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
Nov 28 15:12:55 alpha-pc kernel: [ 4048.923031] [fglrx] AGP enabled,  AgpCommand = 0x1f004302 (selected caps)
Nov 28 15:12:55 alpha-pc kernel: [ 4048.933581] [fglrx] total      GART = 67108864
Nov 28 15:12:55 alpha-pc kernel: [ 4048.933589] [fglrx] free       GART = 51113984
Nov 28 15:12:55 alpha-pc kernel: [ 4048.933591] [fglrx] max single GART = 51113984
Nov 28 15:12:55 alpha-pc kernel: [ 4048.933593] [fglrx] total      LFB  = 134217728
Nov 28 15:12:55 alpha-pc kernel: [ 4048.933595] [fglrx] free       LFB  = 108974080
Nov 28 15:12:55 alpha-pc kernel: [ 4048.933597] [fglrx] max single LFB  = 108974080
Nov 28 15:12:55 alpha-pc kernel: [ 4048.933599] [fglrx] total      Inv  = 0
Nov 28 15:12:55 alpha-pc kernel: [ 4048.933601] [fglrx] free       Inv  = 0
Nov 28 15:12:55 alpha-pc kernel: [ 4048.933602] [fglrx] max single Inv  = 0
Nov 28 15:12:55 alpha-pc kernel: [ 4048.933604] [fglrx] total      TIM  = 0
Nov 28 17:35:12 alpha-pc kernel: Inspecting /boot/System.map-2.6.22-14-generic
Nov 28 17:35:13 alpha-pc kernel: Loaded 25445 symbols from /boot/System.map-2.6.22-14-generic.
Nov 28 17:35:13 alpha-pc kernel: Symbols match kernel version 2.6.22.
Nov 28 17:35:13 alpha-pc kernel: No module symbols loaded - kernel modules not enabled. 
Nov 28 17:35:13 alpha-pc kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
Nov 28 17:35:13 alpha-pc kernel: [    0.000000] BIOS-provided physical RAM map:
Nov 28 17:35:13 alpha-pc kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Nov 28 17:35:13 alpha-pc kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Nov 28 17:35:13 alpha-pc kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Nov 28 17:35:13 alpha-pc kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
Nov 28 17:35:13 alpha-pc kernel: [    0.000000]  BIOS-e820: 000000003fff0000 - 000000003fff3000 (ACPI NVS)
Nov 28 17:35:13 alpha-pc kernel: [    0.000000]  BIOS-e820: 000000003fff3000 - 0000000040000000 (ACPI data)
Nov 28 17:35:13 alpha-pc kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Nov 28 17:35:13 alpha-pc kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Nov 28 17:35:13 alpha-pc kernel: [    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
Nov 28 17:35:13 alpha-pc kernel: [    0.000000] 127MB HIGHMEM available.
Nov 28 17:35:13 alpha-pc kernel: [    0.000000] 896MB LOWMEM available.
Nov 28 17:35:13 alpha-pc kernel: [    0.000000] found SMP MP-table at 000f5bf0
Nov 28 17:35:13 alpha-pc kernel: [    0.000000] Entering add_active_range(0, 0, 262128) 0 entries of 256 used
Nov 28 17:35:13 alpha-pc kernel: [    0.000000] Zone PFN ranges:
Nov 28 17:35:13 alpha-pc kernel: [    0.000000]   DMA             0 ->     4096
Nov 28 17:35:13 alpha-pc kernel: [    0.000000]   Normal       4096 ->   229376
Nov 28 17:35:13 alpha-pc kernel: [    0.000000]   HighMem    229376 ->   262128
Nov 28 17:35:13 alpha-pc kernel: [    0.000000] early_node_map[1] active PFN ranges
Nov 28 17:35:13 alpha-pc kernel: [    0.000000]     0:        0 ->   262128
Nov 28 17:35:13 alpha-pc kernel: [    0.000000] On node 0 totalpages: 262128
Nov 28 17:35:13 alpha-pc kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Nov 28 17:35:13 alpha-pc kernel: [    0.000000]   DMA zone: 0 pages reserved
Nov 28 17:35:13 alpha-pc kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Nov 28 17:35:13 alpha-pc kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Nov 28 17:35:13 alpha-pc kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Nov 28 17:35:13 alpha-pc kernel: [    0.000000]   HighMem zone: 255 pages used for memmap
Nov 28 17:35:13 alpha-pc kernel: [    0.000000]   HighMem zone: 32497 pages, LIFO batch:7
Nov 28 17:35:13 alpha-pc kernel: [    0.000000] DMI 2.2 present.
Nov 28 17:35:13 alpha-pc kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F7620 checksum 0
Nov 28 17:35:13 alpha-pc kernel: [    0.000000] ACPI: RSDP 000F7620, 0014 (r0 Nvidia)
Nov 28 17:35:13 alpha-pc kernel: [    0.000000] ACPI: RSDT 3FFF3000, 002C (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
Nov 28 17:35:13 alpha-pc kernel: [    0.000000] ACPI: FACP 3FFF3040, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
Nov 28 17:35:13 alpha-pc kernel: [    0.000000] ACPI: DSDT 3FFF30C0, 4E50 (r1 NVIDIA AWRDACPI     1000 MSFT  100000E)
Nov 28 17:35:13 alpha-pc kernel: [    0.000000] ACPI: FACS 3FFF0000, 0040
Nov 28 17:35:13 alpha-pc kernel: [    0.000000] ACPI: APIC 3FFF7F40, 006E (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
Nov 28 17:35:13 alpha-pc kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.
Nov 28 17:35:13 alpha-pc kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override
Nov 28 17:35:13 alpha-pc kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Nov 28 17:35:13 alpha-pc kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Nov 28 17:35:13 alpha-pc kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Nov 28 17:35:13 alpha-pc kernel: [    0.000000] Processor #0 6:10 APIC version 16
Nov 28 17:35:13 alpha-pc kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Nov 28 17:35:13 alpha-pc kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Nov 28 17:35:13 alpha-pc kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
Nov 28 17:35:13 alpha-pc kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Nov 28 17:35:13 alpha-pc kernel: [    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
Nov 28 17:35:13 alpha-pc kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Nov 28 17:35:13 alpha-pc kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
Nov 28 17:35:13 alpha-pc kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
Nov 28 17:35:13 alpha-pc kernel: [    0.000000] ACPI: IRQ9 used by override.
Nov 28 17:35:13 alpha-pc kernel: [    0.000000] ACPI: IRQ14 used by override.
Nov 28 17:35:13 alpha-pc kernel: [    0.000000] ACPI: IRQ15 used by override.
Nov 28 17:35:13 alpha-pc kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Nov 28 17:35:13 alpha-pc kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Nov 28 17:35:13 alpha-pc kernel: [    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
Nov 28 17:35:13 alpha-pc kernel: [    0.000000] Built 1 zonelists.  Total pages: 260081
Nov 28 17:35:13 alpha-pc kernel: [    0.000000] Kernel command line: root=UUID=7cf890f6-1437-407b-9f45-d233d3a80826 ro quiet splash
Nov 28 17:35:13 alpha-pc kernel: [    0.000000] mapped APIC to ffffd000 (fee00000)
Nov 28 17:35:13 alpha-pc kernel: [    0.000000] mapped IOAPIC to ffffc000 (fec00000)
Nov 28 17:35:13 alpha-pc kernel: [    0.000000] Enabling fast FPU save and restore... done.
Nov 28 17:35:13 alpha-pc kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Nov 28 17:35:13 alpha-pc kernel: [    0.000000] Initializing CPU#0
Nov 28 17:35:13 alpha-pc kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Nov 28 17:35:13 alpha-pc kernel: [    0.000000] Detected 2074.930 MHz processor.
Nov 28 17:35:13 alpha-pc kernel: [   17.027286] Console: colour VGA+ 80x25
Nov 28 17:35:13 alpha-pc kernel: [   17.027858] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Nov 28 17:35:13 alpha-pc kernel: [   17.028335] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Nov 28 17:35:13 alpha-pc kernel: [   17.056391] Memory: 1027880k/1048512k available (2015k kernel code, 19928k reserved, 916k data, 364k init, 131008k highmem)
Nov 28 17:35:13 alpha-pc kernel: [   17.056401] virtual kernel memory layout:
Nov 28 17:35:13 alpha-pc kernel: [   17.056402]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
Nov 28 17:35:13 alpha-pc kernel: [   17.056404]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Nov 28 17:35:13 alpha-pc kernel: [   17.056405]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Nov 28 17:35:13 alpha-pc kernel: [   17.056406]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Nov 28 17:35:13 alpha-pc kernel: [   17.056408]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
Nov 28 17:35:13 alpha-pc kernel: [   17.056409]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
Nov 28 17:35:13 alpha-pc kernel: [   17.056410]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
Nov 28 17:35:13 alpha-pc kernel: [   17.056413] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Nov 28 17:35:13 alpha-pc kernel: [   17.056458] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Nov 28 17:35:13 alpha-pc kernel: [   17.136397] Calibrating delay using timer specific routine.. 4153.00 BogoMIPS (lpj=8306010)
Nov 28 17:35:13 alpha-pc kernel: [   17.136431] Security Framework v1.0.0 initialized
Nov 28 17:35:13 alpha-pc kernel: [   17.136439] SELinux:  Disabled at boot.
Nov 28 17:35:13 alpha-pc kernel: [   17.136454] Mount-cache hash table entries: 512
Nov 28 17:35:13 alpha-pc kernel: [   17.136605] CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
Nov 28 17:35:13 alpha-pc kernel: [   17.136614] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Nov 28 17:35:13 alpha-pc kernel: [   17.136616] CPU: L2 Cache: 512K (64 bytes/line)
Nov 28 17:35:13 alpha-pc kernel: [   17.136619] CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000420 00000000 00000000 00000000
Nov 28 17:35:13 alpha-pc kernel: [   17.136631] Compat vDSO mapped to ffffe000.
Nov 28 17:35:13 alpha-pc kernel: [   17.136644] Checking 'hlt' instruction... OK.
Nov 28 17:35:13 alpha-pc kernel: [   17.152528] SMP alternatives: switching to UP code
Nov 28 17:35:13 alpha-pc kernel: [   17.152808] Freeing SMP alternatives: 11k freed
Nov 28 17:35:13 alpha-pc kernel: [   17.153135] Early unpacking initramfs... done
Nov 28 17:35:13 alpha-pc kernel: [   17.447638] ACPI: Core revision 20070126
Nov 28 17:35:13 alpha-pc kernel: [   17.447733] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Nov 28 17:35:13 alpha-pc kernel: [   17.450662] CPU0: AMD Athlon(tm) XP 2800+ stepping 00
Nov 28 17:35:13 alpha-pc kernel: [   17.450683] Total of 1 processors activated (4153.00 BogoMIPS).
Nov 28 17:35:13 alpha-pc kernel: [   17.450878] ENABLING IO-APIC IRQs
Nov 28 17:35:13 alpha-pc kernel: [   17.451070] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
Nov 28 17:35:13 alpha-pc kernel: [   17.595987] Brought up 1 CPUs
Nov 28 17:35:13 alpha-pc kernel: [   17.596114] Booting paravirtualized kernel on bare hardware
Nov 28 17:35:13 alpha-pc kernel: [   17.596181] Time: 23:34:50  Date: 10/28/107
Nov 28 17:35:13 alpha-pc kernel: [   17.596205] NET: Registered protocol family 16
Nov 28 17:35:13 alpha-pc kernel: [   17.596303] EISA bus registered
Nov 28 17:35:13 alpha-pc kernel: [   17.596316] ACPI: bus type pci registered
Nov 28 17:35:13 alpha-pc kernel: [   17.628289] PCI: PCI BIOS revision 2.10 entry at 0xfbe50, last bus=2
Nov 28 17:35:13 alpha-pc kernel: [   17.628292] PCI: Using configuration type 1
Nov 28 17:35:13 alpha-pc kernel: [   17.628294] Setting up standard PCI resources
Nov 28 17:35:13 alpha-pc kernel: [   17.633319] ACPI: EC: Look up EC in DSDT
Nov 28 17:35:13 alpha-pc kernel: [   17.638139] ACPI: Interpreter enabled
Nov 28 17:35:13 alpha-pc kernel: [   17.638142] ACPI: (supports S0 S1 S4 S5)
Nov 28 17:35:13 alpha-pc kernel: [   17.638157] ACPI: Using IOAPIC for interrupt routing
Nov 28 17:35:13 alpha-pc kernel: [   17.647271] ACPI: PCI Root Bridge [PCI0] (0000:00)
Nov 28 17:35:13 alpha-pc kernel: [   17.647277] PCI: Probing PCI hardware (bus 00)
Nov 28 17:35:13 alpha-pc kernel: [   17.648104] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Nov 28 17:35:13 alpha-pc kernel: [   17.648260] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
Nov 28 17:35:13 alpha-pc kernel: [   17.648513] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
Nov 28 17:35:13 alpha-pc kernel: [   17.697215] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Nov 28 17:35:13 alpha-pc kernel: [   17.697377] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Nov 28 17:35:13 alpha-pc kernel: [   17.697536] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Nov 28 17:35:13 alpha-pc kernel: [   17.697695] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Nov 28 17:35:13 alpha-pc kernel: [   17.697853] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Nov 28 17:35:13 alpha-pc kernel: [   17.698012] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Nov 28 17:35:13 alpha-pc kernel: [   17.698180] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Nov 28 17:35:13 alpha-pc kernel: [   17.698345] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Nov 28 17:35:13 alpha-pc kernel: [   17.698503] ACPI: PCI Interrupt Link [LAPU] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Nov 28 17:35:13 alpha-pc kernel: [   17.698663] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Nov 28 17:35:13 alpha-pc kernel: [   17.698821] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Nov 28 17:35:13 alpha-pc kernel: [   17.698980] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Nov 28 17:35:13 alpha-pc kernel: [   17.699140] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Nov 28 17:35:13 alpha-pc kernel: [   17.699301] ACPI: PCI Interrupt Link [LFIR] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Nov 28 17:35:13 alpha-pc kernel: [   17.699459] ACPI: PCI Interrupt Link [L3CM] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Nov 28 17:35:13 alpha-pc kernel: [   17.699619] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Nov 28 17:35:13 alpha-pc kernel: [   17.699786] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Nov 28 17:35:13 alpha-pc kernel: [   17.699931] ACPI: PCI Interrupt Link [APC1] (IRQs *16)
Nov 28 17:35:13 alpha-pc kernel: [   17.700054] ACPI: PCI Interrupt Link [APC2] (IRQs *17), disabled.
Nov 28 17:35:13 alpha-pc kernel: [   17.700177] ACPI: PCI Interrupt Link [APC3] (IRQs *18), disabled.
Nov 28 17:35:13 alpha-pc kernel: [   17.700299] ACPI: PCI Interrupt Link [APC4] (IRQs *19), disabled.
Nov 28 17:35:13 alpha-pc kernel: [   17.700421] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
Nov 28 17:35:13 alpha-pc kernel: [   17.700597] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21) *0
Nov 28 17:35:13 alpha-pc kernel: [   17.700772] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21) *0
Nov 28 17:35:13 alpha-pc kernel: [   17.700946] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21) *0
Nov 28 17:35:13 alpha-pc kernel: [   17.701119] ACPI: PCI Interrupt Link [APCI] (IRQs 20 21) *0, disabled.
Nov 28 17:35:13 alpha-pc kernel: [   17.701293] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21) *0
Nov 28 17:35:13 alpha-pc kernel: [   17.701466] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21) *0, disabled.
Nov 28 17:35:13 alpha-pc kernel: [   17.701590] ACPI: PCI Interrupt Link [APCS] (IRQs *23)
Nov 28 17:35:13 alpha-pc kernel: [   17.701763] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21) *0
Nov 28 17:35:13 alpha-pc kernel: [   17.701937] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21) *0, disabled.
Nov 28 17:35:13 alpha-pc kernel: [   17.702110] ACPI: PCI Interrupt Link [AP3C] (IRQs 20 21) *0, disabled.
Nov 28 17:35:13 alpha-pc kernel: [   17.702284] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21) *0, disabled.
Nov 28 17:35:13 alpha-pc kernel: [   17.702466] ACPI: PCI Interrupt Link [APSI] (IRQs 22) *0
Nov 28 17:35:13 alpha-pc kernel: [   17.702601] ACPI: Power Resource [ISAV] (on)
Nov 28 17:35:13 alpha-pc kernel: [   17.702618] Linux Plug and Play Support v0.97 (c) Adam Belay
Nov 28 17:35:13 alpha-pc kernel: [   17.702630] pnp: PnP ACPI init
Nov 28 17:35:13 alpha-pc kernel: [   17.702637] ACPI: bus type pnp registered
Nov 28 17:35:13 alpha-pc kernel: [   17.707166] pnp: PnP ACPI: found 15 devices
Nov 28 17:35:13 alpha-pc kernel: [   17.707169] ACPI: ACPI bus type pnp unregistered
Nov 28 17:35:13 alpha-pc kernel: [   17.707173] PnPBIOS: Disabled by ACPI PNP
Nov 28 17:35:13 alpha-pc kernel: [   17.707227] PCI: Using ACPI for IRQ routing
Nov 28 17:35:13 alpha-pc kernel: [   17.707232] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Nov 28 17:35:13 alpha-pc kernel: [   17.744690] NET: Registered protocol family 8
Nov 28 17:35:13 alpha-pc kernel: [   17.744692] NET: Registered protocol family 20
Nov 28 17:35:13 alpha-pc kernel: [   17.744760] pnp: 00:00: ioport range 0x4000-0x407f has been reserved
Nov 28 17:35:13 alpha-pc kernel: [   17.744764] pnp: 00:00: ioport range 0x4080-0x40ff has been reserved
Nov 28 17:35:13 alpha-pc kernel: [   17.744766] pnp: 00:00: ioport range 0x4400-0x447f has been reserved
Nov 28 17:35:13 alpha-pc kernel: [   17.744769] pnp: 00:00: ioport range 0x4480-0x44ff has been reserved
Nov 28 17:35:13 alpha-pc kernel: [   17.744772] pnp: 00:00: ioport range 0x4200-0x427f has been reserved
Nov 28 17:35:13 alpha-pc kernel: [   17.744774] pnp: 00:00: ioport range 0x4280-0x42ff has been reserved
Nov 28 17:35:13 alpha-pc kernel: [   17.744779] pnp: 00:01: ioport range 0x5000-0x503f has been reserved
Nov 28 17:35:13 alpha-pc kernel: [   17.744782] pnp: 00:01: ioport range 0x5100-0x513f has been reserved
Nov 28 17:35:13 alpha-pc kernel: [   17.744786] pnp: 00:02: iomem range 0xd5800-0xd7fff has been reserved
Nov 28 17:35:13 alpha-pc kernel: [   17.744789] pnp: 00:02: iomem range 0xf0000-0xf7fff could not be reserved
Nov 28 17:35:13 alpha-pc kernel: [   17.744792] pnp: 00:02: iomem range 0xf8000-0xfbfff could not be reserved
Nov 28 17:35:13 alpha-pc kernel: [   17.744795] pnp: 00:02: iomem range 0xfc000-0xfffff could not be reserved
Nov 28 17:35:13 alpha-pc kernel: [   17.747789] Time: tsc clocksource has been installed.
Nov 28 17:35:13 alpha-pc kernel: [   17.775079] PCI: Bridge: 0000:00:08.0
Nov 28 17:35:13 alpha-pc kernel: [   17.775081]   IO window: disabled.
Nov 28 17:35:13 alpha-pc kernel: [   17.775086]   MEM window: disabled.
Nov 28 17:35:13 alpha-pc kernel: [   17.775089]   PREFETCH window: disabled.
Nov 28 17:35:13 alpha-pc kernel: [   17.775096] PCI: Bridge: 0000:00:1e.0
Nov 28 17:35:13 alpha-pc kernel: [   17.775098]   IO window: 9000-9fff
Nov 28 17:35:13 alpha-pc kernel: [   17.775102]   MEM window: e4000000-e5ffffff
Nov 28 17:35:13 alpha-pc kernel: [   17.775106]   PREFETCH window: d0000000-dfffffff
Nov 28 17:35:13 alpha-pc kernel: [   17.775117] PCI: Setting latency timer of device 0000:00:08.0 to 64
Nov 28 17:35:13 alpha-pc kernel: [   17.775132] NET: Registered protocol family 2
Nov 28 17:35:13 alpha-pc kernel: [   17.811774] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Nov 28 17:35:13 alpha-pc kernel: [   17.811948] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
Nov 28 17:35:13 alpha-pc kernel: [   17.813918] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Nov 28 17:35:13 alpha-pc kernel: [   17.814674] TCP: Hash tables configured (established 131072 bind 65536)
Nov 28 17:35:13 alpha-pc kernel: [   17.814677] TCP reno registered
Nov 28 17:35:13 alpha-pc kernel: [   17.823849] checking if image is initramfs... it is
Nov 28 17:35:13 alpha-pc kernel: [   18.275264] Switched to high resolution mode on CPU 0
Nov 28 17:35:13 alpha-pc kernel: [   18.384532] Freeing initrd memory: 7061k freed
Nov 28 17:35:13 alpha-pc kernel: [   18.384960] audit: initializing netlink socket (disabled)
Nov 28 17:35:13 alpha-pc kernel: [   18.384974] audit(1196292890.088:1): initialized
Nov 28 17:35:13 alpha-pc kernel: [   18.385039] highmem bounce pool size: 64 pages
Nov 28 17:35:13 alpha-pc kernel: [   18.386790] VFS: Disk quotas dquot_6.5.1
Nov 28 17:35:13 alpha-pc kernel: [   18.386846] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Nov 28 17:35:13 alpha-pc kernel: [   18.386940] io scheduler noop registered
Nov 28 17:35:13 alpha-pc kernel: [   18.386942] io scheduler anticipatory registered
Nov 28 17:35:13 alpha-pc kernel: [   18.386944] io scheduler deadline registered
Nov 28 17:35:13 alpha-pc kernel: [   18.386958] io scheduler cfq registered (default)
Nov 28 17:35:13 alpha-pc kernel: [   18.419071] Boot video device is 0000:01:00.0
Nov 28 17:35:13 alpha-pc kernel: [   18.419234] isapnp: Scanning for PnP cards...
Nov 28 17:35:13 alpha-pc kernel: [   18.773337] isapnp: No Plug & Play device found
Nov 28 17:35:13 alpha-pc kernel: [   18.796133] Real Time Clock Driver v1.12ac
Nov 28 17:35:13 alpha-pc kernel: [   18.796242] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Nov 28 17:35:13 alpha-pc kernel: [   18.796350] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Nov 28 17:35:13 alpha-pc kernel: [   18.796501] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Nov 28 17:35:13 alpha-pc kernel: [   18.797012] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Nov 28 17:35:13 alpha-pc kernel: [   18.797234] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Nov 28 17:35:13 alpha-pc kernel: [   18.797919] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Nov 28 17:35:13 alpha-pc kernel: [   18.798134] input: Macintosh mouse button emulation as /class/input/input0
Nov 28 17:35:13 alpha-pc kernel: [   18.798207] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Nov 28 17:35:13 alpha-pc kernel: [   18.800875] serio: i8042 KBD port at 0x60,0x64 irq 1
Nov 28 17:35:13 alpha-pc kernel: [   18.800882] serio: i8042 AUX port at 0x60,0x64 irq 12
Nov 28 17:35:13 alpha-pc kernel: [   18.801059] mice: PS/2 mouse device common for all mice
Nov 28 17:35:13 alpha-pc kernel: [   18.801169] EISA: Probing bus 0 at eisa.0
Nov 28 17:35:13 alpha-pc kernel: [   18.801193] Cannot allocate resource for EISA slot 4
Nov 28 17:35:13 alpha-pc kernel: [   18.801195] Cannot allocate resource for EISA slot 5
Nov 28 17:35:13 alpha-pc kernel: [   18.801211] EISA: Detected 0 cards.
Nov 28 17:35:13 alpha-pc kernel: [   18.801309] TCP cubic registered
Nov 28 17:35:13 alpha-pc kernel: [   18.801318] NET: Registered protocol family 1
Nov 28 17:35:13 alpha-pc kernel: [   18.801339] Using IPI No-Shortcut mode
Nov 28 17:35:13 alpha-pc kernel: [   18.801509]   Magic number: 15:605:606
Nov 28 17:35:13 alpha-pc kernel: [   18.801617]   hash matches device ptyad
Nov 28 17:35:13 alpha-pc kernel: [   18.802120] Freeing unused kernel memory: 364k freed
Nov 28 17:35:13 alpha-pc kernel: [   18.842656] input: AT Translated Set 2 keyboard as /class/input/input1
Nov 28 17:35:13 alpha-pc kernel: [   19.989577] AppArmor: AppArmor initialized<5>audit(1196292891.588:2):  type=1505 info="AppArmor initialized" pid=1231
Nov 28 17:35:13 alpha-pc kernel: [   20.008055] fuse init (API version 7.8)
Nov 28 17:35:13 alpha-pc kernel: [   20.108595] Failure registering capabilities with primary security module.
Nov 28 17:35:13 alpha-pc kernel: [   20.958974] usbcore: registered new interface driver usbfs
Nov 28 17:35:13 alpha-pc kernel: [   20.959002] usbcore: registered new interface driver hub
Nov 28 17:35:13 alpha-pc kernel: [   20.959027] usbcore: registered new device driver usb
Nov 28 17:35:13 alpha-pc kernel: [   20.959706] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Nov 28 17:35:13 alpha-pc kernel: [   20.960074] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
Nov 28 17:35:13 alpha-pc kernel: [   20.960083] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 21 (level, high) -> IRQ 16
Nov 28 17:35:13 alpha-pc kernel: [   20.960097] PCI: Setting latency timer of device 0000:00:02.0 to 64
Nov 28 17:35:13 alpha-pc kernel: [   20.960101] ohci_hcd 0000:00:02.0: OHCI Host Controller
Nov 28 17:35:13 alpha-pc kernel: [   20.960313] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
Nov 28 17:35:13 alpha-pc kernel: [   20.960332] ohci_hcd 0000:00:02.0: irq 16, io mem 0xe6001000
Nov 28 17:35:13 alpha-pc kernel: [   21.005449] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
Nov 28 17:35:13 alpha-pc kernel: [   21.020029] usb usb1: configuration #1 chosen from 1 choice
Nov 28 17:35:13 alpha-pc kernel: [   21.020062] hub 1-0:1.0: USB hub found
Nov 28 17:35:13 alpha-pc kernel: [   21.020076] hub 1-0:1.0: 4 ports detected
Nov 28 17:35:13 alpha-pc kernel: [   21.061716] SCSI subsystem initialized
Nov 28 17:35:13 alpha-pc kernel: [   21.066522] libata version 2.21 loaded.
Nov 28 17:35:13 alpha-pc kernel: [   21.120620] ACPI: PCI Interrupt Link [APCG] enabled at IRQ 20
Nov 28 17:35:13 alpha-pc kernel: [   21.120631] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCG] -> GSI 20 (level, high) -> IRQ 17
Nov 28 17:35:13 alpha-pc kernel: [   21.120647] PCI: Setting latency timer of device 0000:00:02.1 to 64
Nov 28 17:35:13 alpha-pc kernel: [   21.120651] ohci_hcd 0000:00:02.1: OHCI Host Controller
Nov 28 17:35:13 alpha-pc kernel: [   21.120677] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
Nov 28 17:35:13 alpha-pc kernel: [   21.120697] ohci_hcd 0000:00:02.1: irq 17, io mem 0xe6002000
Nov 28 17:35:13 alpha-pc kernel: [   21.178202] usb usb2: configuration #1 chosen from 1 choice
Nov 28 17:35:13 alpha-pc kernel: [   21.178234] hub 2-0:1.0: USB hub found
Nov 28 17:35:13 alpha-pc kernel: [   21.178246] hub 2-0:1.0: 4 ports detected
Nov 28 17:35:13 alpha-pc kernel: [   21.204180] Floppy drive(s): fd0 is 1.44M
Nov 28 17:35:13 alpha-pc kernel: [   21.244806] FDC 0 is a post-1991 82077
Nov 28 17:35:13 alpha-pc kernel: [   21.281292] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 21
Nov 28 17:35:13 alpha-pc kernel: [   21.281299] ACPI: PCI Interrupt 0000:00:02.2[C] -> Link [APCL] -> GSI 21 (level, high) -> IRQ 16
Nov 28 17:35:13 alpha-pc kernel: [   21.281312] PCI: Setting latency timer of device 0000:00:02.2 to 64
Nov 28 17:35:13 alpha-pc kernel: [   21.281316] ehci_hcd 0000:00:02.2: EHCI Host Controller
Nov 28 17:35:13 alpha-pc kernel: [   21.281353] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
Nov 28 17:35:13 alpha-pc kernel: [   21.281392] ehci_hcd 0000:00:02.2: debug port 1
Nov 28 17:35:13 alpha-pc kernel: [   21.281397] PCI: cache line size of 64 is not supported by device 0000:00:02.2
Nov 28 17:35:13 alpha-pc kernel: [   21.281405] ehci_hcd 0000:00:02.2: irq 16, io mem 0xe6003000
Nov 28 17:35:13 alpha-pc kernel: [   21.281413] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Nov 28 17:35:13 alpha-pc kernel: [   21.281514] usb usb3: configuration #1 chosen from 1 choice
Nov 28 17:35:13 alpha-pc kernel: [   21.281554] hub 3-0:1.0: USB hub found
Nov 28 17:35:13 alpha-pc kernel: [   21.281564] hub 3-0:1.0: 8 ports detected
Nov 28 17:35:13 alpha-pc kernel: [   21.384542] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 20
Nov 28 17:35:13 alpha-pc kernel: [   21.384548] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCH] -> GSI 20 (level, high) -> IRQ 17
Nov 28 17:35:13 alpha-pc kernel: [   21.384555] PCI: Setting latency timer of device 0000:00:04.0 to 64
Nov 28 17:35:13 alpha-pc kernel: [   21.903664] eth0: forcedeth.c: subsystem: 01462:570c bound to 0000:00:04.0
Nov 28 17:35:13 alpha-pc kernel: [   21.908764] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Nov 28 17:35:13 alpha-pc kernel: [   21.908770] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Nov 28 17:35:13 alpha-pc kernel: [   21.910420] NFORCE2-U400R: IDE controller at PCI slot 0000:00:09.0
Nov 28 17:35:13 alpha-pc kernel: [   21.910531] NFORCE2-U400R: chipset revision 163
Nov 28 17:35:13 alpha-pc kernel: [   21.910534] NFORCE2-U400R: not 100%% native mode: will probe irqs later
Nov 28 17:35:13 alpha-pc kernel: [   21.910539] NFORCE2-U400R: BIOS didn't set cable bits correctly. Enabling workaround.
Nov 28 17:35:13 alpha-pc kernel: [   21.910541] NFORCE2-U400R: BIOS didn't set cable bits correctly. Enabling workaround.
Nov 28 17:35:13 alpha-pc kernel: [   21.910548] NFORCE2-U400R: 0000:00:09.0 (rev a3) UDMA133 controller
Nov 28 17:35:13 alpha-pc kernel: [   21.910558]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
Nov 28 17:35:13 alpha-pc kernel: [   21.910570]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
Nov 28 17:35:13 alpha-pc kernel: [   21.910579] Probing IDE interface ide0...
Nov 28 17:35:13 alpha-pc kernel: [   22.199043] hda: Maxtor 4D040H2, ATA DISK drive
Nov 28 17:35:13 alpha-pc kernel: [   22.870647] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Nov 28 17:35:13 alpha-pc kernel: [   22.888316] Probing IDE interface ide1...
Nov 28 17:35:13 alpha-pc kernel: [   23.621487] hdc: LITE-ON DVDRW SOHW-1633S, ATAPI CD/DVD-ROM drive
Nov 28 17:35:13 alpha-pc kernel: [   24.293178] ide1 at 0x170-0x177,0x376 on irq 15
Nov 28 17:35:13 alpha-pc kernel: [   24.293888] sata_nv 0000:00:0b.0: version 3.4
Nov 28 17:35:13 alpha-pc kernel: [   24.294278] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 22
Nov 28 17:35:13 alpha-pc kernel: [   24.294286] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [APSI] -> GSI 22 (level, high) -> IRQ 18
Nov 28 17:35:13 alpha-pc kernel: [   24.294353] PCI: Setting latency timer of device 0000:00:0b.0 to 64
Nov 28 17:35:13 alpha-pc kernel: [   24.294795] scsi0 : sata_nv
Nov 28 17:35:13 alpha-pc kernel: [   24.294988] scsi1 : sata_nv
Nov 28 17:35:13 alpha-pc kernel: [   24.295170] ata1: SATA max UDMA/133 cmd 0x000109f0 ctl 0x00010bf2 bmdma 0x0001b000 irq 18
Nov 28 17:35:13 alpha-pc kernel: [   24.295175] ata2: SATA max UDMA/133 cmd 0x00010970 ctl 0x00010b72 bmdma 0x0001b008 irq 18
Nov 28 17:35:13 alpha-pc kernel: [   24.301988] hda: max request size: 128KiB
Nov 28 17:35:13 alpha-pc kernel: [   24.310898] hda: 80043264 sectors (40982 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
Nov 28 17:35:13 alpha-pc kernel: [   24.310906] hda: cache flushes not supported
Nov 28 17:35:13 alpha-pc kernel: [   24.310957]  hda: hda1 hda2 < hda5 >
Nov 28 17:35:13 alpha-pc kernel: [   24.368784] hdc: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(66)
Nov 28 17:35:13 alpha-pc kernel: [   24.368794] Uniform CD-ROM driver Revision: 3.20
Nov 28 17:35:13 alpha-pc kernel: [   24.604307] ata1: SATA link down (SStatus 0 SControl 300)
Nov 28 17:35:13 alpha-pc kernel: [   24.684125] Attempting manual resume
Nov 28 17:35:13 alpha-pc kernel: [   24.684129] swsusp: Resume From Partition 3:5
Nov 28 17:35:13 alpha-pc kernel: [   24.684131] PM: Checking swsusp image.
Nov 28 17:35:13 alpha-pc kernel: [   24.684309] PM: Resume from disk failed.
Nov 28 17:35:13 alpha-pc kernel: [   24.697965] EXT3-fs: INFO: recovery required on readonly filesystem.
Nov 28 17:35:13 alpha-pc kernel: [   24.697970] EXT3-fs: write access will be enabled during recovery.
Nov 28 17:35:13 alpha-pc kernel: [   24.915956] ata2: SATA link down (SStatus 0 SControl 300)
Nov 28 17:35:13 alpha-pc kernel: [   25.427950] kjournald starting.  Commit interval 5 seconds
Nov 28 17:35:13 alpha-pc kernel: [   25.427966] EXT3-fs: recovery complete.
Nov 28 17:35:13 alpha-pc kernel: [   25.438046] EXT3-fs: mounted filesystem with ordered data mode.
Nov 28 17:35:13 alpha-pc kernel: [   35.151482] Linux agpgart interface v0.102 (c) Dave Jones
Nov 28 17:35:13 alpha-pc kernel: [   35.201932] agpgart: Detected NVIDIA nForce2 chipset
Nov 28 17:35:13 alpha-pc kernel: [   35.206166] agpgart: AGP aperture is 64M @ 0xe0000000
Nov 28 17:35:13 alpha-pc kernel: [   35.272004] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x5000
Nov 28 17:35:13 alpha-pc kernel: [   35.272036] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x5100
Nov 28 17:35:13 alpha-pc kernel: [   35.684724] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Nov 28 17:35:13 alpha-pc kernel: [   35.689067] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Nov 28 17:35:13 alpha-pc kernel: [   36.342530] parport_pc 00:0c: reported by Plug and Play ACPI
Nov 28 17:35:13 alpha-pc kernel: [   36.342589] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Nov 28 17:35:13 alpha-pc kernel: [   36.360572] input: PC Speaker as /class/input/input2
Nov 28 17:35:13 alpha-pc kernel: [   36.531242] logips2pp: Detected unknown logitech mouse model 89
Nov 28 17:35:13 alpha-pc kernel: [   36.762490] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 21
Nov 28 17:35:13 alpha-pc kernel: [   36.762496] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [APCJ] -> GSI 21 (level, high) -> IRQ 16
Nov 28 17:35:13 alpha-pc kernel: [   36.762523] PCI: Setting latency timer of device 0000:00:06.0 to 64
Nov 28 17:35:13 alpha-pc kernel: [   37.005022] input: ImExPS/2 Logitech Explorer Mouse as /class/input/input3
Nov 28 17:35:13 alpha-pc kernel: [   37.082659] intel8x0_measure_ac97_clock: measured 54740 usecs
Nov 28 17:35:13 alpha-pc kernel: [   37.082664] intel8x0: clocking to 47485
Nov 28 17:35:13 alpha-pc kernel: [   37.508548] loop: module loaded
Nov 28 17:35:13 alpha-pc kernel: [   37.549812] lp0: using parport0 (interrupt-driven).
Nov 28 17:35:13 alpha-pc kernel: [   37.648773] Adding 1686784k swap on /dev/hda5.  Priority:-1 extents:1 across:1686784k
Nov 28 17:35:13 alpha-pc kernel: [   38.149329] EXT3 FS on hda1, internal journal
Nov 28 17:35:13 alpha-pc kernel: [   39.436251] input: Power Button (FF) as /class/input/input4
Nov 28 17:35:13 alpha-pc kernel: [   39.440459] ACPI: Power Button (FF) [PWRF]
Nov 28 17:35:13 alpha-pc kernel: [   39.477156] input: Power Button (CM) as /class/input/input5
Nov 28 17:35:13 alpha-pc kernel: [   39.481323] ACPI: Power Button (CM) [PWRB]
Nov 28 17:35:13 alpha-pc kernel: [   39.539820] No dock devices found.
Nov 28 17:35:13 alpha-pc kernel: [   41.112049] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Nov 28 17:35:13 alpha-pc kernel: [   41.112055] apm: overridden by ACPI.
Nov 28 17:35:14 alpha-pc kernel: [   41.426095] vboxdrv: Trying to deactivate the NMI watchdog permanently...
Nov 28 17:35:14 alpha-pc kernel: [   41.426101] vboxdrv: Successfully done.
Nov 28 17:35:14 alpha-pc kernel: [   41.762172] Failure registering capabilities with primary security module.
Nov 28 17:35:17 alpha-pc kernel: [   44.649545] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Nov 28 17:35:17 alpha-pc kernel: [   44.654055] [fglrx] Maximum main memory to use for locked dma buffers: 929 MBytes.
Nov 28 17:35:17 alpha-pc kernel: [   44.654332] [fglrx] module loaded - fglrx 8.37.6 [May 25 2007] on minor 0
Nov 28 17:35:17 alpha-pc kernel: [   44.963430] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
Nov 28 17:35:17 alpha-pc kernel: [   44.963442] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 19
Nov 28 17:35:19 alpha-pc kernel: [   46.904834] NET: Registered protocol family 17
Nov 28 17:35:22 alpha-pc kernel: [   49.582344] [fglrx] Internal AGP support requested, but kernel AGP support active.
Nov 28 17:35:22 alpha-pc kernel: [   49.582351] [fglrx] Have to use kernel AGP support to avoid conflicts.
Nov 28 17:35:22 alpha-pc kernel: [   49.582355] [fglrx] AGP detected, AgpState   = 0x1f00420b (hardware caps of chipset)
Nov 28 17:35:22 alpha-pc kernel: [   49.583093] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
Nov 28 17:35:22 alpha-pc kernel: [   49.583273] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Nov 28 17:35:22 alpha-pc kernel: [   49.583479] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
Nov 28 17:35:22 alpha-pc kernel: [   49.583672] [fglrx] AGP enabled,  AgpCommand = 0x1f004302 (selected caps)
Nov 28 17:35:22 alpha-pc kernel: [   49.591912] [fglrx] total      GART = 67108864
Nov 28 17:35:22 alpha-pc kernel: [   49.591921] [fglrx] free       GART = 51113984
Nov 28 17:35:22 alpha-pc kernel: [   49.591923] [fglrx] max single GART = 51113984
Nov 28 17:35:22 alpha-pc kernel: [   49.591925] [fglrx] total      LFB  = 134217728
Nov 28 17:35:22 alpha-pc kernel: [   49.591927] [fglrx] free       LFB  = 108974080
Nov 28 17:35:22 alpha-pc kernel: [   49.591929] [fglrx] max single LFB  = 108974080
Nov 28 17:35:22 alpha-pc kernel: [   49.591931] [fglrx] total      Inv  = 0
Nov 28 17:35:22 alpha-pc kernel: [   49.591932] [fglrx] free       Inv  = 0
Nov 28 17:35:22 alpha-pc kernel: [   49.591934] [fglrx] max single Inv  = 0
Nov 28 17:35:22 alpha-pc kernel: [   49.591935] [fglrx] total      TIM  = 0
Nov 28 17:35:24 alpha-pc kernel: [   52.060199] NET: Registered protocol family 10
Nov 28 17:35:24 alpha-pc kernel: [   52.060348] lo: Disabled Privacy Extensions
Nov 28 17:35:35 alpha-pc kernel: [   62.583842] eth0: no IPv6 routers present

```

My specs:

Athlon XP 2800+
1 gig ram
Radeon 9500 Pro running 8.37's from the repos (restricted driver manager)
Ubuntu 7.10

---

### Post by criskat777 on 2007-11-28
welcome to the club if you do a search you will be shock to see how many  of us are having the same problem. mine dose it random i my be able to use my PC for 5min to 1hr but you can count on it that it will freeze in a lockup state. To bad to becuse i love Ubuntu, but what good is it if it will lockup freeze when you least expect it. i think it's compiz but what do i know. try turning it of and see if your PC freezes. good luck.

---

### Post by TheOrangePeanut on 2007-11-28
I don't have Compiz running because fglrx doesn't support it.  This is a month old fresh install of Ubuntu.  The only programs I had running BOTH times it froze were Firefox and Pidgin.  I doubt those are the culprits.

---

### Post by criskat777 on 2007-11-28
man, i was about to tell you that almost every time my Pc freezes i am running Firefox

---

### Post by riven0 on 2007-11-28
Are you guys running Gutsy? That could be a problem as a lot of people are having problems with it. It could be your ATI card, though. Try switching to the "ATI" driver and see if it helps any.

From what I know of Gutsy, you can do it without the terminal, but I haven't upgraded, so I only know how to do it through the terminal:

Open terminal and type:** sudo dpkg-reconfigure xserver-xorg**

Keep on hitting enter for the defaults, until you get to the driver area. Choose the "ati" driver by hitting space and then enter. Continue on until you get back to the terminal, then do a CTRL+Alt+Backspace. Not really a solution, but it could stop the freezes.

---

### Post by TheOrangePeanut on 2007-11-28
The "ati" driver actually freezes my computer before I even have time to login.  That's why I use fglrx.

---

### Post by criskat777 on 2007-11-28
Same here if i install ati drivers then i have No effects, no compiz, no 3D Desktop and that is un acceptable. i mean thats what lured me to Linux in the first place. Security as well but you have to admit Ubuntu look very flat with no effect i mean it looks WinBows 95's. yuk:lolflag:

---

