---
title: "No sound"
date: 2006-05-03
forum: Absolute Beginner Talk
---

### Post by NeoRc on 2006-05-03
I'm new to linux. I install Breezy Badger on a new laptop, but the system have no sound. I return to the Windows and find that it's a Conexant sound card.

```
# lspci:
0000:00:00.0 Host bridge: Intel Corp. Mobile Memory Controller Hub (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corp. Mobile Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corp. Mobile Graphics Controller (rev 03)
0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d4)
0000:00:1e.2 Multimedia audio controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
0000:00:1e.3 Modem: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
0000:00:1f.1 IDE interface: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
0000:06:01.0 CardBus bridge: Texas Instruments: Unknown device 8031
0000:06:01.2 FireWire (IEEE 1394): Texas Instruments: Unknown device 8032
0000:06:01.3 Unknown mass storage controller: Texas Instruments: Unknown device 8033
0000:06:03.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
0000:06:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```

lsmod | grep snd:
no output -_-

---

### Post by zerhacke on 2006-05-05
Please open a terminal, type in ```
lspci
```and hit enter.  Then copy the output to here.  We need to know what kind of sound card it is.

---

### Post by NeoRc on 2006-05-10
[QUOTE=zerhacke]Please open a terminal, type in ```
lspci
```and hit enter.  Then copy the output to here.  We need to know what kind of sound card it is.[/QUOTE]

