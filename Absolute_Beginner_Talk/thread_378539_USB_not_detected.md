---
title: "USB not detected"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by yankeereaper on 2007-03-07
Hello all: I'm new to Ubuntu, not new to Linux. I currently run Fedora6 on my Desktop.
Anyway, I just installed Ubuntu 6.10 on a Toshiba laptop. The distro does not recognize my USB mouse, also when I plug in my camera it also is not recognized. I know the ports work and the cables are good. Any good places to start? I'll send the dmesg report later today, it basically says to check the cable? Fedora has had no problems with the USB ports. Thanks in advance, yankeereaper...

---

### Post by francesco44 on 2007-03-07
I have exactly the same problem with Edgy 6.10 on a thinkpad X30...I posted the same question...but never received an answer...maybe if we join our efforts...

---

### Post by schwascore on 2007-03-07
Plug the devices in and run the command lsusb in a terminal.  Post the output and/or let us know if anything shows up.  It should look something like this:

```
josh@sexybeast:~$ lsusb 
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 03f0:7304 Hewlett-Packard DeskJet 35xx
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 04f9:0028 Brother Industries, Ltd 
Bus 002 Device 001: ID 0000:0000  
```

If your devices are plugged in and you do not see anything listed (Like my two printers listed above),  then your usb devices are inaccessible.  If your output does show devices, then it is probably a matter of finding the right drivers or figuring out how to tell Ubuntu that the devices are there.

---

### Post by yankeereaper on 2007-03-08
Hello schwascore: I only have the usb mouse installed, there are no devices showing in the lsusb command. I seem to remember seeing something about the kernel, installing a different kernel than the one provided with the distro? Any ideas? Thanks in advance. yankeereaper....:confused:

---

### Post by schwascore on 2007-03-08
Are you saying that you installed a different kernel?  If so, how did you install it - did it come from the repositories or did you get it somewhere else?  Right now I'd have to guess that the problem is that Ubuntu isn't working with your Toshiba USB hardware.  I did a quick Google search for the problem and found that this problem is somewhat common, depending on which laptop series you are using.  We also need to see if your USB controllers are recognized.  Run lspci in a terminal.  Output should look a little like this:
```
josh@sexybeast:~$ lspci 
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)

```

If you see USB controllers somewhere in your lspci output, that's a good sign.  If not, then the kernel is not recognizing your hardware at all.  Let us know what you find.

---

### Post by yankeereaper on 2007-03-08
Hello schwascore:  Here's the output of the lspci command, it appears to show usb ( 3 ) of them. Oh, I did not attempt to change my kernel. I hope that will a last resort move. I really appreciate the help. Always, yankee reaper.  :) 








johnp@johnp-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
01:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 33)

---

