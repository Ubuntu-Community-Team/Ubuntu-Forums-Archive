---
title: "Ubuntu impossibly slow on my laptop."
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by KachimiGaNai on 2007-11-18
Hello, I've been poking around reading as many forums as possible to find a fix, but nothing has been close enough to mine that it provides a solution.

I have a Toshiba Tecra 8100, it's a Pentium III 700mhz, with 256mb RAM, and a 40Gb drive. I've had XP running on it for ages, and it ran just fine. I had zero problems with XP, but being a nerd, I decided it was time to try a new OS. I only use the laptop for Firefox, Pidgin, Thunderbird, and that is it. 

I installed Ubuntu 7.04 off a Live CD. It ran perfect, it was slow on the live CD, but not really bad. I had it install, and I was happy. I used it for a few months. Then, stupidly it came up with a "Upgrade to 7.10 :D :D :D :DDDD" and I was like "Sure :D"

This led to being trapped in a time warp where nothing ever ran full speed again. It took 5 minutes for Firefox to load, ages for Thunderbird, etc. So I said "ok screw this" and I threw a new 7.10 CD in, and it never really loaded before I got tired of a 5 hour install and killed it. I got frustrated and tried my old 7.04 CD, and it was ridiculously slow! 

I was upset at this point, so I said "Ok maybe I have hardware problems." I loaded XP from start to finish in 1 hour. It actually takes longer to load Firefox in Ubuntu than it does to install XP AND run Firefox! I read forums, and decided to try Xubuntu to see if speed was the issue. Xubuntu took over 5 hours last night to install (non Live CD) and when it did, it loads up in a SCORCHING 30 minutes. 

So here's my question, and my thoughts:


My laptop hardware is fine, I've run checks on the drives and hardware in XP and off bootable CDs and it all checks out ok. The laptop screams in XP by comparison. There is an issue here, that is hardware related, but I am not sure what. The CPU is at 100% most of the time and yet it runs horribly horribly slow. I personally think either it detected the video card wrong, or it thinks it is always running athe CPU to 100mhz to save power. I need ideas on things to check, as I REALLY want to use Ubuntu, but I can't be without this machine anymore, since I am tired of IMs when I am working on something or playing fullscreen games.

I *really* appreciate any help anyone can provide me. :) I am just looking for any commands or ways to check things to see what is going wrong.

---

### Post by overdrank on 2007-11-18
> **KachimiGaNai said:**
> Hello, I've been poking around reading as many forums as possible to find a fix, but nothing has been close enough to mine that it provides a solution.

I have a Toshiba Tecra 8100, it's a Pentium III 700mhz, with 256mb RAM, and a 40Gb drive. I've had XP running on it for ages, and it ran just fine. I had zero problems with XP, but being a nerd, I decided it was time to try a new OS. I only use the laptop for Firefox, Pidgin, Thunderbird, and that is it. 

I installed Ubuntu 7.04 off a Live CD. It ran perfect, it was slow on the live CD, but not really bad. I had it install, and I was happy. I used it for a few months. Then, stupidly it came up with a "Upgrade to 7.10 :D :D :D :DDDD" and I was like "Sure :D"

This led to being trapped in a time warp where nothing ever ran full speed again. It took 5 minutes for Firefox to load, ages for Thunderbird, etc. So I said "ok screw this" and I threw a new 7.10 CD in, and it never really loaded before I got tired of a 5 hour install and killed it. I got frustrated and tried my old 7.04 CD, and it was ridiculously slow! 

I was upset at this point, so I said "Ok maybe I have hardware problems." I loaded XP from start to finish in 1 hour. It actually takes longer to load Firefox in Ubuntu than it does to install XP AND run Firefox! I read forums, and decided to try Xubuntu to see if speed was the issue. Xubuntu took over 5 hours last night to install (non Live CD) and when it did, it loads up in a SCORCHING 30 minutes. 

So here's my question, and my thoughts:


My laptop hardware is fine, I've run checks on the drives and hardware in XP and off bootable CDs and it all checks out ok. The laptop screams in XP by comparison. There is an issue here, that is hardware related, but I am not sure what. The CPU is at 100% most of the time and yet it runs horribly horribly slow. I personally think either it detected the video card wrong, or it thinks it is always running athe CPU to 100mhz to save power. I need ideas on things to check, as I REALLY want to use Ubuntu, but I can't be without this machine anymore, since I am tired of IMs when I am working on something or playing fullscreen games.

I *really* appreciate any help anyone can provide me. :) I am just looking for any commands or ways to check things to see what is going wrong.

Hi and I have to admit when running Gutsy on 256mb of ram and intergrated video sharing that memory the system if slow. But not as slow as you are speaking of. I would recommend Feisty Xubuntu. 
[http://cdimage.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimage.ubuntu.com/xubuntu/releases/feisty/release/)
Good luck!

---

### Post by LowSky on 2007-11-18
instead of firefox  and thunderbird, try swiftweasel and swiftdove. Both are Firefox based but with enhancement to run better on linux.


here a link
[http://swiftweasel.tuxfamily.org/](http://swiftweasel.tuxfamily.org/)

---

### Post by sports fan Matt on 2007-11-18
I second that,..I uninstalled firefox completely on mine and only run swiftweasel..I may try for xubuntu also..(382 ram here) but its not bad to have it either burned..:)

---

### Post by LowSky on 2007-11-18
why not try XFCE before switching... go to synaptic and look for XFCE4 or install Xubuntu-desktop to get the entire Xubuntu pakage

---

### Post by moulsonp on 2007-11-18
Definately sounds like something is wrong. At what point to do you first notice this extreme slowness? Does it boot up OK? A couple of command you can use to check the basics:

1) You say that CPU is always at 100%? Use the 'top' command to view all running processes, and then type a capital 'P' to sort by CPU usage. What are the top couple of processes?

2) Check how much memory Ubuntu has detected, is in use, and how much swap is available. Use the 'free' command to see all this and paste the results here if you are not sure.

3) Do you get any errors when booting? 'dmesg' will let you view the boot output from a terminal.

4) 'cat /proc/cpuinfo' for details on what it has detected your CPU as.

