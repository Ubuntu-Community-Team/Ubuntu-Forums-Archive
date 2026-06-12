---
title: "Can't install or mount SATA NTFS hard disk (laptop)"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by blueglow on 2007-01-11
**[NOTE: _Solution found_, please look at [my final post in this thread for the fix]("http://ubuntuforums.org/showthread.php?p=2020951#post2020951")]**

Hello Peeps.

I cannot for the life of me get it to see/mount/whatever the internal hard disk, so I can't install.

My computer is a (relatively high-end) Sony Vaio a397xp laptop and I'm using the v6.10 downloadable CD image. The problem is install can't see the drive so after following instructions to mount it, I entered this into the terminal window as directed:
> sudo fdisk -l

And it returned nothing whatsoever! Just a new line. When I plugged in my ext USB drive that was listed fine. Please help! I've been searching this forum and googling around but to no avail.

It's an 80Gb Fujitsu SATA disk with 3 partitions (recovery, C (sys) and D (files). I was going to resize one of them and I've made space. The chipset is an Intel 915 so I'd have thought it was quite popular with regards to the basic drivers/support?

Thank you in advance for your time, I need an OS!

Kind regards,

Jim

[P.S. I've had a bit of a nightmare 24 hours thanks to Win XP randomly losing a load of important drivers, programs and internet access. It now works only after I manually start a load of services and other items that should be automatic. It's pissing me off bad, so I've decided to go Ubuntu!]

---

### Post by Jussi Kukkonen on 2007-01-11
*lspci* output might be useful here.

---

### Post by blueglow on 2007-01-11
Thank you for coming back to me... Output below mate:> ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:01.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
01:01.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
01:01.3 Mass storage controller: <pci_lookup_name: buffer too small>
01:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
01:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
03:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600]


---

### Post by blueglow on 2007-01-11
Ahhh... this is not looking so good... I looked up the line from lspci that looked suspicious on google:> Mass storage controller: <pci_lookup_name: buffer too small>

... and found these two linux-source bugs:
[Bug 72631]("https://launchpad.net/bugs/72631")
[Bug 38760]("https://launchpad.net/bugs/38760")

Do these apply to this release of Ubuntu?

So, can anyone tell me where to go from here? It appears I either need some update to the linux kernel/drivers, or some update to my bios perhaps? (getting updates from sony is like getting blood from a stone) 

Should I also report my problems/findings to somewhere to get things moving a little faster or help with bug hunting?

Any advice or ideas for work around would be much appreciated.

Thanks,

Jim

[looks like I've an evening in with a bottle of wine and the Win XP recovery disk to look forward too (*,) ]

---

### Post by Jussi Kukkonen on 2007-01-11
I've got zero experience with SATA so I really don't know how to debug this, but...

The bugs you mention may apply, the newer one is reported against the current kernel. I'm just not 100% sure if the *"buffer too small"* message is necessarily related to the device not working...

Posting in one the bugs is not a bad idea, but you can also file a new bug and mention the bugs you found -- then someone else can decide if they're duplicates or not. Regardless of whether you do that or continue to investigate this here, please include the output from these:
```
sudo lspci -vv -s 01.3
dmesg

```

Enjoy the wine, I hope it goes well with the XP install ;)

---

### Post by blueglow on 2007-01-11
I've come out of the Ubuntu CD for now to do battle with XP, but I thought I'd just ask a few more things before I go back in tomorrow...

