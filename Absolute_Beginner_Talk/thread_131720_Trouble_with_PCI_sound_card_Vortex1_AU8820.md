---
title: "Trouble with PCI sound card Vortex1 AU8820"
date: 2006-02-17
forum: Absolute Beginner Talk
---

### Post by JackS on 2006-02-17
Hello,
I began my first install of ubuntu 5.10 about two weeks ago.  It detected
most of my peripherals (scanner, printer, mouse, etc).  The sound card
built into the motherboard was not detected and did not make a sound.
I looked around on the board and found a chip with Crystal CX4237B-XQ3
on it.  Tried to find information to get it working, and realized I am in way
over my head.

So I looked at the list of PCI sound cards that are reported to work well
with the 5.10 OS.  I bought and installed a Vortex1 sound card with the
AU8820 chipset (it says so on the biggest chip on the board).  It was
automatically detected by the OS, but I still do not have sound.

sunbus@sunbus73:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. 440LX/EX - 82443LX/EX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 440LX/EX - 82443LX/EX AGP bridge (rev 03)
0000:00:07.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:0a.0 Multimedia audio controller: Aureal Semiconductor Vortex 1 (rev 02)
0000:00:0b.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)
0000:00:0e.0 VGA compatible controller: ATI Technologies Inc 264VT4 [Mach64 VT4] (rev 3a)
sunbus@sunbus73:~$
sunbus@sunbus73:~$ dmesg
[4294667.296000] Linux version 2.6.12-10-386 (buildd@terranova) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Feb 13 12:13:15 UTC 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[4294667.296000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000f2400 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 0000000010000000 (usable)
[4294667.296000]  BIOS-e820: 00000000ffff2400 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 256MB LOWMEM available.
[4294667.296000] On node 0 totalpages: 65536
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:1
[4294667.296000]   Normal zone: 61440 pages, LIFO batch:31
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:1
[4294667.296000] DMI not present.
[4294667.296000] ACPI: Unable to locate RSDP
[4294667.296000] Allocating PCI resources starting at 10000000 (gap: 10000000:efff2400)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda1 ro quiet splash
[4294667.296000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[4294667.296000] mapped APIC to ffffd000 (01201000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[    0.000000] Detected 334.211 MHz processor.
[   38.260984] Using tsc for high-res timesource
[   38.262618] Console: colour VGA+ 80x25
[   38.266041] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   38.268151] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   38.318003] Memory: 251268k/262144k available (1416k kernel code, 10308k reserved, 762k data, 224k init, 0k highmem)
[   38.318026] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   38.318338] Calibrating delay loop... 659.45 BogoMIPS (lpj=329728)
[   38.339546] Security Framework v1.0.0 initialized
[   38.339573] SELinux:  Disabled at boot.
[   38.339631] Mount-cache hash table entries: 512
[   38.340075] CPU: After generic identify, caps: 0183f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   38.340115] CPU: After vendor identify, caps: 0183f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   38.340164] CPU: L1 I cache: 16K, L1 D cache: 16K
[   38.340181] CPU: L2 cache: 512K
[   38.340195] CPU: After all inits, caps: 0183f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[   38.340225] CPU: Intel Pentium II (Deschutes) stepping 00
[   38.340247] Enabling fast FPU save and restore... done.
[   38.340267] Checking 'hlt' instruction... OK.
[   38.343412] Checking for popad bug... OK.
[   38.344048] checking if image is initramfs... it is
[   40.816520] Freeing initrd memory: 5171k freed
[   40.819569] NET: Registered protocol family 16
[   40.819729] EISA bus registered
[   40.820867] PCI: PCI BIOS revision 2.10 entry at 0xfd9c3, last bus=1
[   40.820898] PCI: Using configuration type 1
[   40.820917] mtrr: v2.0 (20020519)
[   40.822669] ACPI: Subsystem revision 20050729
[   40.822684] ACPI: Interpreter disabled.
[   40.822704] Linux Plug and Play Support v0.97 (c) Adam Belay
[   40.822739] pnp: PnP ACPI: disabled
[   40.822755] PnPBIOS: Scanning system for PnP BIOS support...
[   40.822843] PnPBIOS: Found PnP BIOS installation structure at 0xc00f7f30
[   40.822865] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xa9d2, dseg 0x400
[   40.832056] PnPBIOS: 17 nodes reported by PnP BIOS; 17 recorded by driver
[   40.832273] PCI: Probing PCI hardware
[   40.832290] PCI: Probing PCI hardware (bus 00)
[   40.833777] Boot video device is 0000:00:0e.0
[   40.836108] PCI: Using IRQ router PIIX/ICH [8086/7110] at 0000:00:07.0
[   40.836153] PCI: IRQ 0 for device 0000:00:07.2 doesn't match PIRQ mask - try pci=usepirqmask
[   40.836183] PCI: IRQ 0 for device 0000:00:0a.0 doesn't match PIRQ mask - try pci=usepirqmask
[   40.836208] PCI: IRQ 0 for device 0000:00:0b.0 doesn't match PIRQ mask - try pci=usepirqmask
[   40.838783] pnp: 00:01: ioport range 0x15c-0x15d has been reserved
[   40.838833] pnp: 00:0b: ioport range 0x4d0-0x4d1 has been reserved
[   40.838853] pnp: 00:0b: ioport range 0x8000-0x803f has been reserved
[   40.838872] pnp: 00:0b: ioport range 0x2180-0x218f has been reserved
[   40.842574] audit: initializing netlink socket (disabled)
[   40.842606] audit: initialized
[   40.843153] VFS: Disk quotas dquot_6.5.1
[   40.843257] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   40.843434] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[   40.843467] devfs: boot_options: 0x0
[   40.843617] Initializing Cryptographic API
[   40.843644] Limiting direct PCI/PCI transfers.
[   40.844142] isapnp: Scanning for PnP cards...
[   40.953874] isapnp: Card 'CS4237B  Audio'
[   40.953891] isapnp: 1 Plug & Play card detected total
[   41.089634] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   41.092219] serio: i8042 AUX port at 0x60,0x64 irq 12
[   41.092406] serio: i8042 KBD port at 0x60,0x64 irq 1
[   41.092430] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
[   41.092770] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   41.107207] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   41.108046] io scheduler noop registered
[   41.108124] io scheduler anticipatory registered
[   41.108159] io scheduler deadline registered
[   41.108207] io scheduler cfq registered
[   41.110993] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   41.111598] EISA: Probing bus 0 at eisa.0
[   41.111679] Cannot allocate resource for EISA slot 8
[   41.111694] EISA: Detected 0 cards.
[   41.111823] NET: Registered protocol family 2
[   41.121225] IP: routing cache hash table of 2048 buckets, 16Kbytes
[   41.122065] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   41.122996] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[   41.123442] TCP: Hash tables configured (established 16384 bind 16384)
[   41.123897] NET: Registered protocol family 8
[   41.123913] NET: Registered protocol family 20
[   41.125511] Freeing unused kernel memory: 224k freed
[   41.198224] input: AT Translated Set 2 keyboard on isa0060/serio0
[   41.217871] vga16fb: initializing
[   41.217889] vga16fb: mapped to 0xc00a0000
[   41.356024] Console: switching to colour frame buffer device 80x30
[   41.356055] fb0: VGA16 VGA frame buffer device
[   42.665060] Capability LSM initialized
[   42.737003] NET: Registered protocol family 1
[   42.812263] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   42.812312] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   42.843202] PIIX4: IDE controller at PCI slot 0000:00:07.1
[   42.843262] PIIX4: chipset revision 1
[   42.843276] PIIX4: not 100% native mode: will probe irqs later
[   42.843310]     ide0: BM-DMA at 0xdcf0-0xdcf7, BIOS settings: hda:DMA, hdb:pio
[   42.843356]     ide1: BM-DMA at 0xdcf8-0xdcff, BIOS settings: hdc:pio, hdd:DMA
[   42.843394] Probing IDE interface ide0...
[   43.106778] hda: QUANTUM Bigfoot TX8.0AT, ATA DISK drive
[   43.718963] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   43.719221] Probing IDE interface ide1...
[   44.084612] hdc: CD-524EA, ATAPI CD/DVD-ROM drive
[   44.798494] hdd: CR-48XGTE, ATAPI CD/DVD-ROM drive
[   44.849479] ide1 at 0x170-0x177,0x376 on irq 15
[   44.850188] Probing IDE interface ide2...
[   45.362275] Probing IDE interface ide3...
[   45.875194] Probing IDE interface ide4...
[   46.388108] Probing IDE interface ide5...
[   46.927351] hda: max request size: 128KiB
[   46.927374] hda: 15698592 sectors (8037 MB) w/69KiB Cache, CHS=15574/16/63, UDMA(33)
[   46.927402] hda: cache flushes not supported
[   46.927701]  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
[   47.013844] hdc: ATAPI 24X CD-ROM drive, 128kB Cache
[   47.013874] Uniform CD-ROM driver Revision: 3.20
[   47.017425] hdd: ATAPI 54X CD-ROM CD-R/RW drive, 2048kB Cache
[   49.026756] Attempting manual resume
[   49.034804] swsusp: Suspend partition has wrong signature?
[   49.268476] usbcore: registered new driver usbfs
[   49.268689] usbcore: registered new driver hub
[   49.277526] USB Universal Host Controller Interface driver v2.2
[   49.277817] PCI: Enabling device 0000:00:07.2 (0000 -> 0001)
[   49.277848] PCI: IRQ 0 for device 0000:00:07.2 doesn't match PIRQ mask - try pci=usepirqmask
[   49.277875] PCI: setting IRQ 10 as level-triggered
[   49.277891] PCI: Assigned IRQ 10 for device 0000:00:07.2
[   49.277959] uhci_hcd 0000:00:07.2: Intel Corporation 82371AB/EB/MB PIIX4 USB
[   49.340208] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[   49.340246] uhci_hcd 0000:00:07.2: irq 10, io base 0x0000dcc0
[   49.340957] hub 1-0:1.0: USB hub found
[   49.341006] hub 1-0:1.0: 2 ports detected
[   49.485168] 8139too Fast Ethernet driver 0.9.27
[   49.485405] PCI: Enabling device 0000:00:0b.0 (0004 -> 0007)
[   49.485433] PCI: IRQ 0 for device 0000:00:0b.0 doesn't match PIRQ mask - try pci=usepirqmask
[   49.485461] PCI: Assigned IRQ 10 for device 0000:00:0b.0
[   49.486124] eth0: RealTek RTL8139 at 0xd800, 00:0d:88:22:01:1a, IRQ 10
[   49.486141] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   49.509625] usb 1-2: new full speed USB device using uhci_hcd and address 2
[   54.130395] Attempting manual resume
[   54.160761] swsusp: Suspend partition has wrong signature?
[   54.269101] kjournald starting.  Commit interval 5 seconds
[   54.269154] EXT3-fs: mounted filesystem with ordered data mode.
[   56.988592] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[   67.707215] Adding 353388k swap on /dev/hda5.  Priority:-1 extents:1
[   68.196843] EXT3 FS on hda1, internal journal
[   90.599010] parport: PnPBIOS parport detected.
[   90.599095] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   90.708938] lp0: using parport0 (interrupt-driven).
[   90.855225] mice: PS/2 mouse device common for all mice
[   91.269380] logips2pp: Detected unknown logitech mouse model 86
[   91.330835] input: ImExPS/2 Logitech Explorer Mouse on isa0060/serio1
[   92.999680] ts: Compaq touchscreen protocol output
[   96.722454] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[   99.087942] cdrom: open failed.
[   99.092048] cdrom: open failed.
[  104.465217] Linux agpgart interface v0.101 (c) Dave Jones
[  104.518453] agpgart: Detected an Intel 440LX Chipset.
[  104.549692] agpgart: AGP aperture is 64M @ 0xf8000000
[  105.351355] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  105.382975] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x1001
[  106.777404] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[  108.043544] PCI: Enabling device 0000:00:0a.0 (0000 -> 0003)
[  108.043577] PCI: IRQ 0 for device 0000:00:0a.0 doesn't match PIRQ mask - try pci=usepirqmask
[  108.043607] PCI: Assigned IRQ 10 for device 0000:00:0a.0
[  108.043735] Vortex: init.... <6>done.
[  108.449042] gameport: AU88x0 Gameport is pci0000:00:0a.0/gameport0, speed 1924kHz
[  114.174252] Real Time Clock Driver v1.12
[  114.721020] input: PC Speaker
[  116.168493] Floppy drive(s): fd0 is 1.44M
[  116.182979] FDC 0 is a National Semiconductor PC87306
[  118.629234] pnp: Device 01:01.01 activated.
[  118.646080] gameport: NS558 PnP Gameport is pnp01:01.01/gameport0, io 0x200, speed 784kHz
[  121.861239] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  121.941365] NET: Registered protocol family 17
[  123.844708] NET: Registered protocol family 10
[  123.845386] Disabled Privacy Extensions on device c02eb280(lo)
[  123.846281] IPv6 over IPv4 tunneling driver
[  134.488710] eth0: no IPv6 routers present
[  159.885719] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  164.457606] Bluetooth: Core ver 2.7
[  164.457645] NET: Registered protocol family 31
[  164.457658] Bluetooth: HCI device and connection manager initialized
[  164.457704] Bluetooth: HCI socket layer initialized
[  164.593706] Bluetooth: L2CAP ver 2.7
[  164.593729] Bluetooth: L2CAP socket layer initialized
[  164.678668] Bluetooth: RFCOMM ver 1.5
[  164.678712] Bluetooth: RFCOMM socket layer initialized
[  164.678783] Bluetooth: RFCOMM TTY layer initialized
sunbus@sunbus73:~$
sunbus@sunbus73:~$ cat /proc/version
Linux version 2.6.12-10-386 (buildd@terranova) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Feb 13 12:13:15 UTC 2006
sunbus@sunbus73:~$