---

### Post by KachimiGaNai on 2007-11-18
Thanks for the quick responses!

It is currently updating the software via the web, so that may affect these results. Also, I noticed it hasn't turned the fan on once, and it's running really cool. I really feel it's detecting the hardware wrong. I am running out of CD-Rs and patience, as I currently have Ubuntu 7.04, Ubuntu 7.10, Xubuntu 7.10, and Xubuntu 7.10 alternate

Copying the dmesg text file off to USB took about an hour, the actual copy process was fast, but the windows moved so slow, and it took so long to mount the drive that it was impossible to get it to stick. I must have pulled the USB stick out 10 times before the text file was actually on it.

**top:** It's currently at 75% or higher usage, it spikes a lot though. 

Xorg: 50%
synaptic: 24%
dpkg-deb: 12%
top: 5%


**free:**
Mem: 255876, used: 251716, free: 4160, cached: 66880
-/+ buffers/cache: used: 182908, free: 72968 
Swap: 746980, used: 35812, free: 711168

**cpu:** Pentium III, 700mhz


Lastly...

**dmesg:** Mostly gibberish to me, it did have some errors it looks like.


[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000ffe0000 (usable)
[    0.000000]  BIOS-e820: 000000000ffe0000 - 000000000fff0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000000fff0000 - 0000000010000000 (reserved)
[    0.000000]  BIOS-e820: 00000000100a0000 - 00000000100b6e00 (reserved)
[    0.000000]  BIOS-e820: 00000000100b6e00 - 00000000100b7000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000100b7000 - 0000000010100000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 255MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 65504) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    65504
[    0.000000]   HighMem     65504 ->    65504
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    65504
[    0.000000] On node 0 totalpages: 65504
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 479 pages used for memmap
[    0.000000]   Normal zone: 60929 pages, LIFO batch:15
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F4FD0 checksum 0
[    0.000000] ACPI: RSDP 000F4FD0, 0014 (r0 TOSHIB)
[    0.000000] ACPI: RSDT 0FFE0000, 0028 (r1 TOSHIB 750        970814 TASM  4010000)
[    0.000000] ACPI: FACP 0FFE0054, 0074 (r1 TOSHIB 750        970814 TASM  4010000)
[    0.000000] ACPI: DSDT 0FFE00C8, 6CFB (r1 TOSHIB 8100     20000614 MSFT  100000A)
[    0.000000] ACPI: FACS 100B6E00, 0040
[    0.000000] ACPI: PM-Timer IO Port: 0xfe08
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 10100000:efe80000)
[    0.000000] Built 1 zonelists.  Total pages: 64993
[    0.000000] Kernel command line: root=UUID=37554f47-4cd9-4702-8eaf-d1f1b70e4bd9 ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffd000 (0120c000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] Detected 697.438 MHz processor.
[13008.576749] Console: colour VGA+ 80x25
[13008.577323] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[13008.577911] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[13008.606433] Memory: 248332k/262016k available (2015k kernel code, 13200k reserved, 916k data, 364k init, 0k highmem)
[13008.606464] virtual kernel memory layout:
[13008.606467]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[13008.606472]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[13008.606476]     vmalloc : 0xd0800000 - 0xff7fe000   ( 751 MB)
[13008.606481]     lowmem  : 0xc0000000 - 0xcffe0000   ( 255 MB)
[13008.606485]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[13008.606490]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[13008.606494]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[13008.606504] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[13008.606604] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[13008.686627] Calibrating delay using timer specific routine.. 1396.09 BogoMIPS (lpj=2792194)
[13008.686698] Security Framework v1.0.0 initialized
[13008.686717] SELinux:  Disabled at boot.
[13008.686759] Mount-cache hash table entries: 512
[13008.687067] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[13008.687097] CPU: L1 I cache: 16K, L1 D cache: 16K
[13008.687105] CPU: L2 cache: 256K
[13008.687114] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[13008.687142] Compat vDSO mapped to ffffe000.
[13008.687176] Checking 'hlt' instruction... OK.
[13008.702867] SMP alternatives: switching to UP code
[13008.703283] Freeing SMP alternatives: 11k freed
[13008.704034] Early unpacking initramfs... done
[13009.635772] ACPI: Core revision 20070126
[13009.636180] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[13009.641166] ACPI: setting ELCR to 0200 (from 0808)
[13009.641565] CPU0: Intel Pentium III (Coppermine) stepping 06
[13009.641582] SMP motherboard not detected.
[13009.641589] Local APIC not detected. Using dummy APIC emulation.
[13009.641700] Brought up 1 CPUs
[13009.642024] Booting paravirtualized kernel on bare hardware
[13009.642161] Time: 13:05:41  Date: 10/18/107
[13009.642238] NET: Registered protocol family 16
[13009.642621] EISA bus registered
[13009.642650] ACPI: bus type pci registered
[13009.646582] PCI: PCI BIOS revision 2.10 entry at 0xfee03, last bus=21
[13009.646590] PCI: Using configuration type 1
[13009.646596] Setting up standard PCI resources
[13009.650851] ACPI: EC: Look up EC in DSDT
[13009.658223] ACPI: Interpreter enabled
[13009.658234] ACPI: (supports S0 S1 S3 S4 S5)
[13009.658285] ACPI: Using PIC for interrupt routing
[13009.673621] ACPI: PCI Root Bridge [PCI0] (0000:00)
[13009.673647] PCI: Probing PCI hardware (bus 00)
[13009.674062] PCI quirk: region fe00-fe3f claimed by PIIX4 ACPI
[13009.674072] PCI quirk: region fe70-fe7f claimed by PIIX4 SMB
[13009.674083] PIIX4 devres B PIO at 006c-006f
[13009.674790] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[13009.675004] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[13009.684065] ACPI: PCI Interrupt Link [LNKA] (IRQs 5 6 7 10 *11 12)
[13009.685182] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 6 7 10 *11 12)
[13009.686321] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 6 7 10 *11 12)
[13009.687599] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 6 7 10 *11 12)
[13009.688874] ACPI: PCI Interrupt Link [LNKE] (IRQs *3 4)
[13009.690079] ACPI: Power Resource [PIHD] (on)
[13009.690648] ACPI: Power Resource [PMHD] (on)
[13009.690957] ACPI: Power Resource [PFAN] (off)
[13009.690980] Linux Plug and Play Support v0.97 (c) Adam Belay
[13009.691011] pnp: PnP ACPI init
[13009.691040] ACPI: bus type pnp registered
[13009.694354] PCI: setting IRQ 13 as level-triggered
[13009.707347] pnp: PnP ACPI: found 12 devices
[13009.707357] ACPI: ACPI bus type pnp unregistered
[13009.707368] PnPBIOS: Disabled by ACPI PNP
[13009.707531] PCI: Using ACPI for IRQ routing
[13009.707540] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[13009.715914] NET: Registered protocol family 8
[13009.715921] NET: Registered protocol family 20
[13009.716114] pnp: 00:00: iomem range 0x0-0x9ffff could not be reserved
[13009.716124] pnp: 00:00: iomem range 0x0-0x0 could not be reserved
[13009.716132] pnp: 00:00: iomem range 0x0-0x0 could not be reserved
[13009.716141] pnp: 00:00: iomem range 0xf0000-0xfffff could not be reserved
[13009.718492] Time: tsc clocksource has been installed.
[13009.747058] PCI: Bridge: 0000:00:01.0
[13009.747064]   IO window: disabled.
[13009.747074]   MEM window: f0000000-f7ffffff
[13009.747083]   PREFETCH window: 30000000-300fffff
[13009.747093] PCI: Bus 2, cardbus bridge: 0000:00:0b.0
[13009.747100]   IO window: 00001000-000010ff
[13009.747109]   IO window: 00001400-000014ff
[13009.747118]   PREFETCH window: 20000000-23ffffff
[13009.747128]   MEM window: 24000000-27ffffff
[13009.747136] PCI: Bus 6, cardbus bridge: 0000:00:0b.1
[13009.747143]   IO window: 00001800-000018ff
[13009.747152]   IO window: 00002000-000020ff
[13009.747161]   PREFETCH window: 28000000-2bffffff
[13009.747170]   MEM window: 2c000000-2fffffff
[13009.747600] PCI: Enabling device 0000:00:0b.0 (0000 -> 0003)
[13009.748625] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[13009.748635] PCI: setting IRQ 11 as level-triggered
[13009.748642] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[13009.748957] PCI: Enabling device 0000:00:0b.1 (0000 -> 0003)
[13009.749982] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[13009.749990] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[13009.750034] NET: Registered protocol family 2
[13009.786616] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[13009.786731] TCP established hash table entries: 8192 (order: 4, 98304 bytes)
[13009.787017] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[13009.787237] TCP: Hash tables configured (established 8192 bind 8192)
[13009.787245] TCP reno registered
[13009.798867] checking if image is initramfs...<6>Switched to high resolution mode on CPU 0
[13010.596293]  it is
[13011.575297] Freeing initrd memory: 7069k freed
[13011.576204] audit: initializing netlink socket (disabled)
[13011.576241] audit(1195391142.616:1): initialized
[13011.582982] VFS: Disk quotas dquot_6.5.1
[13011.583178] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[13011.583508] io scheduler noop registered
[13011.583517] io scheduler anticipatory registered
[13011.583524] io scheduler deadline registered
[13011.583587] io scheduler cfq registered (default)
[13011.583615] Limiting direct PCI/PCI transfers.
[13011.583666] Boot video device is 0000:01:00.0
[13011.584080] isapnp: Scanning for PnP cards...
[13011.937240] isapnp: No Plug & Play device found
[13012.022730] Real Time Clock Driver v1.12ac
[13012.022976] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[13012.023128] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[13012.025051] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[13012.027226] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[13012.027839] input: Macintosh mouse button emulation as /class/input/input0
[13012.028072] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[13012.031026] serio: i8042 KBD port at 0x60,0x64 irq 1
[13012.031043] serio: i8042 AUX port at 0x60,0x64 irq 12
[13012.031527] mice: PS/2 mouse device common for all mice
[13012.031838] EISA: Probing bus 0 at eisa.0
[13012.031857] Cannot allocate resource for EISA slot 1
[13012.031865] Cannot allocate resource for EISA slot 2
[13012.031893] EISA: Detected 0 cards.
[13012.032156] TCP cubic registered
[13012.032197] NET: Registered protocol family 1
[13012.032266] Using IPI No-Shortcut mode
[13012.032651]   Magic number: 15:274:79
[13012.034353] Freeing unused kernel memory: 364k freed
[13012.074105] input: AT Translated Set 2 keyboard as /class/input/input1
[13013.245731] Clocksource tsc unstable (delta = -896778734 ns)
[13013.251293] Time: acpi_pm clocksource has been installed.
[13013.319259] AppArmor: AppArmor initialized<5>audit(1195391145.149:2):  type=1505 info="AppArmor initialized" pid=1128
[13013.342681] fuse init (API version 7.8)
[13013.360089] Failure registering capabilities with primary security module.
[13013.375968] ACPI: Transitioning device [FAN] to D3
[13013.375980] ACPI: Transitioning device [FAN] to D3
[13013.375991] ACPI: Fan [FAN] (off)
[13013.395078] ACPI: CPU0 (power states: C1[C1] C2[C2])
[13013.399817] ACPI: Thermal Zone [THRM] (43 C)
[13015.547454] SCSI subsystem initialized
[13015.578302] libata version 2.21 loaded.
[13015.587388] ata_piix 0000:00:05.1: version 2.11
[13015.587866] scsi0 : ata_piix
[13015.588020] scsi1 : ata_piix
[13015.589070] ata1: PATA max UDMA/33 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001fff0 irq 14
[13015.589083] ata2: PATA max UDMA/33 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001fff8 irq 15
[13015.611772] ata1.00: ATA-6: ST94811A, 3.05, max UDMA/100
[13015.611787] ata1.00: 78140160 sectors, multi 0: LBA48 
[13015.614988] ata1.00: configured for UDMA/33
[13015.646945] usbcore: registered new interface driver usbfs
[13015.647027] usbcore: registered new interface driver hub
[13015.647099] usbcore: registered new device driver usb
[13015.665826] USB Universal Host Controller Interface driver v3.0
[13015.693987] ata2.00: ATAPI: TOSHIBA DVD-ROM SD-C2302, 1315, max UDMA/33
[13015.715144] ata2.00: configured for UDMA/33
[13015.797020] scsi 0:0:0:0: Direct-Access     ATA      ST94811A         3.05 PQ: 0 ANSI: 5
[13015.797877] scsi 1:0:0:0: CD-ROM            TOSHIBA  DVD-ROM SD-C2302 1315 PQ: 0 ANSI: 5
[13015.799572] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[13015.799584] ACPI: PCI Interrupt 0000:00:05.2[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[13015.799634] uhci_hcd 0000:00:05.2: UHCI Host Controller
[13015.800040] uhci_hcd 0000:00:05.2: new USB bus registered, assigned bus number 1
[13015.800091] uhci_hcd 0000:00:05.2: irq 11, io base 0x0000ff80
[13015.800514] usb usb1: configuration #1 chosen from 1 choice
[13015.800613] hub 1-0:1.0: USB hub found
[13015.800639] hub 1-0:1.0: 2 ports detected
[13016.206164] Floppy drive(s): fd0 is 1.44M
[13016.237150] FDC 0 is a post-1991 82077
[13016.404391] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[13016.404631] sd 0:0:0:0: [sda] Write Protect is off
[13016.404643] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[13016.405743] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[13016.406821] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[13016.407356] sd 0:0:0:0: [sda] Write Protect is off
[13016.407368] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[13016.407828] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[13016.407876]  sda: sda1 sda2 < sda5 >
[13016.482126] sd 0:0:0:0: [sda] Attached SCSI disk
[13016.502462] sd 0:0:0:0: Attached scsi generic sg0 type 0
[13016.503012] sr 1:0:0:0: Attached scsi generic sg1 type 5
[13016.510859] sr0: scsi3-mmc drive: 24x/24x cd/rw xa/form2 cdda tray
[13016.510876] Uniform CD-ROM driver Revision: 3.20
[13016.511662] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   30.484000] Marking TSC unstable due to: possible TSC halt in C2.
[   30.980000] Attempting manual resume
[   30.980000] swsusp: Resume From Partition 8:5
[   30.980000] PM: Checking swsusp image.
[   30.984000] PM: Resume from disk failed.
[   31.472000] kjournald starting.  Commit interval 5 seconds
[   31.472000] EXT3-fs: mounted filesystem with ordered data mode.
[   87.396000] Linux agpgart interface v0.102 (c) Dave Jones
[   87.444000] agpgart: Detected an Intel 440BX Chipset.
[   87.572000] agpgart: AGP aperture is 256M @ 0xd0000000
[   92.872000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   92.916000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  100.384000] Yenta: CardBus bridge found at 0000:00:0b.0 [1179:0001]
[  100.552000] Yenta: ISA IRQ mask 0x04b8, PCI irq 11
[  100.552000] Socket status: 30000007
[  100.556000] Yenta: CardBus bridge found at 0000:00:0b.1 [1179:0001]
[  100.792000] Yenta: ISA IRQ mask 0x04b8, PCI irq 11
[  100.792000] Socket status: 30000020
[  100.800000] irda_init()
[  100.800000] NET: Registered protocol family 23
[  100.860000] piix4_smbus 0000:00:05.3: Found 0000:00:05.3 device
[  101.056000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[  101.056000] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[  101.072000] IrDA: Registered device irda0
[  101.072000] toshoboe: Using multiple tasks, version $Id: donauboe.c V2.18 ven jan 10 03:14:16 2003$
[  101.432000] pccard: CardBus card inserted into slot 1
[  103.016000] input: PC Speaker as /class/input/input2
[  107.852000] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[  113.064000] parport_pc 00:0b: reported by Plug and Play ACPI
[  113.064000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[  117.016000] cs: IO port probe 0x100-0x3af: clean.
[  117.024000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[  117.028000] cs: IO port probe 0x820-0x8ff: clean.
[  117.028000] cs: IO port probe 0xc00-0xcf7: clean.
[  117.032000] cs: IO port probe 0xa00-0xaff: clean.
[  117.100000] cs: IO port probe 0x100-0x3af: clean.
[  117.108000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[  117.112000] cs: IO port probe 0x820-0x8ff: clean.
[  117.116000] cs: IO port probe 0xc00-0xcf7: clean.
[  117.120000] cs: IO port probe 0xa00-0xaff: clean.
[  120.376000] 8139too Fast Ethernet driver 0.9.28
[  120.376000] PCI: Enabling device 0000:06:00.0 (0000 -> 0003)
[  120.376000] ACPI: PCI Interrupt 0000:06:00.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[  120.376000] PCI: Setting latency timer of device 0000:06:00.0 to 64
[  120.384000] eth0: RealTek RTL8139 at 0xd0906000, 00:40:05:87:b0:73, IRQ 11
[  120.384000] eth0:  Identified 8139 chip type 'RTL-8139C'
[  126.676000] ACPI: PCI Interrupt 0000:00:0c.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[  134.376000] loop: module loaded
[  134.784000] lp0: using parport0 (interrupt-driven).
[  135.860000] Adding 746980k swap on /dev/sda5.  Priority:-1 extents:1 across:746980k
[  137.540000] EXT3 FS on sda1, internal journal
[  171.620000] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.19a-dev
[  171.620000] toshiba_acpi:     HCI method: \_SB_.VALD.GHCI
[  171.684000] toshiba_acpi: Toshiba hotkeys are sent as ACPI events
[  171.684000] toshiba_acpi: ktoshkeyd will check 2 times per second
[  171.728000] toshiba_acpi: Dropped 0 keys from the queue on startup
[  172.172000] ACPI: ACPI Dock Station Driver 
[  172.824000] ACPI: AC Adapter [ADP1] (on-line)
[  173.336000] ACPI: Battery Slot [BAT1] (battery present)
[  173.340000] ACPI: Battery Slot [BAT2] (battery absent)
[  174.416000] ACPI: Video Device [VGA] (multi-head: yes  rom: yes  post: no)
[  175.824000] input: Power Button (FF) as /class/input/input4
[  175.828000] ACPI: Power Button (FF) [PWRF]
[  175.864000] input: Lid Switch as /class/input/input5
[  175.868000] ACPI: Lid Switch [LID]
[  204.296000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  205.952000] ppdev: user-space parallel port driver
[  207.192000] audit(1195409348.818:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4919 profile="/usr/sbin/cupsd"
[  208.464000] apm: BIOS version 1.2 Flags 0x02 (Driver version 1.16ac)
[  208.464000] apm: overridden by ACPI.
[  217.024000] Failure registering capabilities with primary security module.
[  225.872000] NET: Registered protocol family 17
[  247.556000] [drm] Initialized drm 1.1.0 20060810
[  247.640000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[  247.684000] [drm] Initialized savage 2.4.1 20050313 on minor 0
[  247.696000] mtrr: base(0xf2000000) is not aligned on a size(0x5000000) boundary
[  247.708000] agpgart: Found an AGP 1.0 compliant device at 0000:00:00.0.
[  247.712000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[  247.716000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[  261.024000] NET: Registered protocol family 10
[  261.028000] lo: Disabled Privacy Extensions
[  271.200000] eth0: no IPv6 routers present

---

### Post by KachimiGaNai on 2007-11-18
I forgot to mention, that it boots up ok, in the sense that it doesn't flash warnings or errors. However, the boot process takes a long time, like 5-10 minutes. It's slow from the start, it never suddenly becomes slow or anything. The entire process from install to completion to running is always slow.

---

### Post by Paulmd on 2007-11-18
> **KachimiGaNai said:**
> Hello, I've been poking around reading as many forums as possible to find a fix, but nothing has been close enough to mine that it provides a solution.

I have a Toshiba Tecra 8100, it's a Pentium III 700mhz, with 256mb RAM, and a 40Gb drive. I've had XP running on it for ages, and it ran just fine. I had zero problems with XP, but being a nerd, I decided it was time to try a new OS. I only use the laptop for Firefox, Pidgin, Thunderbird, and that is it. 

I installed Ubuntu 7.04 off a Live CD. It ran perfect, it was slow on the live CD, but not really bad. I had it install, and I was happy. I used it for a few months. Then, stupidly it came up with a "Upgrade to 7.10 :D :D :D :DDDD" and I was like "Sure :D"

This led to being trapped in a time warp where nothing ever ran full speed again. It took 5 minutes for Firefox to load, ages for Thunderbird, etc. So I said "ok screw this" and I threw a new 7.10 CD in, and it never really loaded before I got tired of a 5 hour install and killed it. I got frustrated and tried my old 7.04 CD, and it was ridiculously slow! 

I was upset at this point, so I said "Ok maybe I have hardware problems." I loaded XP from start to finish in 1 hour. It actually takes longer to load Firefox in Ubuntu than it does to install XP AND run Firefox! I read forums, and decided to try Xubuntu to see if speed was the issue. Xubuntu took over 5 hours last night to install (non Live CD) and when it did, it loads up in a SCORCHING 30 minutes. 

So here's my question, and my thoughts:


My laptop hardware is fine, I've run checks on the drives and hardware in XP and off bootable CDs and it all checks out ok. The laptop screams in XP by comparison. There is an issue here, that is hardware related, but I am not sure what. The CPU is at 100% most of the time and yet it runs horribly horribly slow. I personally think either it detected the video card wrong, or it thinks it is always running athe CPU to 100mhz to save power. I need ideas on things to check, as I REALLY want to use Ubuntu, but I can't be without this machine anymore, since I am tired of IMs when I am working on something or playing fullscreen games.

I *really* appreciate any help anyone can provide me. :) I am just looking for any commands or ways to check things to see what is going wrong.

My earnest advice is then to switch back to Windows. As Windows works fine on your machine and Ubuntu doesn't. To be honest, Ubuntu has lots of really odd bugs that no one has really solved. So does Windows, but they haven't manifested on your machine, the Ubuntu ones have.

There could indeed be some cpu throttling issue, that Ubuntu hasn't solved yet. P3-m , and later chips use speedstep.

---

### Post by moulsonp on 2007-11-18
Well from what you've posted there everything looks normal. From what you've described it seems that your problem lies with the graphics (XWindows) capabilities.

If you log into Ubuntu via a text based terminal (<ctrl> + <alt> + <F1>) do all the operations is the system responsiveness OK? (<ctrl> + <alt> + <F7>) to switch back to your XWindows session btw. 

 I see you have an AGP graphics card. What exact model card do you have? Output of 'lspci -vvv' would be useful. Also, is hardware acceleration enabled? You can see this by 'glxinfo | grep -i direct'. If it output "direct rendering: Yes" then you are OK on that front, but even without hardware acceleration it shouldn't be going that slow.

---

### Post by moulsonp on 2007-11-18
Also, contents of your /etc/X11/xorg.conf file and /var/log/Xorg.0.log might help suss the problem.

---

### Post by Rev60073 on 2007-11-18
I had the same issues trying to install Ubuntu on an old Dell C600 (256MB, PIII-600), it took forever just for it to attempt to start the partitioner for the installation.

I could have tried to use Xubuntu to install it. I tried Fedora Werewolf (8) live CD, and worked like a charm...

---

### Post by KachimiGaNai on 2007-11-18
Okay, here are the logs. It's an old S3 savage card built in, it's like AGP 2x if the specs website is to be believed. It runs a lot faster in Alt+Ctrl+F1 mode, but I don't have anything much to run in terminal outside of simple commands.

I uploaded the X11 stuff, because of the ridiculous length.

Thanks again for helping me out guys! I see a load of topics on "My tecra 8100 runs slow!" and it's weird, because Ubuntu 7.04 the first time ran *awesome* I was falling in love with it. I had 0 problems with it at all. Serves me for trying to upgrade it.

**lspci:**

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
	Subsystem: Toshiba America Info Systems Toshiba Tecra 8100 Laptop System Chipset
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
	Latency: 64
	Region 0: Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 0000f000-00000fff
	Memory behind bridge: f0000000-f7ffffff
	Prefetchable memory behind bridge: 30000000-300fffff
	Secondary status: 66MHz+ FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA+ MAbort- >Reset- FastB2B+

00:05.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0

00:05.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64
	Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	Region 4: I/O ports at fff0 [size=16]

00:05.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64
	Interrupt: pin D routed to IRQ 11
	Region 4: I/O ports at ff80 [size=32]

00:05.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin ? routed to IRQ 9

00:07.0 Communication controller: Agere Systems 56k WinModem (rev 01)
	Subsystem: Toshiba America Info Systems Internal V.90 Modem
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (63000ns min, 3500ns max)
	Interrupt: pin A routed to IRQ 3
	Region 0: Memory at ffefff00 (32-bit, non-prefetchable) [size=256]
	Region 1: I/O ports at 02f8 [size=8]
	Region 2: I/O ports at 1c00 [size=256]
	Capabilities: <access denied>

00:09.0 IRDA controller: Toshiba America Info Systems FIR Port Type-DO
	Subsystem: Toshiba America Info Systems FIR Port Type-DO
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64
	Interrupt: pin A routed to IRQ 11
	Region 0: I/O ports at ff60 [size=32]
	Capabilities: <access denied>

00:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 20)
	Subsystem: Toshiba America Info Systems Unknown device 0001
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 168
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at 30100000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=00, secondary=02, subordinate=05, sec-latency=0
	Memory window 0: 20000000-23fff000 (prefetchable)
	Memory window 1: 24000000-27fff000
	I/O window 0: 00001000-000010ff
	I/O window 1: 00001400-000014ff
	BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset- 16bInt+ PostWrite+
	16-bit legacy interface ports at 0001

00:0b.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 20)
	Subsystem: Toshiba America Info Systems Unknown device 0001
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 168
	Interrupt: pin B routed to IRQ 11
	Region 0: Memory at 30101000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=00, secondary=06, subordinate=09, sec-latency=0
	Memory window 0: 28000000-2bfff000 (prefetchable)
	Memory window 1: 2c000000-2ffff000
	I/O window 0: 00001800-000018ff
	I/O window 1: 00002000-000020ff
	BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset- 16bInt- PostWrite+
	16-bit legacy interface ports at 0001

00:0c.0 Multimedia audio controller: Yamaha Corporation YMF-744B [DS-1S Audio Controller] (rev 02)
	Subsystem: Toshiba America Info Systems Unknown device 0001
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR+
	Latency: 64 (1250ns min, 6250ns max)
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at efff8000 (32-bit, non-prefetchable) [size=32K]
	Region 1: I/O ports at ff00 [size=64]
	Region 2: I/O ports at fefc [size=4]
	Capabilities: <access denied>

01:00.0 VGA compatible controller: S3 Inc. 86C270-294 Savage/MX-MV (rev 11) (prog-if 00 [VGA])
	Subsystem: Toshiba America Info Systems Unknown device 0001
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 248 (1000ns min, 63750ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at f0000000 (32-bit, non-prefetchable) [size=128M]
	Expansion ROM at 30000000 [disabled] [size=64K]
	Capabilities: <access denied>

06:00.0 Ethernet controller: D-Link System Inc DFE-690TXD CardBus PC Card (rev 10)
	Subsystem: D-Link System Inc DFE-690TXD CardBus PC Card
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64 (8000ns min, 16000ns max)
	Interrupt: pin A routed to IRQ 11
	Region 0: I/O ports at 1800 [size=256]
	Region 1: Memory at 2c000000 (32-bit, non-prefetchable) [size=512]
	Capabilities: <access denied>



[http://www.megalixir.com/Xorg.0.log](http://www.megalixir.com/Xorg.0.log)
[http://www.megalixir.com/xorg.conf](http://www.megalixir.com/xorg.conf)

---

### Post by KachimiGaNai on 2007-11-19
bump, any last advice before I give up and just install Windows again?

---

### Post by mivo on 2007-11-19
> **Paulmd said:**
> My earnest advice is then to switch back to Windows. [...] To be honest, Ubuntu has lots of really odd bugs that no one has really solved. So does Windows, but they haven't manifested on your machine, the Ubuntu ones have.

There are other Linux distros if an unresolved bug in Ubuntu causes problems and cannot be worked around. Going back to Windows is a poor resolution, because it is a five year old OS whose successor is already on the market. He can have an up-to-date OS on his laptop with better support and security.

---

### Post by linuxlizard on 2007-11-19
Ubuntu is slow on my laptop as well with similar specs- p3 700mhz, 192 mb ram. Xubuntu is very slow also on it. However, pcfluxboxos flies- boots faster than ubuntu on my athlon 2800+ with 756 mb ram  and everything snaps open at least as fast. It's like getting a new computer. Boots in less than 30 secs.

Oh yeah- it's much faster than win 98 on this laptop as well, which is what it was built for.

---

### Post by Paulmd on 2007-11-19
> **mivo said:**
> There are other Linux distros if an unresolved bug in Ubuntu causes problems and cannot be worked around. Going back to Windows is a poor resolution, because it is a five year old OS whose successor is already on the market. He can have an up-to-date OS on his laptop with better support and security.


The problem is that there is a huge amount of overlapping code among the linuxes. You can never be certian that a bug is confined to one distro, or to a library that's shared across many. The lower level packages (ie, drivers) are common to most of the linuxes.  They may be recompiled, repackaged, or modified, a little, but they're more or less identical. 

In this case, where there's a subtle hardware bug, you are likely to wind up in the same situation as before, if you were to switch. Essensially: same hardware->same buggy drivers.

Also, there aren't that many other distributions that are well supported. I can only think of 3. Ubuntu, Suse, Fedora/redhat.

If the OP goes to another distro, and it works well, i will be pleasantly suprised.

---

### Post by KachimiGaNai on 2007-11-20
Tried Fluxubuntu 7.10, same problems. I'm not surprised. From what I've read the newer kernels are detecting stuff wrong. So it thinks I have a SCSI drive, and runs at like 100ish Mhz. The laptop never gets warm enough to turn the fan on. I am going to try 7.04 one last time, but I used up 10 CD-Rs on this venture.

I'll be switching back to XP after 7.04 fails. I guess I could try 6.10 which I have sitting around, but that didn't do very well with USB or anything else. It's a serious understatement to say I am disappointed. :(

Thanks again everyone for the help.

---

### Post by Paulmd on 2007-11-20
> **KachimiGaNai said:**
> Tried Fluxubuntu 7.10, same problems. I'm not surprised. From what I've read the newer kernels are detecting stuff wrong. So it thinks I have a SCSI drive, and runs at like 100ish Mhz. The laptop never gets warm enough to turn the fan on. I am going to try 7.04 one last time, but I used up 10 CD-Rs on this venture.

Would you believe that they did that deliberately? The detecting IDE as scsi, that is. 




> 
I'll be switching back to XP after 7.04 fails. I guess I could try 6.10 which I have sitting around, but that didn't do very well with USB or anything else. It's a serious understatement to say I am disappointed. :(

Thanks again everyone for the help.


Maybe in a few more years they will have the issues ironed out. :(

---

### Post by mivo on 2007-11-20
> **Paulmd said:**
> The problem is that there is a huge amount of overlapping code among the linuxes. You can never be certian that a bug is confined to one distro, or to a library that's shared across many.   

My new desktop has a Linux-problematic mainboard. Ubuntu choked on it right away and would not even load the Live CD without special boot parameters. Once installed, it stilled balked.  and needed yet another boot option to work. It ran flawlessly after that, though. Fedora threw error messages, but gave a good hint at what boot option was needed, so it was more helpful -- and it ran quickly. ArchLinux did neither: it did not balk and it did not throw error messages, it simply ran right out of the box. These are just three distros, and all three behaved differently on the same hardware.

> Also, there aren't that many other distributions that are well supported. I can only think of 3. Ubuntu, Suse, Fedora/redhat.

I get daily updates for ArchLinux (it is a rolling release distro), and I have Pidgin 2.2.2 and Firefox 2.0.0.9 on it. Neither has been released for Gutsy yet (as of the other day anyway). There are many other distros that are well supported -- Mandrivia, Debian, Gentoo, etc. and many of the "smaller" distros. They have different target groups and goals, so I wouldn't recommend all of them to the topic starter, but his hardware is also not suited for the latest releases of the the full-blown, eye-candy-rich distros like Ubuntu 7,10, SuSE 10.3 or Fedora 8. For good performance he will need to pick a lighter distros. Xubuntu is where I'd start. (Well, actually, I'd go with ArchLinux, though it isn't the best choice for a first distro), and then I'd look at Puppy Linux, DSL, etc. Just to see what works and what doesn't.

---

### Post by Fred06 on 2007-11-20
KachimiGanai,
I had Xubuntu Feisty installed on my Tecra 8100. It was running very well, and even very fast with E17.
But since I upgraded to Gutsy, the PC is running 10 times slower !!
The problem seems due to the new kernel in Gutsy. I still have a 2.6.20 kernel, from my previous install of Feisty. If I boot on this kernel, Xubuntu Gutsy runs quite weel. But as soon as I boot on the 2.6.22, it is a mess. So, I would advise you to go for Xubuntu Feisty, you should not be disapointed.

---

### Post by mivo on 2007-11-20
Were these issues corrected in 2.6.23? (That's the kernel I'm using, but Ubuntu ships with .22.) An overview of the changes can be found here: [http://kernelnewbies.org/Linux_2_6_23](http://kernelnewbies.org/Linux_2_6_23)

---

### Post by scrooge_74 on 2007-11-20
> **Fred06 said:**
> KachimiGanai,
I had Xubuntu Feisty installed on my Tecra 8100. It was running very well, and even very fast with E17.
But since I upgraded to Gutsy, the PC is running 10 times slower !!
The problem seems due to the new kernel in Gutsy. I still have a 2.6.20 kernel, from my previous install of Feisty. If I boot on this kernel, Xubuntu Gutsy runs quite weel. But as soon as I boot on the 2.6.22, it is a mess. So, I would advise you to go for Xubuntu Feisty, you should not be disapointed.

I am running 2.6.22-2-686, ok, I do have 512 of ram but I use Xfce4 (plus I am running Debian Lennny).  It is lighting fast

---

### Post by KachimiGaNai on 2007-11-20
I tried the Live CD of 7.04 I had handy once again, and everything seems to be running fine. The only error I've gotten so far was a samba error upon clicking the updates. When I get the chance I will see if I can't find a slightly lighter version of the same release, like a 7.04 Fluxubuntu, Xubuntu, and so on.

The thing is, I don't mind fooling with Linux when it comes to things like the fan never turning on, (I managed to work that out with a cron job @reboot) but this was a ridiculous waste of time. 

I don't really need flash, I just really like Ubuntu's way of handling software installation, and everything working without dealing with a terminal until I CHOOSE to. I know with 7.04 Ubuntu I'll have Teamspeak, Pidgin, Firefox, and Thunderbird. Fluxubuntu looked decent, but I am only basing my decision solely on the smaller ISO size, and the pictures.

---

### Post by Mike Armstrong on 2007-11-20
I have 6.06 running on an old Dell laptop (was Win ME), Ages to install with the alt install disc and was slow till I paid £21 and put another 256Mb ram in it ...problems solved.

---

### Post by stchman on 2007-11-20
> **KachimiGaNai said:**
> Hello, I've been poking around reading as many forums as possible to find a fix, but nothing has been close enough to mine that it provides a solution.

I have a Toshiba Tecra 8100, it's a Pentium III 700mhz, with 256mb RAM, and a 40Gb drive. I've had XP running on it for ages, and it ran just fine. I had zero problems with XP, but being a nerd, I decided it was time to try a new OS. I only use the laptop for Firefox, Pidgin, Thunderbird, and that is it. 

I installed Ubuntu 7.04 off a Live CD. It ran perfect, it was slow on the live CD, but not really bad. I had it install, and I was happy. I used it for a few months. Then, stupidly it came up with a "Upgrade to 7.10 :D :D :D :DDDD" and I was like "Sure :D"

This led to being trapped in a time warp where nothing ever ran full speed again. It took 5 minutes for Firefox to load, ages for Thunderbird, etc. So I said "ok screw this" and I threw a new 7.10 CD in, and it never really loaded before I got tired of a 5 hour install and killed it. I got frustrated and tried my old 7.04 CD, and it was ridiculously slow! 

I was upset at this point, so I said "Ok maybe I have hardware problems." I loaded XP from start to finish in 1 hour. It actually takes longer to load Firefox in Ubuntu than it does to install XP AND run Firefox! I read forums, and decided to try Xubuntu to see if speed was the issue. Xubuntu took over 5 hours last night to install (non Live CD) and when it did, it loads up in a SCORCHING 30 minutes. 

So here's my question, and my thoughts:


My laptop hardware is fine, I've run checks on the drives and hardware in XP and off bootable CDs and it all checks out ok. The laptop screams in XP by comparison. There is an issue here, that is hardware related, but I am not sure what. The CPU is at 100% most of the time and yet it runs horribly horribly slow. I personally think either it detected the video card wrong, or it thinks it is always running athe CPU to 100mhz to save power. I need ideas on things to check, as I REALLY want to use Ubuntu, but I can't be without this machine anymore, since I am tired of IMs when I am working on something or playing fullscreen games.

I *really* appreciate any help anyone can provide me. :) I am just looking for any commands or ways to check things to see what is going wrong.

Go back to Feisty.  I had the same thing on my laptop as well.  There are a lot of folks complaining about the super slow boot up.  Install Ubuntu with the nuke the hard drive option.

---

### Post by HermanAB on 2007-11-20
There a few ways to speed up a slow machine:
a. Add more RAM.  Linux penguins luuuurve RAM.
b. Install a DNS slave.  This will improve web page access times enormously.
c. Install Xfce4 or IceWM to replace the slooooooow Gnome or KDE desktops.
d. Install a faster disk drive.  Cheap lapop drives are slooooow. A modern 7200 or 10000 rpm drive will improve the boot time a lot.

Note that you can run Gnome or KDE desktops with the Xfce4/IceWM window managers if you read up on it a bit.  This kind of Frankenstein setup will speed things up enormously, without changing your desktop experience.  However, some people actually prefer IceWM/Xfce/Rox desktops over Gnome/KDE.  Especially IceWM with Rox, really rocks.

So, you can mix and match things yourself to get the speed back up, or you can go the easy route and install Xubuntu, which uses Xfce and runs blazingly fast compared to Ubuntu.

Cheers,

Herman

---

### Post by Wiebelhaus on 2007-11-20
Honestly , your computer does not have enough juice to run Ubuntu , Try another distro like [Fluxbuntu]("http://www.google.com/url?sa=t&ct=res&cd=1&url=http%3A%2F%2Ffluxbuntu.org%2F&ei=HC5DR5zWHYX8gASwv9jUAw&usg=AFQjCNFVbQVIdSzCAp3lMIdGJpbzt42_aA&sig2=kJWoYdwxU5-kcCrPxMmESA") , PCLinuxOS , Debian , Puppy linux etc. all these can be found with a nifty google search , My choice on old hardware is Fluxbuntu which is still in release candidacy but is steller non-the-less.

Good Luck.

---

### Post by KachimiGaNai on 2007-11-20
Sorry, but I am going to have to disagree. It's a 700mhz laptop with 256mb of RAM. It's not an electric toaster. I have Ubuntu running, and it was running fine as of this morning when I left for work. I will not be buying RAM, or sacrificing usability for a super light version. XP runs very quick, and 7.04 runs just as quick. I also feel a DNS slave is a ridiculous amount of work to speed up access to websites when they already load up fine.

The problem was not with the machine itself, the speed issue was with the 7.10 versions I was trying. I can't really stress that anymore than I did, but to reiterate it went from a FIVE HOUR INSTALL to a ONE HOUR INSTALL. Without even stress testing it, I can tell it's back to normal speed. Previously it booted up in about 30 minutes, now I can barely get a drink from the fridge and it's up.

I will probably end up going with Xubuntu 7.04, since it still has the vast majority of the Ubuntu features I am looking for. Thanks again for all the help guys, I really do appreciate the suggestions. :)

---

### Post by scrooge_74 on 2007-11-20
I second your idea of using Xubuntu, I have a laptop with 256 of RAM with a slightly faster processor running ok with Ubuntu, changed that to Xubuntu and it improve a lot,  Then I was bored and I put Debian Etch using Xfce as window manager and it is running like a champ.

On the DNS issue, the only thing I would advice is to have a good set of DNS servers in your config file, Open DNS works well for me.  That way I avoid those days when my ISP DNS servers since to be on a strike and loading pages becomes a headache.  I have  hook myself to networks in which I was the only one surfing because their DNS servers were not working properly.

---

### Post by scf on 2007-11-22
Yesterday I upgraded my Tecra 8100 laptop (700MHz, 512Mb RAM) from feisty to gutsy and run into the same unresponsive, extremely slow system described in the thread.

The solution has been to revert back to the feisty kernel using the instructions on [http://blog.vaxius.net/?p=19](http://blog.vaxius.net/?p=19)

> If this is a clean install, you need to download and install them from the Ubuntu Packages site. Those who have upgraded from 7.04 should skip this step. I’ve put the links to the files you need below.

    * linux-image-2.6.20-16-generic
    * linux-headers-2.6.20-16
    * linux-headers-2.6.20-16-generic
    * linux-restricted-modules-2.6.20-16-generic

Now install them.

$ sudo dpkg -i linux-image-2.6.20-16-generic*.deb linux-headers-2.6.20-16*.deb linux-restricted-modules-2.6.20-16-generic*.deb

If you upgraded, you just need to change the default in GRUB. 

I do not know wether it is a SLUB related thing or not, but the system boots up to the logon screen from the grub menu in one minute compared to 4.5 minutes with the original gutsy kernel.

I hope it helps.

Ciao,
Simone

It would be interesting to know if we have to blame SLUB or something else. Any volounteer to recompile the gutsy kernel without it and try?

---

