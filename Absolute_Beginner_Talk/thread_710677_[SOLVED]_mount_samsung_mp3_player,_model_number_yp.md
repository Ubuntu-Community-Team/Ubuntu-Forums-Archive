---
title: "[SOLVED] mount samsung mp3 player, model number yp-k3jqb"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by k33bz on 2008-02-28
I saw some similiar post, and was wondering if anyone else with this model has found a workaround. 

Device doesnt mount in Linux, nor is it even recognized.

---

### Post by xeth_delta on 2008-02-28
I have a Samsung Z5 player. I can mount it as an external HDD. It is possible you have to select USB storage device mode in the player itself. Have you tried this?

That said, connect the player and then run:
```
lsusb
```
Please post the output.

---

### Post by k33bz on 2008-02-28
> **xeth_delta said:**
> I have a Samsung Z5 player. I can mount it as an external HDD. It is possible you have to select USB storage device mode in the player itself. Have you tried this?

That said, connect the player and then run:
```
lsusb
```
Please post the output.

i dont see an area on the mp3 player to select it as a usb storage device, 

as for the code, I have checked, it dont show,how ever I will repost what the info is given when i get back to my house later tonight, dont have my USB cable for the mp3 player with me.

---

### Post by xeth_delta on 2008-02-28
> **k33bz said:**
> i dont see an area on the mp3 player to select it as a usb storage device, 

as for the code, I have checked, it dont show,how ever I will repost what the info is given when i get back to my house later tonight, dont have my USB cable for the mp3 player with me.

Also run "dmesg" after connecting. There should be a message in the output.

---

### Post by k33bz on 2008-02-28
ok, I will do that, and i will repost everything i have.


BTW, dont know if this matters or not, 

but reading other post, I found an update on the firmware for my player, just hope it dont take away my radio, it is part of the reason i got this model,

Also read something about Linux headers as well.  What is the probability of me fixing my problem with one of these 2 solutions.

---

### Post by xeth_delta on 2008-02-28
> **k33bz said:**
> ok, I will do that, and i will repost everything i have.


BTW, dont know if this matters or not, 

but reading other post, I found an update on the firmware for my player, just hope it dont take away my radio, it is part of the reason i got this model,

Also read something about Linux headers as well.  What is the probability of me fixing my problem with one of these 2 solutions.

As long as the firmware is the right one for your player that should not be a problem. If possible make a backup of the current firmware. If I recall right I was able to copy it from the player itself once it was connected, it's a year already since I did that.

The headers you are talking about are needed to compile certain source code. Maybe they were talking about compiling some drivers/modules?

---

### Post by k33bz on 2008-02-28
> **xeth_delta said:**
> As long as the firmware is the right one for your player that should not be a problem. If possible make a backup of the current firmware. If I recall right I was able to copy it from the player itself once it was connected, it's a year already since I did that.

The headers you are talking about are needed to compile certain source code. Maybe they were talking about compiling some drivers/modules?

No it wasnt for writing source, if i remember correctly it was more to do with linux header configurations of some sort. Cant say for sure, it was one the 4 forums that appeared as being closely matched with the title of mine.

---

### Post by xeth_delta on 2008-02-28
> **k33bz said:**
> No it wasnt for writing source, if i remember correctly it was more to do with linux header configurations of some sort. Cant say for sure, it was one the 4 forums that appeared as being closely matched with the title of mine.

If you post a link I might be able to tell you what they referred to.

---