Sorry to post such a long message here, but I read that this information is
a prerequisite.  Thanks for any advice you can provide.  -Jack

---

### Post by romdos on 2006-02-17
i'm not to sure about your pci sound card, but that onboard crystal sound chip sounds like an old isa sound chip to me. To get the crystal up and going, take out the pci card, boot up and open a terminal and type:

sudo modprobe snd-cs4236 dma1=1 dma2=3 io=0x0534 irq=5

now log out of the desktop to the login screen and when you log back in your isa sound should be working.

so you don't have to do this everytime you boot, add the following line to /etc/modules 

snd-cs4236 dma1=1 dma2=3 io=0x0534 irq=5

it is too bad that isa sound isn't well suported in ubuntu, there are a lot extra steps needed to get the 'ol cards working

---

### Post by JackS on 2006-02-17
Thank you for your reply, romdos.
I will certainly keep your suggestions at hand should I fail to get my PCI sound
card running.

According to this URL, the Aureal Vortex1 au8820 should work 'out of the box'.
<https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards?highlight=%28card%29%7C%28sound%29>
I think I am very close to a solution with this PCI sound card.

Here is some additional information which may be helpful in finding a solution

sunbus@sunbus73:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: au8820 [au8820], device 0: AU88x0 ADB [adb]
  Subdevices: 16/16
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
card 0: au8820 [au8820], device 3: AU88x0 WT [wt]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
sunbus@sunbus73:~$ lspci -v
0000:00:00.0 Host bridge: Intel Corp. 440LX/EX - 82443LX/EX Host bridge (rev 03)        Flags: bus master, medium devsel, latency 32
        Memory at f8000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: Intel Corp. 440LX/EX - 82443LX/EX AGP bridge (rev 03) (prog-if 00 [Normal decode])
        Flags: 66MHz, medium devsel
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32

