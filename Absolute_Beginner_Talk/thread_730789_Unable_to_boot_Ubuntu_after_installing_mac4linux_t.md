---
title: "Unable to boot Ubuntu after installing mac4linux themes!"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by mrdosa on 2008-03-21
I have a dual boot ubuntu xp system. I was able to boot normally till now using grub. Morning I installe d many themes from mac4linux project. It worked great, but now, when I select ubuntu,after the ubuntu logo, the screen goes black, and nothing happens. I have to reboot. I can boot only from recovery mode. After choosing recovery mode, I have to type nothing, but just exit. And it boots normally!
Please help me out. Is there any way I can log these errors?:(

---

### Post by Tomatz on 2008-03-21
Try moving the mac4linux theme from the ~/.themes directory then reboot into normal mode :)

---

### Post by Tomatz on 2008-03-21
~/.themes is /home/USERNAME/.themes   :)

---

### Post by mrdosa on 2008-03-21
Where should I move them to? I mean, will I loose the Mac look if I move them to say, the home folder??

Now sometimes I get weird colored vertical lines, and nothing happens...but when booting from recovery mode everything works fine, even the themes work well.

---

### Post by Tomatz on 2008-03-21
Just move them out of the .themes folder then see if gdm will start correctly :)

And yes you will loose your mac look temporarily but at least your system might work

---

### Post by mrdosa on 2008-03-21
I tried that but still no improvement. It sometimes boots properly, other times I get a screen with vertical lines or a dark screen and nothing happens. This happens after the Ubuntu boot screen.
 Heres a screen shot:
[http://img148.imageshack.us/img148/2618/dsc00117hp8.jpg](http://img148.imageshack.us/img148/2618/dsc00117hp8.jpg)

[[IMG]http://img148.imageshack.us/img148/2618/dsc00117hp8.jpg[/IMG]](http://imageshack.us)

---

### Post by Tomatz on 2008-03-21
Thats funky :confused:

When installing the theme were there specific instructions for installing it that differ from the standard way of installing a theme? 

maby you could post me a link to the exact version of mac4lin

:)

---

### Post by mrdosa on 2008-03-21
Here is the link. 
[http://sourceforge.net/projects/mac4lin/](http://sourceforge.net/projects/mac4lin/)

The documentation file has the instructions which I followed. Everything worked fine for two days. And now suddenly this!! Dont know what went wrong? is there any logs which I can post, which will help you solve my prob!?

---

### Post by n6yga on 2008-03-21
I see that the theme comes with a Usplash. That could be the problem. Just my .02.

Mark.

---

### Post by mrdosa on 2008-03-21
> **n6yga said:**
> I see that the theme comes with a Usplash. That could be the problem. Just my .02.

Mark.

I didnt get you! Whats that?:(

---

### Post by Tomatz on 2008-03-21
To me it looks like a graphics problem though i have never come across anything like it.  Its weird because you can see the mouse pointer you would think that would be corrupted with the rest of the display.

Try the mac4lin forum:

[http://sourceforge.net/forum/forum.php?forum_id=730185](http://sourceforge.net/forum/forum.php?forum_id=730185)

Or hang on here for a guru :lolflag:

---

### Post by Tomatz on 2008-03-21
> **n6yga said:**
> I see that the theme comes with a Usplash. That could be the problem. Just my .02.

Mark.

Good point :)

---

### Post by Tomatz on 2008-03-21
a usplash is the picture/logo you see while booting

---

### Post by mrdosa on 2008-03-21
Thanks. I will hang on here for a while. Then move onto some other forum.

---

### Post by mrdosa on 2008-03-21
This is the system log when my screen got all funky!! Hope this helps solve the prob!:(





Mar 22 01:34:41 mybuntu syslogd 1.4.1#21ubuntu3: restart.
Mar 22 01:34:41 mybuntu kernel: Inspecting /boot/System.map-2.6.22-14-generic
Mar 22 01:34:42 mybuntu kernel: Loaded 25445 symbols from /boot/System.map-2.6.22-14-generic.
Mar 22 01:34:42 mybuntu kernel: Symbols match kernel version 2.6.22.
Mar 22 01:34:42 mybuntu kernel: No module symbols loaded - kernel modules not enabled. 
Mar 22 01:34:42 mybuntu kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
Mar 22 01:34:42 mybuntu kernel: [    0.000000] BIOS-provided physical RAM map:
Mar 22 01:34:42 mybuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Mar 22 01:34:42 mybuntu kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Mar 22 01:34:42 mybuntu kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Mar 22 01:34:42 mybuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000277f0000 (usable)
Mar 22 01:34:42 mybuntu kernel: [    0.000000]  BIOS-e820: 00000000277f0000 - 00000000277f3000 (ACPI NVS)
Mar 22 01:34:42 mybuntu kernel: [    0.000000]  BIOS-e820: 00000000277f3000 - 0000000027800000 (ACPI data)
Mar 22 01:34:42 mybuntu kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Mar 22 01:34:42 mybuntu kernel: [    0.000000] 0MB HIGHMEM available.
Mar 22 01:34:42 mybuntu kernel: [    0.000000] 631MB LOWMEM available.
Mar 22 01:34:42 mybuntu kernel: [    0.000000] found SMP MP-table at 000f5f00
Mar 22 01:34:42 mybuntu kernel: [    0.000000] Entering add_active_range(0, 0, 161776) 0 entries of 256 used
Mar 22 01:34:42 mybuntu kernel: [    0.000000] Zone PFN ranges:
Mar 22 01:34:42 mybuntu kernel: [    0.000000]   DMA             0 ->     4096
Mar 22 01:34:42 mybuntu kernel: [    0.000000]   Normal       4096 ->   161776
Mar 22 01:34:42 mybuntu kernel: [    0.000000]   HighMem    161776 ->   161776
Mar 22 01:34:42 mybuntu kernel: [    0.000000] early_node_map[1] active PFN ranges
Mar 22 01:34:42 mybuntu kernel: [    0.000000]     0:        0 ->   161776
Mar 22 01:34:42 mybuntu kernel: [    0.000000] On node 0 totalpages: 161776
Mar 22 01:34:42 mybuntu kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Mar 22 01:34:42 mybuntu kernel: [    0.000000]   DMA zone: 0 pages reserved
Mar 22 01:34:42 mybuntu kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Mar 22 01:34:42 mybuntu kernel: [    0.000000]   Normal zone: 1231 pages used for memmap
Mar 22 01:34:42 mybuntu kernel: [    0.000000]   Normal zone: 156449 pages, LIFO batch:31
Mar 22 01:34:42 mybuntu kernel: [    0.000000]   HighMem zone: 0 pages used for memmap
Mar 22 01:34:42 mybuntu kernel: [    0.000000] DMI 2.3 present.
Mar 22 01:34:42 mybuntu kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F7DA0 checksum 0
Mar 22 01:34:42 mybuntu kernel: [    0.000000] ACPI: RSDP 000F7DA0, 277F3000 (r2 IntelR)
Mar 22 01:34:42 mybuntu kernel: [    0.000000] ACPI Warning (tbutils-0453): BIOS XSDT has NULL entry,using RSDT [20070126]
Mar 22 01:34:42 mybuntu kernel: [    0.000000] ACPI: RSDT 277F3000, 002C (r1 IntelR AWRDACPI 42302E31 AWRD        1)
Mar 22 01:34:42 mybuntu kernel: [    0.000000] ACPI: FACP 277F3040, 0074 (r1 IntelR AWRDACPI 42302E31 AWRD        1)
Mar 22 01:34:42 mybuntu kernel: [    0.000000] ACPI: DSDT 277F30C0, 3971 (r1 INTELR AWRDACPI     1000 MSFT  100000D)
Mar 22 01:34:42 mybuntu kernel: [    0.000000] ACPI: FACS 277F0000, 0040
Mar 22 01:34:42 mybuntu kernel: [    0.000000] ACPI: APIC 277F6A40, 0068 (r1 IntelR AWRDACPI 42302E31 AWRD        1)
Mar 22 01:34:42 mybuntu kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Mar 22 01:34:42 mybuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Mar 22 01:34:42 mybuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Mar 22 01:34:42 mybuntu kernel: [    0.000000] Processor #0 15:2 APIC version 20
Mar 22 01:34:42 mybuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
Mar 22 01:34:42 mybuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Mar 22 01:34:42 mybuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Mar 22 01:34:42 mybuntu kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Mar 22 01:34:42 mybuntu kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Mar 22 01:34:42 mybuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Mar 22 01:34:42 mybuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Mar 22 01:34:42 mybuntu kernel: [    0.000000] ACPI: IRQ0 used by override.
Mar 22 01:34:42 mybuntu kernel: [    0.000000] ACPI: IRQ2 used by override.
Mar 22 01:34:42 mybuntu kernel: [    0.000000] ACPI: IRQ9 used by override.
Mar 22 01:34:42 mybuntu kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Mar 22 01:34:42 mybuntu kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Mar 22 01:34:42 mybuntu kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 27800000:d7400000)
Mar 22 01:34:42 mybuntu kernel: [    0.000000] Built 1 zonelists.  Total pages: 160513
Mar 22 01:34:42 mybuntu kernel: [    0.000000] Kernel command line: root=UUID=8e6a6726-b5fa-49c8-ab00-69ba36105d21 ro quiet splash
Mar 22 01:34:42 mybuntu kernel: [    0.000000] mapped APIC to ffffd000 (fee00000)
Mar 22 01:34:42 mybuntu kernel: [    0.000000] mapped IOAPIC to ffffc000 (fec00000)
Mar 22 01:34:42 mybuntu kernel: [    0.000000] Enabling fast FPU save and restore... done.
Mar 22 01:34:42 mybuntu kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Mar 22 01:34:42 mybuntu kernel: [    0.000000] Initializing CPU#0
Mar 22 01:34:42 mybuntu kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Mar 22 01:34:42 mybuntu kernel: [    0.000000] Detected 2800.186 MHz processor.
Mar 22 01:34:42 mybuntu kernel: [   21.486539] Console: colour VGA+ 80x25
Mar 22 01:34:42 mybuntu kernel: [   21.487566] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Mar 22 01:34:42 mybuntu kernel: [   21.488570] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Mar 22 01:34:42 mybuntu kernel: [   21.503794] Memory: 629644k/647104k available (2015k kernel code, 16800k reserved, 915k data, 364k init, 0k highmem)
Mar 22 01:34:42 mybuntu kernel: [   21.503805] virtual kernel memory layout:
Mar 22 01:34:42 mybuntu kernel: [   21.503806]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
Mar 22 01:34:42 mybuntu kernel: [   21.503808]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Mar 22 01:34:42 mybuntu kernel: [   21.503810]     vmalloc : 0xe8000000 - 0xff7fe000   ( 375 MB)
Mar 22 01:34:42 mybuntu kernel: [   21.503811]     lowmem  : 0xc0000000 - 0xe77f0000   ( 631 MB)
Mar 22 01:34:42 mybuntu kernel: [   21.503812]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
Mar 22 01:34:42 mybuntu kernel: [   21.503813]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
Mar 22 01:34:42 mybuntu kernel: [   21.503814]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
Mar 22 01:34:42 mybuntu kernel: [   21.503817] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Mar 22 01:34:42 mybuntu kernel: [   21.503860] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Mar 22 01:34:42 mybuntu kernel: [   21.583732] Calibrating delay using timer specific routine.. 5604.93 BogoMIPS (lpj=11209876)
Mar 22 01:34:42 mybuntu kernel: [   21.583760] Security Framework v1.0.0 initialized
Mar 22 01:34:42 mybuntu kernel: [   21.583767] SELinux:  Disabled at boot.
Mar 22 01:34:42 mybuntu kernel: [   21.583781] Mount-cache hash table entries: 512
Mar 22 01:34:42 mybuntu kernel: [   21.583929] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
Mar 22 01:34:42 mybuntu kernel: [   21.583942] CPU: Trace cache: 12K uops, L1 D cache: 8K
Mar 22 01:34:42 mybuntu kernel: [   21.583945] CPU: L2 cache: 512K
Mar 22 01:34:42 mybuntu kernel: [   21.583948] CPU: Hyper-Threading is disabled
Mar 22 01:34:42 mybuntu kernel: [   21.583950] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b080 00004400 00000000 00000000
Mar 22 01:34:42 mybuntu kernel: [   21.583962] Compat vDSO mapped to ffffe000.
Mar 22 01:34:42 mybuntu kernel: [   21.583976] Checking 'hlt' instruction... OK.
Mar 22 01:34:42 mybuntu kernel: [   21.599819] SMP alternatives: switching to UP code
Mar 22 01:34:42 mybuntu kernel: [   21.600055] Freeing SMP alternatives: 11k freed
Mar 22 01:34:42 mybuntu kernel: [   21.600379] Early unpacking initramfs... done
Mar 22 01:34:42 mybuntu kernel: [   21.889591] ACPI: Core revision 20070126
Mar 22 01:34:42 mybuntu kernel: [   21.889665] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Mar 22 01:34:42 mybuntu kernel: [   21.892501] CPU0: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 09
Mar 22 01:34:42 mybuntu kernel: [   21.892542] Total of 1 processors activated (5604.93 BogoMIPS).
Mar 22 01:34:42 mybuntu kernel: [   21.892686] ENABLING IO-APIC IRQs
Mar 22 01:34:42 mybuntu kernel: [   21.892885] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Mar 22 01:34:42 mybuntu kernel: [   22.038937] Brought up 1 CPUs
Mar 22 01:34:42 mybuntu kernel: [   22.039091] Booting paravirtualized kernel on bare hardware
Mar 22 01:34:42 mybuntu kernel: [   22.039171] Time:  1:34:22  Date: 02/22/108
Mar 22 01:34:42 mybuntu kernel: [   22.039205] NET: Registered protocol family 16
Mar 22 01:34:42 mybuntu kernel: [   22.039325] EISA bus registered
Mar 22 01:34:42 mybuntu kernel: [   22.039341] ACPI: bus type pci registered
Mar 22 01:34:42 mybuntu kernel: [   22.067396] PCI: PCI BIOS revision 2.10 entry at 0xfb9b0, last bus=1
Mar 22 01:34:42 mybuntu kernel: [   22.067399] PCI: Using configuration type 1
Mar 22 01:34:42 mybuntu kernel: [   22.067401] Setting up standard PCI resources
Mar 22 01:34:42 mybuntu kernel: [   22.077147] ACPI: EC: Look up EC in DSDT
Mar 22 01:34:42 mybuntu kernel: [   22.080994] ACPI: Interpreter enabled
Mar 22 01:34:42 mybuntu kernel: [   22.080999] ACPI: (supports S0 S1 S3 S4 S5)
Mar 22 01:34:42 mybuntu kernel: [   22.081018] ACPI: Using IOAPIC for interrupt routing
Mar 22 01:34:42 mybuntu kernel: [   22.085336] ACPI: PCI Root Bridge [PCI0] (0000:00)
Mar 22 01:34:42 mybuntu kernel: [   22.085352] PCI: Probing PCI hardware (bus 00)
Mar 22 01:34:42 mybuntu kernel: [   22.085801] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
Mar 22 01:34:42 mybuntu kernel: [   22.085803] * this clock source is slow. If you are sure your timer does not have
Mar 22 01:34:42 mybuntu kernel: [   22.085804] * this bug, please use "acpi_pm_good" to disable the workaround
Mar 22 01:34:42 mybuntu kernel: [   22.085852] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
Mar 22 01:34:42 mybuntu kernel: [   22.085855] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
Mar 22 01:34:42 mybuntu kernel: [   22.086201] PCI: Transparent bridge - 0000:00:1e.0
Mar 22 01:34:42 mybuntu kernel: [   22.086226] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Mar 22 01:34:42 mybuntu kernel: [   22.086376] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
Mar 22 01:34:42 mybuntu kernel: [   22.092178] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 *10 11 12 14 15)
Mar 22 01:34:42 mybuntu kernel: [   22.092276] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 7 9 10 11 12 14 15)
Mar 22 01:34:42 mybuntu kernel: [   22.092366] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *9 10 11 12 14 15)
Mar 22 01:34:42 mybuntu kernel: [   22.092457] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12 14 15)
Mar 22 01:34:42 mybuntu kernel: [   22.092548] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Mar 22 01:34:42 mybuntu kernel: [   22.092642] ACPI: PCI Interrupt Link [LNKF] (IRQs *3 4 5 7 9 10 11 12 14 15)
Mar 22 01:34:42 mybuntu kernel: [   22.092734] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Mar 22 01:34:42 mybuntu kernel: [   22.092827] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 9 10 *11 12 14 15)
Mar 22 01:34:42 mybuntu kernel: [   22.092918] Linux Plug and Play Support v0.97 (c) Adam Belay
Mar 22 01:34:42 mybuntu kernel: [   22.092931] pnp: PnP ACPI init
Mar 22 01:34:42 mybuntu kernel: [   22.092942] ACPI: bus type pnp registered
Mar 22 01:34:42 mybuntu kernel: [   22.095532] pnp: PnP ACPI: found 14 devices
Mar 22 01:34:42 mybuntu kernel: [   22.095535] ACPI: ACPI bus type pnp unregistered
Mar 22 01:34:42 mybuntu kernel: [   22.095541] PnPBIOS: Disabled by ACPI PNP
Mar 22 01:34:42 mybuntu kernel: [   22.095612] PCI: Using ACPI for IRQ routing
Mar 22 01:34:42 mybuntu kernel: [   22.095616] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Mar 22 01:34:42 mybuntu kernel: [   22.106333] NET: Registered protocol family 8
Mar 22 01:34:42 mybuntu kernel: [   22.106335] NET: Registered protocol family 20
Mar 22 01:34:42 mybuntu kernel: [   22.106431] pnp: 00:0b: ioport range 0x400-0x4bf could not be reserved
Mar 22 01:34:42 mybuntu kernel: [   22.106767] Time: tsc clocksource has been installed.
Mar 22 01:34:42 mybuntu kernel: [   22.136725] PCI: Bridge: 0000:00:1e.0
Mar 22 01:34:42 mybuntu kernel: [   22.136729]   IO window: c000-cfff
Mar 22 01:34:42 mybuntu kernel: [   22.136735]   MEM window: ec000000-edffffff
Mar 22 01:34:42 mybuntu kernel: [   22.136740]   PREFETCH window: 30000000-300fffff
Mar 22 01:34:42 mybuntu kernel: [   22.136755] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Mar 22 01:34:42 mybuntu kernel: [   22.136770] NET: Registered protocol family 2
Mar 22 01:34:42 mybuntu kernel: [   22.174706] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Mar 22 01:34:42 mybuntu kernel: [   22.174949] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
Mar 22 01:34:42 mybuntu kernel: [   22.177325] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Mar 22 01:34:42 mybuntu kernel: [   22.178213] TCP: Hash tables configured (established 131072 bind 65536)
Mar 22 01:34:42 mybuntu kernel: [   22.178220] TCP reno registered
Mar 22 01:34:42 mybuntu kernel: [   22.186854] checking if image is initramfs... it is
Mar 22 01:34:42 mybuntu kernel: [   22.637771] Switched to high resolution mode on CPU 0
Mar 22 01:34:42 mybuntu kernel: [   22.758896] Freeing initrd memory: 7068k freed
Mar 22 01:34:42 mybuntu kernel: [   22.759403] audit: initializing netlink socket (disabled)
Mar 22 01:34:42 mybuntu kernel: [   22.759426] audit(1206149662.000:1): initialized
Mar 22 01:34:42 mybuntu kernel: [   22.761620] VFS: Disk quotas dquot_6.5.1
Mar 22 01:34:42 mybuntu kernel: [   22.761687] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Mar 22 01:34:42 mybuntu kernel: [   22.761803] io scheduler noop registered
Mar 22 01:34:42 mybuntu kernel: [   22.761806] io scheduler anticipatory registered
Mar 22 01:34:42 mybuntu kernel: [   22.761808] io scheduler deadline registered
Mar 22 01:34:42 mybuntu kernel: [   22.761824] io scheduler cfq registered (default)
Mar 22 01:34:42 mybuntu kernel: [   22.761843] Boot video device is 0000:00:02.0
Mar 22 01:34:42 mybuntu kernel: [   22.762078] isapnp: Scanning for PnP cards...
Mar 22 01:34:42 mybuntu kernel: [   23.115518] isapnp: No Plug & Play device found
Mar 22 01:34:42 mybuntu kernel: [   23.147391] Real Time Clock Driver v1.12ac
Mar 22 01:34:42 mybuntu kernel: [   23.147508] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Mar 22 01:34:42 mybuntu kernel: [   23.147606] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Mar 22 01:34:42 mybuntu kernel: [   23.148596] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Mar 22 01:34:42 mybuntu kernel: [   23.149572] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Mar 22 01:34:42 mybuntu kernel: [   23.149859] input: Macintosh mouse button emulation as /class/input/input0
Mar 22 01:34:42 mybuntu kernel: [   23.149955] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Mar 22 01:34:42 mybuntu kernel: [   23.153165] serio: i8042 KBD port at 0x60,0x64 irq 1
Mar 22 01:34:42 mybuntu kernel: [   23.153175] serio: i8042 AUX port at 0x60,0x64 irq 12
Mar 22 01:34:42 mybuntu kernel: [   23.153403] mice: PS/2 mouse device common for all mice
Mar 22 01:34:42 mybuntu kernel: [   23.153539] EISA: Probing bus 0 at eisa.0
Mar 22 01:34:42 mybuntu kernel: [   23.153578] EISA: Detected 0 cards.
Mar 22 01:34:42 mybuntu kernel: [   23.153707] TCP cubic registered
Mar 22 01:34:42 mybuntu kernel: [   23.153724] NET: Registered protocol family 1
Mar 22 01:34:42 mybuntu kernel: [   23.153750] Using IPI No-Shortcut mode
Mar 22 01:34:42 mybuntu kernel: [   23.153929]   Magic number: 0:765:559
Mar 22 01:34:42 mybuntu kernel: [   23.154061]   hash matches device ptya5
Mar 22 01:34:42 mybuntu kernel: [   23.154745] Freeing unused kernel memory: 364k freed
Mar 22 01:34:42 mybuntu kernel: [   23.192746] input: AT Translated Set 2 keyboard as /class/input/input1
Mar 22 01:34:42 mybuntu kernel: [   24.364138] AppArmor: AppArmor initialized<5>audit(1206149663.500:2):  type=1505 info="AppArmor initialized" pid=1175
Mar 22 01:34:42 mybuntu kernel: [   24.371447] fuse init (API version 7.8)
Mar 22 01:34:42 mybuntu kernel: [   24.376790] Failure registering capabilities with primary security module.
Mar 22 01:34:42 mybuntu kernel: [   24.392037] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
Mar 22 01:34:42 mybuntu kernel: [   25.038859] usbcore: registered new interface driver usbfs
Mar 22 01:34:42 mybuntu kernel: [   25.038890] usbcore: registered new interface driver hub
Mar 22 01:34:42 mybuntu kernel: [   25.038914] usbcore: registered new device driver usb
Mar 22 01:34:42 mybuntu kernel: [   25.039942] USB Universal Host Controller Interface driver v3.0
Mar 22 01:34:42 mybuntu kernel: [   25.040034] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
Mar 22 01:34:42 mybuntu kernel: [   25.040049] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Mar 22 01:34:42 mybuntu kernel: [   25.040053] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Mar 22 01:34:42 mybuntu kernel: [   25.040269] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Mar 22 01:34:42 mybuntu kernel: [   25.040301] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000d800
Mar 22 01:34:42 mybuntu kernel: [   25.040444] usb usb1: configuration #1 chosen from 1 choice
Mar 22 01:34:42 mybuntu kernel: [   25.040473] hub 1-0:1.0: USB hub found
Mar 22 01:34:42 mybuntu kernel: [   25.040485] hub 1-0:1.0: 2 ports detected
Mar 22 01:34:42 mybuntu kernel: [   25.088729] SCSI subsystem initialized
Mar 22 01:34:42 mybuntu kernel: [   25.094215] libata version 2.21 loaded.
Mar 22 01:34:42 mybuntu kernel: [   25.141242] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
Mar 22 01:34:42 mybuntu kernel: [   25.141256] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Mar 22 01:34:42 mybuntu kernel: [   25.141260] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Mar 22 01:34:42 mybuntu kernel: [   25.141286] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Mar 22 01:34:42 mybuntu kernel: [   25.141317] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000d000
Mar 22 01:34:42 mybuntu kernel: [   25.141431] usb usb2: configuration #1 chosen from 1 choice
Mar 22 01:34:42 mybuntu kernel: [   25.141461] hub 2-0:1.0: USB hub found
Mar 22 01:34:42 mybuntu kernel: [   25.141470] hub 2-0:1.0: 2 ports detected
Mar 22 01:34:42 mybuntu kernel: [   25.141579] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Mar 22 01:34:42 mybuntu kernel: [   25.233019] Floppy drive(s): fd0 is 2.88M AMI BIOS
Mar 22 01:34:42 mybuntu kernel: [   25.244900] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
Mar 22 01:34:42 mybuntu kernel: [   25.244915] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Mar 22 01:34:42 mybuntu kernel: [   25.244920] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Mar 22 01:34:42 mybuntu kernel: [   25.244947] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Mar 22 01:34:42 mybuntu kernel: [   25.244977] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d400
Mar 22 01:34:42 mybuntu kernel: [   25.245089] usb usb3: configuration #1 chosen from 1 choice
Mar 22 01:34:42 mybuntu kernel: [   25.245118] hub 3-0:1.0: USB hub found
Mar 22 01:34:42 mybuntu kernel: [   25.245128] hub 3-0:1.0: 2 ports detected
Mar 22 01:34:42 mybuntu kernel: [   25.288248] FDC 0 is a post-1991 82077
Mar 22 01:34:42 mybuntu kernel: [   25.350646] ata_piix 0000:00:1f.1: version 2.11
Mar 22 01:34:42 mybuntu kernel: [   25.350678] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
Mar 22 01:34:42 mybuntu kernel: [   25.350751] PCI: Setting latency timer of device 0000:00:1f.1 to 64
Mar 22 01:34:42 mybuntu kernel: [   25.350911] scsi0 : ata_piix
Mar 22 01:34:42 mybuntu kernel: [   25.350985] scsi1 : ata_piix
Mar 22 01:34:42 mybuntu kernel: [   25.351108] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001f000 irq 14
Mar 22 01:34:42 mybuntu kernel: [   25.351111] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001f008 irq 15
Mar 22 01:34:42 mybuntu kernel: [   25.512491] ata1.00: ATA-6: WDC WD400BB-22FJA1, 14.03G14, max UDMA/100
Mar 22 01:34:42 mybuntu kernel: [   25.512496] ata1.00: 78165360 sectors, multi 16: LBA 
Mar 22 01:34:42 mybuntu kernel: [   25.520488] ata1.00: configured for UDMA/100
Mar 22 01:34:42 mybuntu kernel: [   25.839802] ata2.00: ATAPI: HL-DT-STDVD-RAM GSA-H55N, 1.02, max UDMA/66
Mar 22 01:34:42 mybuntu kernel: [   25.839811] ata2.00: limited to UDMA/33 due to 40-wire cable
Mar 22 01:34:42 mybuntu kernel: [   26.011467] ata2.00: configured for UDMA/33
Mar 22 01:34:42 mybuntu kernel: [   26.011626] scsi 0:0:0:0: Direct-Access     ATA      WDC WD400BB-22FJ 14.0 PQ: 0 ANSI: 5
Mar 22 01:34:42 mybuntu kernel: [   26.013381] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GSA-H55N 1.02 PQ: 0 ANSI: 5
Mar 22 01:34:42 mybuntu kernel: [   26.016424] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
Mar 22 01:34:42 mybuntu kernel: [   26.016444] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Mar 22 01:34:42 mybuntu kernel: [   26.016448] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Mar 22 01:34:42 mybuntu kernel: [   26.016740] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
Mar 22 01:34:42 mybuntu kernel: [   26.016788] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
Mar 22 01:34:42 mybuntu kernel: [   26.016802] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xee080000
Mar 22 01:34:42 mybuntu kernel: [   26.020680] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Mar 22 01:34:42 mybuntu kernel: [   26.021051] usb usb4: configuration #1 chosen from 1 choice
Mar 22 01:34:42 mybuntu kernel: [   26.021202] hub 4-0:1.0: USB hub found
Mar 22 01:34:42 mybuntu kernel: [   26.021211] hub 4-0:1.0: 6 ports detected
Mar 22 01:34:42 mybuntu kernel: [   26.032951] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
Mar 22 01:34:42 mybuntu kernel: [   26.033865] sd 0:0:0:0: [sda] Write Protect is off
Mar 22 01:34:42 mybuntu kernel: [   26.033869] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Mar 22 01:34:42 mybuntu kernel: [   26.033903] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar 22 01:34:42 mybuntu kernel: [   26.033986] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
Mar 22 01:34:42 mybuntu kernel: [   26.033996] sd 0:0:0:0: [sda] Write Protect is off
Mar 22 01:34:42 mybuntu kernel: [   26.033998] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Mar 22 01:34:42 mybuntu kernel: [   26.034015] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar 22 01:34:42 mybuntu kernel: [   26.034020]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 >
Mar 22 01:34:42 mybuntu kernel: [   26.093375] sd 0:0:0:0: [sda] Attached SCSI disk
Mar 22 01:34:42 mybuntu kernel: [   26.099215] sd 0:0:0:0: Attached scsi generic sg0 type 0
Mar 22 01:34:42 mybuntu kernel: [   26.099366] sr 1:0:0:0: Attached scsi generic sg1 type 5
Mar 22 01:34:42 mybuntu kernel: [   26.123318] 8139cp 0000:01:0c.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
Mar 22 01:34:42 mybuntu kernel: [   26.123325] 8139cp 0000:01:0c.0: Try the "8139too" driver instead.
Mar 22 01:34:42 mybuntu kernel: [   26.125281] 8139too Fast Ethernet driver 0.9.28
Mar 22 01:34:42 mybuntu kernel: [   26.125341] ACPI: PCI Interrupt 0000:01:0c.0[A] -> GSI 23 (level, low) -> IRQ 19
Mar 22 01:34:42 mybuntu kernel: [   26.125766] eth0: RealTek RTL8139 at 0xe804e000, 00:11:09:44:ee:13, IRQ 19
Mar 22 01:34:42 mybuntu kernel: [   26.125768] eth0:  Identified 8139 chip type 'RTL-8101'
Mar 22 01:34:42 mybuntu kernel: [   26.134403] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Mar 22 01:34:42 mybuntu kernel: [   26.134411] Uniform CD-ROM driver Revision: 3.20
Mar 22 01:34:42 mybuntu kernel: [   26.134784] sr 1:0:0:0: Attached scsi CD-ROM sr0
Mar 22 01:34:42 mybuntu kernel: [   26.483362] Attempting manual resume
Mar 22 01:34:42 mybuntu kernel: [   26.483367] swsusp: Resume From Partition 8:7
Mar 22 01:34:42 mybuntu kernel: [   26.483369] PM: Checking swsusp image.
Mar 22 01:34:42 mybuntu kernel: [   26.483645] PM: Resume from disk failed.
Mar 22 01:34:42 mybuntu kernel: [   26.517193] kjournald starting.  Commit interval 5 seconds
Mar 22 01:34:42 mybuntu kernel: [   26.517209] EXT3-fs: mounted filesystem with ordered data mode.
Mar 22 01:34:42 mybuntu kernel: [   32.330093] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Mar 22 01:34:42 mybuntu kernel: [   34.169453] Linux agpgart interface v0.102 (c) Dave Jones
Mar 22 01:34:42 mybuntu kernel: [   34.243224] agpgart: Detected an Intel 830M Chipset.
Mar 22 01:34:42 mybuntu kernel: [   34.243379] agpgart: Detected 8060K stolen memory.
Mar 22 01:34:42 mybuntu kernel: [   34.258744] agpgart: AGP aperture is 128M @ 0xe0000000
Mar 22 01:34:42 mybuntu kernel: [   34.278480] intel_rng: FWH not detected
Mar 22 01:34:42 mybuntu kernel: [   34.316896] iTCO_vendor_support: vendor-support=0
Mar 22 01:34:42 mybuntu kernel: [   34.318152] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
Mar 22 01:34:42 mybuntu kernel: [   34.318236] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x0460)
Mar 22 01:34:42 mybuntu kernel: [   34.318289] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Mar 22 01:34:42 mybuntu kernel: [   34.345888] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Mar 22 01:34:42 mybuntu kernel: [   34.373331] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Mar 22 01:34:42 mybuntu kernel: [   34.381980] i810_smbus 0000:00:02.0: i810/i815 i2c device found.
Mar 22 01:34:42 mybuntu kernel: [   34.978049] input: PC Speaker as /class/input/input2
Mar 22 01:34:42 mybuntu kernel: [   35.513588] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 20
Mar 22 01:34:42 mybuntu kernel: [   35.513614] PCI: Setting latency timer of device 0000:00:1f.5 to 64
Mar 22 01:34:42 mybuntu kernel: [   35.836037] intel8x0_measure_ac97_clock: measured 53574 usecs
Mar 22 01:34:42 mybuntu kernel: [   35.836042] intel8x0: clocking to 48000
Mar 22 01:34:42 mybuntu kernel: [   35.883871] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
Mar 22 01:34:42 mybuntu kernel: [   35.887306] parport_pc 00:08: reported by Plug and Play ACPI
Mar 22 01:34:42 mybuntu kernel: [   35.887404] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
Mar 22 01:34:42 mybuntu kernel: [   37.095795] lp0: using parport0 (interrupt-driven).
Mar 22 01:34:42 mybuntu kernel: [   37.148205] Adding 971892k swap on /dev/sda7.  Priority:-1 extents:1 across:971892k
Mar 22 01:34:42 mybuntu kernel: [   37.601580] EXT3 FS on sda6, internal journal
Mar 22 01:34:42 mybuntu kernel: [   40.541587] PPP generic driver version 2.4.2
Mar 22 01:34:42 mybuntu kernel: [   40.599085] NET: Registered protocol family 17
Mar 22 01:34:42 mybuntu kernel: [   40.931911] NET: Registered protocol family 24
Mar 22 01:34:42 mybuntu kernel: [   41.179900] input: Power Button (FF) as /class/input/input4
Mar 22 01:34:42 mybuntu kernel: [   41.185149] ACPI: Power Button (FF) [PWRF]
Mar 22 01:34:42 mybuntu kernel: [   41.220586] input: Power Button (CM) as /class/input/input5
Mar 22 01:34:42 mybuntu kernel: [   41.225827] ACPI: Power Button (CM) [PWRB]
Mar 22 01:34:42 mybuntu kernel: [   41.323307] No dock devices found.
Mar 22 01:34:42 mybuntu pppd[3940]: replacing old default route to eth0 [192.168.1.1]
Mar 22 01:34:42 mybuntu pppd[3940]: Cannot determine ethernet address for proxy ARP
Mar 22 01:34:42 mybuntu pppd[3940]: local  IP address 117.195.192.171
Mar 22 01:34:42 mybuntu pppd[3940]: remote IP address 117.195.192.1
Mar 22 01:34:42 mybuntu pppd[3940]: primary   DNS address 218.248.240.46
Mar 22 01:34:42 mybuntu pppd[3940]: secondary DNS address 218.248.255.146
Mar 22 01:34:42 mybuntu NetworkManager: <info>  starting... 
Mar 22 01:34:42 mybuntu NetworkManager: <info>  Found dial up configuration for dsl-provider via Modem: dsl-provider 
Mar 22 01:34:42 mybuntu kernel: [   42.365574] ip_tables: (C) 2000-2006 Netfilter Core Team
Mar 22 01:34:42 mybuntu NetworkManager: <debug> [1206129882.806928] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2560'). 
Mar 22 01:34:42 mybuntu kernel: [   42.786283] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Mar 22 01:34:42 mybuntu kernel: [   42.786289] apm: overridden by ACPI.
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.082674] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2562'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.085938] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c2'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.088875] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.092346] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_if0'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.093106] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c4'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.093817] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.094516] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_if0'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.095206] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c7'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.095928] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.096708] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_if0'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.097512] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24cd'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.098201] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.098881] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_if0'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.099557] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_244e'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.100272] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_11c1_48c'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.100961] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_10ec_8139'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.101635] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c0'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.102315] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24cb'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.103048] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24cb_scsi_host'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.103762] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24cb_scsi_host_scsi_device_lun0'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.104458] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24cb_scsi_host_0'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.105129] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24cb_scsi_host_0_scsi_device_lun0'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.105790] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c3'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.106453] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.107115] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_eisa_0'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.107795] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_floppy_0'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.108514] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.109157] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.109877] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.110551] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_iTCO_wdt'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.111204] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.111878] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_serial8250'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.112600] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0a03'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.113261] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c02'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.113918] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0200'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.114567] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0b00'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.115215] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0800'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.115882] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c04'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.116539] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0700'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.117187] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0501'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.117833] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0401'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.118534] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0f13'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.119193] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0303'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.119865] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c02_0'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.120520] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_INT0800'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.121162] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.121800] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.122440] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.123079] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.123741] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_11_09_44_ee_13'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.133517] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24cb_scsi_host_scsi_device_lun0_scsi_generic'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.135655] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24cb_scsi_host_0_scsi_device_lun0_scsi_generic'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.137195] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_oss_pcm_1'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.137907] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_oss_pcm_0'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.138545] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_control__1'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.139173] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_oss_pcm_0_0'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.139990] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_oss_mixer__1'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.140659] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_capture_0'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.141292] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_playback_0'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.141910] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_capture_1'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.142505] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_capture_2'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.143124] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_capture_3'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.143766] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_24c5_alsa_playback_4'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.144400] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_sequencer'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.145071] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.145693] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.146302] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_timer'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.146911] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.147518] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.148207] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.148843] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.149511] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.176258] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_usbraw'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.185190] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_usbraw'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.185905] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_usbraw'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.186534] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_usbraw'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.258745] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_floppy_0_storage'). 
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.288653] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_WDC_WD400BB_22FJA1_WD_WMAJA2962300'). 
Mar 22 01:34:43 mybuntu kernel: [   43.592099] Failure registering capabilities with primary security module.
Mar 22 01:34:43 mybuntu avahi-daemon[4811]: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
Mar 22 01:34:43 mybuntu avahi-daemon[4811]: Successfully dropped root privileges.
Mar 22 01:34:43 mybuntu avahi-daemon[4811]: avahi-daemon 0.6.20 starting up.
Mar 22 01:34:43 mybuntu avahi-daemon[4811]: Successfully called chroot().
Mar 22 01:34:43 mybuntu avahi-daemon[4811]: Successfully dropped remaining capabilities.
Mar 22 01:34:43 mybuntu avahi-daemon[4811]: No service file found in /etc/avahi/services.
Mar 22 01:34:43 mybuntu avahi-daemon[4811]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.2.
Mar 22 01:34:43 mybuntu avahi-daemon[4811]: New relevant interface eth0.IPv4 for mDNS.
Mar 22 01:34:43 mybuntu avahi-daemon[4811]: Network interface enumeration completed.
Mar 22 01:34:43 mybuntu avahi-daemon[4811]: Registering new address record for 192.168.1.2 on eth0.IPv4.
Mar 22 01:34:43 mybuntu avahi-daemon[4811]: Registering HINFO record with values 'I686'/'LINUX'.
Mar 22 01:34:43 mybuntu dhcdbd: Started up.
Mar 22 01:34:43 mybuntu NetworkManager: <debug> [1206129883.930269] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_2EAC16D9AC169B81'). 
Mar 22 01:34:44 mybuntu NetworkManager: <debug> [1206129884.093833] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part2_size_1024'). 
Mar 22 01:34:44 mybuntu NetworkManager: <debug> [1206129884.298356] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_5A2E_8757'). 
Mar 22 01:34:44 mybuntu NetworkManager: <debug> [1206129884.305675] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_8e6a6726_b5fa_49c8_ab00_69ba36105d21'). 
Mar 22 01:34:44 mybuntu NetworkManager: <debug> [1206129884.312550] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_94ba6802_c127_4e49_b8df_3f9bd6099d4a'). 
Mar 22 01:34:44 mybuntu NetworkManager: <debug> [1206129884.594042] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_02C3_0762'). 
Mar 22 01:34:44 mybuntu avahi-daemon[4811]: Server startup complete. Host name is mybuntu.local. Local service cookie is 242478200.
Mar 22 01:34:44 mybuntu NetworkManager: <debug> [1206129884.694605] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU0'). 
Mar 22 01:34:44 mybuntu NetworkManager: <debug> [1206129884.700344] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVD_RAM_GSA_H55N'). 
Mar 22 01:34:46 mybuntu ntpd[4897]: ntpd 4.2.4p0@1.1472-o Thu Oct  4 20:58:45 UTC 2007 (1)
Mar 22 01:34:46 mybuntu ntpd[4898]: precision = 1.000 usec
Mar 22 01:34:46 mybuntu ntpd[4898]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Mar 22 01:34:46 mybuntu ntpd[4898]: Listening on interface #1 lo, 127.0.0.1#123 Enabled
Mar 22 01:34:46 mybuntu ntpd[4898]: Listening on interface #2 eth0, 192.168.1.2#123 Enabled
Mar 22 01:34:46 mybuntu ntpd[4898]: Listening on interface #3 ppp0, 117.195.192.171#123 Enabled
Mar 22 01:34:46 mybuntu ntpd[4898]: kernel time sync status 0040
Mar 22 01:34:46 mybuntu ntpd[4898]: frequency initialized 5.058 PPM from /var/lib/ntp/ntp.drift
Mar 22 01:34:46 mybuntu ntpd[4898]: getaddrinfo: "::1" invalid host address, ignored
Mar 22 01:34:46 mybuntu anacron[4919]: Anacron 2.3 started on 2008-03-22
Mar 22 01:34:46 mybuntu anacron[4919]: Normal exit (0 jobs run)
Mar 22 01:34:46 mybuntu kernel: [   46.927643] [drm] Initialized drm 1.1.0 20060810
Mar 22 01:34:46 mybuntu /usr/sbin/cron[4963]: (CRON) INFO (pidfile fd = 3)
Mar 22 01:34:46 mybuntu /usr/sbin/cron[4966]: (CRON) STARTUP (fork ok)
Mar 22 01:34:47 mybuntu /usr/sbin/cron[4966]: (CRON) INFO (Running @reboot jobs)
Mar 22 01:34:47 mybuntu kernel: [   46.964658] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
Mar 22 01:34:47 mybuntu kernel: [   46.965244] [drm] Initialized i915 1.6.0 20060119 on minor 0
Mar 22 01:34:50 mybuntu gdmgreeter[5055]: GdkPixbuf-CRITICAL: gdk_pixbuf_get_width: assertion `pixbuf != NULL' failed 
Mar 22 01:34:50 mybuntu gdmgreeter[5055]: GdkPixbuf-CRITICAL: gdk_pixbuf_get_height: assertion `pixbuf != NULL' failed 
Mar 22 01:34:50 mybuntu gdmgreeter[5055]: GLib-GObject-CRITICAL: g_object_unref: assertion `G_IS_OBJECT (object)' failed

---

### Post by Tomatz on 2008-03-22
[I]Mar 22 01:34:50 mybuntu gdmgreeter[5055]: GdkPixbuf-CRITICAL: gdk_pixbuf_get_width: assertion `pixbuf != NULL' failed
Mar 22 01:34:50 mybuntu gdmgreeter[5055]: GdkPixbuf-CRITICAL: gdk_pixbuf_get_height: assertion `pixbuf != NULL' failed
Mar 22 01:34:50 mybuntu gdmgreeter[5055]: GLib-GObject-CRITICAL: g_object_unref: assertion `G_IS_OBJECT (object)' failed[/I]