0000:00:00.0 Host bridge: Intel Corp. Mobile Memory Controller Hub (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corp. Mobile Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corp. Mobile Graphics Controller (rev 03)
0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d4)
0000:00:1e.2 Multimedia audio controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
0000:00:1e.3 Modem: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
0000:00:1f.1 IDE interface: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
0000:06:01.0 CardBus bridge: Texas Instruments: Unknown device 8031
0000:06:01.2 FireWire (IEEE 1394): Texas Instruments: Unknown device 8032
0000:06:01.3 Unknown mass storage controller: Texas Instruments: Unknown device 8033
0000:06:03.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
0000:06:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by NeoRc on 2006-05-11
And there is my /var/log/dmesg:
```
 Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294670.466000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[4294670.480000] Memory: 502148k/514944k available (1416k kernel code, 12288k reserved, 762k data, 224k init, 0k highmem)
[4294670.480000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294670.480000] Calibrating delay loop... 2555.90 BogoMIPS (lpj=1277952)
[4294670.503000] Security Framework v1.0.0 initialized
[4294670.503000] SELinux:  Disabled at boot.
[4294670.503000] Mount-cache hash table entries: 512
[4294670.503000] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 00000000 00000000 00000000
[4294670.503000] CPU: After vendor identify, caps: afe9fbff 00100000 00000000 00000000 00000000 00000000 00000000
[4294670.503000] CPU: L1 I cache: 32K, L1 D cache: 32K
[4294670.503000] CPU: L2 cache: 1024K
[4294670.503000] CPU: After all inits, caps: afe9fbff 00100000 00000000 00000040 00000000 00000000 00000000
[4294670.503000] CPU: Intel(R) Celeron(R) M processor         1.30GHz stepping 08
[4294670.503000] Enabling fast FPU save and restore... done.
[4294670.503000] Enabling unmasked SIMD FPU exception support... done.
[4294670.503000] Checking 'hlt' instruction... OK.
[4294670.507000] Checking for popad bug... OK.
[4294670.507000] checking if image is initramfs... it is
[4294671.202000] Freeing initrd memory: 5172k freed
[4294671.203000] ACPI: Looking for DSDT in initrd... not found!
[4294671.262000]  not found!
[4294671.316000] ENABLING IO-APIC IRQs
[4294671.316000] ..TIMER: vector=0x31 pin1=2 pin2=-1
[4294671.427000] NET: Registered protocol family 16
[4294671.427000] EISA bus registered
[4294671.427000] ACPI: bus type pci registered
[4294671.427000] PCI: PCI BIOS revision 2.10 entry at 0xfd924, last bus=7
[4294671.427000] PCI: Using MMCONFIG
[4294671.427000] mtrr: v2.0 (20020519)
[4294671.427000] ACPI: Subsystem revision 20050729
[4294671.432000] ACPI: Interpreter enabled
[4294671.432000] ACPI: Using IOAPIC for interrupt routing
[4294671.433000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294671.433000] PCI: Probing PCI hardware (bus 00)
[4294671.433000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[4294671.436000] Boot video device is 0000:00:02.0
[4294671.436000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[4294671.437000] PCI: Transparent bridge - 0000:00:1e.0
[4294671.447000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294671.449000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[4294671.450000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[4294671.451000] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[4294671.451000] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[4294671.452000] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[4294671.452000] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[4294671.452000] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[4294671.452000] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[4294671.453000] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[4294671.453000] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[4294671.453000] burst-mode-ec-10-Aug
[4294671.453000] ACPI: Embedded Controller [EC0] (gpe 29)
[4294671.466000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294671.466000] pnp: PnP ACPI init
[4294671.470000] pnp: PnP ACPI: found 11 devices
[4294671.470000] PnPBIOS: Disabled by ACPI PNP
[4294671.470000] PCI: Using ACPI for IRQ routing
[4294671.470000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294671.492000] Simple Boot Flag at 0x36 set to 0x1
[4294671.492000] audit: initializing netlink socket (disabled)
[4294671.492000] audit: initialized
[4294671.492000] VFS: Disk quotas dquot_6.5.1
[4294671.492000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294671.492000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294671.492000] devfs: boot_options: 0x0
[4294671.492000] Initializing Cryptographic API
[4294671.492000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
[4294671.492000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[4294671.492000] assign_interrupt_mode Found MSI capability
[4294671.492000] Allocate Port Service[pcie00]
[4294671.493000] Allocate Port Service[pcie02]
[4294671.493000] Allocate Port Service[pcie03]
[4294671.493000] isapnp: Scanning for PnP cards...
[4294671.845000] isapnp: No Plug & Play device found
[4294671.864000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[4294671.866000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294671.866000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294671.866000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
[4294671.866000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294671.866000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294671.868000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294671.869000] ACPI: PCI Interrupt 0000:00:1e.3[B] -> GSI 20 (level, low) -> IRQ 20
[4294671.869000] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
[4294671.869000] io scheduler noop registered
[4294671.869000] io scheduler anticipatory registered
[4294671.869000] io scheduler deadline registered
[4294671.869000] io scheduler cfq registered
[4294671.869000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294671.870000] EISA: Probing bus 0 at eisa.0
[4294671.870000] Cannot allocate resource for EISA slot 1
[4294671.870000] Cannot allocate resource for EISA slot 2
[4294671.870000] Cannot allocate resource for EISA slot 4
[4294671.870000] EISA: Detected 0 cards.
[4294671.870000] NET: Registered protocol family 2
[4294671.880000] IP: routing cache hash table of 4096 buckets, 32Kbytes
[4294671.880000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[4294671.880000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[4294671.880000] TCP: Hash tables configured (established 16384 bind 16384)
[4294671.880000] NET: Registered protocol family 8
[4294671.880000] NET: Registered protocol family 20
[4294671.880000] ACPI wakeup devices: 
[4294671.880000] AZAL RP01 RP02 RP03 RP04 LANC MODM 
[4294671.880000] ACPI: (supports S0 S3 S4 S5)
[4294671.880000] Freeing unused kernel memory: 224k freed
[4294671.894000] vga16fb: initializing
[4294671.894000] vga16fb: mapped to 0xc00a0000
[4294672.033000] Console: switching to colour frame buffer device 80x30
[4294672.033000] fb0: VGA16 VGA frame buffer device
[4294672.053000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294673.166000] Capability LSM initialized
[4294673.177000] NET: Registered protocol family 1
[4294673.194000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294673.194000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294673.194000] ACPI: bus type ide registered
[4294673.199000] ICH6: IDE controller at PCI slot 0000:00:1f.1
[4294673.199000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[4294673.199000] ICH6: chipset revision 4
[4294673.199000] ICH6: not 100% native mode: will probe irqs later
[4294673.199000]     ide0: BM-DMA at 0x1810-0x1817, BIOS settings: hda:DMA, hdb:DMA
[4294673.199000] Probing IDE interface ide0...
[4294673.463000] hda: IC25N060ATMR04-0, ATA DISK drive
[4294674.177000] hdb: QSI CD-RW/DVD-ROM SBW242C, ATAPI CD/DVD-ROM drive
[4294674.228000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294674.228000] Probing IDE interface ide1...
[4294674.741000] Probing IDE interface ide2...
[4294675.253000] Probing IDE interface ide3...
[4294675.765000] Probing IDE interface ide4...
[4294676.277000] Probing IDE interface ide5...
[4294676.792000] hda: max request size: 1024KiB
[4294676.812000] hda: 117210240 sectors (60011 MB) w/7884KiB Cache, CHS=16383/255/63, UDMA(33)
[4294676.812000] hda: cache flushes supported
[4294676.812000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 p6 p7 p8 p9 p10 p11 >
[4294676.942000] hdb: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache
[4294676.942000] Uniform CD-ROM driver Revision: 3.20
[4294677.187000] Attempting manual resume
[4294677.209000] swsusp: Suspend partition has wrong signature?
[4294677.270000] usbcore: registered new driver usbfs
[4294677.270000] usbcore: registered new driver hub
[4294677.271000] USB Universal Host Controller Interface driver v2.2
[4294677.271000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23
[4294677.271000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[4294677.271000] uhci_hcd 0000:00:1d.0: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
[4294677.333000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[4294677.333000] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
[4294677.333000] hub 1-0:1.0: USB hub found
[4294677.333000] hub 1-0:1.0: 2 ports detected
[4294677.336000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[4294677.336000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[4294677.336000] uhci_hcd 0000:00:1d.1: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
[4294677.398000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[4294677.398000] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[4294677.398000] hub 2-0:1.0: USB hub found
[4294677.398000] hub 2-0:1.0: 2 ports detected
[4294677.401000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[4294677.401000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[4294677.401000] uhci_hcd 0000:00:1d.2: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
[4294677.463000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[4294677.463000] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[4294677.463000] hub 3-0:1.0: USB hub found
[4294677.463000] hub 3-0:1.0: 2 ports detected
[4294677.466000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[4294677.466000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[4294677.466000] uhci_hcd 0000:00:1d.3: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
[4294677.502000] usb 1-1: new low speed USB device using uhci_hcd and address 2
[4294677.528000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[4294677.528000] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
[4294677.528000] hub 4-0:1.0: USB hub found
[4294677.528000] hub 4-0:1.0: 2 ports detected
[4294677.565000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
[4294677.565000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[4294677.565000] ehci_hcd 0000:00:1d.7: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
[4294677.565000] ehci_hcd 0000:00:1d.7: debug port 1
[4294677.565000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[4294677.565000] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xb0040000
[4294677.569000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[4294677.569000] ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[4294677.569000] hub 5-0:1.0: USB hub found
[4294677.569000] hub 5-0:1.0: 8 ports detected
[4294677.682000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[4294677.682000] 8139cp: pci dev 0000:06:08.0 (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[4294677.682000] 8139cp: Try the "8139too" driver instead.
[4294677.683000] 8139too Fast Ethernet driver 0.9.27
[4294677.683000] ACPI: PCI Interrupt 0000:06:08.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294677.684000] eth0: RealTek RTL8139 at 0x4000, 00:c0:9f:a7:57:d5, IRQ 16
[4294677.684000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[4294677.984000] usb 1-1: device not accepting address 2, error -71
[4294678.502000] usb 1-1: new low speed USB device using uhci_hcd and address 4
[4294679.703000] usbcore: registered new driver hiddev
[4294679.721000] input: USB HID v1.10 Mouse [062a:0000] on usb-0000:00:1d.0-1
[4294679.721000] usbcore: registered new driver usbhid
[4294679.721000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
[4294680.098000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[4294680.098000] ACPI: Processor [CPU0] (supports 8 throttling states)
[4294680.100000] ACPI: Thermal Zone [THRM] (40 C)
[4294680.501000] Attempting manual resume
[4294680.512000] swsusp: Suspend partition has wrong signature?
[4294680.561000] kjournald starting.  Commit interval 5 seconds
[4294680.561000] EXT3-fs: mounted filesystem with ordered data mode.
[4294681.990000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294685.254000] Adding 939760k swap on /dev/hda9.  Priority:-1 extents:1
[4294685.539000] EXT3 FS on hda10, internal journal
[4294695.279000] parport: PnPBIOS parport detected.
[4294695.279000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[4294695.366000] lp0: using parport0 (interrupt-driven).
[4294695.400000] mice: PS/2 mouse device common for all mice
[4294695.455000] ieee1394: Initialized config rom entry `ip1394'
[4294695.465000] SCSI subsystem initialized
[4294695.471000] sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
[4294696.058000] Synaptics Touchpad, model: 1, fw: 5.10, id: 0x258eb1, caps: 0xa04713/0x0
[4294696.061000] input: SynPS/2 Synaptics TouchPad on isa0060/serio1
[4294696.303000] ts: Compaq touchscreen protocol output
[4294698.587000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4294699.614000] cdrom: open failed.
[4294700.684000] kjournald starting.  Commit interval 5 seconds
[4294700.684000] EXT3 FS on hda11, internal journal
[4294700.684000] EXT3-fs: mounted filesystem with ordered data mode.
[4294702.055000] Linux agpgart interface v0.101 (c) Dave Jones
[4294702.064000] agpgart: Detected an Intel 915GM Chipset.
[4294702.064000] agpgart: Detected 7932K stolen memory.
[4294702.099000] agpgart: AGP aperture is 256M @ 0xc0000000
[4294702.197000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294702.209000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294702.550000] hw_random hardware driver 1.0.0 loaded
[4294702.736000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 17 (level, low) -> IRQ 17
[4294702.736000] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[4294703.044000] intel8x0_measure_ac97_clock: measured 49594 usecs
[4294703.044000] intel8x0: clocking to 48000
[4294703.747000] Linux Kernel Card Services
[4294703.747000]   options:  [pci] [cardbus] [pm]
[4294703.760000] ACPI: PCI Interrupt 0000:06:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294703.760000] Yenta: CardBus bridge found at 0000:06:01.0 [17ff:058b]
[4294703.760000] Yenta: Using CSCINT to route CSC interrupts to PCI
[4294703.760000] Yenta: Routing CardBus interrupts to PCI
[4294703.760000] Yenta TI: socket 0000:06:01.0, mfunc 0x00a21b22, devctl 0x64
[4294703.981000] Yenta: ISA IRQ mask 0x0c78, PCI irq 16
[4294703.981000] Socket status: 30000006
[4294704.100000] ohci1394: $Rev: 1250 $ Ben Collins <bcollins@debian.org>
[4294704.100000] ACPI: PCI Interrupt 0000:06:01.2[A] -> GSI 16 (level, low) -> IRQ 16
[4294704.154000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[b8007000-b80077ff]  Max Packet=[2048]
[4294705.415000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00c09f00005ac7b0]
[4294707.377000] Real Time Clock Driver v1.12
[4294708.161000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
```

---

### Post by xyz on 2006-05-11
Hi-
I've found out over time that no sound may or may not mean card problem.
This link solved all my multimedia-related problems. So, who knows, it may help you,too:
[http://ubuntuforums.org/showthread.php?t=157589&highlight=patrick](http://ubuntuforums.org/showthread.php?t=157589&highlight=patrick)
Please do read the thread throuh as it's evolved.

I've got Intel as well.

You could also try
```
sudo alsamixer
``` in a console and, using your left/right-up/down arrows, make sure sound is on everywhere and sufficiently 'up'.

Also double-click on your sound icone to make sure that "Master, PCM and the likes of them" are checked (not red). It may be a trial-and-error thing.

---

### Post by CybaCowboy on 2006-05-11
If your system has two sound cards, Ubuntu often defaults to the on-board sound card...

Try selecting the appropriate sound card from Sound Preferences (System-->Preferences-->Sound).

---

### Post by NeoRc on 2006-05-11
[QUOTE=xyz]Also double-click on your sound icone to make sure that "Master, PCM and the likes of them" are checked (not red). It may be a trial-and-error thing.[/QUOTE]
Actually I do not understand what you mean "checked"?

[QUOTE=CybaCowboy]If your system has two sound cards, Ubuntu often defaults to the on-board sound card...
Try selecting the appropriate sound card from Sound Preferences (System-->Preferences-->Sound).[/QUOTE]
The default sound card in the System-->Preferences-->Sound is "Intel ICH6"

---

### Post by Sef on 2006-05-11
Did you install the codecs?

[http://www.gnu.org/gnu/thegnuproject.html]("http://www.gnu.org/gnu/thegnuproject.html")

---

### Post by NeoRc on 2006-05-11
[QUOTE=Sef]Did you install the codecs?

[http://www.gnu.org/gnu/thegnuproject.html]("http://www.gnu.org/gnu/thegnuproject.html")[/QUOTE]
Actually I don't mean there's no sound when I play a video or something like that. Even when I login, even when I adjust the volume manager, everything.

First time I install the Ubuntu on my laptop, I didn't care about the sound at all, for it had be configured well. Now, for some reason, I have changed my laptop, and everything seems changed. So I don't think it's a errors about the codecs or the multimedia player.

---

### Post by xyz on 2006-05-12
Hi NeoRc,

> Actually I do not understand what you mean "checked"?


Go Application>Sound&Video>Video Control
At this point, you'll see words like "Master,Headphone,PCM" and so on. Little red x may or may not appear there; try to click on the various red x to enable sound. Obviously, when you see red x, it means sound is disabled in that part.
Hope this helps.

---

### Post by jezjones on 2006-05-12
There are ongoing issues with this particular sound card. It was a new intel chip last year sometime and many new laptops have them.

I chased this problem for a couple of months with Breezy and there is no fix i have found. Some people have found that playing with volume controls makes it work, but i have not had any success myself.

Another thread either here or elsewhere said that it was the alsa drivers that were at fault and an upgrade to version 1.0.10 or higher is required.
I found this impossible. Alsa is the most unfriendly part of linux i have ever come across.

I was hoping that an upgraded alsa driver in Dapper would fix the problem but sadly not. I get  a popping sound when the alsa drvers start up on boot but nothing after that.

I have to say that i find it dissappointing that a major sound card from a major manufacturer is so difficult to make work. The many many layers of sound in linux on confuse the issue (ESD, Gstreamer, OSS, ALSA, JACK).
There is also very very little documentation on sound which deals with these.

Good luck, but don't hold your breath....

---

### Post by MrWizard on 2006-05-13
It looks like I have the same problem here.  I am in the process of upgrading my kernel to 2.6.17rc4 to see if that helps.  And I may try to get the latest alsa drivers as well.  This is on a Dell Dimension 4700, btw.

---

### Post by NeoRc on 2006-05-13
I found a website [http://www.linuxant.com/drivers/]("http://www.linuxant.com/drivers/"), and it contain the driver for the Conexant sound card. I download it, but cannot compile it successfully.

BTW, I tried some methods to fix my problem, but it caused a disaster. When I double-click the Volume Control button in the taskbar, it throw a dialog box said No volume control elements and/or devices found. Seems like I delete the sound device from the system by accident.

---

### Post by Sef on 2006-05-13
> I found a website [http://www.linuxant.com/drivers/](http://www.linuxant.com/drivers/), and it contain the driver for the Conexant sound card. I download it, but cannot compile it successfully.

To compile, build-essential needs to be installed.

sudo apt-get update

sudo apt-get install build-essential

> BTW, I tried some methods to fix my problem, but it caused a disaster. When I double-click the Volume Control button in the taskbar, it throw a dialog box said No volume control elements and/or devices found. Seems like I delete the sound device from the system by accident.

Try this, to get it back:

sudo apt-get update

sudo apt-get upgrade

---

### Post by NeoRc on 2006-05-14
[QUOTE=Sef]To compile, build-essential needs to be installed.

sudo apt-get update

sudo apt-get install build-essential
[/QUOTE]
I have install build-essential, so as the kernel source.
The error output is:
```
make[1]: Entering directory `/tmp/riptide-0.6lnxtbeta03122800/scripts'
install -m 755 ripconfig ripstop /usr/sbin
make[1]: Leaving directory `/tmp/riptide-0.6lnxtbeta03122800/scripts'
make[1]: Entering directory `/tmp/riptide-0.6lnxtbeta03122800/modules'
common.mak:11: *** Is the kernel-source package insfind sencetalled? KERNELSRC does not point to a proper directory (/lib/modules/2.6.12-10-386/build).  Stop.
make[1]: Leaving directory `/tmp/riptide-0.6lnxtbeta03122800/modules'
make: *** [install] Error 2
```
I searched /lib/modules/2.6.12-10-386/, didn't find directory "build". I also search the linux source in the /usr/src, but cannot find any sense.

[QUOTE=Sef]Try this, to get it back:

sudo apt-get update

sudo apt-get upgrade[/QUOTE]
I tried, but still cannot fix it

---

