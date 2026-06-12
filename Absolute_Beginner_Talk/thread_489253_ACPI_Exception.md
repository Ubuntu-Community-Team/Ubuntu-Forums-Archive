---
title: "ACPI Exception"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by project4 on 2007-07-01
Hi, I am totally new to Ubuntu and Linux. I have an ACER Aspire 3500 laptop on which I removed windows and installed Ubuntu 7.0.4.

I am experiencing the following issues:
- after around 10 minutes of startup I loose my keyboard... is not responding...
- after a minute or so I loose my mouse and I can then restart the laptop with the power button.

I looked in the log and I see the following (I just copy paste everything). One thing that I am wondering about is what is that ACPI Exception? And are there other strange things going on in the hardware/software? THANKS!

======LOG=====
Jul  1 10:08:07 portos syslogd 1.4.1#20ubuntu4: restart.
Jul  1 10:08:13 portos kernel: [  388.428000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Jul  1 10:08:43 portos kernel: [  418.444000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Jul  1 10:09:13 portos kernel: [  448.460000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Jul  1 10:09:43 portos kernel: [  478.480000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Jul  1 10:10:13 portos kernel: [  508.492000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Jul  1 10:10:43 portos kernel: [  538.508000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Jul  1 10:11:13 portos kernel: [  568.524000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Jul  1 10:11:43 portos kernel: [  598.552000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Jul  1 10:12:13 portos kernel: [  628.560000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Jul  1 10:12:43 portos kernel: [  658.572000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Jul  1 10:13:13 portos kernel: [  688.588000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Jul  1 10:13:43 portos kernel: [  718.608000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Jul  1 10:14:13 portos kernel: [  748.620000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Jul  1 10:17:54 portos syslogd 1.4.1#20ubuntu4: restart.
Jul  1 10:17:54 portos kernel: Inspecting /boot/System.map-2.6.20-15-generic
Jul  1 10:17:55 portos kernel: Loaded 24975 symbols from /boot/System.map-2.6.20-15-generic.
Jul  1 10:17:55 portos kernel: Symbols match kernel version 2.6.20.
Jul  1 10:17:55 portos kernel: No module symbols loaded - kernel modules not enabled. 
Jul  1 10:17:55 portos kernel: [    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
Jul  1 10:17:55 portos kernel: [    0.000000] BIOS-provided physical RAM map:
Jul  1 10:17:55 portos kernel: [    0.000000] sanitize start
Jul  1 10:17:55 portos kernel: [    0.000000] sanitize end
Jul  1 10:17:55 portos kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f400 end: 000000000009f400 type: 1
Jul  1 10:17:55 portos kernel: [    0.000000] copy_e820_map() type is E820_RAM
Jul  1 10:17:55 portos kernel: [    0.000000] copy_e820_map() start: 000000000009f400 size: 0000000000000c00 end: 00000000000a0000 type: 2
Jul  1 10:17:55 portos kernel: [    0.000000] copy_e820_map() start: 00000000000dc000 size: 0000000000024000 end: 0000000000100000 type: 2
Jul  1 10:17:55 portos kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001bcf0000 end: 000000001bdf0000 type: 1
Jul  1 10:17:55 portos kernel: [    0.000000] copy_e820_map() type is E820_RAM
Jul  1 10:17:55 portos kernel: [    0.000000] copy_e820_map() start: 000000001bdf0000 size: 000000000000a000 end: 000000001bdfa000 type: 3
Jul  1 10:17:55 portos kernel: [    0.000000] copy_e820_map() start: 000000001bdfa000 size: 0000000000006000 end: 000000001be00000 type: 4
Jul  1 10:17:55 portos kernel: [    0.000000] copy_e820_map() start: 000000001be00000 size: 0000000004200000 end: 0000000020000000 type: 2
Jul  1 10:17:55 portos kernel: [    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
Jul  1 10:17:55 portos kernel: [    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
Jul  1 10:17:55 portos kernel: [    0.000000] copy_e820_map() start: 00000000fff00000 size: 0000000000100000 end: 0000000100000000 type: 2
Jul  1 10:17:55 portos kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
Jul  1 10:17:55 portos kernel: [    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
Jul  1 10:17:55 portos kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Jul  1 10:17:55 portos kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001bdf0000 (usable)
Jul  1 10:17:55 portos kernel: [    0.000000]  BIOS-e820: 000000001bdf0000 - 000000001bdfa000 (ACPI data)
Jul  1 10:17:55 portos kernel: [    0.000000]  BIOS-e820: 000000001bdfa000 - 000000001be00000 (ACPI NVS)
Jul  1 10:17:55 portos kernel: [    0.000000]  BIOS-e820: 000000001be00000 - 0000000020000000 (reserved)
Jul  1 10:17:55 portos kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Jul  1 10:17:55 portos kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Jul  1 10:17:55 portos kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Jul  1 10:17:55 portos kernel: [    0.000000] 0MB HIGHMEM available.
Jul  1 10:17:55 portos kernel: [    0.000000] 445MB LOWMEM available.
Jul  1 10:17:55 portos kernel: [    0.000000] found SMP MP-table at 000f8180
Jul  1 10:17:55 portos kernel: [    0.000000] Zone PFN ranges:
Jul  1 10:17:55 portos kernel: [    0.000000]   DMA             0 ->     4096
Jul  1 10:17:55 portos kernel: [    0.000000]   Normal       4096 ->   114160
Jul  1 10:17:55 portos kernel: [    0.000000]   HighMem    114160 ->   114160
Jul  1 10:17:55 portos kernel: [    0.000000] early_node_map[1] active PFN ranges
Jul  1 10:17:55 portos kernel: [    0.000000]     0:        0 ->   114160
Jul  1 10:17:55 portos kernel: [    0.000000] DMI present.
Jul  1 10:17:55 portos kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x8008
Jul  1 10:17:55 portos kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jul  1 10:17:55 portos kernel: [    0.000000] Processor #0 6:13 APIC version 20
Jul  1 10:17:55 portos kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jul  1 10:17:55 portos kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Jul  1 10:17:55 portos kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
Jul  1 10:17:55 portos kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jul  1 10:17:55 portos kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jul  1 10:17:55 portos kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
Jul  1 10:17:55 portos kernel: [    0.000000] Detected 1500.080 MHz processor.
Jul  1 10:17:55 portos kernel: [   16.369066] Built 1 zonelists.  Total pages: 113269
Jul  1 10:17:55 portos kernel: [   16.369072] Kernel command line: root=UUID=070e3d13-2759-436a-a3e3-1ba44013255f ro quiet splash
Jul  1 10:17:55 portos kernel: [   16.369268] Enabling fast FPU save and restore... done.
Jul  1 10:17:55 portos kernel: [   16.369271] Enabling unmasked SIMD FPU exception support... done.
Jul  1 10:17:55 portos kernel: [   16.369287] Initializing CPU#0
Jul  1 10:17:55 portos kernel: [   16.369361] PID hash table entries: 2048 (order: 11, 8192 bytes)
Jul  1 10:17:55 portos kernel: [   16.370747] Console: colour VGA+ 80x25
Jul  1 10:17:55 portos kernel: [   16.371140] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Jul  1 10:17:55 portos kernel: [   16.371510] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Jul  1 10:17:55 portos kernel: [   16.389944] Memory: 441408k/456640k available (1992k kernel code, 14676k reserved, 893k data, 328k init, 0k highmem)
Jul  1 10:17:55 portos kernel: [   16.389955] virtual kernel memory layout:
Jul  1 10:17:55 portos kernel: [   16.389957]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
Jul  1 10:17:55 portos kernel: [   16.389958]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Jul  1 10:17:55 portos kernel: [   16.389960]     vmalloc : 0xdc800000 - 0xff7fe000   ( 559 MB)
Jul  1 10:17:55 portos kernel: [   16.389961]     lowmem  : 0xc0000000 - 0xdbdf0000   ( 445 MB)
Jul  1 10:17:55 portos kernel: [   16.389962]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
Jul  1 10:17:55 portos kernel: [   16.389964]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
Jul  1 10:17:55 portos kernel: [   16.389965]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
Jul  1 10:17:55 portos kernel: [   16.389969] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Jul  1 10:17:55 portos kernel: [   16.473274] Calibrating delay using timer specific routine.. 3001.95 BogoMIPS (lpj=6003918)
Jul  1 10:17:55 portos kernel: [   16.473320] Security Framework v1.0.0 initialized
Jul  1 10:17:55 portos kernel: [   16.473329] SELinux:  Disabled at boot.
Jul  1 10:17:55 portos kernel: [   16.473348] Mount-cache hash table entries: 512
Jul  1 10:17:55 portos kernel: [   16.473522] CPU: L1 I cache: 32K, L1 D cache: 32K
Jul  1 10:17:55 portos kernel: [   16.473525] CPU: L2 cache: 1024K
Jul  1 10:17:55 portos kernel: [   16.473540] Compat vDSO mapped to ffffe000.
Jul  1 10:17:55 portos kernel: [   16.473545] Remapping vsyscall page to ffffe000
Jul  1 10:17:55 portos kernel: [   16.473558] Checking 'hlt' instruction... OK.
Jul  1 10:17:55 portos kernel: [   16.489366] SMP alternatives: switching to UP code
Jul  1 10:17:55 portos kernel: [   16.489576] Freeing SMP alternatives: 11k freed
Jul  1 10:17:55 portos kernel: [   16.489778] Early unpacking initramfs... done
Jul  1 10:17:55 portos kernel: [   16.892863] ACPI: Core revision 20060707
Jul  1 10:17:55 portos kernel: [   16.893670] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
Jul  1 10:17:55 portos kernel: [   16.898981] CPU0: Intel(R) Celeron(R) M processor         1.50GHz stepping 08
Jul  1 10:17:55 portos kernel: [   16.899010] Total of 1 processors activated (3001.95 BogoMIPS).
Jul  1 10:17:55 portos kernel: [   16.899115] ENABLING IO-APIC IRQs
Jul  1 10:17:55 portos kernel: [   16.899295] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
Jul  1 10:17:55 portos kernel: [   17.048817] Brought up 1 CPUs
Jul  1 10:17:55 portos kernel: [   17.049093] Booting paravirtualized kernel on bare hardware
Jul  1 10:17:55 portos kernel: [   17.049176] Time:  8:17:27  Date: 06/01/107
Jul  1 10:17:55 portos kernel: [   17.049210] NET: Registered protocol family 16
Jul  1 10:17:55 portos kernel: [   17.049314] EISA bus registered
Jul  1 10:17:55 portos kernel: [   17.049319] ACPI: bus type pci registered
Jul  1 10:17:55 portos kernel: [   17.050627] PCI: PCI BIOS revision 2.10 entry at 0xfd786, last bus=1
Jul  1 10:17:55 portos kernel: [   17.050629] PCI: Using configuration type 1
Jul  1 10:17:55 portos kernel: [   17.050631] Setting up standard PCI resources
Jul  1 10:17:55 portos kernel: [   17.078215] ACPI: Interpreter enabled
Jul  1 10:17:55 portos kernel: [   17.078219] ACPI: Using IOAPIC for interrupt routing
Jul  1 10:17:55 portos kernel: [   17.078605] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jul  1 10:17:55 portos kernel: [   17.079480] Enabling SiS 96x SMBus.
Jul  1 10:17:55 portos kernel: [   17.100463] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 *7 9 10 11)
Jul  1 10:17:55 portos kernel: [   17.100672] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 7 9 10 11)
Jul  1 10:17:55 portos kernel: [   17.100883] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 11) *0, disabled.
Jul  1 10:17:55 portos kernel: [   17.101085] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 7 9 10 11)
Jul  1 10:17:55 portos kernel: [   17.101311] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 *9 10 11)
Jul  1 10:17:55 portos kernel: [   17.101514] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11)
Jul  1 10:17:55 portos kernel: [   17.101722] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11) *0, disabled.
Jul  1 10:17:55 portos kernel: [   17.101923] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 *10 11)
Jul  1 10:17:55 portos kernel: [   17.102275] Linux Plug and Play Support v0.97 (c) Adam Belay
Jul  1 10:17:55 portos kernel: [   17.102287] pnp: PnP ACPI init
Jul  1 10:17:55 portos kernel: [   17.103782] pnp: PnP ACPI: found 9 devices
Jul  1 10:17:55 portos kernel: [   17.103787] PnPBIOS: Disabled by ACPI PNP
Jul  1 10:17:55 portos kernel: [   17.103840] PCI: Using ACPI for IRQ routing
Jul  1 10:17:55 portos kernel: [   17.103843] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Jul  1 10:17:55 portos kernel: [   17.106776] NET: Registered protocol family 8
Jul  1 10:17:55 portos kernel: [   17.106778] NET: Registered protocol family 20
Jul  1 10:17:55 portos kernel: [   17.106934] pnp: 00:04: ioport range 0x8000-0x807f could not be reserved
Jul  1 10:17:55 portos kernel: [   17.106938] pnp: 00:04: ioport range 0x8080-0x80ff has been reserved
Jul  1 10:17:55 portos kernel: [   17.106941] pnp: 00:04: ioport range 0x8100-0x811f has been reserved
Jul  1 10:17:55 portos kernel: [   17.106945] pnp: 00:04: ioport range 0x4d0-0x4d1 has been reserved
Jul  1 10:17:55 portos kernel: [   17.106948] pnp: 00:04: ioport range 0xfe00-0xfe00 has been reserved
Jul  1 10:17:55 portos kernel: [   17.107248] PCI: Ignore bogus resource 6 [0:0] of 0000:01:00.0
Jul  1 10:17:55 portos kernel: [   17.107251] PCI: Bridge: 0000:00:01.0
Jul  1 10:17:55 portos kernel: [   17.107254]   IO window: 9000-9fff
Jul  1 10:17:55 portos kernel: [   17.107260]   MEM window: e2100000-e21fffff
Jul  1 10:17:55 portos kernel: [   17.107264]   PREFETCH window: e8000000-efffffff
Jul  1 10:17:55 portos kernel: [   17.107270] PCI: Bus 2, cardbus bridge: 0000:00:06.0
Jul  1 10:17:55 portos kernel: [   17.107273]   IO window: 00002400-000024ff
Jul  1 10:17:55 portos kernel: [   17.107278]   IO window: 00002800-000028ff
Jul  1 10:17:55 portos kernel: [   17.107282]   PREFETCH window: 30000000-33ffffff
Jul  1 10:17:55 portos kernel: [   17.107287]   MEM window: 34000000-37ffffff
Jul  1 10:17:55 portos kernel: [   17.107311] PCI: Enabling device 0000:00:06.0 (0000 -> 0003)
Jul  1 10:17:55 portos kernel: [   17.107318] ACPI: PCI Interrupt 0000:00:06.0[A] -> GSI 19 (level, low) -> IRQ 16
Jul  1 10:17:55 portos kernel: [   17.107350] NET: Registered protocol family 2
Jul  1 10:17:55 portos kernel: [   17.140772] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
Jul  1 10:17:55 portos kernel: [   17.140864] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
Jul  1 10:17:55 portos kernel: [   17.140981] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
Jul  1 10:17:55 portos kernel: [   17.141050] TCP: Hash tables configured (established 16384 bind 8192)
Jul  1 10:17:55 portos kernel: [   17.141053] TCP reno registered
Jul  1 10:17:55 portos kernel: [   17.152817] checking if image is initramfs... it is
Jul  1 10:17:55 portos kernel: [   17.943711] Freeing initrd memory: 6996k freed
Jul  1 10:17:55 portos kernel: [   17.944314] audit: initializing netlink socket (disabled)
Jul  1 10:17:55 portos kernel: [   17.944333] audit(1183277847.628:1): initialized
Jul  1 10:17:55 portos kernel: [   17.944489] VFS: Disk quotas dquot_6.5.1
Jul  1 10:17:55 portos kernel: [   17.944516] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jul  1 10:17:55 portos kernel: [   17.944577] io scheduler noop registered
Jul  1 10:17:55 portos kernel: [   17.944580] io scheduler anticipatory registered
Jul  1 10:17:55 portos kernel: [   17.944583] io scheduler deadline registered
Jul  1 10:17:55 portos kernel: [   17.944595] io scheduler cfq registered (default)
Jul  1 10:17:55 portos kernel: [   18.391816] isapnp: Scanning for PnP cards...
Jul  1 10:17:55 portos kernel: [   18.745143] isapnp: No Plug & Play device found
Jul  1 10:17:55 portos kernel: [   18.782207] Real Time Clock Driver v1.12ac
Jul  1 10:17:55 portos kernel: [   18.782271] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Jul  1 10:17:55 portos kernel: [   18.783193] PCI: Enabling device 0000:00:02.6 (0000 -> 0001)
Jul  1 10:17:55 portos kernel: [   18.783209] ACPI: PCI Interrupt 0000:00:02.6[C] -> GSI 18 (level, low) -> IRQ 17
Jul  1 10:17:55 portos kernel: [   18.783264] ACPI: PCI interrupt for device 0000:00:02.6 disabled
Jul  1 10:17:55 portos kernel: [   18.783354] mice: PS/2 mouse device common for all mice
Jul  1 10:17:55 portos kernel: [   18.783939] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Jul  1 10:17:55 portos kernel: [   18.784221] input: Macintosh mouse button emulation as /class/input/input0
Jul  1 10:17:55 portos kernel: [   18.784260] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Jul  1 10:17:55 portos kernel: [   18.784265] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Jul  1 10:17:55 portos kernel: [   18.784521] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jul  1 10:17:55 portos kernel: [   18.787281] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul  1 10:17:55 portos kernel: [   18.787288] serio: i8042 AUX port at 0x60,0x64 irq 12
Jul  1 10:17:55 portos kernel: [   18.787439] EISA: Probing bus 0 at eisa.0
Jul  1 10:17:55 portos kernel: [   18.787449] Cannot allocate resource for EISA slot 1
Jul  1 10:17:55 portos kernel: [   18.787452] Cannot allocate resource for EISA slot 2
Jul  1 10:17:55 portos kernel: [   18.787473] Cannot allocate resource for EISA slot 8
Jul  1 10:17:55 portos kernel: [   18.787475] EISA: Detected 0 cards.
Jul  1 10:17:55 portos kernel: [   18.817567] TCP cubic registered
Jul  1 10:17:55 portos kernel: [   18.817577] NET: Registered protocol family 1
Jul  1 10:17:55 portos kernel: [   18.817604] Using IPI No-Shortcut mode
Jul  1 10:17:55 portos kernel: [   18.817676] ACPI: (supports S0 S3 S4 S5)
Jul  1 10:17:55 portos kernel: [   18.817720]   Magic number: 15:644:269
Jul  1 10:17:55 portos kernel: [   18.817770]   hash matches device ttyue
Jul  1 10:17:55 portos kernel: [   18.818193] Freeing unused kernel memory: 328k freed
Jul  1 10:17:55 portos kernel: [   18.819202] Time: tsc clocksource has been installed.
Jul  1 10:17:55 portos kernel: [   18.834371] input: AT Translated Set 2 keyboard as /class/input/input1
Jul  1 10:17:55 portos kernel: [   20.060163] Capability LSM initialized
Jul  1 10:17:55 portos kernel: [   20.098397] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Jul  1 10:17:55 portos kernel: [   20.098407] ACPI: Processor [CPU0] (supports 8 throttling states)
Jul  1 10:17:55 portos kernel: [   20.098416] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
Jul  1 10:17:55 portos kernel: [   20.101648] ACPI: Thermal Zone [THRM] (58 C)
Jul  1 10:17:55 portos kernel: [   20.514071] SCSI subsystem initialized
Jul  1 10:17:55 portos kernel: [   20.523868] ACPI: PCI Interrupt 0000:00:02.5[A] -> GSI 16 (level, low) -> IRQ 18
Jul  1 10:17:55 portos kernel: [   20.523942] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011000 irq 14
Jul  1 10:17:55 portos kernel: [   20.523971] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011008 irq 15
Jul  1 10:17:55 portos kernel: [   20.523988] scsi0 : pata_sis
Jul  1 10:17:55 portos kernel: [   20.552673] usbcore: registered new interface driver usbfs
Jul  1 10:17:55 portos kernel: [   20.552699] usbcore: registered new interface driver hub
Jul  1 10:17:55 portos kernel: [   20.552721] usbcore: registered new device driver usb
Jul  1 10:17:55 portos kernel: [   20.620683] sis900.c: v1.08.10 Apr. 2 2006
Jul  1 10:17:55 portos kernel: [   20.686063] ata1.00: ata_hpa_resize 1: sectors = 117210240, hpa_sectors = 117210240
Jul  1 10:17:55 portos kernel: [   20.686070] ata1.00: ATA-6: IC25N060ATMR04-0, MO3OAD4A, max UDMA/100
Jul  1 10:17:55 portos kernel: [   20.686073] ata1.00: 117210240 sectors, multi 16: LBA48 
Jul  1 10:17:55 portos kernel: [   20.694083] ata1.00: ata_hpa_resize 1: sectors = 117210240, hpa_sectors = 117210240
Jul  1 10:17:55 portos kernel: [   20.694089] ata1.00: configured for UDMA/100
Jul  1 10:17:55 portos kernel: [   20.694105] scsi1 : pata_sis
Jul  1 10:17:55 portos kernel: [    3.864000] Time: acpi_pm clocksource has been installed.
Jul  1 10:17:55 portos kernel: [    4.116000] ata2.00: ATAPI, max UDMA/33
Jul  1 10:17:55 portos kernel: [    4.284000] ata2.00: configured for UDMA/33
Jul  1 10:17:55 portos kernel: [    4.284000] scsi 0:0:0:0: Direct-Access     ATA      IC25N060ATMR04-0 MO3O PQ: 0 ANSI: 5
Jul  1 10:17:55 portos kernel: [    4.284000] scsi 1:0:0:0: CD-ROM            MATSHITA UJ-840D          1.00 PQ: 0 ANSI: 5
Jul  1 10:17:55 portos kernel: [    4.292000] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 19
Jul  1 10:17:55 portos kernel: [    4.292000] ohci_hcd 0000:00:03.0: OHCI Host Controller
Jul  1 10:17:55 portos kernel: [    4.292000] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
Jul  1 10:17:55 portos kernel: [    4.292000] ohci_hcd 0000:00:03.0: irq 19, io mem 0xe2000000
Jul  1 10:17:55 portos kernel: [    4.304000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
Jul  1 10:17:55 portos kernel: [    4.304000] sda: Write Protect is off
Jul  1 10:17:55 portos kernel: [    4.304000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul  1 10:17:55 portos kernel: [    4.304000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
Jul  1 10:17:55 portos kernel: [    4.304000] sda: Write Protect is off
Jul  1 10:17:55 portos kernel: [    4.304000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul  1 10:17:55 portos kernel: [    4.304000]  sda: sda1 sda2 <<6>usb usb1: configuration #1 chosen from 1 choice
Jul  1 10:17:55 portos kernel: [    4.352000] hub 1-0:1.0: USB hub found
Jul  1 10:17:55 portos kernel: [    4.352000] hub 1-0:1.0: 3 ports detected
Jul  1 10:17:55 portos kernel: [    4.360000]  sda5 >
Jul  1 10:17:55 portos kernel: [    4.360000] sd 0:0:0:0: Attached scsi disk sda
Jul  1 10:17:55 portos kernel: [    4.368000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jul  1 10:17:55 portos kernel: [    4.368000] scsi 1:0:0:0: Attached scsi generic sg1 type 5
Jul  1 10:17:55 portos kernel: [    4.372000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Jul  1 10:17:55 portos kernel: [    4.372000] Uniform CD-ROM driver Revision: 3.20
Jul  1 10:17:55 portos kernel: [    4.456000] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 20
Jul  1 10:17:55 portos kernel: [    4.456000] ohci_hcd 0000:00:03.1: OHCI Host Controller
Jul  1 10:17:55 portos kernel: [    4.456000] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
Jul  1 10:17:55 portos kernel: [    4.456000] ohci_hcd 0000:00:03.1: irq 20, io mem 0xe2001000
Jul  1 10:17:55 portos kernel: [    4.516000] usb usb2: configuration #1 chosen from 1 choice
Jul  1 10:17:55 portos kernel: [    4.516000] hub 2-0:1.0: USB hub found
Jul  1 10:17:55 portos kernel: [    4.516000] hub 2-0:1.0: 3 ports detected
Jul  1 10:17:55 portos kernel: [    4.576000] Attempting manual resume
Jul  1 10:17:55 portos kernel: [    4.588000] EXT3-fs: INFO: recovery required on readonly filesystem.
Jul  1 10:17:55 portos kernel: [    4.592000] EXT3-fs: write access will be enabled during recovery.
Jul  1 10:17:55 portos kernel: [    4.620000] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 23 (level, low) -> IRQ 21
Jul  1 10:17:55 portos kernel: [    4.620000] ehci_hcd 0000:00:03.3: EHCI Host Controller
Jul  1 10:17:55 portos kernel: [    4.620000] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 3
Jul  1 10:17:55 portos kernel: [    4.620000] ehci_hcd 0000:00:03.3: irq 21, io mem 0xe2002000
Jul  1 10:17:55 portos kernel: [    4.620000] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jul  1 10:17:55 portos kernel: [    4.620000] usb usb3: configuration #1 chosen from 1 choice
Jul  1 10:17:55 portos kernel: [    4.620000] hub 3-0:1.0: USB hub found
Jul  1 10:17:55 portos kernel: [    4.620000] hub 3-0:1.0: 6 ports detected
Jul  1 10:17:55 portos kernel: [    4.724000] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 16
Jul  1 10:17:55 portos kernel: [    4.728000] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 13.
Jul  1 10:17:55 portos kernel: [    4.732000] 0000:00:04.0: Using transceiver found at address 13 as default
Jul  1 10:17:55 portos kernel: [    4.736000] eth0: SiS 900 PCI Fast Ethernet at 0x2000, IRQ 16, 00:c0:9f:ac:bb:a1.
Jul  1 10:17:55 portos kernel: [    7.316000] kjournald starting.  Commit interval 5 seconds
Jul  1 10:17:55 portos kernel: [    7.316000] EXT3-fs: recovery complete.
Jul  1 10:17:55 portos kernel: [    7.316000] EXT3-fs: mounted filesystem with ordered data mode.
Jul  1 10:17:55 portos kernel: [   19.744000] NET: Registered protocol family 17
Jul  1 10:17:55 portos kernel: [   19.916000] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x8100
Jul  1 10:17:55 portos kernel: [   20.072000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul  1 10:17:55 portos kernel: [   20.076000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jul  1 10:17:55 portos kernel: [   20.076000] ath_hal: module license 'Proprietary' taints kernel.
Jul  1 10:17:55 portos kernel: [   20.080000] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
Jul  1 10:17:55 portos kernel: [   20.192000] wlan: 0.8.4.2 (0.9.3)
Jul  1 10:17:55 portos kernel: [   20.224000] ath_pci: 0.9.4.5 (0.9.3)
Jul  1 10:17:55 portos kernel: [   20.224000] PCI: Enabling device 0000:00:0b.0 (0010 -> 0012)
Jul  1 10:17:55 portos kernel: [   20.224000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 17 (level, low) -> IRQ 22
Jul  1 10:17:55 portos kernel: [   20.228000] eth0: Media Link On 10mbps half-duplex 
Jul  1 10:17:55 portos kernel: [   20.880000] input: PC Speaker as /class/input/input2
Jul  1 10:17:55 portos kernel: [   20.988000] Linux agpgart interface v0.102 (c) Dave Jones
Jul  1 10:17:55 portos kernel: [   21.020000] ath_rate_sample: 1.2 (0.9.3)
Jul  1 10:17:55 portos kernel: [   21.020000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
Jul  1 10:17:55 portos kernel: [   21.020000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
Jul  1 10:17:55 portos kernel: [   21.020000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
Jul  1 10:17:55 portos kernel: [   21.020000] wifi0: mac 7.8 phy 4.5 radio 5.6
Jul  1 10:17:55 portos kernel: [   21.020000] wifi0: Use hw queue 1 for WME_AC_BE traffic
Jul  1 10:17:55 portos kernel: [   21.020000] wifi0: Use hw queue 0 for WME_AC_BK traffic
Jul  1 10:17:55 portos kernel: [   21.020000] wifi0: Use hw queue 2 for WME_AC_VI traffic
Jul  1 10:17:55 portos kernel: [   21.020000] wifi0: Use hw queue 3 for WME_AC_VO traffic
Jul  1 10:17:55 portos kernel: [   21.020000] wifi0: Use hw queue 8 for CAB traffic
Jul  1 10:17:55 portos kernel: [   21.020000] wifi0: Use hw queue 9 for beacons
Jul  1 10:17:55 portos kernel: [   21.060000] wifi0: Atheros 5212: mem=0xe2010000, irq=22
Jul  1 10:17:55 portos kernel: [   21.060000] Yenta: CardBus bridge found at 0000:00:06.0 [1025:0082]
Jul  1 10:17:55 portos kernel: [   21.060000] Yenta: Using CSCINT to route CSC interrupts to PCI
Jul  1 10:17:55 portos kernel: [   21.060000] Yenta: Routing CardBus interrupts to PCI
Jul  1 10:17:55 portos kernel: [   21.060000] Yenta TI: socket 0000:00:06.0, mfunc 0x00521d22, devctl 0x64
Jul  1 10:17:55 portos kernel: [   21.076000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x126eb1, caps: 0xa04713/0x4000
Jul  1 10:17:55 portos kernel: [   21.112000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
Jul  1 10:17:55 portos kernel: [   21.336000] Yenta: ISA IRQ mask 0x06f8, PCI irq 16
Jul  1 10:17:55 portos kernel: [   21.336000] Socket status: 30000006
Jul  1 10:17:55 portos kernel: [   21.336000] agpgart: Detected SiS 661 chipset
Jul  1 10:17:55 portos kernel: [   21.340000] agpgart: AGP aperture is 32M @ 0xe0000000
Jul  1 10:17:55 portos kernel: [   21.496000] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 17
Jul  1 10:17:55 portos kernel: [   21.888000] cs: IO port probe 0x100-0x3af: clean.
Jul  1 10:17:55 portos kernel: [   21.892000] cs: IO port probe 0x3e0-0x4ff: excluding 0x480-0x48f
Jul  1 10:17:55 portos kernel: [   21.892000] cs: IO port probe 0x820-0x8ff: clean.
Jul  1 10:17:55 portos kernel: [   21.892000] cs: IO port probe 0xc00-0xcf7: clean.
Jul  1 10:17:55 portos kernel: [   21.892000] cs: IO port probe 0xa00-0xaff: clean.
Jul  1 10:17:55 portos kernel: [   22.316000] intel8x0_measure_ac97_clock: measured 55477 usecs
Jul  1 10:17:55 portos kernel: [   22.316000] intel8x0: clocking to 48000
Jul  1 10:17:55 portos kernel: [   22.484000] fuse init (API version 7.8)
Jul  1 10:17:55 portos kernel: [   22.528000] lp: driver loaded but no devices found
Jul  1 10:17:55 portos kernel: [   22.556000] Adding 1309256k swap on /dev/disk/by-uuid/9eca3ecf-87bd-4f89-b9fa-53d8ee4a8844.  Priority:-1 extents:1 across:1309256k
Jul  1 10:17:55 portos kernel: [   22.692000] EXT3 FS on sda1, internal journal
Jul  1 10:17:55 portos kernel: [   23.244000] NET: Registered protocol family 10
Jul  1 10:17:55 portos kernel: [   23.244000] lo: Disabled Privacy Extensions
Jul  1 10:17:55 portos kernel: [   27.060000] ACPI: Battery Slot [BAT1] (battery present)
Jul  1 10:17:55 portos kernel: [   27.124000] ACPI: AC Adapter [ACAD] (on-line)
Jul  1 10:17:55 portos kernel: [   27.160000] No dock devices found.
Jul  1 10:17:55 portos kernel: [   27.180000] Using specific hotkey driver
Jul  1 10:17:55 portos kernel: [   27.256000] input: Power Button (FF) as /class/input/input4
Jul  1 10:17:55 portos kernel: [   27.260000] ACPI: Power Button (FF) [PWRF]
Jul  1 10:17:55 portos kernel: [   27.300000] input: Lid Switch as /class/input/input5
Jul  1 10:17:55 portos kernel: [   27.304000] ACPI: Lid Switch [LID]
Jul  1 10:17:55 portos kernel: [   27.340000] input: Power Button (CM) as /class/input/input6
Jul  1 10:17:55 portos kernel: [   27.344000] ACPI: Power Button (CM) [PWRB]
Jul  1 10:17:55 portos kernel: [   27.380000] input: Sleep Button (CM) as /class/input/input7
Jul  1 10:17:55 portos kernel: [   27.384000] ACPI: Sleep Button (CM) [SLPB]
Jul  1 10:17:55 portos kernel: [   27.440000] pcc_acpi: loading...
Jul  1 10:17:57 portos kernel: [   30.348000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Jul  1 10:17:57 portos kernel: [   30.364000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Jul  1 10:17:57 portos kernel: [   30.396000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Jul  1 10:17:57 portos dhcdbd: Started up.
Jul  1 10:17:58 portos dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul  1 10:17:58 portos dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul  1 10:17:59 portos kernel: [   32.832000] ppdev: user-space parallel port driver
Jul  1 10:18:00 portos hpiod: 1.7.3 accepting connections at 2208... 
Jul  1 10:18:01 portos kernel: [   34.468000] apm: BIOS not found.
Jul  1 10:18:02 portos dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Jul  1 10:18:02 portos dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jul  1 10:18:02 portos dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Jul  1 10:18:25 portos kernel: [   58.316000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Jul  1 10:18:35 portos kernel: [   68.816000] c01727b1
Jul  1 10:18:35 portos kernel: [   68.816000] Modules linked in: binfmt_misc ppdev cpufreq_conservative cpufreq_userspace cpufreq_stats cpufreq_ondemand freq_table cpufreq_powersave dev_acpi sony_acpi pcc_acpi tc1100_wmi container button video asus_acpi dock ac backlight battery sbs i2c_ec ipv6 parport_pc lp parport fuse pcmcia joydev snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd wlan_scan_sta sis_agp ath_rate_sample serio_raw soundcore snd_page_alloc agpgart yenta_socket rsrc_nonstatic pcmcia_core pcspkr ath_pci wlan ath_hal(P) shpchp pci_hotplug psmouse i2c_sis96x af_packet i2c_core evdev tsdev ext3 jbd mbcache sg sr_mod cdrom sd_mod generic sis5513 sis900 mii ehci_hcd ohci_hcd usbcore pata_sis ata_generic libata scsi_mod thermal processor fan fbcon tileblit font bitblit softcursor vesafb capability commoncap
Jul  1 10:18:55 portos kernel: [   68.816000]  ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Jul  1 10:19:25 portos kernel: [  118.348000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Jul  1 10:19:55 portos kernel: [  148.364000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Jul  1 10:20:25 portos kernel: [  178.408000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Jul  1 10:20:55 portos kernel: [  208.396000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Jul  1 10:21:25 portos kernel: [  238.412000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Jul  1 10:21:55 portos kernel: [  268.428000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Jul  1 10:22:25 portos kernel: [  298.444000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Jul  1 10:22:55 portos kernel: [  328.464000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Jul  1 10:23:25 portos kernel: [  358.476000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Jul  1 10:23:55 portos kernel: [  388.492000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Jul  1 10:24:25 portos kernel: [  418.508000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Jul  1 10:24:55 portos kernel: [  448.524000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Jul  1 10:25:25 portos kernel: [  478.540000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Jul  1 10:36:06 portos syslogd 1.4.1#20ubuntu4: restart.
============END LOG===============

---

### Post by likemindead on 2007-09-01
I'm having the ***exact same*** issues with my Acer Aspire 3003LCi !!!

Anyone? Thanks in advance....

---

### Post by jvalph on 2007-09-04
Exactly the same issue here on Acer Aspire 3002WLMi. Any suggestions would be greatly appreciated!

UPDATE - Well, removing the battery (barely capable of holding any charge) stopped the error messages and so far no more freezes... So I guess this would be a hardware issue? Will a new battery resolve it?

---

