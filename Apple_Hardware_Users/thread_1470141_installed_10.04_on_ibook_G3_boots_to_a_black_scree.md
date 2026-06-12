---
title: "installed 10.04 on ibook G3 boots to a black screen"
date: 2010-05-02
forum: Apple Hardware Users
---

### Post by ant2ne on 2010-05-02
display with liveCD was fuzzy. Hard to type and click. But I was able to install the OS with some effort. 

on first reboot I got 
> ubuntu 10.04
. . . . [ok]
then black screen

same thing when booted to Linux single. Normally, when I have display problem, it is a bad xorg.conf. Looks like 10.4 don't use xorg.conf!! There is no xorg.conf!! it seems that 10.04 trys to regen the xorg.conf file on every boot up. But it will read one if you have one. So I booted to 9.04 live CD and then created a known good /etc/X11/xorg.conf file. That is,.. it worked in 9.10!

Rebooted again. Still nothing

Booted from live CD again and did 
```
ubuntu@ubuntu:~$ sudo mkdir /mnt/root
ubuntu@ubuntu:~$ sudo mount -t ext4 /dev/sda4 /mnt/root
ubuntu@ubuntu:~$ sudo mount -t proc none /mnt/root/proc
ubuntu@ubuntu:~$ sudo mount -o bind /dev /mnt/root/dev
ubuntu@ubuntu:~$ sudo chroot /mnt/root /bin/bash
ubuntu@ubuntu:~$ sudo apt-get update && sudo apt-get install openssh-server
```

Now I can at least ssh into the darn thing and dont' have to boot from the live CD!

While SSHing; I tried a dpkg-reconfigure xserver-xorg, and it let me boot to a fuzzy hard to read gnome,.. once. But on reboot it was back to black.

