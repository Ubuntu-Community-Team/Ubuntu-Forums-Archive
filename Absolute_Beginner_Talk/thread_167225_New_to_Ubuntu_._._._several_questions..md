---
title: "New to Ubuntu . . . several questions."
date: 2006-04-28
forum: Absolute Beginner Talk
---

### Post by ZelasMetallium on 2006-04-28
Okay, so I have Ubuntu on my computer. Yay.  Now I'm just really really confused. :???: 

Haha, okay, so, I've used Windows for most of my life which is pretty straight forward.  Now, as I'm trying to find equivalents in Ubuntu, I'm completely lost.  You see, I have an external HD but I can't for the life of me seem to be able to access it.  What's the Ubuntu equivalent of "My Computer?"

Also, how do I go about downloading and installing programs.  I looked into getting gtkpod but it wouldn't allow me to download it from SourceForge, saying:  XML pasring Error: not well0formed
Location: hcrome://mozapps/content/downloads/unknownContentType.xul
Line Number 1, Column 1:

/downloads/unknownContent Type.xulUT
^

Any help?

---

### Post by Kethinov on 2006-04-28
What filesystem is the external hard drive using? If it's NTFS, you can make Linux *see* the device, but you won't be able to write new files or modify any of the data because Linux does not support writing to NTFS yet.

Install gtkpod by going to System > Administration > Synaptic Package Manager and doing a search for gtkpod, or simply finding it on the huge list. You install it from there. Alternatively, you can open a terminal and run **sudo apt-get install gtkpod**. It will ask you for your password, then it will install the program.

---

### Post by ZelasMetallium on 2006-04-28
Okay, got GTKPod working (And wow, I really like how you add applications in this OS.) but I don't know what filesystem my hard drive is using.  Do you know how I can find out or change it?

---

### Post by rs3 on 2006-04-28
Regarding your external hard drive--if it is plugged in and powered on, it should appear on the desktop.  But, you'll find the equivalent of My Computer by clicking the Places menu in the top panel, and selecting "Computer" :)

---

### Post by ZelasMetallium on 2006-04-28
The only thing on my desktop is "/" which appears to be a USB drive (Which my HD is.) but it reads as only a GB of free space when the HD is clear so it should have ~80 GB.

Under System => Administration => Discs I see it but I can't seem to, like 'Open' it for use.

---

### Post by Kethinov on 2006-04-28
Do us a favor that will help us understand your situation a little more.

Open a terminal (Applications > Accessories > Terminal) and run **gedit /etc/fstab** and post the contents of that file here.

Also at the terminal run **dmesg** and post that here as well. The dmesg command will spit out a lot of stuff. It's a log of everything your kernel has seen or done since you booted, and it should contain some information about that USB device of yours and possibly what filesystem is on it.

Once we know what's going on, we can show you how to mount the external hard drive and gain access to your data.

---

### Post by ZelasMetallium on 2006-04-28
[QUOTE=Kethinov]Do us a favor that will help us understand your situation a little more.

Open a terminal (Applications > Accessories > Terminal) and run **gedit /etc/fstab** and post the contents of that file here.

Also at the terminal run **dmesg** and post that here as well. The dmesg command will spit out a lot of stuff. It's a log of everything your kernel has seen or done since you booted, and it should contain some information about that USB device of yours and possibly what filesystem is on it.

Once we know what's going on, we can show you how to mount the external hard drive and gain access to your data.[/QUOTE]
Assuming I did the gedit part right, nothing was contained in the window that popped up.

