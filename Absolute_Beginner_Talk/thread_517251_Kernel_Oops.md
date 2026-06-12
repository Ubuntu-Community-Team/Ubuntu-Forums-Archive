---
title: "Kernel Oops"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by jw5801 on 2007-08-04
Not sure where I should put this so it can go here as it tends to get the most traffic.

I'm running a Dell Inspiron 1501 laptop, with Ubuntu Feisty AMD64 (Kernel 2.6.20-16-generic). I'm not entirely sure why, nor do I have any idea how to find out why, but I've been getting kernel oops messages output to terminal every now and again. The term message reads as follows:
```
Message from syslogd@jw5801-laptop at Sat Aug  4 22:41:48 2007 ...
jw5801-laptop kernel: [ 4502.077177] Oops: 0002 [1] SMP 

Message from syslogd@jw5801-laptop at Sat Aug  4 22:41:48 2007 ...
jw5801-laptop kernel: [ 4502.077688] CR2: 0000000000000018
```
After the message is output my wireless network card freezes, any programs that are open continue to run ok, but I can't open any new programs, nor can I open the power menu to reboot. In order to restart and get functionality back, I must either do a hard reset or shutdown via command line (ctrl+alt+F1). This was happening rarely (once every 5 or 6 days, usually when the laptop had been left on for a length of time), I then decided I would try to get rid of the APIC Timing error that had been appearing at startup by adding the "noapic" command to startup, and now the oops is occurring much more often (3 times in the last 4 hours). I have removed the "noapic" command but I'd still like to find out what is causing this error so that I can fix it.

I realise that I haven't included all that much info so if there's anything else that might help let me know and I'll post it, but I'm still new at this and I'm not quite sure where to start looking for what might cause this error. Any help will be greatly appreciated!

---

### Post by apswartz on 2007-08-04
You might want to install another kernel -- say, a generic 386 -- and see how that does. (Trying to eliminate possibilities). If errors persist it might be a hardware problem of some type.

Have you had your laptop long?

How long have you been running linux on it?

Did the problem occur after a kernel upgrade, or did it just start?

---

### Post by jw5801 on 2007-08-05
I've had the laptop for about a month and a half now, and been running linux on it for that long. I don't think I've upgraded the kernel although I do have 2 listed in grub, so it's possible that I did at one point. When I get a chance I'll run a memtest to check out that avenue although since I removed the "noapic" boot option, I haven't had the issue again (I just get an annoying error that flashes on the screen during bootup, well it's not that annoying as it's only there for like 5 seconds, but I don't like errors!)
Thanks for the response! I'll report back with the results of memtest or if I get the oops again.

---

### Post by fimbulvetr on 2007-08-05
The most important thing you can do is get an output of dmesg.

Keep terminal open and type

```
dmesg
```

After this happens. Save the output. Paste it here.

---

### Post by jw5801 on 2007-08-06
I'm not sure if it actually did it again this time (didn't have any open terminal windows for syslog to output into), but I could no longer run any new processes from terminal (would just hang). Ran dmesg and the last few lines read as follows:
```
[  169.388241] APIC error on CPU0: 00(40)
[  183.943433] APIC error on CPU0: 40(40)
[  218.918852] APIC error on CPU0: 40(40)
[  274.290817] APIC error on CPU0: 40(40)
```

---

### Post by jw5801 on 2007-08-07
Here is the complete dmesg output if anyone feels like digging through it. I'm not getting an oops anymore (I only got that when I added the "noapic" boot command) but I'm still getting errors and losing functionality.

