---
title: "need help immediately with SD card thank you so much"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by soundsystem00 on 2007-03-12
I have a gateway mx3230 and Im having problems getting the sd card to read..

it detects it in the terminal. but it wont detect it at all when i put it in.. nothing happens


please helppp!!

---

### Post by VorDesigns on 2007-03-12
First with a useless topic subject like this, most people will ignore your thread.  This is a community of users who help each other.  This isn't paid technical support.
Second what is an SD card?  Stupid Dongle?  San Disk?  Screen Door?

---

### Post by soundsystem00 on 2007-03-12
Sandisk

*snip*

---

### Post by CanadaGradeEh on 2007-03-12
USB, Secure Digital, other? Despite the demeaning reply, he is right -- you should be more clear.

---

### Post by yabbadabbadont on 2007-03-12
> **VorDesigns said:**
> First with a useless topic subject like this, most people will ignore your thread.  This is a community of users who help each other.  This isn't paid technical support.
Second what is an SD card?  Stupid Dongle?  San Disk?  Screen Door?

Don't be mean.

[http://en.wikipedia.org/wiki/Secure_Digital_card](http://en.wikipedia.org/wiki/Secure_Digital_card)

To the OP, please insert a card and then open a terminal window, (Applications->Accessories->Terminal), maximize the window, then run "dmesg".  (don't include the quotation marks)  Use your mouse to select all the text on the screen and then copy it using the copy option on the Edit menu.  Then paste that text into a post here.

---

### Post by yabbadabbadont on 2007-03-12
> **soundsystem00 said:**
> Sandisk

*snip*

Replies like that, even if warranted, will most likely get you banned.  Take the high road.

---

### Post by K.Mandla on 2007-03-12
Keep it civil. If you can't help or didn't get enough information to answer, ask for more. Or don't reply.

In the mean time, for the OPer, you could check to see if the card appears as a drive with the *sudo fdisk -l* command.

---

### Post by dptxp on 2007-03-12
Quite a few users are having problems with detection of removable media, especially on laptops with built-in card readers.
I have the same problem, my MMC card (Multi-Media Card) does not show up. I have posted, but am yet to get a solution.
SD cards are very standard items, like CF cards (compact flash), sony memory sticks and MMC cards.
:guitar:

---

### Post by girishv on 2007-03-12
Hi,

I am sure this question is already answered ('cos I am using that technique on my Z60 latptop). Since, I have forgotten that post, I am trying to answer this question.

The card will not be recognized if it is not inserted in the slat BEFORE booting. To recognize it after booting, you can do the following.

# reload the module sdhce and mmc core
sudo modprobe -r sdhci
sudo modprobe -r mmc_core
sudo modprobe mmc_core
sudo modprobe sdhci

# mount the card
mount /dev/mmcblk0p1 /media/cardreader


I have put all of these in a bash script except the last command. As for some reason,
it wont mount it when called from the script. May be the kernel takes some time recognize and readies the card.



Girish

---

### Post by dptxp on 2007-03-13
The MMC card does not show even if inserted before booting. You have given some
script, but as I assume that these shall have to be run every time I power-uip, there
must be a way by which I can put an icon on desktop and run the script as batchfile
in dos.

---

### Post by treesurf on 2007-03-13
dptxp,

If your internal card reader is made by TI than this Howto may work for you.  

[http://www.ubuntuforums.org/showthread.php?t=315497](http://www.ubuntuforums.org/showthread.php?t=315497)

---

### Post by VorDesigns on 2007-03-14
[mia culpa, mia culpa]("http://weblog.infoworld.com/ittroubleshooter/archives/2006/02/mia_culpa_quote.html").
=
It was not my intention to be mean.

---

### Post by lamalex on 2007-03-14
> **VorDesigns said:**
> First with a useless topic subject like this, most people will ignore your thread.  This is a community of users who help each other.  This isn't paid technical support.
Second what is an SD card?  Stupid Dongle?  San Disk?  Screen Door?

if you're going to be rude at least be intelligent, SD is a specific type of card. Sandisk is a BRAND which makes many memory cards. SD being secure digital. Next time you're going to be rude please make sure you at least know what you're talking about kthxbye

---

### Post by soundsystem00 on 2007-03-14
> **Iamalex said:**
> if you're going to be rude at least be intelligent, SD is a specific type of card. Sandisk is a BRAND which makes many memory cards. SD being secure digital. Next time you're going to be rude please make sure you at least know what you're talking about kthxbye

Its kool. He has the ability to smart off on a message board, but I have the ability to whoop the **** outta him. Oh no wait its the internet, no I can't. Thats why he said it.

---

### Post by VorDesigns on 2007-03-15
[I'm easy enough to find.]("http://www.vordesigns.com/forum")  
I apologized, I was correct in my assertion but, inappropriate in my execution.  
Get over it.

---

### Post by soundsystem00 on 2007-03-15
I'm over it. I was gonna ask another question though about my SD card if thats okay.

I got it to work but restarted my computer and it did not work again. Is there a more solid way to keep it working. Thank you

---

### Post by soundsystem00 on 2007-03-15
BTW heres my info wheni  types desmg but its long

soundsystem00@lump:~$ dmesg
[17179569.184000] Linux version 2.6.15-28-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Feb 1 15:51:56 UTC 2007
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009e000 (usable)
[17179569.184000]  BIOS-e820: 000000000009e000 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000003be80000 (usable)
[17179569.184000]  BIOS-e820: 000000003be80000 - 000000003be8e000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000003be8e000 - 000000003bf00000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000003bf00000 - 0000000040000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[17179569.184000] 62MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f86f0
[17179569.184000] On node 0 totalpages: 245376
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 16000 pages, LIFO batch:3
[17179569.184000] DMI present.
[17179569.184000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f86b0
[17179569.184000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @  0x3be89b82
[17179569.184000] ACPI: FADT (v001 P4MP   PTLTW    0x06040000 PTL_ 0x000f4240) @  0x3be8df3c
[17179569.184000] ACPI: MADT (v001 PTLTD         APIC   0x06040000  LTP 0x00000000) @ 0x3be8dfb0
[17179569.184000] ACPI: SSDT (v001  PmRef  Cpu0Cst 0x00003001 INTL 0x20030224) @  0x3be89db1
[17179569.184000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20030224) @  0x3be89bb6
[17179569.184000] ACPI: DSDT (v001  VIA   PTL_ACPI 0x06040000 MSFT 0x02000001) @  0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x4008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:13 APIC version 20
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 3, address 0xfec00000, GSI 0-23[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] ACPI: IRQ10 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[17179569.184000] Detected 1496.589 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179570.480000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179570.484000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)[17179570.516000] Memory: 962416k/981504k available (1977k kernel code, 18412k r eserved, 605k data, 288k init, 64000k highmem)
[17179570.516000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179570.596000] Calibrating delay using timer specific routine.. 2996.38 BogoMIPS (lpj=5992761)
[17179570.596000] Security Framework v1.0.0 initialized
[17179570.596000] SELinux:  Disabled at boot.
[17179570.596000] Mount-cache hash table entries: 512
[17179570.596000] CPU: After generic identify, caps: afe9fbff 00000000 0000000000000000 00000000 00000000 00000000
[17179570.596000] CPU: After vendor identify, caps: afe9fbff 00000000 00000000 0 0000000 00000000 00000000 00000000
[17179570.596000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179570.596000] CPU: L2 cache: 1024K
[17179570.596000] CPU: After all inits, caps: afe9fbff 00000000 00000000 00000040 00000000 00000000 00000000
[17179570.596000] mtrr: v2.0 (20020519)
[17179570.596000] CPU: Intel(R) Celeron(R) M processor         1.50GHz stepping08
[17179570.596000] Enabling fast FPU save and restore... done.
[17179570.596000] Enabling unmasked SIMD FPU exception support... done.
[17179570.596000] Checking 'hlt' instruction... OK.
[17179570.612000] checking if image is initramfs... it is
[17179571.316000] Freeing initrd memory: 6618k freed
[17179571.324000] ACPI: Looking for DSDT ... not found!
[17179571.332000] ENABLING IO-APIC IRQs
[17179571.332000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[17179571.476000] NET: Registered protocol family 16
[17179571.476000] EISA bus registered
[17179571.476000] ACPI: bus type pci registered
[17179571.476000] PCI: PCI BIOS revision 2.10 entry at 0xfd85e, last bus=1
[17179571.476000] PCI: Using configuration type 1
[17179571.476000] ACPI: Subsystem revision 20051216
[17179571.476000] ACPI: Interpreter enabled
[17179571.476000] ACPI: Using IOAPIC for interrupt routing
[17179571.480000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179571.480000] PCI: Probing PCI hardware (bus 00)
[17179571.480000] Boot video device is 0000:01:00.0
[17179571.480000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179571.488000] ACPI: PCI Interrupt Link [ALKA] (IRQs 16 17 18 19 20 21 22 23) *10, disabled.
[17179571.492000] ACPI: PCI Interrupt Link [ALKB] (IRQs 16 17 18 19 20 21 22 23) *9, disabled.
[17179571.492000] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *7, disabled.
[17179571.492000] ACPI: PCI Interrupt Link [ALKD] (IRQs 21) *0, disabled.
[17179571.492000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 9 *10 11 12)
[17179571.492000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 *9 10 11 12)
[17179571.492000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 9 10 11 12) *7
[17179571.492000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 9 10 11 12) *0, disabled.
[17179571.492000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 9 10 11 12) *0, disabled.
[17179571.492000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 9 10 11 12) *0, disabled.
[17179571.492000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 9 10 11 12) *0, disabled.
[17179571.492000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 9 10 11 12) *0, disabled.
[17179571.496000] ACPI: Embedded Controller [EC] (gpe 1) interrupt mode.
[17179571.496000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179571.496000] pnp: PnP ACPI init
[17179571.496000] pnp: PnP ACPI: found 8 devices
[17179571.496000] PnPBIOS: Disabled by ACPI PNP
[17179571.496000] PCI: Using ACPI for IRQ routing
[17179571.496000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179571.504000] pnp: 00:05: ioport range 0x4d0-0x4d1 has been reserved
[17179571.504000] pnp: 00:05: ioport range 0x278-0x27b has been reserved
[17179571.504000] pnp: 00:05: ioport range 0x678-0x67b has been reserved
[17179571.504000] pnp: 00:05: ioport range 0xfe10-0xfe11 has been reserved
[17179571.504000] PCI: Failed to allocate mem resource #6:10000@d4000000 for 0000:01:00.0
[17179571.504000] PCI: Bridge: 0000:00:01.0
[17179571.504000]   IO window: disabled.
[17179571.504000]   MEM window: d4000000-d4ffffff
[17179571.504000]   PREFETCH window: d0000000-d3ffffff
[17179571.504000] PCI: Bus 2, cardbus bridge: 0000:00:0c.0
[17179571.504000]   IO window: 00002000-000020ff
[17179571.504000]   IO window: 00002400-000024ff
[17179571.504000]   PREFETCH window: 50000000-51ffffff
[17179571.504000]   MEM window: 52000000-53ffffff
[17179571.504000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179571.504000] ACPI: PCI Interrupt 0000:00:0c.0[A] -> GSI 19 (level, low) ->IRQ 177
[17179571.504000] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[17179571.504000] audit: initializing netlink socket (disabled)
[17179571.504000] audit(1173933621.504:1): initialized
[17179571.504000] highmem bounce pool size: 64 pages
[17179571.504000] VFS: Disk quotas dquot_6.5.1
[17179571.504000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179571.504000] Initializing Cryptographic API
[17179571.504000] io scheduler noop registered
[17179571.504000] io scheduler anticipatory registered
[17179571.504000] io scheduler deadline registered
[17179571.504000] io scheduler cfq registered
[17179571.504000] PCI: Bypassing VIA 8237 APIC De-Assert Message
[17179571.504000] isapnp: Scanning for PnP cards...
[17179571.856000] isapnp: No Plug & Play device found
[17179571.872000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64irq 1,12
[17179571.880000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179571.880000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179571.880000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179571.880000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 b locksize
[17179571.880000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179571.880000] ide: Assuming 33MHz system bus speed for PIO modes; override w ith idebus=xx
[17179571.884000] mice: PS/2 mouse device common for all mice
[17179571.884000] EISA: Probing bus 0 at eisa.0
[17179571.884000] Cannot allocate resource for EISA slot 1
[17179571.884000] Cannot allocate resource for EISA slot 2
[17179571.884000] Cannot allocate resource for EISA slot 4
[17179571.884000] EISA: Detected 0 cards.
[17179571.884000] NET: Registered protocol family 2
[17179571.908000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179571.920000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179571.920000] TCP established hash table entries: 131072 (order: 7, 524288 b ytes)
[17179571.920000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[17179571.920000] TCP: Hash tables configured (established 131072 bind 65536)
[17179571.920000] TCP reno registered
[17179571.920000] TCP bic registered
[17179571.920000] NET: Registered protocol family 1
[17179571.920000] NET: Registered protocol family 8
[17179571.920000] NET: Registered protocol family 20
[17179571.920000] Using IPI Shortcut mode
[17179571.920000] ACPI wakeup devices:
[17179571.920000] SLPB LID0 Z003 Z002
[17179571.920000] ACPI: (supports S0 S3 S4 S5)
[17179571.920000] Freeing unused kernel memory: 288k freed
[17179571.968000] vga16fb: initializing
[17179571.968000] vga16fb: mapped to 0xc00a0000
[17179572.100000] Console: switching to colour frame buffer device 80x25
[17179572.100000] fb0: VGA16 VGA frame buffer device
[17179573.168000] Capability LSM initialized
[17179573.276000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[17179573.276000] ACPI: Processor [CPU0] (supports 16 throttling states)
[17179573.328000] ACPI: Thermal Zone [THRM] (52 C)
[17179573.752000] VP_IDE: IDE controller at PCI slot 0000:00:0f.0
[17179573.752000] ACPI: PCI Interrupt 0000:00:0f.0[A] -> GSI 20 (level, low) ->IRQ 185
[17179573.752000] PCI: Via IRQ fixup for 0000:00:0f.0, from 0 to 9
[17179573.752000] VP_IDE: chipset revision 6
[17179573.752000] VP_IDE: not 100% native mode: will probe irqs later
[17179573.752000] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.0
[17179573.752000]     ide0: BM-DMA at 0x1c80-0x1c87, BIOS settings: hda:DMA, hdb:pio
[17179573.752000]     ide1: BM-DMA at 0x1c88-0x1c8f, BIOS settings: hdc:DMA, hdd:pio
[17179573.752000] Probing IDE interface ide0...
[17179574.168000] hda: HTS421240H9AT00, ATA DISK drive
[17179574.840000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179574.860000] Probing IDE interface ide1...
[17179575.724000] hdc: HL-DT-STCD-RW/DVD DRIVE GCC-4244N, ATAPI CD/DVD-ROM drive[17179576.060000] ide1 at 0x170-0x177,0x376 on irq 15
[17179576.068000] hda: max request size: 1024KiB
[17179576.076000] hda: 78140160 sectors (40007 MB) w/1570KiB Cache, CHS=16383/255/63, UDMA(100)
[17179576.076000] hda: cache flushes supported
[17179576.076000]  hda: hda1 hda2 < hda5 >
[17179576.156000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179576.156000] Uniform CD-ROM driver Revision: 3.20
[17179576.484000] usbcore: registered new driver usbfs
[17179576.484000] usbcore: registered new driver hub
[17179576.488000] USB Universal Host Controller Interface driver v2.3
[17179576.488000] **** SET: Misaligned resource pointer: df80b202 Type 07 Len 0[17179576.488000] ACPI: PCI Interrupt Link [ALKD] disabled and referenced, BIOSbug.
[17179576.488000] ACPI: PCI Interrupt Link [ALKD] BIOS reported IRQ 0, using IRQ 21
[17179576.488000] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 21
[17179576.488000] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [ALKD] -> GSI 21 ( level, low) -> IRQ 193
[17179576.488000] PCI: Via IRQ fixup for 0000:00:10.0, from 10 to 1
[17179576.488000] uhci_hcd 0000:00:10.0: UHCI Host Controller
[17179576.488000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[17179576.488000] uhci_hcd 0000:00:10.0: irq 193, io base 0x00001c00
[17179576.488000] hub 1-0:1.0: USB hub found
[17179576.488000] hub 1-0:1.0: 2 ports detected
[17179576.592000] ACPI: PCI Interrupt 0000:00:10.1[A] -> Link [ALKD] -> GSI 21 ( level, low) -> IRQ 193
[17179576.592000] PCI: Via IRQ fixup for 0000:00:10.1, from 10 to 1
[17179576.592000] uhci_hcd 0000:00:10.1: UHCI Host Controller
[17179576.592000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[17179576.592000] uhci_hcd 0000:00:10.1: irq 193, io base 0x00001c20
[17179576.592000] hub 2-0:1.0: USB hub found
[17179576.592000] hub 2-0:1.0: 2 ports detected
[17179576.696000] ACPI: PCI Interrupt 0000:00:10.2[B] -> Link [ALKD] -> GSI 21 ( level, low) -> IRQ 193
[17179576.696000] PCI: Via IRQ fixup for 0000:00:10.2, from 9 to 1
[17179576.696000] uhci_hcd 0000:00:10.2: UHCI Host Controller
[17179576.696000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[17179576.696000] uhci_hcd 0000:00:10.2: irq 193, io base 0x00001c40
[17179576.696000] hub 3-0:1.0: USB hub found
[17179576.696000] hub 3-0:1.0: 2 ports detected
[17179576.800000] ACPI: PCI Interrupt 0000:00:10.3[B] -> Link [ALKD] -> GSI 21 ( level, low) -> IRQ 193
[17179576.800000] PCI: Via IRQ fixup for 0000:00:10.3, from 9 to 1
[17179576.800000] uhci_hcd 0000:00:10.3: UHCI Host Controller
[17179576.800000] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[17179576.800000] uhci_hcd 0000:00:10.3: irq 193, io base 0x00001c60
[17179576.800000] hub 4-0:1.0: USB hub found
[17179576.800000] hub 4-0:1.0: 2 ports detected
[17179576.904000] ACPI: PCI Interrupt 0000:00:10.4[C] -> Link [ALKD] -> GSI 21 ( level, low) -> IRQ 193
[17179576.904000] PCI: Via IRQ fixup for 0000:00:10.4, from 7 to 1
[17179576.904000] ehci_hcd 0000:00:10.4: EHCI Host Controller
[17179576.904000] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[17179576.904000] ehci_hcd 0000:00:10.4: irq 193, io mem 0xd5200000
[17179576.904000] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 D ec 2004
[17179576.904000] hub 5-0:1.0: USB hub found
[17179576.904000] hub 5-0:1.0: 8 ports detected
[17179577.112000] Attempting manual resume
[17179577.200000] EXT3-fs: mounted filesystem with ordered data mode.
[17179577.212000] kjournald starting.  Commit interval 5 seconds
[17179589.312000] Linux agpgart interface v0.101 (c) Dave Jones
[17179589.320000] agpgart: Detected VIA P4M800CE chipset
[17179589.336000] agpgart: AGP aperture is 256M @ 0xc0000000
[17179589.680000] ACPI: PCI Interrupt 0000:00:0c.0[A] -> GSI 19 (level, low) ->IRQ 177
[17179589.680000] Yenta: CardBus bridge found at 0000:00:0c.0 [107b:0216]
[17179589.680000] Yenta: Enabling burst memory read transactions
[17179589.680000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179589.680000] Yenta: Routing CardBus interrupts to PCI
[17179589.680000] Yenta TI: socket 0000:00:0c.0, mfunc 0x00aa1b22, devctl 0x64
[17179589.692000] sdhci: Secure Digital Host Controller Interface driver, 0.10
[17179589.692000] sdhci: Copyright(c) Pierre Ossman
[17179589.780000] rtl_ieee80211_crypt: registered algorithm 'NULL'
[17179589.780000] rtl_ieee80211_crypt: registered algorithm 'TKIP'
[17179589.780000] rtl_ieee80211_crypt: registered algorithm 'WEP'
[17179589.780000] rtl_ieee80211_crypt: registered algorithm 'CCMP'
[17179589.788000]
[17179589.788000] Linux kernel driver for RTL8180 / RTL8185 based WLAN cards
[17179589.788000] Copyright (c) 2004-2005, Andrea Merello
[17179589.788000] rtl8180: Initializing module
[17179589.788000] rtl8180: Wireless extensions version 19
[17179589.788000] rtl8180: Initializing proc filesystem
[17179589.912000] Yenta: ISA IRQ mask 0x08f8, PCI irq 177
[17179589.912000] Socket status: 30000006
[17179589.920000] PCI: Enabling device 0000:00:0c.3 (0000 -> 0002)
[17179589.920000] ACPI: PCI Interrupt 0000:00:0c.3[A] -> GSI 19 (level, low) ->IRQ 177
[17179589.920000] PCI: Setting latency timer of device 0000:00:0c.3 to 64
[17179589.972000] sdhci: ============== REGISTER DUMP ==============
[17179589.972000] sdhci: Sys addr: 0x00000000 | Version:  0x00008900
[17179589.972000] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
[17179589.972000] sdhci: Argument: 0x00000000 | Trn mode: 0x00000000
[17179589.972000] sdhci: Present:  0x000a0000 | Host ctl: 0x00000000
[17179589.972000] sdhci: Power:    0x00000000 | Blk gap:  0x00000000
[17179589.972000] sdhci: Walk up:  0x00000000 | Clock:    0x00000000
[17179589.972000] sdhci: Timeout:  0x0000000e | Int stat: 0x00000000
[17179589.972000] sdhci: Int enab: 0x11ff00cf | Sig enab: 0x11ff00cf
[17179589.972000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[17179589.972000] sdhci: Caps:     0x01e030b0 | Max curr: 0x00000034
[17179589.972000] sdhci: ===========================================
[17179590.020000] mmc0: SDHCI at 0x54002200 irq 177 DMA
[17179590.020000] rtl8180: Configuring chip resources
[17179590.020000] PCI: Enabling device 0000:00:0e.0 (0000 -> 0003)
[17179590.020000] ACPI: PCI Interrupt 0000:00:0e.0[A] -> GSI 17 (level, low) ->IRQ 201
[17179590.020000] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[17179590.020000] rtl8180: Memory mapped space @ 0x54002000
[17179590.020000] rtl8180: MAC controller is a RTL8185 b/g (V. D)
[17179590.020000] rtl8180: This is a MINI-PCI NIC
[17179590.020000] rtl8180: Reported EEPROM chip is a 93c46 (1Kbit)
[17179590.024000] rtl8180: Card MAC address is 00:c0:a8:b5:28:19
[17179590.040000] rtl8180: EEPROM version 105
[17179590.044000] rtl8180: Card reports RF frontend Realtek 8225
[17179590.044000] rtl8180: WW:This driver has EXPERIMENTAL support for this chipset.
[17179590.044000] rtl8180: WW:use it with care and at your own risk and
[17179590.044000] rtl8180: WW:**PLEASE** REPORT SUCCESS/INSUCCESS TO [email]andreamrl@tiscali.it[/email]
[17179590.044000] rtl8180: Energy threshold: b
[17179590.044000] rtl8180: PAPE from CONFIG2: 6
[17179590.044000] rtl8180: IRQ 201
[17179590.044000] rtl8180: Driver probe completed
[17179590.044000]
[17179590.280000] Real Time Clock Driver v1.12
[17179590.564000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179590.612000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179590.660000] input: PC Speaker as /class/input/input1
[17179590.676000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald B ecker
[17179590.676000] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 23 (level, low) ->IRQ 209
[17179590.676000] PCI: Via IRQ fixup for 0000:00:12.0, from 10 to 1
[17179590.680000] eth0: VIA Rhine II at 0x11800, 00:03:25:38:7a:64, IRQ 209.
[17179590.680000] eth0: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[17179590.764000] **** SET: Misaligned resource pointer: f70a2ec2 Type 07 Len 0[17179590.764000] ACPI: PCI Interrupt Link [ALKC] disabled and referenced, BIOSbug.
[17179590.764000] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
[17179590.764000] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[17179590.764000] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 ( level, low) -> IRQ 217
[17179590.764000] PCI: Via IRQ fixup for 0000:00:11.5, from 7 to 9
[17179590.764000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[17179591.292000] ACPI: PCI Interrupt 0000:00:11.6[C] -> Link [ALKC] -> GSI 22 ( level, low) -> IRQ 217
[17179591.292000] PCI: Via IRQ fixup for 0000:00:11.6, from 7 to 9
[17179591.296000] PCI: Setting latency timer of device 0000:00:11.6 to 64
[17179591.376000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x23aeb3, caps: 0xa04713/0x10008
[17179591.384000] cs: IO port probe 0x100-0x3af: clean.
[17179591.384000] cs: IO port probe 0x3e0-0x4ff: clean.
[17179591.388000] cs: IO port probe 0x820-0x8ff: clean.
[17179591.388000] cs: IO port probe 0xc00-0xcf7: clean.
[17179591.388000] cs: IO port probe 0xa00-0xaff: clean.
[17179591.416000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[17179591.472000] ts: Compaq touchscreen protocol output
[17179591.516000] rtl8180: Bringing up iface
[17179591.904000] MC'97 1 converters and GPIO not ready (0x0)
[17179591.984000] rtl8180: Card successfully reset
[17179593.116000] eth0: link down
[17179593.200000] lp: driver loaded but no devices found
[17179593.280000] Adding 1622524k swap on /dev/hda5.  Priority:-1 extents:1 across:1622524k
[17179593.428000] EXT3 FS on hda1, internal journal
[17179593.608000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179593.608000] md: bitmap version 4.39
[17179594.428000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[17179594.520000] NET: Registered protocol family 17
[17179595.024000] cdrom: open failed.
[17179596.936000] Linking with 05B404941317
[17179596.956000] Associated successfully
[17179596.956000] Using G rates
[17179604.604000] ACPI: AC Adapter [AC] (on-line)
[17179604.868000] ACPI: Battery Slot [BAT0] (battery present)
[17179604.956000] ACPI: Power Button (FF) [PWRF]
[17179604.956000] ACPI: Power Button (CM) [PWRB]
[17179604.956000] ACPI: Sleep Button (CM) [SLPB]
[17179604.956000] ACPI: Lid Switch [LID0]
[17179605.056000] ibm_acpi: ec object not found
[17179605.088000] pcc_acpi: loading...
[17179622.836000] ppdev: user-space parallel port driver
[17179623.256000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179623.256000] apm: overridden by ACPI.
[17179623.548000] Bluetooth: Core ver 2.8
[17179623.548000] NET: Registered protocol family 31
[17179623.548000] Bluetooth: HCI device and connection manager initialized
[17179623.548000] Bluetooth: HCI socket layer initialized
[17179623.600000] Bluetooth: L2CAP ver 2.8
[17179623.600000] Bluetooth: L2CAP socket layer initialized
[17179623.604000] Bluetooth: RFCOMM socket layer initialized
[17179623.604000] Bluetooth: RFCOMM TTY layer initialized
[17179623.604000] Bluetooth: RFCOMM ver 1.7
[17181743.916000] Associated successfully
[17181743.916000] Using G rates

---

### Post by treesurf on 2007-03-15
What did you do to make it work that one time?

---

### Post by soundsystem00 on 2007-03-15
Wow it seems to have disappeared from the thread seroiusly. The man told me to prode the card getting some numbers, then paste the numbers again with another command. It works but only temporarily and I forgot to do the step to make it contemporary.

---

