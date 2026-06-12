---
title: "USB Hub Issues .... Aaaaargh"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by mickotoole on 2006-12-06
Hey all, 

I'm in dire straits here ... the sys admin at work decided to head away for 3 months and my boss decided to leave all the sys admin to me even though I'm only barely capable! 

I've spent about 3 days researching this issue. I've searched through ubuntuforums.org and gone through Google and I decided to post here as a last resort ... OK enough of the background here's what's going on ...

The company I'm with sends SMS messages through GSM modems connected to a Linux server via a Serial to USB cable. There are (should I say were!!!) 2 7 port Belkin hubs attached to the 2 USB ports on the server and in turn there were 7 Serial to USB modems plugged into these hubs... I hope you're still with me!

The server used to pick up the hubs and assign an address to them and then proceed to assign addresses to each modem that it found attached to the hub.

One of the hubs decided to go belly up a few days ago so I thought that I could buy a new 7 port hub (not Belkin) and hook the modems up to it and plug it in (much the same way as it was before)

The problem now is that after I rebooted the server it still only picks up 1 hub but instead of assigning addresses to the modems attached to it it just assigns ttyUSB0 to the hub.

When I check dmesg I get ```
usbserial.c: Magic Control Technology USB-RS232 converter now attached to ttyUSB0 (or usb/tts/0 for devfs)
```

I'm really really starting to give up on this altogether ... I've attached the demsg to the bottom of this post ... please please help if you can and also let me know if this post is not clear so I can clarify it.

Thanks in advance

Mick

dmesg output:

