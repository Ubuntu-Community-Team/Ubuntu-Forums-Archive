---
title: "Help with no sound or flash on Mac Quicksilver 2002 w/ Intrepid Ibex"
date: 2009-05-30
forum: Apple Hardware Users
---

### Post by MIBPreacher on 2009-05-30
Can someone help me out.  I have Intrepid Ibex running on a Mac Quicksilver 2002.  I have the following problems, and I am a veteran MS user but a total newb when it comes to Ubuntu 

1.  My sound does not work, when I click on the icon for the speaker, it says that it doesnt recognize any sound devices, but when I had previously installed Dapper Drake that I was trying to get my old Imac to run off of, it autodetected the sound since I could see and hear the nelson mandela video.

2.  I cant get Flash files to play and I am still learning the commands in Ubuntu.

If someone could help me out with the line commands to fix these, that would be freakin awesome.

---

### Post by MIBPreacher on 2009-05-31
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2

---

### Post by MIBPreacher on 2009-05-31
mibpreacher@TitaniumG4:~$ aplay -l
aplay: device_list:215: no soundcards found...
mibpreacher@TitaniumG4:~$ alsactl -v
alsactl version 1.0.17
mibpreacher@TitaniumG4:~$ dmesg
[    0.000000] Crash kernel location must be 0x2000000
[    0.000000] Reserving 0MB of memory at 32MB for crashkernel (System RAM: 768MB)
[    0.000000] Using PowerMac machine description
[    0.000000] Total memory = 768MB; using 2048kB for hash table (at cfe00000)
[    0.000000] Linux version 2.6.25-2-powerpc (buildd@adare) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu8) ) #1 Tue Sep 30 14:49:00 UTC 2008
[    0.000000] Found initrd at 0xc1a00000:0xc2263000
[    0.000000] Found UniNorth memory controller & host bridge @ 0xf8000000 revision: 0x11
[    0.000000] Mapped at 0xfdfc0000
[    0.000000] Found a Keylargo mac-io controller, rev: 3, mapped at 0xfdf40000
[    0.000000] PowerMac motherboard: PowerMac G4 Silver
[    0.000000] console [udbg0] enabled
[    0.000000] Entering add_active_range(0, 0, 196608) 0 entries of 256 used
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
[    0.000000] nvram: gen0=880, gen1=879
[    0.000000] nvram: Active bank is: 0
[    0.000000] nvram: OF partition at 0x410
[    0.000000] nvram: XP partition at 0x1020
[    0.000000] nvram: NR partition at 0x1120
[    0.000000] Top of RAM: 0x30000000, Total RAM: 0x30000000
[    0.000000] Memory hole size: 0MB
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->   196608
[    0.000000]   Normal     196608 ->   196608
[    0.000000]   HighMem    196608 ->   196608
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   196608
[    0.000000] On node 0 totalpages: 196608
[    0.000000]   DMA zone: 1536 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 195072 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 195072
[    0.000000] Kernel command line: root=/dev/hda3 ro quiet splash 
[    0.000000] mpic: Setting up MPIC " MPIC 1   " version 1.2 at 80040000, max 4 CPUs
[    0.000000] mpic: ISU size: 64, shift: 6, mask: 3f
[    0.000000] mpic: Initializing for 64 sources
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] GMT Delta read from XPRAM: 0 minutes, DST: off
[    0.000000] time_init: decrementer frequency = 33.217466 MHz
[    0.000000] time_init: processor frequency   = 999.999997 MHz
[    0.000005] clocksource: timebase mult[786b27e] shift[22] registered
[    0.000013] clockevent: decrementer mult[880] shift[16] cpu[0]
[    0.000090] Console: colour dummy device 80x25
[    0.000097] console handover: boot [udbg0] -> real [tty0]
[    0.000959] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.001953] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.038470] High memory: 0k
[    0.038477] Memory: 763776k/786432k available (3688k kernel code, 22196k reserved, 132k data, 357k bss, 212k init)
[    0.038548] SLUB: Genslabs=12, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[    0.038553] Calibrating delay loop... 66.30 BogoMIPS (lpj=132608)
[    0.124048] Security Framework initialized
[    0.124065] SELinux:  Disabled at boot.
[    0.124074] Capability LSM initialized
[    0.124085] Mount-cache hash table entries: 512
[    0.124399] device-tree: Duplicate name in /cpus/PowerPC,G4@0/l2-cache, renamed to "l2-cache#1"
[    0.124435] device-tree: Duplicate name in /cpus/PowerPC,G4@0, renamed to "l2-cache#1"
[    0.124491] device-tree: Duplicate name in /cpus/PowerPC,G4@1/l2-cache, renamed to "l2-cache#1"
[    0.124529] device-tree: Duplicate name in /cpus/PowerPC,G4@1, renamed to "l2-cache#1"
[    0.125697] Initializing cgroup subsys ns
[    0.126150] net_namespace: 540 bytes
[    0.126477] NET: Registered protocol family 16
[    0.127173] KeyWest i2c @0xf8001003 irq 42 /uni-n@f8000000/i2c@f8001000
[    0.127180]  channel 0 bus <multibus>
[    0.127184]  channel 1 bus <multibus>
[    0.127205] KeyWest i2c @0x80018000 irq 26 /pci@f2000000/mac-io@17/i2c@18000
[    0.127209]  channel 0 bus <multibus>
[    0.127220] PMU i2c /pci@f2000000/mac-io@17/via-pmu@16000
[    0.127224]  channel 1 bus <multibus>
[    0.127227]  channel 2 bus <multibus>
[    0.127289] PCI: Probing PCI hardware
[    0.144087] NET: Registered protocol family 8
[    0.144093] NET: Registered protocol family 20
[    0.144805] NET: Registered protocol family 2
[    0.148014] Switched to high resolution mode on CPU 0
[    0.180080] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.180572] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.182257] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[    0.182692] TCP: Hash tables configured (established 131072 bind 65536)
[    0.182698] TCP reno registered
[    0.192299] checking if image is initramfs... it is
[    1.424198] Freeing initrd memory: 6144k freed
[    1.424883] Freeing initrd memory: 2440k freed
[    1.425187] Thermal assist unit not available
[    1.426142] audit: initializing netlink socket (disabled)
[    1.426179] type=2000 audit(1243755070.424:1): initialized
[    1.430139] VFS: Disk quotas dquot_6.5.1
[    1.430194] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.430589] io scheduler noop registered
[    1.430594] io scheduler anticipatory registered
[    1.430598] io scheduler deadline registered
[    1.430622] io scheduler cfq registered (default)
[    1.430643] pci 0000:00:10.0: nv_msi_ht_cap_quirk didn't locate host bridge
[    1.431681] Using unsupported 640x480 NVDA,Display-B at 98004000, depth=8, pitch=1024
[    1.436937] Console: switching to colour frame buffer device 80x30
[    1.441727] fb0: Open Firmware frame buffer device on /pci@f0000000/NVDA,Parent@10/NVDA,Display-B@1
[    1.483589] Generic RTC Driver v1.07
[    1.483667] Macintosh non-volatile memory driver v1.1
[    1.485053] brd: module loaded
[    1.485137] MacIO PCI driver attached to Keylargo chipset
[    1.486751] input: Macintosh mouse button emulation as /class/input/input0
[    1.487139] Uniform Multi-Platform E-IDE driver
[    1.487146] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.487240] adb: starting probe task...
[    1.487248] adb: finished probe task...
[    1.524009] ide0: Found Apple KeyLargo ATA-4 controller, bus ID 2, irq 19
[    1.524029] Probing IDE interface ide0...
[    1.556307] hda: ST340016A, ATA DISK drive
[    1.620030] hda: host max PIO4 wanted PIO255(auto-tune) selected PIO4
[    1.620196] hda: UDMA/66 mode selected
[    1.620294] ide0 at 0xf1014000-0xf1014007,0xf1014160 on irq 19
[    1.660007] ide1: Found Apple KeyLargo ATA-3 controller, bus ID 0, irq 20
[    1.660020] Probing IDE interface ide1...
[    1.700178] hdc: MATSHITADVD-ROM SR-8585, ATAPI CD/DVD-ROM drive
[    1.732022] hdc: host max PIO4 wanted PIO255(auto-tune) selected PIO4
[    1.732102] hdc: MWDMA2 mode selected
[    1.732202] ide1 at 0xf1016000-0xf1016007,0xf1016160 on irq 20
[    1.772007] ide2: Found Apple KeyLargo ATA-3 controller, bus ID 1, irq 21
[    1.772020] Probing IDE interface ide2...
[    1.840131] mice: PS/2 mouse device common for all mice
[    1.840283] PowerMac i2c bus pmu 2 registered
[    1.840361] PowerMac i2c bus pmu 1 registered
[    1.840426] PowerMac i2c bus mac-io 0 registered
[    1.840492] PowerMac i2c bus uni-n 1 registered
[    1.840558] PowerMac i2c bus uni-n 0 registered
[    1.841393] NET: Registered protocol family 1
[    1.841675] registered taskstats version 1
[    1.841914] input: PMU as /class/input/input1
[    1.852043] Freeing unused kernel memory: 212k init
[    2.236671] fuse init (API version 7.9)
[    4.388343] sungem.c:v0.98 8/24/03 David S. Miller (davem@redhat.com)
[    4.418001] usbcore: registered new interface driver usbfs
[    4.418046] usbcore: registered new interface driver hub
[    4.429062] usbcore: registered new device driver usb
[    4.431920] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.431987] PCI: Enabling device 0001:10:18.0 (0000 -> 0002)
[    4.432020] ohci_hcd 0001:10:18.0: OHCI Host Controller
[    4.432329] ohci_hcd 0001:10:18.0: new USB bus registered, assigned bus number 1
[    4.432366] ohci_hcd 0001:10:18.0: irq 27, io mem 0x80081000
[    4.508189] usb usb1: configuration #1 chosen from 1 choice
[    4.508238] hub 1-0:1.0: USB hub found
[    4.508260] hub 1-0:1.0: 2 ports detected
[    4.556432] PHY ID: 2060e1, addr: 0
[    4.557360] eth0: Sun GEM (PCI) 10/100/1000BaseT Ethernet 00:03:93:75:c1:e0
[    4.557366] eth0: Found BCM5421 PHY
[    4.612252] PCI: Enabling device 0001:10:19.0 (0000 -> 0002)
[    4.612278] ohci_hcd 0001:10:19.0: OHCI Host Controller
[    4.612325] ohci_hcd 0001:10:19.0: new USB bus registered, assigned bus number 2
[    4.612365] ohci_hcd 0001:10:19.0: irq 28, io mem 0x80080000
[    4.688129] usb usb2: configuration #1 chosen from 1 choice
[    4.688182] hub 2-0:1.0: USB hub found
[    4.688204] hub 2-0:1.0: 2 ports detected
[    4.846113] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[40]  MMIO=[f5000000-f50007ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    4.964030] usb 1-1: new low speed USB device using ohci_hcd and address 2
[    5.083218] hda: max request size: 128KiB
[    5.084042] hda: Host Protected Area detected.
[    5.084045]     current capacity is 78163247 sectors (40019 MB)
[    5.084048]     native  capacity is 78165360 sectors (40020 MB)
[    5.088007] hda: Host Protected Area disabled.
[    5.088013] hda: 78165360 sectors (40020 MB) w/2048KiB Cache, CHS=65535/16/63
[    5.088020] hda: cache flushes not supported
[    5.088097]  hda: [mac] hda1 hda2 hda3 hda4
[    5.174233] usb 1-1: configuration #1 chosen from 1 choice
[    5.201901] hdc: ATAPI 32X DVD-ROM drive, 512kB Cache
[    5.201911] Uniform CD-ROM driver Revision: 3.20
[    5.484109] usb 2-1: new low speed USB device using ohci_hcd and address 2
[    5.576000] usb 2-1: configuration #1 chosen from 1 choice
[    5.576368] usbcore: registered new interface driver hiddev
[    5.581614] input: Microsoft Basic Optical Mouse as /class/input/input2
[    5.592117] input,hidraw0: USB HID v1.10 Mouse [Microsoft Basic Optical Mouse] on usb-0001:10:18.0-1
[    5.597652] input: CHICONY USB Keyboard as /class/input/input3
[    5.608071] input,hidraw1: USB HID v1.10 Keyboard [CHICONY USB Keyboard] on usb-0001:10:19.0-1
[    5.613514] input: CHICONY USB Keyboard as /class/input/input4
[    5.624083] input,hidraw2: USB HID v1.10 Mouse [CHICONY USB Keyboard] on usb-0001:10:19.0-1
[    5.624125] usbcore: registered new interface driver usbhid
[    5.624132] /build/buildd/linux-ports-2.6.25/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[    5.840139] PM: Starting manual resume from disk
[    5.896013] kjournald starting.  Commit interval 5 seconds
[    5.896036] EXT3-fs: mounted filesystem with ordered data mode.
[    6.068210] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000393fffe75c1e0]
[    6.420393] eth0: Link is up at 100 Mbps, full-duplex.
[   10.089717] udevd version 124 started
[   14.992085] Linux agpgart interface v0.103
[   15.012086] agpgart: Detected Apple UniNorth 1.5 chipset
[   15.012214] agpgart: configuring for size idx: 8
[   15.024014] agpgart: AGP aperture is 32M @ 0x0
[   18.927349] pmac_zilog: 0.6 (Benjamin Herrenschmidt <benh@kernel.crashing.org>)
[   18.927410] pmac_zilog: i2c-modem detected, id: 1
[   18.927463] ttyPZ0 at MMIO 0x80013020 (irq = 22) is a Z85c30 ESCC - Internal modem
[   18.927716] ttyPZ1 at MMIO 0x80013000 (irq = 29) is a Z85c30 ESCC - Serial port
[   20.891593] apm_emu: PMU APM Emulation initialized.
[   20.949285] loop: module loaded
[   21.010593] SCSI subsystem initialized
[   21.428004] Adding 1650020k swap on /dev/hda4.  Priority:-1 extents:1 across:1650020k
[   21.741556] EXT3 FS on hda3, internal journal
[   22.994126] ip_tables: (C) 2000-2006 Netfilter Core Team
[   25.359087] NET: Registered protocol family 10
[   25.360467] lo: Disabled Privacy Extensions
[   25.681044] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   25.998524] hda: host max PIO4 wanted PIO0 selected PIO0
[   26.165750] lp: driver loaded but no devices found
[   26.377624] ppdev: user-space parallel port driver
[   26.940006] hda: task_no_data_intr: status=0x51 { DriveReady SeekComplete Error }
[   26.940006] hda: task_no_data_intr: error=0x04 { DriveStatusError }
[   26.940006] ide: failed opcode was: 0xef
[   28.296020] input: Mouseemu virtual keyboard as /class/input/input5
[   28.321170] input: Mouseemu virtual mouse as /class/input/input6
[   29.108529] Bluetooth: Core ver 2.11
[   29.109352] NET: Registered protocol family 31
[   29.109358] Bluetooth: HCI device and connection manager initialized
[   29.109365] Bluetooth: HCI socket layer initialized
[   29.325408] Bluetooth: L2CAP ver 2.9
[   29.325420] Bluetooth: L2CAP socket layer initialized
[   29.426505] Bluetooth: RFCOMM socket layer initialized
[   29.427237] Bluetooth: RFCOMM TTY layer initialized
[   29.427245] Bluetooth: RFCOMM ver 1.8
[   29.498024] Bluetooth: SCO (Voice Link) ver 0.5
[   29.498038] Bluetooth: SCO socket layer initialized
[   29.590173] Bluetooth: BNEP (Ethernet Emulation) ver 1.2
[   29.590186] Bluetooth: BNEP filters: protocol multicast
[   29.682470] Bridge firewalling registered
[   29.683409] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   33.081214] eth0: Link is up at 100 Mbps, full-duplex.
[   33.081229] eth0: Pause is enabled (rxfifo: 10240 off: 7168 on: 5632)
[   33.887270] NET: Registered protocol family 17
[   38.728018] eth0: no IPv6 routers present
mibpreacher@TitaniumG4:~$

---

### Post by MIBPreacher on 2009-05-31
I have upgraded to Jaunty 9.04 via the upgrade program.  This did NOT solve my sound problem either.

---

