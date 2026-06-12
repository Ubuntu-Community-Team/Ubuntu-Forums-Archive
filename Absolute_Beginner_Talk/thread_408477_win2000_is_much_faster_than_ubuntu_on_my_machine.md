---
title: "win2000 is much faster than ubuntu on my machine"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by findik1 on 2007-04-13
Hi 

In our lab I installed win2000 to dell optiplex 620 and ubuntu edgy. I installed intel chipset software as dell says it is urgent to install.  I run scientific software MATLAB to run some task on THE SAME machine on windows2000 and on ubuntu. The machine spec is intel pent 4 3.2GHz HT and MEMORY 1.2GB. Ubuntu result is attached. As you see that it performs way below than what it should. I cannot show you window result since I did not have screenshoot software there but you should believe me that the results gave that our machine was number one (the top). So there should be a way to improve the performance at least as win2000.

(note: everything is fresh installed, there are enough of hd and memory)

Any suggestions?
thanks in advance
findik

---

### Post by tgm4883 on 2007-04-13
You can get a screenshot in windows with printscreen and ms paint.  The only thing I can ask is all your hardware recognized in ubuntu?

---

### Post by findik1 on 2007-04-13
> **tgm4883 said:**
> You can get a screenshot in windows with printscreen and ms paint.  The only thing I can ask is all your hardware recognized in ubuntu?