```
[    0.000000] Linux version 2.6.20-16-generic (root@king) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 19:00:28 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] Command line: root=UUID=803ab468-dd4c-4afe-bbab-494bb6425500 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ce000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000037e70000 (usable)
[    0.000000]  BIOS-e820: 0000000037e70000 - 0000000037e80000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000037e80000 - 0000000037f00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000037f00000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 157) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 228976) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x00000000000f8500
[    0.000000] ACPI: RSDT (v001 DELL    M08     0x06040000  LTP 0x00000000) @ 0x0000000037e795b4
[    0.000000] ACPI: FADT (v001 ATI    Bowfin   0x06040000 ATI  0x000f4240) @ 0x0000000037e7fbd2
[    0.000000] ACPI: TCPA (v002 AMD             0x06040000 PTEC 0x00000000) @ 0x0000000037e7fc46
[    0.000000] ACPI: SSDT (v001 PTLTD  POWERNOW 0x06040000  LTP 0x00000001) @ 0x0000000037e7fc78
[    0.000000] ACPI: MADT (v001 PTLTD  	 APIC   0x06040000  LTP 0x00000000) @ 0x0000000037e7fdfa
[    0.000000] ACPI: MCFG (v001 PTLTD    MCFG   0x06040000  LTP 0x00000000) @ 0x0000000037e7fe4e
[    0.000000] ACPI: SLIC (v001 DELL    M08     0x06040000  LTP 0x00000000) @ 0x0000000037e7fe8a
[    0.000000] ACPI: DSDT (v001    ATI    SB600 0x06040000 MSFT 0x03000000) @ 0x0000000000000000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] Number of nodes 1
[    0.000000] Node 0 MemBase 0000000000000000 Limit 0000000037e70000
[    0.000000] Entering add_active_range(0, 0, 157) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 228976) 1 entries of 3200 used
[    0.000000] NUMA: Using 63 for the hash shift.
[    0.000000] Using node hash shift of 63
[    0.000000] Bootmem setup node 0 0000000000000000-0000000037e70000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      157
[    0.000000]     0:      256 ->   228976
[    0.000000] On node 0 totalpages: 228877
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1087 pages reserved
[    0.000000]   DMA zone: 2854 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 3074 pages used for memmap
[    0.000000]   DMA32 zone: 221806 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to physical flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Nosave address range: 000000000009d000 - 000000000009e000
[    0.000000] Nosave address range: 000000000009e000 - 00000000000a0000
[    0.000000] Nosave address range: 00000000000a0000 - 00000000000ce000
[    0.000000] Nosave address range: 00000000000ce000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34048 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 224660
[    0.000000] Kernel command line: root=UUID=803ab468-dd4c-4afe-bbab-494bb6425500 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[   16.215768] Console: colour VGA+ 80x25
[   16.216295] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   16.217111] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   16.217389] Checking aperture...
[   16.217394] CPU 0: aperture @ 7990000000 size 32 MB
[   16.217396] Aperture too small (32 MB)
[   16.228010] No AGP bridge found
[   16.236764] Memory: 889916k/915904k available (2217k kernel code, 25592k reserved, 1162k data, 304k init)
[   16.316793] Calibrating delay using timer specific routine.. 3195.09 BogoMIPS (lpj=6390182)
[   16.316859] Security Framework v1.0.0 initialized
[   16.316864] SELinux:  Disabled at boot.
[   16.316891] Mount-cache hash table entries: 256
[   16.317045] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   16.317049] CPU: L2 Cache: 256K (64 bytes/line)
[   16.317052] CPU 0/0 -> Node 0
[   16.317055] CPU: Physical Processor ID: 0
[   16.317056] CPU: Processor Core ID: 0
[   16.317080] SMP alternatives: switching to UP code
[   16.317359] Early unpacking initramfs... done
[   16.690476] ACPI: Core revision 20060707
[   16.693621] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   17.771005] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   17.811056] Using local APIC timer interrupts.
[   17.873657] result 12469223
[   17.873659] Detected 12.469 MHz APIC timer.
[   17.875675] SMP alternatives: switching to SMP code
[   17.875807] Booting processor 1/2 APIC 0x1
[   17.886305] Initializing CPU#1
[   17.963577] Calibrating delay using timer specific routine.. 3192.24 BogoMIPS (lpj=6384493)
[   17.963584] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   17.963587] CPU: L2 Cache: 256K (64 bytes/line)
[   17.963590] CPU 1/1 -> Node 0
[   17.963592] CPU: Physical Processor ID: 0
[   17.963594] CPU: Processor Core ID: 1
[   17.963665] AMD Turion(tm) 64 X2 Mobile Technology TL-50 stepping 02
[   17.967590] CPU 1: Syncing TSC to CPU 0.
[   17.967459] CPU 1: synchronized TSC with CPU 0 (last diff -2 cycles, maxerr 477 cycles)
[   17.967475] Brought up 2 CPUs
[   17.967522] Disabling vsyscall due to use of PM timer
[   17.967525] time.c: Using 3.579545 MHz WALL PM GTOD PM timer.
[   17.967528] time.c: Detected 1596.059 MHz processor.
[   18.015759] migration_cost=132
[   18.016149] Time:  7:04:00  Date: 07/07/107
[   18.016195] NET: Registered protocol family 16
[   18.016293] ACPI: bus type pci registered
[   18.016300] PCI: Using configuration type 1
[   18.023035] ACPI: Interpreter enabled
[   18.023040] ACPI: Using IOAPIC for interrupt routing
[   18.023656] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   18.023662] PCI: Probing PCI hardware (bus 00)
[   18.025757] Boot video device is 0000:01:05.0
[   18.026322] PCI: Transparent bridge - 0000:00:14.4
[   18.026369] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   18.030939] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT]
[   18.031275] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
[   18.033468] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[   18.033767] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[   18.034061] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[   18.034358] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[   18.034651] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[   18.034945] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[   18.035240] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[   18.035558] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[   18.035853] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 5 7) *0, disabled.
[   18.041474] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   18.041773] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   18.044229] Linux Plug and Play Support v0.97 (c) Adam Belay
[   18.044242] pnp: PnP ACPI init
[   18.048758] pnp: PnP ACPI: found 10 devices
[   18.048831] PCI: Using ACPI for IRQ routing
[   18.048834] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   18.048842] PCI: Cannot allocate resource region 7 of bridge 0000:00:05.0
[   18.048845] PCI: Cannot allocate resource region 8 of bridge 0000:00:05.0
[   18.048954] NET: Registered protocol family 8
[   18.048956] NET: Registered protocol family 20
[   18.049340] pnp: 00:08: ioport range 0x1080-0x1080 has been reserved
[   18.049344] pnp: 00:08: ioport range 0x220-0x22f has been reserved
[   18.049695] PCI: Bridge: 0000:00:01.0
[   18.049699]   IO window: 9000-9fff
[   18.049703]   MEM window: c0100000-c01fffff
[   18.049707]   PREFETCH window: c8000000-cfffffff
[   18.049710] PCI: Bridge: 0000:00:05.0
[   18.049712]   IO window: disabled.
[   18.049714]   MEM window: disabled.
[   18.049717]   PREFETCH window: disabled.
[   18.049720] PCI: Bridge: 0000:00:06.0
[   18.049721]   IO window: disabled.
[   18.049725]   MEM window: c0200000-c02fffff
[   18.049728]   PREFETCH window: disabled.
[   18.049731] PCI: Bridge: 0000:00:14.4
[   18.049733]   IO window: disabled.
[   18.049739]   MEM window: c0300000-c03fffff
[   18.049744]   PREFETCH window: disabled.
[   18.049763] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   18.049770] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   18.049881] NET: Registered protocol family 2
[   18.095301] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   18.095538] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[   18.096646] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   18.097160] TCP: Hash tables configured (established 131072 bind 65536)
[   18.097163] TCP reno registered
[   18.111357] checking if image is initramfs... it is
[   18.871970] Freeing initrd memory: 7034k freed
[   18.876783] audit: initializing netlink socket (disabled)
[   18.876802] audit(1186470239.536:1): initialized
[   18.877022] VFS: Disk quotas dquot_6.5.1
[   18.877047] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   18.877104] io scheduler noop registered
[   18.877107] io scheduler anticipatory registered
[   18.877110] io scheduler deadline registered
[   18.877126] io scheduler cfq registered (default)
[   18.877424] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   18.877447] assign_interrupt_mode Found MSI capability
[   18.877452] Allocate Port Service[0000:00:05.0:pcie00]
[   18.877495] Allocate Port Service[0000:00:05.0:pcie02]
[   18.877570] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   18.877591] assign_interrupt_mode Found MSI capability
[   18.877594] Allocate Port Service[0000:00:06.0:pcie00]
[   18.877631] Allocate Port Service[0000:00:06.0:pcie02]
[   18.908128] Real Time Clock Driver v1.12ac
[   18.908175] Linux agpgart interface v0.102 (c) Dave Jones
[   18.908178] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   18.908973] mice: PS/2 mouse device common for all mice
[   18.909627] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   18.909802] input: Macintosh mouse button emulation as /class/input/input0
[   18.909841] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   18.909846] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   18.910137] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   18.912260] serio: i8042 KBD port at 0x60,0x64 irq 1
[   18.912269] serio: i8042 AUX port at 0x60,0x64 irq 12
[   18.912377] TCP cubic registered
[   18.912389] NET: Registered protocol family 1
[   18.912535] ACPI: (supports S0 S3 S4 S5)
[   18.912585]   Magic number: 3:789:65
[   18.912707] drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   18.912786] Freeing unused kernel memory: 304k freed
[   18.945397] input: AT Translated Set 2 keyboard as /class/input/input1
[   20.160743] Capability LSM initialized
[   20.247529] ACPI: Processor [CPU0] (supports 8 throttling states)
[   20.249809] ACPI: Thermal Zone [THRM] (46 C)
[   20.904775] usbcore: registered new interface driver usbfs
[   20.904800] usbcore: registered new interface driver hub
[   20.904828] usbcore: registered new device driver usb
[   20.905798] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   20.905841] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 16 (level, low) -> IRQ 16
[   20.905861] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   20.906007] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   20.906033] ohci_hcd 0000:00:13.0: irq 16, io mem 0xc0005000
[   20.912453] SCSI subsystem initialized
[   20.935111] libata version 2.20 loaded.
[   20.973259] usb usb1: configuration #1 chosen from 1 choice
[   20.973289] hub 1-0:1.0: USB hub found
[   20.973301] hub 1-0:1.0: 2 ports detected
[   21.081387] ahci 0000:00:12.0: version 2.1
[   21.081415] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 22
[   22.087631] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[   22.087637] ahci 0000:00:12.0: flags: 64bit ncq ilck led clo pmp pio 
[   22.087768] ata1: SATA max UDMA/133 cmd 0xffffc20000024100 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 22
[   22.087856] ata2: SATA max UDMA/133 cmd 0xffffc20000024180 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 22
[   22.087953] ata3: SATA max UDMA/133 cmd 0xffffc20000024200 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 22
[   22.088056] ata4: SATA max UDMA/133 cmd 0xffffc20000024280 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 22
[   22.088072] scsi0 : ahci
[   22.575155] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   22.576051] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[   22.576058] ata1.00: ATA-7: Hitachi HTS541612J9SA00, SBDOC74P, max UDMA/100
[   22.576061] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   22.577109] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[   22.577114] ata1.00: configured for UDMA/100
[   22.577126] scsi1 : ahci
[   22.890850] ata2: SATA link down (SStatus 0 SControl 300)
[   22.890871] scsi2 : ahci
[   23.206560] ata3: SATA link down (SStatus 0 SControl 300)
[   23.206580] scsi3 : ahci
[   23.522267] ata4: SATA link down (SStatus 0 SControl 300)
[   23.522396] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54161 SBDO PQ: 0 ANSI: 5
[   23.524408] b44.c:v1.01 (Jun 16, 2006)
[   23.524437] ACPI: PCI Interrupt 0000:08:00.0[A] -> GSI 21 (level, low) -> IRQ 21
[   23.530078] ACPI: PCI Interrupt 0000:00:13.1[B] -> GSI 17 (level, low) -> IRQ 17
[   23.530103] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   23.530337] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   23.530361] ohci_hcd 0000:00:13.1: irq 17, io mem 0xc0006000
[   23.530629] eth0: Broadcom 4400 10/100BaseT Ethernet 00:19:b9:74:16:af
[   23.535673] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[   23.535689] sda: Write Protect is off
[   23.535692] sda: Mode Sense: 00 3a 00 00
[   23.535710] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.535767] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[   23.535777] sda: Write Protect is off
[   23.535779] sda: Mode Sense: 00 3a 00 00
[   23.535796] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.535800]  sda:<6>usb usb2: configuration #1 chosen from 1 choice
[   23.586472] hub 2-0:1.0: USB hub found
[   23.586485] hub 2-0:1.0: 2 ports detected
[   23.694251] ACPI: PCI Interrupt 0000:00:13.2[C] -> GSI 18 (level, low) -> IRQ 18
[   23.694275] ohci_hcd 0000:00:13.2: OHCI Host Controller
[   23.694305] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   23.694327] ohci_hcd 0000:00:13.2: irq 18, io mem 0xc0007000
[   23.754160] usb usb3: configuration #1 chosen from 1 choice
[   23.754188] hub 3-0:1.0: USB hub found
[   23.754198] hub 3-0:1.0: 2 ports detected
[   23.858102] ACPI: PCI Interrupt 0000:00:13.3[B] -> GSI 17 (level, low) -> IRQ 17
[   23.858125] ohci_hcd 0000:00:13.3: OHCI Host Controller
[   23.858156] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 4
[   23.858174] ohci_hcd 0000:00:13.3: irq 17, io mem 0xc0008000
[   23.918055] usb usb4: configuration #1 chosen from 1 choice
[   23.918086] hub 4-0:1.0: USB hub found
[   23.918102] hub 4-0:1.0: 2 ports detected
[   23.940677]  sda1 sda2 < sda5 >
[   23.969660] sd 0:0:0:0: Attached scsi disk sda
[   23.973899] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   24.025965] ACPI: PCI Interrupt 0000:00:13.4[C] -> GSI 18 (level, low) -> IRQ 18
[   24.025988] ohci_hcd 0000:00:13.4: OHCI Host Controller
[   24.026023] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 5
[   24.026041] ohci_hcd 0000:00:13.4: irq 18, io mem 0xc0009000
[   24.085924] usb usb5: configuration #1 chosen from 1 choice
[   24.085961] hub 5-0:1.0: USB hub found
[   24.085973] hub 5-0:1.0: 2 ports detected
[   24.136175] Attempting manual resume
[   24.136179] swsusp: Resume From Partition 8:5
[   24.136181] PM: Checking swsusp image.
[   24.136336] PM: Resume from disk failed.
[   24.168733] EXT3-fs: INFO: recovery required on readonly filesystem.
[   24.168738] EXT3-fs: write access will be enabled during recovery.
[   24.193965] ACPI: PCI Interrupt 0000:00:13.5[D] -> GSI 19 (level, low) -> IRQ 19
[   24.193985] ehci_hcd 0000:00:13.5: EHCI Host Controller
[   24.194022] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 6
[   24.194066] ehci_hcd 0000:00:13.5: debug port 1
[   24.194085] ehci_hcd 0000:00:13.5: irq 19, io mem 0xc0004400
[   24.194097] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   24.194186] usb usb6: configuration #1 chosen from 1 choice
[   24.194215] hub 6-0:1.0: USB hub found
[   24.194224] hub 6-0:1.0: 10 ports detected
[   24.301686] SB600_PATA: IDE controller at PCI slot 0000:00:14.1
[   24.301706] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[   24.301720] SB600_PATA: chipset revision 0
[   24.301723] SB600_PATA: not 100% native mode: will probe irqs later
[   24.301733]     ide0: BM-DMA at 0x8420-0x8427, BIOS settings: hda:DMA, hdb:pio
[   24.301747] Probing IDE interface ide0...
[   25.041285] hda: HL-DT-STCD-RW/DVD-ROM GCC-4244N, ATAPI CD/DVD-ROM drive
[   25.381611] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   25.398369] hda: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   25.398380] Uniform CD-ROM driver Revision: 3.20
[   29.323775] kjournald starting.  Commit interval 5 seconds
[   29.323795] EXT3-fs: recovery complete.
[   29.324493] EXT3-fs: mounted filesystem with ordered data mode.
[   40.912016] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   40.914659] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   40.956458] sdhci: Secure Digital Host Controller Interface driver
[   40.956464] sdhci: Copyright(c) Pierre Ossman
[   40.956572] sdhci: SDHCI controller found at 0000:08:01.0 [1180:0822] (rev 19)
[   40.956599] ACPI: PCI Interrupt 0000:08:01.0[B] -> GSI 20 (level, low) -> IRQ 20
[   40.956692] mmc0: SDHCI at 0xc0302800 irq 20 DMA
[   40.996892] input: PC Speaker as /class/input/input2
[   41.320743] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16
[   41.360129] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x180b1, caps: 0xa04713/0x200000
[   41.397889] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   41.781636] fuse init (API version 7.8)
[   42.000877] lp: driver loaded but no devices found
[   42.127979] ndiswrapper version 1.46 loaded (smp=yes)
[   42.215355] ndiswrapper (link_pe_images:577): fixing KI_USER_SHARED_DATA address in the driver
[   42.217482] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
[   42.217765] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   42.217809] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   42.221170] ndiswrapper: using IRQ 18
[   42.562079] wlan0: ethernet device 00:19:7e:72:d7:c8 using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4311.5.conf
[   42.562134] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   42.564802] usbcore: registered new interface driver ndiswrapper
[   42.566556] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
[   42.604387] Adding 2626588k swap on /dev/disk/by-uuid/54a08b3e-38f0-4a09-9e82-82c712fa41b7.  Priority:-1 extents:1 across:2626588k
[   42.726817] EXT3 FS on sda1, internal journal
[   44.222956] NET: Registered protocol family 17
[   49.819891] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   49.878485] Using specific hotkey driver
[   49.915505] input: Power Button (FF) as /class/input/input4
[   49.915538] ACPI: Power Button (FF) [PWRF]
[   49.915576] input: Power Button (CM) as /class/input/input5
[   49.915594] ACPI: Power Button (CM) [PWRB]
[   49.915650] input: Sleep Button (CM) as /class/input/input6
[   49.915673] ACPI: Sleep Button (CM) [SLPB]
[   49.915707] input: Lid Switch as /class/input/input7
[   49.915723] ACPI: Lid Switch [LID]
[   49.984396] ACPI: AC Adapter [ACAD] (on-line)
[   50.009361] No dock devices found.
[   50.045964] ACPI: Battery Slot [BAT1] (battery present)
[   50.092216] ibm_acpi: ec object not found
[   50.140823] wmi_add device=ffff810035af5800
[   50.140828] calling WQBA
[   50.151375] pcc_acpi: loading...
[   50.345660] powernow-k8: Found 2 AMD Turion(tm) 64 X2 Mobile Technology TL-50 processors (version 2.00.00)
[   50.345533] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x12
[   50.345538] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x1e
[   55.533690] [fglrx] Maximum main memory to use for locked dma buffers: 796 MBytes.
[   55.534500] [fglrx] module loaded - fglrx 8.34.8 [Feb 20 2007] on minor 0
[   55.576081] ppdev: user-space parallel port driver
[   55.606972] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 17
[   56.072332] NET: Registered protocol family 10
[   56.072447] lo: Disabled Privacy Extensions
[   56.072513] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   56.072516] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   57.649922] [fglrx] total      GART = 130023424
[   57.649933] [fglrx] free       GART = 114032640
[   57.649936] [fglrx] max single GART = 114032640
[   57.649939] [fglrx] total      LFB  = 134217728
[   57.649942] [fglrx] free       LFB  = 119828480
[   57.649945] [fglrx] max single LFB  = 119828480
[   57.649947] [fglrx] total      Inv  = 0
[   57.649949] [fglrx] free       Inv  = 0
[   57.649951] [fglrx] max single Inv  = 0
[   57.649953] [fglrx] total      TIM  = 0
[   57.811130] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   57.935610] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   57.957252] NFSD: starting 90-second grace period
[   58.968768] cdrom: This disc doesn't have any tracks I recognize!
[   61.131613] hda-intel: Invalid position buffer, using LPIB read method instead.
[  107.948130] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  118.951090] eth1: no IPv6 routers present
[  130.875107] APIC error on CPU0: 00(40)
[  212.193558] APIC error on CPU0: 40(40)
[  427.766713] APIC error on CPU0: 40(40)
[ 1119.542438] APIC error on CPU0: 40(40)
[ 1396.442508] APIC error on CPU0: 40(40)
[ 1463.158758] APIC error on CPU0: 40(40)
[ 2512.955854] APIC error on CPU0: 40(40)
[ 2622.095195] APIC error on CPU0: 40(40)
[ 2723.591268] APIC error on CPU0: 40(40)
[ 3467.196005] APIC error on CPU0: 40(40)
[ 3474.839279] APIC error on CPU0: 40(40)
[ 3896.744431] APIC error on CPU0: 40(40)
[ 3905.509552] APIC error on CPU0: 40(40)
[ 3937.527376] APIC error on CPU0: 40(40)
[ 4851.305669] APIC error on CPU0: 40(40)
[ 5054.618972] APIC error on CPU0: 40(40)
[ 5137.917645] APIC error on CPU0: 40(40)
[ 5483.854263] APIC error on CPU0: 40(40)
[ 6043.743274] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[ 6046.708233] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 6046.828344] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[ 6053.650767] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[ 6060.148820] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[ 6066.646874] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[ 6073.144928] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[ 6086.052438] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 7602.982004] APIC error on CPU0: 40(40)
[ 7610.625278] APIC error on CPU0: 40(40)
[ 7663.625458] APIC error on CPU0: 40(40)
[ 8439.484134] APIC error on CPU0: 40(40)
[ 9400.412073] APIC error on CPU0: 40(40)
[ 9459.551437] APIC error on CPU0: 40(40)
[ 9603.725372] APIC error on CPU0: 40(40)
[ 9735.915843] APIC error on CPU0: 40(40)
[ 9924.142447] APIC error on CPU0: 40(40)
[10244.880609] APIC error on CPU0: 40(40)
[10447.870738] APIC error on CPU0: 40(40)
[10447.874736] Losing some ticks... checking if CPU frequency changed.
[11385.075060] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[11392.211950] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[11398.709996] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[11405.848301] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
[11415.519136] ndiswrapper (iw_set_freq:380): setting configuration failed (00010003)
```

---