### Post by yankeereaper on 2007-03-09
Hello all: After some searching on the web (google) I took another look at dmesg. Here's the result:
[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e0000 - 00000000000eee00 (reserved)
[17179569.184000]  BIOS-e820: 00000000000eee00 - 00000000000ef000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000000ef000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000002ef40000 (usable)
[17179569.184000]  BIOS-e820: 000000002ef40000 - 000000002ef50000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000002ef50000 - 000000002f000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec10000 - 00000000fec20000 (reserved)
[17179569.184000]  BIOS-e820: 00000000feda0000 - 00000000fedc0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffb00000 - 00000000ffc00000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffe80000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 751MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 192320
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 188224 pages, LIFO batch:31
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 TOSHIB                                ) @ 0x000f0180
[17179569.184000] ACPI: RSDT (v001 TOSHIB 750      0x00970814 TASM 0x04010000) @ 0x2ef40000
[17179569.184000] ACPI: FADT (v002 TOSHIB 750      0x20030101 TASM 0x04010000) @ 0x2ef40060
[17179569.184000] ACPI: SSDT (v001 TOSHIB A000C    0x20030917 MSFT 0x0100000e) @ 0x2ef402ca
[17179569.184000] ACPI: DBGP (v001 TOSHIB 750      0x00970814 TASM 0x04010000) @ 0x2ef400e4
[17179569.184000] ACPI: BOOT (v001 TOSHIB 750      0x00970814 TASM 0x04010000) @ 0x2ef40038
[17179569.184000] ACPI: MADT (v001 TOSHIB 750      0x00970814 TASM 0x04010000) @ 0x2ef40118
[17179569.184000] ACPI: DSDT (v001 TOSHIB A000C    0x20031216 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0xd808
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:2 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 2f000000:cfc00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[17179569.184000] Detected 2793.521 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179571.060000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179571.060000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179571.080000] Memory: 752616k/769280k available (1910k kernel code, 16156k reserved, 1070k data, 308k init, 0k highmem)
[17179571.080000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179571.160000] Calibrating delay using timer specific routine.. 5592.13 BogoMIPS (lpj=11184277)
[17179571.160000] Security Framework v1.0.0 initialized
[17179571.160000] SELinux:  Disabled at boot.
[17179571.160000] Mount-cache hash table entries: 512
[17179571.160000] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[17179571.160000] CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[17179571.160000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[17179571.160000] CPU: L2 cache: 128K
[17179571.160000] CPU: Hyper-Threading is disabled
[17179571.160000] CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 00004400 00000000 00000000
[17179571.160000] Checking 'hlt' instruction... OK.
[17179571.176000] SMP alternatives: switching to UP code
[17179571.176000] Freeing SMP alternatives: 16k freed
[17179571.176000] checking if image is initramfs... it is
[17179571.660000] Freeing initrd memory: 5563k freed
[17179571.660000] ACPI: Core revision 20060707
[17179571.660000] ACPI: Looking for DSDT ... not found!
[17179571.660000] ACPI: System reset via FADT Reset Register is supported
[17179571.660000] machine_reset = acpi_machine_reset
[17179571.660000] CPU0: Intel(R) Celeron(R) CPU 2.80GHz stepping 09
[17179571.660000] Total of 1 processors activated (5592.13 BogoMIPS).
[17179571.660000] ENABLING IO-APIC IRQs
[17179571.660000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179571.804000] Brought up 1 CPUs
[17179571.804000] migration_cost=0
[17179571.804000] NET: Registered protocol family 16
[17179571.804000] EISA bus registered
[17179571.804000] ACPI: bus type pci registered
[17179571.804000] PCI: PCI BIOS revision 2.10 entry at 0xfd2fe, last bus=3
[17179571.804000] PCI: Using configuration type 1
[17179571.804000] Setting up standard PCI resources
[17179571.804000] ACPI: Interpreter enabled
[17179571.804000] ACPI: Using IOAPIC for interrupt routing
[17179571.808000] ACPI: PCI Interrupt Link [LNKA] (IRQs *10)
[17179571.808000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *11)
[17179571.808000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *11)
[17179571.808000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *11)
[17179571.808000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *11)
[17179571.808000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *11)
[17179571.808000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *11)
[17179571.808000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *11)
[17179571.812000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179571.812000] PCI: Probing PCI hardware (bus 00)
[17179571.812000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179571.812000] Boot video device is 0000:00:02.0
[17179571.812000] PCI quirk: region d800-d87f claimed by ICH4 ACPI/GPIO/TCO
[17179571.812000] PCI quirk: region eec0-eeff claimed by ICH4 GPIO
[17179571.812000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179571.812000] PCI: Transparent bridge - 0000:00:1e.0
[17179571.812000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179571.816000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[17179571.820000] ACPI: Power Resource [PFAN] (off)
[17179571.824000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179571.824000] pnp: PnP ACPI init
[17179571.832000] pnp: PnP ACPI: found 10 devices
[17179571.832000] PnPBIOS: Disabled by ACPI PNP
[17179571.832000] PCI: Using ACPI for IRQ routing
[17179571.832000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179571.832000] PCI: Cannot allocate resource region 4 of device 0000:00:1d.0
[17179571.832000] PCI: Cannot allocate resource region 4 of device 0000:00:1d.1
[17179571.836000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[17179571.836000] PCI: Bus 2, cardbus bridge: 0000:01:0b.0
[17179571.836000]   IO window: 0000c000-0000c0ff
[17179571.836000]   IO window: 0000c400-0000c4ff
[17179571.836000]   PREFETCH window: 38000000-39ffffff
[17179571.836000]   MEM window: 3c000000-3dffffff
[17179571.836000] PCI: Bridge: 0000:00:1e.0
[17179571.836000]   IO window: c000-cfff
[17179571.836000]   MEM window: cff00000-cfffffff
[17179571.836000]   PREFETCH window: 38000000-39ffffff
[17179571.836000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179571.836000] PCI: Enabling device 0000:01:0b.0 (0000 -> 0003)
[17179571.836000] ACPI: PCI Interrupt 0000:01:0b.0[A] -> GSI 18 (level, low) -> IRQ 169
[17179571.836000] NET: Registered protocol family 2
[17179571.876000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179571.876000] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[17179571.876000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[17179571.876000] TCP: Hash tables configured (established 131072 bind 65536)
[17179571.876000] TCP reno registered
[17179571.876000] Simple Boot Flag at 0x7c set to 0x1
[17179571.876000] audit: initializing netlink socket (disabled)
[17179571.876000] audit(1173453081.876:1): initialized
[17179571.880000] VFS: Disk quotas dquot_6.5.1
[17179571.880000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179571.880000] Initializing Cryptographic API
[17179571.880000] io scheduler noop registered
[17179571.880000] io scheduler anticipatory registered
[17179571.880000] io scheduler deadline registered
[17179571.880000] io scheduler cfq registered (default)
[17179571.880000] isapnp: Scanning for PnP cards...
[17179572.232000] isapnp: No Plug & Play device found
[17179572.328000] Real Time Clock Driver v1.12ac
[17179572.328000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179572.328000] PCI: Enabling device 0000:00:1f.6 (0000 -> 0001)
[17179572.328000] ACPI: PCI Interrupt 0000:00:1f.6[B] -> GSI 17 (level, low) -> IRQ 177
[17179572.328000] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[17179572.328000] mice: PS/2 mouse device common for all mice
[17179572.332000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179572.332000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179572.332000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179572.332000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179572.344000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179572.344000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179572.348000] EISA: Probing bus 0 at eisa.0
[17179572.348000] Cannot allocate resource for EISA slot 1
[17179572.348000] EISA: Detected 0 cards.
[17179572.348000] TCP bic registered
[17179572.348000] NET: Registered protocol family 1
[17179572.348000] NET: Registered protocol family 8
[17179572.348000] NET: Registered protocol family 20
[17179572.348000] Using IPI No-Shortcut mode
[17179572.348000] ACPI: (supports S0 S3 S4 S5)
[17179572.348000] Freeing unused kernel memory: 308k freed
[17179572.388000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179573.472000] Capability LSM initialized
[17179573.524000] ACPI: Transitioning device [FAN] to D3
[17179573.524000] ACPI: Transitioning device [FAN] to D3
[17179573.524000] ACPI: Fan [FAN] (off)
[17179573.532000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[17179573.532000] ACPI: Thermal Zone [THRM] (19 C)
[17179574.268000] ICH4: IDE controller at PCI slot 0000:00:1f.1
[17179574.268000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 169
[17179574.268000] ICH4: chipset revision 3
[17179574.268000] ICH4: not 100% native mode: will probe irqs later
[17179574.268000]     ide0: BM-DMA at 0xbfa0-0xbfa7, BIOS settings: hda:DMA, hdb:pio
[17179574.268000]     ide1: BM-DMA at 0xbfa8-0xbfaf, BIOS settings: hdc:DMA, hdd:pio
[17179574.268000] Probing IDE interface ide0...
[17179574.560000] hda: FUJITSU MHV2100AT, ATA DISK drive
[17179575.236000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179575.312000] Probing IDE interface ide1...
[17179576.104000] hdc: TOSHIBA DVD-ROM SD-R2412, ATAPI CD/DVD-ROM drive
[17179576.800000] ide1 at 0x170-0x177,0x376 on irq 15
[17179576.820000] hda: max request size: 512KiB
[17179576.832000] hda: 195371568 sectors (100030 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
[17179576.836000] hda: cache flushes supported
[17179576.836000]  hda: hda1 hda2 < hda5 >
[17179576.920000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179576.920000] Uniform CD-ROM driver Revision: 3.20
[17179577.228000] usbcore: registered new driver usbfs
[17179577.228000] usbcore: registered new driver hub
[17179577.228000] USB Universal Host Controller Interface driver v3.0
[17179577.228000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 185
[17179577.228000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179577.228000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179577.232000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179577.232000] uhci_hcd 0000:00:1d.0: irq 185, io base 0x000018c0
[17179577.232000] usb usb1: configuration #1 chosen from 1 choice
[17179577.232000] hub 1-0:1.0: USB hub found
[17179577.232000] hub 1-0:1.0: 2 ports detected
[17179577.340000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 193
[17179577.340000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179577.340000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179577.340000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179577.340000] uhci_hcd 0000:00:1d.1: irq 193, io base 0x000018e0
[17179577.340000] usb usb2: configuration #1 chosen from 1 choice
[17179577.340000] hub 2-0:1.0: USB hub found
[17179577.340000] hub 2-0:1.0: 2 ports detected
[17179577.448000] PCI: Enabling device 0000:00:1d.7 (0000 -> 0002)
[17179577.448000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 201
[17179577.448000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179577.448000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179577.448000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 3
[17179577.448000] ehci_hcd 0000:00:1d.7: debug port 1
[17179577.448000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[17179577.448000] ehci_hcd 0000:00:1d.7: irq 201, io mem 0x3a080000
[17179577.452000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179577.476000] usb usb3: configuration #1 chosen from 1 choice
[17179577.476000] hub 3-0:1.0: USB hub found
[17179577.476000] hub 3-0:1.0: 6 ports detected
[17179577.624000] Attempting manual resume
[17179577.676000] kjournald starting.  Commit interval 5 seconds
[17179577.676000] EXT3-fs: mounted filesystem with ordered data mode.
[17179578.084000] usb 1-2: new low speed USB device using uhci_hcd and address 2
[17179578.272000] usb 1-2: configuration #1 chosen from 1 choice
[17179591.308000] Linux agpgart interface v0.101 (c) Dave Jones
[17179591.312000] agpgart: Detected an Intel 855 Chipset.
[17179591.312000] agpgart: Detected 16252K stolen memory.
[17179591.320000] agpgart: AGP aperture is 128M @ 0xd8000000
[17179591.368000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179591.376000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179591.452000] hw_random: RNG not detected
[17179591.652000] input: PC Speaker as /class/input/input1
[17179591.940000] pnp: Device 00:09 activated.
[17179591.940000] parport: PnPBIOS parport detected.
[17179591.940000] pnp: Device 00:09 disabled.
[17179592.084000] ACPI: PCI Interrupt 0000:01:0b.0[A] -> GSI 18 (level, low) -> IRQ 169
[17179592.084000] Yenta: CardBus bridge found at 0000:01:0b.0 [1179:0001]
[17179592.248000] Yenta: ISA IRQ mask 0x0cb8, PCI irq 169
[17179592.248000] Socket status: 30000007
[17179592.248000] pcmcia: parent PCI bridge I/O window: 0xc000 - 0xcfff
[17179592.248000] cs: IO port probe 0xc000-0xcfff: clean.
[17179592.248000] pcmcia: parent PCI bridge Memory window: 0xcff00000 - 0xcfffffff
[17179592.248000] pcmcia: parent PCI bridge Memory window: 0x38000000 - 0x39ffffff
[17179592.308000] e100: Intel(R) PRO/100 Network Driver, 3.5.10-k2-NAPI
[17179592.308000] e100: Copyright(c) 1999-2005 Intel Corporation
[17179592.308000] ACPI: PCI Interrupt 0000:01:08.0[A] -> GSI 20 (level, low) -> IRQ 209
[17179592.332000] e100: eth0: e100_probe: addr 0xcffff000, irq 209, MAC addr 00:08:0D:E7:D7:CA
[17179592.336000] input: PS/2 Mouse as /class/input/input2
[17179592.392000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input3
[17179592.496000] ts: Compaq touchscreen protocol output
[17179592.552000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[17179592.568000] PCI: Enabling device 0000:00:1f.5 (0000 -> 0003)
[17179592.568000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 177
[17179592.568000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[17179592.684000] usbcore: registered new driver hiddev
[17179592.704000] input: Cypress Sem PS2/USB Browser Combo Mouse as /class/input/input4
[17179592.704000] input: USB HID v1.00 Mouse [Cypress Sem PS2/USB Browser Combo Mouse] on usb-0000:00:1d.0-2
[17179592.704000] usbcore: registered new driver usbhid
[17179592.704000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179593.148000] cs: IO port probe 0x100-0x3af: excluding 0x1e0-0x1e7
[17179593.148000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179593.148000] cs: IO port probe 0x820-0x8ff: clean.
[17179593.148000] cs: IO port probe 0xc00-0xcf7: clean.
[17179593.148000] cs: IO port probe 0xa00-0xaff: clean.
[17179593.392000] intel8x0_measure_ac97_clock: measured 55377 usecs
[17179593.392000] intel8x0: clocking to 48000
[17179593.564000] lp: driver loaded but no devices found
[17179593.620000] Adding 2216928k swap on /dev/disk/by-uuid/ff717922-dcca-413f-8d4a-a7d2bee6ead5.  Priority:-1 extents:1 across:2216928k
[17179593.632000] NET: Registered protocol family 17
[17179593.716000] EXT3 FS on hda1, internal journal
[17179597.640000] NET: Registered protocol family 10
[17179597.640000] lo: Disabled Privacy Extensions
[17179597.640000] IPv6 over IPv4 tunneling driver
[17179600.128000] ACPI: AC Adapter [ADP1] (on-line)
[17179600.164000] ACPI: Battery Slot [BAT1] (battery present)
[17179600.184000] ACPI: Power Button (FF) [PWRF]
[17179600.184000] ACPI: Lid Switch [LID]
[17179600.184000] ACPI: Power Button (CM) [PWRB]
[17179600.372000] ibm_acpi: ec object not found
[17179600.400000] pcc_acpi: loading...
[17179600.492000] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.19a-dev
[17179600.492000] toshiba_acpi:     HCI method: \_SB_.VALZ.GHCI
[17179600.492000] toshiba_acpi: Toshiba hotkeys are sent as ACPI events
[17179600.492000] toshiba_acpi: ktoshkeyd will check 2 times per second
[17179600.492000] toshiba_acpi: Dropped 0 keys from the queue on startup
[17179600.512000] ACPI: Video Device [VGA] (multi-head: yes  rom: yes  post: no)
[17179600.832000] acpi-cpufreq: CPU0 - ACPI performance management activated.
[17179603.012000] [drm] Initialized drm 1.0.1 20051102
[17179603.016000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 185
[17179603.016000] [drm] Initialized i915 1.5.0 20060119 on minor 0
[17179603.020000] PCI: Enabling device 0000:00:02.1 (0000 -> 0002)
[17179603.020000] [drm] Initialized i915 1.5.0 20060119 on minor 1
[17179604.504000] apm: BIOS not found.
[17179607.508000] usb 1-2: USB disconnect, address 2
[17179607.760000] eth0: no IPv6 routers present
[17179609.264000] Bluetooth: Core ver 2.8
[17179609.264000] NET: Registered protocol family 31
[17179609.264000] Bluetooth: HCI device and connection manager initialized
[17179609.264000] Bluetooth: HCI socket layer initialized
[17179609.320000] Bluetooth: L2CAP ver 2.8
[17179609.320000] Bluetooth: L2CAP socket layer initialized
[17179609.360000] Bluetooth: RFCOMM socket layer initialized
[17179609.360000] Bluetooth: RFCOMM TTY layer initialized
[17179609.360000] Bluetooth: RFCOMM ver 1.7
[17179652.736000] hub 1-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[17179663.516000] hub 1-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[17179681.420000] hub 1-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[17179688.168000] hub 1-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[17179692.052000] hub 1-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[17179720.472000] hub 1-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[17179756.256000] hub 1-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?


I hope that results will help! Thanks yankeereaper:)

---