[U]It looks like gdmgreeter is the problem. Try this:
[/U]
Go to system, administration, login window 

Then the local tab

then change your greeter/gdm theme

[U]Then
[/U]
sudo apt-get install gtweakui

Go to system, preferences, gtweakui-session

Download a simple/small splash from gnome-look like the one below:

[http://www.gnome-look.org/content/show.php/mac-splash.?content=76827](http://www.gnome-look.org/content/show.php/mac-splash.?content=76827)

Add it using the gtweakui-session app


That might all seem a bit much but its best to cover all bases. If that does not work you will have to completely reverse (remove) the mac4lin installation.

Hope that helps :)

---

### Post by mrdosa on 2008-03-22
I changed the gdm theme and its working. :)


But sometimes everything goes weird again. may be I will have to reverse the theme thing! Thanks a lot ppl!!:)

---

### Post by n6yga on 2008-03-22
Sorry about the late return to this thread. I was solving issues that I have...

Anyway, I'm not really a GURU (although I play one on TV...) but, it looks to me to be a video card issue. If the GDM is throwing pixbuf assertions, it may be having issues writing to the video card. What driver are you using? Standard VESA, or some restricted drivers? I didn't get a chance to look through your log to find the video info.

Hey, just my .02. Do you have access to another video card to try?

