---
title: "[SOLVED] Boot errors and Proper uninstall of harddisks"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by zek725 on 2006-12-21
dmesg
> 
[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000000fffd000 (usable)
[17179569.184000]  BIOS-e820: 000000000fffd000 - 000000000ffff000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000000ffff000 - 0000000010000000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 255MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 65533
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 61437 pages, LIFO batch:15
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 ASUS                                  ) @ 0x000f5600
[17179569.184000] ACPI: RSDT (v001 ASUS   P3V133   0x30303031 MSFT 0x31313031) @ 0x0fffd000
[17179569.184000] ACPI: FADT (v001 ASUS   P3V133   0x30303031 MSFT 0x31313031) @ 0x0fffd080
[17179569.184000] ACPI: BOOT (v001 ASUS   P3V133   0x30303031 MSFT 0x31313031) @ 0x0fffd040
[17179569.184000] ACPI: DSDT (v001   ASUS P3V133   0x00001000 MSFT 0x0100000b) @ 0x00000000
[17179569.184000] ACPI: BIOS age (1999) fails cutoff (2000), acpi=force is required to enable ACPI
[17179569.184000] ACPI: acpi=force override
[17179569.184000] ACPI: PM-Timer IO Port: 0xe408
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 10000000:efff0000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda2 ro profile acpi=force lapic
[17179569.184000] Local APIC disabled by BIOS -- reenabling.
[17179569.184000] Found and enabled local APIC!
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[17179569.184000] Detected 601.434 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179571.536000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179571.536000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[17179571.572000] Memory: 250216k/262132k available (1910k kernel code, 11348k reserved, 1070k data, 308k init, 0k highmem)
[17179571.572000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179571.652000] Calibrating delay using timer specific routine.. 1204.34 BogoMIPS (lpj=2408695)
[17179571.652000] Security Framework v1.0.0 initialized
[17179571.652000] SELinux:  Disabled at boot.
[17179571.652000] Mount-cache hash table entries: 512
[17179571.652000] CPU: After generic identify, caps: 0383fbff 00000000 00000000 00000000 00000000 00000000 00000000
[17179571.652000] CPU: After vendor identify, caps: 0383fbff 00000000 00000000 00000000 00000000 00000000 00000000
[17179571.652000] CPU: L1 I cache: 16K, L1 D cache: 16K
[17179571.652000] CPU: L2 cache: 256K
[17179571.652000] CPU: After all inits, caps: 0383fbff 00000000 00000000 00000040 00000000 00000000 00000000
[17179571.652000] Checking 'hlt' instruction... OK.
[17179571.668000] SMP alternatives: switching to UP code
[17179571.668000] Freeing SMP alternatives: 16k freed
[17179571.668000] checking if image is initramfs... it is
[17179573.188000] Freeing initrd memory: 5318k freed
[17179573.188000] ACPI: Core revision 20060707
[17179573.188000] ACPI: Looking for DSDT ... not found!
[17179573.192000] ACPI: setting ELCR to 0200 (from 0c20)
[17179573.192000] CPU0: Intel Pentium III (Coppermine) stepping 01
[17179573.192000] SMP motherboard not detected.
[17179573.296000] Brought up 1 CPUs
[17179573.296000] migration_cost=0
[17179573.296000] NET: Registered protocol family 16
[17179573.296000] EISA bus registered
[17179573.296000] ACPI: bus type pci registered
[17179573.296000] PCI: PCI BIOS revision 2.10 entry at 0xf06a0, last bus=1
[17179573.296000] PCI: Using configuration type 1
[17179573.296000] Setting up standard PCI resources
[17179573.308000] ACPI: Interpreter enabled
[17179573.308000] ACPI: Using PIC for interrupt routing
[17179573.308000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[17179573.312000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179573.312000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[17179573.312000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[17179573.316000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179573.316000] PCI: Probing PCI hardware (bus 00)
[17179573.316000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179573.320000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:04.1
[17179573.320000] Boot video device is 0000:01:00.0
[17179573.320000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179573.336000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179573.336000] pnp: PnP ACPI init
[17179573.348000] pnp: PnP ACPI: found 14 devices
[17179573.348000] PnPBIOS: Disabled by ACPI PNP
[17179573.348000] PCI: Using ACPI for IRQ routing
[17179573.348000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179573.348000] pnp: 00:03: ioport range 0xe400-0xe47f could not be reserved
[17179573.348000] pnp: 00:03: ioport range 0xe800-0xe80f has been reserved
[17179573.348000] pnp: 00:03: ioport range 0x290-0x297 has been reserved
[17179573.352000] PCI: Bridge: 0000:00:01.0
[17179573.352000]   IO window: disabled.
[17179573.352000]   MEM window: d6000000-d7efffff
[17179573.352000]   PREFETCH window: d7f00000-e3ffffff
[17179573.352000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179573.352000] NET: Registered protocol family 2
[17179573.388000] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[17179573.388000] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[17179573.388000] TCP bind hash table entries: 4096 (order: 3, 32768 bytes)
[17179573.388000] TCP: Hash tables configured (established 8192 bind 4096)
[17179573.388000] TCP reno registered
[17179573.388000] Simple Boot Flag at 0x3a set to 0x1
[17179573.388000] audit: initializing netlink socket (disabled)
[17179573.388000] audit(1166787918.388:1): initialized
[17179573.392000] VFS: Disk quotas dquot_6.5.1
[17179573.392000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179573.392000] Initializing Cryptographic API
[17179573.392000] io scheduler noop registered
[17179573.392000] io scheduler anticipatory registered
[17179573.392000] io scheduler deadline registered
[17179573.392000] io scheduler cfq registered (default)
[17179573.392000] Activating ISA DMA hang workarounds.
[17179573.392000] isapnp: Scanning for PnP cards...
[17179573.748000] isapnp: No Plug & Play device found
[17179573.828000] Real Time Clock Driver v1.12ac
[17179573.828000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179573.828000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179573.828000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179573.832000] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179573.832000] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179573.832000] mice: PS/2 mouse device common for all mice
[17179573.836000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179573.836000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179573.836000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179573.836000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179573.840000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179573.840000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179573.840000] EISA: Probing bus 0 at eisa.0
[17179573.840000] EISA: Detected 0 cards.
[17179573.844000] TCP bic registered
[17179573.844000] NET: Registered protocol family 1
[17179573.844000] NET: Registered protocol family 8
[17179573.844000] NET: Registered protocol family 20
[17179573.844000] Using IPI No-Shortcut mode
[17179573.844000] ACPI: (supports S0 S1 S4 S5)
[17179573.844000] Freeing unused kernel memory: 308k freed
[17179574.508000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179574.656000] Capability LSM initialized
[17179574.776000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[17179576.092000] VP_IDE: IDE controller at PCI slot 0000:00:04.1
[17179576.092000] VP_IDE: chipset revision 6
[17179576.092000] VP_IDE: not 100% native mode: will probe irqs later
[17179576.092000] VP_IDE: VIA vt82c596b (rev 12) IDE UDMA66 controller on pci0000:00:04.1
[17179576.092000]     ide0: BM-DMA at 0xd800-0xd807, BIOS settings: hda:DMA, hdb:pio
[17179576.092000]     ide1: BM-DMA at 0xd808-0xd80f, BIOS settings: hdc:pio, hdd:pio
[17179576.092000] Probing IDE interface ide0...
[17179576.512000] hda: ST340015A, ATA DISK drive
[17179577.184000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179577.184000] Probing IDE interface ide1...
[17179582.640000] hdc: IRQ probe failed (0xffffbcf8)
[17179587.864000] hdc: IRQ probe failed (0xffffbcf8)
[17179587.864000] hdc: no response (status = 0x0a), resetting drive
[17179593.208000] hdc: IRQ probe failed (0xffffbcf8)
[17179593.208000] hdc: no response (status = 0x0a)
[17179598.720000] hdd: IRQ probe failed (0xffffbcf8)
[17179603.944000] hdd: IRQ probe failed (0xffffbcf8)
[17179603.944000] hdd: no response (status = 0x0a), resetting drive
[17179609.280000] hdd: IRQ probe failed (0xffffbcf8)
[17179609.280000] hdd: no response (status = 0x0a)
[17179609.352000] hda: max request size: 128KiB
[17179609.356000] hda: 78165360 sectors (40020 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(33)
[17179609.356000] hda: cache flushes supported
[17179609.356000]  hda: hda1 hda2 hda3 < hda5 >
[17179609.764000] Probing IDE interface ide1...
[17179644.756000] ide1: Wait for ready failed before probe !
[17179644.844000] usbcore: registered new driver usbfs
[17179644.848000] usbcore: registered new driver hub
[17179644.856000] USB Universal Host Controller Interface driver v3.0
[17179644.856000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 5
[17179644.856000] PCI: setting IRQ 5 as level-triggered
[17179644.856000] ACPI: PCI Interrupt 0000:00:04.2[D] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[17179644.856000] uhci_hcd 0000:00:04.2: UHCI Host Controller
[17179644.860000] uhci_hcd 0000:00:04.2: new USB bus registered, assigned bus number 1
[17179644.860000] uhci_hcd 0000:00:04.2: irq 5, io base 0x0000d400
[17179644.860000] usb usb1: configuration #1 chosen from 1 choice
[17179644.860000] hub 1-0:1.0: USB hub found
[17179644.860000] hub 1-0:1.0: 2 ports detected
[17179645.336000] usb 1-2: new low speed USB device using uhci_hcd and address 2
[17179645.512000] usb 1-2: configuration #1 chosen from 1 choice
[17179645.544000] usbcore: registered new driver hiddev
[17179645.584000] input: CHESEN USB Keyboard as /class/input/input1
[17179645.584000] input: USB HID v1.10 Keyboard [CHESEN USB Keyboard] on usb-0000:00:04.2-2
[17179645.612000] input: CHESEN USB Keyboard as /class/input/input2
[17179645.616000] input: USB HID v1.10 Device [CHESEN USB Keyboard] on usb-0000:00:04.2-2
[17179645.616000] usbcore: registered new driver usbhid
[17179645.616000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179650.284000] hdc: IRQ probe failed (0xffffbcd8)
[17179655.512000] hdc: IRQ probe failed (0xffffbcd8)
[17179655.512000] hdc: no response (status = 0x0a), resetting drive
[17179660.848000] hdc: IRQ probe failed (0xffffbcd8)
[17179660.848000] hdc: no response (status = 0x0a)
[17179666.352000] hdd: IRQ probe failed (0xffffbcd8)
[17179671.576000] hdd: IRQ probe failed (0xffffbcd8)
[17179671.576000] hdd: no response (status = 0x0a), resetting drive
[17179676.912000] hdd: IRQ probe failed (0xffffbcd8)
[17179676.912000] hdd: no response (status = 0x0a)
[17179677.012000] Attempting manual resume
[17179677.060000] EXT3-fs: INFO: recovery required on readonly filesystem.
[17179677.060000] EXT3-fs: write access will be enabled during recovery.
[17179680.280000] kjournald starting.  Commit interval 5 seconds
[17179680.280000] EXT3-fs: recovery complete.
[17179680.308000] EXT3-fs: mounted filesystem with ordered data mode.
[17179742.408000] input: PC Speaker as /class/input/input3
[17179743.212000] Linux agpgart interface v0.101 (c) Dave Jones
[17179743.308000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179743.320000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179743.360000] agpgart: Detected VIA Apollo Pro 133 chipset
[17179743.364000] agpgart: AGP aperture is 64M @ 0xe4000000
[17179743.424000] logips2pp: Detected unknown logitech mouse model 1
[17179743.468000] 8139too Fast Ethernet driver 0.9.27
[17179743.468000] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[17179743.468000] eth0: RealTek RTL8139 at 0xd0882000, 00:50:ba:5a:f1:fb, IRQ 5
[17179743.468000] eth0:  Identified 8139 chip type 'RTL-8139C'
[17179743.904000] input: PS/2 Logitech Mouse as /class/input/input4
[17179744.628000] Floppy drive(s): fd0 is 1.44M
[17179744.664000] parport: PnPBIOS parport detected.
[17179744.664000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[17179744.664000] FDC 0 is a post-1991 82077
[17179745.140000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[17179745.140000] PCI: setting IRQ 10 as level-triggered
[17179745.140000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[17179746.648000] ts: Compaq touchscreen protocol output
[17179748.024000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[17179749.148000] NET: Registered protocol family 17
[17179749.532000] lp0: using parport0 (interrupt-driven).
[17179749.596000] fuse init (API version 7.6)
[17179750.080000] Adding 2899692k swap on /dev/disk/by-uuid/5282dabd-1f94-4e5a-8b6a-d58749f9a45d.  Priority:-1 extents:1 across:2899692k
[17179750.776000] EXT3 FS on hda2, internal journal
[17179754.396000] NET: Registered protocol family 10
[17179754.400000] lo: Disabled Privacy Extensions
[17179754.400000] IPv6 over IPv4 tunneling driver
[17179765.380000] eth0: no IPv6 routers present
[17179779.496000] ACPI: Power Button (FF) [PWRF]
[17179779.496000] ACPI: Power Button (CM) [PWRB]
[17179779.984000] ibm_acpi: ec object not found
[17179780.084000] pcc_acpi: loading...
[17179792.460000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179792.460000] apm: overridden by ACPI.


I believe this is the cause of my boot lag. I've removed hdc and hdd from the automount. why is it still looking for them? How do I fix this? Should I remove the IDE cable completely?

---

### Post by kidders on 2006-12-22
Hi there,

Your system will probe any hardware connected to it during boot. If you want to ignore some hard disks, the simplest thing to do is disable them in your BIOS.

---

### Post by zek725 on 2006-12-22
> **kidders said:**
> Hi there,

Your system will probe any hardware connected to it during boot. If you want to ignore some hard disks, the simplest thing to do is disable them in your BIOS.

i've already disabled them in BIOS. i somehow fixed this by reattaching the CDROM (hdc). It worked past that "probe" but it takes a while when CHECKING FILE SYSTEM.

---

### Post by kidders on 2006-12-23
Hmmmm... I know this is a dumb thing to say, but are you *certain* you've turned off your secondary IDE controller? If it's not enabled, Ubuntu simply shouldn't see it ... unless of course there's something odd about the way your BIOS does things. :-k

**Edit:** Another way of doing the same thing would be to unplug the devices themselves, as you suggested in your op.

---

### Post by zek725 on 2006-12-23
> **kidders said:**
> Hmmmm... I know this is a dumb thing to say, but are you *certain* you've turned off your secondary IDE controller? If it's not enabled, Ubuntu simply shouldn't see it ... unless of course there's something odd about the way your BIOS does things. :-k

yes. i've already set it from Auto to NONE.

---

### Post by kidders on 2006-12-23
Hmmm... I wonder if that's enough. I'm not so sure. :-k Will your BIOS not let you disable the entire controller, rather than just telling it not to autodetect any connected devices?

It's an odd problem ... I'm sorry I can't offer anything more constructive.

---

### Post by zek725 on 2006-12-23
> **kidders said:**
> Hmmm... I wonder if that's enough. I'm not so sure. :-k Will your BIOS not let you disable the entire controller, rather than just telling it not to autodetect any connected devices?

It's an odd problem ... I'm sorry I can't offer anything more constructive.

and how do you do that?

---

### Post by kidders on 2006-12-23
That depends on your motherboard.

---

### Post by zek725 on 2006-12-23
> **kidders said:**
> That depends on your motherboard.

Thanks. I'll see what I can do.

---

### Post by Scorpuk on 2006-12-23
If you are nto happy playing around with the bios then your best option is to physically disconnect the drives data and power cables.

---

### Post by zek725 on 2006-12-23
> **Scorpuk said:**
> If you are nto happy playing around with the bios then your best option is to physically disconnect the drives data and power cables.

Yes. that's what i did. My "probe" woes were fixed when I reattached the cd drive into hdc. Then it no longer probes for hdd (which a fat32 hdd used to be connected). :D 

Was it supposed to happen (my problem, that is)? Well, then, I guess my box has started to become unreliable. :-k Maybe an update would do. It has been a while since I last updated this. :rolleyes:

Another solution I've come up with so that it will stop probing when there's no hardware connected:

In the Terminal: ```
sudo nano /etc/boot/grub/menu.lst
```
Look for the **kernel** line and append **ide1=noprobe**. 

The culprit, in my case, was *ide1* (secondary; ide0 is the primary). 
hda -> primary master
hdb -> primary slave
hdc -> secondary master
hdd -> secondary slave

---

