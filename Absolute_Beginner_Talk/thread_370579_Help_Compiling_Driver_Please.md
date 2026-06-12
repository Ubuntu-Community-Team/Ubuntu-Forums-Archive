---
title: "Help Compiling Driver Please"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by brandoncolorado on 2007-02-25
Hello,

I would like to install the linux driver for my wireless card.  I am a confused by the instructions.  I am attaching them as .txt (the Readme).

This part:

	(1)Build up the driver from the source code
         	./makedrv

    	(2)Load the driver module to kernel and start up nic
    		./wlan0up
           (if "insmod: error inserting 'r8180.ko': -File exists." met,
	        ./wlan0rmv
		./wlan0down
		./wlan0up
	    should be OK.
	   )
	(3)Refer to < Set wireless lan MIBs > to set Wireless LAN specific parameters.

Do I have to log in/log out of networks in terminal, or can I let network-manager run this?

Also, can you help me make these instructions more clear for just installing the driver?

Thanks a lot.

---

### Post by jamesstansell on 2007-02-26
Hi Brandon,

Yes, those commands are meant to be typed into a terminal.  They appear to assume a high degree of expertise.

I'm not familiar with that driver so there's no specific suggestions I can give you.  Hopefully someone else can chime in.

You've perhaps already seen the documentation, starting here?
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/connect-to-internet.html#wireless](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/connect-to-internet.html#wireless)

I searched briefly in the forums for RTL8185 and found this thread, but didn't notice any quick answers: [http://ubuntuforums.org/showpost.php?p=2060647&postcount=23](http://ubuntuforums.org/showpost.php?p=2060647&postcount=23)

It would be helpful for you to say which wireless card you have, which Ubuntu version, and how you were directed to the RTL8185 driver.

Keep asking questions!

-james.

---

### Post by brandoncolorado on 2007-02-26
Hey, thanks for the response.

I use the RTL8185 on a Gateway MX3414 running Ubuntu 6.10.  I ran across the sourceforge site for the 8185 driver by using google.  I just don't know if I should risk installing it without knowing what I am doing, or if it works with this particular model.

---

### Post by brandoncolorado on 2007-02-27
Can someone please help me walk through this wireless driver compiling?  I don't understand a few things:

1) What level do I have to be at when running these commands in terminal?

2) Do I have to manually set up the wireless settings after installing driver, or can network-manager handle it?  I mean, do I have to use terminal to set network settings?

---

### Post by brandoncolorado on 2007-02-28
bump

---

### Post by Bachstelze on 2007-02-28
I'm at school right now but please provide a link to the file and I'll see if I can help you whel lI'll be back home :)

---

### Post by brandoncolorado on 2007-02-28
> **HymnToLife said:**
> I'm at school right now but please provide a link to the file and I'll see if I can help you whel lI'll be back home :)

Hi, Thanks,

The readme.txt is posted on the original post.

---

### Post by Bachstelze on 2007-02-28
I meant the whole archive with the driver you want to compile, not just the readme ;)

---

### Post by brandoncolorado on 2007-02-28
> **HymnToLife said:**
> I meant the whole archive with the driver you want to compile, not just the readme ;)

HA!, sorry.  Here it is.

---

### Post by Bachstelze on 2007-02-28
It's very easy. Just open a terminal, cd to the dir where you saved the tarball then extract it :

```
tar xzvf rtl8185_linux_26.1010.0531.2006.tar.gz
```

compile the module and make sure you have everything that is needed to do so :

```
sudo apt-get install build-essential linux-headers-$(uname -r)
cd rtl8185_linux_26.1010.0531.2006
./makedrv
```

Load it :

```
sudo ./wlan0up
```

And voilà :)

---

### Post by brandoncolorado on 2007-02-28
> **HymnToLife said:**
> It's very easy. Just open a terminal, cd to the dir where you saved the tarball then extract it :

```
tar xzvf rtl8185_linux_26.1010.0531.2006.tar.gz
```

compile the module and make sure you have everything that is needed to do so :

```
sudo apt-get install build-essential linux-headers-$(uname -r)
cd rtl8185_linux_26.1010.0531.2006
./makedrv
```

Load it :

```
sudo ./wlan0up
```

And voilà :)


Thanks man!

I got to the last step, the wlan0up and I get this:


