---
title: "How do I install/use Arch?"
date: 2008-11-16
forum: Arch and derivatives
---

### Post by Newuser1111 on 2008-11-16
I think I got it installed but there's no GUI.
Did I do something wrong?

---

### Post by OutOfReach on 2008-11-16
Exactly, there is meant to be no GUI. Arch is a distro that you must build up from the foundation it gives you and make your own, that's what makes it lightweight.

I see that you already installed Arch but I would take a look at the installation guide to see if you missed anything:
[http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide](http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide)

And the beginners guide:
[http://wiki.archlinux.org/index.php/Beginners_Guide](http://wiki.archlinux.org/index.php/Beginners_Guide)

don't panic, doing all this gives you great experience and can be fun too.

---

### Post by Newuser1111 on 2008-11-17
I installed it in VirtualBox.


pacman isn't working:
```
[root@myhost ~]# pacman -S libgl
error: 'libgl': not found in sync db

```

---

### Post by SkonesMickLoud on 2008-11-17
The answer to your Arch installations issue/s answers are all found in the 2 wiki articles that OutOfReach linked.

Part of the allure of Arch is that it doesn't hold your hand.  It's user-base isn't known for holding your hand either.  If you have any questions that aren't found in the wiki, then you should ask, after you've done some homework.

---

### Post by fwojciec on 2008-11-17
> **Newuser1111 said:**
> I installed it in VirtualBox.


pacman isn't working:
```
[root@myhost ~]# pacman -S libgl
error: 'libgl': not found in sync db

```

Maybe you need to refresh pacman database with pacman -Sy first.  Also, in case you haven't done it yet, you should upgrade the system before trying to install anything (pacman -Syu).

---

### Post by Newuser1111 on 2008-11-17
I don't like Arch,
I'll try something else.

---

### Post by kerry_s on 2008-11-17
> **Newuser1111 said:**
> I don't like Arch,
I'll try something else.

arch is like any other distro, you just got to adjust to it.
first run " pacman -Sy " it's like " apt-get update " in debian.
than you can " pacman -S program-name " it's like " apt-get install " in debian. example for xorg: pacman -S xorg
which installs the main xorg stuff, so you need to pacman -Ss xf86-video
find the 1 for your card, once you have that, than Xorg -configure to give you a basic xorg.conf, i think i had to put it in the right place with cat xorg.conf.new > /etc/X11/xorg.conf, than edit it if you need to.
than you can install a wm or desktop, i went with jwm.

to search " pacman -Ss program " like " apt-cache search " in debian.
you can " man pacman " if you need to see all the commands.

i gave it a week and came right back to debian, frankly for me it was much slower than my custom debian install, udev in arch startup just takes way to long, the speed of the programs was okay but nothing special.
it was okay but debian is easier for me since i'm already so use to it.

---

### Post by medic2000 on 2008-11-17
kerry_s why do you think that udev takes that much?. Isn't it a issue in debian?

---

### Post by kerry_s on 2008-11-17
> **medic2000 said:**
> kerry_s why do you think that udev takes that much?. Isn't it a issue in debian?

no, in debian it doesn't stop at the udev line, in arch there's a 2 or 3 second delay at udev before it continues. 
maybe it's just my laptop, it is 10 years old, 450mhz 256mb ram. i'm currently running debian lenny, it does not have any pauses at boot, i just had to fix some of the kernel related things, like compiling my sound card firmware, cause debian choose to drop yamaha sound cards from kernel 2.6.23 on. debian etch ran with out any issues at all, but i wanted to go more updated on this install.
here's my dmesg if you want to have a look at what debian does, i haven't got around to a custom kernel yet:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.26-1-686 (Debian 2.6.26-8) (waldi@debian.org) (gcc version 4.1.3 20080623 (prerelease) (Debian 4.1.2-23)) #1 SMP Thu Oct 9 15:18:09 UTC 2008
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000eac00 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000fff0000 (usable)
[    0.000000]  BIOS-e820: 000000000fff0000 - 000000000ffff800 (ACPI data)
[    0.000000]  BIOS-e820: 000000000ffff800 - 0000000010000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 255MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 65520) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    65520
[    0.000000]   HighMem     65520 ->    65520
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    65520
[    0.000000] On node 0 totalpages: 65520
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 480 pages used for memmap
[    0.000000]   Normal zone: 60944 pages, LIFO batch:15
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.1 present.
[    0.000000] ACPI: RSDP 000F7120, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 0FFFC04D, 002C (r1 SONY   K1       20000204 PTL         0)
[    0.000000] ACPI: FACP 0FFFF765, 0074 (r1 SONY   K1       20000204 PTL     F4240)
[    0.000000] ACPI: DSDT 0FFFC079, 36EC (r1   SONY  K1      20000204 MSFT  1000007)
[    0.000000] ACPI: FACS 0FFFFFC0, 0040
[    0.000000] ACPI: BOOT 0FFFF7D9, 0027 (r1 SONY   A0       20000204 PTL         1)
[    0.000000] ACPI: DMI detected: Sony
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 10000000:eff80000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000eb000
[    0.000000] PM: Registered nosave memory: 00000000000eb000 - 0000000000100000
[    0.000000] SMP: Allowing 0 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 37960 bytes of per cpu data
[    0.000000] NR_CPUS: 8, nr_cpu_ids: 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 65008
[    0.000000] Kernel command line: root=/dev/hda2 ro vga=792 pci=routeirq 
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffb000 (0120c000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] Detected 446.697 MHz processor.
[    0.004000] Console: colour dummy device 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.004000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[    0.004000] Memory: 249292k/262080k available (1768k kernel code, 12312k reserved, 749k data, 244k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xfff4c000 - 0xfffff000   ( 716 kB)
[    0.004000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.004000]     vmalloc : 0xd0800000 - 0xff7fe000   ( 751 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xcfff0000   ( 255 MB)
[    0.004000]       .init : 0xc037d000 - 0xc03ba000   ( 244 kB)
[    0.004000]       .data : 0xc02ba053 - 0xc0375620   ( 749 kB)
[    0.004000]       .text : 0xc0100000 - 0xc02ba053   (1768 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.084588] Calibrating delay using timer specific routine.. 894.95 BogoMIPS (lpj=1789902)
[    0.084778] Security Framework initialized
[    0.084815] SELinux:  Disabled at boot.
[    0.084841] Capability LSM initialized
[    0.084924] Mount-cache hash table entries: 512
[    0.085488] Initializing cgroup subsys ns
[    0.085519] Initializing cgroup subsys cpuacct
[    0.085544] Initializing cgroup subsys devices
[    0.085633] CPU: L1 I cache: 16K, L1 D cache: 16K
[    0.085663] CPU: L2 cache: 256K
[    0.085687] Intel machine check architecture supported.
[    0.085716] Intel machine check reporting enabled on CPU#0.
[    0.085778] Checking 'hlt' instruction... OK.
[    0.101250] SMP alternatives: switching to UP code
[    0.120007] Freeing SMP alternatives: 16k freed
[    0.120007] ACPI: Core revision 20080321
[    0.137433] weird, boot CPU (#0) not listedby the BIOS.
[    0.137467] SMP motherboard not detected.
[    0.137489] Local APIC not detected. Using dummy APIC emulation.
[    0.137513] SMP disabled
[    0.137753] Brought up 1 CPUs
[    0.137778] Total of 1 processors activated (894.95 BogoMIPS).
[    0.137822] CPU0 attaching sched-domain:
[    0.137837]  domain 0: span 0
[    0.137847]   groups: 0
[    0.138740] net_namespace: 660 bytes
[    0.138797] Booting paravirtualized kernel on bare hardware
[    0.139987] NET: Registered protocol family 16
[    0.140693] ACPI: bus type pci registered
[    0.157469] PCI: PCI BIOS revision 2.10 entry at 0xfd99e, last bus=1
[    0.157505] PCI: Using configuration type 1 for base access
[    0.157592] Setting up standard PCI resources
[    0.167262] ACPI: EC: Look up EC in DSDT
[    0.187983] ACPI: Interpreter enabled
[    0.188040] ACPI: (supports S0 S1 S3 S4 S5)
[    0.188138] ACPI: Using PIC for interrupt routing
[    0.197462] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.249655] ACPI: EC: GPE = 0x9, I/O: command/status = 0x66, data = 0x62
[    0.249700] ACPI: EC: driver started in interrupt mode
[    0.249917] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.250542] pci 0000:00:07.3: quirk: region 8000-803f claimed by PIIX4 ACPI
[    0.250578] pci 0000:00:07.3: quirk: region 1040-104f claimed by PIIX4 SMB
[    0.250615] pci 0000:00:07.3: PIIX4 devres I PIO at 0398-0399
[    0.250642] pci 0000:00:07.3: PIIX4 devres J PIO at 0398-0399
[    0.251264] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.261824] ACPI: PCI Interrupt Link [LNKA] (IRQs *9)
[    0.262470] ACPI: PCI Interrupt Link [LNKB] (IRQs *9)
[    0.263101] ACPI: PCI Interrupt Link [LNKC] (IRQs *9)
[    0.263731] ACPI: PCI Interrupt Link [LNKD] (IRQs *9)
[    0.264370] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.264546] pnp: PnP ACPI init
[    0.264594] ACPI: bus type pnp registered
[    0.302790] pnp: PnP ACPI: found 11 devices
[    0.302830] ACPI: ACPI bus type pnp unregistered
[    0.302862] PnPBIOS: Disabled by ACPI PNP
[    0.304192] PCI: Using ACPI for IRQ routing
[    0.304222] PCI: Routing PCI interrupts for all devices because "pci=routeirq" specified
[    0.305262] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 9
[    0.305293] PCI: setting IRQ 9 as level-triggered
[    0.305304] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[    0.305356] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[    0.306307] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 9
[    0.306335] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKC] -> GSI 9 (level, low) -> IRQ 9
[    0.307286] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 9
[    0.307315] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKB] -> GSI 9 (level, low) -> IRQ 9
[    0.308312] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 9
[    0.308341] ACPI: PCI Interrupt 0000:00:0c.0[A] -> Link [LNKA] -> GSI 9 (level, low) -> IRQ 9
[    0.308391] ACPI: PCI Interrupt 0000:00:0c.1[B] -> Link [LNKB] -> GSI 9 (level, low) -> IRQ 9
[    0.308439] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 9 (level, low) -> IRQ 9
[    0.309091] ACPI: RTC can wake from S4
[    0.309233] system 00:01: ioport range 0x398-0x399 has been reserved
[    0.309266] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.309296] system 00:01: ioport range 0x1040-0x104f has been reserved
[    0.309327] system 00:01: ioport range 0x8000-0x804f could not be reserved
[    0.309395] system 00:02: iomem range 0x100000-0xfffffff could not be reserved
[    0.309432] system 00:02: iomem range 0x0-0x9ffff could not be reserved
[    0.309462] system 00:02: iomem range 0xe0000-0xfffff could not be reserved
[    0.309494] system 00:02: iomem range 0xfff80000-0xffffffff could not be reserved
[    0.309529] system 00:02: iomem range 0xfff7f600-0xfff7ffff has been reserved
[    0.341568] PCI: Bridge: 0000:00:01.0
[    0.341595]   IO window: disabled.
[    0.341618]   MEM window: 0xfe800000-0xfecfffff
[    0.341644]   PREFETCH window: 0x00000000fd000000-0x00000000fdffffff
[    0.341676] PCI: Bus 2, cardbus bridge: 0000:00:0c.0
[    0.341699]   IO window: 0x00001400-0x000014ff
[    0.341723]   IO window: 0x00001800-0x000018ff
[    0.341747]   PREFETCH window: 0x20000000-0x23ffffff
[    0.341772]   MEM window: 0x24000000-0x27ffffff
[    0.341796] PCI: Bus 6, cardbus bridge: 0000:00:0c.1
[    0.341819]   IO window: 0x00001c00-0x00001cff
[    0.341843]   IO window: 0x00002000-0x000020ff
[    0.341867]   PREFETCH window: 0x28000000-0x2bffffff
[    0.341892]   MEM window: 0x2c000000-0x2fffffff
[    0.341975] ACPI: PCI Interrupt 0000:00:0c.0[A] -> Link [LNKA] -> GSI 9 (level, low) -> IRQ 9
[    0.342052] ACPI: PCI Interrupt 0000:00:0c.1[B] -> Link [LNKB] -> GSI 9 (level, low) -> IRQ 9
[    0.342198] NET: Registered protocol family 2
[    0.342664] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.343702] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.343939] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.344200] TCP: Hash tables configured (established 8192 bind 8192)
[    0.344231] TCP reno registered
[    0.344620] NET: Registered protocol family 1
[    0.345139] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[    1.736390]  it is
[    3.297392] Freeing initrd memory: 6761k freed
[    3.298071] Simple Boot Flag at 0x35 set to 0x1
[    3.299791] audit: initializing netlink socket (disabled)
[    3.299866] type=2000 audit(1226947056.296:1): initialized
[    3.300392] Total HugeTLB memory allocated, 0
[    3.300705] VFS: Disk quotas dquot_6.5.1
[    3.300857] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    3.301067] msgmni has been set to 500
[    3.301623] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    3.301664] io scheduler noop registered
[    3.301685] io scheduler anticipatory registered
[    3.301706] io scheduler deadline registered
[    3.301769] io scheduler cfq registered (default)
[    3.301818] pci 0000:00:00.0: Limiting direct PCI/PCI transfers
[    3.301922] pci 0000:01:00.0: Boot video device
[    3.303459] vesafb: framebuffer at 0xfd000000, mapped to 0xd0880000, using 2496k, total 2496k
[    3.303505] vesafb: mode is 1024x768x24, linelength=3072, pages=0
[    3.303532] vesafb: protected mode interface info at c000:ae30
[    3.303559] vesafb: pmi: set display start = c00cae66, set palette = c00caf06
[    3.303586] vesafb: scrolling: redraw
[    3.303610] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[    3.370720] Console: switching to colour frame buffer device 128x48
[    3.437289] fb0: VESA VGA frame buffer device
[    3.438249] isapnp: Scanning for PnP cards...
[    3.750102] isapnp: No Plug & Play device found
[    3.763346] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    3.773316] brd: module loaded
[    3.774195] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUE] at 0x60,0x64 irq 1,12
[    3.778291] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.778951] serio: i8042 AUX port at 0x60,0x64 irq 12
[    3.780590] mice: PS/2 mouse device common for all mice
[    3.781841] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    3.782651] rtc0: alarms up to one month, y3k
[    3.783377] cpuidle: using governor ladder
[    3.783908] cpuidle: using governor menu
[    3.784571] No iBFT detected.
[    3.787266] TCP cubic registered
[    3.787692] NET: Registered protocol family 17
[    3.788115] Using IPI No-Shortcut mode
[    3.789258] registered taskstats version 1
[    3.790273] rtc_cmos 00:04: setting system clock to 2008-11-17 18:37:37 UTC (1226947057)
[    3.792024] Freeing unused kernel memory: 244k freed
[    3.816608] input: AT Translated Set 2 keyboard as /class/input/input0
[    4.427449] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    4.454523] ACPI: ACPI0007:00 is registered as cooling_device0
[    4.482323] ACPI: Processor [CPU0] (supports 8 throttling states)
[    4.524708] ACPI: LNXTHERM:01 is registered as thermal_zone0
[    4.555621] ACPI: Thermal Zone [ATF0] (60 C)
[    6.473204] Uniform Multi-Platform E-IDE driver
[    6.500579] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    6.739114] usbcore: registered new interface driver usbfs
[    6.767323] usbcore: registered new interface driver hub
[    6.949495] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[    7.031765] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[9]  MMIO=[fedf7000-fedf77ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    7.612610] usbcore: registered new device driver usb
[    7.923037] USB Universal Host Controller Interface driver v3.0
[    8.206917] FDC 0 is a National Semiconductor PC87306
[    8.278818] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[    8.309508] uhci_hcd 0000:00:07.2: UHCI Host Controller
[    8.339975] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[    8.371689] uhci_hcd 0000:00:07.2: irq 9, io base 0x0000fca0
[    8.404016] usb usb1: configuration #1 chosen from 1 choice
[    8.432175] hub 1-0:1.0: USB hub found
[    8.461676] hub 1-0:1.0: 2 ports detected
[    8.539143] Marking TSC unstable due to: TSC halts in idle.
[    8.592595] usb usb1: New USB device found, idVendor=1d6b, idProduct=0001
[    8.622271] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    8.651842] usb usb1: Product: UHCI Host Controller
[    8.683839] usb usb1: Manufacturer: Linux 2.6.26-1-686 uhci_hcd
[    8.713377] usb usb1: SerialNumber: 0000:00:07.2
[    8.759744] PIIX4: IDE controller (0x8086:0x7111 rev 0x01) at  PCI slot 0000:00:07.1
[    8.789665] PIIX4: not 100% native mode: will probe irqs later
[    8.819148]     ide0: BM-DMA at 0xfc90-0xfc97
[    8.851172]     ide1: BM-DMA at 0xfc98-0xfc9f
[    8.880315] Probing IDE interface ide0...
[    9.096072] usb 1-2: new low speed USB device using uhci_hcd and address 2
[    9.236192] hda: TOSHIBA MK2016GAP, ATA DISK drive
[    9.324022] usb 1-2: configuration #1 chosen from 1 choice
[    9.353629] Clocksource tsc unstable (delta = -229391344 ns)
[    9.406802] usb 1-2: New USB device found, idVendor=15d9, idProduct=0a4c
[    9.437375] usb 1-2: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[    9.468051] usb 1-2: Product:  USB OPTICAL MOUSE
[    9.605027] usbcore: registered new interface driver hiddev
[    9.636702] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[08004603002d748c]
[    9.656225] input:  USB OPTICAL MOUSE as /class/input/input1
[    9.691904] input,hidraw0: USB HID v1.11 Mouse [ USB OPTICAL MOUSE] on usb-0000:00:07.2-2
[    9.724038] usbcore: registered new interface driver usbhid
[    9.755663] usbhid: v2.6:USB HID core driver
[   10.116247] hda: host max PIO4 wanted PIO255(auto-tune) selected PIO4
[   10.116343] hda: UDMA/33 mode selected
[   10.147474] Probing IDE interface ide1...
[   10.884524] hdc: TOSHIBA DVD-ROM SD-C2202, ATAPI CD/DVD-ROM drive
[   11.584210] hdc: host max PIO4 wanted PIO255(auto-tune) selected PIO4
[   11.584522] hdc: UDMA/33 mode selected
[   11.615735] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   11.990527] ide1 at 0x170-0x177,0x376 on irq 15
[   12.038210] No dock devices found.
[   12.125715] SCSI subsystem initialized
[   12.223915] libata version 3.00 loaded.
[   12.385467] hda: max request size: 128KiB
[   12.478450] hda: 39070080 sectors (20003 MB), CHS=38760/16/63
[   12.507879] hda: cache flushes not supported
[   12.540042]  hda: hda1 hda2
[   12.597190] hdc: ATAPI 24X DVD-ROM drive, 128kB Cache
[   12.626134] Uniform CD-ROM driver Revision: 3.20
[   13.175023] PM: Starting manual resume from disk
[   17.084733] udevd version 125 started
[   22.568343] input: PC Speaker as /class/input/input2
[   23.398637] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   24.007066] Linux agpgart interface v0.103
[   24.055862] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   24.547111] Yenta: CardBus bridge found at 0000:00:0c.0 [104d:8073]
[   25.016522] Yenta: ISA IRQ mask 0x0c98, PCI irq 9
[   25.044772] Socket status: 30000006
[   25.979674] agpgart: Detected an Intel 440BX Chipset.
[   26.009794] agpgart: AGP aperture is 16M @ 0x40000000
[   26.038149] Yenta: CardBus bridge found at 0000:00:0c.1 [104d:8073]
[   26.608873] Yenta: ISA IRQ mask 0x0c98, PCI irq 9
[   26.637000] Socket status: 30000820
[   26.797608] input: PS/2 Mouse as /class/input/input3
[   26.864560] input: AlpsPS/2 ALPS GlidePoint as /class/input/input4
[   27.526425] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[   27.560024] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKC] -> GSI 9 (level, low) -> IRQ 9
[   28.030511] firmware: requesting yamaha/ds1_dsp.fw
[   28.164102] pccard: CardBus card inserted into slot 1
[   30.066221] ACPI: AC Adapter [ACAD] (on-line)
[   30.366022] sony-laptop: Sony Programmable IO Control Driver v0.6.
[   30.394163] sony-laptop: detected Type1 model
[   30.783012] input: Power Button (CM) as /class/input/input5
[   30.816020] input: Sony Vaio Keys as /class/input/input6
[   31.032815] ACPI: Power Button (CM) [PWRB]
[   31.091225] input: Sony Vaio Jogdial as /class/input/input7
[   31.204922] firmware: requesting yamaha/ds1e_ctrl.fw
[   31.345357] sony-laptop: device allocated minor is 60
[   31.610375] ACPI: Battery Slot [BAT1] (battery absent)
[   31.643651] ACPI: Battery Slot [BAT2] (battery absent)
[   31.963031] sony-laptop: Sony Notebook Control Driver v0.6.
[   32.039733] cs: IO port probe 0x100-0x3af: clean.
[   32.090292] cs: IO port probe 0x3e0-0x4ff: clean.
[   32.167123] cs: IO port probe 0x100-0x3af: clean.
[   32.340293] cs: IO port probe 0x3e0-0x4ff: clean.
[   32.396552] cs: IO port probe 0x820-0x8ff: clean.
[   32.612778] cs: IO port probe 0x820-0x8ff: clean.
[   32.648009] cs: IO port probe 0xc00-0xcf7: clean.
[   32.876259] cs: IO port probe 0xc00-0xcf7: clean.
[   32.912572] cs: IO port probe 0xa00-0xaff: clean.
[   33.151078] cs: IO port probe 0xa00-0xaff: clean.
[   33.654847] Linux Tulip driver version 1.1.15-NAPI (Feb 27, 2007)
[   33.679451] tulip 0000:06:00.0: enabling device (0000 -> 0003)
[   33.703899] ACPI: PCI Interrupt 0000:06:00.0[A] -> Link [LNKB] -> GSI 9 (level, low) -> IRQ 9
[   33.732515] PCI: Setting latency timer of device 0000:06:00.0 to 64
[   33.733130] tulip0:  MII transceiver #1 config 3000 status 786d advertising 01e1.
[   33.768290] eth0: ADMtek Comet rev 17 at Port 0x1c00, 00:30:f1:17:1e:4c, IRQ 9.
[   34.453419] udev: renamed network interface eth0 to eth1
[   35.972984] Adding 746980k swap on /dev/hda1.  Priority:-1 extents:1 across:746980k
[   36.919658] loop: module loaded

```

---