### Post by k33bz on 2008-02-28
it would be this one here:
[http://ubuntuforums.org/showthread.php?t=321423&page=2]("http://ubuntuforums.org/showthread.php?t=321423&page=2")

---

### Post by xeth_delta on 2008-02-28
> **k33bz said:**
> it would be this one here:
[http://ubuntuforums.org/showthread.php?t=321423&page=2]("http://ubuntuforums.org/showthread.php?t=321423&page=2")

Are you sure? I didn't find any mention of headers. By the way, TheKiteGuy has the same player model I have.

---

### Post by k33bz on 2008-02-28
i beleive it was that one, ya i know Kite guy doesnt have the same model as me, didnt see any posting with the same model as me.

---

### Post by xeth_delta on 2008-02-28
> **k33bz said:**
> i beleive it was that one, ya i know Kite guy doesnt have the same model as me, didnt see any posting with the same model as me.

What post number is the one you mentioned?

---

### Post by k33bz on 2008-02-28
let me go look right quick, not even sure what page it was on, just recognised them talking about it breifly on the 3rd page, So I figured it was on the 2nd page that it went into detail about it, but i was readin 3 other threads at same time.

---

### Post by alzie on 2008-02-28
I found this at [www.anythingbutipod.com](www.anythingbutipod.com)

They seem to be using a korean firmware update 1.05 (done on a windows box) to make the player UMS compatible.

[http://www.anythingbutipod.com/forum/showthread.php?t=8618&highlight=linux](http://www.anythingbutipod.com/forum/showthread.php?t=8618&highlight=linux) is the thread I was looking at.

Good Luck

---

### Post by k33bz on 2008-02-29
ok, so now it is showing when I list the usb devices, still dont know how to mount it though

```
keebler@K33bz-mobile:~$ lsusb
Bus 005 Device 003: ID 04e8:5081 Samsung Electronics Co., Ltd 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c01e Logitech, Inc. MX518 Optical Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```

---

### Post by k33bz on 2008-02-29
```
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v002 PTLTD                                 ) @ 0x000f6650
[    0.000000] ACPI: XSDT (v001 ACRSYS ACRPRDCT 0x06040000  LTP 0x00000000) @ 0x1f69257e
[    0.000000] ACPI: FADT (v003 INTEL  CALISTGA 0x06040000 ALAN 0x00000001) @ 0x1f69bc38
[    0.000000] ACPI: MADT (v001 INTEL  CALISTGA 0x06040000 LOHR 0x0000005a) @ 0x1f69bd2c
[    0.000000] ACPI: HPET (v001 INTEL  CALISTGA 0x06040000 LOHR 0x0000005a) @ 0x1f69bd94
[    0.000000] ACPI: MCFG (v001 INTEL  CALISTGA 0x06040000 LOHR 0x0000005a) @ 0x1f69bdcc
[    0.000000] ACPI: MADT (v001 PTLTD    APIC   0x06040000  LTP 0x00000000) @ 0x1f69be08
[    0.000000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x1f69be62
[    0.000000] ACPI: SLIC (v001 ACRSYS ACRPRDCT 0x06040000 acer 0x00000000) @ 0x1f69be8a
[    0.000000] ACPI: SSDT (v001  PmRef  Cpu0Cst 0x00003001 INTL 0x20050624) @ 0x1f692ad0
[    0.000000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20050624) @ 0x1f6925ea
[    0.000000] ACPI: DSDT (v002 INTEL  CALISTGA 0x06040000 MSFT 0x03000000) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: 2 duplicate APIC table ignored.
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:c0000000)
[    0.000000] Detected 1600.182 MHz processor.
[   33.544062] Built 1 zonelists.  Total pages: 127651
[   33.544067] Kernel command line: root=UUID=6ad9127b-ab77-4b84-ba4b-9a38ec340bfd ro quiet splash
[   33.544220] mapped APIC to ffffd000 (fee00000)
[   33.544222] mapped IOAPIC to ffffc000 (fec00000)
[   33.544225] Enabling fast FPU save and restore... done.
[   33.544228] Enabling unmasked SIMD FPU exception support... done.
[   33.544236] Initializing CPU#0
[   33.544306] PID hash table entries: 2048 (order: 11, 8192 bytes)
[   33.546001] Console: colour VGA+ 80x25
[   33.546171] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   33.546336] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   33.556628] Memory: 498100k/514624k available (1993k kernel code, 16004k reserved, 900k data, 328k init, 0k highmem)
[   33.556637] virtual kernel memory layout:
[   33.556638]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   33.556639]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   33.556640]     vmalloc : 0xe0000000 - 0xff7fe000   ( 503 MB)
[   33.556641]     lowmem  : 0xc0000000 - 0xdf690000   ( 502 MB)
[   33.556643]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   33.556644]       .data : 0xc02f24c9 - 0xc03d36d4   ( 900 kB)
[   33.556645]       .text : 0xc0100000 - 0xc02f24c9   (1993 kB)
[   33.556648] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   33.556803] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   33.556810] hpet0: 3 64-bit timers, 14318180 Hz
[   33.557815] Using HPET for base-timer
[   33.636686] Calibrating delay using timer specific routine.. 3203.83 BogoMIPS (lpj=6407672)
[   33.636727] Security Framework v1.0.0 initialized
[   33.636731] SELinux:  Disabled at boot.
[   33.636746] Mount-cache hash table entries: 512
[   33.636873] CPU: After generic identify, caps: afebfbff 20100000 00000000 00000000 0000e31d 00000000 00000001
[   33.636881] monitor/mwait feature present.
[   33.636883] using mwait in idle threads.
[   33.636886] CPU: L1 I cache: 32K, L1 D cache: 32K
[   33.636889] CPU: L2 cache: 1024K
[   33.636892] CPU: After all inits, caps: afebfbff 20100000 00000000 00003940 0000e31d 00000000 00000001
[   33.636900] Compat vDSO mapped to ffffe000.
[   33.636904] Remapping vsyscall page to ffffe000
[   33.636915] Checking 'hlt' instruction... OK.
[   33.652758] SMP alternatives: switching to UP code
[   33.652936] Freeing SMP alternatives: 11k freed
[   33.653112] Early unpacking initramfs... done
[   33.999351] ACPI: Core revision 20060707
[   34.024659] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   34.029047] CPU0: Intel(R) Celeron(R) M CPU        520  @ 1.60GHz stepping 06
[   34.029072] Total of 1 processors activated (3203.83 BogoMIPS).
[   34.029268] ENABLING IO-APIC IRQs
[   34.029463] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   34.175890] Brought up 1 CPUs
[   34.176119] Booting paravirtualized kernel on bare hardware
[   34.176200] Time: 12:27:39  Date: 01/29/108
[   34.176224] NET: Registered protocol family 16
[   34.176304] EISA bus registered
[   34.176308] ACPI: bus type pci registered
[   34.188418] PCI: PCI BIOS revision 2.10 entry at 0xfd6c2, last bus=12
[   34.188420] PCI: Using configuration type 1
[   34.188421] Setting up standard PCI resources
[   34.195358] ACPI: Interpreter enabled
[   34.195361] ACPI: Using IOAPIC for interrupt routing
[   34.195670] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   34.195676] PCI: Probing PCI hardware (bus 00)
[   34.196312] Boot video device is 0000:00:02.0
[   34.197000] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   34.197005] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   34.197871] PCI: Transparent bridge - 0000:00:1e.0
[   34.197942] PCI: Bus #0b (-#0e) is hidden behind transparent bridge #0a (-#0b) (try 'pci=assign-busses')
[   34.197945] Please report the result to linux-kernel to fix this permanently
[   34.198015] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   34.203466] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   34.203720] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   34.203960] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[   34.204645] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   34.205156] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   34.205405] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   34.205656] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[   34.205903] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   34.206154] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[   34.206401] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   34.206650] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[   34.206896] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   34.229129] Linux Plug and Play Support v0.97 (c) Adam Belay
[   34.229139] pnp: PnP ACPI init
[   34.232217] pnp: PnP ACPI: found 9 devices
[   34.232222] PnPBIOS: Disabled by ACPI PNP
[   34.232268] PCI: Using ACPI for IRQ routing
[   34.232271] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   34.232276] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[   34.232278] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[   34.232280] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.0
[   34.232283] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.1
[   34.232285] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1
[   34.232287] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.1
[   34.232289] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.2
[   34.232291] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.2
[   34.232293] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.2
[   34.263100] NET: Registered protocol family 8
[   34.263102] NET: Registered protocol family 20
[   34.263610] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[   34.263631] PCI: Bridge: 0000:00:1c.0
[   34.263635]   IO window: 2000-2fff
[   34.263641]   MEM window: 34000000-340fffff
[   34.263646]   PREFETCH window: disabled.
[   34.263661] PCI: Bridge: 0000:00:1c.1
[   34.263662]   IO window: disabled.
[   34.263669]   MEM window: 34100000-341fffff
[   34.263673]   PREFETCH window: disabled.
[   34.263679] PCI: Bridge: 0000:00:1c.2
[   34.263680]   IO window: disabled.
[   34.263686]   MEM window: disabled.
[   34.263690]   PREFETCH window: disabled.
[   34.263699] PCI: Bus 11, cardbus bridge: 0000:0a:09.0
[   34.263701]   IO window: 00003000-000030ff
[   34.263706]   IO window: 00003400-000034ff
[   34.263712]   PREFETCH window: 30000000-33ffffff
[   34.263718]   MEM window: 38000000-3bffffff
[   34.263730] PCI: Bridge: 0000:00:1e.0
[   34.263733]   IO window: 3000-3fff
[   34.263739]   MEM window: d0200000-d02fffff
[   34.263744]   PREFETCH window: 30000000-33ffffff
[   34.263773] PCI: Enabling device 0000:00:1c.0 (0000 -> 0003)
[   34.263781] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   34.263789] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   34.263813] PCI: Enabling device 0000:00:1c.1 (0000 -> 0002)
[   34.263818] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[   34.263825] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   34.263850] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   34.263858] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   34.263869] PCI: Enabling device 0000:00:1e.0 (0004 -> 0007)
[   34.263876] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   34.263893] PCI: Enabling device 0000:0a:09.0 (0000 -> 0003)
[   34.263898] ACPI: PCI Interrupt 0000:0a:09.0[A] -> GSI 20 (level, low) -> IRQ 19
[   34.263925] NET: Registered protocol family 2
[   34.299721] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   34.299790] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   34.299864] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   34.299902] TCP: Hash tables configured (established 16384 bind 8192)
[   34.299904] TCP reno registered
[   34.311756] checking if image is initramfs... it is
[   34.991882] Freeing initrd memory: 7868k freed
[   34.992101] Simple Boot Flag at 0x36 set to 0x1
[   34.992402] audit: initializing netlink socket (disabled)
[   34.992417] audit(1204288059.516:1): initialized
[   34.992521] VFS: Disk quotas dquot_6.5.1
[   34.992537] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   34.992583] io scheduler noop registered
[   34.992586] io scheduler anticipatory registered
[   34.992587] io scheduler deadline registered
[   34.992594] io scheduler cfq registered (default)
[   34.992832] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   34.992893] assign_interrupt_mode Found MSI capability
[   34.992896] Allocate Port Service[0000:00:1c.0:pcie00]
[   34.992926] Allocate Port Service[0000:00:1c.0:pcie02]
[   34.993050] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   34.993110] assign_interrupt_mode Found MSI capability
[   34.993113] Allocate Port Service[0000:00:1c.1:pcie00]
[   34.993142] Allocate Port Service[0000:00:1c.1:pcie02]
[   34.993267] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   34.993327] assign_interrupt_mode Found MSI capability
[   34.993329] Allocate Port Service[0000:00:1c.2:pcie00]
[   34.993359] Allocate Port Service[0000:00:1c.2:pcie02]
[   34.993533] isapnp: Scanning for PnP cards...
[   35.347372] isapnp: No Plug & Play device found
[   35.368565] Real Time Clock Driver v1.12ac
[   35.368621] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   35.369252] mice: PS/2 mouse device common for all mice
[   35.369757] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   35.369978] input: Macintosh mouse button emulation as /class/input/input0
[   35.370009] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   35.370054] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   35.370290] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   35.383697] i8042.c: Detected active multiplexing controller, rev 1.1.
[   35.391182] serio: i8042 KBD port at 0x60,0x64 irq 1
[   35.391187] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   35.391189] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   35.391192] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   35.391194] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   35.391583] EISA: Probing bus 0 at eisa.0
[   35.391590] Cannot allocate resource for EISA slot 1
[   35.391593] Cannot allocate resource for EISA slot 2
[   35.391595] Cannot allocate resource for EISA slot 3
[   35.391617] EISA: Detected 0 cards.
[   35.421667] TCP cubic registered
[   35.421672] NET: Registered protocol family 1
[   35.421691] Using IPI No-Shortcut mode
[   35.421749] ACPI: (supports S0 S3 S4 S5)
[   35.421795]   Magic number: 12:352:482
[   35.421961] Time: tsc clocksource has been installed.
[   35.422060] Freeing unused kernel memory: 328k freed
[   35.441008] input: AT Translated Set 2 keyboard as /class/input/input1
[   36.653747] Capability LSM initialized
[   36.685270] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   36.685277] ACPI: Processor [CPU0] (supports 8 throttling states)
[   36.685288] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   36.688918] ACPI: Thermal Zone [THRM] (36 C)
[   37.087261] usbcore: registered new interface driver usbfs
[   37.087281] usbcore: registered new interface driver hub
[   37.087302] usbcore: registered new device driver usb
[   37.088112] USB Universal Host Controller Interface driver v3.0
[   37.088161] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
[   37.088172] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   37.088177] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   37.088295] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   37.088329] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00001820
[   37.088422] usb usb1: configuration #1 chosen from 1 choice
[   37.088444] hub 1-0:1.0: USB hub found
[   37.088449] hub 1-0:1.0: 2 ports detected
[   37.156149] SCSI subsystem initialized
[   37.179889] libata version 2.20 loaded.
[   37.191430] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 21
[   37.191441] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   37.191446] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   37.191468] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   37.191502] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00001840
[   37.191583] usb usb2: configuration #1 chosen from 1 choice
[   37.191607] hub 2-0:1.0: USB hub found
[   37.191612] hub 2-0:1.0: 2 ports detected
[   37.295273] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   37.295286] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   37.295290] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   37.295315] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   37.295349] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[   37.295432] usb usb3: configuration #1 chosen from 1 choice
[   37.295454] hub 3-0:1.0: USB hub found
[   37.295460] hub 3-0:1.0: 2 ports detected
[    3.684000] Time: hpet clocksource has been installed.
[    3.744000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[    3.744000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    3.744000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.744000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.744000] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
[    3.744000] usb usb4: configuration #1 chosen from 1 choice
[    3.744000] hub 4-0:1.0: USB hub found
[    3.744000] hub 4-0:1.0: 2 ports detected
[    3.848000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
[    3.848000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    3.848000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.848000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    3.848000] ehci_hcd 0000:00:1d.7: debug port 1
[    3.848000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    3.848000] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xd0644000
[    3.852000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.852000] usb usb5: configuration #1 chosen from 1 choice
[    3.852000] hub 5-0:1.0: USB hub found
[    3.852000] hub 5-0:1.0: 8 ports detected
[    3.956000] ata_piix 0000:00:1f.2: version 2.10ac1
[    3.956000] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    4.112000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 21
[    4.112000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    4.112000] ata1: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x000118b0 irq 14
[    4.112000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x000118b8 irq 15
[    4.112000] scsi0 : ata_piix
[    4.276000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    4.276000] ata1.00: ATA-7: ST980811AS, 3.ALD, max UDMA/133
[    4.276000] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    4.284000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    4.284000] ata1.00: configured for UDMA/133
[    4.284000] scsi1 : ata_piix
[    4.604000] ata2.00: ATAPI, max UDMA/33
[    4.768000] ata2.00: configured for UDMA/33
[    4.768000] scsi 0:0:0:0: Direct-Access     ATA      ST980811AS       3.AL PQ: 0 ANSI: 5
[    4.768000] scsi 1:0:0:0: CD-ROM            Optiarc  CD-RW CRX880A    KX07 PQ: 0 ANSI: 5
[    4.788000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    4.788000] sda: Write Protect is off
[    4.788000] sda: Mode Sense: 00 3a 00 00
[    4.788000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.788000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    4.788000] sda: Write Protect is off
[    4.788000] sda: Mode Sense: 00 3a 00 00
[    4.788000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.788000]  sda: sda1 sda2 < sda5 >
[    4.872000] sd 0:0:0:0: Attached scsi disk sda
[    4.876000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.876000] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    4.884000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    4.884000] Uniform CD-ROM driver Revision: 3.20
[    4.884000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.084000] Attempting manual resume
[    5.084000] swsusp: Resume From Partition 8:5
[    5.084000] PM: Checking swsusp image.
[    5.084000] PM: Resume from disk failed.
[    5.148000] kjournald starting.  Commit interval 5 seconds
[    5.148000] EXT3-fs: mounted filesystem with ordered data mode.
[   16.868000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   16.868000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   17.084000] Linux agpgart interface v0.102 (c) Dave Jones
[   17.096000] agpgart: Detected an Intel 945GM Chipset.
[   17.096000] agpgart: Detected 7932K stolen memory.
[   17.112000] agpgart: AGP aperture is 256M @ 0xc0000000
[   17.940000] ACPI: PCI Interrupt 0000:0a:09.2[A] -> GSI 20 (level, low) -> IRQ 19
[   17.976000] Yenta: CardBus bridge found at 0000:0a:09.0 [1025:0110]
[   17.976000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   17.976000] Yenta: Routing CardBus interrupts to PCI
[   17.976000] Yenta TI: socket 0000:0a:09.0, mfunc 0x01321b22, devctl 0x66
[   17.984000] intel_rng: FWH not detected
[   18.064000] iTCO_vendor_support: vendor-support=0
[   18.064000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   18.208000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 19
[   18.208000] Socket status: 30000006
[   18.208000] Yenta: Raising subordinate bus# of parent bus (#0a) from #0b to #0e
[   18.208000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   18.208000] cs: IO port probe 0x3000-0x3fff: clean.
[   18.208000] pcmcia: parent PCI bridge Memory window: 0xd0200000 - 0xd02fffff
[   18.208000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[   18.208000] PCI: Enabling device 0000:02:00.0 (0000 -> 0003)
[   18.208000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   18.208000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   18.208000] sky2 0000:02:00.0: v1.13 addr 0x34000000 irq 16 Yukon-FE (0xb7) rev 1
[   18.208000] sky2 eth0: addr 00:1b:24:26:5b:e1
[   18.316000] sky2 eth0: enabling interface
[   18.320000] sky2 eth0: ram buffer 4K
[   18.520000] snd_hda_codec: disagrees about version of symbol snd_ctl_add
[   18.520000] snd_hda_codec: Unknown symbol snd_ctl_add
[   18.520000] snd_hda_codec: disagrees about version of symbol snd_card_proc_new
[   18.520000] snd_hda_codec: Unknown symbol snd_card_proc_new
[   18.520000] snd_hda_codec: disagrees about version of symbol snd_ctl_find_id
[   18.520000] snd_hda_codec: Unknown symbol snd_ctl_find_id
[   18.520000] snd_hda_codec: disagrees about version of symbol snd_ctl_new1
[   18.520000] snd_hda_codec: Unknown symbol snd_ctl_new1
[   18.520000] snd_hda_codec: Unknown symbol snd_ctl_elem_read
[   18.520000] snd_hda_codec: Unknown symbol snd_ctl_elem_write
[   18.520000] snd_hda_codec: disagrees about version of symbol snd_pcm_hw_constraint_list
[   18.520000] snd_hda_codec: Unknown symbol snd_pcm_hw_constraint_list
[   18.520000] snd_hda_codec: disagrees about version of symbol snd_device_new
[   18.520000] snd_hda_codec: Unknown symbol snd_device_new
[   18.520000] snd_hda_codec: disagrees about version of symbol snd_pcm_hw_constraint_step
[   18.520000] snd_hda_codec: Unknown symbol snd_pcm_hw_constraint_step
[   18.520000] snd_hda_intel: disagrees about version of symbol snd_pcm_new
[   18.520000] snd_hda_intel: Unknown symbol snd_pcm_new
[   18.520000] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates
[   18.520000] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[   18.520000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[   18.520000] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[   18.520000] snd_hda_intel: Unknown symbol snd_hda_bus_new
[   18.520000] snd_hda_intel: Unknown symbol snd_hda_build_pcms
[   18.520000] snd_hda_intel: Unknown symbol snd_hda_codec_new
[   18.520000] snd_hda_intel: Unknown symbol snd_hda_queue_unsol_event
[   18.520000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_malloc_pages
[   18.520000] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[   18.520000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_ioctl
[   18.520000] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[   18.520000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_free_pages
[   18.520000] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[   18.520000] snd_hda_intel: Unknown symbol snd_hda_calc_stream_format
[   18.520000] snd_hda_intel: disagrees about version of symbol snd_pcm_set_ops
[   18.520000] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[   18.520000] snd_hda_intel: Unknown symbol snd_hda_suspend
[   18.520000] snd_hda_intel: disagrees about version of symbol snd_device_new
[   18.520000] snd_hda_intel: Unknown symbol snd_device_new
[   18.520000] snd_hda_intel: disagrees about version of symbol snd_pcm_suspend_all
[   18.520000] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[   18.520000] snd_hda_intel: Unknown symbol snd_hda_resume
[   18.520000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_integer
[   18.520000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[   18.520000] snd_hda_intel: Unknown symbol snd_hda_build_controls
[   18.520000] snd_hda_intel: disagrees about version of symbol snd_pcm_period_elapsed
[   18.520000] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[   18.520000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_step
[   18.520000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step
[   18.688000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1280b1, caps: 0xa04713/0x204000
[   18.688000] cs: IO port probe 0x100-0x3af: clean.
[   18.692000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   18.692000] cs: IO port probe 0x820-0x8ff: clean.
[   18.692000] cs: IO port probe 0xc00-0xcf7: clean.
[   18.696000] cs: IO port probe 0xa00-0xaff: clean.
[   18.748000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[   18.752000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   18.752000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   18.976000] fuse init (API version 7.8)
[   19.036000] lp: driver loaded but no devices found
[   19.100000] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
[   19.196000] ndiswrapper: driver net5211 (,11/15/2006,5.1.1.9) loaded
[   19.196000] PCI: Enabling device 0000:03:00.0 (0000 -> 0002)
[   19.196000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   19.196000] ndiswrapper (ZwClose:2467): closing handle 0xd82550e8 not implemented
[   19.196000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   19.624000] ndiswrapper: using IRQ 17
[   19.700000] NET: Registered protocol family 17
[   20.132000] wlan0: ethernet device 00:19:7e:4d:5b:1b using serialized NDIS driver: net5211, version: 0x50001, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 168C:001C.5.conf
[   20.132000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   20.136000] usbcore: registered new interface driver ndiswrapper
[   20.140000] snd_hda_codec: disagrees about version of symbol snd_ctl_add
[   20.140000] snd_hda_codec: Unknown symbol snd_ctl_add
[   20.140000] snd_hda_codec: disagrees about version of symbol snd_card_proc_new
[   20.140000] snd_hda_codec: Unknown symbol snd_card_proc_new
[   20.140000] snd_hda_codec: disagrees about version of symbol snd_ctl_find_id
[   20.140000] snd_hda_codec: Unknown symbol snd_ctl_find_id
[   20.140000] snd_hda_codec: disagrees about version of symbol snd_ctl_new1
[   20.140000] snd_hda_codec: Unknown symbol snd_ctl_new1
[   20.140000] snd_hda_codec: Unknown symbol snd_ctl_elem_read
[   20.140000] snd_hda_codec: Unknown symbol snd_ctl_elem_write
[   20.140000] snd_hda_codec: disagrees about version of symbol snd_pcm_hw_constraint_list
[   20.140000] snd_hda_codec: Unknown symbol snd_pcm_hw_constraint_list
[   20.140000] snd_hda_codec: disagrees about version of symbol snd_device_new
[   20.140000] snd_hda_codec: Unknown symbol snd_device_new
[   20.140000] snd_hda_codec: disagrees about version of symbol snd_pcm_hw_constraint_step
[   20.140000] snd_hda_codec: Unknown symbol snd_pcm_hw_constraint_step
[   20.144000] snd_hda_intel: disagrees about version of symbol snd_pcm_new
[   20.144000] snd_hda_intel: Unknown symbol snd_pcm_new
[   20.144000] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates
[   20.144000] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[   20.144000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[   20.144000] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[   20.144000] snd_hda_intel: Unknown symbol snd_hda_bus_new
[   20.144000] snd_hda_intel: Unknown symbol snd_hda_build_pcms
[   20.144000] snd_hda_intel: Unknown symbol snd_hda_codec_new
[   20.144000] snd_hda_intel: Unknown symbol snd_hda_queue_unsol_event
[   20.144000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_malloc_pages
[   20.144000] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[   20.144000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_ioctl
[   20.144000] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[   20.144000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_free_pages
[   20.144000] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[   20.144000] snd_hda_intel: Unknown symbol snd_hda_calc_stream_format
[   20.144000] snd_hda_intel: disagrees about version of symbol snd_pcm_set_ops
[   20.144000] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[   20.144000] snd_hda_intel: Unknown symbol snd_hda_suspend
[   20.144000] snd_hda_intel: disagrees about version of symbol snd_device_new
[   20.144000] snd_hda_intel: Unknown symbol snd_device_new
[   20.144000] snd_hda_intel: disagrees about version of symbol snd_pcm_suspend_all
[   20.144000] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[   20.144000] snd_hda_intel: Unknown symbol snd_hda_resume
[   20.144000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_integer
[   20.144000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[   20.144000] snd_hda_intel: Unknown symbol snd_hda_build_controls
[   20.144000] snd_hda_intel: disagrees about version of symbol snd_pcm_period_elapsed
[   20.144000] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[   20.144000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_step
[   20.144000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step
[   20.160000] Adding 1477940k swap on /dev/disk/by-uuid/08ff4819-c6d6-4d01-a9fb-742b1f24f79a.  Priority:-1 extents:1 across:1477940k
[   20.360000] EXT3 FS on sda1, internal journal
[   24.476000] Using specific hotkey driver
[   24.544000] input: Power Button (FF) as /class/input/input3
[   24.548000] ACPI: Power Button (FF) [PWRF]
[   24.580000] input: Lid Switch as /class/input/input4
[   24.584000] ACPI: Lid Switch [LID]
[   24.620000] input: Power Button (CM) as /class/input/input5
[   24.624000] ACPI: Power Button (CM) [PWRB]
[   24.656000] input: Sleep Button (CM) as /class/input/input6
[   24.660000] ACPI: Sleep Button (CM) [SLPB]
[   24.688000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   24.716000] ACPI: ACPI Dock Station Driver 
[   24.920000] ACPI: AC Adapter [ACAD] (off-line)
[   24.984000] ACPI: Battery Slot [BAT1] (battery present)
[   25.044000] ibm_acpi: ec object not found
[   25.100000] pcc_acpi: loading...
[   25.108000] wmi_add device=dddda000
[   25.108000] calling WQBA
[   28.496000] ppdev: user-space parallel port driver
[   29.800000] [drm] Initialized drm 1.1.0 20060810
[   29.956000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   29.956000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   30.724000] NET: Registered protocol family 10
[   30.724000] lo: Disabled Privacy Extensions
[   30.724000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   36.936000] apm: BIOS not found.
[   41.344000] wlan0: no IPv6 routers present
[   51.728000] wlan0: no IPv6 routers present
[  112.068000] usb 2-1: new low speed USB device using uhci_hcd and address 2
[  112.244000] usb 2-1: configuration #1 chosen from 1 choice
[  112.364000] usbcore: registered new interface driver hiddev
[  112.380000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input7
[  112.380000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.1-1
[  112.380000] usbcore: registered new interface driver usbhid
[  112.380000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[  202.532000] usb 5-4: new high speed USB device using ehci_hcd and address 3
[  202.680000] usb 5-4: configuration #1 chosen from 1 choice
keebler@K33bz-mobile:~$ 

```

and i copied everythang i was able to copy from "dmesg"  I guess it can see it here, but cant put a name on it, only have 2 usb devices connected right now, my samsung player as well as my mouse.

Also I noticed the problem with my sound card, having an issue with that as well, I have a thread on that as well, although no one replied to it. Hope someone can help me with that as well.

Thanks

---

### Post by xeth_delta on 2008-02-29
Is there any USB message on your player?
Depending on how many HDDs you have in your system, your player should be placed as sdb, sdc or sdd.

Let's assume it is sdc. To mount it:
```
sudo mkdir /mnt/k3
sudo mount /dev/sdc1 /mnt/k3
```

I am surprised it was not mounted automatically. To unmount the device, quit any program accessing it and
```
sudo umount /dev/sdc1
```

---

### Post by k33bz on 2008-02-29
I tried all 3 variables, and each time says special device does not exist. So I listed out what was in that folder, this is what I have, dont see it myself, maybe I am mssing something, take a look:

```
keebler@K33bz-mobile:/dev$ ls
acpi       ptyd6  ptysc  ptyy2       tty27  ttyca  ttys0  ttyx2
agpgart    ptyd7  ptysd  ptyy3       tty28  ttycb  ttyS0  ttyx3
bus        ptyd8  ptyse  ptyy4       tty29  ttycc  ttys1  ttyx4
cdrom      ptyd9  ptysf  ptyy5       tty3   ttycd  ttyS1  ttyx5
cdrw       ptyda  ptyt0  ptyy6       tty30  ttyce  ttys2  ttyx6
console    ptydb  ptyt1  ptyy7       tty31  ttycf  ttyS2  ttyx7
core       ptydc  ptyt2  ptyy8       tty32  ttyd0  ttys3  ttyx8
disk       ptydd  ptyt3  ptyy9       tty33  ttyd1  ttyS3  ttyx9
dri        ptyde  ptyt4  ptyya       tty34  ttyd2  ttys4  ttyxa
dvd        ptydf  ptyt5  ptyyb       tty35  ttyd3  ttys5  ttyxb
fd         ptye0  ptyt6  ptyyc       tty36  ttyd4  ttys6  ttyxc
full       ptye1  ptyt7  ptyyd       tty37  ttyd5  ttys7  ttyxd
fuse       ptye2  ptyt8  ptyye       tty38  ttyd6  ttys8  ttyxe
hpet       ptye3  ptyt9  ptyyf       tty39  ttyd7  ttys9  ttyxf
initctl    ptye4  ptyta  ptyz0       tty4   ttyd8  ttysa  ttyy0
input      ptye5  ptytb  ptyz1       tty40  ttyd9  ttysb  ttyy1
kmem       ptye6  ptytc  ptyz2       tty41  ttyda  ttysc  ttyy2
kmsg       ptye7  ptytd  ptyz3       tty42  ttydb  ttysd  ttyy3
log        ptye8  ptyte  ptyz4       tty43  ttydc  ttyse  ttyy4
loop0      ptye9  ptytf  ptyz5       tty44  ttydd  ttysf  ttyy5
MAKEDEV    ptyea  ptyu0  ptyz6       tty45  ttyde  ttyt0  ttyy6
mem        ptyeb  ptyu1  ptyz7       tty46  ttydf  ttyt1  ttyy7
net        ptyec  ptyu2  ptyz8       tty47  ttye0  ttyt2  ttyy8
null       ptyed  ptyu3  ptyz9       tty48  ttye1  ttyt3  ttyy9
nvidia0    ptyee  ptyu4  ptyza       tty49  ttye2  ttyt4  ttyya
nvidiactl  ptyef  ptyu5  ptyzb       tty5   ttye3  ttyt5  ttyyb
oldmem     ptyp0  ptyu6  ptyzc       tty50  ttye4  ttyt6  ttyyc
port       ptyp1  ptyu7  ptyzd       tty51  ttye5  ttyt7  ttyyd
ppp        ptyp2  ptyu8  ptyze       tty52  ttye6  ttyt8  ttyye
psaux      ptyp3  ptyu9  ptyzf       tty53  ttye7  ttyt9  ttyyf
ptmx       ptyp4  ptyua  ram0        tty54  ttye8  ttyta  ttyz0
pts        ptyp5  ptyub  ram1        tty55  ttye9  ttytb  ttyz1
ptya0      ptyp6  ptyuc  ram10       tty56  ttyea  ttytc  ttyz2
ptya1      ptyp7  ptyud  ram11       tty57  ttyeb  ttytd  ttyz3
ptya2      ptyp8  ptyue  ram12       tty58  ttyec  ttyte  ttyz4
ptya3      ptyp9  ptyuf  ram13       tty59  ttyed  ttytf  ttyz5
ptya4      ptypa  ptyv0  ram14       tty6   ttyee  ttyu0  ttyz6
ptya5      ptypb  ptyv1  ram15       tty60  ttyef  ttyu1  ttyz7
ptya6      ptypc  ptyv2  ram2        tty61  ttyp0  ttyu2  ttyz8
ptya7      ptypd  ptyv3  ram3        tty62  ttyp1  ttyu3  ttyz9
ptya8      ptype  ptyv4  ram4        tty63  ttyp2  ttyu4  ttyza
ptya9      ptypf  ptyv5  ram5        tty7   ttyp3  ttyu5  ttyzb
ptyaa      ptyq0  ptyv6  ram6        tty8   ttyp4  ttyu6  ttyzc
ptyab      ptyq1  ptyv7  ram7        tty9   ttyp5  ttyu7  ttyzd
ptyac      ptyq2  ptyv8  ram8        ttya0  ttyp6  ttyu8  ttyze
ptyad      ptyq3  ptyv9  ram9        ttya1  ttyp7  ttyu9  ttyzf
ptyae      ptyq4  ptyva  random      ttya2  ttyp8  ttyua  urandom
ptyaf      ptyq5  ptyvb  rtc         ttya3  ttyp9  ttyub  usbdev1.1_ep00
ptyb0      ptyq6  ptyvc  scd0        ttya4  ttypa  ttyuc  usbdev1.1_ep81
ptyb1      ptyq7  ptyvd  sda         ttya5  ttypb  ttyud  usbdev2.1_ep00
ptyb2      ptyq8  ptyve  sda1        ttya6  ttypc  ttyue  usbdev2.1_ep81
ptyb3      ptyq9  ptyvf  sda2        ttya7  ttypd  ttyuf  usbdev2.3_ep00
ptyb4      ptyqa  ptyw0  sda5        ttya8  ttype  ttyv0  usbdev2.3_ep81
ptyb5      ptyqb  ptyw1  sequencer   ttya9  ttypf  ttyv1  usbdev3.1_ep00
ptyb6      ptyqc  ptyw2  sequencer2  ttyaa  ttyq0  ttyv2  usbdev3.1_ep81
ptyb7      ptyqd  ptyw3  sg0         ttyab  ttyq1  ttyv3  usbdev4.1_ep00
ptyb8      ptyqe  ptyw4  sg1         ttyac  ttyq2  ttyv4  usbdev4.1_ep81
ptyb9      ptyqf  ptyw5  shm         ttyad  ttyq3  ttyv5  usbdev5.1_ep00
ptyba      ptyr0  ptyw6  snapshot    ttyae  ttyq4  ttyv6  usbdev5.1_ep81
ptybb      ptyr1  ptyw7  snd         ttyaf  ttyq5  ttyv7  usbdev5.3_ep00
ptybc      ptyr2  ptyw8  sndstat     ttyb0  ttyq6  ttyv8  usbdev5.3_ep02
ptybd      ptyr3  ptyw9  sr0         ttyb1  ttyq7  ttyv9  usbdev5.3_ep81
ptybe      ptyr4  ptywa  stderr      ttyb2  ttyq8  ttyva  usbdev5.3_ep83
ptybf      ptyr5  ptywb  stdin       ttyb3  ttyq9  ttyvb  vcs
ptyc0      ptyr6  ptywc  stdout      ttyb4  ttyqa  ttyvc  vcs1
ptyc1      ptyr7  ptywd  tty         ttyb5  ttyqb  ttyvd  vcs2
ptyc2      ptyr8  ptywe  tty0        ttyb6  ttyqc  ttyve  vcs3
ptyc3      ptyr9  ptywf  tty1        ttyb7  ttyqd  ttyvf  vcs4
ptyc4      ptyra  ptyx0  tty10       ttyb8  ttyqe  ttyw0  vcs5
ptyc5      ptyrb  ptyx1  tty11       ttyb9  ttyqf  ttyw1  vcs6
ptyc6      ptyrc  ptyx2  tty12       ttyba  ttyr0  ttyw2  vcs7
ptyc7      ptyrd  ptyx3  tty13       ttybb  ttyr1  ttyw3  vcs8
ptyc8      ptyre  ptyx4  tty14       ttybc  ttyr2  ttyw4  vcsa
ptyc9      ptyrf  ptyx5  tty15       ttybd  ttyr3  ttyw5  vcsa1
ptyca      ptys0  ptyx6  tty16       ttybe  ttyr4  ttyw6  vcsa2
ptycb      ptys1  ptyx7  tty17       ttybf  ttyr5  ttyw7  vcsa3
ptycc      ptys2  ptyx8  tty18       ttyc0  ttyr6  ttyw8  vcsa4
ptycd      ptys3  ptyx9  tty19       ttyc1  ttyr7  ttyw9  vcsa5
ptyce      ptys4  ptyxa  tty2        ttyc2  ttyr8  ttywa  vcsa6
ptycf      ptys5  ptyxb  tty20       ttyc3  ttyr9  ttywb  vcsa7
ptyd0      ptys6  ptyxc  tty21       ttyc4  ttyra  ttywc  vcsa8
ptyd1      ptys7  ptyxd  tty22       ttyc5  ttyrb  ttywd  watchdog
ptyd2      ptys8  ptyxe  tty23       ttyc6  ttyrc  ttywe  xconsole
ptyd3      ptys9  ptyxf  tty24       ttyc7  ttyrd  ttywf  zero
ptyd4      ptysa  ptyy0  tty25       ttyc8  ttyre  ttyx0
ptyd5      ptysb  ptyy1  tty26       ttyc9  ttyrf  ttyx1

```

---

### Post by xeth_delta on 2008-02-29
No device file seems to be associated to the player. Any message on the player screen when you plug it in?

Regarding your sound card problem, that means that the modules/drivers cannot be loaded into the kernel. It might be an incompatible interface to the kernel. Have you updated your kernel recently? Does that happn all the time? Please give me a link o that thread, too.

---

### Post by k33bz on 2008-03-01
only message i get on the player is that it is being connected, then its charging. Same thing happens when I plug it in a machine running windoze.

and here is the link to the page about my sound card issue
[http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=4167431]("http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=4167431")

And I had made alot of updates at the same time, one of them could of been a kernal update, but I couldnt say for sure, I had over 50 updates to do, and that one time I didnt bother checking to see what they were, I usual do, but was in a rush that day.

---

### Post by xeth_delta on 2008-03-01
> **k33bz said:**
> only message i get on the player is that it is being connected, then its charging. Same thing happens when I plug it in a machine running windoze.

and here is the link to the page about my sound card issue
[http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=4167431]("http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=4167431")

And I had made alot of updates at the same time, one of them could of been a kernal update, but I couldnt say for sure, I had over 50 updates to do, and that one time I didnt bother checking to see what they were, I usual do, but was in a rush that day.

Did the sound stop working after the updates? If so, that's probably what happened. In the wors case I guess you will need to recompile the drivers. It is not difficult. I will have a look at the other thread, too.

---

### Post by k33bz on 2008-03-01
> **xeth_delta said:**
> Did the sound stop working after the updates? If so, that's probably what happened. In the wors case I guess you will need to recompile the drivers. It is not difficult. I will have a look at the other thread, too.

ya, thats when it stopped working, how do i recompile the drivers?

^^^^^^^figuring out, but having problems locating my driver.


What do I do about my mp3 player though?

---

### Post by xeth_delta on 2008-03-02
> **k33bz said:**
> ya, thats when it stopped working, how do i recompile the drivers?

^^^^^^^figuring out, but having problems locating my driver.


What do I do about my mp3 player though?

Seems to me the player is not completely recognized. Could you unplug, then plug again and check dmesg. Post the results.

Did the link form anythingbutipod.com help at all?

---

### Post by k33bz on 2008-03-04
will be tryin this starting thursday

---

### Post by k33bz on 2008-03-09
> **alzie said:**
> I found this at [www.anythingbutipod.com](www.anythingbutipod.com)

They seem to be using a korean firmware update 1.05 (done on a windows box) to make the player UMS compatible.

[http://www.anythingbutipod.com/forum/showthread.php?t=8618&highlight=linux](http://www.anythingbutipod.com/forum/showthread.php?t=8618&highlight=linux) is the thread I was looking at.

Good Luck


thanks, that worked perfectly :)

---

### Post by xeth_delta on 2008-03-09
Great! you now have a fully functional player - computer link. :) Remember to mark the thread as solved.

---

### Post by k33bz on 2008-03-09
> **xeth_delta said:**
> Great! you now have a fully functional player - computer link. :) Remember to mark the thread as solved.

lol, ooops, thought I had already marked it solved, sorry bout that, well its marked as solved now.


Just need to finish up my sound problem now, but Imma take my time on it.

---

