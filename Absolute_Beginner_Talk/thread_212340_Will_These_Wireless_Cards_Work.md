---
title: "Will These Wireless Cards Work?"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by kc5hwb on 2006-07-09
Netgear WG311 v2 PCI card
0000:00:03.0 0200: 1039:0900 (rev 90)

Airlink 101 USB
Bus 002 Device 002: ID 0ace:1215 ZyDAS

I got this by running "lspci" and lspci -n" and the same for the Airlink, which is USB. (lsusb)

I saw a thread in the wireless section that listed chipsets for all the known supported wireless cards for Ubuntu and neither of these were listed, but it did mention something about adding a new wirless card to the list if you found one.

So will either of these work?

I can't get Ubuntu to even recognize the USB one...but

With the Netgear, it sees the card, allows me to activate it and shows active as wlan1.  But it will not detect my network AT ALL.  I opened up the whole router and still it will not see my network.  So I guess I am doing something wrong, or the chipset isn't right for Ubuntu, because there were other WG311 v2 cards on that wireless list in the other thread, but none of them matched this chipset that I have.

---

### Post by HarrisonHopkins on 2006-07-09
Use ndiswrapper. Thats what I did to get wireless to work with my Xubuntu one time.

---

### Post by kc5hwb on 2006-07-09
Yeah....someone else said that too.  But I can't see to figure out how to use  it...

---

### Post by Apple 101 on 2006-07-09
Download *ndisgtk* (in Universe), *ndiswrapper-tools*, *wireless-tools*, *wpa_supplicant* in Synaptic (see below for how to get the Universe repository) and the appropriate .INF and .SYS files for your Netgear card (check the Netgear site).

Copy the .INF and .SYS files somewhere (ie: /home) and open *ndisgtk* (System --> Administration --> Windows Wireless Drivers).  Select Install (or whatever that option is called).  Find your .INF file and select it for opening.  The card should be displayed and say Hardware Present: Yes.  Press OK, and open your network settings.  Configure your card.

---

### Post by kc5hwb on 2006-07-09
> **Apple 101 said:**
> Download *ndisgtk* (in Universe), *ndiswrapper-tools*, *wireless-tools*, *wpa_supplicant* and the appropriate .INF and .SYS files for your Netgear card (check the Netgear site).

I do not understand what you mean here.  Universe?  Is that Synaptic?  The rest of these are DL'd also with Synaptic?

---

### Post by orb9220 on 2006-07-09
He said to get them yes thru synaptic except!

"and the appropriate .INF and .SYS files for your Netgear card (check the Netgear site)."

Those are propriety drivers for windows that synaptic cannot distrubute

---

### Post by Apple 101 on 2006-07-10
[QUOTE="kc5hwb"]I do not understand what you mean here. Universe? Is that Synaptic? The rest of these are DL'd also with Synaptic?[/QUOTE]Sorry if I was not clear on that point.  All of the packages excepting the Netgear files are downloadable in Synaptic.

To get ndisgtk: Open Synaptic --> Settings --> Repositories --> Check the box for Ubuntu 6.06 LTS Community Maintained (Universe) --> Close --> Reload --> Search for ndisgtk.

Now follow the rest of my post above.

---

### Post by Stormboy on 2006-08-06
I did all that, but get "Hardaware Present: No"
Does it have to be blacklisted?

---

### Post by Apple 101 on 2006-08-06
Open a terminal and type *dmesg*.  Look for something that says *mrv8k* in the output.  Let me know if it says anything like that.

