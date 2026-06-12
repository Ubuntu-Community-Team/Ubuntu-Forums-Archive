---
title: "help!@!@! with sound card"
date: 2006-05-29
forum: Absolute Beginner Talk
---

### Post by newhen on 2006-05-29
Hi, Im trying to use skype and it says problem with sound card I'm not sure what sound card i have **shoulkd i open up the back of my comp to check?** here is the lspci results:```
admin@defualt:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
0000:00:01.0 PCI bridge: Intel Corp. 82845 845 (Brookdale) Chipset AGP Bridge (rev 04)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 05)
0000:00:1f.0 ISA bridge: Intel Corp. 82801BA ISA Bridge (LPC) (rev 05)
0000:00:1f.1 IDE interface: Intel Corp. 82801BA IDE U100 ([rev 05)
0000:00:1f.2 USB Controller: Intel Corp. 82801BA/BAM USB (Hub #1) (rev 05)
0000:00:1f.3 SMBus: Intel Corp. 82801BA/BAM SMBus (rev 05)
0000:00:1f.4 USB Controller: Intel Corp. 82801BA/BAM USB (Hub #2) (rev 05)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
0000:02:08.0 Ethernet controller: Intel Corp. 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)
0000:02:09.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
0000:02:0a.0 Modem: Broadcom Corporation BCM4212 v.90 56k modem
admin@defualt:~$

```
and i thought this might be helpfull too dmesg :```
admin@defualt:~$ dmesg
0
[4294667.296000] ACPI: FADT (v001 GATEWA PT84510A 0x20011205 MSFT 0x00001011) @ 0x0fff1000
[4294667.296000] ACPI: MADT (v001 GATEWA PT84510A 0x20011205 MSFT 0x00001011) @ 0x0ffe360f
[4294667.296000] ACPI: SSDT (v001 GATEWA PT84510A 0x00000001 MSFT 0x0100000b) @ 0x0ffe3677
[4294667.296000] ACPI: DSDT (v001 GATEWA PT84510A 0x00000002 MSFT 0x0100000b) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x408
[4294667.296000] ACPI: Local APIC address 0xfee00000
[4294667.296000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[4294667.296000] Processor #0 15:1 APIC version 20
[4294667.296000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] disabled)
[4294667.296000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[4294667.296000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[4294667.296000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[4294667.296000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[4294667.296000] ACPI: IRQ0 used by override.
[4294667.296000] ACPI: IRQ2 used by override.
[4294667.296000] ACPI: IRQ9 used by override.
[4294667.296000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[4294667.296000] Using ACPI (MADT) for SMP configuration information
[4294667.296000] Allocating PCI resources starting at 10000000 (gap: 10000000:eec00000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda1 ro quiet splash
[4294667.296000] mapped APIC to ffffd000 (fee00000)
[4294667.296000] mapped IOAPIC to ffffc000 (fec00000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 1024 (order: 10, 16384 bytes)
[4294667.296000] Detected 1794.865 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294670.212000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)[4294670.212000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[4294670.221000] Memory: 251012k/261888k available (1416k kernel code, 10284k reserved, 762k data, 224k init, 0k highmem)
[4294670.221000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294670.221000] Calibrating delay loop... 3555.32 BogoMIPS (lpj=1777664)
[4294670.243000] Security Framework v1.0.0 initialized
[4294670.243000] SELinux:  Disabled at boot.
[4294670.243000] Mount-cache hash table entries: 512
[4294670.243000] CPU: After generic identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000
[4294670.243000] CPU: After vendor identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000
[4294670.243000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[4294670.243000] CPU: L2 cache: 256K
[4294670.243000] CPU: After all inits, caps: 3febfbff 00000000 00000000 00000080 00000000 00000000 00000000
[4294670.243000] CPU: Intel(R) Pentium(R) 4 CPU 1.80GHz stepping 02
[4294670.243000] Enabling fast FPU save and restore... done.
[4294670.243000] Enabling unmasked SIMD FPU exception support... done.
[4294670.243000] Checking 'hlt' instruction... OK.
[4294670.247000] Checking for popad bug... OK.
[4294670.247000] checking if image is initramfs... it is
[4294670.908000] Freeing initrd memory: 5164k freed
[4294670.908000] ACPI: Looking for DSDT in initrd... not found!
[4294670.971000]  not found!
[4294670.981000] ENABLING IO-APIC IRQs
[4294670.981000] ..TIMER: vector=0x31 pin1=2 pin2=-1
[4294671.092000] NET: Registered protocol family 16
[4294671.092000] EISA bus registered
[4294671.092000] ACPI: bus type pci registered
[4294671.092000] PCI: PCI BIOS revision 2.10 entry at 0xfda95, last bus=2
[4294671.092000] PCI: Using configuration type 1
[4294671.092000] mtrr: v2.0 (20020519)
[4294671.093000] ACPI: Subsystem revision 20050729
[4294671.101000] ACPI: Interpreter enabled
[4294671.101000] ACPI: Using IOAPIC for interrupt routing
[4294671.102000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294671.102000] PCI: Probing PCI hardware (bus 00)
[4294671.102000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[4294671.105000] Boot video device is 0000:01:00.0
[4294671.106000] PCI: Transparent bridge - 0000:00:1e.0
[4294671.107000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294671.107000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[4294671.109000] ACPI: Power Resource [FDDP] (off)
[4294671.109000] ACPI: Power Resource [URP1] (off)
[4294671.110000] ACPI: Power Resource [URP2] (off)
[4294671.110000] ACPI: Power Resource [LPTP] (off)
[4294671.112000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[4294671.112000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[4294671.112000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[4294671.113000] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[4294671.113000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[4294671.113000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[4294671.114000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[4294671.114000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[4294671.114000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294671.114000] pnp: PnP ACPI init
[4294671.118000] pnp: PnP ACPI: found 11 devices
[4294671.118000] PnPBIOS: Disabled by ACPI PNP
[4294671.118000] PCI: Using ACPI for IRQ routing
[4294671.118000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294671.123000] audit: initializing netlink socket (disabled)
[4294671.123000] audit: initialized
[4294671.123000] VFS: Disk quotas dquot_6.5.1
[4294671.123000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294671.123000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294671.123000] devfs: boot_options: 0x0
[4294671.123000] Initializing Cryptographic API
[4294671.124000] isapnp: Scanning for PnP cards...
[4294671.480000] isapnp: No Plug & Play device found
[4294671.507000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[4294671.510000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294671.510000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294671.510000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
[4294671.510000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294671.514000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294671.514000] ACPI: PCI Interrupt 0000:02:0a.0[A] -> GSI 22 (level, low) -> IRQ 22
[4294671.514000] io scheduler noop registered
[4294671.514000] io scheduler anticipatory registered
[4294671.514000] io scheduler deadline registered
[4294671.514000] io scheduler cfq registered
[4294671.515000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294671.515000] EISA: Probing bus 0 at eisa.0
[4294671.515000] EISA: Detected 0 cards.
[4294671.515000] NET: Registered protocol family 2
[4294671.524000] IP: routing cache hash table of 2048 buckets, 16Kbytes
[4294671.524000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[4294671.524000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[4294671.524000] TCP: Hash tables configured (established 16384 bind 16384)
[4294671.524000] NET: Registered protocol family 8
[4294671.524000] NET: Registered protocol family 20
[4294671.524000] ACPI wakeup devices:
[4294671.524000] PBTN PCI1 UAR1  USB USB2  AC9  SMB
[4294671.524000] ACPI: (supports S0 S1 S3 S4 S5)
[4294671.525000] Freeing unused kernel memory: 224k freed
[4294671.554000] vga16fb: initializing
[4294671.554000] vga16fb: mapped to 0xc00a0000
[4294671.711000] Console: switching to colour frame buffer device 80x30
[4294671.711000] fb0: VGA16 VGA frame buffer device
[4294671.815000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294672.867000] Capability LSM initialized
[4294672.886000] NET: Registered protocol family 1
[4294672.905000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294672.905000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294672.905000] ACPI: bus type ide registered
[4294672.916000] ICH2: IDE controller at PCI slot 0000:00:1f.1
[4294672.916000] ICH2: chipset revision 5
[4294672.916000] ICH2: not 100% native mode: will probe irqs later
[4294672.916000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pio
[4294672.916000]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:DMA
[4294672.916000] Probing IDE interface ide0...
[4294673.180000] hda: MAXTOR 6L040J2, ATA DISK drive
[4294673.792000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294673.792000] Probing IDE interface ide1...
[4294674.464000] hdc: HL-DT-STDVD-ROM GDR8160B, ATAPI CD/DVD-ROM drive
[4294675.178000] hdd: LITE-ON LTR-16102B, ATAPI CD/DVD-ROM drive
[4294675.229000] ide1 at 0x170-0x177,0x376 on irq 15
[4294675.229000] Probing IDE interface ide2...
[4294675.742000] Probing IDE interface ide3...
[4294676.254000] Probing IDE interface ide4...
[4294676.766000] Probing IDE interface ide5...
[4294677.284000] hda: max request size: 128KiB
[4294677.295000] hda: 78177792 sectors (40027 MB) w/1819KiB Cache, CHS=65535/16/63, UDMA(100)
[4294677.295000] hda: cache flushes supported
[4294677.295000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
[4294677.339000] hdc: ATAPI 48X DVD-ROM drive, 512kB Cache
[4294677.339000] Uniform CD-ROM driver Revision: 3.20
[4294677.349000] hdd: ATAPI 40X CD-ROM CD-R/RW drive, 2048kB Cache
[4294678.122000] Attempting manual resume
[4294678.127000] swsusp: Suspend partition has wrong signature?
[4294678.192000] usbcore: registered new driver usbfs
[4294678.192000] usbcore: registered new driver hub
[4294678.193000] USB Universal Host Controller Interface driver v2.2
[4294678.193000] ACPI: PCI Interrupt 0000:00:1f.2[D] -> GSI 19 (level, low) -> IRQ 19
[4294678.193000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[4294678.193000] uhci_hcd 0000:00:1f.2: Intel Corporation 82801BA/BAM USB (Hub #1)
[4294678.255000] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[4294678.255000] uhci_hcd 0000:00:1f.2: irq 19, io base 0x0000ef40
[4294678.255000] hub 1-0:1.0: USB hub found
[4294678.255000] hub 1-0:1.0: 2 ports detected
[4294678.258000] ACPI: PCI Interrupt 0000:00:1f.4[C] -> GSI 23 (level, low) -> IRQ 23
[4294678.258000] PCI: Setting latency timer of device 0000:00:1f.4 to 64
[4294678.258000] uhci_hcd 0000:00:1f.4: Intel Corporation 82801BA/BAM USB (Hub #2)
[4294678.320000] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 2
[4294678.320000] uhci_hcd 0000:00:1f.4: irq 23, io base 0x0000ef80
[4294678.320000] hub 2-0:1.0: USB hub found
[4294678.320000] hub 2-0:1.0: 2 ports detected
[4294678.366000] e100: Intel(R) PRO/100 Network Driver, 3.4.8-k2-NAPI
[4294678.366000] e100: Copyright(c) 1999-2005 Intel Corporation
[4294678.366000] ACPI: PCI Interrupt 0000:02:08.0[A] -> GSI 20 (level, low) -> IRQ 20
[4294678.390000] e100: eth0: e100_probe: addr 0xfeaff000, irq 20, MAC addr 00:03:47:D3:24:5B
[4294678.452000] usb 1-2: new low speed USB device using uhci_hcd and address 2
[4294678.741000] usb 2-2: new full speed USB device using uhci_hcd and address 2[4294678.824000] hub 2-2:1.0: USB hub found
[4294678.826000] hub 2-2:1.0: 4 ports detected
[4294680.435000] usbcore: registered new driver hiddev
[4294680.452000] input: USB HID v1.10 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1f.2-2
[4294680.452000] usbcore: registered new driver usbhid
[4294680.452000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
[4294681.359000] ACPI: CPU0 (power states: C1[C1])
[4294681.562000] Attempting manual resume
[4294681.562000] swsusp: Suspend partition has wrong signature?
[4294681.592000] kjournald starting.  Commit interval 5 seconds
[4294681.592000] EXT3-fs: mounted filesystem with ordered data mode.
[4294682.847000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294687.209000] Adding 746980k swap on /dev/hda5.  Priority:-1 extents:1
[4294687.480000] EXT3 FS on hda1, internal journal
[4294693.816000] parport: PnPBIOS parport detected.
[4294693.817000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[4294693.903000] lp0: using parport0 (interrupt-driven).
[4294693.958000] mice: PS/2 mouse device common for all mice
[4294697.353000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4294698.293000] cdrom: open failed.
[4294698.297000] cdrom: open failed.
[4294701.025000] Linux agpgart interface v0.101 (c) Dave Jones
[4294701.039000] agpgart: Detected an Intel i845 Chipset.
[4294701.068000] agpgart: AGP aperture is 64M @ 0xf8000000
[4294701.404000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294701.423000] shpchp: shpc_init : shpc_cap_offset == 0
[4294701.423000] shpchp: shpc_init : shpc_cap_offset == 0
[4294701.423000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294701.599000] hw_random hardware driver 1.0.0 loaded
[4294702.379000] ath_hal: module license 'Proprietary' taints kernel.
[4294702.386000] ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413)
[4294702.395000] wlan: 0.8.6.0 (EXPERIMENTAL)
[4294702.402000] ath_rate_sample: 1.2
[4294702.415000] ath_pci: 0.9.6.0 (EXPERIMENTAL)
[4294702.421000] ACPI: PCI Interrupt 0000:02:09.0[A] -> GSI 21 (level, low) -> IRQ 21
[4294702.702000] Build date: Nov 22 2005
[4294702.702000] Debugging version (IEEE80211)
[4294702.702000] ath0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[4294702.703000] ath0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[4294702.703000] ath0: H/W encryption support: WEP AES AES_CCM TKIP
[4294702.703000] ath0: mac 5.6 phy 4.1 radio 1.7
[4294702.703000] ath0: Use hw queue 1 for WME_AC_BE traffic
[4294702.703000] ath0: Use hw queue 0 for WME_AC_BK traffic
[4294702.703000] ath0: Use hw queue 2 for WME_AC_VI traffic
[4294702.703000] ath0: Use hw queue 3 for WME_AC_VO traffic
[4294702.703000] ath0: Use hw queue 8 for CAB traffic
[4294702.703000] ath0: Use hw queue 9 for beacons
[4294702.703000] Debugging version (ATH)
[4294702.703000] ath0: Atheros 5212: mem=0xfeae0000, irq=21
[4294704.357000] Real Time Clock Driver v1.12
[4294704.411000] input: PC Speaker
[4294704.815000] Floppy drive(s): fd0 is 1.44M
[4294704.829000] FDC 0 is a post-1991 82077
[4294705.706000] ts: Compaq touchscreen protocol output
[4294706.552000] NET: Registered protocol family 17
[4294798.264000] ACPI: Power Button (FF) [PWRF]
[4294798.264000] ACPI: Power Button (CM) [PBTN]
[4294798.437000] ibm_acpi: ec object not found
[4294805.843000] apm: BIOS not found.
[4294808.143000] Bluetooth: Core ver 2.7
[4294808.143000] NET: Registered protocol family 31
[4294808.143000] Bluetooth: HCI device and connection manager initialized
[4294808.143000] Bluetooth: HCI socket layer initialized
[4294808.164000] Bluetooth: L2CAP ver 2.7
[4294808.164000] Bluetooth: L2CAP socket layer initialized
[4294808.205000] Bluetooth: RFCOMM ver 1.5
[4294808.205000] Bluetooth: RFCOMM socket layer initialized
[4294808.205000] Bluetooth: RFCOMM TTY layer initialized
[4294840.928000] NET: Registered protocol family 10
[4294840.929000] Disabled Privacy Extensions on device c02eb280(lo)
[4294840.929000] IPv6 over IPv4 tunneling driver
[4294851.005000] ath0: no IPv6 routers present
[4294851.105000] eth0: no IPv6 routers present
[4295271.580000] ibm_acpi: ec object not found
[4295286.673000] ath0: no IPv6 routers present
admin@defualt:~$
admin@defualt:~$

```
if anybody knows anythinbg about this stuff please reply Im also avilble on AIM newhen222 and skype if i can get it running

---

### Post by newhen on 2006-05-29
bump

---

### Post by nalmeth on 2006-05-29
What output does skype give you with the error? Do you have another app using sound at the same time?

---

### Post by newhen on 2006-05-29
my sound card is soundblaster live ! also Im not useing anything other then skype it says problem with sound hardware! Its deftitly something with that>

---