yes. Ubuntu is working perfectly fine on the computer. The only thing is I would not expect ubuntu would do well in graphics (since no specific graphic accelarator or graphic driver I installed in ubuntu), so as you see  ubuntu was very poor on 3D (LAST COLUMN, 3D imaging) compared to others on that issue. But still in some mathematical calculations , it is still slower than win2000(see, column 1 to 5.

---

### Post by compmodder26 on 2007-04-13
What version of Ubuntu are you using and what kernel (type "uname -r" in a terminal)?

---

### Post by fobnicat on 2007-04-13
is the software compatible with ubuntu or are you running it through a windows emu like WINE?

---

### Post by kdemetter on 2007-04-13
if it's a problem with 3D , you can check if 3D hardware acceleration is enabled .

type : sudo glxinfo | grep rendering

it should say : direct rendering : Yes

---

### Post by findik1 on 2007-04-13
> **compmodder26 said:**
> What version of Ubuntu are you using and what kernel (type "uname -r" in a terminal)?

I was using ubuntu edgy , also tested on feisty
I typed your command but did not give anything , you mean just username -r?

---

### Post by tgm4883 on 2007-04-13
I would try installing the 3d drivers, I don't expect it to have any impact.  But I would rather make all things equal

---

### Post by findik1 on 2007-04-13
> **fobnicat said:**
> is the software compatible with ubuntu or are you running it through a windows emu like WINE?

yes it is compatible, I dont use windows emu ...

---

### Post by findik1 on 2007-04-13
> **kdemetter said:**
> if it's a problem with 3D , you can check if 3D hardware acceleration is enabled .

type : sudo glxinfo | grep rendering

it should say : direct rendering : Yes

kdemetter: how do I do that? In any case it should only improve the last column (3D), but of course I would like to improve that too.
thanjks

---

### Post by tgm4883 on 2007-04-13
no uname -r != username -r

do 
```
uname -r
```

---

### Post by findik1 on 2007-04-13
> **tgm4883 said:**
> I would try installing the 3d drivers, I don't expect it to have any impact.  But I would rather make all things equal

tgm4883: I agree with you. It would help on 3D part only. Any suggestion how to install 3d drivers?

---

### Post by findik1 on 2007-04-13
> **tgm4883 said:**
> no uname -r != username -r

do 
```
uname -r
```

that gave: 2.6.20-14-generic

---

### Post by tgm4883 on 2007-04-13
> **findik1 said:**
> tgm4883: I agree with you. It would help on 3D part only. Any suggestion how to install 3d drivers?

what video card?

---

### Post by tgm4883 on 2007-04-13
can we get an output of lspci and dmesg

---

### Post by jvc26 on 2007-04-13
```

lspci | grep "Display controller"

```
Would tell you that
Il

---

### Post by findik1 on 2007-04-13
> **Illuvator said:**
> ```

lspci | grep "Display controller"

```
Would tell you that
Il

Illuvator:
00:02.1 Display controller: Intel Corporation 82Q963/Q965 Integrated Graphics Controller (rev 02)

---

### Post by findik1 on 2007-04-13
> **tgm4883 said:**
> can we get an output of lspci and dmesg

00:00.0 Host bridge: Intel Corporation 82Q963/Q965 Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82Q963/Q965 Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation 82Q963/Q965 Integrated Graphics Controller (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5754 Gigabit Ethernet PCI Express (rev 02)


and dmesg gives:
[    0.000000] Linux version 2.6.20-14-generic (root@rothera) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Mon Apr 2 20:37:49 UTC 2007 (Ubuntu 2.6.20-14.22-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003f4ffc00 end: 000000003f5ffc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000003f5ffc00 size: 0000000000002000 end: 000000003f601c00 type: 4
[    0.000000] copy_e820_map() start: 000000003f603c00 size: 0000000000050000 end: 000000003f653c00 type: 2
[    0.000000] copy_e820_map() start: 000000003f653c00 size: 0000000000002000 end: 000000003f655c00 type: 3
[    0.000000] copy_e820_map() start: 000000003f655c00 size: 00000000009aa400 end: 0000000040000000 type: 2
[    0.000000] copy_e820_map() start: 00000000e0000000 size: 0000000010000000 end: 00000000f0000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000100400 end: 00000000fed00400 type: 2
[    0.000000] copy_e820_map() start: 00000000fed20000 size: 0000000000080000 end: 00000000feda0000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000100000 end: 00000000fef00000 type: 2
[    0.000000] copy_e820_map() start: 00000000ffb00000 size: 0000000000500000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f5ffc00 (usable)
[    0.000000]  BIOS-e820: 000000003f5ffc00 - 000000003f601c00 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f603c00 - 000000003f653c00 (reserved)
[    0.000000]  BIOS-e820: 000000003f653c00 - 000000003f655c00 (ACPI data)
[    0.000000]  BIOS-e820: 000000003f655c00 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] 117MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000fe710
[    0.000000] Entering add_active_range(0, 0, 259583) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   259583
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   259583
[    0.000000] On node 0 totalpages: 259583
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 235 pages used for memmap
[    0.000000]   HighMem zone: 29972 pages, LIFO batch:7
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v002 DELL                                  ) @ 0x000febf0
[    0.000000] ACPI: XSDT (v001 DELL    B8K     0x00000014 ASL  0x00000061) @ 0x000fce90
[    0.000000] ACPI: FADT (v003 DELL    B8K     0x00000014 ASL  0x00000061) @ 0x000fcfb8
[    0.000000] ACPI: SSDT (v001   DELL    st_ex 0x00001000 INTL 0x20050624) @ 0xfff6e4a9
[    0.000000] ACPI: MADT (v001 DELL    B8K     0x00000014 ASL  0x00000061) @ 0x000fd0ac
[    0.000000] ACPI: BOOT (v001 DELL    B8K     0x00000014 ASL  0x00000061) @ 0x000fd13e
[    0.000000] ACPI: ASF! (v032 DELL    B8K     0x00000014 ASL  0x00000061) @ 0x000fd166
[    0.000000] ACPI: MCFG (v001 DELL    B8K     0x00000014 ASL  0x00000061) @ 0x000fd1f8
[    0.000000] ACPI: HPET (v001 DELL    B8K     0x00000014 ASL  0x00000061) @ 0x000fd236
[    0.000000] ACPI: TCPA (v001 DELL    B8K     0x00000014 ASL  0x00000061) @ 0x000fd492
[    0.000000]   >>> ERROR: Invalid checksum
[    0.000000] ACPI: SLIC (v001 DELL    B8K     0x00000014 ASL  0x00000061) @ 0x000fd26e
[    0.000000] ACPI: SSDT (v001 DpgPmm  Cpu0Ist 0x00000011 INTL 0x20050624) @ 0x3f5ffc40
[    0.000000] ACPI: SSDT (v001 DpgPmm  Cpu1Ist 0x00000011 INTL 0x20050624) @ 0x3f600049
[    0.000000] ACPI: SSDT (v001 DpgPmm    CpuPm 0x00000010 INTL 0x20050624) @ 0x3f600452
[    0.000000] ACPI: DSDT (v001   DELL    dt_ex 0x00001000 INTL 0x20050624) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x05] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x07] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high level lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] Detected 1860.705 MHz processor.
[   11.189559] Built 1 zonelists.  Total pages: 257556
[   11.189562] Kernel command line: root=UUID=196a765e-09e0-4af0-8c6c-71d25b42d942 ro quiet splash
[   11.189690] mapped APIC to ffffd000 (fee00000)
[   11.189692] mapped IOAPIC to ffffc000 (fec00000)
[   11.189694] Enabling fast FPU save and restore... done.
[   11.189696] Enabling unmasked SIMD FPU exception support... done.
[   11.189704] Initializing CPU#0
[   11.189757] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   11.191230] Console: colour VGA+ 80x25
[   11.191541] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   11.191842] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   11.207986] Memory: 1018152k/1038332k available (1992k kernel code, 19396k reserved, 893k data, 328k init, 120828k highmem)
[   11.207994] virtual kernel memory layout:
[   11.207995]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   11.207996]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   11.207997]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   11.207998]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   11.207999]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   11.208000]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   11.208001]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   11.208004] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   11.208130] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   11.208134] hpet0: 3 64-bit timers, 14318180 Hz
[   11.209137] Using HPET for base-timer
[   11.288083] Calibrating delay using timer specific routine.. 3724.11 BogoMIPS (lpj=7448237)
[   11.288114] Security Framework v1.0.0 initialized
[   11.288118] SELinux:  Disabled at boot.
[   11.288131] Mount-cache hash table entries: 512
[   11.288233] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[   11.288240] monitor/mwait feature present.
[   11.288241] using mwait in idle threads.
[   11.288244] CPU: L1 I cache: 32K, L1 D cache: 32K
[   11.288247] CPU: L2 cache: 2048K
[   11.288249] CPU: Physical Processor ID: 0
[   11.288250] CPU: Processor Core ID: 0
[   11.288252] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
[   11.288259] Compat vDSO mapped to ffffe000.
[   11.288262] Remapping vsyscall page to ffffe000
[   11.288272] Checking 'hlt' instruction... OK.
[   11.304157] SMP alternatives: switching to UP code
[   11.304449] Early unpacking initramfs... done
[   11.587024] ACPI: Core revision 20060707
[   11.605003] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   11.731276] CPU0: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz stepping 02
[   11.731291] SMP alternatives: switching to SMP code
[   11.731351] Booting processor 1/1 eip 3000
[   11.741716] Initializing CPU#1
[   11.819748] Calibrating delay using timer specific routine.. 3721.36 BogoMIPS (lpj=7442739)
[   11.819755] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[   11.819760] monitor/mwait feature present.
[   11.819762] CPU: L1 I cache: 32K, L1 D cache: 32K
[   11.819764] CPU: L2 cache: 2048K
[   11.819766] CPU: Physical Processor ID: 0
[   11.819767] CPU: Processor Core ID: 1
[   11.819768] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
[   11.820221] CPU1: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz stepping 02
[   11.820239] Total of 2 processors activated (7445.48 BogoMIPS).
[   11.820376] ENABLING IO-APIC IRQs
[   11.820549] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   11.967657] checking TSC synchronization across 2 CPUs: passed.
[    0.003999] Brought up 2 CPUs
[    0.032554] migration_cost=23
[    0.032786] Booting paravirtualized kernel on bare hardware
[    0.032861] Time:  9:05:23  Date: 03/13/107
[    0.032885] NET: Registered protocol family 16
[    0.032958] EISA bus registered
[    0.032965] ACPI: bus type pci registered
[    0.066921] PCI: PCI BIOS revision 2.10 entry at 0xfb56f, last bus=3
[    0.066923] PCI: Using configuration type 1
[    0.066924] Setting up standard PCI resources
[    0.156194] ACPI: Interpreter enabled
[    0.156197] ACPI: Using IOAPIC for interrupt routing
[    0.162060] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.162068] PCI: Probing PCI hardware (bus 00)
[    0.162084] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[    0.172151] Boot video device is 0000:00:02.0
[    0.172660] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    0.172664] PCI quirk: region 0880-08bf claimed by ICH6 GPIO
[    0.173044] PCI: Transparent bridge - 0000:00:1e.0
[    0.173083] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    2.023011] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI4._PRT]
[    2.035485] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI2._PRT]
[    2.068755] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI5._PRT]
[    2.172925] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[    2.174678] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[    2.176410] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 12 15)
[    2.178189] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[    2.179943] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[    2.181708] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[    2.183469] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[    2.185199] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[    2.185621] Linux Plug and Play Support v0.97 (c) Adam Belay
[    2.185629] pnp: PnP ACPI init
[    2.275784] pnp: PnP ACPI: found 12 devices
[    2.275788] PnPBIOS: Disabled by ACPI PNP
[    2.275824] PCI: Using ACPI for IRQ routing
[    2.275826] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    2.285120] NET: Registered protocol family 8
[    2.285122] NET: Registered protocol family 20
[    2.303146] pnp: 00:01: ioport range 0x800-0x85f could not be reserved
[    2.303149] pnp: 00:01: ioport range 0xc00-0xc7f has been reserved
[    2.303151] pnp: 00:01: ioport range 0x860-0x8ff could not be reserved
[    2.303162] pnp: 00:0a: ioport range 0x100-0x1fe has been reserved
[    2.303164] pnp: 00:0a: ioport range 0x200-0x277 has been reserved
[    2.303166] pnp: 00:0a: ioport range 0x280-0x2e7 has been reserved
[    2.303169] pnp: 00:0a: ioport range 0x2f0-0x2f7 has been reserved
[    2.303171] pnp: 00:0a: ioport range 0x300-0x377 has been reserved
[    2.303173] pnp: 00:0a: ioport range 0x380-0x3bb has been reserved
[    2.303176] pnp: 00:0a: ioport range 0x3c0-0x3e7 could not be reserved
[    2.303178] pnp: 00:0a: ioport range 0x3f6-0x3f7 has been reserved
[    2.303421] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[    2.303425] PCI: Bridge: 0000:00:1c.0
[    2.303426]   IO window: disabled.
[    2.303430]   MEM window: dfc00000-dfcfffff
[    2.303434]   PREFETCH window: disabled.
[    2.303438] PCI: Bridge: 0000:00:1c.4
[    2.303439]   IO window: disabled.
[    2.303443]   MEM window: dfb00000-dfbfffff
[    2.303446]   PREFETCH window: disabled.
[    2.303450] PCI: Bridge: 0000:00:1e.0
[    2.303451]   IO window: disabled.
[    2.303455]   MEM window: disabled.
[    2.303458]   PREFETCH window: disabled.
[    2.303477] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[    2.303482] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    2.303497] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 16 (level, low) -> IRQ 16
[    2.303501] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[    2.303510] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    2.303531] NET: Registered protocol family 2
[    2.350778] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    2.350871] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    2.351261] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    2.351459] TCP: Hash tables configured (established 131072 bind 65536)
[    2.351462] TCP reno registered
[    2.366933] checking if image is initramfs... it is
[    2.927116] Freeing initrd memory: 6747k freed
[    2.927265] Simple Boot Flag at 0x7a set to 0x1
[    2.927666] audit: initializing netlink socket (disabled)
[    2.927680] audit(1176455126.772:1): initialized
[    2.927763] highmem bounce pool size: 64 pages
[    2.927833] VFS: Disk quotas dquot_6.5.1
[    2.927848] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.927888] io scheduler noop registered
[    2.927890] io scheduler anticipatory registered
[    2.927892] io scheduler deadline registered
[    2.927901] io scheduler cfq registered (default)
[    2.942750] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    2.942789] assign_interrupt_mode Found MSI capability
[    2.942792] Allocate Port Service[0000:00:1c.0:pcie00]
[    2.942824] Allocate Port Service[0000:00:1c.0:pcie02]
[    2.942928] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[    2.942964] assign_interrupt_mode Found MSI capability
[    2.942966] Allocate Port Service[0000:00:1c.4:pcie00]
[    2.942992] Allocate Port Service[0000:00:1c.4:pcie02]
[    2.943121] isapnp: Scanning for PnP cards...
[    3.295843] isapnp: No Plug & Play device found
[    3.314279] Real Time Clock Driver v1.12ac
[    3.314647] hpet_resources: 0xfed00000 is busy
[    3.314656] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    3.314773] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    3.315290] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    3.315437] mice: PS/2 mouse device common for all mice
[    3.315918] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    3.316107] input: Macintosh mouse button emulation as /class/input/input0
[    3.316137] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    3.316140] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    3.316390] PNP: No PS/2 controller found. Probing ports directly.
[    3.318959] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.318963] serio: i8042 AUX port at 0x60,0x64 irq 12
[    3.319057] EISA: Probing bus 0 at eisa.0
[    3.319067] Cannot allocate resource for EISA slot 2
[    3.319075] Cannot allocate resource for EISA slot 5
[    3.319077] Cannot allocate resource for EISA slot 6
[    3.319086] EISA: Detected 0 cards.
[    3.349217] TCP cubic registered
[    3.349225] NET: Registered protocol family 1
[    3.349244] Starting balanced_irq
[    3.349250] Using IPI No-Shortcut mode
[    3.349346] ACPI: (supports S0 S1 S3 S4 S5)
[    3.349386]   Magic number: 3:429:70
[    3.349615] Freeing unused kernel memory: 328k freed
[    3.349903] Time: tsc clocksource has been installed.
[    4.560478] Capability LSM initialized
[    4.595264] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    4.595271] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    4.905981] usbcore: registered new interface driver usbfs
[    4.906000] usbcore: registered new interface driver hub
[    4.911633] usbcore: registered new device driver usb
[    4.948297] USB Universal Host Controller Interface driver v3.0
[    4.948352] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[    4.948365] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[    4.948368] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    4.948468] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    4.948494] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000ff20
[    4.948592] usb usb1: configuration #1 chosen from 1 choice
[    4.948615] hub 1-0:1.0: USB hub found
[    4.948620] hub 1-0:1.0: 2 ports detected
[    4.989057] Floppy drive(s): fd0 is 1.44M
[    5.007999] FDC 0 is a post-1991 82077
[    5.050749] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 17 (level, low) -> IRQ 17
[    5.050760] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[    5.050763] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    5.050861] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    5.050887] uhci_hcd 0000:00:1a.1: irq 17, io base 0x0000ff00
[    5.051242] usb usb2: configuration #1 chosen from 1 choice
[    5.051358] hub 2-0:1.0: USB hub found
[    5.051364] hub 2-0:1.0: 2 ports detected
[    5.155595] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 18
[    5.155604] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    5.155607] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    5.155628] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[    5.155653] uhci_hcd 0000:00:1d.0: irq 18, io base 0x0000ff80
[    5.155722] usb usb3: configuration #1 chosen from 1 choice
[    5.155744] hub 3-0:1.0: USB hub found
[    5.155749] hub 3-0:1.0: 2 ports detected
[    5.260294] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 17
[    5.260303] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    5.260306] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    5.260329] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[    5.260350] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000ff60
[    5.260431] usb usb4: configuration #1 chosen from 1 choice
[    5.260454] hub 4-0:1.0: USB hub found
[    5.260460] hub 4-0:1.0: 2 ports detected
[    5.292370] usb 1-2: new low speed USB device using uhci_hcd and address 2
[    5.360798] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
[    5.360807] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    5.360810] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    5.360833] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[    5.360856] uhci_hcd 0000:00:1d.2: irq 19, io base 0x0000ff40
[    5.360943] usb usb5: configuration #1 chosen from 1 choice
[    5.360965] hub 5-0:1.0: USB hub found
[    5.360970] hub 5-0:1.0: 2 ports detected
[    5.461252] usb 1-2: configuration #1 chosen from 1 choice
[    5.465746] tg3.c:v3.72 (January 8, 2007)
[    5.465765] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[    5.465774] PCI: Setting latency timer of device 0000:02:00.0 to 64
[    5.486009] eth0: Tigon3 [partno(BCM95754) rev b002 PHY(5787)] (PCI Express) 10/100/1000Base-T Ethernet 00:19:b9:2c:f4:f5
[    5.486016] eth0: RXcsums[1] LinkChgREG[1] MIirq[1] ASF[0] Split[0] WireSpeed[1] TSOcap[1] 
[    5.486018] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    5.490785] SCSI subsystem initialized
[    5.494932] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 22 (level, low) -> IRQ 20
[    5.494942] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[    5.494946] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    5.494974] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[    5.495001] ehci_hcd 0000:00:1a.7: debug port 1
[    5.495006] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[    5.495015] ehci_hcd 0000:00:1a.7: irq 20, io mem 0xdfdfbc00
[    5.498893] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    5.498957] libata version 2.20 loaded.
[    5.498983] usb usb6: configuration #1 chosen from 1 choice
[    5.499008] hub 6-0:1.0: USB hub found
[    5.499015] hub 6-0:1.0: 4 ports detected
[    5.602566] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 18
[    5.602579] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    5.602583] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    5.602608] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[    5.602635] ehci_hcd 0000:00:1d.7: debug port 1
[    5.602641] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    5.602646] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xff980800
[    5.606519] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    5.606582] usb usb7: configuration #1 chosen from 1 choice
[    5.606605] hub 7-0:1.0: USB hub found
[    5.606611] hub 7-0:1.0: 6 ports detected
[    5.646898] usb 1-2: USB disconnect, address 2
[    5.647023] usbcore: registered new interface driver hiddev
[    5.713868] ata_piix 0000:00:1f.2: version 2.10ac1
[    5.713874] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    5.713896] ACPI: PCI Interrupt 0000:00:1f.2[C] -> GSI 20 (level, low) -> IRQ 21
[    5.713913] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    5.714227] ata1: SATA max UDMA/133 cmd 0x0001fe00 ctl 0x0001fe12 bmdma 0x0001fec0 irq 21
[    5.714249] ata2: SATA max UDMA/133 cmd 0x0001fe20 ctl 0x0001fe32 bmdma 0x0001fec8 irq 21
[    5.714259] scsi0 : ata_piix
[    5.884504] ata1.00: ATA-7: SAMSUNG HD160JJ/P, ZM100-34, max UDMA7
[    5.884508] ata1.00: 312500000 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    5.892536] ata1.00: configured for UDMA/133
[    5.892545] scsi1 : ata_piix
[    6.142372] usbcore: registered new interface driver usbhid
[    6.142376] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[    6.380031] usb 1-2: new low speed USB device using uhci_hcd and address 3
[    6.392323] ata2.00: ATAPI, max UDMA/100
[    6.549639] usb 1-2: configuration #1 chosen from 1 choice
[    6.565583] input: USB Optical Mouse as /class/input/input1
[    6.565606] input: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:1a.0-2
[    6.573736] ata2.00: configured for UDMA/100
[    6.573839] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HD160JJ/ ZM10 PQ: 0 ANSI: 5
[    6.595318] scsi 1:0:0:0: CD-ROM            SONY     DVD+-RW AW-Q160S KDS1 PQ: 0 ANSI: 5
[    6.615821] ata_piix 0000:00:1f.5: MAP [ P0 P2 P1 P3 ]
[    6.771040] ACPI: PCI Interrupt 0000:00:1f.5[C] -> GSI 20 (level, low) -> IRQ 21
[    6.771058] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[    6.771086] ata3: SATA max UDMA/133 cmd 0x0001fe40 ctl 0x0001fe52 bmdma 0x0001fed0 irq 21
[    6.771109] ata4: SATA max UDMA/133 cmd 0x0001fe60 ctl 0x0001fe72 bmdma 0x0001fed8 irq 21
[    6.771116] scsi2 : ata_piix
[    6.807309] usb 4-1: new low speed USB device using uhci_hcd and address 3
[    6.923877] scsi3 : ata_piix
[    7.015333] usb 4-1: configuration #1 chosen from 1 choice
[    7.068362] input: Dell Dell USB Keyboard as /class/input/input2
[    7.068372] input: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1d.1-1
[    7.115527] SCSI device sda: 312500000 512-byte hdwr sectors (160000 MB)
[    7.115537] sda: Write Protect is off
[    7.115538] sda: Mode Sense: 00 3a 00 00
[    7.115556] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.115596] SCSI device sda: 312500000 512-byte hdwr sectors (160000 MB)
[    7.115604] sda: Write Protect is off
[    7.115605] sda: Mode Sense: 00 3a 00 00
[    7.115617] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.115621]  sda:sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    7.120664] Uniform CD-ROM driver Revision: 3.20
[    7.120702] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    7.123768]  sda1 sda2 sda3 sda4
[    7.123907] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    7.123926] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    7.150279] sd 0:0:0:0: Attached scsi disk sda
[    7.394836] Attempting manual resume
[    7.394839] swsusp: Resume From Partition 8:4
[    7.394840] PM: Checking swsusp image.
[    7.395028] PM: Resume from disk failed.
[    7.426038] kjournald starting.  Commit interval 5 seconds
[    7.426044] EXT3-fs: mounted filesystem with ordered data mode.
[   18.772065] Linux agpgart interface v0.102 (c) Dave Jones
[   18.786717] agpgart: Detected an Intel 965Q Chipset.
[   18.787182] agpgart: Unknown page table size, assuming 512KB
[   18.787186] agpgart: Detected 7676K stolen memory.
[   18.799074] agpgart: AGP aperture is 256M @ 0xc0000000
[   18.945499] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   18.990114] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   18.999865] parport: PnPBIOS parport detected.
[   18.999919] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   19.134692] input: PC Speaker as /class/input/input3
[   19.141853] iTCO_vendor_support: vendor-support=0
[   19.142880] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   19.142964] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   19.142971] iTCO_wdt: No card detected
[   19.198565] NET: Registered protocol family 17
[   19.357285] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   19.357298] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   19.719590] lp0: using parport0 (interrupt-driven).
[   19.742650] Adding 2610552k swap on /dev/disk/by-uuid/9de8bcef-96ad-4b8a-8330-e8366f3c9e53.  Priority:-1 extents:1 across:2610552k
[   19.836688] EXT3 FS on sda3, internal journal
[   20.161876] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   20.228753] NTFS volume version 3.1.
[   21.983839] tg3: eth0: Link is up at 1000 Mbps, full duplex.
[   21.983843] tg3: eth0: Flow control is on for TX and on for RX.
[   25.075227] NET: Registered protocol family 10
[   25.075303] lo: Disabled Privacy Extensions
[   26.652448] input: Power Button (FF) as /class/input/input4
[   26.652468] ACPI: Power Button (FF) [PWRF]
[   26.652502] input: Power Button (CM) as /class/input/input5
[   26.652520] ACPI: Power Button (CM) [VBTN]
[   26.699778] Using specific hotkey driver
[   26.738239] No dock devices found.
[   26.791428] ibm_acpi: ec object not found
[   26.904899] pcc_acpi: loading...
[   32.030785] [drm] Initialized drm 1.1.0 20060810
[   32.032548] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   32.032594] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   32.039050] mtrr: type mismatch for c0000000,10000000 old: write-back new: write-combining
[   32.710650] ppdev: user-space parallel port driver
[   33.775518] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   33.775521] apm: disabled - APM is not SMP safe.
[   34.063651] Bluetooth: Core ver 2.11
[   34.063701] NET: Registered protocol family 31
[   34.063703] Bluetooth: HCI device and connection manager initialized
[   34.063706] Bluetooth: HCI socket layer initialized
[   34.093221] Bluetooth: L2CAP ver 2.8
[   34.093224] Bluetooth: L2CAP socket layer initialized
[   34.236636] Bluetooth: RFCOMM socket layer initialized
[   34.236649] Bluetooth: RFCOMM TTY layer initialized
[   34.236651] Bluetooth: RFCOMM ver 1.8
[   45.284168] eth0: no IPv6 routers present
[  269.300181] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  273.297463] tg3: eth0: Link is up at 1000 Mbps, full duplex.
[  273.297467] tg3: eth0: Flow control is on for TX and on for RX.
[  273.299641] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  284.117259] eth0: no IPv6 routers present
[  381.234143] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  385.234065] tg3: eth0: Link is up at 1000 Mbps, full duplex.
[  385.234070] tg3: eth0: Flow control is on for TX and on for RX.
[  385.234082] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  401.074438] eth0: no IPv6 routers present
[  901.319955] usb 6-3: new high speed USB device using ehci_hcd and address 3
[  901.548036] usb 6-3: configuration #1 chosen from 1 choice
[  901.625740] usbcore: registered new interface driver libusual
[  901.633420] Initializing USB Mass Storage driver...
[  901.633612] scsi4 : SCSI emulation for USB Mass Storage devices
[  901.633787] usbcore: registered new interface driver usb-storage
[  901.633860] USB Mass Storage support registered.
[  901.634000] usb-storage: device found at 3
[  901.634003] usb-storage: waiting for device to settle before scanning
[  906.640390] usb-storage: device scan complete
[  906.641141] scsi 4:0:0:0: Direct-Access              USB Flash Memory 1.00 PQ: 0 ANSI: 2
[  906.648987] SCSI device sdb: 1001472 512-byte hdwr sectors (513 MB)
[  906.649610] sdb: Write Protect is off
[  906.649613] sdb: Mode Sense: 0b 00 00 08
[  906.649615] sdb: assuming drive cache: write through
[  906.657481] SCSI device sdb: 1001472 512-byte hdwr sectors (513 MB)
[  906.658104] sdb: Write Protect is off
[  906.658107] sdb: Mode Sense: 0b 00 00 08
[  906.658109] sdb: assuming drive cache: write through
[  906.658111]  sdb: sdb1
[  906.659158] sd 4:0:0:0: Attached scsi removable disk sdb
[  906.659198] sd 4:0:0:0: Attached scsi generic sg2 type 0

