---
title: "Broken internet connections w/ Ubuntu"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by acoluthus on 2007-07-08
Dear All-
Thank you for being here; whenever I run into something I check as many posts as possible. This is my first note in the system.
I have: a 7 year old iMac OS9.+ and it's just getting too old to connect to sites like my bank, ebay, etc. I've recently been given a nicely loaded, three year old ShuttleXP running newer, better drive, memory, ram, etc. than the iMac.  I'm desiring to make the switch but have been significantly discouraged by my linux experience thus far. *the Shuttle was a gift; I still don't even know how to view/list the components to see what Ram, Memory, etc. is actually inside it...

For internet: I swap my cable modem line from the Mac to the Shuttle XP to try it, but when on the PC-Linux (not partitioned, all Ubuntu) I get SO many broken connections it's beyond frustrating.  It took a half hour to keep pulling up my hotmail account to read 5 messages and reply to one message.  On the mac; not an issue. It's rare when I get a broken connection.

I tried to update the linux today and nothing loaded up; it was all broken connections.

Also: I took a break off trying to learn Ubuntu for  a while and forgot all password/userid info; it took hours to get that to reset. I tried at least 4 or 5 suggestions on these forums but got stuck every time (even from the CDRom didn't work). Obviously the last one worked and here I am back again.

I've bought the books, read them cover to cover, done some homework  to decide that Ubuntu was the one for my minimal usage (websurf/email/photo/ebay- no games or not much interactive chat/etc.) but  the broken connections really waste -hours- of time. 

I've shouted at my ISP; they say it's fine.  The router is a couple of years old; I"m willing to get another router that is line-based/ no wireless anymore in case we've got people tapping in (condensed urban area-it happens a lot here). I run linux with the Connection Properties window and System Monitor windows open just to see what's happening.

But: I still don't understand why a 7year old Mac can hold the same connections better than a 3year old loaded/higher equipped PC?

Someone/anyone: I still barely know the terminologies, so please, with recommendations, please spell it out for a low-tech person/ step by step..

Graciously appreciated,
A.C.

Thanks much.

---

### Post by Rebeca on 2007-07-15
I would suggest you take a look at: [https://help.ubuntu.com/community/InternetHowto](https://help.ubuntu.com/community/InternetHowto)

And, if that link doesn't point you to the information you need or if you'd like more help, then open the terminal  (Applications > Accesories > Terminal) and post the results that you get after typing each of the following commands: 

```
dmesg
``` 
```
uname -a
```
```
lsb_release -a
```

---

### Post by Bartender on 2007-07-15
Are you unplugging the router for a minute before plugging in a different PC?  I know almost nothing about networking but found out the hard way that you can't just jack PC's in and out.  Something about addresses.  The router expects the computer to be at a certain address or something like that.
I'm probably wrong on this, but it's worth a try.  Unplug the router, don't just switch it off.  Unplugging it clears the addresses.  Then plug your Linux PC in, turn on the router, then turn on the PC.

---

### Post by Rebeca on 2007-07-16
If he did use a router, why would he need to unplug his connection? He could have both computers connected at the same time, no?

Either way, he needs to give us more information for us to give him any useful advice.

---

### Post by acoluthus on 2007-07-29
Dear All- 
thanks for your communications; I've run the tests/terminal info; no clue what it says/means.. as an alternative, i thought I'd try another browser: this reply is going through my Linux computer (I"ve not plugged the ethernet back into the mac ; just linux connections, still many broken/delayed) Initially I've been using FIrefox as browser, this message run through Epiphany; it seems a bit faster, though I can't successfully log into my bank at all or read e-mails on MSN without several attempts; if any success at all.
Thank you for your continued assistance.
Sincerely, 
A. C.

Results from: uname -a
Linux dave-desktop 2.6.17-11-generic #2 SMP Fri May 18 23:39:08 UTC 2007 i686 GNU/Linux

Results from: lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 6.10
Release:        6.10
Codename:       edgy

---

### Post by acoluthus on 2007-07-29
Results from :  dmesg

[17179569.184000] Linux version 2.6.17-11-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri May 18 23:39:08 UTC 2007 (Ubuntu 2.6.17-11.38-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 0000000000097400 (usable)
[17179569.184000]  BIOS-e820: 0000000000097400 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000003f7f0000 (usable)
[17179569.184000]  BIOS-e820: 000000003f7f0000 - 000000003f7f3000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000003f7f3000 - 000000003f800000 (ACPI data)
[17179569.184000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[17179569.184000] 119MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f5700
[17179569.184000] On node 0 totalpages: 260080
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 30704 pages, LIFO batch:7
[17179569.184000] DMI 2.2 present.
[17179569.184000] ACPI: RSDP (v000 XPC                                   ) @ 0x000f9300
[17179569.184000] ACPI: RSDT (v001 XPC    AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3f7f3040
[17179569.184000] ACPI: FADT (v001 XPC    AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3f7f30c0
[17179569.184000] ACPI: MCFG (v001 XPC    AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3f7f7440
[17179569.184000] ACPI: MADT (v001 XPC    AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3f7f7340
[17179569.184000] ACPI: DSDT (v001 XPC     SB86V10 0x00001000 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x408
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:4 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[17179569.184000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[17179569.184000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 40000000 (gap: 3f800000:a0800000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/sda1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[17179569.184000] Detected 3074.333 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.520000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179569.520000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.540000] Memory: 1021420k/1040320k available (1911k kernel code, 18040k reserved, 1073k data, 308k init, 122816k highmem)
[17179569.540000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.620000] Calibrating delay using timer specific routine.. 6155.39 BogoMIPS (lpj=12310795)
[17179569.620000] Security Framework v1.0.0 initialized
[17179569.620000] SELinux:  Disabled at boot.
[17179569.620000] Mount-cache hash table entries: 512
[17179569.620000] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000651d 00000000 00000000
[17179569.620000] CPU: After vendor identify, caps: bfebfbff 20100000 00000000 00000000 0000651d 00000000 00000000
[17179569.620000] monitor/mwait feature present.
[17179569.620000] using mwait in idle threads.
[17179569.620000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[17179569.620000] CPU: L2 cache: 256K
[17179569.620000] CPU: Hyper-Threading is disabled
[17179569.620000] CPU: After all inits, caps: bfebfbff 20100000 00000000 00000180 0000651d 00000000 00000000
[17179569.620000] Checking 'hlt' instruction... OK.
[17179569.636000] SMP alternatives: switching to UP code
[17179569.636000] Freeing SMP alternatives: 16k freed
[17179569.636000] checking if image is initramfs... it is
[17179570.056000] Freeing initrd memory: 5327k freed
[17179570.056000] ACPI: Core revision 20060707
[17179570.064000] ACPI: Looking for DSDT ... not found!
[17179570.068000] CPU0: Intel(R) Celeron(R) CPU 3.06GHz stepping 09
[17179570.068000] Total of 1 processors activated (6155.39 BogoMIPS).
[17179570.068000] ENABLING IO-APIC IRQs
[17179570.068000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179570.212000] Brought up 1 CPUs
[17179570.212000] migration_cost=0
[17179570.212000] NET: Registered protocol family 16
[17179570.212000] EISA bus registered
[17179570.212000] ACPI: bus type pci registered
[17179570.212000] PCI: Using MMCONFIG
[17179570.212000] Setting up standard PCI resources
[17179570.232000] ACPI: Interpreter enabled
[17179570.232000] ACPI: Using IOAPIC for interrupt routing
[17179570.232000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.232000] PCI: Probing PCI hardware (bus 00)
[17179570.236000] Boot video device is 0000:00:02.0
[17179570.236000] PCI quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[17179570.236000] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[17179570.236000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179570.236000] PCI: Transparent bridge - 0000:00:1e.0
[17179570.236000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.248000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[17179570.248000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[17179570.252000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 11 *12 14 15)
[17179570.252000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[17179570.252000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[17179570.256000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[17179570.256000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[17179570.256000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[17179570.256000] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[17179570.256000] ACPI: PCI Interrupt Link [LNK1] (IRQs *3 4 5 7 9 10 11 12 14 15)
[17179570.256000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.256000] pnp: PnP ACPI init
[17179570.260000] pnp: PnP ACPI: found 14 devices
[17179570.260000] PnPBIOS: Disabled by ACPI PNP
[17179570.260000] PCI: Using ACPI for IRQ routing
[17179570.260000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.260000] pnp: 00:0a: ioport range 0x400-0x4bf could not be reserved
[17179570.260000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[17179570.260000] PCI: Bridge: 0000:00:1c.0
[17179570.260000]   IO window: c000-cfff
[17179570.260000]   MEM window: d0000000-d00fffff
[17179570.260000]   PREFETCH window: 40000000-400fffff
[17179570.260000] PCI: Bridge: 0000:00:1e.0
[17179570.260000]   IO window: d000-dfff
[17179570.260000]   MEM window: d0100000-d01fffff
[17179570.260000]   PREFETCH window: 40100000-401fffff
[17179570.260000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179570.260000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179570.260000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179570.260000] NET: Registered protocol family 2
[17179570.300000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179570.300000] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[17179570.300000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[17179570.300000] TCP: Hash tables configured (established 131072 bind 65536)
[17179570.300000] TCP reno registered
[17179570.300000] audit: initializing netlink socket (disabled)
[17179570.300000] audit(1185631402.300:1): initialized
[17179570.300000] highmem bounce pool size: 64 pages
[17179570.300000] VFS: Disk quotas dquot_6.5.1
[17179570.300000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.300000] Initializing Cryptographic API
[17179570.300000] io scheduler noop registered
[17179570.300000] io scheduler anticipatory registered
[17179570.300000] io scheduler deadline registered
[17179570.300000] io scheduler cfq registered (default)
[17179570.300000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179570.300000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179570.300000] assign_interrupt_mode Found MSI capability
[17179570.300000] Allocate Port Service[0000:00:1c.0:pcie00]
[17179570.300000] Allocate Port Service[0000:00:1c.0:pcie02]
[17179570.300000] Allocate Port Service[0000:00:1c.0:pcie03]
[17179570.300000] isapnp: Scanning for PnP cards...
[17179570.652000] isapnp: No Plug & Play device found
[17179570.700000] Real Time Clock Driver v1.12ac
[17179570.700000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179570.700000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179570.700000] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179570.700000] mice: PS/2 mouse device common for all mice
[17179570.700000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179570.700000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179570.700000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx

---

### Post by acoluthus on 2007-07-29
[17179570.700000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[17179570.700000] PNP: PS/2 controller doesn't have AUX irq; using default 12
[17179570.704000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179570.704000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179570.704000] EISA: Probing bus 0 at eisa.0
[17179570.704000] EISA: Detected 0 cards.
[17179570.704000] TCP bic registered
[17179570.704000] NET: Registered protocol family 1
[17179570.704000] NET: Registered protocol family 8
[17179570.704000] NET: Registered protocol family 20
[17179570.704000] Using IPI No-Shortcut mode
[17179570.704000] ACPI: (supports S0 S3 S4 S5)
[17179570.704000] Freeing unused kernel memory: 308k freed
[17179571.044000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179571.796000] Capability LSM initialized
[17179571.832000] ACPI: Fan [FAN] (on)
[17179571.836000] ACPI Exception (acpi_processor-0693): AE_NOT_FOUND, Processor Device is not present [20060707]
[17179571.836000] ACPI: Getting cpuindex for acpiid 0x1
[17179571.836000] ACPI Exception (acpi_processor-0693): AE_NOT_FOUND, Processor Device is not present [20060707]
[17179571.836000] ACPI: Getting cpuindex for acpiid 0x2
[17179571.836000] ACPI Exception (acpi_processor-0693): AE_NOT_FOUND, Processor Device is not present [20060707]
[17179571.836000] ACPI: Getting cpuindex for acpiid 0x3
[17179571.836000] ACPI: Thermal Zone [THRM] (26 C)
[17179572.348000] ICH6: IDE controller at PCI slot 0000:00:1f.1
[17179572.348000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 193
[17179572.348000] ICH6: chipset revision 3
[17179572.348000] ICH6: not 100% native mode: will probe irqs later
[17179572.348000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:pio
[17179572.348000]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:pio, hdd:pio
[17179572.348000] Probing IDE interface ide0...
[17179573.088000] hda: Memorex DVD16+/-DL4RWnD2, ATAPI CD/DVD-ROM drive
[17179573.764000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179573.764000] Probing IDE interface ide1...
[17179574.344000] hda: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179574.344000] Uniform CD-ROM driver Revision: 3.20
[17179574.404000] SCSI subsystem initialized
[17179574.408000] libata version 1.20 loaded.
[17179574.408000] ahci 0000:00:1f.2: version 1.2
[17179574.408000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 201
[17179580.228000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179580.228000] ahci 0000:00:1f.2: AHCI 0001.0000 32 slots 4 ports 1.5 Gbps 0xf impl IDE mode
[17179580.228000] ahci 0000:00:1f.2: flags: 64bit ncq pm led slum part 
[17179580.228000] ata1: SATA max UDMA/133 cmd 0xF8858100 ctl 0x0 bmdma 0x0 irq 201
[17179580.228000] ata2: SATA max UDMA/133 cmd 0xF8858180 ctl 0x0 bmdma 0x0 irq 201
[17179580.228000] ata3: SATA max UDMA/133 cmd 0xF8858200 ctl 0x0 bmdma 0x0 irq 201
[17179580.228000] ata4: SATA max UDMA/133 cmd 0xF8858280 ctl 0x0 bmdma 0x0 irq 201
[17179580.604000] ata1: SATA link up 1.5 Gbps (SStatus 113)
[17179580.608000] ata1: dev 0 cfg 49:2f00 82:746b 83:7f61 84:4023 85:7469 86:3e41 87:4023 88:207f
[17179580.608000] ata1: dev 0 ATA-7, max UDMA/133, 390721968 sectors: LBA48
[17179580.608000] ata1: dev 0 configured for UDMA/133
[17179580.608000] scsi0 : ahci
[17179580.812000] ata2: SATA link down (SStatus 0)
[17179580.812000] scsi1 : ahci
[17179581.016000] ata3: SATA link down (SStatus 0)
[17179581.016000] scsi2 : ahci
[17179581.220000] ata4: SATA link down (SStatus 0)
[17179581.220000] scsi3 : ahci
[17179581.220000]   Vendor: ATA       Model: WDC WD2000JS-55N  Rev: 10.0
[17179581.224000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179581.236000] SCSI device sda: 390721968 512-byte hdwr sectors (200050 MB)
[17179581.236000] sda: Write Protect is off
[17179581.236000] sda: Mode Sense: 00 3a 00 00
[17179581.236000] SCSI device sda: drive cache: write back
[17179581.236000] SCSI device sda: 390721968 512-byte hdwr sectors (200050 MB)
[17179581.236000] sda: Write Protect is off
[17179581.236000] sda: Mode Sense: 00 3a 00 00
[17179581.236000] SCSI device sda: drive cache: write back
[17179581.236000]  sda: sda1 sda2 < sda5 >
[17179581.276000] sd 0:0:0:0: Attached scsi disk sda
[17179581.512000] SiI680: IDE controller at PCI slot 0000:02:09.0
[17179581.512000] ACPI: PCI Interrupt 0000:02:09.0[A] -> GSI 17 (level, low) -> IRQ 209
[17179581.512000] SiI680: chipset revision 2
[17179581.512000] SiI680: BASE CLOCK == 133
[17179581.512000] SiI680: 100% native mode on irq 209
[17179581.512000]     ide2: MMIO-DMA , BIOS settings: hde:pio, hdf:pio
[17179581.512000]     ide3: MMIO-DMA , BIOS settings: hdg:pio, hdh:pio
[17179581.512000] Probing IDE interface ide2...
[17179582.080000] Probing IDE interface ide3...
[17179582.688000] Probing IDE interface ide1...
[17179582.720000] usbcore: registered new driver usbfs
[17179582.720000] usbcore: registered new driver hub
[17179582.720000] USB Universal Host Controller Interface driver v3.0
[17179582.720000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 217
[17179582.720000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179582.720000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179582.724000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179582.724000] uhci_hcd 0000:00:1d.0: irq 217, io base 0x0000e000
[17179582.724000] usb usb1: configuration #1 chosen from 1 choice
[17179582.724000] hub 1-0:1.0: USB hub found
[17179582.724000] hub 1-0:1.0: 2 ports detected
[17179582.784000] ieee1394: Initialized config rom entry `ip1394'
[17179582.828000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 201
[17179582.828000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179582.828000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179582.832000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179582.832000] uhci_hcd 0000:00:1d.1: irq 201, io base 0x0000e100
[17179582.832000] usb usb2: configuration #1 chosen from 1 choice
[17179582.832000] hub 2-0:1.0: USB hub found
[17179582.832000] hub 2-0:1.0: 2 ports detected
[17179582.936000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 193
[17179582.936000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179582.936000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179582.940000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179582.940000] uhci_hcd 0000:00:1d.2: irq 193, io base 0x0000e200
[17179582.940000] usb usb3: configuration #1 chosen from 1 choice
[17179582.940000] hub 3-0:1.0: USB hub found
[17179582.940000] hub 3-0:1.0: 2 ports detected
[17179583.044000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 169
[17179583.044000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17179583.044000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[17179583.048000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[17179583.048000] uhci_hcd 0000:00:1d.3: irq 169, io base 0x0000e300
[17179583.048000] usb usb4: configuration #1 chosen from 1 choice
[17179583.048000] hub 4-0:1.0: USB hub found
[17179583.048000] hub 4-0:1.0: 2 ports detected
[17179583.068000] usb 1-1: new low speed USB device using uhci_hcd and address 2
[17179583.156000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 217
[17179583.156000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179583.156000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179583.156000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[17179583.156000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[17179583.156000] ehci_hcd 0000:00:1d.7: irq 217, io mem 0xd02c4000
[17179583.160000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179583.160000] usb usb5: configuration #1 chosen from 1 choice
[17179583.160000] hub 5-0:1.0: USB hub found
[17179583.160000] hub 5-0:1.0: 8 ports detected
[17179583.268000] ACPI: PCI Interrupt 0000:02:0a.0[A] -> GSI 18 (level, low) -> IRQ 193
[17179583.268000] PCI: Via IRQ fixup for 0000:02:0a.0, from 5 to 1
[17179583.320000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[193]  MMIO=[d0180000-d01807ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[17179583.328000] Probing IDE interface ide2...
[17179583.604000] usb 1-1: device not accepting address 2, error -71
[17179583.904000] Probing IDE interface ide3...
[17179584.340000] usb 5-4: new high speed USB device using ehci_hcd and address 3
[17179584.492000] Attempting manual resume
[17179584.492000] usb 5-4: configuration #1 chosen from 1 choice
[17179584.524000] kjournald starting.  Commit interval 5 seconds
[17179584.524000] EXT3-fs: mounted filesystem with ordered data mode.
[17179584.600000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00301bbb00006bbb]
[17179584.680000] usbcore: registered new driver libusual
[17179584.920000] usb 1-1: new low speed USB device using uhci_hcd and address 4
[17179585.096000] usb 1-1: configuration #1 chosen from 1 choice
[17179585.224000] Initializing USB Mass Storage driver...
[17179585.340000] usb 4-2: new low speed USB device using uhci_hcd and address 2
[17179585.504000] usb 4-2: configuration #1 chosen from 1 choice
[17179585.508000] scsi4 : SCSI emulation for USB Mass Storage devices
[17179585.508000] usb-storage: device found at 3
[17179585.508000] usb-storage: waiting for device to settle before scanning
[17179585.508000] usbcore: registered new driver usb-storage
[17179585.508000] USB Mass Storage support registered.
[17179590.508000] usb-storage: device scan complete
[17179590.512000]   Vendor: USB2.0    Model: CF  CardReader    Rev: 9144
[17179590.512000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179590.516000]   Vendor: USB2.0    Model: CBO CardReader    Rev: 9144
[17179590.516000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179590.520000] sd 4:0:0:0: Attached scsi removable disk sdb
[17179590.528000] sd 4:0:0:1: Attached scsi removable disk sdc
[17179593.240000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179593.240000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179593.512000] usbcore: registered new driver hiddev
[17179593.688000] Linux agpgart interface v0.101 (c) Dave Jones
[17179593.692000] agpgart: Detected an Intel 915G Chipset.
[17179593.692000] agpgart: Detected 7932K stolen memory.
[17179593.708000] agpgart: AGP aperture is 256M @ 0xc0000000
[17179593.712000] FDC 0 is a post-1991 82077
[17179593.716000] hiddev96: USB HID v1.10 Device [CPS UPS AE550] on usb-0000:00:1d.0-1
[17179593.732000] hw_random: RNG not detected
[17179593.736000] input: HID 062a:0000 as /class/input/input1
[17179593.736000] input: USB HID v1.10 Mouse [HID 062a:0000] on usb-0000:00:1d.3-2
[17179593.736000] usbcore: registered new driver usbhid
[17179593.736000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179593.780000] input: PC Speaker as /class/input/input2
[17179593.984000] parport: PnPBIOS parport detected.
[17179593.984000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[17179594.052000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179594.052000] PCI: Setting latency timer of device 0000:01:00.0 to 64
[17179594.052000] sky2 v1.6.1 addr 0xd0020000 irq 169 Yukon-EC (0xb6) rev 1
[17179594.052000] sky2 eth0: addr 00:30:1b:bb:6b:57
[17179594.092000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179594.092000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[17179594.308000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179594.312000] sd 4:0:0:0: Attached scsi generic sg1 type 0
[17179594.312000] sd 4:0:0:1: Attached scsi generic sg2 type 0
[17179594.412000] ts: Compaq touchscreen protocol output
[17179594.464000] hda_codec: Unknown model for ALC880, trying auto-probe from BIOS...
[17179594.560000] hda_codec: Cannot set up configuration from BIOS.  Using 3-stack mode...
[17179594.828000] lp0: using parport0 (interrupt-driven).
[17179594.856000] sky2 eth0: enabling interface
[17179594.884000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179594.884000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179594.920000] Adding 3004112k swap on /dev/disk/by-uuid/97616b39-84cc-4eaa-8fc8-133beeceb9c8.  Priority:-1 extents:1 across:3004112k
[17179595.020000] EXT3 FS on sda1, internal journal
[17179595.928000] NET: Registered protocol family 17
[17179596.800000] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control none
[17179600.744000] ACPI: Power Button (FF) [PWRF]
[17179600.744000] ACPI: Power Button (CM) [PWRB]
[17179600.860000] ibm_acpi: ec object not found
[17179600.888000] pcc_acpi: loading...
[17179603.300000] [drm] Initialized drm 1.0.1 20051102
[17179603.304000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179603.304000] [drm] Initialized i915 1.5.0 20060119 on minor 0
[17179604.188000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179604.188000] apm: overridden by ACPI.
[17179607.708000] Bluetooth: Core ver 2.8
[17179607.708000] NET: Registered protocol family 31
[17179607.708000] Bluetooth: HCI device and connection manager initialized
[17179607.708000] Bluetooth: HCI socket layer initialized
[17179607.760000] Bluetooth: L2CAP ver 2.8
[17179607.760000] Bluetooth: L2CAP socket layer initialized
[17179607.784000] Bluetooth: RFCOMM socket layer initialized
[17179607.784000] Bluetooth: RFCOMM TTY layer initialized
[17179607.784000] Bluetooth: RFCOMM ver 1.7
[17179610.736000] NET: Registered protocol family 10
[17179610.736000] lo: Disabled Privacy Extensions
[17179610.736000] IPv6 over IPv4 tunneling driver
[17179621.672000] eth0: no IPv6 routers present

---

### Post by Rebeca on 2007-08-06
Maybe you can try the [_latest version_ of ubuntu (7.04 Feisty)](http://www.ubuntu.com/getubuntu/download). It fixes several bugs and has some new features as well. Since you have problems connecting, I'm not sure if upgrading would be the best option... It might be easier to simply download the latest version (with your mac) and then burn the iso to install from scratch. (Of course, if you have any important files in your ubuntu PC, you can save them on a CD first.)

Let me know if you want to try to see if the new version fixes your problem or if you'd like to continue troubleshooting with edgy.

---

