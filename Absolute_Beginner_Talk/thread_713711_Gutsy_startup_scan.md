---
title: "Gutsy startup scan"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by elexhobby on 2008-03-03
I've been using gutsy for about 2 months now. I shifted from Dapper to Edgy to Gutsy. 

Gutsy takes a very long time to boot (8-10 mins). It scans all my hard drives each time. Is there a way I can prevent this scanning, because I do not see any problems with my drives. Dapper and Edgy never had this startup scan and would boot very fast.

Thanks.

---

### Post by northern lights on 2008-03-03
What process does the scanning? Run ```
dmesg
``` after booting, you should see what's slowing you down.

---

### Post by elexhobby on 2008-03-03
```

[    0.000000] Linux version 2.6.22-14-rt (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP PREEMPT RT Tue Dec 18 10:01:34 UTC 2007 (Unofficial)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001dff0000 (usable)
[    0.000000]  BIOS-e820: 000000001dff0000 - 000000001dff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001dff3000 - 000000001e000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 479MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 122864) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   122864
[    0.000000]   HighMem    122864 ->   122864
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   122864
[    0.000000] On node 0 totalpages: 122864
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4040 pages, LIFO batch:0
[    0.000000]   Normal zone: 1623 pages used for memmap
[    0.000000]   Normal zone: 117145 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6C60 checksum 0
[    0.000000] ACPI: RSDP 000F6C60, 0014 (r0 JETWAY)
[    0.000000] ACPI: RSDT 1DFF3000, 0028 (r1 JETWAY AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 1DFF3040, 0074 (r1 JETWAY AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 1DFF30C0, 2FEB (r1 JETWAY AWRDACPI     1000 MSFT  100000C)
[    0.000000] ACPI: FACS 1DFF0000, 0040
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1e000000:e1ff0000)
[    0.000000] Real-Time Preemption Support (C) 2004-2007 Ingo Molnar
[    0.000000] Built 1 zonelists.  Total pages: 121185
[    0.000000] Kernel command line: root=UUID=ac238ec3-81fb-4878-83a6-998cbfb1720a ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffd000 (016a0000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] WARNING: experimental RCU implementation.
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1616.083 MHz processor.
[   28.643396] Console: colour VGA+ 80x25
[   28.644073] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   28.644650] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   28.672525] Memory: 472596k/491456k available (2056k kernel code, 18204k reserved, 970k data, 364k init, 0k highmem)
[   28.672541] virtual kernel memory layout:
[   28.672543]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   28.672545]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   28.672547]     vmalloc : 0xde800000 - 0xff7fe000   ( 527 MB)
[   28.672549]     lowmem  : 0xc0000000 - 0xddff0000   ( 479 MB)
[   28.672551]       .init : 0xc03fb000 - 0xc0456000   ( 364 kB)
[   28.672553]       .data : 0xc030233c - 0xc03f4b44   ( 970 kB)
[   28.672554]       .text : 0xc0100000 - 0xc030233c   (2056 kB)
[   28.672560] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   28.732773] Calibrating delay using timer specific routine.. 3234.44 BogoMIPS (lpj=1617223)
[   28.732854] Security Framework v1.0.0 initialized
[   28.732868] SELinux:  Disabled at boot.
[   28.732899] Mount-cache hash table entries: 512
[   28.733212] CPU: After generic identify, caps: 3febf9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   28.733237] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   28.733242] CPU: L2 cache: 256K
[   28.733246] CPU: Hyper-Threading is disabled
[   28.733252] CPU: After all inits, caps: 3febf9ff 00000000 00000000 0000b080 00000000 00000000 00000000
[   28.733275] Compat vDSO mapped to ffffe000.
[   28.733303] Checking 'hlt' instruction... OK.
[   28.737003] SMP alternatives: switching to UP code
[   28.737369] Freeing SMP alternatives: 9k freed
[   28.737965] Early unpacking initramfs... done
[   29.282630] ACPI: Core revision 20070126
[   29.282768] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   29.284720] ACPI: setting ELCR to 0200 (from 0e20)
[   29.286794] CPU0: Intel(R) Pentium(R) 4 CPU 1.60GHz stepping 02
[   29.286808] SMP motherboard not detected.
[   29.286812] Local APIC not detected. Using dummy APIC emulation.
[   29.287867] Brought up 1 CPUs
[   29.288206] Booting paravirtualized kernel on bare hardware
[   29.288348] Time: 20:06:37  Date: 02/03/108
[   29.288410] NET: Registered protocol family 16
[   29.288705] EISA bus registered
[   29.288732] ACPI: bus type pci registered
[   29.330197] PCI: PCI BIOS revision 2.10 entry at 0xfb2d0, last bus=1
[   29.330201] PCI: Using configuration type 1
[   29.330204] Setting up standard PCI resources
[   29.343807] ACPI: EC: Look up EC in DSDT
[   29.348534] ACPI: Interpreter enabled
[   29.348548] ACPI: (supports S0 S1 S4 S5)
[   29.348580] ACPI: Using PIC for interrupt routing
[   29.358827] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   29.358855] PCI: Probing PCI hardware (bus 00)
[   29.359981] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   29.378211] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[   29.378419] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   29.378646] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 *5 6 7 10 11 12 14 15)
[   29.378874] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *10 11 12 14 15)
[   29.379206] Linux Plug and Play Support v0.97 (c) Adam Belay
[   29.379236] pnp: PnP ACPI init
[   29.379263] ACPI: bus type pnp registered
[   29.385716] pnp: PnP ACPI: found 13 devices
[   29.385723] ACPI: ACPI bus type pnp unregistered
[   29.385731] PnPBIOS: Disabled by ACPI PNP
[   29.385878] PCI: Using ACPI for IRQ routing
[   29.385885] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   29.392915] NET: Registered protocol family 8
[   29.392920] NET: Registered protocol family 20
[   29.393208] pnp: 00:00: iomem range 0xd5800-0xd7fff has been reserved
[   29.393215] pnp: 00:00: iomem range 0xf0000-0xf7fff could not be reserved
[   29.393219] pnp: 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[   29.393224] pnp: 00:00: iomem range 0xfc000-0xfffff could not be reserved
[   29.424232] PCI: Bridge: 0000:00:01.0
[   29.424238]   IO window: disabled.
[   29.424246]   MEM window: ec000000-edffffff
[   29.424252]   PREFETCH window: e0000000-e7ffffff
[   29.424281] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   29.424338] NET: Registered protocol family 2
[   29.430055] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   29.430211] TCP established hash table entries: 16384 (order: 7, 720896 bytes)
[   29.432175] TCP bind hash table entries: 16384 (order: 7, 589824 bytes)
[   29.434035] TCP: Hash tables configured (established 16384 bind 16384)
[   29.434049] TCP reno registered
[   29.436297] checking if image is initramfs... it is
[   30.521774] Freeing initrd memory: 7067k freed
[   30.522754] audit: initializing netlink socket (disabled)
[   30.522790] audit(1204574798.720:1): initialized
[   30.523251] VFS: Disk quotas dquot_6.5.1
[   30.523269] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   30.523391] io scheduler noop registered
[   30.523396] io scheduler anticipatory registered
[   30.523399] io scheduler deadline registered
[   30.523416] io scheduler cfq registered (default)
[   30.523444] PCI: VIA PCI bridge detected. Disabling DAC.
[   30.523496] Boot video device is 0000:01:00.0
[   30.524199] isapnp: Scanning for PnP cards...
[   30.881054] isapnp: No Plug & Play device found
[   31.036707] Real Time Clock Driver v1.12ac
[   31.036964] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   31.037122] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   31.037769] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   31.040148] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   31.041247] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   31.043860] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   31.044215] input: Macintosh mouse button emulation as /class/input/input0
[   31.044437] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   31.044443] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   31.045099] serio: i8042 KBD port at 0x60,0x64 irq 1
[   31.045278] serio: i8042 AUX port at 0x60,0x64 irq 12
[   31.045785] mice: PS/2 mouse device common for all mice
[   31.046179] EISA: Probing bus 0 at eisa.0
[   31.046229] EISA: Detected 0 cards.
[   31.046410] TCP cubic registered
[   31.046422] NET: Registered protocol family 1
[   31.046463] Using IPI No-Shortcut mode
[   31.046968]   Magic number: 0:392:143
[   31.048313] Freeing unused kernel memory: 364k freed
[   31.070867] input: AT Translated Set 2 keyboard as /class/input/input1
[   32.601462] AppArmor: AppArmor initialized<5>audit(1204574800.720:2):  type=1505 info="AppArmor initialized" pid=1129
[   32.622647] fuse init (API version 7.8)
[   32.636123] Failure registering capabilities with primary security module.
[   32.658966] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   32.658978] ACPI: Processor [CPU0] (supports 2 throttling states)
[   34.832510] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   34.832525] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   34.961795] usbcore: registered new interface driver usbfs
[   34.964032] usbcore: registered new interface driver hub
[   34.967528] 8139too Fast Ethernet driver 0.9.28
[   34.970233] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 5
[   34.970243] PCI: setting IRQ 5 as level-triggered
[   34.970250] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[   34.975540] fealnx.c:v2.52 Sep-11-2006
[   34.982950] Floppy drive(s): fd0 is 1.44M
[   34.986480] usbcore: registered new device driver usb
[   34.994740] eth0: RealTek RTL8139 at 0xde83a000, 00:40:f4:ed:41:18, IRQ 5
[   34.994747] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   34.995469] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
[   34.995476] PCI: setting IRQ 10 as level-triggered
[   34.995483] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[   34.995694] eth1: 100/10M Ethernet PCI Adapter at 0001d400, 00:e0:50:01:9e:ad, IRQ 10.
[   34.995784] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[   34.996434] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[   34.996441] PCI: setting IRQ 11 as level-triggered
[   34.996447] ACPI: PCI Interrupt 0000:00:11.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   34.996457] PCI: VIA VLink IRQ fixup for 0000:00:11.1, from 255 to 11
[   34.996490] VP_IDE: chipset revision 6
[   34.996494] VP_IDE: not 100% native mode: will probe irqs later
[   34.996518] VP_IDE: VIA vt8233a (rev 00) IDE UDMA133 controller on pci0000:00:11.1
[   34.996533]     ide0: BM-DMA at 0xd800-0xd807, BIOS settings: hda:DMA, hdb:DMA
[   34.996554]     ide1: BM-DMA at 0xd808-0xd80f, BIOS settings: hdc:pio, hdd:DMA
[   34.996571] Probing IDE interface ide0...
[   35.003027] FDC 0 is a post-1991 82077
[   35.037897] USB Universal Host Controller Interface driver v3.0
[   35.421062] hda: SAMSUNG SP0802N, ATA DISK drive
[   35.675849] hdb: ST3250820AV, ATA DISK drive
[   35.727325] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   35.732299] Probing IDE interface ide1...
[   36.782919] hdd: HL-DT-ST DVDRAM GSA-H42N, ATAPI CD/DVD-ROM drive
[   36.835121] ide1 at 0x170-0x177,0x376 on irq 15
[   36.838482] ACPI: PCI Interrupt 0000:00:11.2[D] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[   36.838513] uhci_hcd 0000:00:11.2: UHCI Host Controller
[   36.839413] uhci_hcd 0000:00:11.2: new USB bus registered, assigned bus number 1
[   36.839575] uhci_hcd 0000:00:11.2: irq 10, io base 0x0000dc00
[   36.841039] usb usb1: configuration #1 chosen from 1 choice
[   36.841557] hub 1-0:1.0: USB hub found
[   36.841587] hub 1-0:1.0: 2 ports detected
[   36.950127] ACPI: PCI Interrupt 0000:00:11.3[D] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[   36.950160] uhci_hcd 0000:00:11.3: UHCI Host Controller
[   36.950807] uhci_hcd 0000:00:11.3: new USB bus registered, assigned bus number 2
[   36.950860] uhci_hcd 0000:00:11.3: irq 10, io base 0x0000e000
[   36.952143] usb usb2: configuration #1 chosen from 1 choice
[   36.952765] hub 2-0:1.0: USB hub found
[   36.952800] hub 2-0:1.0: 2 ports detected
[   36.952930] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   36.971964] SCSI subsystem initialized
[   36.990220] libata version 2.21 loaded.
[   37.134694] hda: max request size: 512KiB
[   37.139511] hda: 156368016 sectors (80060 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(33)
[   37.139761] hda: cache flushes supported
[   37.139881]  hda: hda1 hda2 < hda5 hda6 hda7 >
[   37.184988] hdb: max request size: 512KiB
[   37.230663] hdb: 488397168 sectors (250059 MB) w/8192KiB Cache, CHS=30401/255/63, UDMA(33)
[   37.252424] usb 1-2: new full speed USB device using uhci_hcd and address 2
[   37.255027] hdb: cache flushes supported
[   37.255136]  hdb: hdb1 < hdb5 > hdb2 hdb3 hdb4
[   37.282017] hdd: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(66)
[   37.282041] Uniform CD-ROM driver Revision: 3.20
[   37.406402] usb 1-2: configuration #1 chosen from 1 choice
[   37.408239] hub 1-2:1.0: USB hub found
[   37.411103] hub 1-2:1.0: 4 ports detected
[   37.904568] usb 1-2.4: new low speed USB device using uhci_hcd and address 3
[   38.031670] usb 1-2.4: configuration #1 chosen from 1 choice
[   38.097744] usbcore: registered new interface driver hiddev
[   38.111473] input: Microsoft Basic Optical Mouse as /class/input/input2
[   38.112044] input: USB HID v1.10 Mouse [Microsoft Basic Optical Mouse] on usb-0000:00:11.2-2.4
[   38.112081] usbcore: registered new interface driver usbhid
[   38.112090] /build/buildd/linux-source-2.6.22-2.6.22/debian/build/custom-source-rt/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   38.219999] Attempting manual resume
[   38.220007] swsusp: Resume From Partition 3:69
[   38.220010] PM: Checking swsusp image.
[   38.226352] PM: Resume from disk failed.
[   38.288992] kjournald starting.  Commit interval 5 seconds
[   38.289024] EXT3-fs: mounted filesystem with ordered data mode.
[   44.391040] eth0: link down
[   46.547126] NET: Registered protocol family 10
[   46.547279] lo: Disabled Privacy Extensions
[   46.547411] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   49.468430] input: PC Speaker as /class/input/input3
[   49.787090] Linux agpgart interface v0.102 (c) Dave Jones
[   49.927635] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   50.018034] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   50.036444] agpgart: Detected VIA P4M266x/P4N266 chipset
[   50.091297] agpgart: AGP aperture is 64M @ 0xe8000000
[   50.467539] irda_init()
[   50.467589] NET: Registered protocol family 23
[   50.545341] parport_pc 00:0a: reported by Plug and Play ACPI
[   50.545405] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   51.518537] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[   51.518693] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   52.516593] lp0: using parport0 (interrupt-driven).
[   52.626815] Adding 979892k swap on /dev/hdb5.  Priority:-1 extents:1 across:979892k
[   54.066988] EXT3 FS on hdb2, internal journal
[   57.093697] eth1: no IPv6 routers present
[  236.242102] PPP generic driver version 2.4.2
[  236.276249] NET: Registered protocol family 17
[  236.363547] NET: Registered protocol family 24
[  238.100034] input: Power Button (FF) as /class/input/input4
[  238.100660] ACPI: Power Button (FF) [PWRF]
[  238.101980] input: Power Button (CM) as /class/input/input5
[  238.102630] ACPI: Power Button (CM) [PWRB]
[  238.103471] input: Sleep Button (CM) as /class/input/input6
[  238.103575] ACPI: Sleep Button (CM) [SLPB]
[  238.413396] No dock devices found.
[  239.833598] ip_tables: (C) 2000-2006 Netfilter Core Team
[  242.313429] ppdev: user-space parallel port driver
[  243.153055] audit(1204555211.529:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4806 profile="/usr/sbin/cupsd"
[  245.689726] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[  245.689739] apm: overridden by ACPI.
[  246.496205] Failure registering capabilities with primary security module.
[  246.877384] Bluetooth: Core ver 2.11
[  246.878086] NET: Registered protocol family 31
[  246.878100] Bluetooth: HCI device and connection manager initialized
[  246.878108] Bluetooth: HCI socket layer initialized
[  246.918078] Bluetooth: L2CAP ver 2.8
[  246.918089] Bluetooth: L2CAP socket layer initialized
[  246.949846] Bluetooth: RFCOMM socket layer initialized
[  246.949883] Bluetooth: RFCOMM TTY layer initialized
[  246.949888] Bluetooth: RFCOMM ver 1.8
[  251.161749] [drm] Initialized drm 1.1.0 20060810
[  251.171763] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[  251.172600] [drm] Initialized savage 2.4.1 20050313 on minor 0
[  251.183498] mtrr: base(0xe2000000) is not aligned on a size(0x5000000) boundary
[  251.184918] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[  251.184957] agpgart: Putting AGP V2 device at 0000:00:00.0 into 0x mode
[  251.185025] agpgart: Putting AGP V2 device at 0000:01:00.0 into 0x mode

```

Here's the output. However, I couldn't make much sense out of it. While booting, on the screen it shows scanning hda1, hda5 hda6 and hda7, (these are my drive names), and shows the number of clusters, etc. It is this scanning process that takes the bulk of the time I feel, because the screen is sort of hanged for a large amount of time during this.

Please help. Thanks.

---

### Post by LarryJ2 on 2008-03-03
Is your harddisk hda healthy?  Maybe that's why  fsck is taking so long.  6 - 10 minutes is abnormally long.

Also you might consider shifting the fsck checks to shutdown.   [https://wiki.ubuntu.com/AutoFsck](https://wiki.ubuntu.com/AutoFsck)

---