0000:00:07.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
        Flags: bus master, medium devsel, latency 0

0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
        Flags: bus master, medium devsel, latency 32
        I/O ports at dcf0 [size=16]

0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])
        Flags: bus master, medium devsel, latency 32, IRQ 10
        I/O ports at dcc0 [size=32]

0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
        Flags: medium devsel, IRQ 9

0000:00:0a.0 Multimedia audio controller: Aureal Semiconductor Vortex 1 (rev 02)        Flags: bus master, medium devsel, latency 32, IRQ 10
        Memory at fede0000 (32-bit, non-prefetchable) [size=128K]
        I/O ports at dce0 [size=8]
        I/O ports at dce8 [size=8]
        Capabilities: <available only to root>

0000:00:0b.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)
        Subsystem: D-Link System Inc DFE-530TX+ 10/100 Ethernet Adapter
        Flags: bus master, medium devsel, latency 32, IRQ 10
        I/O ports at d800 [size=256]
        Memory at feddfc00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:0e.0 VGA compatible controller: ATI Technologies Inc 264VT4 [Mach64 VT4] (rev 3a) (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc 264VT4 [Mach64 VT4]
        Flags: bus master, stepping, medium devsel, latency 66
        Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        I/O ports at d400 [size=256]
        Memory at fedde000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

Thank you for any advice or encouragement you can send my way.
This is my very first time using the Linux OS and aside from this
sound card dissapointment all has gone well.   -Jack

---

### Post by JackS on 2006-02-17
Romdos,
I tried your suggestion and it failed to produce the desired result

sunbus@sunbus73:/etc$ sudo modprobe snd-cs4236 dma1=1 dma2=3 io=0x0534 irq=5
FATAL: Error inserting snd_cs4236 (/lib/modules/2.6.12-10-386/kernel/sound/isa/cs423x/snd-cs4236.ko): No such device
FATAL: Error running install command for snd_cs4236
sunbus@sunbus73:/etc$

I am further along using the PCI card, so I am going back to that hardware config.



With regard to the Vortex1 au8820 PCI sound card, I have checked some of the
obvious things.  The wiring connections from the bracket to the speakers is
correct.  The powered speakers are turned on.  Also, I ran "alsamixer" and
made sure that none of the outputs are muted.  Still stuck with no sound.  -Jack

---

### Post by romdos on 2006-02-17
hmmm...

i found a vortex1 AU8820 and it seems to be up and working in breezy

guest@freekbox:~$ lspci
0000:00:0d.0 Multimedia audio controller: Aureal Semiconductor Vortex 1 (rev 02)


is the snd_au8820 module loaded?

guest@freekbox:~$ lsmod | grep snd_au8820
snd_au8820             32192  1
gameport               14472  2 snd_au8820
snd_ac97_codec         72188  1 snd_au8820
snd_pcm                78344  3 snd_au8820,snd_ac97_codec,snd_pcm_oss
snd_mpu401_uart         6784  1 snd_au8820
snd                    48644  11 snd_au8820,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device

if not, try:
guest@freekbox:~$ modprobe snd_au8820

does the little speaker icon in the upper right have an X through it, or can you click on it to make adjustments?

if everything looks like it should be working, perhaps there are some resourse configuration settings in you bios that are conflicting with your card...

---

### Post by JackS on 2006-02-17
It looks like the snd_au8820 is as it should be:

sunbus@sunbus73:~$ lsmod | grep snd_au8820
snd_au8820             32192  1
gameport               14472  4 ns558,snd_au8820
snd_ac97_codec         72188  1 snd_au8820
snd_pcm                78344  3 snd_au8820,snd_ac97_codec,snd_pcm_oss
snd_mpu401_uart         6784  1 snd_au8820
snd                    48644  11 snd_au8820,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
sunbus@sunbus73:~$

There's no little red X on the speaker icon next to the date/clock.

I looked in bios and did not find anything related to a PCI sound card.

Thanks for your reply.  -Jack

---

### Post by JackS on 2006-02-17
Bad news and good news:

The bad news is that the Vortex1 au8820 PCI sound card is broken.
I bought it second hand from an auction on ebay.  Caveat emptor.
:-(

The good news is that a friend of mine took sympathy on me and
gave me a used Vortex1 au8810 PCI sound card.  I plugged into the
PCI slot and as it booted up I heard the speakers crackle.  :-)
Then, at the Ubuntu login I heard the sound of drumbeats in the
distance.  IT'S ALIVE!!!

Thank you all so very much for your guidance and assistance.
I'm sure I will be back here with more questions as I continue to
use Ubuntu.  -Jack

---

