---
title: "Tibook won't boot 2.6.22 kernel in Gutsy"
date: 2007-06-19
forum: Apple PPC Users
---

### Post by digv on 2007-06-19
Hello All,

Just installed Gutsy.  The 2.6.22-6 kernel with Gutsy will not fully boot for me.  2.6.20-15 from Feisty boots fine.  I tried completely purging and reinstalling the kernel and other packages I thought might be associated hoping for an easy fix.  No luck.  I have a Powerbook 667 G4.

It doesn't get far enough through the boot to leave a log but I've annotated in the output from dmesg booting the 2.6.20 kernel where it hangs....

[    0.000000] Using PowerMac machine description
[    0.000000] Total memory = 512MB; using 1024kB for hash table (at cff00000)
[    0.000000] Linux version 2.6.20-15-powerpc-smp (root@adare) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #3 SMP Sun Apr 15 06:49:11 UTC 2007 (Ubuntu 2.6.2
0-15.27-powerpc-smp)
[    0.000000] Found initrd at 0xc1900000:0xc21d4000
[    0.000000] Found UniNorth memory controller & host bridge @ 0xf8000000 revision: 0x11
[    0.000000] Mapped at 0xfdfc0000
[    0.000000] Found a Keylargo mac-io controller, rev: 3, mapped at 0xfdf40000
[    0.000000] Processor NAP mode on idle enabled.
[    0.000000] PowerMac motherboard: PowerBook Titanium III
[    0.000000] via-pmu: Server Mode is disabled
[    0.000000] PMU driver v2 initialized for Core99, firmware: 0c
[    0.000000] Entering add_active_range(0, 0, 131072) 0 entries of 256 used
[    0.000000] Found UniNorth PCI host bridge at 0x00000000f0000000. Firmware bus number: 0->1
[    0.000000] Found UniNorth PCI host bridge at 0x00000000f2000000. Firmware bus number: 0->1
[    0.000000] Found UniNorth PCI host bridge at 0x00000000f4000000. Firmware bus number: 0->1
[    0.000000] nvram: Checking bank 0...
[    0.000000] nvram: gen0=82, gen1=81
[    0.000000] nvram: Active bank is: 0
[    0.000000] nvram: OF partition at 0x410
[    0.000000] nvram: XP partition at 0xffffffff
[    0.000000] nvram: NR partition at 0xffffffff
[    0.000000] Top of RAM: 0x20000000, Total RAM: 0x20000000
[    0.000000] Memory hole size: 0MB
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->   131072
[    0.000000]   Normal     131072 ->   131072
[    0.000000]   HighMem    131072 ->   131072
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131072
[    0.000000] On node 0 totalpages: 131072
[    0.000000]   DMA zone: 1024 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 130048 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] Built 1 zonelists.  Total pages: 130048
[    0.000000] Kernel command line: root=/dev/hda4 ro 
[    0.000000] mpic: Setting up MPIC " MPIC 1   " version 1.2 at 80040000, max 4 CPUs
[    0.000000] mpic: ISU size: 64, shift: 6, mask: 3f
[    0.000000] mpic: Initializing for 64 sources
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] GMT Delta read from XPRAM: 0 minutes, DST: on
[    0.000000] time_init: decrementer frequency = 33.331323 MHz
[    0.000000] time_init: processor frequency   = 667.000000 MHz
[   28.276318] Console: colour dummy device 80x25
[   28.276993] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   28.277630] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   28.305173] High memory: 0k
[   28.305185] Memory: 505344k/524288k available (3368k kernel code, 18564k reserved, 124k data, 286k bss, 204k init)
[   28.305509] Calibrating delay loop... 66.56 BogoMIPS (lpj=133120)
[   28.392163] Security Framework v1.0.0 initialized
[   28.392191] SELinux:  Disabled at boot.
[   28.392240] Mount-cache hash table entries: 512
[   28.392593] device-tree: Duplicate name in /cpus/PowerPC,G4@0/l2-cache, renamed to "l2-cache#1"
[   28.392672] device-tree: Duplicate name in /cpus/PowerPC,G4@0, renamed to "l2-cache#1"
[   28.394838] PowerMac SMP probe found 1 cpus
[   28.394957] Brought up 1 CPUs
[   28.395723] NET: Registered protocol family 16
[   28.396241] KeyWest i2c @0xf8001003 irq 42 /uni-n@f8000000/i2c@f8001000
[   28.396266]  channel 0 bus <multibus>
[   28.396278]  channel 1 bus <multibus>
[   28.396329] KeyWest i2c @0x80018000 irq 26 /pci@f2000000/mac-io@17/i2c@18000
[   28.396345]  channel 0 bus <multibus>
[   28.396371] PMU i2c /pci@f2000000/mac-io@17/via-pmu@16000
[   28.396385]  channel 1 bus <multibus>
[   28.396397]  channel 2 bus <multibus>
[   28.396964] PCI: Probing PCI hardware
[   28.399459] Can't get bus-range for /pci@f2000000/cardbus@1a, assuming it starts at 0
[   28.404419] NET: Registered protocol family 8
[   28.404444] NET: Registered protocol family 20
[   28.405357] NET: Registered protocol family 2
[   28.436210] IP route cache hash table entries: 16384 (order: 4, 65536 bytes)
[   28.436559] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
[   28.439775] TCP bind hash table entries: 32768 (order: 6, 262144 bytes)
[   28.441386] TCP: Hash tables configured (established 65536 bind 32768)
[   28.441410] TCP reno registered
[   28.452474] checking if image is initramfs... it is
[   30.359415] Freeing initrd memory: 9040k freed
[   30.360814] Thermal assist unit not available
[   30.361040] Registering PowerMac CPU frequency driver
[   30.361057] Low: 667 Mhz, High: 667 Mhz, Boot: 667 Mhz
[   30.361725] audit: initializing netlink socket (disabled)
[   30.361780] audit(1182283572.084:1): initialized
[   30.362108] VFS: Disk quotas dquot_6.5.1
[   30.362167] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   30.362335] io scheduler noop registered
[   30.362353] io scheduler anticipatory registered
[   30.362369] io scheduler deadline registered
[   30.362402] io scheduler cfq registered (default)
[   30.363377] PCI: Enabling device 0000:00:10.0 (0086 -> 0087)
[   30.562136] radeonfb (0000:00:10.0): Invalid ROM signature 0 should be 0xaa55
[   30.562152] radeonfb: Retrieved PLL infos from Open Firmware
[   30.562171] radeonfb: Reference=27.00 MHz (RefDiv=12) Memory=183.00 Mhz, System=230.00 MHz
[   30.562193] radeonfb: PLL min 12000 max 35000
[   30.661419] i2c_adapter i2c-2: unable to read EDID block.
[   30.817410] i2c_adapter i2c-2: unable to read EDID block.
[   30.973410] i2c_adapter i2c-2: unable to read EDID block.
[   31.129410] i2c_adapter i2c-3: unable to read EDID block.
[   31.285410] i2c_adapter i2c-3: unable to read EDID block.
[   31.441409] i2c_adapter i2c-3: unable to read EDID block.
[   31.497051] radeonfb: Monitor 1 type LCD found
[   31.497064] radeonfb: EDID probed
[   31.497076] radeonfb: Monitor 2 type no found
[   31.497103] radeonfb: Using Firmware dividers 0x0002008e from PPLL 0
[   31.656045] radeonfb: Dynamic Clock Power Management enabled
[   31.691039] Console: switching to colour frame buffer device 160x53
[   31.714212] radeonfb: Backlight initialized (radeonbl0)
[   31.714398] radeonfb (0000:00:10.0): ATI Radeon LW 
[   31.793290] Generic RTC Driver v1.07
[   31.793588] Macintosh non-volatile memory driver v1.1
[   31.794036] mice: PS/2 mouse device common for all mice
[   31.796156] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   31.797170] MacIO PCI driver attached to Keylargo chipset
[   31.800306] input: Macintosh mouse button emulation as /class/input/input0
[   31.800966] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   31.801196] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   31.801608] adb: starting probe task...
[   32.056557] adb devices: [2]: 2 c3 [3]: 3 1 [7]: 7 1f
[   32.063201] ADB keyboard at 2, handler 1
[   32.063356] Detected ADB keyboard, type ANSI.
[   32.063720] input: ADB keyboard as /class/input/input1
[   32.064112] input: ADB Powerbook buttons as /class/input/input2
[   32.079587] ADB mouse at 3, handler set to 4 (trackpad)
[   32.139425] input: ADB mouse as /class/input/input3
[   32.139684] adb: finished probe task...
[   32.820049] ide0: Found Apple KeyLargo ATA-4 controller, bus ID 2, irq 19
[   32.820292] Probing IDE interface ide0...
[   33.136356] hda: TOSHIBA MK3018GAS, ATA DISK drive
[   33.808055] hda: Enabling Ultra DMA 4
[   33.809280] ide0 at 0xe1012000-0xe1012007,0xe1012160 on irq 19
[   34.828042] ide1: Found Apple KeyLargo ATA-3 controller, bus ID 0, irq 20
[   34.828283] Probing IDE interface ide1...
[   35.228220] hdc: MATSHITACD-RW CW-8121, ATAPI CD/DVD-ROM drive
[   35.564044] hdc: Enabling MultiWord DMA 2
[   35.565237] ide1 at 0xe101e000-0xe101e007,0xe101e160 on irq 20
[   36.584038] ide2: Found Apple KeyLargo ATA-3 controller, bus ID 1, irq 21
[   36.584279] Probing IDE interface ide2...
[   37.152322] PowerMac i2c bus pmu 2 registered
[   37.159839] PowerMac i2c bus pmu 1 registered
[   37.167192] PowerMac i2c bus mac-io 0 registered
[   37.174489] PowerMac i2c bus uni-n 1 registered
[   37.181728] PowerMac i2c bus uni-n 0 registered
[   37.188943] TCP cubic registered
[   37.195836] NET: Registered protocol family 1
[   37.203057] input: PMU as /class/input/input4
[   37.210572] Registered led device: pmu-front-led
[   37.217856] Freeing unused kernel memory: 204k init
[   37.857632] Capability LSM initialized
[   37.881499] device-mapper: ioctl: 4.11.0-ioctl (2006-10-12) initialised: [email]dm-devel@redhat.com[/email]
[   38.758996] md: linear personality registered for level -1
[   38.810455] md: multipath personality registered for level -4
[   38.825559] md: raid0 personality registered for level 0
[   38.842699] md: raid1 personality registered for level 1
[   38.856989] raid5: measuring checksumming speed
[   38.876036]    8regs     :   559.000 MB/sec
[   38.896031]    8regs_prefetch:   558.000 MB/sec
[   38.916034]    32regs    :   622.000 MB/sec
[   38.936028]    32regs_prefetch:   587.000 MB/sec
[   38.936751] raid5: using function: 32regs (622.000 MB/sec)
[   39.240247] raid6: int32x1    208 MB/s
[   39.308213] raid6: int32x2    278 MB/s
[   39.376154] raid6: int32x4    373 MB/s
[   39.444204] raid6: int32x8    216 MB/s
[   39.512073] raid6: altivecx1   849 MB/s
[   39.580043] raid6: altivecx2  1110 MB/s
[   39.648066] raid6: altivecx4  1373 MB/s
[   39.716063] raid6: altivecx8  1124 MB/s
[   39.716763] raid6: using algorithm altivecx4 (1373 MB/s)
[   39.717513] md: raid6 personality registered for level 6
[   39.718257] md: raid5 personality registered for level 5
[   39.719001] md: raid4 personality registered for level 4
[   39.912153] md: raid10 personality registered for level 10
[   41.584392] usbcore: registered new interface driver usbfs
[   41.585248] usbcore: registered new interface driver hub
[   41.586073] usbcore: registered new device driver usb
[   41.590527] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   41.590648] PCI: Enabling device 0001:10:18.0 (0000 -> 0002)
[   41.591440] ohci_hcd 0001:10:18.0: OHCI Host Controller
[   41.592512] ohci_hcd 0001:10:18.0: new USB bus registered, assigned bus number 1
[   41.593374] ohci_hcd 0001:10:18.0: irq 27, io mem 0xa0002000
[   42.115978] ieee1394: Initialized config rom entry `ip1394'
[   42.172450] usb usb1: configuration #1 chosen from 1 choice
[   42.173333] hub 1-0:1.0: USB hub found
[   42.174060] hub 1-0:1.0: 2 ports detected
[   42.276420] PCI: Enabling device 0001:10:19.0 (0000 -> 0002)
[   42.277238] ohci_hcd 0001:10:19.0: OHCI Host Controller
[   42.278044] ohci_hcd 0001:10:19.0: new USB bus registered, assigned bus number 2
[   42.278909] ohci_hcd 0001:10:19.0: irq 28, io mem 0xa0001000
[   42.352181] usb usb2: configuration #1 chosen from 1 choice
[   42.353061] hub 2-0:1.0: USB hub found
[   42.353781] hub 2-0:1.0: 2 ports detected
[   42.512558] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[40]  MMIO=[f5000000-f50007ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[   42.519499] sungem.c:v0.98 8/24/03 David S. Miller (davem@redhat.com)
[   42.588367] PHY ID: 2060e1, addr: 0
[   42.589072] eth0: Sun GEM (PCI) 10/100/1000BaseT Ethernet 00:03:93:9d:ff:92 
[   42.590036] eth0: Found BCM5421 PHY


This is where 2.6.22 stalls. Is it something to do with the hard-drive?  I never see the lines below for hda.

[   43.033897] hda: max request size: 128KiB
[   43.788600] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000393fffe9dff92]

I do get this line ^^^^^^^^^^^^^^ 

[   43.926595] hda: 58605120 sectors (30005 MB), CHS=58140/16/63, UDMA(66)
[   43.927560] hda: cache flushes supported
[   43.928383]  hda: [mac] hda1 hda2 hda3 hda4 hda5 hda6
[   44.016760] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, DMA
[   44.017693] Uniform CD-ROM driver Revision: 3.20
[   44.988240] eth0: Link is up at 100 Mbps, full-duplex.

And I do get ^^^^^^^^ this line that the link is up.  I do not get any of the lines concerning the the hard drive.  After this I get nothing else. 

[   45.383651] kjournald starting.  Commit interval 5 seconds
[   45.384488] EXT3-fs: mounted filesystem with ordered data mode.
[   54.538181] eth0: Link is up at 100 Mbps, full-duplex.
[   54.538966] eth0: Pause is enabled (rxfifo: 10240 off: 7168 on: 5632)
[   60.754619] Linux agpgart interface v0.102 (c) Dave Jones
[   60.838998] agpgart: Detected Apple UniNorth 1.5 chipset
[   60.839917] agpgart: configuring for size idx: 8
[   60.840731] agpgart: AGP aperture is 32M @ 0x0
[   62.163865] Yenta: CardBus bridge found at 0001:10:1a.0 [0000:0000]


Any one else having problems booting 2.6.22?

Any ideas where to look for the problem?

And if its not something screwy that I did,  any ideas on what package to file a bug with?

Thanks for your help,

digger

---

### Post by stmiller on 2007-06-20
> [ 0.000000] Linux version 2.6.20-15-powerpc-smp (root@adare) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #3 SMP Sun Apr 15 06:49:11 UTC 2007 (Ubuntu 2.6.2
0-15.27-powerpc-smp)

According to this, it is booting the older 2.6.20-15 kernel. Or trying to at least. If you don't have another kernel option to boot into, it may get messy to try and repair.

---

### Post by digv on 2007-06-20
> **stmiller said:**
> According to this, it is booting the older 2.6.20-15 kernel. Or trying to at least. If you don't have another kernel option to boot into, it may get messy to try and repair.

Thanks for replying but you must have missed in my original post that this IS a log from the 2.6.20-15 kernel.

I don't have a log for the 2.6.22 kernel.

The boot process doesn't go go far enough to write to a log file.  I would have to try and copy by hand what is left on the screen.

To my eye and memory I do not see a difference up to the point at which it stalls. 

I was hoping that someone understanding the boot process better than me could tell me what should be happening next in the boot process that is not.

There are a number of lines concerning the ide hardrive (hda) and cdrom (hdc) that I get in the 2.6.20 log that don't ever happen in the 2.6.22 boot process.  Is a module missing?  Something with the device mapper? Something to do with LVM2?

digger

---

### Post by stmiller on 2007-06-21
Crap sorry, Yeah I totally missed that. 

Do you have any other kernel options to boot from? Like selecting 'old' from the yaboot menu. Then you could go in and try to reinstall the Gutsy kernel. Press tab and the yaboot menu to see options. 

The alternative CD has a rescue mode you can boot into to do some dirty work, though if you don't have critical info to save on the hard drive perhaps just try a reinstall of Gutsy.

---

### Post by pianoman8 on 2007-06-30
I just hit this while upgrading from feisty on my ibook g3.  It appears the ide driver either isn't loaded, or not working anymore.  My guess is the the module isn't getting loaded into the initramfs, but that's just a guess.  I'll see what i can find out..

---

### Post by jjmaestro on 2007-07-05
OK guys,

Same thing here, the problem as pianoman8 mentioned is that the initramfs does not seem to load the ide_disk kernel module.

Thus, to fix this bug:

   1. Edit  /etc/initramfs/modules and add at the bottom "ide_generic" (without the " of course :)
   2. Update the initramfs with   sudo update-initramfs
   3. reboot! :)

It worked for me, with kernel 2.6.22-7 :D

Cheers,

---

### Post by digv on 2007-07-15
I was about to file a bug, found this, and added a comment

[https://bugs.launchpad.net/ubuntu/+bug/126146](https://bugs.launchpad.net/ubuntu/+bug/126146)

---

### Post by nkbj on 2007-10-17
Has anybody had any luck booting the Gutsy RC (or later) desktop cd on a PowerMac?

Regards,
Niels Kristian

---

