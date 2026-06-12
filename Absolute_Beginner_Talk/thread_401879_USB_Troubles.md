---
title: "USB Troubles"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by Mike_SMD on 2007-04-05
Hey everybody...

A few weeks ago all of my usb devices stopped working, doesn't seem to matter what I plug in to the ports... just nothing happens. Normally I have two things on the go, a USB webcam and a cable for hooking up my digital camera.

Trying to access the camera via Camorama gives me an error message stating that there is no camera connected to the system.

Plugging in my digital camera seems to do nothing where as before it would mount up for me and I could access the pictures.

Now, I peeked arounf the forums and looked into other *related* usb problems, many things similar but nothing quite the same.

Forgive the size, but here's the output from typing dmesg in terminal after turning the digital camera on and off a couple of times. After that I've posted the output from typing in sudo fdisk -l and lsusb...

I'm no guru.
It looks to me like Linux is recognizing that the components have been hooked up but I can't figure out why they aren't automounting or being recognized by other programs (ie: Camorama).

I already went to System->Preferences->Removable Drives and Media and made sure that the appropriate settings were enabled in that menu. They were, I reselected them just in case... still no dice.

Anybody have any ideas as to what I can try next?
All help is thankfully appreciated!


Mike.

--------------------------

mike@mike-desktop:~$ dmesg
[17179569.184000] Linux version 2.6.17-11-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Thu Feb 1 19:52:28 UTC 2007 (Ubuntu 2.6.17-11.35-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000ec000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001bff0000 (usable)
[17179569.184000]  BIOS-e820: 000000001bff0000 - 000000001bff8000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000001bff8000 - 000000001c000000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 447MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 114672
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 110576 pages, LIFO batch:31
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 AMI                                   ) @ 0x000fabf0
[17179569.184000] ACPI: RSDT (v001 AMIINT VIA_K7   0x00000010 MSFT 0x00000097) @ 0x1bff0000
[17179569.184000] ACPI: FADT (v001 AMIINT VIA_K7   0x00000011 MSFT 0x00000097) @ 0x1bff0030
[17179569.184000] ACPI: DSDT (v001    VIA   VT8371 0x00001000 MSFT 0x0100000b) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x808
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 1c000000:e3ff0000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash rootflags=data=writeback
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (0138b000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[17179569.184000] Detected 1102.704 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179572.848000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179572.848000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179572.880000] Memory: 445024k/458688k available (1911k kernel code, 13104k reserved, 1073k data, 308k init, 0k highmem)
[17179572.880000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179572.960000] Calibrating delay using timer specific routine.. 2207.65 BogoMIPS (lpj=4415312)
[17179572.960000] Security Framework v1.0.0 initialized
[17179572.960000] SELinux:  Disabled at boot.
[17179572.960000] Mount-cache hash table entries: 512
[17179572.960000] CPU: After generic identify, caps: 0183f9ff c1c7f9ff 00000000 00000000 00000000 00000000 00000000
[17179572.960000] CPU: After vendor identify, caps: 0183f9ff c1c7f9ff 00000000 00000000 00000000 00000000 00000000
[17179572.960000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179572.960000] CPU: L2 Cache: 256K (64 bytes/line)
[17179572.960000] CPU: After all inits, caps: 0183f9ff c1c7f9ff 00000000 00000420 00000000 00000000 00000000
[17179572.960000] Checking 'hlt' instruction... OK.
[17179572.976000] SMP alternatives: switching to UP code
[17179572.976000] Freeing SMP alternatives: 16k freed
[17179572.976000] checking if image is initramfs... it is
[17179573.856000] Freeing initrd memory: 5327k freed
[17179573.856000] ACPI: Core revision 20060707
[17179573.864000] ACPI: Looking for DSDT ... not found!
[17179573.868000] ACPI: setting ELCR to 0200 (from 0e00)
[17179573.868000] CPU0: AMD Athlon(tm) Processor stepping 04
[17179573.868000] SMP motherboard not detected.
[17179573.868000] Local APIC not detected. Using dummy APIC emulation.
[17179573.868000] Brought up 1 CPUs
[17179573.868000] migration_cost=0
[17179573.868000] NET: Registered protocol family 16
[17179573.868000] EISA bus registered
[17179573.868000] ACPI: bus type pci registered
[17179573.884000] PCI: PCI BIOS revision 2.10 entry at 0xfdb61, last bus=1
[17179573.884000] PCI: Using configuration type 1
[17179573.884000] Setting up standard PCI resources
[17179573.908000] ACPI: Interpreter enabled
[17179573.908000] ACPI: Using PIC for interrupt routing
[17179573.908000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179573.908000] PCI: Probing PCI hardware (bus 00)
[17179573.908000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:07.1
[17179573.908000] PCI quirk: region 0800-08ff claimed by vt82c586 ACPI
[17179573.908000] PCI quirk: region 0c00-0c7f claimed by vt82c686 HW-mon
[17179573.908000] PCI quirk: region 0400-040f claimed by vt82c686 SMB
[17179573.908000] Boot video device is 0000:01:00.0
[17179573.908000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179573.912000] ACPI: Power Resource [URP1] (off)
[17179573.912000] ACPI: Power Resource [URP2] (off)
[17179573.912000] ACPI: Power Resource [FDDP] (off)
[17179573.912000] ACPI: Power Resource [LPTP] (off)
[17179573.916000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[17179573.916000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179573.916000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[17179573.916000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[17179573.916000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179573.916000] pnp: PnP ACPI init
[17179573.920000] pnp: PnP ACPI: found 11 devices
[17179573.920000] PnPBIOS: Disabled by ACPI PNP
[17179573.920000] PCI: Using ACPI for IRQ routing
[17179573.920000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179573.932000] PCI: Bridge: 0000:00:01.0
[17179573.932000]   IO window: 9000-afff
[17179573.932000]   MEM window: dfe00000-dfefffff
[17179573.932000]   PREFETCH window: bfc00000-dfcfffff
[17179573.932000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179573.932000] NET: Registered protocol family 2
[17179573.968000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179573.968000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[17179573.968000] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[17179573.968000] TCP: Hash tables configured (established 16384 bind 8192)
[17179573.968000] TCP reno registered
[17179573.968000] audit: initializing netlink socket (disabled)
[17179573.968000] audit(1175758570.968:1): initialized
[17179573.968000] VFS: Disk quotas dquot_6.5.1
[17179573.968000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179573.968000] Initializing Cryptographic API
[17179573.968000] io scheduler noop registered
[17179573.968000] io scheduler anticipatory registered
[17179573.968000] io scheduler deadline registered
[17179573.968000] io scheduler cfq registered (default)
[17179573.968000] PCI: Disabling Via external APIC routing
[17179573.968000] isapnp: Scanning for PnP cards...
[17179574.324000] isapnp: No Plug & Play device found
[17179574.364000] Real Time Clock Driver v1.12ac
[17179574.364000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179574.364000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179574.364000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179574.368000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179574.368000] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179574.368000] mice: PS/2 mouse device common for all mice
[17179574.368000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179574.368000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179574.368000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179574.368000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[17179574.372000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179574.372000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179574.372000] EISA: Probing bus 0 at eisa.0
[17179574.372000] EISA: Detected 0 cards.
[17179574.372000] TCP bic registered
[17179574.372000] NET: Registered protocol family 1
[17179574.372000] NET: Registered protocol family 8
[17179574.372000] NET: Registered protocol family 20
[17179574.372000] Using IPI No-Shortcut mode
[17179574.372000] ACPI: (supports S0 S1 S4 S5)
[17179574.372000] Freeing unused kernel memory: 308k freed
[17179574.392000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179575.576000] Capability LSM initialized
[17179575.644000] ACPI: Thermal Zone [THRM] (30 C)
[17179576.496000] VP_IDE: IDE controller at PCI slot 0000:00:07.1
[17179576.496000] PCI: Via IRQ fixup for 0000:00:07.1, from 255 to 0
[17179576.496000] VP_IDE: chipset revision 16
[17179576.496000] VP_IDE: not 100% native mode: will probe irqs later
[17179576.496000] VP_IDE: VIA vt82c686a (rev 22) IDE UDMA66 controller on pci0000:00:07.1
[17179576.500000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:DMA
[17179576.500000]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:DMA
[17179576.500000] Probing IDE interface ide0...
[17179576.916000] hda: WDC WD400EB-32CPF0, ATA DISK drive
[17179577.364000] hdb: ASUS CD-S500/A, ATAPI CD/DVD-ROM drive
[17179577.420000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179577.432000] Probing IDE interface ide1...
[17179577.848000] hdc: WDC WD84AA, ATA DISK drive
[17179578.632000] hdd: LITE-ON LTR-24102B, ATAPI CD/DVD-ROM drive
[17179578.688000] ide1 at 0x170-0x177,0x376 on irq 15
[17179578.720000] hda: max request size: 128KiB
[17179578.748000] hda: 78165360 sectors (40020 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(66)
[17179578.748000] hda: cache flushes not supported
[17179578.748000]  hda: hda1 hda2 < hda5 >
[17179578.788000] hdc: max request size: 128KiB
[17179578.788000] hdb: ATAPI 50X CD-ROM drive, 128kB Cache, UDMA(33)
[17179578.788000] Uniform CD-ROM driver Revision: 3.20
[17179578.788000] hdc: 16514064 sectors (8455 MB) w/2048KiB Cache, CHS=16383/16/63, UDMA(66)
[17179578.792000] hdc: cache flushes not supported
[17179578.792000]  hdc: hdc1
[17179578.828000] hdd: ATAPI 40X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179579.196000] usbcore: registered new driver usbfs
[17179579.196000] usbcore: registered new driver hub
[17179579.200000] USB Universal Host Controller Interface driver v3.0
[17179579.200000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
[17179579.200000] PCI: setting IRQ 10 as level-triggered
[17179579.200000] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[17179579.200000] uhci_hcd 0000:00:07.2: UHCI Host Controller
[17179579.200000] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[17179579.200000] uhci_hcd 0000:00:07.2: irq 10, io base 0x0000d800
[17179579.204000] usb usb1: configuration #1 chosen from 1 choice
[17179579.204000] hub 1-0:1.0: USB hub found
[17179579.204000] hub 1-0:1.0: 2 ports detected
[17179579.308000] ACPI: PCI Interrupt 0000:00:07.3[D] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[17179579.308000] uhci_hcd 0000:00:07.3: UHCI Host Controller
[17179579.308000] uhci_hcd 0000:00:07.3: new USB bus registered, assigned bus number 2
[17179579.308000] uhci_hcd 0000:00:07.3: irq 10, io base 0x0000dc00
[17179579.308000] usb usb2: configuration #1 chosen from 1 choice
[17179579.308000] hub 2-0:1.0: USB hub found
[17179579.308000] hub 2-0:1.0: 2 ports detected
[17179579.504000] Attempting manual resume
[17179579.560000] kjournald starting.  Commit interval 5 seconds
[17179579.560000] EXT3-fs: mounted filesystem with writeback data mode.
[17179595.776000] parport_pc: VIA 686A/8231 detected
[17179595.776000] parport_pc: probing current configuration
[17179595.776000] parport_pc: Current parallel port base: 0x378
[17179595.776000] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[17179595.872000] parport_pc: VIA parallel port: io=0x378, irq=7
[17179595.892000] Linux agpgart interface v0.101 (c) Dave Jones
[17179595.916000] agpgart: Detected VIA Twister-K/KT133x/KM133 chipset
[17179595.924000] agpgart: AGP aperture is 64M @ 0xe0000000
[17179596.376000] ne2k-pci.c:v1.03 9/22/2003 D. Becker/P. Gortmaker
[17179596.376000]   [http://www.scyld.com/network/ne2k-pci.html](http://www.scyld.com/network/ne2k-pci.html)
[17179596.376000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[17179596.376000] PCI: setting IRQ 11 as level-triggered
[17179596.376000] ACPI: PCI Interrupt 0000:00:0c.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179596.376000] eth0: RealTek RTL-8029 found at 0xd400, IRQ 11, 00:60:67:65:C9:E6.
[17179596.684000] input: PC Speaker as /class/input/input1
[17179597.240000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179597.328000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179597.716000] Floppy drive(s): fd0 is 1.44M
[17179597.736000] FDC 0 is a post-1991 82077
[17179597.956000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 9
[17179597.956000] PCI: setting IRQ 9 as level-triggered
[17179597.956000] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LNKC] -> GSI 9 (level, low) -> IRQ 9
[17179598.156000] input: ImPS/2 Logitech Wheel Mouse as /class/input/input2
[17179598.192000] ts: Compaq touchscreen protocol output
[17179598.776000] NET: Registered protocol family 17
[17179599.120000] lp0: using parport0 (interrupt-driven).
[17179599.184000] Adding 1317288k swap on /dev/disk/by-uuid/9c689857-bb3b-46e9-96b3-0dcbace0c006.  Priority:-1 extents:1 across:1317288k
[17179599.288000] EXT3 FS on hda1, internal journal
[17179602.260000] NET: Registered protocol family 10
[17179602.260000] lo: Disabled Privacy Extensions
[17179602.260000] IPv6 over IPv4 tunneling driver
[17179606.416000] ACPI: Power Button (FF) [PWRF]
[17179606.416000] ACPI: Power Button (CM) [PWRB]
[17179606.416000] ACPI: Sleep Button (CM) [SLPB]
[17179606.608000] ibm_acpi: ec object not found
[17179606.664000] pcc_acpi: loading...
[17179607.228000] powernow: No powernow capabilities detected
[17179608.996000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179608.996000] apm: overridden by ACPI.
[17179609.932000] [drm] Initialized drm 1.0.1 20051102
[17179610.028000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179610.032000] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[17179611.148000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17179611.148000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[17179611.148000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[17179611.652000] [drm] Setting GART location based on new memory map
[17179611.652000] [drm] Loading R300 Microcode
[17179611.652000] [drm] writeback test succeeded in 1 usecs
[17179613.240000] eth0: no IPv6 routers present
[17179617.716000] ip_tables: (C) 2000-2006 Netfilter Core Team
[17179617.844000] Netfilter messages via NETLINK v0.30.
[17179617.856000] ip_conntrack version 2.4 (3583 buckets, 28664 max) - 224 bytes per conntrack
[17179681.864000] usb 1-2: new full speed USB device using uhci_hcd and address 2
[17179682.052000] usb 1-2: configuration #1 chosen from 1 choice
[17179682.396000] usbcore: registered new driver snd-usb-audio
[17179972.420000] usb 1-1: new full speed USB device using uhci_hcd and address 3
[17179972.588000] usb 1-1: configuration #1 chosen from 2 choices
[17180876.608000] usb 1-1: USB disconnect, address 3
[17181053.500000] usb 1-1: new full speed USB device using uhci_hcd and address 4
[17181053.668000] usb 1-1: configuration #1 chosen from 2 choices
[17181646.720000] usb 1-1: USB disconnect, address 4
[17181704.164000] usb 1-1: new full speed USB device using uhci_hcd and address 5
[17181704.332000] usb 1-1: configuration #1 chosen from 2 choices
[17181720.808000] usb 1-1: USB disconnect, address 5
[17182336.180000] usb 1-1: new full speed USB device using uhci_hcd and address 6
[17182336.348000] usb 1-1: configuration #1 chosen from 2 choices


--------------------------

mike@mike-desktop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4701    37760751   83  Linux
/dev/hda2            4702        4865     1317330    5  Extended
/dev/hda5            4702        4865     1317298+  82  Linux swap / Solaris

Disk /dev/hdc: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1        1027     8249346   83  Linux

---------------------------

mike@mike-desktop:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 054c:0010 Sony Corp. DSC-S30/S70/S75/F505V/F505/FD92 Cybershot/Mavica Digital Camera
Bus 001 Device 002: ID 046d:08d7 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  
mike@mike-desktop:~$

---

### Post by PurplePenguin on 2007-04-05
You're not alone.  I've got a feeling that it must have been a kernel update (or some other kind of update) that did this.  It's just not that important to me, so I haven't paid attention to it, but I wouldn't mind figuring out how to fix it! :)

---

### Post by Mike_SMD on 2007-04-05
Ha!
Yeah... I'm with you on fixing it.

Funny how the priority of a problem directly depends upon the level of your own personal need in relation to it. This whole 'lost usb' thing, *I* could probably wait until the new release and then just see if it's been fixed without any further tinkering...

... but my partner is going positively bonkers at the thought of a whole weekend without being able to upload any pictures. 

Absolute CRISIS!

Weird thing though, and I do hope somebody else out there has some insight as to what to do next.

Take care,

Mike.

---

### Post by emilih on 2007-04-06
With Synaptic search libgphoto2-2 and  force instal back version 
idem with libgphoto2-2-.dev

Salutacions

---

### Post by Mike_SMD on 2007-04-06
Hi emilih!

Well, I downgraded both of those libraries like you suggested, then restarted the system but still nothing. Sadly, It didn't seem to fix the problem... like before everything shows up but just doesn't work.

Anybody else want to take a crack at this...?

I reached the edge of my technical limitations pretty early with this problem, I'm all ears and humbly thankful of any help I can get!

Mike.

---

### Post by dkaddict on 2007-04-18
I had similar problems to the ones above which I resolved by editng '/boot/grub/menu.lst' and adding 'noapic' to the end of the kernel line so >>

open gedit or kate for Kubuntu

enter>>

'sudo gedit /boot/grub/menu.lst'

when gedit opens the file, scroll down to the 'end default options' line and enter 'noapic'  at the end of the line below it which begins with 'kernel' so it looks like>>>

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=77f9d071-f5ae-49d9-b480-60a41e1eca7b ro quiet splash noapic
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=77f9d071-f5ae-49d9-b480-60a41e1eca7b ro single noapic
initrd		/boot/initrd.img-2.6.20-15-generic

It got all of my USB devices working but adding 'noapic' means that I can't get USB devices and a wireless connection to work at the same time. IE, if I turn on my internal wireless card with 'alt+f2' I cannot connect to a wirelss router until I reboot. When I reboot, none of my USB devices work again because the 'noapic' option has been removed.

Hope this helps a little. I am really new to Linux too so I would verify my suggestions first. If anyone reading this knows how to overcome the 'noapic' and USB problem I have I would be grateful.

dkaddict

Just found a way of getting USB and Wireless to run at the same time. I dunno if this will help you but here's what I did.

Instead of adding 'noapic' to the end of the line beggining with 'kernel' in /boot/grub/menu.lst, I added 'irqpoll' and now have everything working.

The relevant change looks like

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=77f9d071-f5ae-49d9-b480-60a41e1eca7b ro quiet splash irqpoll
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=77f9d071-f5ae-49d9-b480-60a41e1eca7b ro single irqpoll
initrd		/boot/initrd.img-2.6.20-15-generic

Well happy about getting that sorted.

Hope you have luck

---

### Post by vicks on 2007-04-22
I have the exact same problem as the original poster here. And it started just the same, in the middle of feisty development. 

I can't even do lsusb, or enter the usvb module of kde hardware-info. 

So...bump. Have you guys got it sorted? I haven't. So if anyone knows whats up, please post!

---