[LIST=1]
[*]The boot up from the downloaded CD takes over 15 minutes to get into Ubuntu - Is that a sign of something not working during hardware detect or just the way it is (I've a Pentium M @ 2Ghz)
[*]Is there any logging I can access or activate as the system starts from CD? Is it worth doing, and how do I go about it?
[*]Can I install or run Ubuntu from a ext. USB drive? It's a long shot.
[/LIST]

Thanks for your help Jussi, I'll run those commands you mentioned and post the results back tomorrow.

Jim

---

### Post by Jussi Kukkonen on 2007-01-11
The boot time does sound very long...

> 
Is there any logging I can access or activate as the system starts from CD? Is it worth doing, and how do I go about it?
Can't think of anything special -- but you should be able to do everything we've already covered here while booted in to liveCD (I'm not sure where you ran the commands before, livecd or from the installer).

> 
Can I install or run Ubuntu from a ext. USB drive? It's a long shot.
It's possible install ubuntu to a usb disk, but your BIOS needs to be able to boot from there, I believe. Anyway, I wouldn't do that myself (more things that can go wrong, slower disk, etc.) but if you do, you should probably post another thread for advice.

---

### Post by blueglow on 2007-01-12
Hello, [the terminal output requested are too long so I've split it across two posts]

Here's the output from those commands Jussi suggested:
> **sudo lspci -vv -s 01.3**
01:01.3 Mass storage controller: <pci_lookup_name: buffer too small>
        Subsystem: Sony Corporation Unknown device 8190
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (1750ns min, 1000ns max), Cache Line Size: 64 bytes
        Interrupt: pin B routed to IRQ 6
        Region 0: Memory at fe9fd000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

And
> **dmesg**
[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000005ffc0000 (usable)
[17179569.184000]  BIOS-e820: 000000005ffc0000 - 000000005ffcf000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000005ffcf000 - 0000000060000000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
[17179569.184000] 639MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000ff780
[17179569.184000] On node 0 totalpages: 393152
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 163776 pages, LIFO batch:31
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 SONY                                  ) @ 0x000f68c0
[17179569.184000] ACPI: RSDT (v001   SONY       F2 0x20041216 MSFT 0x00000097) @ 0x5ffc0000
[17179569.184000] ACPI: FADT (v002   SONY       F2 0x20041216 MSFT 0x00000097) @ 0x5ffc0200
[17179569.184000] ACPI: MADT (v001   SONY       F2 0x20041216 MSFT 0x00000097) @ 0x5ffc0390
[17179569.184000] ACPI: MCFG (v001   SONY       F2 0x20041216 MSFT 0x00000097) @ 0x5ffc03f0
[17179569.184000] ACPI: OEMB (v001   SONY       F2 0x20041216 MSFT 0x00000097) @ 0x5ffcf040
[17179569.184000]   >>> ERROR: Invalid checksum
[17179569.184000] ACPI: SSDT (v001   SONY       F2 0x20041216 INTL 0x02002026) @ 0x5ffc5840
[17179569.184000] ACPI: DSDT (v001   SONY       F2 0x20041216 INTL 0x02002026) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x808
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:13 APIC version 20
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 68000000 (gap: 60000000:80000000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash --  vga=0x322
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[17179569.184000] Detected 1995.358 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour dummy device 80x25
[17179572.600000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179572.600000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179572.652000] Memory: 1549040k/1572608k available (1910k kernel code, 22444k reserved, 1070k data, 308k init, 655104k highmem)
[17179572.652000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179572.732000] Calibrating delay using timer specific routine.. 3994.92 BogoMIPS (lpj=7989848)
[17179572.732000] Security Framework v1.0.0 initialized
[17179572.732000] SELinux:  Disabled at boot.
[17179572.732000] Mount-cache hash table entries: 512
[17179572.732000] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 00000180 00000000 00000000
[17179572.732000] CPU: After vendor identify, caps: afe9fbff 00100000 00000000 00000000 00000180 00000000 00000000
[17179572.732000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179572.732000] CPU: L2 cache: 2048K
[17179572.732000] CPU: After all inits, caps: afe9fbff 00100000 00000000 00000040 00000180 00000000 00000000
[17179572.732000] Checking 'hlt' instruction... OK.
[17179572.748000] SMP alternatives: switching to UP code
[17179572.748000] Freeing SMP alternatives: 16k freed
[17179572.748000] checking if image is initramfs... it is
[17179573.212000] Freeing initrd memory: 5564k freed
[17179573.212000] ACPI: Core revision 20060707
[17179573.212000] ACPI: Looking for DSDT ... not found!
[17179573.212000] ACPI: System reset via FADT Reset Register is supported
[17179573.212000] machine_reset = acpi_machine_reset
[17179573.216000] CPU0: Intel(R) Pentium(R) M processor 2.00GHz stepping 08
[17179573.216000] Total of 1 processors activated (3994.92 BogoMIPS).
[17179573.216000] ENABLING IO-APIC IRQs
[17179573.216000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179573.360000] Brought up 1 CPUs
[17179573.360000] migration_cost=0
[17179573.360000] NET: Registered protocol family 16
[17179573.360000] EISA bus registered
[17179573.360000] ACPI: bus type pci registered
[17179573.360000] PCI: Using MMCONFIG
[17179573.360000] Setting up standard PCI resources
[17179573.364000] ACPI: Interpreter enabled
[17179573.364000] ACPI: Using IOAPIC for interrupt routing
[17179573.364000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179573.364000] PCI: Probing PCI hardware (bus 00)
[17179573.368000] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[17179573.368000] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[17179573.368000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179573.368000] Boot video device is 0000:03:00.0
[17179573.368000] PCI: Transparent bridge - 0000:00:1e.0
[17179573.368000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179573.372000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[17179573.372000] ACPI: Embedded Controller [EC0] (gpe 28) interrupt mode.
[17179573.376000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *11)
[17179573.376000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7)
[17179573.376000] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7)
[17179573.376000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7) *0, disabled.
[17179573.376000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 *4 5 6 7)
[17179573.376000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 *7)
[17179573.376000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 *6 7)
[17179573.376000] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7)


[continues into next post...]

---

### Post by blueglow on 2007-01-12
[...Continued from above post] > 
[17179573.376000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179573.376000] pnp: PnP ACPI init
[17179573.380000] pnp: PnP ACPI: found 15 devices
[17179573.380000] PnPBIOS: Disabled by ACPI PNP
[17179573.380000] PCI: Using ACPI for IRQ routing
[17179573.380000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179573.380000] PCI: Bridge: 0000:00:01.0
[17179573.380000]   IO window: a000-cfff
[17179573.380000]   MEM window: fea00000-feafffff
[17179573.380000]   PREFETCH window: cff00000-dfefffff
[17179573.380000] PCI: Bus 2, cardbus bridge: 0000:01:01.0
[17179573.380000]   IO window: 00009000-000090ff
[17179573.380000]   IO window: 00009400-000094ff
[17179573.380000]   PREFETCH window: 68000000-69ffffff
[17179573.380000]   MEM window: 6c000000-6dffffff
[17179573.380000] PCI: Bridge: 0000:00:1e.0
[17179573.380000]   IO window: 9000-9fff
[17179573.380000]   MEM window: fe900000-fe9fffff
[17179573.380000]   PREFETCH window: 68000000-6affffff
[17179573.380000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179573.380000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179573.380000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179573.380000] ACPI: PCI Interrupt 0000:01:01.0[A] -> GSI 21 (level, low) -> IRQ 177
[17179573.380000] NET: Registered protocol family 2
[17179573.420000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179573.420000] TCP established hash table entries: 262144 (order: 9, 2097152 bytes)
[17179573.420000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[17179573.420000] TCP: Hash tables configured (established 262144 bind 65536)
[17179573.420000] TCP reno registered
[17179573.420000] audit: initializing netlink socket (disabled)
[17179573.420000] audit(1168646551.420:1): initialized
[17179573.420000] highmem bounce pool size: 64 pages
[17179573.420000] VFS: Disk quotas dquot_6.5.1
[17179573.424000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179573.424000] Initializing Cryptographic API
[17179573.424000] io scheduler noop registered
[17179573.424000] io scheduler anticipatory registered
[17179573.424000] io scheduler deadline registered
[17179573.424000] io scheduler cfq registered (default)
[17179573.424000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179573.424000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179573.424000] assign_interrupt_mode Found MSI capability
[17179573.424000] Allocate Port Service[0000:00:01.0:pcie00]
[17179573.424000] Allocate Port Service[0000:00:01.0:pcie03]
[17179573.424000] isapnp: Scanning for PnP cards...
[17179573.776000] isapnp: No Plug & Play device found
[17179573.796000] Real Time Clock Driver v1.12ac
[17179573.796000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179573.796000] mice: PS/2 mouse device common for all mice
[17179573.796000] RAMDISK driver initialized: 16 RAM disks of 1048576K size 1024 blocksize
[17179573.796000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179573.796000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179573.800000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179573.800000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179573.800000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179573.800000] EISA: Probing bus 0 at eisa.0
[17179573.800000] EISA: Detected 0 cards.
[17179573.800000] TCP bic registered
[17179573.800000] NET: Registered protocol family 1
[17179573.800000] NET: Registered protocol family 8
[17179573.800000] NET: Registered protocol family 20
[17179573.800000] Using IPI No-Shortcut mode
[17179573.800000] ACPI: (supports S0 S3 S4 S5)
[17179573.800000] Freeing unused kernel memory: 308k freed
[17179573.828000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179573.840000] vesafb: framebuffer at 0xd0000000, mapped to 0xf8880000, using 3750k, total 131008k
[17179573.840000] vesafb: mode is 800x600x32, linelength=3200, pages=67
[17179573.840000] vesafb: protected mode interface info at c000:59bd
[17179573.840000] vesafb: scrolling: redraw
[17179573.840000] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[17179573.892000] Console: switching to colour frame buffer device 100x37
[17179573.892000] fb0: VESA VGA frame buffer device
[17179575.036000] Capability LSM initialized
[17179575.056000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[17179575.056000] ACPI: Processor [CPU1] (supports 8 throttling states)
[17179575.060000] ACPI: Thermal Zone [ATF0] (66 C)
[17179575.300000] ICH6: IDE controller at PCI slot 0000:00:1f.1
[17179575.300000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 201
[17179575.300000] ICH6: chipset revision 4
[17179575.300000] ICH6: not 100% native mode: will probe irqs later
[17179575.300000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pio
[17179575.300000]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:pio, hdd:pio
[17179575.300000] Probing IDE interface ide0...
[17179578.096000] hda: SONY DVD RW DW-D56A, ATAPI CD/DVD-ROM drive
[17179580.696000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179580.696000] Probing IDE interface ide1...
[17179582.768000] hda: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179582.768000] Uniform CD-ROM driver Revision: 3.20
[17179585.916000] SCSI subsystem initialized
[17179585.920000] libata version 1.20 loaded.
[17179585.920000] ahci 0000:00:1f.2: version 1.2
[17179585.920000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 209
[17179652.668000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179652.668000] ahci 0000:00:1f.2: AHCI 0001.0000 32 slots 4 ports 1.5 Gbps 0x5 impl IDE mode
[17179652.668000] ahci 0000:00:1f.2: flags: 64bit ncq pm led slum part 
[17179652.668000] ata1: SATA max UDMA/133 cmd 0xF885AD00 ctl 0x0 bmdma 0x0 irq 209
[17179652.668000] ata2: SATA max UDMA/133 cmd 0xF885AD80 ctl 0x0 bmdma 0x0 irq 209
[17179652.668000] ata3: SATA max UDMA/133 cmd 0xF885AE00 ctl 0x0 bmdma 0x0 irq 209
[17179652.668000] ata4: SATA max UDMA/133 cmd 0xF885AE80 ctl 0x0 bmdma 0x0 irq 209
[17179653.044000] ata1: SATA link up 1.5 Gbps (SStatus 113)
[17179653.044000] ata1: dev 0 cfg 49:2f00 82:346b 83:7f09 84:6063 85:3469 86:3e09 87:6063 88:203f
[17179653.044000] ata1: dev 0 ATA-7, max UDMA/100, 156301488 sectors: LBA48
[17179653.048000] ata1: dev 0 configured for UDMA/100
[17179653.048000] scsi0 : ahci
[17179653.416000] ata2: SATA link down (SStatus 0)
[17179653.416000] scsi1 : ahci
[17179653.516000] irq 209: nobody cared (try booting with the "irqpoll" option)
[17179653.516000]  <c01499a4> __report_bad_irq+0x24/0x80  <c0149a9d> note_interrupt+0x9d/0x270
[17179653.516000]  <c0149323> handle_IRQ_event+0x33/0x60  <c0149448> __do_IRQ+0xf8/0x110
[17179653.516000]  <c0105c89> do_IRQ+0x19/0x30  <c010408a> common_interrupt+0x1a/0x20
[17179653.516000]  <f885163e> acpi_processor_idle+0x181/0x3af [processor]  <c0102122> cpu_idle+0x42/0xb0
[17179653.516000]  <c03f07a1> start_kernel+0x321/0x3a0  <c03f0210> unknown_bootoption+0x0/0x270
[17179653.516000] handlers:
[17179653.516000] [<f8c2bad0>] (ahci_interrupt+0x0/0x200 [ahci])
[17179653.516000] Disabling IRQ #209
[17179654.820000] ata3: SATA link down (SStatus 0)
[17179654.820000] scsi2 : ahci
[17179655.452000] ata4: SATA link down (SStatus 0)
[17179655.452000] scsi3 : ahci
[17179655.452000]   Vendor: ATA       Model: FUJITSU MHT2080B  Rev: 4000
[17179655.452000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179655.460000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[17179655.460000] sda: Write Protect is off
[17179655.460000] sda: Mode Sense: 00 3a 00 00
[17179655.460000] SCSI device sda: drive cache: write back
[17179655.460000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[17179655.460000] sda: Write Protect is off
[17179655.460000] sda: Mode Sense: 00 3a 00 00
[17179655.460000] SCSI device sda: drive cache: write back
[17179655.460000]  sda:<4>ata1: handling error/timeout
[17179685.544000] ata1: port reset, p_is 1 is 1 pis 1 cmd c017 tf 50 ss 113 se 0
[17179685.544000] ata1: status=0x50 { DriveReady SeekComplete }
[17179685.544000] sda: Current: sense key: No Sense
[17179685.544000]     Additional sense: No additional sense information
[17179685.544000] Info fld=0x7
[17179685.544000]  sda1 sda2 sda3 <<4>ata1: handling error/timeout
[17179715.624000] ata1: port reset, p_is 1 is 1 pis 1 cmd c017 tf 50 ss 113 se 0
[17179715.624000] ata1: status=0x50 { DriveReady SeekComplete }
[17179715.624000] sda: Current: sense key: No Sense
[17179715.624000]     Additional sense: No additional sense information
[17179715.624000] Info fld=0x45dcdd7
[17179715.624000]  sda5 >
[17179715.624000] sd 0:0:0:0: Attached scsi disk sda
[17179745.776000] ata1: handling error/timeout
[17179745.776000] ata1: port reset, p_is 1 is 1 pis 1 cmd c017 tf 50 ss 113 se 0
[17179745.776000] ata1: status=0x50 { DriveReady SeekComplete }
[17179745.776000] sda: Current: sense key: No Sense
[17179745.776000]     Additional sense: No additional sense information
[17179745.776000] Info fld=0x950f807
[17179775.884000] ata1: handling error/timeout
[17179775.884000] ata1: port reset, p_is 1 is 1 pis 1 cmd c017 tf 50 ss 113 se 0
[17179775.884000] ata1: status=0x50 { DriveReady SeekComplete }
[17179775.884000] sda: Current: sense key: No Sense
[17179775.884000]     Additional sense: No additional sense information
[17179775.884000] Info fld=0x950f8af
[17179805.924000] ata1: handling error/timeout
[17179805.924000] ata1: port reset, p_is 1 is 1 pis 1 cmd c017 tf 50 ss 113 se 0
[17179805.924000] ata1: status=0x50 { DriveReady SeekComplete }
[17179805.924000] sda: Current: sense key: No Sense
[17179805.924000]     Additional sense: No additional sense information
[17179805.924000] Info fld=0x950f877
[17179835.984000] ata1: handling error/timeout
[17179835.984000] ata1: port reset, p_is 1 is 1 pis 1 cmd c017 tf 50 ss 113 se 0
[17179835.984000] ata1: status=0x50 { DriveReady SeekComplete }
[17179835.984000] sda: Current: sense key: No Sense
[17179835.984000]     Additional sense: No additional sense information
[17179835.984000] Info fld=0x950f7b7
[17179866.008000] ata1: handling error/timeout
[17179866.008000] ata1: port reset, p_is 1 is 1 pis 1 cmd c017 tf 50 ss 113 se 0
[17179866.008000] ata1: status=0x50 { DriveReady SeekComplete }
[17179866.008000] sda: Current: sense key: No Sense
[17179866.008000]     Additional sense: No additional sense information
[17179866.008000] Info fld=0x950f8a7
[17179896.188000] ata1: handling error/timeout
[17179896.188000] ata1: port reset, p_is 1 is 1 pis 1 cmd c017 tf 50 ss 113 se 0
[17179896.188000] ata1: status=0x50 { DriveReady SeekComplete }
[17179896.188000] sda: Current: sense key: No Sense
[17179896.188000]     Additional sense: No additional sense information
[17179896.188000] Info fld=0x950f727
[17179926.256000] ata1: handling error/timeout
[17179926.256000] ata1: port reset, p_is 1 is 1 pis 1 cmd c017 tf 50 ss 113 se 0
[17179926.256000] ata1: status=0x50 { DriveReady SeekComplete }
[17179926.256000] sda: Current: sense key: No Sense
[17179926.256000]     Additional sense: No additional sense information
[17179926.256000] Info fld=0xdf8ec6
[17179956.356000] ata1: handling error/timeout
[17179956.356000] ata1: port reset, p_is 1 is 1 pis 1 cmd c017 tf 50 ss 113 se 0
[17179956.356000] ata1: status=0x50 { DriveReady SeekComplete }
[17179956.356000] sda: Current: sense key: No Sense
[17179956.356000]     Additional sense: No additional sense information
[17179956.356000] Info fld=0x45dcd17
[17179986.436000] ata1: handling error/timeout
[17179986.436000] ata1: port reset, p_is 1 is 1 pis 1 cmd c017 tf 50 ss 113 se 0
[17179986.436000] ata1: status=0x50 { DriveReady SeekComplete }
[17179986.436000] sda: Current: sense key: No Sense
[17179986.436000]     Additional sense: No additional sense information
[17179986.436000] Info fld=0x45dcdd1
[17180016.512000] ata1: handling error/timeout
[17180016.512000] ata1: port reset, p_is 1 is 1 pis 1 cmd c017 tf 50 ss 113 se 0
[17180016.512000] ata1: status=0x50 { DriveReady SeekComplete }
[17180016.512000] sda: Current: sense key: No Sense
[17180016.512000]     Additional sense: No additional sense information
[17180016.512000] Info fld=0x950e416
[17180046.592000] ata1: handling error/timeout
[17180046.592000] ata1: port reset, p_is 1 is 1 pis 1 cmd c017 tf 50 ss 113 se 0
[17180046.592000] ata1: status=0x50 { DriveReady SeekComplete }
[17180046.592000] sda: Current: sense key: No Sense
[17180046.592000]     Additional sense: No additional sense information
[17180046.592000] Info fld=0x7
[17180075.872000] Probing IDE interface ide1...
[17180075.900000] usbcore: registered new driver usbfs
[17180075.900000] usbcore: registered new driver hub
[17180075.904000] USB Universal Host Controller Interface driver v3.0
[17180075.904000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 217
[17180075.904000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17180075.904000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17180075.904000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17180075.904000] uhci_hcd 0000:00:1d.0: irq 217, io base 0x0000d880
[17180075.904000] usb usb1: configuration #1 chosen from 1 choice
[17180075.904000] hub 1-0:1.0: USB hub found
[17180075.904000] hub 1-0:1.0: 2 ports detected
[17180075.960000] ieee1394: Initialized config rom entry `ip1394'
[17180076.132000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 22 (level, low) -> IRQ 225
[17180076.132000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17180076.132000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17180076.132000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17180076.132000] uhci_hcd 0000:00:1d.1: irq 225, io base 0x0000dc00
[17180076.136000] usb usb2: configuration #1 chosen from 1 choice
[17180076.136000] hub 2-0:1.0: USB hub found
[17180076.136000] hub 2-0:1.0: 2 ports detected
[17180076.320000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 20 (level, low) -> IRQ 233
[17180076.320000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17180076.320000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17180076.320000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17180076.320000] uhci_hcd 0000:00:1d.2: irq 233, io base 0x0000e000
[17180076.320000] usb usb3: configuration #1 chosen from 1 choice
[17180076.320000] hub 3-0:1.0: USB hub found
[17180076.320000] hub 3-0:1.0: 2 ports detected
[17180076.496000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 21 (level, low) -> IRQ 177
[17180076.496000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17180076.496000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[17180076.496000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[17180076.496000] uhci_hcd 0000:00:1d.3: irq 177, io base 0x0000e080
[17180076.500000] usb usb4: configuration #1 chosen from 1 choice
[17180076.500000] hub 4-0:1.0: USB hub found
[17180076.500000] hub 4-0:1.0: 2 ports detected
[17180076.644000] ata1: handling error/timeout
[17180076.644000] ata1: port reset, p_is 1 is 1 pis 1 cmd c017 tf 50 ss 113 se 0
[17180076.644000] ata1: status=0x50 { DriveReady SeekComplete }
[17180076.644000] sda: Current: sense key: No Sense
[17180076.644000]     Additional sense: No additional sense information
[17180076.644000] Info fld=0xdf8f8e
[17180076.648000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 217
[17180076.648000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17180076.648000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17180076.648000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[17180076.648000] ehci_hcd 0000:00:1d.7: debug port 1
[17180076.648000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[17180076.648000] ehci_hcd 0000:00:1d.7: irq 217, io mem 0xfebff800
[17180076.652000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17180076.652000] usb usb5: configuration #1 chosen from 1 choice
[17180076.652000] hub 5-0:1.0: USB hub found
[17180076.652000] hub 5-0:1.0: 8 ports detected
[17180076.884000] ACPI: PCI Interrupt 0000:01:01.2[C] -> GSI 23 (level, low) -> IRQ 217
[17180076.936000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[217]  MMIO=[fe9ff000-fe9ff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[17180080.932000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0800460301d47738]
[17180083.968000] usb 1-2: new low speed USB device using uhci_hcd and address 2
[17180084.888000] usb 1-2: configuration #1 chosen from 1 choice
[17180086.588000] usb 4-2: new full speed USB device using uhci_hcd and address 2
[17180087.200000] usb 4-2: configuration #1 chosen from 1 choice
[17180087.204000] usbcore: registered new driver hiddev
[17180087.224000] input: Logitech USB Receiver as /class/input/input1
[17180087.224000] input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-2
[17180087.224000] usbcore: registered new driver usbhid
[17180087.224000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17180090.768000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17180090.884000] ISO 9660 Extensions: RRIP_1991A
[17180090.928000] Registering unionfs 1.1.4
[17180090.932000] loop: loaded (max 8 devices)
[17180091.128000] squashfs: version 3.0 (2006/03/15) Phillip Lougher
[17180106.664000] ata1: handling error/timeout
[17180106.664000] ata1: port reset, p_is 1 is 1 pis 1 cmd c017 tf 50 ss 113 se 0
[17180106.664000] ata1: status=0x50 { DriveReady SeekComplete }
[17180106.664000] sda: Current: sense key: No Sense
[17180106.664000]     Additional sense: No additional sense information
[17180106.664000] Info fld=0x45dcdcf
[17180136.960000] ata1: handling error/timeout
[17180136.960000] ata1: port reset, p_is 1 is 1 pis 1 cmd c017 tf 50 ss 113 se 0
[17180136.960000] ata1: status=0x50 { DriveReady SeekComplete }
[17180136.960000] sda: Current: sense key: No Sense
[17180136.960000]     Additional sense: No additional sense information
[17180136.960000] Info fld=0x950e4c0
[17180166.968000] ata1: handling error/timeout
[17180166.968000] ata1: port reset, p_is 1 is 1 pis 1 cmd c017 tf 50 ss 113 se 0
[17180166.968000] ata1: status=0x50 { DriveReady SeekComplete }
[17180166.968000] sda: Current: sense key: No Sense
[17180166.968000]     Additional sense: No additional sense information
[17180166.968000] Info fld=0x27
[17180170.988000] r8169 Gigabit Ethernet driver 2.2LK loaded
[17180170.988000] ACPI: PCI Interrupt 0000:01:03.0[A] -> GSI 17 (level, low) -> IRQ 209
[17180170.988000] eth0: Identified chip type is 'RTL8169s/8110s'.
[17180170.988000] eth0: RTL8169 at 0xf8d06c00, 00:01:4a:1c:cd:e1, IRQ 209
[17180179.400000] hw_random: RNG not detected
[17180179.456000] Linux agpgart interface v0.101 (c) Dave Jones
[17180179.492000] agpgart: Detected an Intel 915GM Chipset.
[17180179.512000] agpgart: AGP aperture is 256M @ 0x0
[17180179.788000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17180179.936000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17180180.132000] input: PC Speaker as /class/input/input2
[17180180.316000] ieee80211_crypt: registered algorithm 'NULL'
[17180180.316000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[17180180.316000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17180180.868000] input: PS/2 Mouse as /class/input/input3
[17180180.884000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input4
[17180180.912000] ACPI: PCI Interrupt 0000:01:01.0[A] -> GSI 21 (level, low) -> IRQ 177
[17180180.912000] Yenta: CardBus bridge found at 0000:01:01.0 [104d:818f]
[17180180.912000] Yenta: Enabling burst memory read transactions
[17180180.912000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17180180.912000] Yenta: Routing CardBus interrupts to PCI
[17180180.912000] Yenta TI: socket 0000:01:01.0, mfunc 0x01001b22, devctl 0x64
[17180181.216000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq
[17180181.216000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[17180181.216000] Driver 'ipw2200' needs updating - please use bus_type methods
[17180181.248000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 177
[17180181.248000] Socket status: 30000006
[17180181.248000] pcmcia: parent PCI bridge I/O window: 0x9000 - 0x9fff
[17180181.248000] cs: IO port probe 0x9000-0x9fff: clean.
[17180181.248000] pcmcia: parent PCI bridge Memory window: 0xfe900000 - 0xfe9fffff
[17180181.248000] pcmcia: parent PCI bridge Memory window: 0x68000000 - 0x6affffff
[17180181.288000] ACPI: PCI Interrupt 0000:01:02.0[A] -> GSI 18 (level, low) -> IRQ 201
[17180181.288000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[17180181.472000] Bluetooth: Core ver 2.8
[17180181.472000] NET: Registered protocol family 31
[17180181.472000] Bluetooth: HCI device and connection manager initialized
[17180181.472000] Bluetooth: HCI socket layer initialized
[17180181.532000] Bluetooth: HCI USB driver ver 2.9
[17180181.540000] usbcore: registered new driver hci_usb
[17180181.688000] ts: Compaq touchscreen protocol output
[17180182.236000] ipw2200: Detected geography ZZD (13 802.11bg channels, 0 802.11a channels)
[17180182.236000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 169
[17180182.236000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[17180182.484000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17180183.036000] cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x370-0x377
[17180183.036000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17180183.036000] cs: IO port probe 0x820-0x8ff: clean.
[17180183.036000] cs: IO port probe 0xc00-0xcf7: clean.
[17180183.036000] cs: IO port probe 0xa00-0xaff: clean.
[17180183.056000] r8169: eth0: link down
[17180184.508000] NET: Registered protocol family 17
[17180184.656000] eth1: NETDEV_TX_BUSY returned; driver should report queue full via ieee_device->is_queue_full.
[17180197.132000] ata1: handling error/timeout
[17180197.132000] ata1: port reset, p_is 1 is 1 pis 1 cmd c017 tf 50 ss 113 se 0
[17180197.132000] ata1: status=0x50 { DriveReady SeekComplete }
[17180197.132000] sda: Current: sense key: No Sense
[17180197.132000]     Additional sense: No additional sense information
[17180197.132000] Info fld=0xdf8f8f
[17180227.172000] ata1: handling error/timeout
[17180227.172000] ata1: port reset, p_is 1 is 1 pis 1 cmd c017 tf 50 ss 113 se 0
[17180227.172000] ata1: status=0x50 { DriveReady SeekComplete }
[17180227.172000] sda: Current: sense key: No Sense
[17180227.172000]     Additional sense: No additional sense information
[17180227.172000] Info fld=0x45dcd97
[17180257.296000] ata1: handling error/timeout
[17180257.296000] ata1: port reset, p_is 1 is 1 pis 1 cmd c017 tf 50 ss 113 se 0
[17180257.296000] ata1: status=0x50 { DriveReady SeekComplete }
[17180257.296000] sda: Current: sense key: No Sense
[17180257.296000]     Additional sense: No additional sense information
[17180257.296000] Info fld=0x950e486
[17180287.440000] ata1: handling error/timeout
[17180287.440000] ata1: port reset, p_is 1 is 1 pis 1 cmd c017 tf 50 ss 113 se 0
[17180287.440000] ata1: status=0x50 { DriveReady SeekComplete }
[17180287.440000] sda: Current: sense key: No Sense
[17180287.440000]     Additional sense: No additional sense information
[17180287.440000] Info fld=0x87
[17180317.592000] ata1: handling error/timeout
[17180317.592000] ata1: port reset, p_is 1 is 1 pis 1 cmd c017 tf 50 ss 113 se 0
[17180317.592000] ata1: status=0x50 { DriveReady SeekComplete }
[17180317.592000] sda: Current: sense key: No Sense
[17180317.592000]     Additional sense: No additional sense information
[17180317.592000] Info fld=0xdf8f56
[17180347.752000] ata1: handling error/timeout
[17180347.752000] ata1: port reset, p_is 1 is 1 pis 1 cmd c017 tf 50 ss 113 se 0
[17180347.752000] ata1: status=0x50 { DriveReady SeekComplete }
[17180347.752000] sda: Current: sense key: No Sense
[17180347.752000]     Additional sense: No additional sense information
[17180347.752000] Info fld=0x45dccd7
[17180377.756000] ata1: handling error/timeout
[17180377.756000] ata1: port reset, p_is 1 is 1 pis 1 cmd c017 tf 50 ss 113 se 0
[17180377.756000] ata1: status=0x50 { DriveReady SeekComplete }
[17180377.756000] sda: Current: sense key: No Sense
[17180377.756000]     Additional sense: No additional sense information
[17180377.756000] Info fld=0x950e3c6
[17180407.908000] ata1: handling error/timeout
[17180407.908000] ata1: port reset, p_is 1 is 1 pis 1 cmd c017 tf 50 ss 113 se 0
[17180407.908000] ata1: status=0x50 { DriveReady SeekComplete }
[17180407.908000] sda: Current: sense key: No Sense
[17180407.908000]     Additional sense: No additional sense information
[17180407.908000] Info fld=0x207
[17180438.036000] ata1: handling error/timeout
[17180438.036000] ata1: port reset, p_is 1 is 1 pis 1 cmd c017 tf 50 ss 113 se 0
[17180438.036000] ata1: status=0x50 { DriveReady SeekComplete }
[17180438.036000] sda: Current: sense key: No Sense
[17180438.036000]     Additional sense: No additional sense information
[17180438.036000] Info fld=0xdf8e96
[17180468.196000] ata1: handling error/timeout
[17180468.196000] ata1: port reset, p_is 1 is 1 pis 1 cmd c017 tf 50 ss 113 se 0
[17180468.196000] ata1: status=0x50 { DriveReady SeekComplete }
[17180468.196000] sda: Current: sense key: No Sense
[17180468.196000]     Additional sense: No additional sense information
[17180468.196000] Info fld=0x45dcdc7
[17180498.328000] ata1: handling error/timeout
[17180498.328000] ata1: port reset, p_is 1 is 1 pis 1 cmd c017 tf 50 ss 113 se 0
[17180498.328000] ata1: status=0x50 { DriveReady SeekComplete }
[17180498.328000] sda: Current: sense key: No Sense
[17180498.328000]     Additional sense: No additional sense information
[17180498.328000] Info fld=0x45dcdd1
[17180528.332000] ata1: handling error/timeout
[17180528.332000] ata1: port reset, p_is 1 is 1 pis 1 cmd c017 tf 50 ss 113 se 0
[17180528.332000] ata1: status=0x50 { DriveReady SeekComplete }
[17180528.332000] sda: Current: sense key: No Sense
[17180528.332000]     Additional sense: No additional sense information
[17180528.332000] Info fld=0x950e4b6
[17180551.036000] ACPI: AC Adapter [ACAD] (on-line)
[17180551.052000] Asus Laptop ACPI Extras version 0.30
[17180551.052000]   unsupported model F2, trying default values
[17180551.052000]   send /proc/acpi/dsdt to the developers
[17180551.064000] ACPI: Battery Slot [BAT1] (battery present)
[17180551.092000] ACPI: Power Button (CM) [PWRB]
[17180551.092000] ACPI: Lid Switch [LID]
[17180552.336000] ibm_acpi: ec object not found
[17180553.380000] pcc_acpi: loading...
[17180553.428000] ACPI Sony Notebook Control Driver v0.2 successfully installed
[17180557.588000] lp: driver loaded but no devices found
[17180557.696000] ppdev: user-space parallel port driver
[17180558.292000] [drm] Initialized drm 1.0.1 20051102
[17180558.336000] ata1: handling error/timeout
[17180558.336000] ata1: port reset, p_is 1 is 1 pis 1 cmd c017 tf 50 ss 113 se 0
[17180558.336000] ata1: status=0x50 { DriveReady SeekComplete }
[17180558.336000] sda: Current: sense key: No Sense
[17180558.336000]     Additional sense: No additional sense information
[17180558.336000] Info fld=0xdf8f86
[17180558.340000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 16 (level, low) -> IRQ 169
[17180558.340000] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[17180563.596000] apm: BIOS not found.
[17180563.836000] [drm] Setting GART location based on new memory map
[17180563.836000] [drm] Loading R300 Microcode
[17180563.836000] [drm] writeback test succeeded in 1 usecs
[17180582.480000] NET: Registered protocol family 10
[17180582.480000] lo: Disabled Privacy Extensions
[17180582.480000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17180582.480000] IPv6 over IPv4 tunneling driver
[17180588.356000] ata1: handling error/timeout
[17180588.356000] ata1: port reset, p_is 1 is 1 pis 1 cmd c017 tf 50 ss 113 se 0
[17180588.356000] ata1: status=0x50 { DriveReady SeekComplete }
[17180588.356000] sda: Current: sense key: No Sense
[17180588.356000]     Additional sense: No additional sense information
[17180588.356000] Info fld=0x45dcc47
[17180593.360000] eth1: no IPv6 routers present
[17180603.860000] sonypi: Sony Programmable I/O Controller Driver v1.26.
[17180603.860000] sonypi: detected type3 model, verbose = 0, fnkeyinit = off, camera = off, compat = off, mask = 0xffffffff, useinput = on, acpi = on
[17180603.860000] sonypi: enabled at irq=11, port1=0x1080, port2=0x1084
[17180603.860000] sonypi: device allocated minor is 62
[17180603.860000] input: Sony Vaio Jogdial as /class/input/input5
[17180603.860000] input: Sony Vaio Keys as /class/input/input6
[17180607.380000] Bluetooth: L2CAP ver 2.8
[17180607.380000] Bluetooth: L2CAP socket layer initialized
[17180607.848000] Bluetooth: RFCOMM socket layer initialized
[17180607.848000] Bluetooth: RFCOMM TTY layer initialized
[17180607.848000] Bluetooth: RFCOMM ver 1.7
[17180618.356000] ata1: handling error/timeout
[17180618.356000] ata1: port reset, p_is 1 is 1 pis 1 cmd c017 tf 50 ss 113 se 0
[17180618.356000] ata1: status=0x50 { DriveReady SeekComplete }
[17180618.356000] sda: Current: sense key: No Sense
[17180618.356000]     Additional sense: No additional sense information
[17180618.356000] Info fld=0x950e336
[17180620.208000] Asus ACPI: LED (WLED) write failed
[17180648.364000] ata1: handling error/timeout
[17180648.364000] ata1: port reset, p_is 1 is 1 pis 1 cmd c017 tf 50 ss 113 se 0
[17180648.364000] ata1: status=0x50 { DriveReady SeekComplete }
[17180648.364000] sda: Current: sense key: No Sense
[17180648.364000]     Additional sense: No additional sense information
[17180648.364000] Info fld=0x45dcdd1
[17180678.372000] ata1: handling error/timeout
[17180678.372000] ata1: port reset, p_is 1 is 1 pis 1 cmd c017 tf 50 ss 113 se 0
[17180678.372000] ata1: status=0x50 { DriveReady SeekComplete }
[17180678.372000] sda: Current: sense key: No Sense
[17180678.372000]     Additional sense: No additional sense information
[17180678.372000] Info fld=0xdf8e06
[17180689.756000] usb 5-1: new high speed USB device using ehci_hcd and address 4
[17180689.912000] usb 5-1: configuration #1 chosen from 1 choice
[17180693.796000] usbcore: registered new driver libusual
[17180693.892000] Initializing USB Mass Storage driver...
[17180693.892000] scsi4 : SCSI emulation for USB Mass Storage devices
[17180693.892000] usb-storage: device found at 4
[17180693.892000] usb-storage: waiting for device to settle before scanning
[17180693.892000] usbcore: registered new driver usb-storage
[17180693.892000] USB Mass Storage support registered.
[17180698.896000] usb-storage: device scan complete
[17180698.896000]   Vendor: Maxtor 6  Model: 9GDH              Rev: 1DD0
[17180698.896000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17180698.900000] SCSI device sdb: 781422768 512-byte hdwr sectors (400088 MB)
[17180698.900000] sdb: Write Protect is off
[17180698.900000] sdb: Mode Sense: 00 38 00 00
[17180698.900000] sdb: assuming drive cache: write through
[17180698.900000] SCSI device sdb: 781422768 512-byte hdwr sectors (400088 MB)
[17180698.900000] sdb: Write Protect is off
[17180698.900000] sdb: Mode Sense: 00 38 00 00
[17180698.900000] sdb: assuming drive cache: write through
[17180698.900000]  sdb: sdb1
[17180698.924000] sd 4:0:0:0: Attached scsi disk sdb
[17180698.924000] sd 4:0:0:0: Attached scsi generic sg1 type 0
[17180699.360000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[17180699.360000] NTFS-fs warning (device sdb1): parse_options(): Option iocharset is deprecated. Please use option nls=<charsetname> in the future.
[17180699.404000] NTFS volume version 3.1.
[17180708.372000] ata1: handling error/timeout
[17180708.372000] ata1: port reset, p_is 1 is 1 pis 1 cmd c017 tf 50 ss 113 se 0
[17180708.372000] ata1: status=0x50 { DriveReady SeekComplete }
[17180708.372000] sda: Current: sense key: No Sense
[17180708.372000]     Additional sense: No additional sense information
[17180708.372000] Info fld=0xdf8f97
[17180738.380000] ata1: handling error/timeout
[17180738.380000] ata1: port reset, p_is 1 is 1 pis 1 cmd c017 tf 50 ss 113 se 0
[17180738.380000] ata1: status=0x50 { DriveReady SeekComplete }
[17180738.380000] sda: Current: sense key: No Sense
[17180738.380000]     Additional sense: No additional sense information
[17180738.380000] Info fld=0x45dce16
[17180763.400000] ieee80211_crypt: registered algorithm 'WEP'
[17180768.384000] ata1: handling error/timeout
[17180768.384000] ata1: port reset, p_is 1 is 1 pis 1 cmd c017 tf 50 ss 113 se 0
[17180768.384000] ata1: status=0x50 { DriveReady SeekComplete }
[17180768.384000] sda: Current: sense key: No Sense
[17180768.384000]     Additional sense: No additional sense information
[17180768.384000] Info fld=0x46
[17180774.192000] eth1: no IPv6 routers present
[17180798.384000] ata1: handling error/timeout
[17180798.384000] ata1: port reset, p_is 1 is 1 pis 1 cmd c017 tf 50 ss 113 se 0
[17180798.384000] ata1: status=0x50 { DriveReady SeekComplete }
[17180798.384000] sda: Current: sense key: No Sense
[17180798.384000]     Additional sense: No additional sense information
[17180798.384000] Info fld=0xdf8fb7
[17180828.384000] ata1: handling error/timeout
[17180828.384000] ata1: port reset, p_is 1 is 1 pis 1 cmd c017 tf 50 ss 113 se 0
[17180828.384000] ata1: status=0x50 { DriveReady SeekComplete }
[17180828.384000] sda: Current: sense key: No Sense
[17180828.384000]     Additional sense: No additional sense information
[17180828.384000] Info fld=0x45dce36
[17180858.392000] ata1: handling error/timeout
[17180858.392000] ata1: port reset, p_is 1 is 1 pis 1 cmd c017 tf 50 ss 113 se 0
[17180858.392000] ata1: status=0x50 { DriveReady SeekComplete }
[17180858.392000] sda: Current: sense key: No Sense
[17180858.392000]     Additional sense: No additional sense information
[17180858.392000] Info fld=0x66
[17180888.392000] ata1: handling error/timeout
[17180888.392000] ata1: port reset, p_is 1 is 1 pis 1 cmd c017 tf 50 ss 113 se 0
[17180888.392000] ata1: status=0x50 { DriveReady SeekComplete }
[17180888.392000] sda: Current: sense key: No Sense
[17180888.392000]     Additional sense: No additional sense information
[17180888.392000] Info fld=0xdf9017
[17180918.396000] ata1: handling error/timeout
[17180918.396000] ata1: port reset, p_is 1 is 1 pis 1 cmd c017 tf 50 ss 113 se 0
[17180918.396000] ata1: status=0x50 { DriveReady SeekComplete }
[17180918.396000] sda: Current: sense key: No Sense
[17180918.396000]     Additional sense: No additional sense information
[17180918.396000] Info fld=0x45dce96
[17180948.396000] ata1: handling error/timeout
[17180948.396000] ata1: port reset, p_is 1 is 1 pis 1 cmd c017 tf 50 ss 113 se 0
[17180948.396000] ata1: status=0x50 { DriveReady SeekComplete }
[17180948.396000] sda: Current: sense key: No Sense
[17180948.396000]     Additional sense: No additional sense information
[17180948.396000] Info fld=0xc6
[17180978.396000] ata1: handling error/timeout
[17180978.396000] ata1: port reset, p_is 1 is 1 pis 1 cmd c017 tf 50 ss 113 se 0
[17180978.396000] ata1: status=0x50 { DriveReady SeekComplete }
[17180978.396000] sda: Current: sense key: No Sense
[17180978.396000]     Additional sense: No additional sense information
[17180978.396000] Info fld=0xdf9197
[17181008.400000] ata1: handling error/timeout
[17181008.400000] ata1: port reset, p_is 1 is 1 pis 1 cmd c017 tf 50 ss 113 se 0
[17181008.400000] ata1: status=0x50 { DriveReady SeekComplete }
[17181008.400000] sda: Current: sense key: No Sense
[17181008.400000]     Additional sense: No additional sense information
[17181008.400000] Info fld=0x45dd016
[17181038.408000] ata1: handling error/timeout
[17181038.408000] ata1: port reset, p_is 1 is 1 pis 1 cmd c017 tf 50 ss 113 se 0
[17181038.408000] ata1: status=0x50 { DriveReady SeekComplete }
[17181038.408000] sda: Current: sense key: No Sense
[17181038.408000]     Additional sense: No additional sense information
[17181038.408000] Info fld=0x246
[17181068.408000] ata1: handling error/timeout
[17181068.408000] ata1: port reset, p_is 1 is 1 pis 1 cmd c017 tf 50 ss 113 se 0
[17181068.408000] ata1: status=0x50 { DriveReady SeekComplete }
[17181068.408000] sda: Current: sense key: No Sense
[17181068.408000]     Additional sense: No additional sense information
[17181068.408000] Info fld=0xff8f97
[17181098.412000] ata1: handling error/timeout
[17181098.412000] ata1: port reset, p_is 1 is 1 pis 1 cmd c017 tf 50 ss 113 se 0
[17181098.412000] ata1: status=0x50 { DriveReady SeekComplete }
[17181098.412000] sda: Current: sense key: No Sense
[17181098.412000]     Additional sense: No additional sense information
[17181098.412000] Info fld=0x47dce16
[17181128.412000] ata1: handling error/timeout
[17181128.412000] ata1: port reset, p_is 1 is 1 pis 1 cmd c017 tf 50 ss 113 se 0
[17181128.412000] ata1: status=0x50 { DriveReady SeekComplete }
[17181128.412000] sda: Current: sense key: No Sense
[17181128.412000]     Additional sense: No additional sense information
[17181128.412000] Info fld=0xab46e


I've also been into the bios and there are no options really except boot order. I'm currently looking for a bios update now but doubt there is one.

Does the above output provide any clues or workarounds?

Thanks,

Jim

---

### Post by Jussi Kukkonen on 2007-01-13
All those ata errors are probably  related to this... Someone who understands that stuff could probably tell what is happening based on that output.

There is also some irq problem (those aren't that rare and it could be harmless, but you never know):

[QUOTE=dmesg]
[17179653.516000] irq 209: nobody cared (try booting with the "irqpoll" option)[/QUOTE]
I doubt it helps, but you could try booting with "irqpoll" as it suggests.

---

### Post by blueglow on 2007-01-13
Thanks again Jussi.

At the risk of sounding like a total noob, which I am, how do I boot with the ***irqpoll*** option? If there's a page that gives step-by-step instructions that'd be good too.

Since this thread has got to the point of being about irq/hardware/laptops/ata, should I cross post this somewhere else on this forum? Or is cross-posting evil? Where would I find *"Someone who understands that stuff"*?

Any more ideas or advice would be much appreciated.

Thanks again,

Jim

---

### Post by Jussi Kukkonen on 2007-01-13
No problem.

Posting on a another subforum is fine, I believe this is no longer "Absolute beginner" stuff :) You could try Installation or Laptop...

It's been a while since I've seen the liveCD, but adding boot options (like irqpoll) should happen on the first screen where you normally select "start Ubuntu" or "Check memory" etc.

---

### Post by blueglow on 2007-01-16
It's amazing what one can find when one has just a few keywords! As a noob I had no point of reference, but as soon a Jussi told me about the **irqpoll** option I was able to find a thread the provides the solution. So here's the fix as it worked for me...

(I have now installed Ubuntu Edgy (6.10) on my laptop from the LiveCD twice - the second time to allow more space and move partitions around - and bizarely the second time fix for hard drive detection was slightly different.)

_**Solution**_ for my Sony Vaio a397xp with its Intel 915 chipset and a Fujitsu 80Gb SATA drive and for dual boot using Grub - was spread around this thread: [Edgy Install Doesn't Recognize Hard Drive]("http://ubuntuforums.org/showthread.php?t=299929")
[INDENT]
[LIST=1]
[*]Start the computer with the LiveCD in the drive, but at initial boot screen press F6 for extra options.
[*]On the "Start/Install Ubuntu" (top) line, edit the line by following the instructions at the bottom of the screen and add " **pci=nomsi**" to the end of the line. Press return and then boot with the new option.
[*](Perhaps not required) If the hard drive still isn't detected (no disk light/activity) or the boot process takes an age, press reset and repeat but add " **acpi=force irqpoll**" in addition to " pci=nomsi".
[*]Install Ubuntu as normal when system comes up (I did a dual boot with existing XP). Close everything, eject the LiveCD, restart the computer.
[/LIST]
At this point my laptop worked fine, but if the boot from hard drive still isn't detected without the pci or irqpoll parameters (from steps 2 and/or 3 above) then once you should update your system ASAP (System > Administration > Synaptic Package Manager: Click Reload, then Mark All Upgrades, then Apply. Restart if/when prompted).

You may need to add those boot options to the Grub settings so they're always run when you start up... [COLOR="DimGray"]_How to edit grub menu settings_: When in Ubuntu press alt-F2 and type "gksudo nautilus" and enter your new password to open a new window acting as the root account (you need root permission to for the next step). Using the new window, navigate to /boot/grub (probably /media/sda1/boot/grub or similar) and double-click "menu.lst". Near the bottom you'll see sections for "Ubuntu <version>" and Ubuntu <version> (recovery)". On the lines start "kernel", append the boot options that worked for you to the end, save.[/COLOR]
[/INDENT]
I am still left with a slow boot where sort of sticks at the very first sliver of progress bar for a minute or so before the hard drive springs into life, XP loads very quickly by comparison. If anyone has any ideas as to why I'd love to hear them.

**Thanks again to Jussi for his help**.

All the best,

Jim

---