brandon@brandon-laptop:~/Wireless/rtl8185_linux_26.1010.0531.2006$ sudo ./wlan0up
insmod: error inserting 'ieee80211_crypt-rtl.ko': -1 File exists
insmod: error inserting 'ieee80211_crypt_wep-rtl.ko': -1 File exists
insmod: error inserting 'ieee80211_crypt_tkip-rtl.ko': -1 File exists
insmod: error inserting 'ieee80211_crypt_ccmp-rtl.ko': -1 File exists
insmod: error inserting 'ieee80211-rtl.ko': -1 File exists
insmod: error inserting 'r8180.ko': -1 Unknown symbol in module
brandon@brandon-laptop:~/Wireless/rtl8185_linux_26.1010.0531.2006$

---

### Post by Bachstelze on 2007-02-28
```

sudo ./wlan0rmv
sudo ./wlan0down
sudo ./wlan0up
```

---

### Post by brandoncolorado on 2007-02-28
This is my dmesg output, I think that this may be a problem because I had tried to install an open source driver first:

[17179573.312000] PCI: No mmconfig possible on 6:9
[17179573.312000] Setting up standard PCI resources
[17179573.320000] ACPI: Interpreter enabled
[17179573.320000] ACPI: Using IOAPIC for interrupt routing
[17179573.320000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179573.320000] PCI: Probing PCI hardware (bus 00)
[17179573.320000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179573.324000] Boot video device is 0000:00:05.0
[17179573.324000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:0d.0
[17179573.324000] PCI: Transparent bridge - 0000:00:10.0
[17179573.324000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179573.352000] ACPI: Embedded Controller [EC] (gpe 91) interrupt mode.
[17179573.352000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[17179573.356000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[17179573.356000] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 10 11 14 15) *0, disabled.
[17179573.356000] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 10 *11 14 15)
[17179573.356000] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 10 11 14 15) *0, disabled.
[17179573.356000] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 10 11 14 15) *0, disabled.
[17179573.356000] ACPI: PCI Interrupt Link [LK1E] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[17179573.356000] ACPI: PCI Interrupt Link [LK2E] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[17179573.356000] ACPI: PCI Interrupt Link [LK3E] (IRQs 16 17 18 19 20 21 22 23) *5
[17179573.356000] ACPI: PCI Interrupt Link [LK4E] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[17179573.356000] ACPI: PCI Interrupt Link [LSMB] (IRQs 16 17 18 19 20 21 22 23) *10
[17179573.356000] ACPI: PCI Interrupt Link [LUS0] (IRQs 16 17 18 19 20 21 22 23) *11
[17179573.360000] ACPI: PCI Interrupt Link [LUS2] (IRQs 16 17 18 19 20 21 22 23) *7
[17179573.360000] ACPI: PCI Interrupt Link [LMAC] (IRQs 16 17 18 19 20 21 22 23) *10
[17179573.360000] ACPI: PCI Interrupt Link [LAZA] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[17179573.360000] ACPI: PCI Interrupt Link [LACI] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[17179573.360000] ACPI: PCI Interrupt Link [LMCI] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[17179573.360000] ACPI: PCI Interrupt Link [LPID] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[17179573.360000] ACPI: PCI Interrupt Link [LTID] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[17179573.360000] ACPI: PCI Interrupt Link [LSI1] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[17179573.360000] ACPI: PCI Interrupt Link [LPMU] (IRQs 16 17 18 19 20 21 22 23) *10
[17179573.360000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179573.360000] pnp: PnP ACPI init
[17179573.368000] pnp: PnP ACPI: found 11 devices
[17179573.368000] PnPBIOS: Disabled by ACPI PNP
[17179573.368000] PCI: Using ACPI for IRQ routing
[17179573.368000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179573.368000] pnp: 00:03: ioport range 0x1000-0x107f could not be reserved
[17179573.368000] pnp: 00:03: ioport range 0x1080-0x10ff has been reserved
[17179573.368000] pnp: 00:03: ioport range 0x1400-0x147f has been reserved
[17179573.368000] pnp: 00:03: ioport range 0x1480-0x14ff could not be reserved
[17179573.368000] pnp: 00:03: ioport range 0x1800-0x187f has been reserved
[17179573.368000] pnp: 00:03: ioport range 0x1880-0x18ff has been reserved
[17179573.368000] pnp: 00:03: ioport range 0x3040-0x307f has been reserved
[17179573.368000] pnp: 00:03: ioport range 0x3000-0x303f has been reserved
[17179573.368000] PCI: Bridge: 0000:00:03.0
[17179573.368000]   IO window: 9000-9fff
[17179573.368000]   MEM window: fa100000-fa8fffff
[17179573.368000]   PREFETCH window: bdf00000-bfefffff
[17179573.368000] PCI: Bridge: 0000:00:10.0
[17179573.368000]   IO window: 6000-6fff
[17179573.368000]   MEM window: b3400000-b34fffff
[17179573.368000]   PREFETCH window: disabled.
[17179573.368000] PCI: Setting latency timer of device 0000:00:03.0 to 64
[17179573.368000] PCI: Setting latency timer of device 0000:00:10.0 to 64
[17179573.368000] NET: Registered protocol family 2
[17179573.404000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179573.404000] TCP established hash table entries: 131072 (order: 7, 524288 bytes)
[17179573.404000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[17179573.404000] TCP: Hash tables configured (established 131072 bind 65536)
[17179573.404000] TCP reno registered
[17179573.404000] Simple Boot Flag at 0x31 set to 0x1
[17179573.404000] audit: initializing netlink socket (disabled)
[17179573.404000] audit(1172658485.404:1): initialized
[17179573.404000] highmem bounce pool size: 64 pages
[17179573.404000] VFS: Disk quotas dquot_6.5.1
[17179573.404000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179573.404000] Initializing Cryptographic API
[17179573.404000] io scheduler noop registered
[17179573.404000] io scheduler anticipatory registered
[17179573.404000] io scheduler deadline registered
[17179573.404000] io scheduler cfq registered (default)
[17179581.404000] 0000:00:0b.1 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
[17179581.404000] PCI: Setting latency timer of device 0000:00:03.0 to 64
[17179581.404000] pcie_portdrv_probe->Dev[02fd:10de] has invalid IRQ. Check vendor BIOS
[17179581.404000] assign_interrupt_mode Found MSI capability
[17179581.404000] Allocate Port Service[0000:00:03.0:pcie00]
[17179581.404000] Allocate Port Service[0000:00:03.0:pcie03]
[17179581.404000] isapnp: Scanning for PnP cards...
[17179581.756000] isapnp: No Plug & Play device found
[17179581.776000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179581.776000] mice: PS/2 mouse device common for all mice
[17179581.776000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179581.776000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179581.776000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179581.776000] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[17179581.784000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179581.784000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179581.784000] EISA: Probing bus 0 at eisa.0
[17179581.784000] Cannot allocate resource for EISA slot 1
[17179581.784000] Cannot allocate resource for EISA slot 2
[17179581.784000] Cannot allocate resource for EISA slot 3
[17179581.784000] Cannot allocate resource for EISA slot 6
[17179581.784000] EISA: Detected 0 cards.
[17179581.784000] TCP bic registered
[17179581.784000] NET: Registered protocol family 1
[17179581.784000] NET: Registered protocol family 8
[17179581.784000] NET: Registered protocol family 20
[17179581.784000] Using IPI Shortcut mode
[17179581.784000] ACPI: (supports S3 S4 S5)
[17179581.784000] Freeing unused kernel memory: 288k freed
[17179581.880000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179582.876000] Capability LSM initialized
[17179582.916000] ACPI: Getting cpuindex for acpiid 0x1
[17179583.432000] SCSI subsystem initialized
[17179583.436000] libata version 1.20 loaded.
[17179583.440000] NFORCE-MCP51: IDE controller at PCI slot 0000:00:0d.0
[17179583.440000] NFORCE-MCP51: chipset revision 241
[17179583.440000] NFORCE-MCP51: not 100% native mode: will probe irqs later
[17179583.440000] NFORCE-MCP51: 0000:00:0d.0 (rev f1) UDMA133 controller
[17179583.440000]     ide0: BM-DMA at 0x3080-0x3087, BIOS settings: hda:DMA, hdb:pio
[17179583.440000]     ide1: BM-DMA at 0x3088-0x308f, BIOS settings: hdc:DMA, hdd:pio
[17179583.440000] Probing IDE interface ide0...
[17179583.728000] hda: ST9100825A, ATA DISK drive
[17179584.400000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179584.400000] Probing IDE interface ide1...
[17179585.136000] hdc: HL-DT-ST DVD-RW GWA-4082N, ATAPI CD/DVD-ROM drive
[17179585.472000] ide1 at 0x170-0x177,0x376 on irq 15
[17179585.484000] hda: max request size: 512KiB
[17179585.488000] hda: 195371568 sectors (100030 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
[17179585.492000] hda: cache flushes supported
[17179585.492000]  hda: hda1 hda2 hda3 hda4 < hda5 >
[17179585.564000] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179585.564000] Uniform CD-ROM driver Revision: 3.20
[17179585.908000] usbcore: registered new driver usbfs
[17179585.908000] usbcore: registered new driver hub
[17179585.908000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179585.956000] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 23
[17179585.956000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LUS0] -> GSI 23 (level, high) -> IRQ 193
[17179585.956000] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[17179585.956000] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[17179585.956000] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[17179586.168000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.54.
[17179586.176000] ohci_hcd 0000:00:0b.0: irq 193, io mem 0xb0004000
[17179586.232000] usb usb1: configuration #1 chosen from 1 choice
[17179586.232000] hub 1-0:1.0: USB hub found
[17179586.232000] hub 1-0:1.0: 8 ports detected
[17179586.336000] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[17179586.336000] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LUS2] -> GSI 22 (level, high) -> IRQ 201
[17179586.336000] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[17179586.336000] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[17179586.336000] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[17179586.336000] ehci_hcd 0000:00:0b.1: debug port 1
[17179586.336000] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
[17179586.336000] ehci_hcd 0000:00:0b.1: irq 201, io mem 0xb0005000
[17179586.336000] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179586.336000] usb usb2: configuration #1 chosen from 1 choice
[17179586.336000] hub 2-0:1.0: USB hub found
[17179586.336000] hub 2-0:1.0: 8 ports detected
[17179586.440000] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 21
[17179586.440000] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [LMAC] -> GSI 21 (level, high) -> IRQ 209
[17179586.440000] PCI: Setting latency timer of device 0000:00:14.0 to 64
[17179586.440000] forcedeth: using HIGHDMA
[17179586.960000] eth0: forcedeth.c: subsystem: 0107b:0317 bound to 0000:00:14.0
[17179587.208000] kjournald starting.  Commit interval 5 seconds
[17179587.208000] EXT3-fs: mounted filesystem with ordered data mode.
[17179599.432000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179599.436000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179599.928000] input: PC Speaker as /class/input/input1
[17179600.148000] Real Time Clock Driver v1.12ac
[17179600.360000] rtl_ieee80211_crypt: registered algorithm 'NULL'
[17179600.360000] rtl_ieee80211_crypt: registered algorithm 'TKIP'
[17179600.360000] rtl_ieee80211_crypt: registered algorithm 'WEP'
[17179600.360000] rtl_ieee80211_crypt: registered algorithm 'CCMP'
[17179600.368000] 
[17179600.368000] Linux kernel driver for RTL8180 / RTL8185 based WLAN cards
[17179600.368000] Copyright (c) 2004-2005, Andrea Merello
[17179600.368000] rtl8180: Initializing module
[17179600.368000] rtl8180: Wireless extensions version 20
[17179600.368000] rtl8180: Initializing proc filesystem
[17179600.368000] rtl8180: Configuring chip resources
[17179600.368000] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 11
[17179600.368000] ACPI: PCI Interrupt 0000:06:09.0[A] -> Link [LNK1] -> GSI 11 (level, high) -> IRQ 11
[17179600.368000] rtl8180: Memory mapped space @ 0xb3400000 
[17179600.368000] rtl8180: MAC controller is a RTL8185 b/g (V. D)
[17179600.368000] rtl8180: This is a MINI-PCI NIC
[17179600.368000] rtl8180: Reported EEPROM chip is a 93c46 (1Kbit)
[17179600.372000] rtl8180: Card MAC address is 00:c0:a8:bc:53:7f
[17179600.388000] rtl8180: EEPROM version 105
[17179600.388000] rtl8180: Card reports RF frontend Realtek 8225
[17179600.388000] rtl8180: WW:This driver has EXPERIMENTAL support for this chipset.
[17179600.388000] rtl8180: WW:use it with care and at your own risk and
[17179600.388000] rtl8180: WW:**PLEASE** REPORT SUCCESS/INSUCCESS TO [email]andreamrl@tiscali.it[/email]
[17179600.388000] rtl8180: Energy threshold: b
[17179600.388000] rtl8180: PAPE from CONFIG2: 6
[17179600.388000] rtl8180: IRQ 11
[17179600.388000] rtl8180: Driver probe completed
[17179600.388000] 
[17179600.496000] Linux agpgart interface v0.101 (c) Dave Jones
[17179600.864000] nvidia: module license 'NVIDIA' taints kernel.
[17179601.144000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x23aeb3, caps: 0xa04713/0x10008
[17179601.188000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[17179601.304000] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 20
[17179601.304000] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LAZA] -> GSI 20 (level, high) -> IRQ 217
[17179601.304000] PCI: Setting latency timer of device 0000:00:10.1 to 64
[17179601.760000] ACPI: PCI Interrupt Link [LK3E] enabled at IRQ 19
[17179601.760000] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [LK3E] -> GSI 19 (level, high) -> IRQ 225
[17179601.760000] PCI: Setting latency timer of device 0000:00:05.0 to 64
[17179601.760000] NVRM: loading NVIDIA UNIX x86 Kernel Module  1.0-9746  Fri Dec 15 09:54:45 PST 2006
[17179601.824000] ts: Compaq touchscreen protocol output
[17179602.052000] eth0: no link during initialization.
[17179602.360000] lp: driver loaded but no devices found
[17179602.404000] fuse init (API version 7.6)
[17179602.464000] Unable to find swap-space signature
[17179602.520000] EXT3 FS on hda3, internal journal
[17179602.704000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179602.704000] md: bitmap version 4.39
[17179602.892000] device-mapper: 4.6.0-ioctl (2006-02-17) initialised: [email]dm-devel@redhat.com[/email]
[17179603.260000] NET: Registered protocol family 17
[17179604.404000] Unable to find swap-space signature
[17179609.012000] ACPI: AC Adapter [AC] (off-line)
[17179609.072000] ACPI: Battery Slot [BAT0] (battery present)
[17179609.088000] ACPI: Power Button (FF) [PWRF]
[17179609.088000] ACPI: Power Button (CM) [PWRB]
[17179609.088000] ACPI: Sleep Button (CM) [SLPB]
[17179609.088000] ACPI: Lid Switch [LID]
[17179609.196000] ibm_acpi: ec object not found
[17179609.228000] pcc_acpi: loading...
[17179609.520000] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.60.2)
[17179609.520000] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x13 (1075 mV)
[17179609.520000] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x1e (800 mV)
[17179609.520000] cpu_init done, current fid 0x8, vid 0x13
[17179615.532000] apm: BIOS not found.
[17179620.052000] rtl8180: Bringing up iface
[17179620.264000] rtl8180: Card successfully reset
[17179621.908000] Bluetooth: Core ver 2.8
[17179621.908000] NET: Registered protocol family 31
[17179621.908000] Bluetooth: HCI device and connection manager initialized
[17179621.908000] Bluetooth: HCI socket layer initialized
[17179621.944000] Bluetooth: L2CAP ver 2.8
[17179621.944000] Bluetooth: L2CAP socket layer initialized
[17179621.956000] Bluetooth: HIDP (Human Interface Emulation) ver 1.1-mh1
[17179621.968000] Bluetooth: RFCOMM socket layer initialized
[17179621.968000] Bluetooth: RFCOMM TTY layer initialized
[17179621.968000] Bluetooth: RFCOMM ver 1.7
[17179623.348000] rtl8180: Setting SW wep key
[17179634.044000] NET: Registered protocol family 10
[17179634.044000] lo: Disabled Privacy Extensions
[17179634.044000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179634.044000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[17179634.044000] IPv6 over IPv4 tunneling driver
[17180505.848000] rtl8180: Setting SW wep key
[17182480.008000] rtl8180: Bringing up iface
[17182480.216000] rtl8180: Card successfully reset
[17182481.108000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[17182482.268000] rtl8180: Setting SW wep key
[17182482.268000] rtl8180: Setting SW wep key
[17182482.268000] rtl8180: Setting SW wep key
[17182482.268000] rtl8180: Setting SW wep key
[17182482.272000] rtl8180: Setting SW wep key
[17182482.296000] Linking with JAYHAWK
[17182482.312000] Associated successfully
[17182482.312000] Using G rates
[17182482.324000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[17182482.348000] Linking with JAYHAWK
[17182484.860000] Linking with JAYHAWK
[17182484.876000] Associated successfully
[17182484.876000] Using G rates
[17182503.696000] wlan0: no IPv6 routers present
[17182884.100000] Associated successfully
[17182884.100000] Using G rates
[17182890.108000] Associated successfully
[17182890.108000] Using G rates
[17182898.216000] Associated successfully
[17182898.216000] Using G rates
[17182905.104000] Associated successfully
[17182905.104000] Using G rates
[17183008.828000] Associated successfully
[17183008.828000] Using G rates
[17183021.552000] Associated successfully
[17183021.552000] Using G rates
[17183030.144000] Associated successfully
[17183030.144000] Using G rates
[17183036.940000] Associated successfully
[17183036.940000] Using G rates
[17183044.368000] Associated successfully
[17183044.368000] Using G rates
[17183050.372000] Associated successfully
[17183050.372000] Using G rates
[17183061.372000] Associated successfully
[17183061.372000] Using G rates
[17183139.980000] Associated successfully
[17183139.980000] Using G rates
[17183149.364000] Associated successfully
[17183149.364000] Using G rates
[17183159.368000] Associated successfully
[17183159.368000] Using G rates
[17183165.384000] Associated successfully
[17183165.384000] Using G rates
[17183175.036000] Associated successfully
[17183175.036000] Using G rates
[17183437.928000] ieee80211_crypt: registered algorithm 'NULL'
[17183437.932000] ieee80211_crypt: registered algorithm 'WEP'
[17183437.932000] ieee80211_crypt: registered algorithm 'TKIP'
[17183437.956000] ieee80211_crypt: registered algorithm 'CCMP'
[17183437.960000] r8180: Unknown symbol ieee80211_reset_queue
[17183437.964000] r8180: Unknown symbol alloc_ieee80211_rtl
[17183437.964000] r8180: Unknown symbol ieee80211_wx_set_essid
[17183437.964000] r8180: Unknown symbol ieee80211_wx_get_encode_rtl
[17183437.964000] r8180: Unknown symbol ieee80211_wx_set_wap
[17183437.964000] r8180: Unknown symbol ieee80211_wx_set_rate
[17183437.964000] r8180: Unknown symbol ieee80211_wake_queue
[17183437.964000] r8180: Unknown symbol ieee80211_wx_set_power
[17183437.964000] r8180: Unknown symbol ieee80211_wx_set_freq
[17183437.964000] r8180: Unknown symbol ieee80211_wx_set_encode_rtl
[17183437.964000] r8180: Unknown symbol ieee80211_wx_get_mode
[17183437.964000] r8180: Unknown symbol ieee80211_wx_set_mode
[17183437.964000] r8180: Unknown symbol ieee80211_wx_get_essid
[17183437.964000] r8180: Unknown symbol ieee80211_get_beacon
[17183437.964000] r8180: Unknown symbol ieee80211_wpa_supplicant_ioctl
[17183437.964000] r8180: Unknown symbol ieee80211_wx_get_scan_rtl
[17183437.964000] r8180: Unknown symbol ieee80211_wx_get_power
[17183437.964000] r8180: Unknown symbol ieee80211_wx_set_rawtx
[17183437.964000] r8180: Unknown symbol ieee80211_softmac_stop_protocol
[17183437.964000] r8180: Unknown symbol ieee80211_is_54g
[17183437.964000] r8180: Unknown symbol ieee80211_stop_queue
[17183437.964000] r8180: Unknown symbol ieee80211_ps_tx_ack
[17183437.964000] r8180: Unknown symbol ieee80211_wx_get_rate
[17183437.964000] r8180: Unknown symbol ieee80211_wx_set_scan
[17183437.964000] r8180: Unknown symbol ieee80211_wx_get_wap
[17183437.964000] r8180: Unknown symbol ieee80211_wx_get_name_rtl
[17183437.964000] r8180: Unknown symbol ieee80211_is_shortslot
[17183437.964000] r8180: Unknown symbol ieee80211_rx_rtl
[17183437.964000] r8180: Unknown symbol ieee80211_wlan_frequencies
[17183437.964000] r8180: Unknown symbol free_ieee80211_rtl
[17183437.964000] r8180: Unknown symbol ieee80211_softmac_start_protocol
[17183437.964000] r8180: Unknown symbol ieee80211_wx_get_freq
[17183485.688000] r8180: Unknown symbol ieee80211_reset_queue
[17183485.688000] r8180: Unknown symbol alloc_ieee80211_rtl
[17183485.692000] r8180: Unknown symbol ieee80211_wx_set_essid
[17183485.692000] r8180: Unknown symbol ieee80211_wx_get_encode_rtl
[17183485.692000] r8180: Unknown symbol ieee80211_wx_set_wap
[17183485.692000] r8180: Unknown symbol ieee80211_wx_set_rate
[17183485.692000] r8180: Unknown symbol ieee80211_wake_queue
[17183485.692000] r8180: Unknown symbol ieee80211_wx_set_power
[17183485.692000] r8180: Unknown symbol ieee80211_wx_set_freq
[17183485.692000] r8180: Unknown symbol ieee80211_wx_set_encode_rtl
[17183485.692000] r8180: Unknown symbol ieee80211_wx_get_mode
[17183485.692000] r8180: Unknown symbol ieee80211_wx_set_mode
[17183485.692000] r8180: Unknown symbol ieee80211_wx_get_essid
[17183485.692000] r8180: Unknown symbol ieee80211_get_beacon
[17183485.692000] r8180: Unknown symbol ieee80211_wpa_supplicant_ioctl
[17183485.692000] r8180: Unknown symbol ieee80211_wx_get_scan_rtl
[17183485.692000] r8180: Unknown symbol ieee80211_wx_get_power
[17183485.692000] r8180: Unknown symbol ieee80211_wx_set_rawtx
[17183485.692000] r8180: Unknown symbol ieee80211_softmac_stop_protocol
[17183485.692000] r8180: Unknown symbol ieee80211_is_54g
[17183485.692000] r8180: Unknown symbol ieee80211_stop_queue
[17183485.692000] r8180: Unknown symbol ieee80211_ps_tx_ack
[17183485.692000] r8180: Unknown symbol ieee80211_wx_get_rate
[17183485.692000] r8180: Unknown symbol ieee80211_wx_set_scan
[17183485.692000] r8180: Unknown symbol ieee80211_wx_get_wap
[17183485.692000] r8180: Unknown symbol ieee80211_wx_get_name_rtl
[17183485.692000] r8180: Unknown symbol ieee80211_is_shortslot
[17183485.692000] r8180: Unknown symbol ieee80211_rx_rtl
[17183485.692000] r8180: Unknown symbol ieee80211_wlan_frequencies
[17183485.692000] r8180: Unknown symbol free_ieee80211_rtl
[17183485.692000] r8180: Unknown symbol ieee80211_softmac_start_protocol
[17183485.692000] r8180: Unknown symbol ieee80211_wx_get_freq
[17183518.024000] Associated successfully
[17183518.024000] Using G rates
[17183644.192000] Associated successfully
[17183644.192000] Using G rates
[17183645.608000] Linking with JAYHAWK
[17183647.656000] rtl8180: Setting SW wep key
[17183652.268000] rtl8180: Bringing up iface
[17183652.476000] rtl8180: Card successfully reset
[17183653.360000] Linking with JAYHAWK
[17183653.372000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[17183653.380000] Associated successfully
[17183653.380000] Using G rates
[17183653.392000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[17183654.428000] rtl8180: Setting SW wep key
[17183654.428000] rtl8180: Setting SW wep key
[17183654.428000] rtl8180: Setting SW wep key
[17183654.428000] rtl8180: Setting SW wep key
[17183654.428000] rtl8180: Setting SW wep key
[17183654.452000] Linking with JAYHAWK
[17183654.492000] Linking with JAYHAWK
[17183654.508000] Associated successfully
[17183654.508000] Using G rates
[17183667.896000] wlan0: no IPv6 routers present
[17184041.112000] ieee80211_crypt: unregistered algorithm 'CCMP'
[17184041.116000] ieee80211_crypt: unregistered algorithm 'TKIP'
[17184041.120000] ieee80211_crypt: unregistered algorithm 'WEP'
[17184041.124000] ieee80211_crypt: unregistered algorithm 'NULL' (deinit)
[17184047.424000] ieee80211_crypt: registered algorithm 'NULL'
[17184047.424000] ieee80211_crypt: registered algorithm 'WEP'
[17184047.444000] ieee80211_crypt: registered algorithm 'TKIP'
[17184047.452000] ieee80211_crypt: registered algorithm 'CCMP'
[17184047.456000] r8180: Unknown symbol ieee80211_reset_queue
[17184047.456000] r8180: Unknown symbol alloc_ieee80211_rtl
[17184047.456000] r8180: Unknown symbol ieee80211_wx_set_essid
[17184047.456000] r8180: Unknown symbol ieee80211_wx_get_encode_rtl
[17184047.456000] r8180: Unknown symbol ieee80211_wx_set_wap
[17184047.456000] r8180: Unknown symbol ieee80211_wx_set_rate
[17184047.456000] r8180: Unknown symbol ieee80211_wake_queue
[17184047.456000] r8180: Unknown symbol ieee80211_wx_set_power
[17184047.456000] r8180: Unknown symbol ieee80211_wx_set_freq
[17184047.456000] r8180: Unknown symbol ieee80211_wx_set_encode_rtl
[17184047.456000] r8180: Unknown symbol ieee80211_wx_get_mode
[17184047.456000] r8180: Unknown symbol ieee80211_wx_set_mode
[17184047.456000] r8180: Unknown symbol ieee80211_wx_get_essid
[17184047.456000] r8180: Unknown symbol ieee80211_get_beacon
[17184047.460000] r8180: Unknown symbol ieee80211_wpa_supplicant_ioctl
[17184047.460000] r8180: Unknown symbol ieee80211_wx_get_scan_rtl
[17184047.460000] r8180: Unknown symbol ieee80211_wx_get_power
[17184047.460000] r8180: Unknown symbol ieee80211_wx_set_rawtx
[17184047.460000] r8180: Unknown symbol ieee80211_softmac_stop_protocol
[17184047.460000] r8180: Unknown symbol ieee80211_is_54g
[17184047.460000] r8180: Unknown symbol ieee80211_stop_queue
[17184047.460000] r8180: Unknown symbol ieee80211_ps_tx_ack
[17184047.460000] r8180: Unknown symbol ieee80211_wx_get_rate
[17184047.460000] r8180: Unknown symbol ieee80211_wx_set_scan
[17184047.460000] r8180: Unknown symbol ieee80211_wx_get_wap
[17184047.460000] r8180: Unknown symbol ieee80211_wx_get_name_rtl
[17184047.460000] r8180: Unknown symbol ieee80211_is_shortslot
[17184047.460000] r8180: Unknown symbol ieee80211_rx_rtl
[17184047.460000] r8180: Unknown symbol ieee80211_wlan_frequencies
[17184047.460000] r8180: Unknown symbol free_ieee80211_rtl
[17184047.460000] r8180: Unknown symbol ieee80211_softmac_start_protocol
[17184047.460000] r8180: Unknown symbol ieee80211_wx_get_freq
[17184047.472000] rtl8180: Bringing up iface
[17184047.680000] rtl8180: Card successfully reset
[17184049.496000] Linking with JAYHAWK
[17184049.508000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[17184049.508000] Associated successfully
[17184049.508000] Using G rates
[17184049.524000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[17184050.536000] Linking with JAYHAWK
[17184050.572000] Linking with JAYHAWK
[17184052.588000] rtl8180: Setting SW wep key
[17184052.588000] rtl8180: Bringing up iface
[17184052.796000] rtl8180: Card successfully reset
[17184053.676000] Linking with JAYHAWK
[17184053.692000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[17184053.692000] Associated successfully
[17184053.692000] Using G rates
[17184053.704000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[17184054.784000] rtl8180: Setting SW wep key
[17184054.784000] rtl8180: Setting SW wep key
[17184054.784000] rtl8180: Setting SW wep key
[17184054.784000] rtl8180: Setting SW wep key
[17184054.784000] rtl8180: Setting SW wep key
[17184054.812000] Linking with JAYHAWK
[17184054.848000] Linking with JAYHAWK
[17184054.864000] Associated successfully
[17184054.864000] Using G rates
[17184070.732000] wlan0: no IPv6 routers present
brandon@brandon-laptop:~/Wireless/rtl8185_linux_26.1010.0531.2006$

---

### Post by brandoncolorado on 2007-02-28
because I had this installed:

[http://rtl8180-sa2400.sourceforge.net/](http://rtl8180-sa2400.sourceforge.net/)

---

### Post by brandoncolorado on 2007-03-01
bump

---

### Post by jcondal on 2007-03-20
I've been trying the same process but for some reason I can't build the driver in the first place. I keep getting the following output:
```

make -C /lib/modules/2.6.15-28-386/build M=/home/jeff/belkin/rtl8185_linux_26.1010.0531.2006/ieee80211 CC=gcc modules
make[1]: Entering directory `/lib/modules/2.6.15-28-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.15-28-386/build'
make: *** [modules] Error 2
rm -f *.mod.c *.mod *.o .*.cmd *.ko
rm -rf /home/jeff/belkin/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/tmp
make -C /lib/modules/2.6.15-28-386/build M=/home/jeff/belkin/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1 CC=gcc modules
make[1]: Entering directory `/lib/modules/2.6.15-28-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.15-28-386/build'
make: *** [modules] Error 2
```

Can anybody point me in the right direction?

---

### Post by aferbar on 2007-10-28
I've got a SMCWPCI-G wireless card. 
I've installed Ubuntu 7.04 feisty
I've downloaded the driver ant I've tried to follow your instructions but when I make the 

./makedrv

I get several errors compiling softmac.o. 
The first error is from macro "INIT_WORK"

Can someone help me

Thanks in advance for your help

---

