---
title: "webcam installation"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by angelosapo on 2008-02-02
Hi,

this is my first post.

I am a newbie in Linux,installed xubuntu a few days ago and managed to accomplish a lot actually:) but for that webcam. :mad:

I searched the forum, read a lot of threads, got quite confused, installed some software (followed links in within the forum) to test the webcam or something like that, but...I did not manage to make it work.(Obviously)

I got the webcam from ebay. There is no name,model or anything the like.

Item title: USB WEBCAM CAMERA MIC MIKROFON 1.3M6LED KAMAERA WEB CAM
Web Address: [http://cgi.ebay.com.au/ws/eBayISAPI.dll?ViewItem&item=130163415258](http://cgi.ebay.com.au/ws/eBayISAPI.dll?ViewItem&item=130163415258)
Item number: 130163415258

I have a cd which includes the drivers but it does no run.

Any ideas? My primary purpose is using the webcam with skype, I downloaded the BETA version and it does not recognise teh webcam.

So, it would be great if you could provide me with some hints or ideas on how to start.

Thanx in advance and sorry for the long text. I wanted to be as descriptive as possible.

---

### Post by Shazaam on 2008-02-02
Well, you could get good news and bad news. First off, does it work on a Windows machine?

---

### Post by spiderbatdad on 2008-02-02
could you please post results of command```
lsmod
```or look for yourself to see if you see the cam loaded at usbcore. The cam must be plugged in when you run the command.

---

### Post by angelosapo on 2008-02-02
Yes!

Although after during installation of the driver from the cd that came along there was a message stating that it did not pass microsoft authentication process or something like that, but it worked!

thanx for the reply!

---

### Post by angelosapo on 2008-02-02
> **spiderbatdad said:**
> could you please post results of command```
lsmod
```

angel@angel-laptop:~$ lsmod
Module                  Size  Used by
ipv6                  273892  8 
af_packet              24840  2 
radeon                125472  1 
drm                    83348  2 radeon
ppdev                  10244  0 
acpi_cpufreq           10568  0 
speedstep_lib           6404  0 
cpufreq_stats           7232  0 
cpufreq_userspace       5280  0 
cpufreq_ondemand        9612  1 
cpufreq_powersave       2688  0 
freq_table              5792  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8072  0 
video                  18060  0 
dock                   10656  0 
sbs                    19592  0 
button                  8976  0 
battery                11012  0 
container               5504  0 
ac                      6148  0 
sbp2                   24072  0 
lp                     12580  0 
joydev                 11328  0 
snd_ali5451            24460  1 
snd_ac97_codec        100644  1 snd_ali5451
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
pcmcia                 41388  0 
psmouse                39952  0 
snd_rawmidi            25728  1 snd_seq_midi
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
serio_raw               8068  0 
pcspkr                  4224  0 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
i2c_ali15x3             9092  0 
i2c_ali1535             8196  0 
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i2c_core               26112  2 i2c_ali15x3,i2c_ali1535
snd                    54660  12 snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
snd_page_alloc         11400  1 snd_pcm
pcmcia_core            40980  3 pcmcia,yenta_socket,rsrc_nonstatic
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
ati_agp                10124  1 
agpgart                35016  2 drm,ati_agp
evdev                  11136  5 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
ide_cd                 32672  1 
cdrom                  37536  1 ide_cd
ide_disk               18560  3 
floppy                 60004  0 
alim15x3               12556  0 [permanent]
ide_core              116804  3 ide_cd,ide_disk,alim15x3
natsemi                31328  0 
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
ehci_hcd               36492  0 
ata_generic             8452  0 
libata                125168  1 ata_generic
scsi_mod              147084  2 sbp2,libata
uhci_hcd               26640  0 
usbcore               138632  3 ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  2 acpi_cpufreq,thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor
angel@angel-laptop:~$ 


or look for yourself to see if you see the cam loaded at usbcore. The cam must be plugged in when you run the command.

The camera is always plugged in.

As for the usbcore....I think I might know what that is, but do not know where or how to find it.
:lolflag:

---

### Post by spiderbatdad on 2008-02-02
ok maybe try unplugging the cam for a second, then plug back in and post the result of```
dmesg | tail
```

---

### Post by angelosapo on 2008-02-02
angel@angel-laptop:~$ dmesg
[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Dec 18 08:02:57 UTC 2007 (Ubuntu 2.6.22-14.47-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d8000 - 00000000000e0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000bf70000 (usable)
[    0.000000]  BIOS-e820: 000000000bf70000 - 000000000bf7c000 (ACPI data)
[    0.000000]  BIOS-e820: 000000000bf7c000 - 000000000bf80000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000000bf80000 - 000000000c000000 (reserved)
[    0.000000]  BIOS-e820: 000000001bf80000 - 000000001c000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 191MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 49008) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    49008
[    0.000000]   HighMem     49008 ->    49008
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    49008
[    0.000000] On node 0 totalpages: 49008
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 350 pages used for memmap
[    0.000000]   Normal zone: 44562 pages, LIFO batch:7
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6AB0 checksum 0
[    0.000000] ACPI: RSDP 000F6AB0, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 0BF7529B, 002C (r1 PTLTD    RSDT    6040000  LTP        0)
[    0.000000] ACPI: FACP 0BF7BF64, 0074 (r1 ATI    Salmon    6040000 ATI     F4240)
[    0.000000] ACPI: DSDT 0BF752C7, 6C9D (r1    ATI MS2_1535  6040000 MSFT  100000E)
[    0.000000] ACPI: FACS 0BF7CFC0, 0040
[    0.000000] ACPI: BOOT 0BF7BFD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1c000000:e3f80000)
[    0.000000] Built 1 zonelists.  Total pages: 48626
[    0.000000] Kernel command line: root=UUID=524043ee-ee4d-4e69-b264-b6675f4d766d ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffd000 (0118c000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] Detected 2791.119 MHz processor.
[  182.601743] Console: colour VGA+ 80x25
[  182.602137] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[  182.602392] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[  182.614298] Memory: 182824k/196032k available (2015k kernel code, 12680k reserved, 916k data, 364k init, 0k highmem)
[  182.614322] virtual kernel memory layout:
[  182.614323]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[  182.614324]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[  182.614328]     vmalloc : 0xcc800000 - 0xff7fe000   ( 815 MB)
[  182.614329]     lowmem  : 0xc0000000 - 0xcbf70000   ( 191 MB)
[  182.614333]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[  182.614334]       .data : 0xc02f7de6 - 0xc03dce84   ( 916 kB)
[  182.614337]       .text : 0xc0100000 - 0xc02f7de6   (2015 kB)
[  182.614343] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[  182.614438] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[  182.694303] Calibrating delay using timer specific routine.. 5589.74 BogoMIPS (lpj=11179489)
[  182.694371] Security Framework v1.0.0 initialized
[  182.694395] SELinux:  Disabled at boot.
[  182.694421] Mount-cache hash table entries: 512
[  182.694775] CPU: After generic identify, caps: bfebf9ff 00000000 00000000 00000000 00004400 00000000 00000000
[  182.694802] CPU: Trace cache: 12K uops, L1 D cache: 8K
[  182.694807] CPU: L2 cache: 512K
[  182.694813] CPU: Hyper-Threading is disabled
[  182.694818] CPU: After all inits, caps: bfebf9ff 00000000 00000000 0000b080 00004400 00000000 00000000
[  182.694842] Compat vDSO mapped to ffffe000.
[  182.694877] Checking 'hlt' instruction... OK.
[  182.710544] SMP alternatives: switching to UP code
[  182.711114] Freeing SMP alternatives: 11k freed
[  182.711799] Early unpacking initramfs... done
[  183.272644] ACPI: Core revision 20070126
[  183.272821] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[  183.276521] ACPI: setting ELCR to 0200 (from 0420)
[  183.278778] CPU0: Intel Mobile Intel(R) Pentium(R) 4     CPU 2.80GHz stepping 09
[  183.278786] SMP motherboard not detected.
[  183.278789] Local APIC not detected. Using dummy APIC emulation.
[  183.278842] Brought up 1 CPUs
[  183.279040] Booting paravirtualized kernel on bare hardware
[  183.279149] Time:  1:03:50  Date: 01/03/108
[  183.279187] NET: Registered protocol family 16
[  183.279340] EISA bus registered
[  183.279359] ACPI: bus type pci registered
[  183.335772] PCI: PCI BIOS revision 2.10 entry at 0xfd89b, last bus=2
[  183.335775] PCI: Using configuration type 1
[  183.335777] Setting up standard PCI resources
[  183.338437] ACPI: EC: Look up EC in DSDT
[  183.339718] ACPI: EC: GPE=0x18, ports=0x66, 0x62
[  183.368124] ACPI: Interpreter enabled
[  183.368131] ACPI: (supports S0 S3 S4 S5)
[  183.368152] ACPI: Using PIC for interrupt routing
[  183.375345] ACPI: EC: GPE=0x18, ports=0x66, 0x62
[  183.375409] ACPI: PCI Root Bridge [PCI0] (0000:00)
[  183.375427] PCI: Probing PCI hardware (bus 00)
[  183.375921] PCI quirk: region 8000-803f claimed by ali7101 ACPI
[  183.375924] PCI quirk: region 8040-805f claimed by ali7101 SMB
[  183.376152] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[  183.376231] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[  183.377881] ACPI: PCI Interrupt Link [LNK0] (IRQs 7 10) *0, disabled.
[  183.378007] ACPI: PCI Interrupt Link [LNK1] (IRQs 7 *10)
[  183.378129] ACPI: PCI Interrupt Link [LNK2] (IRQs 7 *10)
[  183.378250] ACPI: PCI Interrupt Link [LNK3] (IRQs 7 *10)
[  183.378372] ACPI: PCI Interrupt Link [LNK4] (IRQs 7 10) *0, disabled.
[  183.378495] ACPI: PCI Interrupt Link [LNK5] (IRQs 7 11) *0, disabled.
[  183.378618] ACPI: PCI Interrupt Link [LNK6] (IRQs 7 10) *0, disabled.
[  183.378740] ACPI: PCI Interrupt Link [LNK7] (IRQs *5)
[  183.378861] ACPI: PCI Interrupt Link [LNK8] (IRQs 7 10) *0, disabled.
[  183.378974] Linux Plug and Play Support v0.97 (c) Adam Belay
[  183.378990] pnp: PnP ACPI init
[  183.379008] ACPI: bus type pnp registered
[  183.382169] pnp: PnP ACPI: found 11 devices
[  183.382173] ACPI: ACPI bus type pnp unregistered
[  183.382181] PnPBIOS: Disabled by ACPI PNP
[  183.382260] PCI: Using ACPI for IRQ routing
[  183.382264] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[  183.384908] NET: Registered protocol family 8
[  183.384911] NET: Registered protocol family 20
[  183.385027] pnp: 00:07: ioport range 0x40b-0x40b has been reserved
[  183.385030] pnp: 00:07: ioport range 0x480-0x48f has been reserved
[  183.385032] pnp: 00:07: ioport range 0x4d0-0x4d1 has been reserved
[  183.385035] pnp: 00:07: ioport range 0x4d6-0x4d6 has been reserved
[  183.385037] pnp: 00:07: ioport range 0x8000-0x807f could not be reserved
[  183.385041] pnp: 00:07: iomem range 0xd0009000-0xd0009fff has been reserved
[  183.388691] Time: tsc clocksource has been installed.
[  183.415361] PCI: Bridge: 0000:00:01.0
[  183.415364]   IO window: 9000-9fff
[  183.415368]   MEM window: d0300000-d03fffff
[  183.415372]   PREFETCH window: d8000000-dfffffff
[  183.415376] PCI: Bus 2, cardbus bridge: 0000:00:0a.0
[  183.415378]   IO window: 00001800-000018ff
[  183.415382]   IO window: 00001c00-00001cff
[  183.415385]   PREFETCH window: 20000000-23ffffff
[  183.415389]   MEM window: 24000000-27ffffff
[  183.415413] PCI: Enabling device 0000:00:0a.0 (0000 -> 0003)
[  183.415620] ACPI: PCI Interrupt Link [LNK5] enabled at IRQ 11
[  183.415624] PCI: setting IRQ 11 as level-triggered
[  183.415627] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNK5] -> GSI 11 (level, low) -> IRQ 11
[  183.415650] NET: Registered protocol family 2
[  183.452610] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[  183.452668] TCP established hash table entries: 8192 (order: 4, 98304 bytes)
[  183.452775] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[  183.452844] TCP: Hash tables configured (established 8192 bind 8192)
[  183.452847] TCP reno registered
[  183.464668] checking if image is initramfs... it is
[  183.915516] Switched to high resolution mode on CPU 0
[  184.041869] Freeing initrd memory: 7063k freed
[  184.042142] Simple Boot Flag at 0x37 set to 0x1
[  184.042459] audit: initializing netlink socket (disabled)
[  184.042485] audit(1202000630.260:1): initialized
[  184.044879] VFS: Disk quotas dquot_6.5.1
[  184.044942] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[  184.045076] io scheduler noop registered
[  184.045078] io scheduler anticipatory registered
[  184.045080] io scheduler deadline registered
[  184.045098] io scheduler cfq registered (default)
[  184.045119] Activating ISA DMA hang workarounds.
[  184.045161] Boot video device is 0000:01:05.0
[  184.045369] isapnp: Scanning for PnP cards...
[  184.398966] isapnp: No Plug & Play device found
[  184.441063] Real Time Clock Driver v1.12ac
[  184.441213] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[  184.441642] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[  184.442642] PCI: Enabling device 0000:00:08.0 (0000 -> 0003)
[  184.442906] ACPI: PCI Interrupt Link [LNK6] enabled at IRQ 10
[  184.442910] PCI: setting IRQ 10 as level-triggered
[  184.442914] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNK6] -> GSI 10 (level, low) -> IRQ 10
[  184.445226] 0000:00:08.0: ttyS0 at I/O 0x1428 (irq = 10) is a 8250
[  184.446472] 0000:00:08.0: ttyS2 at I/O 0x1440 (irq = 10) is a 8250
[  184.447265] 0000:00:08.0: ttyS3 at I/O 0x1450 (irq = 10) is a 8250
[  184.447484] Couldn't register serial port 0000:00:08.0: -28
[  184.448169] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[  184.448469] input: Macintosh mouse button emulation as /class/input/input0
[  184.448588] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[  184.454250] serio: i8042 KBD port at 0x60,0x64 irq 1
[  184.454260] serio: i8042 AUX port at 0x60,0x64 irq 12
[  184.454542] mice: PS/2 mouse device common for all mice
[  184.454692] EISA: Probing bus 0 at eisa.0
[  184.454707] Cannot allocate resource for EISA slot 1
[  184.454710] Cannot allocate resource for EISA slot 2
[  184.454734] Cannot allocate resource for EISA slot 8
[  184.454736] EISA: Detected 0 cards.
[  184.454884] TCP cubic registered
[  184.454904] NET: Registered protocol family 1
[  184.454937] Using IPI No-Shortcut mode
[  184.455175]   Magic number: 12:812:52
[  184.456025] Freeing unused kernel memory: 364k freed
[  184.504227] input: AT Translated Set 2 keyboard as /class/input/input1
[  185.675977] AppArmor: AppArmor initialized<5>audit(1202000631.760:2):  type=1505 info="AppArmor initialized" pid=1142
[  185.701772] fuse init (API version 7.8)
[  185.907730] Failure registering capabilities with primary security module.
[  186.017281] ACPI: CPU0 (power states: C1[C1] C2[C2])
[  186.317689] ACPI: Thermal Zone [THRM] (41 C)
[  189.127104] usbcore: registered new interface driver usbfs
[  189.127144] usbcore: registered new interface driver hub
[  189.127171] usbcore: registered new device driver usb
[  189.128275] USB Universal Host Controller Interface driver v3.0
[  189.128644] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 10
[  189.128648] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNK2] -> GSI 10 (level, low) -> IRQ 10
[  189.128664] uhci_hcd 0000:00:0b.0: UHCI Host Controller
[  189.128990] uhci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[  189.129022] uhci_hcd 0000:00:0b.0: irq 10, io base 0x00002000
[  189.129188] usb usb1: configuration #1 chosen from 1 choice
[  189.129224] hub 1-0:1.0: USB hub found
[  189.129233] hub 1-0:1.0: 2 ports detected
[  189.220724] SCSI subsystem initialized
[  189.227013] libata version 2.21 loaded.
[  189.230747] ACPI: PCI Interrupt Link [LNK3] enabled at IRQ 10
[  189.230753] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LNK3] -> GSI 10 (level, low) -> IRQ 10
[  189.230769] uhci_hcd 0000:00:0b.1: UHCI Host Controller
[  189.230805] uhci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[  189.230832] uhci_hcd 0000:00:0b.1: irq 10, io base 0x00002020
[  189.230954] usb usb2: configuration #1 chosen from 1 choice
[  189.230983] hub 2-0:1.0: USB hub found
[  189.230993] hub 2-0:1.0: 2 ports detected
[  189.255046] natsemi dp8381x driver, version 2.1, Sept 11, 2006
[  189.255049]   originally by Donald Becker <becker@scyld.com>
[  189.255050]   2.4.x kernel port by Jeff Garzik, Tjeerd Mulder
[  189.342621] PCI: Enabling device 0000:00:0c.0 (0010 -> 0012)
[  189.342636] ACPI: PCI Interrupt 0000:00:0c.0[A] -> Link [LNK2] -> GSI 10 (level, low) -> IRQ 10
[  189.392572] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[10]  MMIO=[d0003800-d0003fff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[  189.398767] PCI: Enabling device 0000:00:0b.2 (0010 -> 0012)
[  189.398786] ACPI: PCI Interrupt 0000:00:0b.2[C] -> Link [LNK5] -> GSI 11 (level, low) -> IRQ 11
[  189.398807] ehci_hcd 0000:00:0b.2: EHCI Host Controller
[  189.398860] ehci_hcd 0000:00:0b.2: new USB bus registered, assigned bus number 3
[  189.398912] ehci_hcd 0000:00:0b.2: irq 11, io mem 0xd0003000
[  189.398919] ehci_hcd 0000:00:0b.2: USB 2.0 started, EHCI 0.95, driver 10 Dec 2004
[  189.399051] usb usb3: configuration #1 chosen from 1 choice
[  189.399089] hub 3-0:1.0: USB hub found
[  189.399099] hub 3-0:1.0: 4 ports detected
[  189.424328] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[  189.424338] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[  189.455771] Floppy drive(s): fd0 is 1.44M
[  189.489453] FDC 0 is a post-1991 82077
[  189.503430] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 10
[  189.503438] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LNK1] -> GSI 10 (level, low) -> IRQ 10
[  189.505232] natsemi eth0: NatSemi DP8381[56] at 0xd0008000 (0000:00:12.0), 00:0f:20:ca:67:cf, IRQ 10, port TP.
[  189.505626] ALI15X3: IDE controller at PCI slot 0000:00:10.0
[  189.505644] ACPI: Unable to derive IRQ for device 0000:00:10.0
[  189.505647] ACPI: PCI Interrupt 0000:00:10.0[A]: no GSI
[  189.505656] ALI15X3: chipset revision 196
[  189.505659] ALI15X3: not 100% native mode: will probe irqs later
[  189.505727]     ide0: BM-DMA at 0x2040-0x2047, BIOS settings: hda:DMA, hdb:pio
[  189.505746]     ide1: BM-DMA at 0x2048-0x204f, BIOS settings: hdc:DMA, hdd:pio
[  189.505760] Probing IDE interface ide0...
[    7.004000] Marking TSC unstable due to: possible TSC halt in C2.
[    7.008000] Time: acpi_pm clocksource has been installed.
[    7.180000] hda: TOSHIBA MK4025GAS, ATA DISK drive
[    7.852000] hda: selected mode 0x45
[    7.852000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    7.864000] usb 1-2: new full speed USB device using uhci_hcd and address 2
[    7.900000] Probing IDE interface ide1...
[    8.048000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000f2071a0c9e850]
[    8.060000] usb 1-2: configuration #1 chosen from 1 choice
[    8.636000] hdc: HL-DT-ST DVDRAM GSA-T20N, ATAPI CD/DVD-ROM drive
[    8.972000] hdc: selected mode 0x42
[    8.972000] ide1 at 0x170-0x177,0x376 on irq 15
[    8.988000] hda: max request size: 128KiB
[    8.988000] hda: 78140160 sectors (40007 MB), CHS=65535/16/63, UDMA(100)
[    8.988000] hda: cache flushes supported
[    8.988000]  hda: hda1 hda2 < hda5 >
[    9.084000] hdc: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[    9.084000] Uniform CD-ROM driver Revision: 3.20
[    9.592000] Attempting manual resume
[    9.592000] swsusp: Resume From Partition 3:5
[    9.592000] PM: Checking swsusp image.
[    9.616000] PM: Resume from disk failed.
[    9.684000] kjournald starting.  Commit interval 5 seconds
[    9.684000] EXT3-fs: mounted filesystem with ordered data mode.
[   20.688000] Linux agpgart interface v0.102 (c) Dave Jones
[   20.844000] agpgart: Detected Ati IGP345M chipset
[   20.852000] agpgart: AGP aperture is 64M @ 0xd4000000
[   20.864000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   20.888000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   20.944000] Yenta: CardBus bridge found at 0000:00:0a.0 [0000:0000]
[   20.944000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   20.944000] Yenta: Routing CardBus interrupts to PCI
[   20.944000] Yenta TI: socket 0000:00:0a.0, mfunc 0x01111112, devctl 0x64
[   21.176000] Yenta: ISA IRQ mask 0x00b8, PCI irq 11
[   21.176000] Socket status: 30000006
[   21.532000] input: PC Speaker as /class/input/input2
[   21.616000] parport_pc 00:09: reported by Plug and Play ACPI
[   21.616000] parport0: PC-style at 0x378 (0x778), irq 7, dma 0 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   22.036000] PCI: Enabling device 0000:00:06.0 (0005 -> 0007)
[   22.036000] ACPI: PCI Interrupt Link [LNK7] enabled at IRQ 5
[   22.036000] PCI: setting IRQ 5 as level-triggered
[   22.036000] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [LNK7] -> GSI 5 (level, low) -> IRQ 5
[   22.100000] cs: IO port probe 0x100-0x3af: excluding 0x200-0x207 0x220-0x22f 0x330-0x337 0x388-0x38f
[   22.104000] cs: IO port probe 0x3e0-0x4ff: clean.
[   22.104000] cs: IO port probe 0x820-0x8ff: clean.
[   22.104000] cs: IO port probe 0xc00-0xcf7: clean.
[   22.108000] cs: IO port probe 0xa00-0xaff: clean.
[   22.244000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x236eb3, caps: 0x904713/0x10008
[   22.276000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   24.736000] AC'97 1 does not respond - RESET
[   24.752000] AC'97 1 access is not valid [0xffffffff], removing mixer.
[   24.752000] ali mixer 1 creating error.
[   25.364000] lp0: using parport0 (interrupt-driven).
[   25.456000] Adding 554200k swap on /dev/hda5.  Priority:-1 extents:1 across:554200k
[   25.752000] EXT3 FS on hda1, internal journal
[   27.308000] ACPI: AC Adapter [ACAD] (on-line)
[   27.388000] ACPI: Battery Slot [BAT1] (battery present)
[   27.436000] input: Power Button (FF) as /class/input/input4
[   27.444000] ACPI: Power Button (FF) [PWRF]
[   27.480000] input: Power Button (CM) as /class/input/input5
[   27.484000] ACPI: Power Button (CM) [PWRB]
[   27.520000] input: Lid Switch as /class/input/input6
[   27.528000] ACPI: Lid Switch [LID]
[   27.588000] No dock devices found.
[   27.628000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   29.272000] ppdev: user-space parallel port driver
[   29.496000] eth0: DSPCFG accepted after 0 usec.
[   29.496000] eth0: link up.
[   29.496000] eth0: Setting full-duplex based on negotiated link capability.
[   29.664000] audit(1202000659.326:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4560 profile="/usr/sbin/cupsd"
[   29.708000] apm: BIOS not found.
[   30.080000] Failure registering capabilities with primary security module.
[   31.784000] Clocksource tsc unstable (delta = -64122076 ns)
[   32.500000] [drm] Initialized drm 1.1.0 20060810
[   32.516000] ACPI: PCI Interrupt Link [LNK0] enabled at IRQ 10
[   32.516000] ACPI: PCI Interrupt 0000:01:05.0[A] -> Link [LNK0] -> GSI 10 (level, low) -> IRQ 10
[   32.520000] [drm] Initialized radeon 1.27.0 20060524 on minor 0
[   34.024000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   34.024000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   34.024000] agpgart: Putting AGP V2 device at 0000:01:05.0 into 4x mode
[   34.700000] NET: Registered protocol family 17
[   35.640000] [drm] Setting GART location based on new memory map
[   35.640000] [drm] writeback test succeeded in 1 usecs
[   36.416000] NET: Registered protocol family 10
[   36.416000] lo: Disabled Privacy Extensions
[   46.792000] eth0: no IPv6 routers present
[ 8332.952000] usb 1-2: USB disconnect, address 2
[ 8340.396000] usb 1-2: new full speed USB device using uhci_hcd and address 3
[ 8340.592000] usb 1-2: configuration #1 chosen from 1 choice
angel@angel-laptop:~$ tail


I hope I executed the commands correctly. I am a total newby

---

### Post by spiderbatdad on 2008-02-02
```
[ 8332.952000] usb 1-2: USB disconnect, address 2
[ 8340.396000] usb 1-2: new full speed USB device using uhci_hcd and address 3
[ 8340.592000] usb 1-2: configuration #1 chosen from 1 choice
```

so it knows you plugged something in...it does not seem to know its a cam. You might check synaptic to ensure you have libusb installed...if you use the search tool it will be easier to find it. Beyond that I'm not sure...and I'm tired. ;)  The only thing I can think of after verifying you have libusb is```
modprobe -v ehci_hcd
``` not uhci, but echi_hcd as listed by lsmod,  but I believe we already saw that module mounted.  Have you tried installing camorama in add/remove to see if you can use the cam that way?

---

### Post by angelosapo on 2008-02-02
Allright.

Go to bed! Im guessing its quite late where you are and its reaaaaally early where I am.(Greece)I will try the commands and we will see. 

Thank you so much.

You rock

---

### Post by spiderbatdad on 2008-02-02
[QUOTE=spiderbatdad;4258336]```
[ 8332.952000] usb 1-2: USB disconnect, address 2
[ 8340.396000] usb 1-2: new full speed USB device using uhci_hcd and address 3
[ 8340.592000] usb 1-2: configuration #1 chosen from 1 choice
```

just so you know...those aren't commands...thats from your dmesg.

---

### Post by angelosapo on 2008-02-02
When trying to run camorama an error message appeared on the screen saying 

Could not connect to video device (dev/video/0) Please check connection.

libusb is installed. 

Anyway, many thanx spiderbatdad. You:guitar:

And thank u2 Shazaam.

---

### Post by angelosapo on 2008-02-02
When trying to run camorama an error message appeared on the screen saying

Could not connect to video device (dev/video/0) Please check connection.

I checked libusb. It is indeed installed.

Anyway, many thanx spiderbatdad. You :guitar:

And thank u2 Shazaam.
__________________

---

### Post by angelosapo on 2008-02-02
When trying to run camorama an error message appeared on the screen saying

Could not connect to video device (dev/video/0) Please check connection.

libusb is installed.

Anyway, many thanx spiderbatdad. You :guitar:

And thank u2 Shazaam.


I hope i got it right this time.........

---