Mark.

---

### Post by artir on 2008-03-22
sudo dpkg-reconfigure xserver-xorg
:)

---

### Post by mrdosa on 2008-03-22
> **n6yga said:**
> Sorry about the late return to this thread. I was solving issues that I have...

Anyway, I'm not really a GURU (although I play one on TV...) but, it looks to me to be a video card issue. If the GDM is throwing pixbuf assertions, it may be having issues writing to the video card. What driver are you using? Standard VESA, or some restricted drivers? I didn't get a chance to look through your log to find the video info.

Hey, just my .02. Do you have access to another video card to try?

Mark.

Well I dont have any idea about what drivers I am using!! And I dont have access to any other graphic card!! I have been using ubuntu for over a month now and it worked absolutely fine. Even after installing the mac look it still worked fine. Dont know what went wrong!

---

### Post by mrdosa on 2008-03-22
> **artir said:**
> sudo dpkg-reconfigure xserver-xorg
:)

What does that do?

---

### Post by Tomatz on 2008-03-22
Reconfigures xorg (the graphics server) doubt it would correct your problem though.

---

### Post by n6yga on 2008-03-23
Just out of curiosity, can you boot into Windows? That should be a ruler as to whether or not the video card is working.

Mark.

---

### Post by Tomatz on 2008-03-23
> **n6yga said:**
> Just out of curiosity, can you boot into Windows? That should be a ruler as to whether or not the video card is working.

