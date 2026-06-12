---
title: "Linsys Wireless Adapter problems"
date: 2010-06-28
forum: Apple Hardware Users
---

### Post by penguinguy1 on 2010-06-28
Hello everyone.

As you can tell, I am new to these forums, as well as Ubuntu Linux, so please be patient with me.

I have been a hardcore Windows user for some time now, and I have finally switched to linux completly.

Anyways.

I have a Mac G4 Quicksilver running Ubuntu 9.04.

My Linksys WUSB100 wireless adapter would not work with Mac OS.

It doesnt work with Ubuntu.

It seems the only way I could get this adapter to work within linux is using ndiswrapper, which only works on x86 based cpus, not Power PC Cpus.

Is there ANY way that I can make this adapter work with Ubuntu with my Mac?

---

### Post by linuxopjemac on 2010-06-29
I thionk your card has a Ralink chipset (2870?)

I guess you have to compile the driver yourself:
[http://web.ralinktech.com/ralink/Home/Support/Linux.html](http://web.ralinktech.com/ralink/Home/Support/Linux.html)

Google a bit
[http://ubuntuforums.org/showthread.php?t=960642](http://ubuntuforums.org/showthread.php?t=960642)

---

### Post by penguinguy1 on 2010-06-29
I have no idea how to do that. 

Could you walk me through it?

And also, one of the links provided was unusable.

Which one should I download?

---

### Post by linuxopjemac on 2010-06-29
You have to first find out which chipset your card has.

Give me the output of
```
lspci
```

and

```
dmsesg
```

---

### Post by penguinguy1 on 2010-06-29
Results for lspci:
0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth 1.5 AGP
0000:00:10.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev a1)
0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth 1.5 PCI
0001:10:12.0 SCSI storage controller: Adaptec AIC-7850 (rev 03)
0001:10:17.0 Class ff00: Apple Computer Inc. KeyLargo Mac I/O (rev 03)
0001:10:18.0 USB Controller: Apple Computer Inc. KeyLargo USB
0001:10:19.0 USB Controller: Apple Computer Inc. KeyLargo USB
0002:20:0b.0 Host bridge: Apple Computer Inc. UniNorth 1.5 Internal PCI
0002:20:0e.0 FireWire (IEEE 1394): Agere Systems FW323
0002:20

Results for dmsesg:
bash: dmsesg: command not found

---

### Post by linuxopjemac on 2010-06-30
sorry

```
dmesg
```

---

### Post by penguinguy1 on 2010-06-30
[    0.000000] Using PowerMac machine description
[    0.000000] Total memory = 1536MB; using 4096kB for hash table (at cfc00000)
[    0.000000] Linux version 2.6.28-6-powerpc (buildd@adare) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #20-Ubuntu Fri Apr 17 08:30:40 UTC 2009 (Ubuntu 2.6.28-6.20-powerpc)
[    0.000000] Found initrd at 0xc1a00000:0xc2273000
[    0.000000] Found UniNorth memory controller & host bridge @ 0xf8000000 revision: 0x11
[    0.000000] Mapped at 0xff7c0000
[    0.000000] Found a Keylargo mac-io controller, rev: 3, mapped at 0xff740000
[    0.000000] Processor NAP mode on idle enabled.
[    0.000000] PowerMac motherboard: PowerMac G4 Silver
[    0.000000] console [udbg0] enabled
[    0.000000] Found UniNorth PCI host bridge at 0x00000000f0000000. Firmware bus number: 0->0
[    0.000000] PCI host bridge /pci@f0000000  ranges:
[    0.000000]  MEM 0x00000000f1000000..0x00000000f1ffffff -> 0x00000000f1000000 
[    0.000000]   IO 0x00000000f0000000..0x00000000f07fffff -> 0x0000000000000000
[    0.000000]  MEM 0x0000000090000000..0x00000000afffffff -> 0x0000000090000000 
[    0.000000] Found UniNorth PCI host bridge at 0x00000000f2000000. Firmware bus number: 0->0
[    0.000000] PCI host bridge /pci@f2000000 (primary) ranges:
[    0.000000]  MEM 0x00000000f3000000..0x00000000f3ffffff -> 0x00000000f3000000 
[    0.000000]   IO 0x00000000f2000000..0x00000000f27fffff -> 0x0000000000000000
[    0.000000]  MEM 0x0000000080000000..0x000000008fffffff -> 0x0000000080000000 
[    0.000000] Found UniNorth PCI host bridge at 0x00000000f4000000. Firmware bus number: 0->0
[    0.000000] PCI host bridge /pci@f4000000  ranges:
[    0.000000]  MEM 0x00000000f5000000..0x00000000f5ffffff -> 0x00000000f5000000 
[    0.000000]   IO 0x00000000f4000000..0x00000000f47fffff -> 0x0000000000000000
[    0.000000] via-pmu: Server Mode is disabled
[    0.000000] PMU driver v2 initialized for Core99, firmware: 0c
[    0.000000] nvram: Checking bank 0...
[    0.000000] nvram: gen0=380, gen1=381
[    0.000000] nvram: Active bank is: 1
[    0.000000] nvram: OF partition at 0x410
[    0.000000] nvram: XP partition at 0x1020
[    0.000000] nvram: NR partition at 0x1120
[    0.000000] Top of RAM: 0x60000000, Total RAM: 0x60000000
[    0.000000] Memory hole size: 0MB
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00030000
[    0.000000]   Normal   0x00030000 -> 0x00030000
[    0.000000]   HighMem  0x00030000 -> 0x00060000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00060000
[    0.000000] On node 0 totalpages: 393216
[    0.000000] free_area_init_node: node 0, pgdat c045c5fc, node_mem_map c04d0000
[    0.000000]   DMA zone: 1536 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 195072 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   HighMem zone: 1536 pages used for memmap
[    0.000000]   HighMem zone: 195072 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 390144
[    0.000000] Kernel command line: root=/dev/hda3 ro quiet splash 
[    0.000000] mpic: Setting up MPIC " MPIC 1   " version 1.2 at 80040000, max 4 CPUs
[    0.000000] mpic: ISU size: 64, shift: 6, mask: 3f
[    0.000000] mpic: Initializing for 64 sources
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] GMT Delta read from XPRAM: -240 minutes, DST: on
[    0.000000] time_init: decrementer frequency = 33.218083 MHz
[    0.000000] time_init: processor frequency   = 733.333331 MHz
[    0.000000] clocksource: timebase mult[786a955] shift[22] registered
[    0.000000] clockevent: decrementer mult[880] shift[16] cpu[0]
[    0.000091] Console: colour dummy device 80x25
[    0.000099] console handover: boot [udbg0] -> real [tty0]
[    0.001768] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004128] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.210275] High memory: 786432k
[    0.210283] Memory: 1540732k/1572864k available (4296k kernel code, 31108k reserved, 176k data, 360k bss, 212k init)
[    0.210390] SLUB: Genslabs=12, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.210408] Calibrating delay loop... 66.30 BogoMIPS (lpj=132608)
[    0.296465] Security Framework initialized
[    0.296491] SELinux:  Disabled at boot.
[    0.296560] AppArmor: AppArmor initialized
[    0.296577] Mount-cache hash table entries: 512
[    0.297043] device-tree: Duplicate name in /cpus/PowerPC,G4@0, renamed to "l2-cache#1"
[    0.299190] Initializing cgroup subsys ns
[    0.299201] Initializing cgroup subsys freezer
[    0.299753] net_namespace: 752 bytes
[    0.299848] regulator: core version 0.5
[    0.299952] NET: Registered protocol family 16
[    0.300470] KeyWest i2c @0xf8001003 irq 42 /uni-n@f8000000/i2c@f8001000
[    0.300480]  channel 0 bus <multibus>
[    0.300485]  channel 1 bus <multibus>
[    0.300537] KeyWest i2c @0x80018000 irq 26 /pci@f2000000/mac-io@17/i2c@18000
[    0.300544]  channel 0 bus <multibus>
[    0.300566] PMU i2c /pci@f2000000/mac-io@17/via-pmu@16000
[    0.300571]  channel 1 bus <multibus>
[    0.300576]  channel 2 bus <multibus>
[    0.300741] PCI: Probing PCI hardware
[    0.300903] pci 0000:00:10.0: reg 10 32bit mmio: [0x91000000-0x91ffffff]
[    0.300914] pci 0000:00:10.0: reg 14 32bit mmio: [0x98000000-0x9fffffff]
[    0.300936] pci 0000:00:10.0: reg 30 32bit mmio: [0x90000000-0x9000ffff]
[    0.301243] pci 0001:10:12.0: reg 10 io port: [0x400-0x4ff]
[    0.301254] pci 0001:10:12.0: reg 14 32bit mmio: [0x80082000-0x80082fff]
[    0.301309] pci 0001:10:17.0: reg 10 32bit mmio: [0x80000000-0x8007ffff]
[    0.301358] pci 0001:10:18.0: reg 10 32bit mmio: [0x80081000-0x80081fff]
[    0.301407] pci 0001:10:19.0: reg 10 32bit mmio: [0x80080000-0x80080fff]
[    0.301872] pci 0002:20:0e.0: reg 10 32bit mmio: [0xf5000000-0xf5000fff]
[    0.301902] pci 0002:20:0e.0: supports D1 D2
[    0.301908] pci 0002:20:0e.0: PME# supported from D0 D1 D2 D3hot
[    0.301916] pci 0002:20:0e.0: PME# disabled
[    0.301939] pci 0002:20:0f.0: reg 10 32bit mmio: [0xf5200000-0xf53fffff]
[    0.301963] pci 0002:20:0f.0: reg 30 32bit mmio: [0xf5100000-0xf51fffff]
[    0.302265] bus: 00 index 0 io port: [0x802000-0x1001fff]
[    0.302273] bus: 00 index 1 mmio: [0xf1000000-0xf1ffffff]
[    0.302279] bus: 00 index 2 mmio: [0x90000000-0xafffffff]
[    0.302285] bus: 10 index 0 io port: [0x00-0x7fffff]
[    0.302291] bus: 10 index 1 mmio: [0xf3000000-0xf3ffffff]
[    0.302297] bus: 10 index 2 mmio: [0x80000000-0x8fffffff]
[    0.302303] bus: 20 index 0 io port: [0xff7fe000-0xffffdfff]
[    0.302310] bus: 20 index 1 mmio: [0xf5000000-0xf5ffffff]
[    0.304992] usbcore: registered new interface driver usbfs
[    0.305033] usbcore: registered new interface driver hub
[    0.305105] usbcore: registered new device driver usb
[    0.316509] NET: Registered protocol family 8
[    0.316515] NET: Registered protocol family 20
[    0.316655] AppArmor: AppArmor Filesystem Enabled
[    0.317048] NET: Registered protocol family 2
[    0.320512] Switched to high resolution mode on CPU 0
[    0.352564] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.353147] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.356689] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[    0.357623] TCP: Hash tables configured (established 131072 bind 65536)
[    0.357631] TCP reno registered
[    0.368649] NET: Registered protocol family 1
[    0.368980] checking if image is initramfs... it is
[    2.022259] Freeing initrd memory: 8652k freed
[    2.023643] Thermal assist unit not available
[    2.023746] setup_kcore: restrict size=3fffffff
[    2.024127] audit: initializing netlink socket (disabled)
[    2.024164] type=2000 audit(1277948458.020:1): initialized
[    2.038471] highmem bounce pool size: 64 pages
[    2.041512] VFS: Disk quotas dquot_6.5.1
[    2.041560] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.041765] fuse init (API version 7.10)
[    2.041994] msgmni has been set to 1492
[    2.042381] alg: No test for stdrng (krng)
[    2.042413] io scheduler noop registered
[    2.042418] io scheduler anticipatory registered
[    2.042423] io scheduler deadline registered
[    2.042466] io scheduler cfq registered (default)
[    2.042502] pci 0000:00:10.0: nv_msi_ht_cap_quirk didn't locate host bridge
[    2.043089] Using unsupported 1024x768 NVDA,NVMac at 98004000, depth=8, pitch=1024
[    2.055981] Console: switching to colour frame buffer device 128x48
[    2.068420] fb0: Open Firmware frame buffer device on /pci@f0000000/NVDA,NVMac@10
[    2.071055] Generic non-volatile memory driver v1.1
[    2.072856] brd: module loaded
[    2.072965] Fixed MDIO Bus: probed
[    2.073054] MacIO PCI driver attached to Keylargo chipset
[    2.074432] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    2.074729] Uniform Multi-Platform E-IDE driver
[    2.075002] adb: starting probe task...
[    2.075015] adb: finished probe task...
[    3.092505] ide-pmac: Found Apple KeyLargo ATA-4 controller (macio), bus ID 2, irq 19
[    3.092543] Probing IDE interface ide0...
[    3.380800] hda: IBM-DTLA-305040, ATA DISK drive
[    4.052601] hda: host max PIO4 wanted PIO255(auto-tune) selected PIO4
[    4.052784] hda: UDMA/66 mode selected
[    4.052995] ide0 at 0xf1018000-0xf1018070,0xf1018160 on irq 19
[    5.072503] ide-pmac: Found Apple KeyLargo ATA-3 controller (macio), bus ID 0, irq 20
[    5.072530] Probing IDE interface ide1...
[    5.472675] hdc: SONY CD-RW CRX155E, ATAPI CD/DVD-ROM drive
[    6.144573] hdc: host max PIO4 wanted PIO255(auto-tune) selected PIO4
[    6.144871] hdc: MWDMA2 mode selected
[    6.145238] ide1 at 0xf1020000-0xf1020070,0xf1020160 on irq 20
[    7.164504] ide-pmac: Found Apple KeyLargo ATA-3 controller (macio), bus ID 1, irq 21
[    7.164531] Probing IDE interface ide2...
[    7.732607] ide2 at 0xf1028000-0xf1028070,0xf1028160 on irq 21
[    7.732777] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    7.732849] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    7.732904] ohci_hcd 0001:10:18.0: enabling device (0000 -> 0002)
[    7.732927] ohci_hcd 0001:10:18.0: OHCI Host Controller
[    7.733112] ohci_hcd 0001:10:18.0: new USB bus registered, assigned bus number 1
[    7.733153] ohci_hcd 0001:10:18.0: irq 27, io mem 0x80081000
[    7.808601] usb usb1: configuration #1 chosen from 1 choice
[    7.808675] hub 1-0:1.0: USB hub found
[    7.808708] hub 1-0:1.0: 2 ports detected
[    7.808956] ohci_hcd 0001:10:19.0: enabling device (0000 -> 0002)
[    7.808979] ohci_hcd 0001:10:19.0: OHCI Host Controller
[    7.809115] ohci_hcd 0001:10:19.0: new USB bus registered, assigned bus number 2
[    7.809152] ohci_hcd 0001:10:19.0: irq 28, io mem 0x80080000
[    7.884549] usb usb2: configuration #1 chosen from 1 choice
[    7.884619] hub 2-0:1.0: USB hub found
[    7.884649] hub 2-0:1.0: 2 ports detected
[    7.884877] uhci_hcd: USB Universal Host Controller Interface driver
[    7.885037] usbcore: registered new interface driver libusual
[    7.896586] mice: PS/2 mouse device common for all mice
[    7.896761] platform ppc-rtc.0: rtc core: registered ppc_md as rtc0
[    7.896836] PowerMac i2c bus pmu 2 registered
[    7.896879] PowerMac i2c bus pmu 1 registered
[    7.896923] PowerMac i2c bus mac-io 0 registered
[    7.896965] PowerMac i2c bus uni-n 1 registered
[    7.897025] PowerMac i2c bus uni-n 0 registered
[    7.897393] TCP cubic registered
[    7.897649] registered taskstats version 1
[    7.897984] input: PMU as /devices/virtual/input/input1
[    7.908546] /build/buildd/linux-ports-2.6.28/drivers/rtc/hctosys.c: unable to open rtc device (y)
[    7.908576] Freeing unused kernel memory: 212k init
[    8.184563] usb 1-1: new full speed USB device using ohci_hcd and address 2
[    8.435693] usb 1-1: configuration #1 chosen from 1 choice
[    8.640574] usb 1-2: new full speed USB device using ohci_hcd and address 3
[    8.786274] SCSI subsystem initialized
[    8.837670] ide-gd driver 1.18
[    8.837725] hda: max request size: 128KiB
[    8.837877] aic7xxx 0001:10:12.0: enabling device (0014 -> 0017)
[    8.870014] usb 1-2: configuration #1 chosen from 1 choice
[    8.881647] hub 1-2:1.0: USB hub found
[    8.882580] hub 1-2:1.0: 3 ports detected
[    8.885250] hda: 80418240 sectors (41174 MB) w/380KiB Cache, CHS=65535/16/63
[    8.885264] hda: cache flushes not supported
[    8.885443]  hda:<6>ide-cd driver 5.00
[    8.917595]  [mac] hda1 hda2 hda3 hda4
[    8.919985] ide-cd: hdc: ATAPI 32X CD-ROM CD-R/RW drive, 8192kB Cache
[    8.920006] Uniform CD-ROM driver Revision: 3.20
[    9.030971] sungem.c:v0.98 8/24/03 David S. Miller (davem@redhat.com)
[    9.073417] usb 2-1: new full speed USB device using ohci_hcd and address 2
[    9.096980] PHY ID: 206071, addr: 0
[    9.755765] usb 2-1: configuration #1 chosen from 1 choice
[    9.757685] hub 2-1:1.0: USB hub found
[    9.759544] hub 2-1:1.0: 3 ports detected
[    9.849556] usb 1-2.3: new low speed USB device using ohci_hcd and address 4
[    9.966818] usb 1-2.3: configuration #1 chosen from 1 choice
[   10.045202] eth0: Sun GEM (PCI) 10/100/1000BaseT Ethernet 00:03:93:4a:91:32
[   10.045213] eth0: Found BCM5411 PHY
[   10.099403] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[40]  MMIO=[f5000000-f50007ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[   10.106542] usb 2-1.1: new full speed USB device using ohci_hcd and address 3
[   10.211813] usb 2-1.1: configuration #1 chosen from 1 choice
[   10.294699] usb 2-1.2: new low speed USB device using ohci_hcd and address 4
[   10.417723] usb 2-1.2: configuration #1 chosen from 1 choice
[   10.417845] usbcore: registered new interface driver hiddev
[   10.461886] generic-usb 0003:05AC:9213.0001: hiddev96,hidraw0: USB HID v1.00 Device [Studio Display] on usb-0001:10:18.0-2.3/input0
[   10.465983] input: Mitsumi Electric Apple Extended USB Keyboard as /devices/pci0001:10/0001:10:19.0/usb2/2-1/2-1.1/2-1.1:1.0/input/input2
[   10.480760] generic-usb 0003:05AC:0204.0002: input,hidraw1: USB HID v1.10 Keyboard [Mitsumi Electric Apple Extended USB Keyboard] on usb-0001:10:19.0-1.1/input0
[   10.488024] input: Mitsumi Electric Apple Extended USB Keyboard as /devices/pci0001:10/0001:10:19.0/usb2/2-1/2-1.1/2-1.1:1.1/input/input3
[   10.496751] generic-usb 0003:05AC:0204.0003: input,hidraw2: USB HID v1.10 Device [Mitsumi Electric Apple Extended USB Keyboard] on usb-0001:10:19.0-1.1/input1
[   10.501773] input: Logitech M4848 as /devices/pci0001:10/0001:10:19.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input4
[   10.512831] generic-usb 0003:05AC:0301.0004: input,hidraw3: USB HID v1.00 Mouse [Logitech M4848] on usb-0001:10:19.0-1.2/input0
[   10.512885] usbcore: registered new interface driver usbhid
[   10.512894] usbhid: v2.6:USB HID core driver
[   11.392791] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000393fffe4a9132]
[   12.012720] eth0: Link is up at 100 Mbps, full-duplex.
[   23.868525] scsi0 : Adaptec AIC7XXX EISA/VLB/PCI SCSI HBA DRIVER, Rev 7.0
[   23.868530]         <Adaptec 2902/04/10/15/20C/30C SCSI adapter>
[   23.868534]         aic7850: Single Channel A, SCSI Id=7, 3/253 SCBs
[   23.868538] 
[   24.064444] PM: Starting manual resume from disk
[   24.185722] kjournald starting.  Commit interval 5 seconds
[   24.185756] EXT3-fs: mounted filesystem with ordered data mode.
[   30.812449] udev: starting version 141
[   31.258243] pmac_zilog: 0.6 (Benjamin Herrenschmidt <benh@kernel.crashing.org>)
[   31.258326] pmac_zilog: i2c-modem detected, id: 1
[   31.258919] ttyPZ0 at MMIO 0x80013020 (irq = 22) is a Z85c30 ESCC - Internal modem
[   31.259266] ttyPZ1 at MMIO 0x80013000 (irq = 29) is a Z85c30 ESCC - Serial port
[   31.362995] Linux agpgart interface v0.103
[   31.428050] agpgart-uninorth 0000:00:0b.0: Apple UniNorth 1.5 chipset
[   31.428270] agpgart-uninorth 0000:00:0b.0: configuring for size idx: 8
[   31.428603] agpgart-uninorth 0000:00:0b.0: AGP aperture is 32M @ 0x0
[   33.765886] input: PowerMac Beep as /devices/pci0001:10/0001:10:17.0/input/input5
[   33.855750] apm_emu: PMU APM Emulation initialized.
[   34.719366] Adding 1695404k swap on /dev/hda4.  Priority:-1 extents:1 across:1695404k
[   35.413390] EXT3 FS on hda3, internal journal
[   36.968014] type=1505 audit(1277948492.964:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1716
[   37.194506] type=1505 audit(1277948493.192:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1720
[   37.195126] type=1505 audit(1277948493.192:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1720
[   37.195393] type=1505 audit(1277948493.192:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1720
[   37.195609] type=1505 audit(1277948493.192:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1720
[   37.827477] type=1505 audit(1277948493.824:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1725
[   37.828408] type=1505 audit(1277948493.824:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1725
[   37.965604] type=1505 audit(1277948493.964:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1729
[   41.255808] NET: Registered protocol family 10
[   41.256115] lo: Disabled Privacy Extensions
[   42.171814] hda: host max PIO4 wanted PIO0 selected PIO0
[   42.842593] input: Mouseemu virtual keyboard as /devices/virtual/input/input6
[   42.869821] input: Mouseemu virtual mouse as /devices/virtual/input/input7
[   43.286489] hda: task_no_data_intr: status=0x51 { DriveReady SeekComplete Error }
[   43.286509] hda: task_no_data_intr: error=0x04 { DriveStatusError }
[   43.286517] ide: failed opcode was: 0xef
[   44.813667] Bluetooth: Core ver 2.13
[   44.813859] NET: Registered protocol family 31
[   44.813866] Bluetooth: HCI device and connection manager initialized
[   44.813875] Bluetooth: HCI socket layer initialized
[   44.870282] Bluetooth: L2CAP ver 2.11
[   44.870295] Bluetooth: L2CAP socket layer initialized
[   44.918683] Bluetooth: RFCOMM socket layer initialized
[   44.918722] Bluetooth: RFCOMM TTY layer initialized
[   44.918727] Bluetooth: RFCOMM ver 1.10
[   45.021411] Bluetooth: SCO (Voice Link) ver 0.6
[   45.021420] Bluetooth: SCO socket layer initialized
[   45.172344] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   45.172355] Bluetooth: BNEP filters: protocol multicast
[   45.289546] Bridge firewalling registered
[   48.368186] lp: driver loaded but no devices found
[   48.396458] ppdev: user-space parallel port driver
[   49.386756] Process Xorg (pid:2391) mapped non-existing PCI legacy memory for 00000:00
[   51.002604] eth0: Link is up at 100 Mbps, full-duplex.
[   51.002617] eth0: Pause is enabled (rxfifo: 10240 off: 7168 on: 5632)
[   52.315954] NET: Registered protocol family 17
[   61.224499] eth0: no IPv6 routers present

---

### Post by linuxopjemac on 2010-07-01
I don't see any entry for your wireless USB card. I doubt that the kernel module/driver responsible for this apparatus is loaded. Try:

```
lsusb
```

I found some more info. There was a problem with this card in the past. The rt2870 kernel driver did not work. You might have to do the same thing.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/350695](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/350695)

---

### Post by penguinguy1 on 2010-07-01
lsusb results:
Bus 002 Device 004: ID 05ac:0301 Apple, Inc. USB Mouse [Mitsumi, M4848]
Bus 002 Device 003: ID 05ac:0204 Apple, Inc. 
Bus 002 Device 002: ID 05ac:1002 Apple, Inc. Extended Keyboard Hub [Mitsumi]
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 045e:0710 Microsoft Corp. 
Bus 001 Device 004: ID 05ac:9213 Apple, Inc. 
Bus 001 Device 003: ID 04cc:1122 Philips Semiconductors Hub
Bus 001 Device 002: ID 1737:0070 Linksys 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I do notice that ubuntu detects the device, since Linksys is in the list.

What do I need to do from here?

I know you provided me a link to help, but I am completly new to this, so if you could help me through this, I would really appreciate it.

If I can get this working, I wont have to trade this wireless adapter in for a Cat5e cable from my friend. i would rather use wireless.

Thank you again, in advance.

---

### Post by linuxopjemac on 2010-07-02
People say that you have to recompile the kernel. This is not so easy, especially for beginners. I would suggest you try the last post:

> I do not know if it helps fixing the bug, but

echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "1737 0078" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf

Gets the device up and running for me. With the driver that comes with 2.6.32-19-generic, no re-compilation of kernel or driver src.

Best regards,
GrandTheft

So I would try this:

```
sudo echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "1737 0070" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf
```

---

### Post by ryan! on 2010-07-03
I gave up on wireless cards in ubuntu so instead i use an access point. I recommend getting one.

If interested here is the one I have: [http://www.amazon.com/gp/product/B000799LPE/ref=oss_product](http://www.amazon.com/gp/product/B000799LPE/ref=oss_product)

---