Here is my lspci
> 0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth/Pangea AGP
0000:00:10.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth/Pangea PCI
0001:10:17.0 Class ff00: Apple Computer Inc. KeyLargo/Pangea Mac I/O
0001:10:18.0 USB Controller: Apple Computer Inc. KeyLargo/Pangea USB
0001:10:19.0 USB Controller: Apple Computer Inc. KeyLargo/Pangea USB
0002:20:0b.0 Host bridge: Apple Computer Inc. UniNorth/Pangea Internal PCI
0002:20:0e.0 FireWire (IEEE 1394): Apple Computer Inc. UniNorth/Pangea FireWire
0002:20:0f.0 Ethernet controller: Apple Computer Inc. UniNorth/Pangea GMAC (Sun G

Here is my xorg.conf
> Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"speedo"
	Load	"type1"
	Load	"v4l"
	Load	"vbe"
	Load	"xtt"
	Load	"aiptek"
EndSection


Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility 7500 M7 (RV200 LW)"
	Driver		"ati"
	BusID		"PCI:0:16:0"
	Option		"UseFBDev"		"true"
	# Added by zombie 11/04/05 - Disabled as it works, but very very slow.
	#Option		"backingstore"              "true"
	#Option 	"AllowGLXWithComposite" "true"
	#
EndSection

Section "Monitor"
	Identifier	"Color LCD"
	HorizSync	28-49
	VertRefresh	43-72
	Option		"DPMS"
	DisplaySize	270	203	# 1024x768 96dpi
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility 7500 M7 (RV200 LW)"
	Monitor		"Color LCD"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection


#Section "DRI"
#	Mode	0666
#EndSection


Here is my dmesg
> [    0.000000] Using PowerMac machine description
[    0.000000] Total memory = 640MB; using 2048kB for hash table (at cfe00000)
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Linux version 2.6.32-21-powerpc (buildd@ross) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #32-Ubuntu Fri Apr 16 08:10:47 UTC 2010 (Ubuntu 2.6.32-21.32-powerpc 2.6.32.11+drm33.2)
[    0.000000] Found initrd at 0xc1d00000:0xc2596000
[    0.000000] Found UniNorth memory controller & host bridge @ 0xf8000000 revision: 0xc0
[    0.000000] Mapped at 0xff7c0000
[    0.000000] Found a Pangea mac-io controller, rev: 0, mapped at 0xff740000
[    0.000000] Processor NAP mode on idle enabled.
[    0.000000] PowerMac motherboard: iBook 2 rev. 2
[    0.000000] via-pmu: Server Mode is disabled
[    0.000000] PMU driver v2 initialized for Core99, firmware: 0c
[    0.000000] bootconsole [udbg0] enabled
[    0.000000] Found UniNorth PCI host bridge at 0x00000000f0000000. Firmware bus number: 0->0
[    0.000000] PCI host bridge /pci@f0000000  ranges:
[    0.000000]  MEM 0x00000000f1000000..0x00000000f1ffffff -> 0x00000000f1000000 
[    0.000000]   IO 0x00000000f0000000..0x00000000f07fffff -> 0x0000000000000000
[    0.000000]  MEM 0x0000000090000000..0x000000009fffffff -> 0x0000000090000000 
[    0.000000] Found UniNorth PCI host bridge at 0x00000000f2000000. Firmware bus number: 0->0
[    0.000000] PCI host bridge /pci@f2000000 (primary) ranges:
[    0.000000]  MEM 0x00000000f3000000..0x00000000f3ffffff -> 0x00000000f3000000 
[    0.000000]   IO 0x00000000f2000000..0x00000000f27fffff -> 0x0000000000000000
[    0.000000]  MEM 0x0000000080000000..0x000000008fffffff -> 0x0000000080000000 
[    0.000000] Found UniNorth PCI host bridge at 0x00000000f4000000. Firmware bus number: 0->0
[    0.000000] PCI host bridge /pci@f4000000  ranges:
[    0.000000]  MEM 0x00000000f5000000..0x00000000f5ffffff -> 0x00000000f5000000 
[    0.000000]   IO 0x00000000f4000000..0x00000000f47fffff -> 0x0000000000000000
[    0.000000] nvram: Checking bank 0...
[    0.000000] nvram: gen0=346, gen1=347
[    0.000000] nvram: Active bank is: 1
[    0.000000] nvram: OF partition at 0x410
[    0.000000] nvram: XP partition at 0x1020
[    0.000000] nvram: NR partition at 0x1120
[    0.000000] Top of RAM: 0x28000000, Total RAM: 0x28000000
[    0.000000] Memory hole size: 0MB
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00028000
[    0.000000]   Normal   0x00028000 -> 0x00028000
[    0.000000]   HighMem  0x00028000 -> 0x00028000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00028000
[    0.000000] On node 0 totalpages: 163840
[    0.000000] free_area_init_node: node 0, pgdat c073c9cc, node_mem_map c07d4000
[    0.000000]   DMA zone: 1280 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 162560 pages, LIFO batch:31
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 162560
[    0.000000] Kernel command line: root=/dev/hda3 ro quiet splash video=ofonly 
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] High memory: 0k
[    0.000000] Memory: 630016k/655360k available (7200k kernel code, 24968k reserved, 280k data, 481k bss, 336k init)
[    0.000000] Kernel virtual memory layout:
[    0.000000]   * 0xfffef000..0xfffff000  : fixmap
[    0.000000]   * 0xff800000..0xffc00000  : highmem PTEs
[    0.000000]   * 0xfdf32000..0xff800000  : early ioremap
[    0.000000]   * 0xe9000000..0xfdf32000  : vmalloc & ioremap
[    0.000000] SLUB: Genslabs=13, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:512
[    0.000000] mpic: Setting up MPIC " MPIC 1   " version 1.2 at 80040000, max 4 CPUs
[    0.000000] mpic: ISU size: 64, shift: 6, mask: 3f
[    0.000000] mpic: Initializing for 64 sources
[    0.000000] GMT Delta read from XPRAM: 0 minutes, DST: off
[    0.000000] time_init: decrementer frequency = 24.835277 MHz
[    0.000000] time_init: processor frequency   = 800.000000 MHz
[    0.000000] clocksource: timebase mult[a10fac1] shift[22] registered
[    0.000000] clockevent: decrementer mult[65b9ace] shift[32] cpu[0]
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled, bootconsole disabled
[    0.000260] Security Framework initialized
[    0.000371] AppArmor: AppArmor initialized
[    0.000394] Mount-cache hash table entries: 512
[    0.000994] device-tree: Duplicate name in /cpus/PowerPC,750@0, renamed to "l2-cache#1"
[    0.002293] device-tree: Duplicate name in /pci@f2000000/mac-io@17/gpio@50, renamed to "extint-gpio4@5c#1"
[    0.003497] Initializing cgroup subsys ns
[    0.003513] Initializing cgroup subsys devices
[    0.003523] Initializing cgroup subsys freezer
[    0.003530] Initializing cgroup subsys net_cls
[    0.003566] ftrace: allocating 17431 entries in 52 pages
[    0.015412] devtmpfs: initialized
[    0.016577] regulator: core version 0.5
[    0.016798] NET: Registered protocol family 16
[    0.017438] irq: irq 42 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 42
[    0.017522] KeyWest i2c @0xf8001003 irq 42 /uni-n@f8000000/i2c@f8001000
[    0.017536]  channel 0 bus <multibus>
[    0.017541]  channel 1 bus <multibus>
[    0.017587] irq: irq 26 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 26
[    0.017679] KeyWest i2c @0x80018000 irq 26 /pci@f2000000/mac-io@17/i2c@18000
[    0.017688]  channel 0 bus <multibus>
[    0.017713] PMU i2c /pci@f2000000/mac-io@17/via-pmu@16000/pmu-i2c
[    0.017721]  channel 1 bus <multibus>
[    0.017727]  channel 2 bus <multibus>
[    0.017801] irq: irq 25 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 25
[    0.017833] irq: irq 47 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 47
[    0.018002] PCI: Probing PCI hardware
[    0.018265] pci 0000:00:10.0: reg 10 32bit mmio pref: [0x98000000-0x9fffffff]
[    0.018277] pci 0000:00:10.0: reg 14 io port: [0x400-0x4ff]
[    0.018288] pci 0000:00:10.0: reg 18 32bit mmio: [0x90000000-0x9000ffff]
[    0.018307] pci 0000:00:10.0: reg 30 32bit mmio pref: [0x90020000-0x9003ffff]
[    0.018335] pci 0000:00:10.0: supports D1 D2
[    0.018404] irq: irq 48 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 48
[    0.018714] pci 0001:10:17.0: reg 10 32bit mmio: [0x80000000-0x8007ffff]
[    0.018785] pci 0001:10:18.0: reg 10 32bit mmio: [0x80081000-0x80081fff]
[    0.018830] pci 0001:10:18.0: supports D1 D2
[    0.018837] pci 0001:10:18.0: PME# supported from D1 D2 D3hot
[    0.018848] pci 0001:10:18.0: PME# disabled
[    0.018890] pci 0001:10:19.0: reg 10 32bit mmio: [0x80080000-0x80080fff]
[    0.018935] pci 0001:10:19.0: supports D1 D2
[    0.018942] pci 0001:10:19.0: PME# supported from D1 D2 D3hot
[    0.018950] pci 0001:10:19.0: PME# disabled
[    0.019001] irq: irq 27 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 27
[    0.019029] irq: irq 28 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 28
[    0.019398] pci 0002:20:0e.0: reg 10 32bit mmio: [0xf5000000-0xf5000fff]
[    0.019434] pci 0002:20:0e.0: supports D1 D2
[    0.019441] pci 0002:20:0e.0: PME# supported from D0 D1 D2 D3hot
[    0.019448] pci 0002:20:0e.0: PME# disabled
[    0.019478] pci 0002:20:0f.0: reg 10 32bit mmio: [0xf5200000-0xf53fffff]
[    0.019502] pci 0002:20:0f.0: reg 30 32bit mmio pref: [0xf5100000-0xf51fffff]
[    0.019559] irq: irq 40 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 40
[    0.019586] irq: irq 41 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 41
[    0.019845] PCI 0000:00 Cannot reserve Legacy IO [0x802000-0x802fff]
[    0.019869] pci_bus 0000:00: resource 0 io:  [0x802000-0x1001fff]
[    0.019878] pci_bus 0000:00: resource 1 mem: [0xf1000000-0xf1ffffff]
[    0.019886] pci_bus 0000:00: resource 2 mem: [0x90000000-0x9fffffff]
[    0.019894] pci_bus 0001:10: resource 0 io:  [0x00-0x7fffff]
[    0.019902] pci_bus 0001:10: resource 1 mem: [0xf3000000-0xf3ffffff]
[    0.019910] pci_bus 0001:10: resource 2 mem: [0x80000000-0x8fffffff]
[    0.019918] pci_bus 0002:20: resource 0 io:  [0xff7fe000-0xffffdfff]
[    0.019926] pci_bus 0002:20: resource 1 mem: [0xf5000000-0xf5ffffff]
[    0.023900] bio: create slab <bio-0> at 0
[    0.024453] vgaarb: device added: PCI:0000:00:10.0,decodes=io+mem,owns=mem,locks=none
[    0.024473] vgaarb: loaded
[    0.024909] SCSI subsystem initialized
[    0.025122] libata version 3.00 loaded.
[    0.025406] usbcore: registered new interface driver usbfs
[    0.025447] usbcore: registered new interface driver hub
[    0.025606] usbcore: registered new device driver usb
[    0.026160] NetLabel: Initializing
[    0.026168] NetLabel:  domain hash size = 128
[    0.026173] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.026234] NetLabel:  unlabeled traffic allowed by default
[    0.026249] Switching to clocksource timebase
[    0.032541] AppArmor: AppArmor Filesystem Enabled
[    0.033316] NET: Registered protocol family 2
[    0.033587] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.035348] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.042536] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[    0.044310] TCP: Hash tables configured (established 131072 bind 65536)
[    0.044320] TCP reno registered
[    0.044851] NET: Registered protocol family 1
[    0.045379] Thermal assist unit using timers, shrink_timer: 500 jiffies
[    0.045893] Registering PowerMac CPU frequency driver
[    0.045901] Low: 400 Mhz, High: 800 Mhz, Boot: 800 Mhz
[    0.046513] audit: initializing netlink socket (disabled)
[    0.046593] type=2000 audit(1272831705.040:1): initialized
[    0.063551] Trying to unpack rootfs image as initramfs...
[    0.094481] VFS: Disk quotas dquot_6.5.2
[    0.094883] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.095986] fuse init (API version 7.13)
[    0.096376] msgmni has been set to 1231
[    0.102808] alg: No test for stdrng (krng)
[    0.103187] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.103200] io scheduler noop registered
[    0.103206] io scheduler anticipatory registered
[    0.103213] io scheduler deadline registered
[    0.103402] io scheduler cfq registered (default)
[    0.108643] Generic non-volatile memory driver v1.1
[    0.108872] Using unsupported 1024x768 ATY,Bee_A at 9c008000, depth=8, pitch=1024
[    0.124990] Console: switching to colour frame buffer device 128x48
[    0.140391] fb0: Open Firmware frame buffer device on /pci@f0000000/ATY,BeeParent@10/ATY,Bee_A
[    0.174810] Using unsupported 640x480 ATY,Bee_B at 99008000, depth=8, pitch=768
[    0.175286] fb1: Open Firmware frame buffer device on /pci@f0000000/ATY,BeeParent@10/ATY,Bee_B
[    0.183035] brd: module loaded
[    0.183194] MacIO PCI driver attached to Pangea chipset
[    0.183730] irq: irq 32 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 32
[    0.183995] irq: irq 19 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 19
[    0.184015] irq: irq 11 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 16
[    0.184104] irq: irq 57 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 57
[    0.184206] irq: irq 22 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 22
[    0.184226] irq: irq 5 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 17
[    0.184244] irq: irq 6 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 18
[    0.184378] irq: irq 23 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 23
[    0.184397] irq: irq 7 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 20
[    0.184416] irq: irq 8 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 21
[    0.184847] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    0.185456] Uniform Multi-Platform E-IDE driver
[    0.190427] adb: starting probe task...
[    0.447048] adb devices: [2]: 2 c3 [3]: 3 1 [7]: 7 1f
[    0.454619] ADB keyboard at 2, handler 1
[    0.454687] Detected ADB keyboard, type ANSI.
[    0.454972] input: ADB keyboard as /devices/virtual/input/input1
[    0.455129] input: ADB Powerbook buttons as /devices/virtual/input/input2
[    0.470803] ADB mouse at 3, handler set to 4 (trackpad)
[    0.531007] input: ADB mouse as /devices/virtual/input/input3
[    0.531040] adb: finished probe task...
[    0.653585] Freeing initrd memory: 8792k freed
[    1.202301] ide-pmac: Found Apple KeyLargo ATA-4 controller (macio), bus ID 2, irq 19
[    1.202394] Probing IDE interface ide0...
[    1.490598] hda: TOSHIBA MK3021GAS, ATA DISK drive
[    1.994277] hdb: QSI CD-ROM SCR-242, ATAPI CD/DVD-ROM drive
[    1.994547] hda: host max PIO4 wanted PIO255(auto-tune) selected PIO4
[    1.994630] hda: host side 80-wire cable detection failed, limiting max speed to UDMA33
[    1.994640] hda: UDMA/33 mode selected
[    1.994704] hdb: host max PIO4 wanted PIO255(auto-tune) selected PIO4
[    1.994762] hdb: MWDMA2 mode selected
[    1.994924] ide0 at 0xe902e000-0xe902e070,0xe902e160 on irq 19
[    1.995233] ide-gd driver 1.18
[    1.995308] hda: max request size: 128KiB
[    2.447435] hda: 58605120 sectors (30005 MB), CHS=58140/16/63
[    2.447562] hda: cache flushes supported
[    2.447826]  hda: [mac] hda1 hda2 hda3 hda4 hda5 hda6
[    2.548115] ide-cd driver 5.00
[    2.554091] ide-cd: hdb: ATAPI 24X CD-ROM drive, 128kB Cache
[    2.554110] Uniform CD-ROM driver Revision: 3.20
[    2.583946] Fixed MDIO Bus: probed
[    2.583971] tun: Universal TUN/TAP device driver, 1.6
[    2.583978] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    2.584309] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.584379] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.584486] ohci_hcd 0001:10:18.0: enabling device (0000 -> 0002)
[    2.584544] ohci_hcd 0001:10:18.0: OHCI Host Controller
[    2.584669] ohci_hcd 0001:10:18.0: new USB bus registered, assigned bus number 1
[    2.584750] ohci_hcd 0001:10:18.0: irq 27, io mem 0x80081000
[    2.657989] usb usb1: configuration #1 chosen from 1 choice
[    2.658128] hub 1-0:1.0: USB hub found
[    2.658188] hub 1-0:1.0: 2 ports detected
[    2.658388] ohci_hcd 0001:10:19.0: enabling device (0000 -> 0002)
[    2.658420] ohci_hcd 0001:10:19.0: OHCI Host Controller
[    2.658595] ohci_hcd 0001:10:19.0: new USB bus registered, assigned bus number 2
[    2.658647] ohci_hcd 0001:10:19.0: irq 28, io mem 0x80080000
[    2.733913] usb usb2: configuration #1 chosen from 1 choice
[    2.733996] hub 2-0:1.0: USB hub found
[    2.734045] hub 2-0:1.0: 2 ports detected
[    2.734177] uhci_hcd: USB Universal Host Controller Interface driver
[    2.735001] mice: PS/2 mouse device common for all mice
[    2.735197] PowerMac i2c bus pmu 2 registered
[    2.735255] PowerMac i2c bus pmu 1 registered
[    2.735310] PowerMac i2c bus mac-io 0 registered
[    2.735364] PowerMac i2c bus uni-n 1 registered
[    2.735430] PowerMac i2c bus uni-n 0 registered
[    2.736857] TCP cubic registered
[    2.736870] NET: Registered protocol family 17
[    2.737268] registered taskstats version 1
[    2.737759] input: PMU as /devices/virtual/input/input4
[    2.737839] Registered led device: pmu-led::front
[    2.737854] /build/buildd/linux-2.6.32/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[    2.737916] Freeing unused kernel memory: 336k init
[    2.831104] udev: starting version 151
[    3.523283] sungem.c:v0.98 8/24/03 David S. Miller (davem@redhat.com)
[    3.590781] PHY ID: 4061e4, addr: 0
[    3.592656] eth0: Sun GEM (PCI) 10/100/1000BaseT Ethernet 00:0a:95:86:16:b6
[    3.592669] eth0: Found BCM5221 PHY
[    3.660467] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[40]  MMIO=[f5000000-f50007ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    3.775008] EXT4-fs (hda3): INFO: recovery required on readonly filesystem
[    3.775035] EXT4-fs (hda3): write access will be enabled during recovery
[    3.934534] EXT4-fs (hda3): recovery complete
[    3.935962] EXT4-fs (hda3): mounted filesystem with ordered data mode
[    4.942759] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000a95fffe8616b6]
[    5.990501] eth0: Link is up at 100 Mbps, full-duplex.
[   16.410360] Adding 1253368k swap on /dev/hda4.  Priority:-1 extents:1 across:1253368k 
[   16.556292] udev: starting version 151
[   17.195896] Linux agpgart interface v0.103
[   17.347191] agpgart-uninorth 0000:00:0b.0: Apple UniNorth/Pangea chipset
[   17.349805] agpgart-uninorth 0000:00:0b.0: configuring for size idx: 64
[   17.350178] agpgart-uninorth 0000:00:0b.0: AGP aperture is 256M @ 0x0
[   17.991909] type=1505 audit(1272831722.983:2):  operation="profile_load" pid=363 name="/sbin/dhclient3"
[   17.992813] type=1505 audit(1272831722.983:3):  operation="profile_load" pid=363 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   17.993304] type=1505 audit(1272831722.983:4):  operation="profile_load" pid=363 name="/usr/lib/connman/scripts/dhclient-script"
[   18.193775] [drm] Initialized drm 1.1.0 20060810
[   18.234914] rtc-generic rtc-generic: rtc core: registered rtc-generic as rtc0
[   18.490593] pmac_zilog: 0.6 (Benjamin Herrenschmidt <benh@kernel.crashing.org>)
[   18.490877] ttyPZ0 at MMIO 0x80013020 (irq = 22) is a Z85c30 ESCC - Serial port
[   18.517879] ttyPZ1 at MMIO 0x80013000 (irq = 23) is a Z85c30 ESCC - Serial port
[   19.060447] cfg80211: Calling CRDA to update world regulatory domain
[   19.128910] cfg80211: World regulatory domain updated:
[   19.128938] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   19.128950] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.128959] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.128967] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.128976] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.128985] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.464052] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   19.909868] type=1505 audit(1272831724.899:5):  operation="profile_load" pid=496 name="/usr/share/gdm/guest-session/Xsession"
[   19.957707] type=1505 audit(1272831724.947:6):  operation="profile_replace" pid=497 name="/sbin/dhclient3"
[   19.983076] type=1505 audit(1272831724.975:7):  operation="profile_replace" pid=497 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   19.983692] type=1505 audit(1272831724.975:8):  operation="profile_replace" pid=497 name="/usr/lib/connman/scripts/dhclient-script"
[   20.012215] [drm] radeon defaulting to kernel modesetting.
[   20.012235] [drm] radeon kernel modesetting enabled.
[   20.012491] radeon 0000:00:10.0: enabling device (0086 -> 0087)
[   20.100489] [drm] radeon: Initializing kernel modesetting.
[   20.110582] [drm] register mmio base: 0x90000000
[   20.110603] [drm] register mmio size: 65536
[   20.110783] radeon 0000:00:10.0: Invalid ROM contents
[   20.110824] radeon 0000:00:10.0: Invalid ROM contents
[   20.110836] [drm:radeon_get_bios] *ERROR* Unable to locate a BIOS ROM
[   20.111051] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
[   20.111063] [drm] Using generic clock info
[   20.111185] agpgart-uninorth 0000:00:0b.0: putting AGP V2 device into 2x mode
[   20.111198] radeon 0000:00:10.0: putting AGP V2 device into 2x mode
[   20.111250] [drm] radeon: VRAM 64M
[   20.111255] [drm] radeon: VRAM from 0x10000000 to 0x13FFFFFF
[   20.111262] [drm] radeon: GTT 256M
[   20.111267] [drm] radeon: GTT from 0x00000000 to 0x0FFFFFFF
[   20.111380] [drm] radeon: irq initialized.
[   20.111389] [drm] Detected VRAM RAM=64M, BAR=128M
[   20.111395] [drm] RAM width 64bits DDR
[   20.113425] [TTM] Zone  kernel: Available graphics memory: 319760 kiB.
[   20.113533] [drm] radeon: 32M of VRAM memory ready
[   20.113542] [drm] radeon: 256M of GTT memory ready.
[   20.113876] [drm] radeon: cp idle (0x00008383)
[   20.116932] [drm] Loading R100 Microcode
[   20.119277] platform radeon_cp.0: firmware: requesting radeon/R100_cp.bin
[   20.276784] [drm] radeon: ring at 0x0000000000000000
[   20.276839] [drm] ring test succeeded in 0 usecs
[   20.308331] type=1505 audit(1272831725.299:9):  operation="profile_load" pid=498 name="/usr/bin/evince"
[   20.311984] [drm] radeon: ib pool ready.
[   20.350956] eth0: Link is up at 100 Mbps, full-duplex.
[   20.350978] eth0: Pause is disabled
[   20.396107] type=1505 audit(1272831725.387:10):  operation="profile_load" pid=498 name="/usr/bin/evince-previewer"
[   20.456982] type=1505 audit(1272831725.447:11):  operation="profile_load" pid=498 name="/usr/bin/evince-thumbnailer"
[   21.004853] NET: Registered protocol family 10
[   21.006033] lo: Disabled Privacy Extensions
[   21.047872] airport 0.15 (Benjamin Herrenschmidt <benh@kernel.crashing.org>)
[   21.048042] airport: Physical address 80030000
[   22.008147] irq: irq 1 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 24
[   22.008220] irq: irq 2 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 29
[   22.035996] irq: irq 58 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 58
[   22.413625] airport 0.00030000:radio: Hardware identity 0005:0001:0001:0002
[   22.413757] airport 0.00030000:radio: Station identity  001f:0001:0008:0046
[   22.413769] airport 0.00030000:radio: Firmware determined as Lucent/Agere 8.70
[   22.459751] input: PowerMac Beep as /devices/pci0001:10/0001:10:17.0/input/input5
[   22.697517] Unable to handle kernel paging request for data at address 0x00000000
[   22.697539] Faulting instruction address: 0xc05233c0
[   22.697556] Oops: Kernel access of bad area, sig: 11 [#1]
[   22.697567] PowerMac
[   22.697572] Modules linked in: snd_aoa_i2sbus(+) snd_powermac snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer airport(+) snd_seq_device ipv6 radeon(+) orinoco snd ttm cfg80211 drm_kms_helper pmac_zilog serial_core evdev rfkill snd_aoa_soundbus rtc_generic soundcore drm uninorth_agp agpgart snd_page_alloc ohci1394 sungem ieee1394 sungem_phy windfarm_core
[   22.697654] NIP: c05233c0 LR: c0523840 CTR: c05237f4
[   22.697667] REGS: e057dd80 TRAP: 0300   Not tainted  (2.6.32-21-powerpc)
[   22.697673] MSR: 00009032 <EE,ME,IR,DR>  CR: 24000428  XER: 00000000
[   22.697690] DAR: 00000000, DSISR: 42000000
[   22.697698] TASK = e0ac5d00[633] 'Xorg' THREAD: e057c000
[   22.697704] GPR00: e057de3c e057de30 e0ac5d00 c22ee64c e9593e34 00000000 e95aa304 00000279 
[   22.697720] GPR08: 0000e200 00000000 0000007f ffffffff 24000422 101f6984 101ee9a8 101ee9ac 
[   22.697736] GPR16: 00000000 10732a10 00000001 101eec84 101eeb60 00000000 101ea62c c22ee400 
[   22.697752] GPR24: 00009032 c22ee5d0 c22ee650 e068f5f4 e95a9310 e0ac5d00 c22ee64c e057de30 
[   22.697802] NIP [c05233c0] __mutex_lock_slowpath+0x58/0x114
[   22.697811] LR [c0523840] mutex_lock+0x4c/0x68
[   22.697818] Call Trace:
[   22.697832] [e057de30] [c2359540] 0xc2359540 (unreliable)
[   22.697844] [e057de60] [c0523840] mutex_lock+0x4c/0x68
[   22.697967] [e057de70] [e959f0a8] drm_fb_release+0x4c/0xec [drm]
[   22.697992] [e057de90] [e9593224] drm_release+0x484/0x4ec [drm]
[   22.698008] [e057ded0] [c013fb88] __fput+0x11c/0x270
[   22.698017] [e057df00] [c013fd1c] fput+0x40/0x58
[   22.698040] [e057df10] [c013ae1c] filp_close+0x84/0xcc
[   22.698049] [e057df30] [c013af08] sys_close+0xa4/0xdc
[   22.698065] [e057df40] [c001a448] ret_from_syscall+0x0/0x38
[   22.698076] --- Exception: c01 at 0xff5a858
[   22.698080]     LR = 0xf931990
[   22.698085] Instruction dump:
[   22.698092] 93c10028 93e1002c 7c3f0b78 81230008 381f000c 3b430004 3960ffff 90030008 
[   22.698107] 7c7e1b78 935f000c 7c5d1378 913f0010 <90090000> 917f0008 905f0014 801f0008 
[   22.698134] ---[ end trace 1899f7c8536d8f5c ]---
[   22.730431] airport 0.00030000:radio: firmware: requesting agere_sta_fw.bin
[   22.864656] airport 0.00030000:radio: Hardware identity 0005:0001:0001:0002
[   22.864796] airport 0.00030000:radio: Station identity  001f:0002:0009:0030
[   22.864808] airport 0.00030000:radio: Firmware determined as Lucent/Agere 9.48
[   22.864817] airport 0.00030000:radio: Ad-hoc demo mode supported
[   22.864824] airport 0.00030000:radio: IEEE standard IBSS ad-hoc mode supported
[   22.864832] airport 0.00030000:radio: WEP supported, 104-bit key
[   22.864839] airport 0.00030000:radio: WPA-PSK supported
[   22.874458] [drm:radeon_fence_wait] *ERROR* fence(e04b1420:0x00000001) 556ms timeout going to reset GPU
[   22.875849] [drm] CP reset succeed (RBBM_STATUS=0x00000140)
[   22.875860] [drm] radeon: cp idle (0x00008080)
[   22.875926] [drm] radeon: ring at 0x0000000000000000
[   23.017467] [drm:r100_ring_test] *ERROR* radeon: ring test failed (sracth(0x15E8)=0xCAFEDEAD)
[   23.017478] [drm:r100_cp_init] *ERROR* radeon: cp isn't working (-22).
[   23.017487] [drm:r100_gpu_reset] *ERROR* Failed to reset GPU (RBBM_STATUS=0x80010140)
[   23.017500] [drm:radeon_fence_wait] *ERROR* fence(e04b1420:0x00000001) 704ms timeout
[   23.017508] [drm:radeon_fence_wait] *ERROR* last signaled fence(0x00000001)
[   23.158965] [drm:r100_ib_test] *ERROR* radeon: ib test failed (sracth(0x15E4)=0xCAFEDEAD)
[   23.719680] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   23.774021] apm_emu: PMU APM Emulation initialized.
[   24.106339] radeon 0000:00:10.0: failled testing IB (-22).
[   24.106654] radeon 0000:00:10.0: failled initializing IB (-22).
[   24.106663] radeon 0000:00:10.0: Disabling GPU acceleration
[   24.247878] [drm:r100_cp_fini] *ERROR* Wait for CP idle timeout, shutting down CP.
[   24.498603] [drm] radeon: cp finalized
[   24.498900] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
[   24.498914] [drm] radeon: cp finalized
[   24.499185] [TTM] Zone  kernel: Used memory at exit: 0 kiB.
[   24.499197] [drm] radeon: ttm finalized
[   24.499205] [drm] Forcing AGP to PCI mode
[   24.499302] radeon 0000:00:10.0: Invalid ROM contents
[   24.499344] radeon 0000:00:10.0: Invalid ROM contents
[   24.499355] [drm:radeon_get_bios] *ERROR* Unable to locate a BIOS ROM
[   24.499565] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
[   24.499578] [drm] Using generic clock info
[   24.499623] [drm] radeon: VRAM 64M
[   24.499629] [drm] radeon: VRAM from 0x00000000 to 0x03FFFFFF
[   24.499635] [drm] radeon: GTT 512M
[   24.499640] [drm] radeon: GTT from 0x20000000 to 0x3FFFFFFF
[   24.499718] [drm] radeon: irq initialized.
[   24.499726] [drm] Detected VRAM RAM=64M, BAR=128M
[   24.499734] [drm] RAM width 64bits DDR
[   24.500022] [TTM] Zone  kernel: Available graphics memory: 319760 kiB.
[   24.500108] [drm] radeon: 32M of VRAM memory ready
[   24.500116] [drm] radeon: 512M of GTT memory ready.
[   24.500128] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   24.506185] [drm] radeon: cp idle (0x00008080)
[   24.526926] [drm] radeon: ring at 0x0000000020000000
[   24.526982] [drm] ring test succeeded in 0 usecs
[   24.527420] [drm] radeon: ib pool ready.
[   24.527514] [drm] ib test succeeded in 0 usecs
[   24.527705] [drm] Connector Table: 2 (ibook)
[   24.527736] [drm] Panel info derived from registers
[   24.527744] [drm] Panel Size 1024x768
[   24.538066] [drm] Radeon Display Connectors
[   24.538084] [drm] Connector 0:
[   24.538091] [drm]   LVDS
[   24.538100] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
[   24.538106] [drm]   Encoders:
[   24.538112] [drm]     LCD1: INTERNAL_LVDS
[   24.538117] [drm] Connector 1:
[   24.538122] [drm]   VGA
[   24.538129] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[   24.538134] [drm]   Encoders:
[   24.538139] [drm]     CRT2: INTERNAL_DAC2
[   24.538144] [drm] Connector 2:
[   24.538148] [drm]   S-video
[   24.538152] [drm]   Encoders:
[   24.538156] [drm]     TV1: INTERNAL_DAC2
[   24.920332] hda: host max PIO4 wanted PIO0 selected PIO0
[   25.087584] [drm] Determined LVDS native mode details from EDID
[   25.139211] [drm] fb mappable at 0x98040000
[   25.139229] [drm] vram apper at 0x98000000
[   25.139234] [drm] size 786432
[   25.139239] [drm] fb depth is 8
[   25.139244] [drm]    pitch is 1024
[   25.238780] fb: conflicting fb hw usage radeondrmfb vs OFfb ATY,Bee_B - removing generic driver
[   25.250512] Trying to free nonexistent resource <0000000099008000-0000000099061fff>
[   25.251606] fb1: radeondrmfb frame buffer device
[   25.251614] registered panic notifier
[   25.251643] [drm] Initialized radeon 2.0.0 20080528 for 0000:00:10.0 on minor 0
[   25.448293] lp: driver loaded but no devices found
[   25.617743] ppdev: user-space parallel port driver
[   31.448143] eth0: no IPv6 routers present
[   86.800556] ondemand governor failed, too long transition latency of HW, fallback to performance governor

---

### Post by ant2ne on 2010-05-03
I will try [https://wiki.ubuntu.com/X/KernelModeSetting]("https://wiki.ubuntu.com/X/KernelModeSetting") when I get home.

---

### Post by ant2ne on 2010-05-04
Well, that worked. But now, randomly my Xorg eats up 96-99.2% of my CPU and the system is just completely unresponsive!!

---

### Post by linuxopjemac on 2010-05-04
sounds good ;)

---

### Post by ant2ne on 2010-05-05
> **linuxopjemac said:**
> sounds good ;)??

How does... 
> randomly my Xorg eats up 96-99.2% of my CPU and the system is just completely unresponsive!! ... sound good?

---

### Post by linuxopjemac on 2010-05-05
it was meant as a joke. I thought you'd understand...

---

### Post by ant2ne on 2010-05-05
Oh, right I get it now.

---

