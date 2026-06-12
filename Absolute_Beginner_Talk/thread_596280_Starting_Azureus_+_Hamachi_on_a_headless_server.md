---
title: "Starting Azureus + Hamachi on a headless server"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by ReddyReal on 2007-10-29
Hi guys,
Thanks to[this]("http://nerdica.com/?p=30") article (full of errors and out-of-date information), I've been trying for the past few weeks to conquer this lofty idea of setting up a Headless BitTorrent server on my PC with Ubuntu. Where I'm running into problems, over and over, is when I run "update-rc.d gdm remove," not only does my computer not login automatically, it does not start Azureus automatically. 

Through the help of these forums, I've been able to configure Hamachi and Azureus properly so that when I'm at the GNOME desktop, everything works great. But when I run the update-rc.d script and just come to the non-GDM  terminal, nothing works. Azureus will start and then exit immediately. 

Some threads seem to imply that my problem is logging in as a root is causing these problems. Is that the issue? And if so, what can I do to solve that?  I am, as the forum implies, very noob to all things Ubuntu, Linux and networking. So your patience is appreciated.

Thanks!
Reddy

---

### Post by DezSP on 2007-10-29
Azureus is a Java app, surely it needs an X server to run? Try running it manually, or check the system logs to see what the problem is. What do you need Hamachi for?

---

### Post by ReddyReal on 2007-10-31
I decided to just try and focus on getting Azureus running at boot and worry about Hamachi later. Fwiw, I thought having Hamachi would allow me to connect to my Ubuntu Headless PC from my Mac. Is that not really true? 

Regardless, I just want to get Azureus up and running at boot for the time being and worry about connecting to my PC through my router later. I followed [these]("http://www.azureuswiki.com/index.php/HeadlessSwingUIAtBoot") directions and they seemed to make sense. In fact, everything worked great...until reboot. 

Here is my log from where I believe my final reboot happened:

```
ct 30 23:45:20 Ubuntu kernel: [    0.000000] BIOS-provided physical RAM map:
Oct 30 23:45:20 Ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
Oct 30 23:45:20 Ubuntu kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Oct 30 23:45:20 Ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
Oct 30 23:45:20 Ubuntu kernel: [    0.000000]  BIOS-e820: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
Oct 30 23:45:20 Ubuntu kernel: [    0.000000]  BIOS-e820: 000000001fff3000 - 0000000020000000 (ACPI data)
Oct 30 23:45:20 Ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Oct 30 23:45:20 Ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Oct 30 23:45:20 Ubuntu kernel: [    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
Oct 30 23:45:20 Ubuntu kernel: [    0.000000] 0MB HIGHMEM available.
Oct 30 23:45:20 Ubuntu kernel: [    0.000000] 511MB LOWMEM available.
Oct 30 23:45:20 Ubuntu kernel: [    0.000000] found SMP MP-table at 000f5330
Oct 30 23:45:20 Ubuntu kernel: [    0.000000] Entering add_active_range(0, 0, 131056) 0 entries of 256 used
Oct 30 23:45:20 Ubuntu kernel: [    0.000000] Zone PFN ranges:
Oct 30 23:45:20 Ubuntu kernel: [    0.000000]   DMA             0 ->     4096
Oct 30 23:45:20 Ubuntu kernel: [    0.000000]   Normal       4096 ->   131056
Oct 30 23:45:20 Ubuntu kernel: [    0.000000]   HighMem    131056 ->   131056
Oct 30 23:45:20 Ubuntu kernel: [    0.000000] early_node_map[1] active PFN ranges
Oct 30 23:45:20 Ubuntu kernel: [    0.000000]     0:        0 ->   131056
Oct 30 23:45:20 Ubuntu kernel: [    0.000000] On node 0 totalpages: 131056
Oct 30 23:45:20 Ubuntu kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Oct 30 23:45:20 Ubuntu kernel: [    0.000000]   DMA zone: 0 pages reserved
Oct 30 23:45:20 Ubuntu kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Oct 30 23:45:20 Ubuntu kernel: [    0.000000]   Normal zone: 991 pages used for memmap
Oct 30 23:45:20 Ubuntu kernel: [    0.000000]   Normal zone: 125969 pages, LIFO batch:31
Oct 30 23:45:20 Ubuntu kernel: [    0.000000]   HighMem zone: 0 pages used for memmap
Oct 30 23:45:20 Ubuntu kernel: [    0.000000] DMI 2.3 present.
Oct 30 23:45:20 Ubuntu kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F6E70 checksum 0
Oct 30 23:45:20 Ubuntu kernel: [    0.000000] ACPI: RSDP 000F6E70, 0014 (r0 GBT   )
Oct 30 23:45:20 Ubuntu kernel: [    0.000000] ACPI: RSDT 1FFF3000, 002C (r1 GBT    AWRDACPI 42302E31 AWRD        0)
Oct 30 23:45:20 Ubuntu kernel: [    0.000000] ACPI: FACP 1FFF3040, 0074 (r1 GBT    AWRDACPI 42302E31 AWRD        0)
Oct 30 23:45:20 Ubuntu kernel: [    0.000000] ACPI: DSDT 1FFF30C0, 2B39 (r1 GBT    AWRDACPI     1000 MSFT  100000C)
Oct 30 23:45:20 Ubuntu kernel: [    0.000000] ACPI: FACS 1FFF0000, 0040
Oct 30 23:45:20 Ubuntu kernel: [    0.000000] ACPI: APIC 1FFF5C00, 005A (r1 GBT    AWRDACPI 42302E31 AWRD        0)
Oct 30 23:45:20 Ubuntu kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Oct 30 23:45:20 Ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Oct 30 23:45:20 Ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Oct 30 23:45:20 Ubuntu kernel: [    0.000000] Processor #0 6:6 APIC version 16
Oct 30 23:45:20 Ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] dfl dfl lint[0x1])
Oct 30 23:45:20 Ubuntu kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Oct 30 23:45:20 Ubuntu kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
Oct 30 23:45:20 Ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Oct 30 23:45:20 Ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Oct 30 23:45:20 Ubuntu kernel: [    0.000000] ACPI: IRQ0 used by override.
Oct 30 23:45:20 Ubuntu kernel: [    0.000000] ACPI: IRQ2 used by override.
Oct 30 23:45:20 Ubuntu kernel: [    0.000000] ACPI: IRQ9 used by override.
Oct 30 23:45:20 Ubuntu kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Oct 30 23:45:20 Ubuntu kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Oct 30 23:45:20 Ubuntu kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
Oct 30 23:45:20 Ubuntu kernel: [    0.000000] Built 1 zonelists.  Total pages: 130033
Oct 30 23:45:20 Ubuntu kernel: [    0.000000] Kernel command line: root=UUID=00305087-9b82-4803-9ecf-24f675d6f4f4 ro quiet splash
Oct 30 23:45:20 Ubuntu kernel: [    0.000000] mapped APIC to ffffd000 (fee00000)
Oct 30 23:45:20 Ubuntu kernel: [    0.000000] mapped IOAPIC to ffffc000 (fec00000)
Oct 30 23:45:20 Ubuntu kernel: [    0.000000] Enabling fast FPU save and restore... done.
Oct 30 23:45:20 Ubuntu kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Oct 30 23:45:20 Ubuntu kernel: [    0.000000] Initializing CPU#0
Oct 30 23:45:20 Ubuntu kernel: [    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
Oct 30 23:45:20 Ubuntu kernel: [    0.000000] Detected 1161.519 MHz processor.
Oct 30 23:45:20 Ubuntu kernel: [   48.959482] Console: colour VGA+ 80x25
Oct 30 23:45:20 Ubuntu kernel: [   48.960128] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Oct 30 23:45:20 Ubuntu kernel: [   48.960601] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Oct 30 23:45:20 Ubuntu kernel: [   48.985416] Memory: 507916k/524224k available (2015k kernel code, 15728k reserved, 916k data, 364k init, 0k highmem)
Oct 30 23:45:20 Ubuntu kernel: [   48.985435] virtual kernel memory layout:
Oct 30 23:45:20 Ubuntu kernel: [   48.985436]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
Oct 30 23:45:20 Ubuntu kernel: [   48.985439]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Oct 30 23:45:20 Ubuntu kernel: [   48.985441]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
Oct 30 23:45:20 Ubuntu kernel: [   48.985443]     lowmem  : 0xc0000000 - 0xdfff0000   ( 511 MB)
Oct 30 23:45:20 Ubuntu kernel: [   48.985445]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
Oct 30 23:45:20 Ubuntu kernel: [   48.985448]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
Oct 30 23:45:20 Ubuntu kernel: [   48.985450]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
Oct 30 23:45:20 Ubuntu kernel: [   48.985456] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Oct 30 23:45:20 Ubuntu kernel: [   48.985529] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Oct 30 23:45:20 Ubuntu kernel: [   49.065501] Calibrating delay using timer specific routine.. 2325.22 BogoMIPS (lpj=4650458)
Oct 30 23:45:20 Ubuntu kernel: [   49.065554] Security Framework v1.0.0 initialized
Oct 30 23:45:20 Ubuntu kernel: [   49.065566] SELinux:  Disabled at boot.
Oct 30 23:45:20 Ubuntu kernel: [   49.065593] Mount-cache hash table entries: 512
Oct 30 23:45:20 Ubuntu kernel: [   49.065819] CPU: After generic identify, caps: 0383fbff c1cbfbff 00000000 00000000 00000000 00000000 00000000
Oct 30 23:45:20 Ubuntu kernel: [   49.065835] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Oct 30 23:45:20 Ubuntu kernel: [   49.065840] CPU: L2 Cache: 256K (64 bytes/line)
Oct 30 23:45:20 Ubuntu kernel: [   49.065845] CPU: After all inits, caps: 0383fbff c1cbfbff 00000000 00000420 00000000 00000000 00000000
Oct 30 23:45:20 Ubuntu kernel: [   49.065864] Compat vDSO mapped to ffffe000.
Oct 30 23:45:20 Ubuntu kernel: [   49.065884] Checking 'hlt' instruction... OK.
Oct 30 23:45:20 Ubuntu kernel: [   49.081703] SMP alternatives: switching to UP code
Oct 30 23:45:20 Ubuntu kernel: [   49.082133] Freeing SMP alternatives: 11k freed
Oct 30 23:45:20 Ubuntu kernel: [   49.082736] Early unpacking initramfs... done
Oct 30 23:45:20 Ubuntu kernel: [   49.640081] ACPI: Core revision 20070126
Oct 30 23:45:20 Ubuntu kernel: [   49.640221] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Oct 30 23:45:20 Ubuntu kernel: [   49.643037] CPU0: AMD Athlon(tm)  stepping 02
Oct 30 23:45:20 Ubuntu kernel: [   49.643073] Total of 1 processors activated (2325.22 BogoMIPS).
Oct 30 23:45:20 Ubuntu kernel: [   49.643808] ENABLING IO-APIC IRQs
Oct 30 23:45:20 Ubuntu kernel: [   49.644128] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Oct 30 23:45:20 Ubuntu kernel: [   49.789095] Brought up 1 CPUs
Oct 30 23:45:20 Ubuntu kernel: [   49.789367] Booting paravirtualized kernel on bare hardware
Oct 30 23:45:20 Ubuntu kernel: [   49.789478] Time:  4:44:53  Date: 09/31/107
Oct 30 23:45:20 Ubuntu kernel: [   49.789527] NET: Registered protocol family 16
Oct 30 23:45:20 Ubuntu kernel: [   49.789701] EISA bus registered
Oct 30 23:45:20 Ubuntu kernel: [   49.789720] ACPI: bus type pci registered
Oct 30 23:45:20 Ubuntu kernel: [   49.819927] PCI: PCI BIOS revision 2.10 entry at 0xfb690, last bus=1
Oct 30 23:45:20 Ubuntu kernel: [   49.819931] PCI: Using configuration type 1
Oct 30 23:45:20 Ubuntu kernel: [   49.819935] Setting up standard PCI resources
Oct 30 23:45:20 Ubuntu kernel: [   49.822454] ACPI: EC: Look up EC in DSDT
Oct 30 23:45:20 Ubuntu kernel: [   49.826969] ACPI: Interpreter enabled
Oct 30 23:45:20 Ubuntu kernel: [   49.826975] ACPI: (supports S0 S1 S4 S5)
Oct 30 23:45:20 Ubuntu kernel: [   49.827001] ACPI: Using IOAPIC for interrupt routing
Oct 30 23:45:20 Ubuntu kernel: [   49.832483] ACPI: PCI Root Bridge [PCI0] (0000:00)
Oct 30 23:45:20 Ubuntu kernel: [   49.832500] PCI: Probing PCI hardware (bus 00)
Oct 30 23:45:20 Ubuntu kernel: [   49.832845] PCI quirk: region 6000-607f claimed by vt82c686 HW-mon
Oct 30 23:45:20 Ubuntu kernel: [   49.832851] PCI quirk: region 5000-500f claimed by vt82c686 SMB
Oct 30 23:45:20 Ubuntu kernel: [   49.833297] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Oct 30 23:45:20 Ubuntu kernel: [   49.853168] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 11 12 14 15)
Oct 30 23:45:20 Ubuntu kernel: [   49.853372] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 *5 6 7 10 11 12 14 15)
Oct 30 23:45:20 Ubuntu kernel: [   49.853576] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 11 *12 14 15)
Oct 30 23:45:20 Ubuntu kernel: [   49.853777] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
Oct 30 23:45:20 Ubuntu kernel: [   49.853905] Linux Plug and Play Support v0.97 (c) Adam Belay
Oct 30 23:45:20 Ubuntu kernel: [   49.853926] pnp: PnP ACPI init
Oct 30 23:45:20 Ubuntu kernel: [   49.853942] ACPI: bus type pnp registered
Oct 30 23:45:20 Ubuntu kernel: [   49.857342] pnp: PnP ACPI: found 12 devices
Oct 30 23:45:20 Ubuntu kernel: [   49.857347] ACPI: ACPI bus type pnp unregistered
Oct 30 23:45:20 Ubuntu kernel: [   49.857354] PnPBIOS: Disabled by ACPI PNP
Oct 30 23:45:20 Ubuntu kernel: [   49.857450] PCI: Using ACPI for IRQ routing
Oct 30 23:45:20 Ubuntu kernel: [   49.857455] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Oct 30 23:45:20 Ubuntu kernel: [   49.886608] NET: Registered protocol family 8
Oct 30 23:45:20 Ubuntu kernel: [   49.886612] NET: Registered protocol family 20
Oct 30 23:45:20 Ubuntu kernel: [   49.886743] pnp: 00:00: iomem range 0xc9000-0xcbfff has been reserved
Oct 30 23:45:20 Ubuntu kernel: [   49.886749] pnp: 00:00: iomem range 0xf0000-0xf7fff could not be reserved
Oct 30 23:45:20 Ubuntu kernel: [   49.886754] pnp: 00:00: iomem range 0xf8000-0xfbfff could not be reserved
Oct 30 23:45:20 Ubuntu kernel: [   49.886759] pnp: 00:00: iomem range 0xfc000-0xfffff could not be reserved
Oct 30 23:45:20 Ubuntu kernel: [   49.888951] Time: tsc clocksource has been installed.
Oct 30 23:45:20 Ubuntu kernel: [   49.917261] PCI: Bridge: 0000:00:01.0
Oct 30 23:45:20 Ubuntu kernel: [   49.917264]   IO window: disabled.
Oct 30 23:45:20 Ubuntu kernel: [   49.917270]   MEM window: e6000000-e8ffffff
Oct 30 23:45:20 Ubuntu kernel: [   49.917276]   PREFETCH window: e4000000-e5ffffff
Oct 30 23:45:20 Ubuntu kernel: [   49.917306] NET: Registered protocol family 2
Oct 30 23:45:20 Ubuntu kernel: [   49.957006] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
Oct 30 23:45:20 Ubuntu kernel: [   49.957109] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
Oct 30 23:45:20 Ubuntu kernel: [   49.957613] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
Oct 30 23:45:20 Ubuntu kernel: [   49.957982] TCP: Hash tables configured (established 16384 bind 16384)
Oct 30 23:45:20 Ubuntu kernel: [   49.957987] TCP reno registered
Oct 30 23:45:20 Ubuntu kernel: [   49.969166] checking if image is initramfs...<6>Switched to high resolution mode on CPU 0
Oct 30 23:45:20 Ubuntu kernel: [   50.448211]  it is
Oct 30 23:45:20 Ubuntu kernel: [   51.026301] Freeing initrd memory: 7352k freed
Oct 30 23:45:20 Ubuntu kernel: [   51.027075] audit: initializing netlink socket (disabled)
Oct 30 23:45:20 Ubuntu kernel: [   51.027102] audit(1193805893.800:1): initialized
Oct 30 23:45:20 Ubuntu kernel: [   51.030335] VFS: Disk quotas dquot_6.5.1
Oct 30 23:45:20 Ubuntu kernel: [   51.030430] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Oct 30 23:45:20 Ubuntu kernel: [   51.030604] io scheduler noop registered
Oct 30 23:45:20 Ubuntu kernel: [   51.030608] io scheduler anticipatory registered
Oct 30 23:45:20 Ubuntu kernel: [   51.030612] io scheduler deadline registered
Oct 30 23:45:20 Ubuntu kernel: [   51.030636] io scheduler cfq registered (default)
Oct 30 23:45:20 Ubuntu kernel: [   51.030659] PCI: Enabling Via external APIC routing
Oct 30 23:45:20 Ubuntu kernel: [   51.030724] Boot video device is 0000:01:05.0
Oct 30 23:45:20 Ubuntu kernel: [   51.031023] isapnp: Scanning for PnP cards...
Oct 30 23:45:20 Ubuntu kernel: [   51.384833] isapnp: No Plug & Play device found
Oct 30 23:45:20 Ubuntu kernel: [   51.437898] Real Time Clock Driver v1.12ac
Oct 30 23:45:20 Ubuntu kernel: [   51.438048] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Oct 30 23:45:20 Ubuntu kernel: [   51.438195] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Oct 30 23:45:20 Ubuntu kernel: [   51.438612] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Oct 30 23:45:20 Ubuntu kernel: [   51.439882] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Oct 30 23:45:20 Ubuntu kernel: [   51.440474] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Oct 30 23:45:20 Ubuntu kernel: [   51.441827] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Oct 30 23:45:20 Ubuntu kernel: [   51.442202] input: Macintosh mouse button emulation as /class/input/input0
Oct 30 23:45:20 Ubuntu kernel: [   51.442335] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Oct 30 23:45:20 Ubuntu kernel: [   51.442340] PNP: PS/2 controller doesn't have AUX irq; using default 12
Oct 30 23:45:20 Ubuntu kernel: [   51.442829] serio: i8042 KBD port at 0x60,0x64 irq 1
Oct 30 23:45:20 Ubuntu kernel: [   51.442839] serio: i8042 AUX port at 0x60,0x64 irq 12
Oct 30 23:45:20 Ubuntu kernel: [   51.443103] mice: PS/2 mouse device common for all mice
Oct 30 23:45:20 Ubuntu kernel: [   51.443308] EISA: Probing bus 0 at eisa.0
Oct 30 23:45:20 Ubuntu kernel: [   51.443338] Cannot allocate resource for EISA slot 4
Oct 30 23:45:20 Ubuntu kernel: [   51.443343] Cannot allocate resource for EISA slot 5
Oct 30 23:45:20 Ubuntu kernel: [   51.443346] Cannot allocate resource for EISA slot 6
Oct 30 23:45:20 Ubuntu kernel: [   51.443359] EISA: Detected 0 cards.
Oct 30 23:45:20 Ubuntu kernel: [   51.443673] TCP cubic registered
Oct 30 23:45:20 Ubuntu kernel: [   51.443690] NET: Registered protocol family 1
Oct 30 23:45:20 Ubuntu kernel: [   51.443725] Using IPI No-Shortcut mode
Oct 30 23:45:20 Ubuntu kernel: [   51.444111]   Magic number: 11:460:718
Oct 30 23:45:20 Ubuntu kernel: [   51.445160] Freeing unused kernel memory: 364k freed
Oct 30 23:45:20 Ubuntu kernel: [   51.475921] input: AT Translated Set 2 keyboard as /class/input/input1
Oct 30 23:45:20 Ubuntu kernel: [   52.814192] AppArmor: AppArmor initialized<5>audit(1193805895.300:2):  type=1505 info="AppArmor initialized" pid=1175
Oct 30 23:45:20 Ubuntu kernel: [   52.825317] fuse init (API version 7.8)
Oct 30 23:45:20 Ubuntu kernel: [   52.835682] Failure registering capabilities with primary security module.
Oct 30 23:45:20 Ubuntu kernel: [   52.864307] ACPI: Processor [CPU0] (supports 2 throttling states)
Oct 30 23:45:20 Ubuntu kernel: [   53.828512] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Oct 30 23:45:20 Ubuntu kernel: [   53.828525] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Oct 30 23:45:20 Ubuntu kernel: [   53.829611] VP_IDE: IDE controller at PCI slot 0000:00:07.1
Oct 30 23:45:20 Ubuntu kernel: [   53.829648] VP_IDE: chipset revision 6
Oct 30 23:45:20 Ubuntu kernel: [   53.829652] VP_IDE: not 100%% native mode: will probe irqs later
Oct 30 23:45:20 Ubuntu kernel: [   53.829669] VP_IDE: VIA vt82c686b (rev 40) IDE UDMA100 controller on pci0000:00:07.1
Oct 30 23:45:20 Ubuntu kernel: [   53.829681]     ide0: BM-DMA at 0xc400-0xc407, BIOS settings: hda:DMA, hdb:DMA
Oct 30 23:45:20 Ubuntu kernel: [   53.829700]     ide1: BM-DMA at 0xc408-0xc40f, BIOS settings: hdc:DMA, hdd:DMA
Oct 30 23:45:20 Ubuntu kernel: [   53.829711] Probing IDE interface ide0...
Oct 30 23:45:20 Ubuntu kernel: [   53.856140] usbcore: registered new interface driver usbfs
Oct 30 23:45:20 Ubuntu kernel: [   53.856193] usbcore: registered new interface driver hub
Oct 30 23:45:20 Ubuntu kernel: [   53.856238] usbcore: registered new device driver usb
Oct 30 23:45:20 Ubuntu kernel: [   53.857787] USB Universal Host Controller Interface driver v3.0
Oct 30 23:45:20 Ubuntu kernel: [   54.019035] epic100.c:v1.11 1/7/2001 Written by Donald Becker <becker@scyld.com>
Oct 30 23:45:20 Ubuntu kernel: [   54.019040]   (unofficial 2.4.x kernel port, version 2.1, Sept 11, 2006)
Oct 30 23:45:20 Ubuntu kernel: [   54.030339] SCSI subsystem initialized
Oct 30 23:45:20 Ubuntu kernel: [   54.039472] libata version 2.21 loaded.
Oct 30 23:45:20 Ubuntu kernel: [   54.049447] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Oct 30 23:45:20 Ubuntu kernel: [   54.223659] Floppy drive(s): fd0 is 1.44M
Oct 30 23:45:20 Ubuntu kernel: [   54.261924] hda: WDC WD300BB-00AUA1, ATA DISK drive
Oct 30 23:45:20 Ubuntu kernel: [   54.290047] FDC 0 is a post-1991 82077
Oct 30 23:45:20 Ubuntu kernel: [   54.541681] hdb: MAXTOR 6L040J2, ATA DISK drive
Oct 30 23:45:20 Ubuntu kernel: [   54.599641] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Oct 30 23:45:20 Ubuntu kernel: [   54.619506] Probing IDE interface ide1...
Oct 30 23:45:20 Ubuntu kernel: [   55.480979] hdc: LITE-ON LTR-32123S, ATAPI CD/DVD-ROM drive
Oct 30 23:45:20 Ubuntu kernel: [   56.264400] hdd: PLEXTOR CD-R PX-W8432T, ATAPI CD/DVD-ROM drive
Oct 30 23:45:20 Ubuntu kernel: [   56.321735] ide1 at 0x170-0x177,0x376 on irq 15
Oct 30 23:45:20 Ubuntu kernel: [   56.332629] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
Oct 30 23:45:20 Ubuntu kernel: [   56.332649] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Oct 30 23:45:20 Ubuntu kernel: [   56.332672] uhci_hcd 0000:00:07.2: UHCI Host Controller
Oct 30 23:45:20 Ubuntu kernel: [   56.333466] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
Oct 30 23:45:20 Ubuntu kernel: [   56.333513] uhci_hcd 0000:00:07.2: irq 11, io base 0x0000c800
Oct 30 23:45:20 Ubuntu kernel: [   56.334321] usb usb1: configuration #1 chosen from 1 choice
Oct 30 23:45:20 Ubuntu kernel: [   56.334601] hub 1-0:1.0: USB hub found
Oct 30 23:45:20 Ubuntu kernel: [   56.334616] hub 1-0:1.0: 2 ports detected
Oct 30 23:45:20 Ubuntu kernel: [   56.346465] hda: max request size: 128KiB
Oct 30 23:45:20 Ubuntu kernel: [   56.361511] hda: 58633344 sectors (30020 MB) w/2048KiB Cache, CHS=58168/16/63, UDMA(100)
Oct 30 23:45:20 Ubuntu kernel: [   56.361527] hda: cache flushes not supported
Oct 30 23:45:20 Ubuntu kernel: [   56.361618]  hda: hda1 hda2 < hda5 >
Oct 30 23:45:20 Ubuntu kernel: [   56.387342] hdb: max request size: 128KiB
Oct 30 23:45:20 Ubuntu kernel: [   56.388280] hdb: 78177792 sectors (40027 MB) w/1819KiB Cache, CHS=65535/16/63, UDMA(100)
Oct 30 23:45:20 Ubuntu kernel: [   56.388445] hdb: cache flushes supported
Oct 30 23:45:20 Ubuntu kernel: [   56.388501]  hdb: hdb1
Oct 30 23:45:20 Ubuntu kernel: [   56.434847] hdc: ATAPI 40X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
Oct 30 23:45:20 Ubuntu kernel: [   56.434864] Uniform CD-ROM driver Revision: 3.20
Oct 30 23:45:20 Ubuntu kernel: [   56.436386] ACPI: PCI Interrupt 0000:00:07.3[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Oct 30 23:45:20 Ubuntu kernel: [   56.436412] uhci_hcd 0000:00:07.3: UHCI Host Controller
Oct 30 23:45:20 Ubuntu kernel: [   56.436460] uhci_hcd 0000:00:07.3: new USB bus registered, assigned bus number 2
Oct 30 23:45:20 Ubuntu kernel: [   56.436492] uhci_hcd 0000:00:07.3: irq 11, io base 0x0000cc00
Oct 30 23:45:20 Ubuntu kernel: [   56.436686] usb usb2: configuration #1 chosen from 1 choice
Oct 30 23:45:20 Ubuntu kernel: [   56.436737] hub 2-0:1.0: USB hub found
Oct 30 23:45:20 Ubuntu kernel: [   56.436755] hub 2-0:1.0: 2 ports detected
Oct 30 23:45:20 Ubuntu kernel: [   56.470942] hdd: ATAPI 32X CD-ROM CD-R/RW drive, 4096kB Cache, DMA
Oct 30 23:45:20 Ubuntu kernel: [   56.540506] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 18 (level, low) -> IRQ 16
Oct 30 23:45:20 Ubuntu kernel: [   56.594144] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[16]  MMIO=[ea006000-ea0067ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
Oct 30 23:45:20 Ubuntu kernel: [   56.601772] ACPI: PCI Interrupt 0000:00:0c.0[A] -> GSI 16 (level, low) -> IRQ 17
Oct 30 23:45:20 Ubuntu kernel: [   56.601914] epic100 0000:00:0c.0: MII transceiver #3 control 3000 status 7809.
Oct 30 23:45:20 Ubuntu kernel: [   56.602726] epic100 0000:00:0c.0: Autonegotiation advertising 01e1 link partner 0001.
Oct 30 23:45:20 Ubuntu kernel: [   56.602892] eth0: SMSC EPIC/100 83c170 at 0xd400, IRQ 17, 00:e0:29:26:87:50.
Oct 30 23:45:20 Ubuntu kernel: [   56.603056] pata_pdc2027x 0000:00:10.0: version 0.9
Oct 30 23:45:20 Ubuntu kernel: [   56.603151] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 19 (level, low) -> IRQ 18
Oct 30 23:45:20 Ubuntu kernel: [   56.702413] pata_pdc2027x 0000:00:10.0: PLL input clock 2116691 kHz
Oct 30 23:45:20 Ubuntu kernel: [   56.702418] pata_pdc2027x: Invalid PLL input clock 2116691kHz, give up!
Oct 30 23:45:20 Ubuntu kernel: [   56.703201] scsi0 : pata_pdc2027x
Oct 30 23:45:20 Ubuntu kernel: [   56.703306] scsi1 : pata_pdc2027x
Oct 30 23:45:20 Ubuntu kernel: [   56.703352] ata1: PATA max UDMA/133 cmd 0xe09017c0 ctl 0xe0901fda bmdma 0xe0901000 irq 18
Oct 30 23:45:20 Ubuntu kernel: [   56.703359] ata2: PATA max UDMA/133 cmd 0xe09015c0 ctl 0xe0901dda bmdma 0xe0901008 irq 18
Oct 30 23:45:20 Ubuntu kernel: [   56.907746] usb 1-2: new low speed USB device using uhci_hcd and address 2
Oct 30 23:45:20 Ubuntu kernel: [   56.963511] Attempting manual resume
Oct 30 23:45:20 Ubuntu kernel: [   56.963519] swsusp: Resume From Partition 3:5
Oct 30 23:45:20 Ubuntu kernel: [   56.963522] PM: Checking swsusp image.
Oct 30 23:45:20 Ubuntu kernel: [   56.963798] PM: Resume from disk failed.
Oct 30 23:45:20 Ubuntu kernel: [   57.030004] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 16 (level, low) -> IRQ 17
Oct 30 23:45:20 Ubuntu kernel: [   57.030033] ohci_hcd 0000:00:11.0: OHCI Host Controller
Oct 30 23:45:20 Ubuntu kernel: [   57.030113] ohci_hcd 0000:00:11.0: new USB bus registered, assigned bus number 3
Oct 30 23:45:20 Ubuntu kernel: [   57.030150] ohci_hcd 0000:00:11.0: irq 17, io mem 0xea007000
Oct 30 23:45:20 Ubuntu kernel: [   57.033196] kjournald starting.  Commit interval 5 seconds
Oct 30 23:45:20 Ubuntu kernel: [   57.033230] EXT3-fs: mounted filesystem with ordered data mode.
Oct 30 23:45:20 Ubuntu kernel: [   57.589951] usb usb3: configuration #1 chosen from 1 choice
Oct 30 23:45:20 Ubuntu kernel: [   57.590004] hub 3-0:1.0: USB hub found
Oct 30 23:45:20 Ubuntu kernel: [   57.590024] hub 3-0:1.0: 3 ports detected
Oct 30 23:45:20 Ubuntu kernel: [   57.596603] usb 1-2: configuration #1 chosen from 1 choice
Oct 30 23:45:20 Ubuntu kernel: [   57.871200] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00110600000035a4]
Oct 30 23:45:20 Ubuntu kernel: [   58.103104] ACPI: PCI Interrupt 0000:00:11.1[B] -> GSI 17 (level, low) -> IRQ 19
Oct 30 23:45:20 Ubuntu kernel: [   58.103132] ohci_hcd 0000:00:11.1: OHCI Host Controller
Oct 30 23:45:20 Ubuntu kernel: [   58.103179] ohci_hcd 0000:00:11.1: new USB bus registered, assigned bus number 4
Oct 30 23:45:20 Ubuntu kernel: [   58.103212] ohci_hcd 0000:00:11.1: irq 19, io mem 0xea008000
Oct 30 23:45:20 Ubuntu kernel: [   58.665174] usb usb4: configuration #1 chosen from 1 choice
Oct 30 23:45:20 Ubuntu kernel: [   58.665227] hub 4-0:1.0: USB hub found
Oct 30 23:45:20 Ubuntu kernel: [   58.665248] hub 4-0:1.0: 2 ports detected
Oct 30 23:45:20 Ubuntu kernel: [   59.178512] ACPI: PCI Interrupt 0000:00:11.2[C] -> GSI 18 (level, low) -> IRQ 16
Oct 30 23:45:20 Ubuntu kernel: [   59.178536] ehci_hcd 0000:00:11.2: EHCI Host Controller
Oct 30 23:45:20 Ubuntu kernel: [   59.178589] ehci_hcd 0000:00:11.2: new USB bus registered, assigned bus number 5
Oct 30 23:45:20 Ubuntu kernel: [   59.202048] ehci_hcd 0000:00:11.2: irq 16, io mem 0xea009000
Oct 30 23:45:20 Ubuntu kernel: [   59.202062] ehci_hcd 0000:00:11.2: USB 2.0 started, EHCI 0.95, driver 10 Dec 2004
Oct 30 23:45:20 Ubuntu kernel: [   59.202300] usb usb5: configuration #1 chosen from 1 choice
Oct 30 23:45:20 Ubuntu kernel: [   59.202351] hub 5-0:1.0: USB hub found
Oct 30 23:45:20 Ubuntu kernel: [   59.202371] hub 5-0:1.0: 5 ports detected
Oct 30 23:45:20 Ubuntu kernel: [   68.763536] Linux agpgart interface v0.102 (c) Dave Jones
Oct 30 23:45:20 Ubuntu kernel: [   68.765648] agpgart: Detected AMD 761 chipset
Oct 30 23:45:20 Ubuntu kernel: [   68.774875] agpgart: AGP aperture is 64M @ 0xe0000000
Oct 30 23:45:20 Ubuntu kernel: [   68.811961] parport_pc: VIA 686A/8231 detected
Oct 30 23:45:20 Ubuntu kernel: [   68.811969] parport_pc: probing current configuration
Oct 30 23:45:20 Ubuntu kernel: [   68.811988] parport_pc: Current parallel port base: 0x378
Oct 30 23:45:20 Ubuntu kernel: [   68.812066] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
Oct 30 23:45:20 Ubuntu kernel: [   68.890315] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Oct 30 23:45:20 Ubuntu kernel: [   68.894747] shpchp: HPC vendor_id 1022 device_id 700f ss_vid 0 ss_did 0
Oct 30 23:45:20 Ubuntu kernel: [   68.894758] shpchp: shpc_init: cannot reserve MMIO region
Oct 30 23:45:20 Ubuntu kernel: [   68.894793] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Oct 30 23:45:20 Ubuntu kernel: [   68.906848] parport_pc: VIA parallel port: io=0x378, irq=7
Oct 30 23:45:20 Ubuntu kernel: [   70.177678] Driver for 1-wire Dallas network protocol.
Oct 30 23:45:20 Ubuntu kernel: [   70.236839] matrox_w1 0000:01:05.0: Matrox G400 GPIO transport layer for 1-wire.
Oct 30 23:45:20 Ubuntu kernel: [   70.629602] input: PC Speaker as /class/input/input2
Oct 30 23:45:20 Ubuntu kernel: [   70.998835] usbcore: registered new interface driver hiddev
Oct 30 23:45:20 Ubuntu kernel: [   71.036763] input: Microsoft Microsoft Wireless Intellimouse Explorer® 1.0A as /class/input/input3
Oct 30 23:45:20 Ubuntu kernel: [   71.036892] input: USB HID v1.10 Mouse [Microsoft Microsoft Wireless Intellimouse Explorer® 1.0A] on usb-0000:00:07.2-2
Oct 30 23:45:20 Ubuntu kernel: [   71.036925] usbcore: registered new interface driver usbhid
Oct 30 23:45:20 Ubuntu kernel: [   71.036933] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Oct 30 23:45:20 Ubuntu kernel: [   71.360428] ACPI: PCI Interrupt 0000:00:0e.0[A] -> GSI 18 (level, low) -> IRQ 16
Oct 30 23:45:20 Ubuntu kernel: [   73.491555] lp0: using parport0 (interrupt-driven).
Oct 30 23:45:20 Ubuntu kernel: [   73.596369] Adding 1253028k swap on /dev/hda5.  Priority:-1 extents:1 across:1253028k
Oct 30 23:45:20 Ubuntu kernel: [   74.023771] EXT3 FS on hda1, internal journal
Oct 30 23:45:20 Ubuntu kernel: [   75.587210] input: Power Button (FF) as /class/input/input4
Oct 30 23:45:20 Ubuntu kernel: [   75.595368] ACPI: Power Button (FF) [PWRF]
Oct 30 23:45:20 Ubuntu kernel: [   75.653841] input: Power Button (CM) as /class/input/input5
Oct 30 23:45:20 Ubuntu kernel: [   75.654324] ACPI: Power Button (CM) [PWRB]
Oct 30 23:45:20 Ubuntu kernel: [   75.685817] input: Sleep Button (CM) as /class/input/input6
Oct 30 23:45:20 Ubuntu kernel: [   75.686311] ACPI: Sleep Button (CM) [SLPB]
Oct 30 23:45:20 Ubuntu kernel: [   75.855959] No dock devices found.
Oct 30 23:45:21 Ubuntu NetworkManager: <info>  eth0: Device is fully-supported using driver 'epic100'. 
Oct 30 23:45:21 Ubuntu NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 30 23:45:21 Ubuntu NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 30 23:45:21 Ubuntu NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Oct 30 23:45:21 Ubuntu NetworkManager: <info>  Deactivating device eth0. 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.579154] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1022_700e'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.606560] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1022_700f'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.607809] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_102b_525'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.609105] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1106_686'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.610280] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1106_571'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.611494] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1106_571_ide_0_0'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.612655] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1106_571_ide_0_1'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.613813] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1106_571_ide_1_0'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.615129] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1106_571_ide_1_1'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.616319] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1106_3038'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.617484] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_07_2'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.618670] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_07_2_if0'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.619839] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_45e_59_noserial'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.620994] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_45e_59_noserial_if0'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.622150] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1106_3038_0'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.623337] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_07_3'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.624488] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_07_3_if0'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.625625] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1106_3057'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.626873] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1106_3044'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.628042] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_10b8_5'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.629287] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1274_5880'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.630439] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_105a_5275'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.631620] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1033_35'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.632752] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_11_0'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.633878] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_11_0_if0'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.635040] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1033_35_0'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.636285] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_11_1'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.637424] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_11_1_if0'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.638588] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1033_e0'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.639750] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_11_2'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.640871] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_11_2_if0'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.641988] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_eisa_0'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.643267] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_floppy_0'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.644409] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.645526] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.646665] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.647806] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.648923] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_serial8250'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.650029] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.651167] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0a03'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.652281] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c02'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.653379] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0200'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.654477] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0b00'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.655619] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0800'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.656818] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c04'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.657931] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0700'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.659062] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0501'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.660160] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0501_0'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.661242] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0401'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.662316] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0303'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.663552] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.664660] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.665749] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_45e_59_noserial_if0_logicaldev_input'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.666955] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_e0_29_26_87_50'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.669653] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1274_5880_oss_pcm_1'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.670790] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1274_5880_oss_pcm_0'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.671985] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1274_5880_alsa_control__1'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.673079] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1274_5880_oss_pcm_0_0'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.674146] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1274_5880_oss_midi_0'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.681234] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1274_5880_alsa_midi_0'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.682427] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1274_5880_oss_mixer__1'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.683560] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1274_5880_alsa_capture_0'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.684630] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1274_5880_alsa_playback_0'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.685694] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1274_5880_alsa_playback_1'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.686782] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_sequencer'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.687917] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.689334] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.690500] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_timer'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.691841] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.692923] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.693996] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.695116] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.696206] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.697383] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0501_0_serial_platform_1'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.698459] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.699570] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_07_2_usbraw'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.700630] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_45e_59_noserial_usbraw'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.701680] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_07_3_usbraw'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.702888] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_11_0_usbraw'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.703978] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_11_1_usbraw'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.705022] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_11_2_usbraw'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Oct 30 23:45:21 Ubuntu NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Oct 30 23:45:21 Ubuntu NetworkManager: <info>  Will activate connection 'eth0'. 
Oct 30 23:45:21 Ubuntu NetworkManager: <info>  Device eth0 activation scheduled... 
Oct 30 23:45:21 Ubuntu NetworkManager: <info>  Activation (eth0) started... 
Oct 30 23:45:21 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 30 23:45:21 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Oct 30 23:45:21 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Oct 30 23:45:21 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Oct 30 23:45:21 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Oct 30 23:45:21 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Oct 30 23:45:21 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct 30 23:45:21 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Oct 30 23:45:21 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Oct 30 23:45:21 Ubuntu NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Oct 30 23:45:21 Ubuntu NetworkManager: <info>  Activation (eth0) failure scheduled... 
Oct 30 23:45:21 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.750701] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_floppy_0_storage'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.761201] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_WD_WMA6W2045489'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.773418] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_00305087_9b82_4803_9ecf_24f675d6f4f4'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.816942] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part2_size_1024'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.828032] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_e3ca5711_89d2_4c29_8f48_02ca332b7abb'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <debug> [1193805921.880173] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_362209924106'). 
Oct 30 23:45:21 Ubuntu NetworkManager: <info>  Activation (eth0) failed. 
Oct 30 23:45:21 Ubuntu NetworkManager: <info>  Deactivating device eth0. 
Oct 30 23:45:21 Ubuntu NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Oct 30 23:45:21 Ubuntu NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Oct 30 23:45:21 Ubuntu NetworkManager: <info>  Will activate connection 'eth0'. 
Oct 30 23:45:21 Ubuntu NetworkManager: <info>  Device eth0 activation scheduled... 
Oct 30 23:45:21 Ubuntu NetworkManager: <info>  Activation (eth0) started... 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Oct 30 23:45:22 Ubuntu NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Activation (eth0) failure scheduled... 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Oct 30 23:45:22 Ubuntu kernel: [   78.463863] NET: Registered protocol family 10
Oct 30 23:45:22 Ubuntu kernel: [   78.464049] lo: Disabled Privacy Extensions
Oct 30 23:45:22 Ubuntu NetworkManager: <debug> [1193805922.157739] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_D640417440415C7D'). 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Activation (eth0) failed. 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Deactivating device eth0. 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Oct 30 23:45:22 Ubuntu NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Will activate connection 'eth0'. 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Device eth0 activation scheduled... 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Activation (eth0) started... 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Oct 30 23:45:22 Ubuntu NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Activation (eth0) failure scheduled... 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Oct 30 23:45:22 Ubuntu NetworkManager: <debug> [1193805922.309640] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_LITE_ON_LTR_32123S'). 
Oct 30 23:45:22 Ubuntu NetworkManager: <debug> [1193805922.365110] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU0'). 
Oct 30 23:45:22 Ubuntu NetworkManager: <debug> [1193805922.369789] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_PLEXTOR_CD_R_PX_W8432T'). 
Oct 30 23:45:22 Ubuntu kernel: [   78.789888] ppdev: user-space parallel port driver
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Activation (eth0) failed. 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Deactivating device eth0. 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Oct 30 23:45:22 Ubuntu NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Will activate connection 'eth0'. 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Device eth0 activation scheduled... 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Activation (eth0) started... 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Oct 30 23:45:22 Ubuntu NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Activation (eth0) failure scheduled... 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Oct 30 23:45:22 Ubuntu kernel: [   78.928133] audit(1193805922.548:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4728 profile="/usr/sbin/cupsd"
Oct 30 23:45:22 Ubuntu kernel: [   78.995489] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Oct 30 23:45:22 Ubuntu kernel: [   78.995500] apm: overridden by ACPI.
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Activation (eth0) failed. 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Deactivating device eth0. 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Oct 30 23:45:22 Ubuntu NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Will activate connection 'eth0'. 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Device eth0 activation scheduled... 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Activation (eth0) started... 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Oct 30 23:45:22 Ubuntu NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Activation (eth0) failure scheduled... 
Oct 30 23:45:22 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Oct 30 23:45:23 Ubuntu kernel: [   79.337476] Failure registering capabilities with primary security module.
Oct 30 23:45:23 Ubuntu avahi-daemon[4930]: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
Oct 30 23:45:23 Ubuntu avahi-daemon[4930]: Successfully dropped root privileges.
Oct 30 23:45:23 Ubuntu avahi-daemon[4930]: avahi-daemon 0.6.20 starting up.
Oct 30 23:45:23 Ubuntu avahi-daemon[4930]: Successfully called chroot().
Oct 30 23:45:23 Ubuntu avahi-daemon[4930]: Successfully dropped remaining capabilities.
Oct 30 23:45:23 Ubuntu avahi-daemon[4930]: No service file found in /etc/avahi/services.
Oct 30 23:45:23 Ubuntu avahi-daemon[4930]: Network interface enumeration completed.
Oct 30 23:45:23 Ubuntu NetworkManager: <info>  Activation (eth0) failed. 
Oct 30 23:45:23 Ubuntu NetworkManager: <info>  Deactivating device eth0. 
Oct 30 23:45:23 Ubuntu NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Oct 30 23:45:23 Ubuntu NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Oct 30 23:45:23 Ubuntu NetworkManager: <info>  Will activate connection 'eth0'. 
Oct 30 23:45:23 Ubuntu NetworkManager: <info>  Device eth0 activation scheduled... 
Oct 30 23:45:23 Ubuntu NetworkManager: <info>  Activation (eth0) started... 
Oct 30 23:45:23 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 30 23:45:23 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Oct 30 23:45:23 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Oct 30 23:45:23 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Oct 30 23:45:23 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Oct 30 23:45:23 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Oct 30 23:45:23 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct 30 23:45:23 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Oct 30 23:45:23 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Oct 30 23:45:23 Ubuntu NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Oct 30 23:45:23 Ubuntu NetworkManager: <info>  Activation (eth0) failure scheduled... 
Oct 30 23:45:23 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Oct 30 23:45:23 Ubuntu avahi-daemon[4930]: Registering HINFO record with values 'I686'/'LINUX'.
Oct 30 23:45:23 Ubuntu avahi-daemon[4930]: Server startup complete. Host name is Ubuntu.local. Local service cookie is 3699617949.
Oct 30 23:45:23 Ubuntu dhcdbd: Started up.
Oct 30 23:45:23 Ubuntu hcid[4981]: Bluetooth HCI daemon
Oct 30 23:45:23 Ubuntu kernel: [   79.646714] Bluetooth: Core ver 2.11
Oct 30 23:45:23 Ubuntu kernel: [   79.646951] NET: Registered protocol family 31
Oct 30 23:45:23 Ubuntu kernel: [   79.646957] Bluetooth: HCI device and connection manager initialized
Oct 30 23:45:23 Ubuntu kernel: [   79.646963] Bluetooth: HCI socket layer initialized
Oct 30 23:45:23 Ubuntu NetworkManager: <info>  Activation (eth0) failed. 
Oct 30 23:45:23 Ubuntu NetworkManager: <info>  Deactivating device eth0. 
Oct 30 23:45:23 Ubuntu NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Oct 30 23:45:23 Ubuntu hcid[4981]: Starting SDP server
Oct 30 23:45:23 Ubuntu kernel: [   79.691305] Bluetooth: L2CAP ver 2.8
Oct 30 23:45:23 Ubuntu kernel: [   79.691315] Bluetooth: L2CAP socket layer initialized
Oct 30 23:45:23 Ubuntu hcid[4981]: Created local server at unix:abstract=/var/run/dbus-GMtKtk4fPz,guid=560da66d4767a22ebb277f0047280863
Oct 30 23:45:23 Ubuntu audio[4994]: Bluetooth Audio daemon
Oct 30 23:45:23 Ubuntu audio[4994]: Parsing /etc/bluetooth/audio.conf failed: No such file or directory
Oct 30 23:45:23 Ubuntu audio[4994]: Unix socket created: 5
Oct 30 23:45:23 Ubuntu input[4993]: Bluetooth Input daemon
Oct 30 23:45:23 Ubuntu input[4993]: Registered input manager path:/org/bluez/input
Oct 30 23:45:23 Ubuntu kernel: [   79.826464] Bluetooth: RFCOMM socket layer initialized
Oct 30 23:45:23 Ubuntu kernel: [   79.826618] Bluetooth: RFCOMM TTY layer initialized
Oct 30 23:45:23 Ubuntu kernel: [   79.826622] Bluetooth: RFCOMM ver 1.8
Oct 30 23:45:23 Ubuntu audio[4994]: add_service_record: got record id 0x10000
Oct 30 23:45:23 Ubuntu audio[4994]: add_service_record: got record id 0x10001
Oct 30 23:45:23 Ubuntu audio[4994]: Registered manager path:/org/bluez/audio
Oct 30 23:45:24 Ubuntu kernel: [   80.833986] eth0: Setting full-duplex based on MII #3 link partner capability of 45e1.
Oct 30 23:45:25 Ubuntu anacron[5061]: Anacron 2.3 started on 2007-10-30
Oct 30 23:45:25 Ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Oct 30 23:45:25 Ubuntu NetworkManager: <info>  Will activate connection 'eth0'. 
Oct 30 23:45:25 Ubuntu NetworkManager: <info>  Device eth0 activation scheduled... 
Oct 30 23:45:25 Ubuntu NetworkManager: <info>  Activation (eth0) started... 
Oct 30 23:45:25 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 30 23:45:25 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Oct 30 23:45:25 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Oct 30 23:45:25 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Oct 30 23:45:25 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Oct 30 23:45:25 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Oct 30 23:45:25 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct 30 23:45:25 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Oct 30 23:45:25 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Oct 30 23:45:25 Ubuntu /usr/sbin/cron[5118]: (CRON) INFO (pidfile fd = 3)
Oct 30 23:45:25 Ubuntu /usr/sbin/cron[5120]: (CRON) STARTUP (fork ok)
Oct 30 23:45:25 Ubuntu /usr/sbin/cron[5120]: (CRON) INFO (Running @reboot jobs)
Oct 30 23:45:25 Ubuntu kernel: [   82.251886] [drm] Initialized drm 1.1.0 20060810
Oct 30 23:45:25 Ubuntu anacron[5061]: Normal exit (0 jobs run)
Oct 30 23:45:25 Ubuntu kernel: [   82.306579] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 16 (level, low) -> IRQ 17
Oct 30 23:45:25 Ubuntu kernel: [   82.311575] [drm] Initialized mga 3.2.1 20051102 on minor 0
Oct 30 23:45:25 Ubuntu kernel: [   82.312951] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Oct 30 23:45:25 Ubuntu kernel: [   82.313390] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
Oct 30 23:45:25 Ubuntu kernel: [   82.313752] agpgart: Putting AGP V2 device at 0000:01:05.0 into 1x mode
Oct 30 23:45:26 Ubuntu NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Oct 30 23:45:26 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Oct 30 23:45:26 Ubuntu NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
Oct 30 23:45:27 Ubuntu NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
Oct 30 23:45:27 Ubuntu kernel: [   83.939417] NET: Registered protocol family 17
Oct 30 23:45:27 Ubuntu dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Oct 30 23:45:27 Ubuntu dhclient: DHCPACK from 192.168.1.1
Oct 30 23:45:27 Ubuntu avahi-daemon[4930]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.101.
Oct 30 23:45:27 Ubuntu avahi-daemon[4930]: New relevant interface eth0.IPv4 for mDNS.
Oct 30 23:45:27 Ubuntu avahi-daemon[4930]: Registering new address record for 192.168.1.101 on eth0.IPv4.
Oct 30 23:45:27 Ubuntu NetworkManager: <info>  DHCP daemon state is now 4 (reboot) for interface eth0 
Oct 30 23:45:27 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Oct 30 23:45:27 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Oct 30 23:45:27 Ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Oct 30 23:45:27 Ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Oct 30 23:45:27 Ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Oct 30 23:45:27 Ubuntu NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Oct 30 23:45:27 Ubuntu NetworkManager: <info>    address 192.168.1.101 
Oct 30 23:45:27 Ubuntu NetworkManager: <info>    netmask 255.255.255.0 
Oct 30 23:45:27 Ubuntu NetworkManager: <info>    broadcast 192.168.1.255 
Oct 30 23:45:27 Ubuntu NetworkManager: <info>    gateway 192.168.1.1 
Oct 30 23:45:27 Ubuntu NetworkManager: <info>    nameserver 68.87.72.130 
Oct 30 23:45:27 Ubuntu NetworkManager: <info>    nameserver 68.87.77.130 
Oct 30 23:45:27 Ubuntu NetworkManager: <info>    domain name 'hsd1.il.comcast.net.' 
Oct 30 23:45:27 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Oct 30 23:45:27 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Oct 30 23:45:27 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Oct 30 23:45:27 Ubuntu avahi-daemon[4930]: Withdrawing address record for 192.168.1.101 on eth0.
Oct 30 23:45:27 Ubuntu avahi-daemon[4930]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.101.
Oct 30 23:45:27 Ubuntu avahi-daemon[4930]: Interface eth0.IPv4 no longer relevant for mDNS.
Oct 30 23:45:27 Ubuntu avahi-daemon[4930]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.101.
Oct 30 23:45:27 Ubuntu avahi-daemon[4930]: New relevant interface eth0.IPv4 for mDNS.
Oct 30 23:45:27 Ubuntu avahi-daemon[4930]: Registering new address record for 192.168.1.101 on eth0.IPv4.
Oct 30 23:45:27 Ubuntu dhclient: bound to 192.168.1.101 -- renewal in 39636 seconds.
Oct 30 23:45:28 Ubuntu NetworkManager: <info>  Clearing nscd hosts cache. 
Oct 30 23:45:28 Ubuntu NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Oct 30 23:45:28 Ubuntu NetworkManager: <info>  Activation (eth0) successful, device activated. 
Oct 30 23:45:28 Ubuntu NetworkManager: <info>  Activation (eth0) Finish handler scheduled. 
Oct 30 23:45:28 Ubuntu NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Oct 30 23:45:30 Ubuntu ntpdate[5276]: adjust time server 91.189.94.4 offset -0.215221 sec
Oct 30 23:45:30 Ubuntu avahi-daemon[4930]: Registering new address record for fe80::2e0:29ff:fe26:8750 on eth0.*.
Oct 30 23:45:39 Ubuntu kernel: [   95.883030] eth0: no IPv6 routers present
Oct 30 23:45:43 Ubuntu gdm[5033]: WARNING: Couldn't authenticate user 
Oct 30 23:45:54 Ubuntu hcid[4981]: Default passkey agent (:1.21, /org/bluez/passkey) registered
Oct 30 23:45:54 Ubuntu hcid[4981]: Default authorization agent (:1.21, /org/bluez/auth) registered
Oct 30 23:46:00 Ubuntu NetworkManager: <info>  Updating allowed wireless network lists. 
Oct 30 23:46:00 Ubuntu NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
```

I'm sorry it's so long! I have no idea what to parse apart in here.

Some other, perhaps relevant info:
I'm working behind a Linksys WRT54G router that I'm using only to connect my Ubuntu PC to my Mac and to share the internet connection. 

Any ideas about where to begin looking for a problem?

Thanks so much for your help, DezSp.

---

### Post by dfreer on 2007-10-31
Wouldn't it be easier to use Torrentflux? I just started using Hamachi, looks like it would be good for remote management from behind a NAT, and should work with SSH/Torrentflux.

---