```
[42949377.950000] Brought up 1 CPUs
[42949377.950000] NET: Registered protocol family 16
[42949377.950000] EISA bus registered
[42949377.950000] ACPI: bus type pci registered
[42949377.950000] PCI: PCI BIOS revision 2.10 entry at 0xfdb31, last bus=2
[42949377.950000] PCI: Using configuration type 1
[42949377.950000] ACPI: Subsystem revision 20051216
[42949377.950000] ACPI: Interpreter enabled
[42949377.950000] ACPI: Using IOAPIC for interrupt routing
[42949377.950000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[42949377.950000] PCI: Probing PCI hardware (bus 00)
[42949377.950000] Uncovering SIS963 that hid as a SIS503 (compatible=0)
[42949377.950000] Enabling SiS 96x SMBus.
[42949377.950000] Boot video device is 0000:01:00.0
[42949377.950000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[42949377.960000] ACPI: Power Resource [URP1] (off)
[42949377.960000] ACPI: Power Resource [URP2] (off)
[42949377.960000] ACPI: Power Resource [FDDP] (off)
[42949377.960000] ACPI: Power Resource [LPTP] (off)
[42949377.960000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 1                                              5)
[42949377.960000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 *6 7 10 11 12 14 1                                              5)
[42949377.960000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 12 14 1                                              5)
[42949377.960000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 *4 5 6 7 10 11 12 14 1                                              5)
[42949377.960000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 *7 10 11 12 14 1                                              5)
[42949377.960000] ACPI: PCI Interrupt Link [LNKF] (IRQs *3 4 5 6 7 10 11 12 14 1                                              5)
[42949377.960000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15                                              ) *0, disabled.
[42949377.960000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 1                                              5)
[42949377.960000] Linux Plug and Play Support v0.97 (c) Adam Belay
[42949377.960000] pnp: PnP ACPI init
[42949377.970000] pnp: PnP ACPI: found 8 devices
[42949377.970000] PnPBIOS: Disabled by ACPI PNP
[42949377.970000] PCI: Using ACPI for IRQ routing
[42949377.970000] PCI: If a device doesn't work, try "pci=routeirq".  If it help                                              s, post a report
[42949377.970000] PCI: Ignore bogus resource 6 [0:0] of 0000:01:00.0
[42949377.970000] PCI: Bridge: 0000:00:01.0
[42949377.970000]   IO window: 9000-9fff
[42949377.970000]   MEM window: cfd00000-cfefffff
[42949377.970000]   PREFETCH window: bfa00000-cfbfffff
[42949377.970000] audit: initializing netlink socket (disabled)
[42949377.970000] audit(1165425972.960:1): initialized
[42949377.970000] VFS: Disk quotas dquot_6.5.1
[42949377.970000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[42949377.970000] Initializing Cryptographic API
[42949377.970000] io scheduler noop registered
[42949377.970000] io scheduler anticipatory registered
[42949377.970000] io scheduler deadline registered
[42949377.970000] io scheduler cfq registered
[42949377.970000] isapnp: Scanning for PnP cards...
[42949378.330000] isapnp: No Plug & Play device found
[42949378.340000] Real Time Clock Driver v1.12
[42949378.340000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64                                               irq 1,12
[42949378.340000] Failed to disable AUX port, but continuing anyway... Is this a                                               SiS?
[42949378.340000] If AUX port is really absent please use the 'i8042.noaux' opti                                              on.
[42949378.350000] serio: i8042 AUX port at 0x60,0x64 irq 12
[42949378.350000] serio: i8042 KBD port at 0x60,0x64 irq 1
[42949378.350000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ shar                                              ing enabled
[42949378.350000] ACPI: PCI Interrupt 0000:00:02.6[C] -> GSI 18 (level, low) ->                                               IRQ 169
[42949378.350000] ACPI: PCI interrupt for device 0000:00:02.6 disabled
[42949378.350000] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) ->                                               IRQ 177
[42949378.380000] 0000:00:09.0: ttyS4 at I/O 0xc800 (irq = 177) is a ST16650V2
[42949378.380000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 b                                              locksize
[42949378.380000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[42949378.380000] ide: Assuming 33MHz system bus speed for PIO modes; override w                                              ith idebus=xx
[42949378.380000] mice: PS/2 mouse device common for all mice
[42949378.390000] EISA: Probing bus 0 at eisa.0
[42949378.390000] EISA: Detected 0 cards.
[42949378.390000] NET: Registered protocol family 2
[42949378.410000] input: AT Translated Set 2 keyboard as /class/input/input0
[42949378.500000] IP route cache hash table entries: 1024 (order: 0, 4096 bytes)
[42949378.500000] TCP established hash table entries: 4096 (order: 3, 32768 byte                                              s)
[42949378.500000] TCP bind hash table entries: 4096 (order: 3, 32768 bytes)
[42949378.500000] TCP: Hash tables configured (established 4096 bind 4096)
[42949378.500000] TCP reno registered
[42949378.500000] TCP bic registered
[42949378.500000] NET: Registered protocol family 1
[42949378.500000] NET: Registered protocol family 8
[42949378.500000] NET: Registered protocol family 20
[42949378.500000] Using IPI No-Shortcut mode
[42949378.500000] ACPI wakeup devices:
[42949378.500000] PCI0 PS2M PS2K USB1 USB2 EHCI  LAN  MDM  AUD
[42949378.500000] ACPI: (supports S0 S1 S4 S5)
[42949378.500000] Freeing unused kernel memory: 332k freed
[42949378.540000] vga16fb: initializing
[42949378.540000] vga16fb: mapped to 0xc00a0000
[42949378.630000] Console: switching to colour frame buffer device 80x25
[42949378.630000] fb0: VGA16 VGA frame buffer device
[42949378.640000] Capability LSM initialized
[42949379.340000] SIS5513: IDE controller at PCI slot 0000:00:02.5
[42949379.340000] SIS5513: chipset revision 0
[42949379.340000] SIS5513: not 100% native mode: will probe irqs later
[42949379.340000] SIS5513: SiS 962/963 MuTIOL IDE UDMA133 controller
[42949379.340000]     ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:DMA, hdb                                              :DMA
[42949379.340000]     ide1: BM-DMA at 0xff08-0xff0f, BIOS settings: hdc:DMA, hdd                                              :DMA
[42949379.340000] Probing IDE interface ide0...
[42949379.650000] hda: Maxtor 2B020H1, ATA DISK drive
[42949380.370000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[42949380.380000] Probing IDE interface ide1...
[42949381.160000] hdc: CD-ROM 52X L, ATAPI CD/DVD-ROM drive
[42949381.880000] ide1 at 0x170-0x177,0x376 on irq 15
[42949381.890000] hda: max request size: 128KiB
[42949381.890000] hda: 40020624 sectors (20490 MB) w/2048KiB Cache, CHS=39703/16                                              /63, UDMA(100)
[42949381.890000] hda: cache flushes not supported
[42949381.890000]  hda: hda1 hda2 < hda5 >
[42949381.930000] hdc: ATAPI 52X CD-ROM drive, 128kB Cache, UDMA(33)
[42949381.930000] Uniform CD-ROM driver Revision: 3.20
[42949382.220000] usbcore: registered new driver usbfs
[42949382.220000] usbcore: registered new driver hub
[42949382.220000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI)                                               Driver (PCI)
[42949382.220000] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) ->                                               IRQ 185
[42949382.220000] ohci_hcd 0000:00:03.0: OHCI Host Controller
[42949382.240000] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus nu                                              mber 1
[42949382.240000] ohci_hcd 0000:00:03.0: irq 185, io mem 0xcfff9000
[42949382.300000] hub 1-0:1.0: USB hub found
[42949382.300000] hub 1-0:1.0: 3 ports detected
[42949382.410000] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) ->                                               IRQ 193
[42949382.410000] ohci_hcd 0000:00:03.1: OHCI Host Controller
[42949382.440000] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus nu                                              mber 2
[42949382.440000] ohci_hcd 0000:00:03.1: irq 193, io mem 0xcfffa000
[42949382.500000] hub 2-0:1.0: USB hub found
[42949382.500000] hub 2-0:1.0: 3 ports detected
[42949382.610000] ACPI: PCI Interrupt 0000:00:03.2[D] -> GSI 23 (level, low) ->                                               IRQ 201
[42949382.610000] ehci_hcd 0000:00:03.2: EHCI Host Controller
[42949382.610000] PCI: cache line size of 64 is not supported by device 0000:00:                                              03.2
[42949382.610000] ehci_hcd 0000:00:03.2: new USB bus registered, assigned bus nu                                              mber 3
[42949382.610000] ehci_hcd 0000:00:03.2: irq 201, io mem 0xcfffb000
[42949382.610000] ehci_hcd 0000:00:03.2: USB 2.0 started, EHCI 1.00, driver 10 D                                              ec 2004
[42949382.610000] hub 3-0:1.0: USB hub found
[42949382.610000] hub 3-0:1.0: 6 ports detected
[42949382.790000] Attempting manual resume
[42949382.840000] kjournald starting.  Commit interval 5 seconds
[42949382.840000] EXT3-fs: mounted filesystem with ordered data mode.
[42949383.090000] usb 3-2: new high speed USB device using ehci_hcd and address                                               2
[42949383.240000] hub 3-2:1.0: USB hub found
[42949383.240000] hub 3-2:1.0: 7 ports detected
[42949387.330000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[42949387.400000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[42949387.470000] Linux agpgart interface v0.101 (c) Dave Jones
[42949387.490000] agpgart: Detected SiS 741 chipset
[42949387.490000] agpgart: AGP aperture is 64M @ 0xd0000000
[42949387.510000] sis900.c: v1.08.09 Sep. 19 2005
[42949387.510000] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) ->                                               IRQ 209
[42949387.510000] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address                                               1.
[42949387.520000] 0000:00:04.0: Using transceiver found at address 1 as default
[42949387.520000] eth0: SiS 900 PCI Fast Ethernet at 0xcc00, IRQ 209, 00:0b:6a:4                                              d:a2:d6.
[42949387.520000] i2c-sis96x version 1.0.0
[42949387.520000] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x0c00
[42949387.630000] input: PC Speaker as /class/input/input1
[42949388.030000] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) ->                                               IRQ 169
[42949388.230000] input: ImPS/2 Generic Wheel Mouse as /class/input/input2
[42949388.270000] ts: Compaq touchscreen protocol output
[42949388.860000] intel8x0_measure_ac97_clock: measured 59273 usecs
[42949388.860000] intel8x0: clocking to 48000
[42949389.690000] NET: Registered protocol family 17
[42949389.690000] lp: driver loaded but no devices found
[42949389.750000] usbcore: registered new driver usbserial
[42949389.750000] drivers/usb/serial/usb-serial.c: USB Serial support registered                                               for generic
[42949389.750000] usbcore: registered new driver usbserial_generic
[42949389.750000] drivers/usb/serial/usb-serial.c: USB Serial Driver core
[42949389.750000] drivers/usb/serial/usb-serial.c: USB Serial support registered                                               for pl2303
[42949389.750000] usbcore: registered new driver pl2303
[42949389.750000] drivers/usb/serial/pl2303.c: Prolific PL2303 USB to serial ada                                              ptor driver
[42949389.760000] drivers/usb/serial/usb-serial.c: USB Serial support registered                                               for MCT U232
[42949389.760000] usbcore: registered new driver mct_u232
[42949389.760000] drivers/usb/serial/mct_u232.c: Magic Control Technology USB-RS                                              232 converter driver z2.0
[42949389.910000] Adding 273064k swap on /dev/hda5.  Priority:-1 extents:1 acros                                              s:273064k
[42949390.010000] EXT3 FS on hda1, internal journal
[42949390.400000] eth0: Media Link On 100mbps full-duplex
[42949390.400000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[42949390.400000] md: bitmap version 4.39
[42949390.900000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@                                              redhat.com
[42949393.720000] cdrom: open failed.
[42949394.090000] NET: Registered protocol family 10
[42949394.090000] lo: Disabled Privacy Extensions
[42949394.090000] IPv6 over IPv4 tunneling driver
[42949404.530000] eth0: no IPv6 routers present
[42949757.480000] usb 3-2: USB disconnect, address 2
[42949757.760000] usb 3-2: new high speed USB device using ehci_hcd and address                                               3
[42949757.910000] hub 3-2:1.0: USB hub found
[42949757.910000] hub 3-2:1.0: 7 ports detected
[42949759.730000] usb 3-2: USB disconnect, address 3

```

---

