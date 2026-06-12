---
title: "External Hard drive"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by sinisterman on 2007-12-22
Hello new user here just got a western digital passport external hard drive. I plugged it in but cannot figure out how to access it. thanks

---

### Post by PriceChild on 2007-12-22
Does it automount?

ie. do you see an icon appear on your desktop, the Places menu, or on the left bar in nautilus?

---

### Post by sinisterman on 2007-12-22
no I dont

---

### Post by taurus on 2007-12-22
See if you can mount it by hand from a terminal?  What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l <-- lower case letter l, not number 1
```

---

### Post by eternicode on 2007-12-22
Unplug the drive.  Open a terminal, then plug the drive back in.  Enter ```
dmesg | tail
``` into the terminal and press "Enter".  Post the output back here.

If it's not automounting (which I believe it should be), you'll have to mount it manually.

Edit@taurus: duh.  Why do I always forget fdisk??

---

### Post by sinisterman on 2007-12-22
Here it is

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9545    76670181   83  Linux
/dev/hda2            9546        9729     1477980    5  Extended
/dev/hda5            9546        9729     1477948+  82  Linux swap / Solaris

---

### Post by taurus on 2007-12-22
You did turn it on and plug it in to a USB port, right?

---

### Post by eternicode on 2007-12-22
> **sinisterman said:**
> Here it is

Is that the entire output?  If so, post your dmesg output...

---

### Post by sinisterman on 2007-12-22
Here it is, and yes is powered up.

[17179569.184000] Linux version 2.6.17-12-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Tue Dec 18 02:12:38 UTC 2007 (Ubuntu 2.6.17-12.42-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000ce000 - 00000000000d0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001f6e0000 (usable)
[17179569.184000]  BIOS-e820: 000000001f6e0000 - 000000001f6ec000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000001f6ec000 - 000000001f700000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000001f700000 - 0000000020000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec10000 - 00000000fec20000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ff800000 - 00000000ffc00000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 502MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 128736
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 124640 pages, LIFO batch:31
[17179569.184000] DMI present.
[17179569.184000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f67c0
[17179569.184000] ACPI: RSDT (v001 PTLTD  Montara  0x06040000  LTP 0x00000000) @ 0x1f6e5b60
[17179569.184000] ACPI: FADT (v001 INTEL  MONTARA  0x06040000 PTL  0x00000050) @ 0x1f6ebed2
[17179569.184000] ACPI: BOOT (v001 GATEWA 450ROG   0x06040000  LTP 0x00000001) @ 0x1f6ebfd8
[17179569.184000] ACPI: DSDT (v001 INTEL  MONTARAG 0x06040000 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec10000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (013fa000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[17179569.184000] Detected 1495.346 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179572.532000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179572.532000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179572.548000] Memory: 500832k/514944k available (1911k kernel code, 13548k reserved, 1073k data, 308k init, 0k highmem)
[17179572.548000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179572.628000] Calibrating delay using timer specific routine.. 2992.91 BogoMIPS (lpj=5985832)
[17179572.628000] Security Framework v1.0.0 initialized
[17179572.628000] SELinux:  Disabled at boot.
[17179572.628000] Mount-cache hash table entries: 512
[17179572.628000] CPU: After generic identify, caps: a7e9f9bf 00000000 00000000 00000000 00000180 00000000 00000000
[17179572.628000] CPU: After vendor identify, caps: a7e9f9bf 00000000 00000000 00000000 00000180 00000000 00000000
[17179572.628000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179572.628000] CPU: L2 cache: 1024K
[17179572.628000] CPU: After all inits, caps: a7e9f9bf 00000000 00000000 00000040 00000180 00000000 00000000
[17179572.628000] Checking 'hlt' instruction... OK.
[17179572.644000] SMP alternatives: switching to UP code
[17179572.644000] Freeing SMP alternatives: 16k freed
[17179572.644000] checking if image is initramfs... it is
[17179573.244000] Freeing initrd memory: 5327k freed
[17179573.244000] ACPI: Core revision 20060707
[17179573.244000] ACPI: Looking for DSDT ... not found!
[17179573.248000] ACPI: setting ELCR to 0200 (from 0c00)
[17179573.304000] CPU0: Intel(R) Pentium(R) M processor 1500MHz stepping 05
[17179573.304000] SMP motherboard not detected.
[17179573.304000] Local APIC not detected. Using dummy APIC emulation.
[17179573.304000] Brought up 1 CPUs
[17179573.304000] migration_cost=0
[17179573.304000] NET: Registered protocol family 16
[17179573.304000] EISA bus registered
[17179573.304000] ACPI: bus type pci registered
[17179573.308000] PCI: PCI BIOS revision 2.10 entry at 0xfd9c2, last bus=2
[17179573.308000] PCI: Using configuration type 1
[17179573.308000] Setting up standard PCI resources
[17179573.324000] ACPI: Interpreter enabled
[17179573.324000] ACPI: Using PIC for interrupt routing
[17179573.324000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179573.324000] PCI: Probing PCI hardware (bus 00)
[17179573.328000] Boot video device is 0000:00:02.0
[17179573.328000] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[17179573.328000] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[17179573.328000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179573.328000] PCI: Transparent bridge - 0000:00:1e.0
[17179573.328000] PCI: Bus #03 (-#06) is hidden behind transparent bridge #02 (-#02) (try 'pci=assign-busses')
[17179573.328000] Please report the result to linux-kernel to fix this permanently
[17179573.328000] PCI: Bus #07 (-#0a) is hidden behind transparent bridge #02 (-#02) (try 'pci=assign-busses')
[17179573.328000] Please report the result to linux-kernel to fix this permanently
[17179573.328000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179573.332000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[17179573.332000] ACPI: PCI Interrupt Link [LNKA] (IRQs *11)
[17179573.332000] ACPI: PCI Interrupt Link [LNKB] (IRQs *10)
[17179573.332000] ACPI: PCI Interrupt Link [LNKC] (IRQs *10)
[17179573.332000] ACPI: PCI Interrupt Link [LNKD] (IRQs 11) *10
[17179573.332000] ACPI: PCI Interrupt Link [LNKE] (IRQs *11)
[17179573.336000] ACPI: PCI Interrupt Link [LNKG] (IRQs *11)
[17179573.336000] ACPI: PCI Interrupt Link [LNKH] (IRQs *10)
[17179573.336000] ACPI: Embedded Controller [H_EC] (gpe 29) interrupt mode.
[17179573.340000] ACPI: Device [LPTB] status [0000000c]: functional but not present; setting present
[17179573.340000] ACPI: Power Resource [PFN0] (off)
[17179573.340000] ACPI: Power Resource [PFN1] (off)
[17179573.340000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179573.340000] pnp: PnP ACPI init
[17179573.344000] pnp: PnP ACPI: found 8 devices
[17179573.344000] PnPBIOS: Disabled by ACPI PNP
[17179573.348000] PCI: Using ACPI for IRQ routing
[17179573.348000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179573.352000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[17179573.352000] PCI: Bus 3, cardbus bridge: 0000:02:05.0
[17179573.352000]   IO window: 00003000-000030ff
[17179573.352000]   IO window: 00003400-000034ff
[17179573.352000]   PREFETCH window: 30000000-31ffffff
[17179573.352000]   MEM window: 36000000-37ffffff
[17179573.352000] PCI: Bus 7, cardbus bridge: 0000:02:05.1
[17179573.352000]   IO window: 00003800-000038ff
[17179573.352000]   IO window: 00003c00-00003cff
[17179573.352000]   PREFETCH window: 32000000-33ffffff
[17179573.352000]   MEM window: 38000000-39ffffff
[17179573.352000] PCI: Bridge: 0000:00:1e.0
[17179573.352000]   IO window: 3000-4fff
[17179573.352000]   MEM window: e0200000-e06fffff
[17179573.352000]   PREFETCH window: 30000000-33ffffff
[17179573.352000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179573.352000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[17179573.352000] PCI: setting IRQ 10 as level-triggered
[17179573.352000] ACPI: PCI Interrupt 0000:02:05.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[17179573.352000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[17179573.352000] ACPI: PCI Interrupt 0000:02:05.1[B] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[17179573.352000] NET: Registered protocol family 2
[17179573.392000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179573.392000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[17179573.392000] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[17179573.392000] TCP: Hash tables configured (established 16384 bind 8192)
[17179573.392000] TCP reno registered
[17179573.392000] Simple Boot Flag at 0x36 set to 0x1
[17179573.392000] audit: initializing netlink socket (disabled)
[17179573.392000] audit(1198356135.392:1): initialized
[17179573.392000] VFS: Disk quotas dquot_6.5.1
[17179573.392000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179573.392000] Initializing Cryptographic API
[17179573.392000] io scheduler noop registered
[17179573.392000] io scheduler anticipatory registered
[17179573.392000] io scheduler deadline registered
[17179573.392000] io scheduler cfq registered (default)
[17179573.392000] isapnp: Scanning for PnP cards...
[17179573.744000] isapnp: No Plug & Play device found
[17179573.776000] Real Time Clock Driver v1.12ac
[17179573.776000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179573.776000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179573.776000] 00:05: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179573.776000] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[17179573.776000] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[17179573.776000] mice: PS/2 mouse device common for all mice
[17179573.776000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179573.776000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179573.776000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179573.776000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179573.784000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179573.784000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179573.784000] EISA: Probing bus 0 at eisa.0
[17179573.784000] Cannot allocate resource for EISA slot 1
[17179573.784000] Cannot allocate resource for EISA slot 2
[17179573.784000] Cannot allocate resource for EISA slot 3
[17179573.784000] Cannot allocate resource for EISA slot 4
[17179573.784000] EISA: Detected 0 cards.
[17179573.784000] TCP bic registered
[17179573.784000] NET: Registered protocol family 1
[17179573.784000] NET: Registered protocol family 8
[17179573.784000] NET: Registered protocol family 20
[17179573.784000] Using IPI No-Shortcut mode
[17179573.784000] ACPI: (supports S0 S3 S4 S5)
[17179573.784000] Freeing unused kernel memory: 308k freed
[17179573.828000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179574.924000] Capability LSM initialized
[17179574.956000] ACPI: Transitioning device [FAN0] to D3
[17179574.956000] ACPI: Transitioning device [FAN0] to D3
[17179574.956000] ACPI: Fan [FAN0] (off)
[17179574.956000] ACPI: Transitioning device [FAN1] to D3
[17179574.956000] ACPI: Transitioning device [FAN1] to D3
[17179574.956000] ACPI: Fan [FAN1] (off)
[17179574.960000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[17179574.960000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179574.960000] ACPI: Thermal Zone [THRM] (34 C)
[17179575.248000] ICH4: IDE controller at PCI slot 0000:00:1f.1
[17179575.248000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[17179575.248000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[17179575.248000] ICH4: chipset revision 3
[17179575.248000] ICH4: not 100% native mode: will probe irqs later
[17179575.248000]     ide0: BM-DMA at 0x1810-0x1817, BIOS settings: hda:DMA, hdb:pio
[17179575.248000]     ide1: BM-DMA at 0x1818-0x181f, BIOS settings: hdc:DMA, hdd:pio
[17179575.248000] Probing IDE interface ide0...
[17179575.536000] hda: SAMSUNG HM080IC, ATA DISK drive
[17179576.208000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179576.300000] Probing IDE interface ide1...
[17179577.036000] hdc: UJDA755 DVD/CDRW, ATAPI CD/DVD-ROM drive
[17179577.708000] ide1 at 0x170-0x177,0x376 on irq 15
[17179577.716000] hda: max request size: 512KiB
[17179577.724000] hda: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
[17179577.724000] hda: cache flushes supported
[17179577.724000]  hda: hda1 hda2 < hda5 >
[17179577.868000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179577.868000] Uniform CD-ROM driver Revision: 3.20
[17179578.096000] usbcore: registered new driver usbfs
[17179578.096000] usbcore: registered new driver hub
[17179578.096000] USB Universal Host Controller Interface driver v3.0
[17179578.096000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[17179578.096000] PCI: setting IRQ 11 as level-triggered
[17179578.096000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179578.096000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179578.096000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179578.096000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179578.096000] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00001820
[17179578.096000] usb usb1: configuration #1 chosen from 1 choice
[17179578.096000] hub 1-0:1.0: USB hub found
[17179578.096000] hub 1-0:1.0: 2 ports detected
[17179578.168000] ieee1394: Initialized config rom entry `ip1394'
[17179578.200000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[17179578.200000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179578.200000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179578.200000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179578.200000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179578.200000] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001840
[17179578.200000] usb usb2: configuration #1 chosen from 1 choice
[17179578.200000] hub 2-0:1.0: USB hub found
[17179578.200000] hub 2-0:1.0: 2 ports detected
[17179578.304000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[17179578.304000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179578.304000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179578.304000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179578.304000] uhci_hcd 0000:00:1d.2: irq 10, io base 0x00001860
[17179578.304000] usb usb3: configuration #1 chosen from 1 choice
[17179578.304000] hub 3-0:1.0: USB hub found
[17179578.304000] hub 3-0:1.0: 2 ports detected
[17179578.408000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10
[17179578.408000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 10 (level, low) -> IRQ 10
[17179578.408000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179578.408000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179578.408000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[17179578.408000] ehci_hcd 0000:00:1d.7: debug port 1
[17179578.408000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[17179578.408000] ehci_hcd 0000:00:1d.7: irq 10, io mem 0xe0100000
[17179578.412000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179578.412000] usb usb4: configuration #1 chosen from 1 choice
[17179578.412000] hub 4-0:1.0: USB hub found
[17179578.412000] hub 4-0:1.0: 6 ports detected
[17179578.440000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[17179578.516000] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 11
[17179578.516000] ACPI: PCI Interrupt 0000:02:05.2[C] -> Link [LNKG] -> GSI 11 (level, low) -> IRQ 11
[17179578.576000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[11]  MMIO=[e0604000-e06047ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[17179578.624000] Attempting manual resume
[17179578.664000] kjournald starting.  Commit interval 5 seconds
[17179578.664000] EXT3-fs: mounted filesystem with ordered data mode.
[17179578.900000] usb 4-1: new high speed USB device using ehci_hcd and address 2
[17179579.032000] usb 4-1: configuration #1 chosen from 1 choice
[17179579.032000] hub 4-1:1.0: USB hub found
[17179579.032000] hub 4-1:1.0: 4 ports detected
[17179579.520000] usb 4-1.1: new low speed USB device using ehci_hcd and address 4
[17179579.616000] usb 4-1.1: configuration #1 chosen from 1 choice
[17179579.820000] usb 4-1.2: new high speed USB device using ehci_hcd and address 5
[17179579.856000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e0b80500008a79]
[17179579.912000] usb 4-1.2: configuration #1 chosen from 1 choice
[17179580.152000] usb 1-2: new low speed USB device using uhci_hcd and address 3
[17179580.400000] usb 1-2: configuration #1 chosen from 1 choice
[17179589.800000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179589.804000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179589.824000] hw_random: cannot enable RNG, aborting
[17179590.016000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x1c4cb1, caps: 0x80471b/0x0
[17179590.048000] input: SynPS/2 Synaptics TouchPad as /class/input/input1
[17179590.368000] Linux agpgart interface v0.101 (c) Dave Jones
[17179590.488000] agpgart: Detected an Intel 855 Chipset.
[17179590.488000] agpgart: Detected 8060K stolen memory.
[17179590.496000] agpgart: AGP aperture is 128M @ 0xe8000000
[17179590.680000] usbcore: registered new driver hiddev
[17179590.748000] input: Cypress Semi. RF Multimedia Keyboard/Mouse as /class/input/input2
[17179590.748000] input: USB HID v1.10 Keyboard [Cypress Semi. RF Multimedia Keyboard/Mouse] on usb-0000:00:1d.7-1.1
[17179590.792000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[17179590.792000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[17179590.816000] input: Cypress Semi. RF Multimedia Keyboard/Mouse as /class/input/input3
[17179590.816000] input: USB HID v1.10 Mouse [Cypress Semi. RF Multimedia Keyboard/Mouse] on usb-0000:00:1d.7-1.1
[17179590.836000] ieee80211_crypt: registered algorithm 'NULL'
[17179590.840000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[17179590.840000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17179590.880000] input:   USB Keyboard as /class/input/input4
[17179590.880000] input: USB HID v1.10 Keyboard [  USB Keyboard] on usb-0000:00:1d.0-2
[17179590.884000] e100: Intel(R) PRO/100 Network Driver, 3.5.10-k2-NAPI
[17179590.884000] e100: Copyright(c) 1999-2005 Intel Corporation
[17179590.900000] ts: Compaq touchscreen protocol output
[17179590.952000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq
[17179590.952000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[17179590.952000] Driver 'ipw2200' needs updating - please use bus_type methods
[17179590.972000] input:   USB Keyboard as /class/input/input5
[17179590.972000] input: USB HID v1.10 Device [  USB Keyboard] on usb-0000:00:1d.0-2
[17179590.972000] usbcore: registered new driver usbhid
[17179590.972000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179591.616000] intel8x0_measure_ac97_clock: measured 55476 usecs
[17179591.616000] intel8x0: clocking to 48000
[17179591.616000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[17179591.616000] ACPI: PCI Interrupt 0000:02:08.0[A] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
[17179591.636000] e100: eth0: e100_probe: addr 0xe0603000, irq 11, MAC addr 00:E0:B8:6D:3B:18
[17179591.640000] ACPI: PCI Interrupt 0000:02:05.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[17179591.640000] Yenta: CardBus bridge found at 0000:02:05.0 [107b:0500]
[17179591.768000] Yenta: ISA IRQ mask 0x00b8, PCI irq 10
[17179591.768000] Socket status: 30000006
[17179591.768000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[17179591.768000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x4fff
[17179591.768000] cs: IO port probe 0x3000-0x4fff: clean.
[17179591.768000] pcmcia: parent PCI bridge Memory window: 0xe0200000 - 0xe06fffff
[17179591.768000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[17179591.772000] ACPI: PCI Interrupt 0000:02:05.1[B] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[17179591.772000] Yenta: CardBus bridge found at 0000:02:05.1 [107b:0500]
[17179591.880000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[17179591.900000] Yenta: ISA IRQ mask 0x00b8, PCI irq 10
[17179591.900000] Socket status: 30000006
[17179591.900000] Yenta: Raising subordinate bus# of parent bus (#02) from #06 to #0a
[17179591.900000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x4fff
[17179591.900000] cs: IO port probe 0x3000-0x4fff: clean.
[17179591.900000] pcmcia: parent PCI bridge Memory window: 0xe0200000 - 0xe06fffff
[17179591.900000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[17179591.904000] ACPI: PCI Interrupt 0000:02:04.0[A] -> Link [LNKH] -> GSI 10 (level, low) -> IRQ 10
[17179591.908000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[17179592.124000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[17179592.504000] cs: IO port probe 0x100-0x3af: clean.
[17179592.504000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179592.504000] cs: IO port probe 0x820-0x8ff: clean.
[17179592.508000] cs: IO port probe 0xc00-0xcf7: clean.
[17179592.688000] cs: IO port probe 0x100-0x3af: clean.
[17179592.688000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179592.688000] cs: IO port probe 0x820-0x8ff: clean.
[17179592.692000] cs: IO port probe 0xc00-0xcf7: clean.
[17179592.924000] cs: IO port probe 0xa00-0xaff: clean.
[17179592.924000] cs: IO port probe 0xa00-0xaff: clean.
[17179592.968000] NET: Registered protocol family 17
[17179593.076000] lp: driver loaded but no devices found
[17179593.120000] SCSI subsystem initialized
[17179593.128000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179593.128000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179593.152000] Adding 1477940k swap on /dev/disk/by-uuid/d48fe78d-f9ad-403a-9950-ad446d9f68eb.  Priority:-1 extents:1 across:1477940k
[17179593.220000] EXT3 FS on hda1, internal journal
[17179593.788000] eth1: NETDEV_TX_BUSY returned; driver should report queue full via ieee_device->is_queue_full.
[17179593.984000] NET: Registered protocol family 10
[17179593.984000] lo: Disabled Privacy Extensions
[17179593.984000] IPv6 over IPv4 tunneling driver
[17179597.952000] ACPI: AC Adapter [ACAD] (on-line)
[17179598.064000] ACPI: Battery Slot [BAT1] (battery present)
[17179598.064000] ACPI: Battery Slot [BAT2] (battery absent)
[17179598.080000] ACPI: Power Button (FF) [PWRF]
[17179598.080000] ACPI: Lid Switch [LID0]
[17179598.080000] ACPI: Sleep Button (CM) [SLPB]
[17179598.120000] ACPI: Error installing notify handler
[17179598.256000] ibm_acpi: ec object not found
[17179598.284000] pcc_acpi: loading...
[17179598.420000] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[17179601.048000] [drm] Initialized drm 1.0.1 20051102
[17179601.052000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179601.052000] [drm] Initialized i915 1.5.0 20060119 on minor 0
[17179601.052000] [drm] Initialized i915 1.5.0 20060119 on minor 1
[17179602.172000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179602.172000] apm: overridden by ACPI.
[17179604.468000] eth0: no IPv6 routers present
[17179604.932000] eth1: no IPv6 routers present
[17179605.888000] Bluetooth: Core ver 2.8
[17179605.888000] NET: Registered protocol family 31
[17179605.888000] Bluetooth: HCI device and connection manager initialized
[17179605.888000] Bluetooth: HCI socket layer initialized
[17179605.948000] Bluetooth: L2CAP ver 2.8
[17179605.948000] Bluetooth: L2CAP socket layer initialized
[17179605.964000] Bluetooth: RFCOMM socket layer initialized
[17179605.964000] Bluetooth: RFCOMM TTY layer initialized
[17179605.964000] Bluetooth: RFCOMM ver 1.7
[17180575.456000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17180575.480000] ISOFS: changing to secondary root

---

### Post by sinisterman on 2007-12-22
Out put from dmesg | tail

[17183662.488000] usb 4-1.2: USB disconnect, address 5
[17183675.796000] usb 4-1.1: USB disconnect, address 4
[17183675.996000] usb 4-1.1: new low speed USB device using ehci_hcd and address 6
[17183676.092000] usb 4-1.1: configuration #1 chosen from 1 choice
[17183676.096000] input: Cypress Semi. RF Multimedia Keyboard/Mouse as /class/input/input6
[17183676.096000] input: USB HID v1.10 Keyboard [Cypress Semi. RF Multimedia Keyboard/Mouse] on usb-0000:00:1d.7-1.1
[17183676.104000] input: Cypress Semi. RF Multimedia Keyboard/Mouse as /class/input/input7
[17183676.104000] input: USB HID v1.10 Mouse [Cypress Semi. RF Multimedia Keyboard/Mouse] on usb-0000:00:1d.7-1.1
[17183682.396000] usb 4-1.2: new high speed USB device using ehci_hcd and address 7
[17183682.488000] usb 4-1.2: configuration #1 chosen from 1 choice

---

### Post by eternicode on 2007-12-22
Egads...

Sorry, I meant for you to refer back to this post...

> **eternicode said:**
> Unplug the drive.  Open a terminal, then plug the drive back in.  Enter ```
dmesg | tail
``` into the terminal and press "Enter".  Post the output back here.

If it's not automounting (which I believe it should be), you'll have to mount it manually.

Edit@taurus: duh.  Why do I always forget fdisk??

---

### Post by eternicode on 2007-12-22
> **sinisterman said:**
> 
[17183682.396000] usb 4-1.2: new high speed USB device using ehci_hcd and address 7
[17183682.488000] usb 4-1.2: configuration #1 chosen from 1 choice

Well, the system seems to be recognizing it...if "sudo fdisk -l" doesn't list it, I'm not sure what to do :(

---

### Post by sinisterman on 2007-12-22
is a restart required after the fdisk command

---

### Post by eternicode on 2007-12-22
No, "fdisk -l" is purely informational.  Though I suppose trying a reboot wouldn't hurt.  Doubt it'll do anything, though.

---

### Post by budluva04 on 2007-12-31
im having the same problem, it seems that the ext. hdd is being detected as HID (Human Interface Device) ie. keyboard/mouse, i have been scouring google/forums/irc for help and no one seems to have an answer yet....so...

---