Mark.

It is working :)

It was the mac4lin gdm theme that was crashing.

Look at the log he posted.

---

### Post by mrdosa on 2008-03-23
I was able to log into windows. But not into Ubuntu. but after changing the GDM theme everything is working fine. I actually had made a copy of the grub menu list so could revert back many changes. Thanks everyone.

---

### Post by smartboyathome on 2008-03-23
The problem you have is because of a button for some reason having (it seems) layers outside of the image. Quite strange, really, for a PNG image which doesn't use layers. I think this is a bug with the theme (I don't use it myself).

---

### Post by mrdosa on 2008-03-23
Mar 24 06:57:14 mybuntu kernel: [   67.168099] [drm] Initialized drm 1.1.0 20060810
Mar 24 06:57:14 mybuntu kernel: [   67.172809] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
Mar 24 06:57:14 mybuntu kernel: [   67.175723] [drm] Initialized i915 1.6.0 20060119 on minor 0
Mar 24 06:57:18 mybuntu gdmgreeter[5047]: GdkPixbuf-CRITICAL: gdk_pixbuf_get_width: assertion `pixbuf != NULL' failed 
Mar 24 06:57:18 mybuntu gdmgreeter[5047]: GdkPixbuf-CRITICAL: gdk_pixbuf_get_height: assertion `pixbuf != NULL' failed 
Mar 24 06:57:18 mybuntu gdmgreeter[5047]: GLib-GObject-CRITICAL: g_object_unref: assertion `G_IS_OBJECT (object)' failed 


I checked my syslog file and I am still getting the same error, but ubuntu is logging on normally!! Can anyone explain!!

---

### Post by Tomatz on 2008-03-24
If you want a nice original theme below is mine:


[[IMG]http://img296.imageshack.us/img296/6114/screenshotresizedzq9.th.png[/IMG]](http://img296.imageshack.us/my.php?image=screenshotresizedzq9.png)


[B]Slickness theme, wallpaper, emerald boarders:
[/B]
[http://www.gnome-look.org/content/show.php/SlicknesS?content=71993](http://www.gnome-look.org/content/show.php/SlicknesS?content=71993)
(be sure to follow instructions on that page otherwise you will bork firefox)

[B]nuoveXT 2 icons:
[/B]
[url]http://www.gnome-look.org/content/show.php
/nuoveXT+2?content=56625[/url]

[B]Font:
[/B]
Malayalam

[B]Custom menu button attached below:
[/B]
:)

*Clock in screenlets package, dock is of course awn*

---