dmesg showed:
[4294669.066000] Initializing Cryptographic API
[4294669.066000] isapnp: Scanning for PnP cards...
[4294669.420000] isapnp: No Plug & Play device found
[4294669.437000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[4294669.444000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294669.444000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294669.444000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
[4294669.446000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[4294669.446000] PCI: setting IRQ 5 as level-triggered
[4294669.446000] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[4294669.446000] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[4294669.446000] io scheduler noop registered
[4294669.446000] io scheduler anticipatory registered
[4294669.446000] io scheduler deadline registered
[4294669.446000] io scheduler cfq registered
[4294669.447000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294669.448000] EISA: Probing bus 0 at eisa.0
[4294669.448000] Cannot allocate resource for EISA slot 1
[4294669.448000] Cannot allocate resource for EISA slot 2
[4294669.448000] EISA: Detected 0 cards.
[4294669.448000] NET: Registered protocol family 2
[4294669.458000] IP: routing cache hash table of 4096 buckets, 32Kbytes
[4294669.458000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[4294669.458000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[4294669.458000] TCP: Hash tables configured (established 16384 bind 16384)
[4294669.458000] NET: Registered protocol family 8
[4294669.458000] NET: Registered protocol family 20
[4294669.458000] ACPI wakeup devices:
[4294669.458000] LID0 LANC USB0 USB1 MODM
[4294669.458000] ACPI: (supports S0 S3 S4 S5)
[4294669.459000] Freeing unused kernel memory: 224k freed
[4294669.473000] vga16fb: initializing
[4294669.473000] vga16fb: mapped to 0xc00a0000
[4294669.586000] Console: switching to colour frame buffer device 80x30
[4294669.586000] fb0: VGA16 VGA frame buffer device
[4294669.599000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294670.681000] Capability LSM initialized
[4294670.691000] NET: Registered protocol family 1
[4294670.705000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294670.705000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294670.705000] ACPI: bus type ide registered
[4294670.711000] ICH4: IDE controller at PCI slot 0000:00:1f.1
[4294670.711000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[4294670.711000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[4294670.711000] PCI: setting IRQ 10 as level-triggered
[4294670.711000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[4294670.711000] ICH4: chipset revision 3
[4294670.711000] ICH4: not 100% native mode: will probe irqs later
[4294670.711000]     ide0: BM-DMA at 0x1810-0x1817, BIOS settings: hda:DMA, hdb:pio
[4294670.711000]     ide1: BM-DMA at 0x1818-0x181f, BIOS settings: hdc:DMA, hdd:pio
[4294670.711000] Probing IDE interface ide0...
[4294670.975000] hda: IC25N060ATMR04-0, ATA DISK drive
[4294671.587000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294671.587000] Probing IDE interface ide1...
[4294672.259000] hdc: QSI CD-RW/DVD-ROM SBW242C, ATAPI CD/DVD-ROM drive
[4294672.871000] ide1 at 0x170-0x177,0x376 on irq 15
[4294672.871000] Probing IDE interface ide2...
[4294673.384000] Probing IDE interface ide3...
[4294673.896000] Probing IDE interface ide4...
[4294674.408000] Probing IDE interface ide5...
[4294674.923000] hda: max request size: 1024KiB
[4294674.943000] hda: 117210240 sectors (60011 MB) w/7884KiB Cache, CHS=16383/255/63, UDMA(100)
[4294674.944000] hda: cache flushes supported
[4294674.944000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
[4294675.011000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache
[4294675.011000] Uniform CD-ROM driver Revision: 3.20
[4294675.226000] Attempting manual resume
[4294675.256000] swsusp: Suspend partition has wrong signature?
[4294675.323000] usbcore: registered new driver usbfs
[4294675.323000] usbcore: registered new driver hub
[4294675.323000] USB Universal Host Controller Interface driver v2.2
[4294675.324000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[4294675.324000] PCI: setting IRQ 11 as level-triggered
[4294675.324000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4294675.324000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[4294675.324000] uhci_hcd 0000:00:1d.0: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
[4294675.386000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[4294675.386000] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00001820
[4294675.386000] hub 1-0:1.0: USB hub found
[4294675.386000] hub 1-0:1.0: 2 ports detected
[4294675.389000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[4294675.389000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4294675.389000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[4294675.389000] uhci_hcd 0000:00:1d.1: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
[4294675.451000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[4294675.451000] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001840
[4294675.451000] hub 2-0:1.0: USB hub found
[4294675.451000] hub 2-0:1.0: 2 ports detected
[4294675.470000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10
[4294675.470000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 10 (level, low) -> IRQ 10
[4294675.470000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[4294675.470000] ehci_hcd 0000:00:1d.7: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
[4294675.470000] ehci_hcd 0000:00:1d.7: debug port 1
[4294675.470000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 3
[4294675.470000] ehci_hcd 0000:00:1d.7: irq 10, io mem 0xe0100000
[4294675.474000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[4294675.474000] ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[4294675.474000] hub 3-0:1.0: USB hub found
[4294675.474000] hub 3-0:1.0: 4 ports detected
[4294675.549000] b44.c:v0.95 (Aug 3, 2004)
[4294675.549000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4294675.553000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:e0:b8:91:2c:49
[4294675.870000] usb 3-1: new high speed USB device using ehci_hcd and address 2[4294676.305000] usb 1-2: new low speed USB device using uhci_hcd and address 2
[4294677.608000] usbcore: registered new driver hiddev
[4294677.625000] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.0-2
[4294677.625000] usbcore: registered new driver usbhid
[4294677.625000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
[4294677.650000] SCSI subsystem initialized
[4294677.652000] Initializing USB Mass Storage driver...
[4294677.652000] scsi0 : SCSI emulation for USB Mass Storage devices
[4294677.652000] usb-storage: device found at 2
[4294677.652000] usb-storage: waiting for device to settle before scanning
[4294677.652000] usbcore: registered new driver usb-storage
[4294677.652000] USB Mass Storage support registered.
[4294677.934000] ACPI: Fan [FAN1] (off)
[4294677.937000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[4294677.938000]     ACPI-0362: *** Error: Looking up [FAN2] in namespace, AE_NOT_FOUND
[4294677.938000] search_node df211be0 start_node df211be0 return_node 00000000
[4294677.939000] ACPI: Thermal Zone [THRM] (62 C)
[4294678.123000] Attempting manual resume
[4294678.142000] swsusp: Suspend partition has wrong signature?
[4294678.206000] kjournald starting.  Commit interval 5 seconds
[4294678.206000] EXT3-fs: mounted filesystem with ordered data mode.
[4294679.410000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294681.726000] Adding 1485972k swap on /dev/hda5.  Priority:-1 extents:1
[4294681.958000] EXT3 FS on hda1, internal journal
[4294682.656000]   Vendor: Seagate   Model: External Drive    Rev:
[4294682.656000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294682.658000] usb-storage: device scan complete
[4294685.110000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[4294685.110000] sda: assuming drive cache: write through
[4294685.113000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[4294685.113000] sda: assuming drive cache: write through
[4294685.113000]  /dev/scsi/host0/bus0/target0/lun0: p1
[4294685.134000] Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
[4294689.070000] lp: driver loaded but no devices found
[4294689.133000] mice: PS/2 mouse device common for all mice
[4294689.275000] ieee1394: Initialized config rom entry `ip1394'
[4294689.280000] sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
[4294689.758000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x23aeb3, caps: 0xa04713/0x10008
[4294689.761000] input: SynPS/2 Synaptics TouchPad on isa0060/serio1
[4294689.949000] ts: Compaq touchscreen protocol output
[4294693.442000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294694.656000] Linux agpgart interface v0.101 (c) Dave Jones
[4294694.664000] agpgart: Detected an Intel 855 Chipset.
[4294694.664000] agpgart: Detected 8060K stolen memory.
[4294694.687000] agpgart: AGP aperture is 128M @ 0xe8000000
[4294694.968000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294694.979000] shpchp: shpc_init : shpc_cap_offset == 0
[4294694.979000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294695.032000] hw_random: cannot enable RNG, aborting
[4294695.449000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[4294695.449000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[4294695.755000] intel8x0_measure_ac97_clock: measured 49771 usecs
[4294695.755000] intel8x0: clocking to 48000
[4294696.192000] Linux Kernel Card Services
[4294696.192000]   options:  [pci] [cardbus] [pm]
[4294696.204000] ACPI: PCI Interrupt 0000:02:02.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4294696.204000] Yenta: CardBus bridge found at 0000:02:02.0 [107b:0460]
[4294696.204000] Yenta: Enabling burst memory read transactions
[4294696.204000] Yenta: Using CSCINT to route CSC interrupts to PCI
[4294696.204000] Yenta: Routing CardBus interrupts to PCI
[4294696.204000] Yenta TI: socket 0000:02:02.0, mfunc 0x01ac1b22, devctl 0x64
[4294696.425000] Yenta: ISA IRQ mask 0x00d8, PCI irq 11
[4294696.425000] Socket status: 30000006
[4294696.570000] ohci1394: $Rev: 1250 $ Ben Collins <bcollins@debian.org>
[4294696.570000] ACPI: PCI Interrupt 0000:02:02.2[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[4294696.624000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[10]  MMIO=[e020a000-e020a7ff]  Max Packet=[2048]
[4294697.884000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e0b80360007a06][4294698.138000] Real Time Clock Driver v1.12
[4294699.052000] NET: Registered protocol family 17
[4294700.039000] b44: eth0: Link is down.
[4294702.039000] b44: eth0: Link is up at 100 Mbps, full duplex.
[4294702.039000] b44: eth0: Flow control is off for TX and off for RX.
[4294707.654000] NET: Registered protocol family 10
[4294707.654000] Disabled Privacy Extensions on device c02eb280(lo)
[4294707.656000] IPv6 over IPv4 tunneling driver
[4294708.793000] ACPI: AC Adapter [ACAD] (on-line)
[4294708.851000] ACPI: Battery Slot [BAT0] (battery present)
[4294708.872000] ACPI: Power Button (FF) [PWRF]
[4294708.872000] ACPI: Lid Switch [LID0]
[4294708.872000] ACPI: Sleep Button (CM) [SLPB]
[4294708.980000] ibm_acpi: ec object not found
[4294709.098000] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)[4294710.061000] cs: IO port probe 0x100-0x4ff: excluding 0x4d0-0x4d7
[4294710.063000] cs: IO port probe 0xc00-0xcf7: clean.
[4294710.064000] cs: IO port probe 0xa00-0xaff: clean.
[4294718.306000] eth0: no IPv6 routers present
[4294998.930000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294998.930000] apm: overridden by ACPI.
[4294998.982000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294998.982000] apm: disabled on user request.
[4295019.840000] Bluetooth: Core ver 2.7
[4295019.840000] NET: Registered protocol family 31
[4295019.840000] Bluetooth: HCI device and connection manager initialized
[4295019.840000] Bluetooth: HCI socket layer initialized
[4295019.915000] Bluetooth: L2CAP ver 2.7
[4295019.915000] Bluetooth: L2CAP socket layer initialized
[4295020.016000] Bluetooth: RFCOMM ver 1.5
[4295020.016000] Bluetooth: RFCOMM socket layer initialized
[4295020.016000] Bluetooth: RFCOMM TTY layer initialized
[4295091.326000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4295091.326000] apm: disabled on user request.
[4295096.282000] ibm_acpi: ec object not found
[4295284.324000] b44: eth0: Link is up at 100 Mbps, full duplex.
[4295284.324000] b44: eth0: Flow control is off for TX and off for RX.
[4295292.101000] eth0: no IPv6 routers present
[4295294.324000] NETDEV WATCHDOG: eth0: transmit timed out
[4295294.324000] b44: eth0: transmit timed out, resetting
[4295294.325000] b44: eth0: Link is down.
[4295297.325000] b44: eth0: Link is up at 100 Mbps, full duplex.
[4295297.325000] b44: eth0: Flow control is off for TX and off for RX.
[4295338.629000] ppdev: user-space parallel port driver
[4295338.638000] ppdev0: claim the port first
[4295338.647000] ppdev1: claim the port first
[4295338.655000] ppdev2: claim the port first
[4295485.305000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4295485.305000] apm: disabled on user request.
[4295487.113000] [drm] Initialized drm 1.0.0 20040925
[4295487.137000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4295487.141000] [drm] Initialized i915 1.2.0 20040405 on minor 0: Intel Corporation 82852/855GM Integrated Graphics Device
[4295487.144000] [drm] Initialized i915 1.2.0 20040405 on minor 1: Intel Corporation 82852/855GM Integrated Graphics Device (#2)
[4295487.145000] mtrr: base(0xe8020000) is not aligned on a size(0x600000) boundary
[4295507.118000] kjournald starting.  Commit interval 5 seconds
[4295507.119000] EXT3 FS on sda1, internal journal
[4295507.119000] EXT3-fs: mounted filesystem with ordered data mode.
[4295514.844000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295514.844000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295514.994000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295514.994000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296436.697000] Warning: /proc/ide/hd?/settings interface is obsolete, and will be removed soon!
[4296496.635000] cdrom: This disc doesn't have any tracks I recognize!
[4296650.518000] cdrom: This disc doesn't have any tracks I recognize!
[4296706.570000] kjournald starting.  Commit interval 5 seconds
[4296706.571000] EXT3 FS on sda1, internal journal
[4296706.571000] EXT3-fs: mounted filesystem with ordered data mode.
[4297039.079000] ibm_acpi: ec object not found
[4297051.361000] cdrom: open failed.
[4298724.205000] cdrom: open failed.
[4298724.244000] cdrom: open failed.
[4300340.768000] kjournald starting.  Commit interval 5 seconds
[4300340.768000] EXT3 FS on sda1, internal journal
[4300340.768000] EXT3-fs: mounted filesystem with ordered data mode.

---

### Post by Kethinov on 2006-04-28
Try running the command as root instead. **sudo gedit /etc/fstab**. It will ask for your password.

---

### Post by ZelasMetallium on 2006-04-28
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0

---

### Post by Kethinov on 2006-04-28
Try modifying the last line such that reads **/dev/sda1 /media/usb0 ntfs user,ro,umask=000 0 0**. Save the file. Then from the terminal run **cd /media** then **mount usb0** and tell me what happens.

---

### Post by duality on 2006-04-28
if you got dapper:
    [http://easylinux.info/wiki/Ubuntu_dapper](http://easylinux.info/wiki/Ubuntu_dapper)

if you got breezy:
   [http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu)


These age guides to how to do stuff on ubuntu,, gl

---

### Post by ZelasMetallium on 2006-04-28
[QUOTE=Kethinov]Try modifying the last line such that reads **/dev/sda1 /media/usb0 ntfs user,ro,umask=000 0 0**. Save the file. Then from the terminal run **cd /media** then **mount usb0** and tell me what happens.[/QUOTE]

This is what it said:

kendra@kendra:~$ cd /media
kendra@kendra:/media$ mount usb
mount: /dev/sda1 already mounted or /media/usb0 busy
mount: according to mtab, /dev/sda1 is mounted on /media/usbdisk
kendra@kendra:/media$

---

### Post by Kethinov on 2006-04-28
Run **ls /media/usbdisk**

---

### Post by ZelasMetallium on 2006-04-28
bin    debootstrap  home        lib         mnt   root  sys  var
boot   dev          initrd      lost+found  opt   sbin  tmp  vmlinuz
cdrom  etc          initrd.img  media       proc  srv   usr
kendra@kendra:~$

---