---

### Post by kdemetter on 2007-04-13
just type it in a console window

sudo glxinfo | grep rendering

however , this only checks if the 3D acceleration is on . 
if it says No than yes have to install the drivers . 

But what kind of graphics card are you using ?

---

### Post by findik1 on 2007-04-13
> **tgm4883 said:**
> what video card?

tgm4883:
I guess this: 
00:02.1 Display controller: Intel Corporation 82Q963/Q965 Integrated Graphics Controller (rev 02)

---

### Post by kdemetter on 2007-04-13
from what i can see , this is you GPU :

Intel Corporation 82Q963/Q965 Integrated Graphics Controller (rev 02)

---

### Post by findik1 on 2007-04-13
yes I guess so

---

### Post by lamalex on 2007-04-13
> **findik1 said:**
> yes. Ubuntu is working perfectly fine on the computer. The only thing is I would not expect ubuntu would do well in graphics (since no specific graphic accelarator or graphic driver I installed in ubuntu), so as you see  ubuntu was very poor on 3D (LAST COLUMN, 3D imaging) compared to others on that issue. But still in some mathematical calculations , it is still slower than win2000(see, column 1 to 5.

why is everyone focusing on graphics? That's the least important part of this, the question is why isn't his processor working at full speed. I would suggest making sure the processor is scaling itself properly. Add the cpu frequency scaling monitor to a panel and see what it does. It's possible that your processor isn't being scaled correctly.

---

### Post by findik1 on 2007-04-13
> **kdemetter said:**
> just type it in a console window

sudo glxinfo | grep rendering

however , this only checks if the 3D acceleration is on . 
if it says No than yes have to install the drivers . 

But what kind of graphics card are you using ?

kdemetter;
It gave:
direct rendering: Yes
I guess Intel (default one) as can be seen from my other replies

---

### Post by kdemetter on 2007-04-13
yes , i know , sorry , i reacted to slowly

---

### Post by findik1 on 2007-04-13
> **Iamalex said:**
> why is everyone focusing on graphics? That's the least important part of this, the question is why isn't his processor working at full speed. I would suggest making sure the processor is scaling itself properly. Add the cpu frequency scaling monitor to a panel and see what it does. It's possible that your processor isn't being scaled correctly.

Iamalex: I COMPLETELY agree with you. I do scientific computation with this machine, nothing else. so graphic card is least priority. 

How do I do scaling property? THis may be important indeed. I heard this also help for power manager.

---

### Post by lamalex on 2007-04-13
install that applet and run some calculations, see if your processor is maxing at a lower frequency than it should be, I have seen people get capped at like 800mhz. What kind of processor are you using (exact make/model would be good).

---

### Post by hosk on 2007-04-13
is your processor a dual core?  I'm not sure if you would still need to recompile the kernel or if it's supported right out of the box for multiple procs, but I remember you had to recompile 2.4 for MP support.

stare at some system monitoring software when you benchmark, maybe?

---

### Post by compmodder26 on 2007-04-13
No it's a P4 Hyperthreading.  No dual core.  And anyway, the generic kernel supports multiple cores and hyperthreading.  That shouldn't be the issue.  I'm inclined to agree with Iamalex's idea.

---

### Post by maniacmusician on 2007-04-13
you can type "cat /proc/cpuinfo" to see what speed your processor is running at during the calculations. If it's not achieving its maximum speed, that's probably the problem.

---

### Post by findik1 on 2007-04-13
> **Iamalex said:**
> install that applet and run some calculations, see if your processor is maxing at a lower frequency than it should be, I have seen people get capped at like 800mhz. What kind of processor are you using (exact make/model would be good).

OK, which applet am I installing? from Synaptic I found:
cpudyn
cpufreqd
emifreq-applet

When I tried to install(cpudyn cpufreq) it automatically try to UNinstall powernowd. I guess it is OK to uninstall powernowd , since I remember from some webpage to do scaling (for powermanager) it was saying to uninstall first powernowd. Should I go ahaed?

The one that I am using one in  this lab right now has similar problem with speed and it is intel core 2 duo. To get more spec I meed to reboot to windows? or is there some utility to check on ubuntu?
thanks

---

### Post by lamalex on 2007-04-13
my idea or maniac's are the same thing, i would do
```
watch cat /proc/cpuinfo
```

---

### Post by tgm4883 on 2007-04-13
> **compmodder26 said:**
> No it's a P4 Hyperthreading.  No dual core.  And anyway, the generic kernel supports multiple cores and hyperthreading.  That shouldn't be the issue.  I'm inclined to agree with Iamalex's idea.

See, now thats a problem.  The dmesg output lists this 

```
**[ 11.731276] CPU0: Intel(R) Core(TM)2 CPU 6300 @ 1.86GHz stepping 02**
[ 11.731291] SMP alternatives: switching to SMP code
[ 11.731351] Booting processor 1/1 eip 3000
[ 11.741716] Initializing CPU#1
[ 11.819748] Calibrating delay using timer specific routine.. 3721.36 BogoMIPS (lpj=7442739)
[ 11.819755] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[ 11.819760] monitor/mwait feature present.
[ 11.819762] CPU: L1 I cache: 32K, L1 D cache: 32K
[ 11.819764] CPU: L2 cache: 2048K
[ 11.819766] CPU: Physical Processor ID: 0
[ 11.819767] CPU: Processor Core ID: 1
[ 11.819768] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
**[ 11.820221] CPU1: Intel(R) Core(TM)2 CPU 6300 @ 1.86GHz stepping 02**
[ 11.820239] Total of 2 processors activated (7445.48 BogoMIPS).
```

And unless im mistaken, thats not a P4 dual core hyperthreading cpu

:EDIT:

> **findik1 said:**
> OK, which applet am I installing? from Synaptic I found:
cpudyn
cpufreqd
emifreq-applet

When I tried to install(cpudyn cpufreq) it automatically try to UNinstall powernowd. I guess it is OK to uninstall powernowd , since I remember from some webpage to do scaling (for powermanager) it was saying to uninstall first powernowd. Should I go ahaed?

The one that I am using one in  this lab right now has similar problem with speed and it is intel core 2 duo. To get more spec I meed to reboot to windows? or is there some utility to check on ubuntu?
thanks

You can't tell us it's a P4 3Ghz Hyperthreading cpu then run commands on a different computer (with a different cpu)

---

### Post by compmodder26 on 2007-04-13
No, that would suggest otherwise.  I didn't see that, I was just going off of the OP's first post in this thread.

edit: but it does show that both cores are being utilized.  I'm still inclined to think it is a scaling issue.

---

### Post by hosk on 2007-04-13
> **compmodder26 said:**
> I'm inclined to agree with Iamalex's idea.

after a little research, i am too.

[http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/](http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/)

---

### Post by lamalex on 2007-04-13
hahah wtf?? are you sure you have a P4 and not a core2duo? I mean, that's a dumb question .... but .. Ubuntu needs to be asked it.

---

### Post by findik1 on 2007-04-13
> **compmodder26 said:**
> No it's a P4 Hyperthreading.  No dual core.  And anyway, the generic kernel supports multiple cores and hyperthreading.  That shouldn't be the issue.  I'm inclined to agree with Iamalex's idea.

I agree, It is P4 HT. But I should have said: right now I am in different machine in this lab with intel core 2 duo (but similar problem with matlab, slower in ubuntu) Yes I am trying to follow lamalex's idea

---

### Post by findik1 on 2007-04-13
> **maniacmusician said:**
> you can type "cat /proc/cpuinfo" to see what speed your processor is running at during the calculations. If it's not achieving its maximum speed, that's probably the problem.

It gave(I am on a different machine right now but matlab is still slower in this machine too compared to win): :D I love this community. It really great help for a beginner like me(I hope I dont take you time much).:D  Even I cannot respond to all of you that quickly.

Here:
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz
stepping        : 2
cpu MHz         : 1600.000
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 3724.11
clflush size    : 64

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz
stepping        : 2
cpu MHz         : 1600.000
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 3721.36
clflush size    : 64

---

### Post by lamalex on 2007-04-13
in Ubuntu you should try using Octave instad of matlab. It works much better and supports matlab files. [http://www.gnu.org/software/octave/](http://www.gnu.org/software/octave/)

---

### Post by tgm4883 on 2007-04-13
Im thinking a scaling problem too as two errors were thrown

ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present

---

### Post by compmodder26 on 2007-04-13
> **findik1 said:**
> It gave(I am on a different machine right now but matlab is still slower in this machine too compared to win): :D I love this community. It really great help for a beginner like me(I hope I dont take you time much).:D  Even I cannot respond to all of you that quickly.

Here:
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz
stepping        : 2
cpu MHz         : 1600.000
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 3724.11
clflush size    : 64

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz
stepping        : 2
cpu MHz         : 1600.000
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 3721.36
clflush size    : 64

It does appear that your processor is being scaled down.  Its at 1600 MHZ in both cores, when it should be at 1860 MHZ.

---

### Post by lamalex on 2007-04-13
problem discovered! Too bad now we need to figure out how to fix it. That will probably be a bit harder

---

### Post by findik1 on 2007-04-13
OK guys, sorry for the confusion. I did that test and saved that screenshot file on different machine with P4 HT (3.2GHz). But situation was the same on this machine too. (This machine is not that "far" different from that one). I can test here and send you the results later.

As people suggested, it may be related to frequency scaling and will look for that

---

### Post by compmodder26 on 2007-04-13
On my laptop, I can control the scaling of my Core 2 Duo processor through "/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor" and "/sys/devices/system/cpu/cpu1/cpufreq/scaling_governor".  These files determine how scaling should be done.

To have it use the max frequency I use this command:

```
echo "performance" >/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor && echo "performance" >/sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
```

---

### Post by tgm4883 on 2007-04-13
> **compmodder26 said:**
> It does appear that your processor is being scaled down.  Its at 1600 MHZ in both cores, when it should be at 1860 MHZ.

> **Iamalex said:**
> problem discovered! Too bad now we need to figure out how to fix it. That will probably be a bit harder

I'm not too sure about that, i have the exact same processor which idle's at 1.6 Ghz (85%), but under full load does do 1.86 Ghz.  So I could see his problem maybe being a scaling issue where it is not getting to full speed at full load, but my guess is that he ran that command at idle.

---

### Post by compmodder26 on 2007-04-13
Could very well be.  Could it be possible that the benchmark isn't stressing the CPU enough to make it scale up?

---

### Post by lamalex on 2007-04-13
is matlab being slower on both machines or just the P4 machine, is the P4 machine identifying the processor correctly?

---

### Post by tgm4883 on 2007-04-13
> **compmodder26 said:**
> On my laptop, I can control the scaling of my Core 2 Duo processor through "/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor" and "/sys/devices/system/cpu/cpu1/cpufreq/scaling_governor".  These files determine how scaling should be done.

To have it use the max frequency I use this command:

```
echo "performance" >/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor && echo "performance" >/sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
```

I get permission denied no matter how I run that command

---

### Post by compmodder26 on 2007-04-13
sorry forgot to say you need to do it as root.

---

### Post by tgm4883 on 2007-04-13
> **Iamalex said:**
> is matlab being slower on both machines or just the P4 machine, is the P4 machine identifying the processor correctly?

To add on to this, have you tried matlab in windows on the core 2 duo machine?  Is matlab a multithreaded application?  Is matlab a 64 bit application?  Are you running a 64 bit version windows?  Are you running a 64 bit version of ubuntu?

---

### Post by tgm4883 on 2007-04-13
> **compmodder26 said:**
> sorry forgot to say you need to do it as root.

Unless there is something better than sudo I tried that

---

### Post by compmodder26 on 2007-04-13
hmm.... I wonder why it works on mine and not yours.  Try editing the file in nano or vi.  It should just have one line (default is "ondemand").  Just clear that line and type "performance".  Do that for both files I mentioned above.  If that doesn't work as root, then I don't know what to say.

---

### Post by lamalex on 2007-04-13
you might need to do
```
sudo echo "performance" >/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor && sudo echo "performance" >/sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
```or
```
sudo echo "performance" >/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
sudo echo "performance" >/sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
```

---

### Post by tgm4883 on 2007-04-13
> **Iamalex said:**
> you might need to do
```
sudo echo "performance" >/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor && sudo echo "performance" >/sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
```or
```
sudo echo "performance" >/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
sudo echo "performance" >/sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
```

Unfortunatly that is the command i tried

---

### Post by compmodder26 on 2007-04-13
Try the method I posted above about using an editor

---

### Post by tgm4883 on 2007-04-13
trying that now, weird as it says it's opening the file, but opens a blank file.  I can see the ondemand in the icon if i look at the file from nautilus, but if i open it it still opens a blank file.  weird.

---

### Post by tgm4883 on 2007-04-13
also failed at doing the commands seperatly

---

### Post by findik1 on 2007-04-13
> **tgm4883 said:**
> To add on to this, have you tried matlab in windows on the core 2 duo machine?  Is matlab a multithreaded application?  Is matlab a 64 bit application?  Are you running a 64 bit version windows?  Are you running a 64 bit version of ubuntu?

OK , sorry I am slow in response.

Now again I am on core 2 machine, switch to windows (xp on it) as you asked

I run matlab bench. and again it gave this machine as top! I can show you the result if there is a way of getting screenshot of it. I did not see on ms paint. You have to trust me.

I dont know whether matlab is multithreaded application
matlab is 32
machine is 32

---

### Post by devnulljp on 2007-04-13
> **findik1 said:**
> I was using ubuntu edgy , also tested on feisty
I typed your command but did not give anything , you mean just username -r?
No, type exactly **uname -r** at a terminal
What do you mean it did not give anything? Where did you type it? If you actually typed uname -r and it gave nothing in repsonse, I think you're in trouble
I don't want to be mean or anything, but it sounds like the problem you have is something to do with your lack of familiarity with linux and maybe better familiarity with windows?

My guess is you are not using the correct kernel for your hardware, but probably a generic 386 kernel. Also, you need to install and correctly configure your video drivers for your hardware -- this is necessary on linux and not on windows because of patents & trade secrets and corporate deals done between video card manufacturers and microsoft that are not available to the rest of us.

---

### Post by tgm4883 on 2007-04-13
I dont think we need a screenshot, but you get one by hitting printscreen, opening up ms paint and doing an edit paste, then saving as a pic file.

your using ubuntu 32 bit right?

---

### Post by compmodder26 on 2007-04-13
> **devnulljp said:**
> No, type exactly uname -r at a terminal
What do you mean it did not give anything? Where did you type it?
I don't want to be mean or anything, but it sounds like the problem you have is mor eto do with your familiarity with windows and lack of familiarity with linux.

My guess is you are not using the correct kernel for your hardware, but probably a generic 386 kernel. Also, you need to install and correctly configure your video drivers for your hardware -- this is necessary on linux and not on windows because of patents & trade secrets and corporate deals done between video card manufacturers and microsoft that are not available to the rest of us.

I suspect you may have missed a few pages of this thread.

---

### Post by tgm4883 on 2007-04-13
> **devnulljp said:**
> No, type exactly uname -r at a terminal
What do you mean it did not give anything? Where did you type it?
I don't want to be mean or anything, but it sounds like the problem you have is mor eto do with your familiarity with windows and lack of familiarity with linux.

My guess is you are not using the correct kernel for your hardware, but probably a generic 386 kernel. Also, you need to install and correctly configure your video drivers for your hardware -- this is necessary on linux and not on windows because of patents & trade secrets and corporate deals done between video card manufacturers and microsoft that are not available to the rest of us.

Way to go, you made it through the first page before hitting the reply button.  Now if you would only have saw the first 3 posts on the second page you would have noticed this

> that gave: 2.6.20-14-generic

And what is the correct kernel for either a P4 3Ghz HT cpu or a Core 2 Duo? (Both running 32 bit)

---

### Post by compmodder26 on 2007-04-13
> **tgm4883 said:**
> trying that now, weird as it says it's opening the file, but opens a blank file.  I can see the ondemand in the icon if i look at the file from nautilus, but if i open it it still opens a blank file.  weird.

Try opening the files from the command line.

---

### Post by findik1 on 2007-04-13
> **tgm4883 said:**
> To add on to this, have you tried matlab in windows on the core 2 duo machine?  Is matlab a multithreaded application?  Is matlab a 64 bit application?  Are you running a 64 bit version windows?  Are you running a 64 bit version of ubuntu?

> **findik1 said:**
> OK , sorry I am slow in response.

Now again I am on core 2 machine, switch to windows (xp on it) as you asked

I run matlab bench. and again it gave this machine as top! I can show you the result if there is a way of getting screenshot of it. I did not see on ms paint. You have to trust me.

I dont know whether matlab is multithreaded application
matlab is 32
machine is 32


I will do scaling 
but first I checked matlab again, I was trying to test now matlab on ubuntu on this machine (core duo) . Now I see that matlab graphical interface does not work properly after this morning I upgraded to feisty!. Does anyone know how to start  matlab without graphical interface, but just from a terminal (>> )

---

### Post by tgm4883 on 2007-04-13
> **compmodder26 said:**
> Try opening the files from the command line.

Tried that to.  Im starting to wonder if I can't access it because of gnome-power-manager or something?

---

### Post by compmodder26 on 2007-04-13
Not sure.  It does seem odd to me.  Root shouldn't be denied on anything.

---

### Post by findik1 on 2007-04-13
> **tgm4883 said:**
> I dont think we need a screenshot, but you get one by hitting printscreen, opening up ms paint and doing an edit paste, then saving as a pic file.

your using ubuntu 32 bit right?

yes 32 bit

---

### Post by tgm4883 on 2007-04-13
> **compmodder26 said:**
> Not sure.  It does seem odd to me.  Root shouldn't be denied on anything.

I know !  it tells me permission denied and im like What!?!  Im root dammit

---

### Post by findik1 on 2007-04-13
> **tgm4883 said:**
> I know !  it tells me permission denied and im like What!?!  Im root dammit

Do you have this kind of problem? Maybe it helps, but not sure.

[http://ubuntuforums.org/showthread.php?t=151941](http://ubuntuforums.org/showthread.php?t=151941)

---

### Post by tgm4883 on 2007-04-13
> **findik1 said:**
> Do you have this kind of problem? Maybe it helps, but not sure.

[http://ubuntuforums.org/showthread.php?t=151941](http://ubuntuforums.org/showthread.php?t=151941)

got halfway through that thread and thought, hmm maybe it's some sort of graphical editor problem.  opened a terminal, used nano and it opened right up.  changed each file and now im 1.87Ghz all the time.

```
thomas@poseidon:/sys/devices/system/cpu/cpu0/cpufreq$ cat /proc/cpuinfoprocessor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz
stepping        : 2
cpu MHz         : 1867.000
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx lm constant_tsc pni monitor ds_cpl vmx est tm2 cx16 xtpr lahf_lm
bogomips        : 3736.68
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz
stepping        : 2
cpu MHz         : 1867.000
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx lm constant_tsc pni monitor ds_cpl vmx est tm2 cx16 xtpr lahf_lm
bogomips        : 3733.46
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

```

So back on topic, it could be a combination of things.  and im starting to think that the OP should use another benchmarking program to verify his results of matlab.

---

### Post by thefoolisme on 2007-04-13
I would try different benchmarking programs.  The only reason I suggest this is because I recently did a benchmarking project for a class I'm taking.  Ubuntu vs. Xubuntu vs. Windows XP.  I used Metabench and SiSoft Sandra through Wine so I get the same programs on both OSs.  I thought the emulation through Wine might slow down the results, and was prepared for that.  What I wasn't prepared for was that the linux distros came in first in every test, even going through Wine.  Granted, this is XP, which is more bloated than 2000, but I was fascinated by the fact that XP couldn't win.  My guess is that something is causing the slowdown.  Too much of a noob to know what it is, but I can't imagine that Ubuntu would be that much slower than 2000, when it kicked XP's butt in my tests.  :-)

---

### Post by Tachyon1000 on 2007-04-13
Has anyone considered placing the blame on the producers of Matlab for Linux rather than the operating system?

---

### Post by tgm4883 on 2007-04-13
> **Tachyon1000 said:**
> Has anyone considered placing the blame on the producers of Matlab for Linux rather than the operating system?

Isn't that what were talking about now?  that we should verify results with a different benchmarking app

---

### Post by lamalex on 2007-04-13
I guess no one read my post telling him to try Octave. Because, it was implied, at least I though so.

---

### Post by findik1 on 2007-04-13
> **Iamalex said:**
> I guess no one read my post telling him to try Octave. Because, it was implied, at least I though so.


there was no blaming on linux. matlab should work almost at the same speed on both operating systems and I am trying to improve its performance on linux. As you suggested there are some issues (freq scaling) already taken care of in windows but as a linux beginners we need to know from somebody else how to take care of these things for linux. We are endusers not developers and I dont know why these things already taken care of at the beginning. I would be very happy as a linux beginners to be pointed out so that we learn more in software(and hardware) instead of focusing some fancy utilities like "desktop effects" as come from feisty. I know that it is/may be a good feature but that's not the whole point. I believe many people do not use linux features and many people even dont know their system is slower than windows due to a need for a small adjustment.

I can try Octove but not now.

---

### Post by lamalex on 2007-04-13
for most people everything works fine, which is why most people can focus on just fun things like                                desktop effects and that kind of stuff. As for octave, it's a good program. Give it a try.

---

### Post by tgm4883 on 2007-04-13
> **findik1 said:**
> there was no blaming on linux. matlab should work almost at the same speed on both operating systems and I am trying to improve its performance on linux. As you suggested there are some issues (freq scaling) already taken care of in windows but as a linux beginners we need to know from somebody else how to take care of these things for linux. We are endusers not developers and I dont know why these things already taken care of at the beginning. I would be very happy as a linux beginners to be pointed out so that we learn more in software(and hardware) instead of focusing some fancy utilities like "desktop effects" as come from feisty. I know that it is/may be a good feature but that's not the whole point. I believe many people do not use linux features and many people even dont know their system is slower than windows due to a need for a small adjustment.

I can try Octove but not now.

Just try another benchmarking program.  We are trying to see if it is your setup that is slow, or poor programming in matlab.

---

### Post by findik1 on 2007-04-14
> **hosk said:**
> after a little research, i am too.

[http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/](http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/)


I followed up the CPU scaling from here:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

they suggest it for power manager, it should be helpful to power manager for laptops especially.

---

### Post by findik1 on 2007-04-14
> **tgm4883 said:**
> Unfortunatly that is the command i tried

> **maniacmusician said:**
> you can type "cat /proc/cpuinfo" to see what speed your processor is running at during the calculations. If it's not achieving its maximum speed, that's probably the problem.

Now I am on P4 HT machine again, as seen below. I also did frequency scaling from the web page that I sent you just 10 min ago but did not change "matlab" results. OK I assume for now it is matlab is responsible for slow speed.

[PHP]processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Pentium(R) 4 CPU 3.20GHz
stepping        : 3
cpu MHz         : 3200.000
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc up pni monitor ds_cpl est cid cx16 xtpr
bogomips        : 6389.84
[/PHP]

---

### Post by ToohTaah on 2007-04-16
Using a real application to benchmark the system is a good idea since you are really using that application on daily basis. I used a small program written by my colleague to perform matrix times matrix to measure the speed of my system since my work will mostly rely on matrix time matrix tasks.

I have 2 questions though.

1. Are the version of MatLAB on both Linux and Windows the same?
2. When you said win2k is much faster, can you give us some pictures of how much faster you got?

---