Make sure that you have the correct .INF and .SYS files in a directory.  Navigate to that directory in a terminal. Type: *ndiswrapper -l*.  Now type: *sudo ndiswrapper -e <driver name here (from above)>*.  Now type: *sudo ndiswrapper -i <wg311v2.inf>* (the filename and extension of the .INF file.  Now type: *sudo ndiswrapper -m*.

---

### Post by Stormboy on 2006-08-06
> **Apple 101 said:**
> Open a terminal and type *dmesg*.  Look for something that says *mrv8k* in the output.  Let me know if it says anything like that.

Make sure that you have the correct .INF and .SYS files in a directory.  Navigate to that directory in a terminal. Type: *ndiswrapper -l*.  Now type: *sudo ndiswrapper -e <driver name here (from above)>*.  Now type: *sudo ndiswrapper -i <wg311v2.inf>* (the filename and extension of the .INF file.  Now type: *sudo ndiswrapper -m*.

Dont see mrv8k.

> chris@Ubuntu:~$ dmesg
[17179569.184000] Linux version 2.6.15-26-686 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Thu Aug 3 03:13:28 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 0000000017ef0000 (usable)
[17179569.184000]  BIOS-e820: 0000000017ef0000 - 0000000017ef3000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 0000000017ef3000 - 0000000017f00000 (ACPI data)
[17179569.184000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 382MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 98032
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 93936 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI 2.2 present.
[17179569.184000] ACPI: RSDP (v000 GBT                                   ) @ 0x000f7870
[17179569.184000] ACPI: RSDT (v001 GBT    AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x17ef3000
[17179569.184000] ACPI: FADT (v001 GBT    AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x17ef3040
[17179569.184000] ACPI: DSDT (v001 GBT    AWRDACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x4008
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 17f00000:e7c00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (013a0000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[17179569.184000] Detected 935.574 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179572.608000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179572.608000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)[17179572.648000] Memory: 377064k/392128k available (2110k kernel code, 14428k reserved, 595k data, 332k init, 0k highmem)
[17179572.648000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179572.728000] Calibrating delay using timer specific routine.. 1872.85 BogoMIPS (lpj=3745719)
[17179572.728000] Security Framework v1.0.0 initialized
[17179572.728000] SELinux:  Disabled at boot.
[17179572.728000] Mount-cache hash table entries: 512
[17179572.728000] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[17179572.728000] CPU: After vendor identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[17179572.728000] CPU: L1 I cache: 16K, L1 D cache: 16K
[17179572.728000] CPU: L2 cache: 256K
[17179572.728000] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[17179572.728000] mtrr: v2.0 (20020519)
[17179572.728000] Enabling fast FPU save and restore... done.
[17179572.728000] Enabling unmasked SIMD FPU exception support... done.
[17179572.728000] Checking 'hlt' instruction... OK.
[17179572.744000] SMP alternatives: switching to UP code
[17179572.744000] checking if image is initramfs... it is
[17179573.920000] Freeing initrd memory: 6809k freed
[17179573.960000] ACPI: Looking for DSDT ... not found!
[17179573.964000] ACPI: setting ELCR to 0200 (from 0e00)
[17179573.964000] CPU0: Intel Pentium III (Coppermine) stepping 06
[17179573.964000] SMP motherboard not detected.
[17179573.964000] Local APIC not detected. Using dummy APIC emulation.
[17179573.964000] Brought up 1 CPUs
[17179573.964000] NET: Registered protocol family 16
[17179573.968000] EISA bus registered
[17179573.968000] ACPI: bus type pci registered
[17179573.980000] PCI: PCI BIOS revision 2.10 entry at 0xfb130, last bus=1
[17179573.980000] PCI: Using configuration type 1
[17179573.980000] ACPI: Subsystem revision 20051216
[17179573.992000] ACPI: Interpreter enabled
[17179573.992000] ACPI: Using PIC for interrupt routing
[17179573.992000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179573.992000] PCI: Probing PCI hardware (bus 00)
[17179573.992000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179573.996000] Boot video device is 0000:00:02.0
[17179573.996000] PCI quirk: region 4000-407f claimed by ICH4 ACPI/GPIO/TCO
[17179573.996000] PCI quirk: region 4080-40bf claimed by ICH4 GPIO
[17179574.000000] PCI: Transparent bridge - 0000:00:1e.0
[17179574.000000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179574.028000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[17179574.032000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11 12 14 15) *9
[17179574.032000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11 12 14 15) *9
[17179574.032000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[17179574.032000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 14 15) *9
[17179574.032000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179574.036000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179574.036000] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179574.036000] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11 12 14 15) *9
[17179574.040000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179574.040000] pnp: PnP ACPI init
[17179574.048000] pnp: PnP ACPI: found 13 devices
[17179574.048000] PnPBIOS: Disabled by ACPI PNP
[17179574.048000] PCI: Using ACPI for IRQ routing
[17179574.048000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179574.060000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[17179574.060000] PCI: Bridge: 0000:00:1e.0
[17179574.060000]   IO window: c000-cfff
[17179574.060000]   MEM window: d4000000-d5ffffff
[17179574.060000]   PREFETCH window: 20000000-200fffff
[17179574.060000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179574.060000] audit: initializing netlink socket (disabled)
[17179574.060000] audit(1154840790.056:1): initialized
[17179574.060000] VFS: Disk quotas dquot_6.5.1
[17179574.060000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179574.060000] Initializing Cryptographic API
[17179574.060000] io scheduler noop registered
[17179574.060000] io scheduler anticipatory registered
[17179574.060000] io scheduler deadline registered
[17179574.060000] io scheduler cfq registered
[17179574.060000] isapnp: Scanning for PnP cards...
[17179574.416000] isapnp: No Plug & Play device found
[17179574.456000] Real Time Clock Driver v1.12
[17179574.456000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179574.456000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179574.456000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179574.456000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179574.460000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179574.460000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179574.464000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179574.464000] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179574.464000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179574.464000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179574.464000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179574.468000] mice: PS/2 mouse device common for all mice
[17179574.468000] EISA: Probing bus 0 at eisa.0
[17179574.468000] Cannot allocate resource for EISA slot 4
[17179574.468000] EISA: Detected 0 cards.
[17179574.468000] NET: Registered protocol family 2
[17179574.496000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179574.508000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179574.508000] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[17179574.508000] TCP bind hash table entries: 16384 (order: 5, 196608 bytes)
[17179574.508000] TCP: Hash tables configured (established 16384 bind 16384)
[17179574.508000] TCP reno registered
[17179574.508000] TCP bic registered
[17179574.508000] NET: Registered protocol family 1
[17179574.508000] NET: Registered protocol family 8
[17179574.508000] NET: Registered protocol family 20
[17179574.508000] Using IPI No-Shortcut mode
[17179574.508000] ACPI wakeup devices:
[17179574.508000] SLPB PCI0 HUB0 USB0 USB1
[17179574.508000] ACPI: (supports S0 S1 S3 S4 S5)
[17179574.508000] Freeing unused kernel memory: 332k freed
[17179574.628000] vga16fb: initializing
[17179574.628000] vga16fb: mapped to 0xc00a0000
[17179574.732000] Console: switching to colour frame buffer device 80x25
[17179574.732000] fb0: VGA16 VGA frame buffer device
[17179575.832000] Capability LSM initialized
[17179575.900000] ACPI: Fan [FAN] (on)
[17179575.908000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[17179575.908000] ACPI: Processor [CPU0] (supports 2 throttling states)
[17179575.912000] ACPI: Thermal Zone [THRM] (27 C)
[17179577.144000] ICH2: IDE controller at PCI slot 0000:00:1f.1
[17179577.144000] ICH2: chipset revision 1
[17179577.144000] ICH2: not 100% native mode: will probe irqs later
[17179577.144000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:pio
[17179577.144000]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:pio
[17179577.144000] Probing IDE interface ide0...
[17179577.432000] hda: ST380011A, ATA DISK drive
[17179578.104000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179578.108000] Probing IDE interface ide1...
[17179578.844000] hdc: LTN526S, ATAPI CD/DVD-ROM drive
[17179579.180000] ide1 at 0x170-0x177,0x376 on irq 15
[17179579.196000] hda: max request size: 1024KiB
[17179579.216000] hda: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[17179579.216000] hda: cache flushes supported
[17179579.216000]  hda: hda1 hda2 < hda5 >
[17179579.248000] hdc: ATAPI 52X CD-ROM drive, 120kB Cache, UDMA(33)
[17179579.248000] Uniform CD-ROM driver Revision: 3.20
[17179579.540000] usbcore: registered new driver usbfs
[17179579.540000] usbcore: registered new driver hub
[17179579.548000] USB Universal Host Controller Interface driver v2.3
[17179579.548000] **** SET: Misaligned resource pointer: d6966862 Type 07 Len 0
[17179579.548000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[17179579.548000] PCI: setting IRQ 11 as level-triggered
[17179579.548000] ACPI: PCI Interrupt 0000:00:1f.2[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179579.548000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179579.548000] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[17179579.548000] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[17179579.548000] uhci_hcd 0000:00:1f.2: irq 11, io base 0x0000d000
[17179579.552000] hub 1-0:1.0: USB hub found
[17179579.552000] hub 1-0:1.0: 2 ports detected
[17179579.656000] **** SET: Misaligned resource pointer: d69666e2 Type 07 Len 0
[17179579.656000] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 10
[17179579.656000] PCI: setting IRQ 10 as level-triggered
[17179579.656000] ACPI: PCI Interrupt 0000:00:1f.4[C] -> Link [LNK1] -> GSI 10 (level, low) -> IRQ 10
[17179579.656000] PCI: Setting latency timer of device 0000:00:1f.4 to 64
[17179579.656000] uhci_hcd 0000:00:1f.4: UHCI Host Controller
[17179579.656000] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 2
[17179579.656000] uhci_hcd 0000:00:1f.4: irq 10, io base 0x0000d800
[17179579.656000] hub 2-0:1.0: USB hub found
[17179579.656000] hub 2-0:1.0: 2 ports detected
[17179579.908000] Attempting manual resume
[17179579.936000] kjournald starting.  Commit interval 5 seconds
[17179579.936000] EXT3-fs: mounted filesystem with ordered data mode.
[17179593.384000] input: PC Speaker as /class/input/input1
[17179593.428000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179593.432000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179593.488000] Linux agpgart interface v0.101 (c) Dave Jones
[17179593.500000] agpgart: Detected an Intel i815 Chipset.
[17179593.508000] agpgart: AGP aperture is 64M @ 0xd0000000
[17179593.520000] hw_random hardware driver 1.0.0 loaded
[17179593.576000] i810_smbus 0000:00:02.0: i810/i815 i2c device found.
[17179593.892000] input: PS2++ Logitech MX Mouse as /class/input/input2
[17179593.912000] natsemi dp8381x driver, version 1.07+LK1.0.17, Sep 27, 2002
[17179593.912000]   originally by Donald Becker <becker@scyld.com>
[17179593.912000]   [http://www.scyld.com/network/natsemi.html](http://www.scyld.com/network/natsemi.html)
[17179593.912000]   2.4.x kernel port by Jeff Garzik, Tjeerd Mulder
[17179593.912000] **** SET: Misaligned resource pointer: d3ef5b82 Type 07 Len 0
[17179593.912000] ACPI: PCI Interrupt Link [LNK0] enabled at IRQ 11
[17179593.912000] ACPI: PCI Interrupt 0000:01:02.0[A] -> Link [LNK0] -> GSI 11 (level, low) -> IRQ 11
[17179593.916000] natsemi eth0: NatSemi DP8381[56] at 0xd5062000 (0000:01:02.0), 00:09:5b:05:80:6a, IRQ 11, port TP.
[17179594.412000] ts: Compaq touchscreen protocol output
[17179594.668000] Floppy drive(s): fd0 is 1.44M
[17179594.684000] FDC 0 is a post-1991 82077
[17179594.688000] parport: PnPBIOS parport detected.
[17179594.688000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[17179595.244000] ACPI: PCI Interrupt 0000:01:0a.0[A] -> Link [LNK0] -> GSI 11 (level, low) -> IRQ 11
[17179595.436000] eth0: DSPCFG accepted after 0 usec.
[17179595.436000] eth0: link up.
[17179595.436000] eth0: Setting full-duplex based on negotiated link capability.[17179596.640000] NET: Registered protocol family 17
[17179597.204000] Intel ISA PCIC probe: not found.
[17179597.404000] lp0: using parport0 (interrupt-driven).
[17179597.588000] Adding 1124508k swap on /dev/hda5.  Priority:-1 extents:1 across:1124508k
[17179597.716000] EXT3 FS on hda1, internal journal
[17179598.020000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179598.020000] md: bitmap version 4.39
[17179598.812000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[17179600.652000] NET: Registered protocol family 10
[17179600.652000] lo: Disabled Privacy Extensions
[17179600.652000] IPv6 over IPv4 tunneling driver
[17179606.168000] cdrom: open failed.
[17179608.144000] ACPI: Power Button (FF) [PWRF]
[17179608.144000] ACPI: Power Button (CM) [PWRB]
[17179608.148000] ACPI: Sleep Button (CM) [SLPB]
[17179608.368000] ibm_acpi: ec object not found
[17179608.428000] pcc_acpi: loading...
[17179610.704000] eth0: no IPv6 routers present
[17179616.132000] ppdev: user-space parallel port driver
[17179618.752000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179618.752000] apm: overridden by ACPI.
[17179621.340000] Bluetooth: Core ver 2.8
[17179621.340000] NET: Registered protocol family 31
[17179621.340000] Bluetooth: HCI device and connection manager initialized
[17179621.340000] Bluetooth: HCI socket layer initialized
[17179621.376000] Bluetooth: L2CAP ver 2.8
[17179621.376000] Bluetooth: L2CAP socket layer initialized
[17179621.428000] Bluetooth: RFCOMM socket layer initialized
[17179621.428000] Bluetooth: RFCOMM TTY layer initialized
[17179621.428000] Bluetooth: RFCOMM ver 1.7
chris@Ubuntu:~$


Also got this with: **ndiswrapper -l**

chris@Ubuntu:~$ cd Desktop
chris@Ubuntu:~/Desktop$ ls
bookmarks.html  net
chris@Ubuntu:~/Desktop$ cd net
chris@Ubuntu:~/Desktop/net$ ls
netwg311_XP.sys  wg311v2.inf
chris@Ubuntu:~/Desktop/net$ ndiswrapper -l
Installed ndis drivers:
wg311v2         driver present
chris@Ubuntu:~/Desktop/net$

---

### Post by Apple 101 on 2006-08-06
Are they the latest drivers from Netgear?

---

### Post by Stormboy on 2006-08-06
> **Apple 101 said:**
> Are they the latest drivers from Netgear?
Yep downloaded them before the install :)

I am very impressed with Ubuntu but getting the wireless to work ... not so far lol just using nic for now :)

---

### Post by Apple 101 on 2006-08-06
Open Network Manager (System --> Administration --> Network Manager) and tell me if you see wlan0 or ath0.

If not, do this:
1. Open a terminal.
2. gksudo gedit /etc/modules
3. Add *ndiswrapper* at the bottom of the list and then press enter.
4. Save and exit Gedit.
5. Open Synaptic, and install Network Manager (and its all dependent packages).
6. Activate your wireless router/access point (if you haven't done so) and restart your computer.

The theory is that Network Manager should detect your wireless broadcast signal.  Your wlan0 should be in Network Manager and the WLAN should be listed in the tray icon list (left-click it).

This method worked for me, and I have a Netgear WG311v3.

---

### Post by Stormboy on 2006-08-06
Just rebooting so hope this does it!
Thanks for you help so far!

> **Apple 101 said:**
> Open Network Manager (System --> Administration --> Network Manager) and tell me if you see wlan0 or ath0.

If not, do this:
1. Open a terminal.
2. gksudo gedit /etc/modules
3. Add *ndiswrapper* at the bottom of the list and then press enter.
4. Save and exit Gedit.
5. Open Synaptic, and install Network Manager (and its all dependent packages).
6. Activate your wireless router/access point (if you haven't done so) and restart your computer.

The theory is that Network Manager should detect your wireless broadcast signal.  Your wlan0 should be in Network Manager and the WLAN should be listed in the tray icon list (left-click it).

This method worked for me, and I have a Netgear WG311v3.

---

### Post by Stormboy on 2006-08-06
:-( No luck

---

### Post by Cryonic on 2006-08-06
The output of "ndiswrapper -l" should say "driver present, **hardware present**", which it doesn't, in your case.
So installing drivers won't help unless the hardware is recognized. 
Check this [WirelessTroubleshootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide") and go from step 4.1 using the commands in paragraph 3.

---

### Post by Stormboy on 2006-08-07
Thanks
It's there :
But I will have to see what to do later the dumbo version lol :D
> *-network:1 UNCLAIMED
                description: Network controller
                product: Texas Instruments
                vendor: Texas Instruments
                physical id: 4
                bus info: pci@01:04.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                resources: iomemory:d5040000-d5041fff iomemory:d5000000-d503ffff
> **Cryonic said:**
> The output of "ndiswrapper -l" should say "driver present, **hardware present**", which it doesn't, in your case.
So installing drivers won't help unless the hardware is recognized. 
Check this [WirelessTroubleshootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide") and go from step 4.1 using the commands in paragraph 3.

---

### Post by kc5hwb on 2006-09-21
Is there a list somewhere of wireless cards that will work with Ubuntu?  For the life of me, I cannot get this Netgear card to work.

---

