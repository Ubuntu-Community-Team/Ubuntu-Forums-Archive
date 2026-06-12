---
title: "help a wired 3com dhcp won't respond"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by DarinB on 2007-10-13
I have posted many times no one answers,
here is my problem i have a wired connection from my modem to a hub **_using the exact same Ethernet wires_**
i have a main box running feisty goes on line no problem 
i have a second wire from the hub i can fire up a laptop running ubuntu goes on line no problem
and a 2nd old lap top running m$ it goes online no problem
i got an old p3 512Mb ram machine with a 3com pci card with a clean install of feisty. it also went online as a windows 2k box.
using the exact same wires and it doesn't get an answer from the dhcp server 
i tried using the wires i have that work on other machines and no dhcp response on the p3 machine i even tried going straight in to the broadband modem it will work on all the other machines. then i tried and install of the last beta of gutsy same thing. i reinstalled m$ xp it worked reinstalled Gutsy no go
then i lspci it shows the 3com card and did the cli stuff from a post and turned off the network made sure it was eth0 then restart no go.
what is going on and how do i get help?? 
where do i post for a response???
thanks 
i am glad my main box wasn't this hard that is why i gave up with red hat years ago. 
i just put the other computer under the desk but i really want to get it to work now it is a matter of accomplishment.
what do ya think????
D

---

### Post by louieb on 2007-10-13
> **DarinB said:**
> ... have a wired connection from my modem to a hub **_...._** t shows the 3com card ...D

[COLOR=Red]**hub**[/COLOR] hum  Don't think a hub is going to work. You sure its not a router? 
You need something to act as a DHCP server. On most home networks that something is a router.  

Gutsy has a problem connecting to the internet when you reboot it. You need to run [COLOR=Blue]**sudo dhclient**[/COLOR] to get an IP address assigned. They'll probably  have that one fixed before its released.

---

### Post by DarinB on 2007-10-14
i understand that it is probably a hybrid between a router and a dummy hub, now a days these cheap devices are all hybrids and this one is about 4 or 5 years old. It does work on all of my other machines and even connecting direct to the broadband modem doesn't work but it does on all of my  other computers.
I do not think it is the hub or the Ethernet cable i troubleshot both. the dhcp client sounds like a good thing to try. when i get back to my computer i will try it. i am aways right now.
thanks i'll be back. i couldn't get it to work with feisty either or a live cd of pc linux os, but that may be the live cd they tend to have problems with connectivity.
D

---

### Post by louieb on 2007-10-14
One more thought. If [COLOR=Blue]ifconfig [/COLOR]shows  the card and  [COLOR=Blue]dhclient[/COLOR] doesn't get an IP lease.  I'd suspect the card. Try re-seating it or put another card in. 
I've found that Linux can work with just about any old wired network card out of the box.

---

### Post by DarinB on 2007-10-14
oh like ipconfig in m$ it does come up and is eth0 in lspci and on the hard ware list.
i did re-seat it.
no go when i get home i will ifconfig it 
but why would it work with m$ and not ubuntu???
if it were the card it would just not work at all.
hum it is confusing i am glad my main box worked so easily. 
would have never stuck with it other wise
thanks i get back to you when i get to my computer.

---

### Post by louieb on 2007-10-14
Yea ifconfig is similar to ipconfig. same type of info is displayed. 
No good reason for your 3-com card not to work. I got a couple of them . 
Had a NetGear card go bad the other day. Replace it with a 10 year old 3-com card. Rebooted and Linux picked it right up. Even windows said new hardware, loaded the driver without having to put the install CD in.

---

### Post by DarinB on 2007-10-15
Here are some answers i have no idea???

darin@darin-desktop:~$ lspci -nn 
00:00.0 Host bridge [0600]: Intel Corporation 82810E DC-133 (GMCH) Graphics Memory Controller Hub [8086:7124] (rev 03) 
00:01.0 VGA compatible controller [0300]: Intel Corporation 82810E DC-133 (CGC) Chipset Graphics Controller [8086:7125] (rev 03) 
00:1e.0 PCI bridge [0604]: Intel Corporation 82801AA PCI Bridge [8086:2418] (rev 02) 
00:1f.0 ISA bridge [0601]: Intel Corporation 82801AA ISA Bridge (LPC) [8086:2410] (rev 02) 
00:1f.1 IDE interface [0101]: Intel Corporation 82801AA IDE Controller [8086:2411] (rev 02) 
00:1f.2 USB Controller [0c03]: Intel Corporation 82801AA USB Controller [8086:2412] (rev 02) 
00:1f.3 SMBus [0c05]: Intel Corporation 82801AA SMBus Controller [8086:2413] (rev 02) 
01:09.0 Multimedia audio controller [0401]: Ensoniq ES1371 [AudioPCI-97] [1274:1371] (rev 09) 
01:0a.0 Ethernet controller [0200]: 3Com Corporation 3c905B 100BaseTX [Cyclone] [10b7:9055] (rev 30) 
01:0b.0 Communication controller [0780]: Conexant HCF 56k Data/Fax Modem [14f1:1033] (rev 08) 
darin@darin-desktop:~$ sudo lshw -C network 
  *-network               
       description: Ethernet interface 
       product: 3c905B 100BaseTX [Cyclone] 
       vendor: 3Com Corporation 
       physical id: a 
       bus info: pci@0000:01:0a.0 
       logical name: eth0 
       version: 30 
       serial: 00:10:5a:1e:62:46 
       size: 100MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full latency=64 link=yes maxlatency=10 mingnt=10 module=3c59x multicast=yes port=MII speed=100MB/s 
darin@darin-desktop:~$ dmesg 
[    0.000000] Linux version 2.6.22-12-generic (buildd@vernadsky) (gcc version 4.1.3 20070831 (prerelease) (Ubuntu 4.1.2-16ubuntu1)) #1 SMP Sun Sep 23 18:11:30 GMT 2007 (Ubuntu 2.6.22-12.39-generic) 
[    0.000000] BIOS-provided physical RAM map: 
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable) 
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved) 
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved) 
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fec0000 (usable) 
[    0.000000]  BIOS-e820: 000000001fec0000 - 000000001fef8000 (ACPI data) 
[    0.000000]  BIOS-e820: 000000001fef8000 - 000000001ff00000 (ACPI NVS) 
[    0.000000]  BIOS-e820: 00000000ffb80000 - 00000000ffc00000 (reserved) 
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved) 
[    0.000000] 0MB HIGHMEM available. 
[    0.000000] 510MB LOWMEM available. 
[    0.000000] Entering add_active_range(0, 0, 130752) 0 entries of 256 used 
[    0.000000] Zone PFN ranges: 
[    0.000000]   DMA             0 ->     4096 
[    0.000000]   Normal       4096 ->   130752 
[    0.000000]   HighMem    130752 ->   130752 
[    0.000000] early_node_map[1] active PFN ranges 
[    0.000000]     0:        0 ->   130752 
[    0.000000] On node 0 totalpages: 130752 
[    0.000000]   DMA zone: 32 pages used for memmap 
[    0.000000]   DMA zone: 0 pages reserved 
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0 
[    0.000000]   Normal zone: 989 pages used for memmap 
[    0.000000]   Normal zone: 125667 pages, LIFO batch:31 
[    0.000000]   HighMem zone: 0 pages used for memmap 
[    0.000000] DMI 2.3 present. 
[    0.000000] ACPI: RSDP 000FF980, 0014 (r0 AMI   ) 
[    0.000000] ACPI: RSDT 1FEF0000, 0028 (r1 DELL   MUMMY    20000615 MSFT       97) 
[    0.000000] ACPI: FACP 1FEF1000, 0074 (r1 DELL   MUMMY    20000615 MSFT       97) 
[    0.000000] ACPI: DSDT 1FEE0000, 28B5 (r1 DELL   DIM_L          12 MSFT  100000B) 
[    0.000000] ACPI: FACS 1FEF8000, 0040 
[    0.000000] ACPI: PM-Timer IO Port: 0x408 
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1ff00000:dfc80000) 
[    0.000000] Built 1 zonelists.  Total pages: 129731 
[    0.000000] Kernel command line: root=UUID=4b76c17d-cb54-43fb-931b-d3773120eaac ro quiet splash 
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic" 
[    0.000000] mapped APIC to ffffd000 (0140d000) 
[    0.000000] Enabling fast FPU save and restore... done. 
[    0.000000] Enabling unmasked SIMD FPU exception support... done. 
[    0.000000] Initializing CPU#0 
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes) 
[    0.000000] Detected 664.548 MHz processor. 
[   30.651947] Console: colour VGA+ 80x25 
[   30.653030] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes) 
[   30.654465] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes) 
[   30.716592] Memory: 506764k/523008k available (2017k kernel code, 15716k reserved, 918k data, 364k init, 0k highmem) 
[   30.716625] virtual kernel memory layout: 
[   30.716629]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB) 
[   30.716633]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB) 
[   30.716638]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB) 
[   30.716642]     lowmem  : 0xc0000000 - 0xdfec0000   ( 510 MB) 
[   30.716647]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB) 
[   30.716651]       .data : 0xc02f8456 - 0xc03ddea4   ( 918 kB) 
[   30.716655]       .text : 0xc0100000 - 0xc02f8456   (2017 kB) 
[   30.716666] Checking if this processor honours the WP bit even in supervisor mode... Ok. 
[   30.716777] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1 
[   30.796768] Calibrating delay using timer specific routine.. 1330.36 BogoMIPS (lpj=2660728) 
[   30.796839] Security Framework v1.0.0 initialized 
[   30.796862] SELinux:  Disabled at boot. 
[   30.796905] Mount-cache hash table entries: 512 
[   30.797248] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000 
[   30.797282] CPU: L1 I cache: 16K, L1 D cache: 16K 
[   30.797291] CPU: L2 cache: 256K 
[   30.797300] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000 
[   30.797328] Compat vDSO mapped to ffffe000. 
[   30.797371] Checking 'hlt' instruction... OK. 
[   30.813018] SMP alternatives: switching to UP code 
[   30.813456] Freeing SMP alternatives: 11k freed 
[   30.814264] Early unpacking initramfs... done 
[   31.835503] ACPI: Core revision 20070126 
[   31.835765] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found. 
[   31.839623] ACPI: setting ELCR to 0200 (from 0e08) 
[   31.839967] CPU0: Intel Pentium III (Coppermine) stepping 03 
[   31.839985] SMP motherboard not detected. 
[   31.839992] Local APIC not detected. Using dummy APIC emulation. 
[   31.840116] Brought up 1 CPUs 
[   31.840564] Booting paravirtualized kernel on bare hardware 
[   31.840713] Time: 16:16:19  Date: 09/15/107 
[   31.840801] NET: Registered protocol family 16 
[   31.841122] EISA bus registered 
[   31.841149] ACPI: bus type pci registered 
[   31.841973] PCI: PCI BIOS revision 2.10 entry at 0xfda95, last bus=1 
[   31.841981] PCI: Using configuration type 1 
[   31.841987] Setting up standard PCI resources 
[   31.846658] ACPI: EC: Look up EC in DSDT 
[   31.856609] ACPI: Interpreter enabled 
[   31.856620] ACPI: (supports S0 S1 S4 S5) 
[   31.856670] ACPI: Using PIC for interrupt routing 
[   31.867281] ACPI: PCI Root Bridge [PCI0] (0000:00) 
[   31.867336] PCI: Probing PCI hardware (bus 00) 
[   31.867683] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO 
[   31.867693] PCI quirk: region 0500-053f claimed by ICH4 GPIO 
[   31.868208] PCI: Transparent bridge - 0000:00:1e.0 
[   31.868252] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT] 
[   31.868543] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT] 
[   31.871495] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15) 
[   31.871766] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15) 
[   31.872032] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 12 14 15) 
[   31.872418] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *9 10 11 12 14 15) 
[   31.872747] ACPI: Power Resource [URP1] (off) 
[   31.872831] ACPI: Power Resource [URP2] (off) 
[   31.872915] ACPI: Power Resource [FDDP] (off) 
[   31.872998] ACPI: Power Resource [LPTP] (off) 
[   31.873029] Linux Plug and Play Support v0.97 (c) Adam Belay 
[   31.873066] pnp: PnP ACPI init 
[   31.873113] ACPI: bus type pnp registered 
[   31.880094] pnp: PnP ACPI: found 12 devices 
[   31.880103] ACPI: ACPI bus type pnp unregistered 
[   31.880118] PnPBIOS: Disabled by ACPI PNP 
[   31.880368] PCI: Using ACPI for IRQ routing 
[   31.880379] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report 
[   31.882684] NET: Registered protocol family 8 
[   31.882691] NET: Registered protocol family 20 
[   31.882906] pnp: 00:0b: iomem range 0x0-0x9ffff could not be reserved 
[   31.882917] pnp: 00:0b: iomem range 0xe0000-0xfffff could not be reserved 
[   31.882927] pnp: 00:0b: iomem range 0x100000-0x1fefffff could not be reserved 
[   31.882936] pnp: 00:0b: iomem range 0x0-0x0 could not be reserved 
[   31.884140] Time: tsc clocksource has been installed. 
[   31.913849] PCI: Bridge: 0000:00:1e.0 
[   31.913857]   IO window: d000-dfff 
[   31.913870]   MEM window: ff800000-ff8fffff 
[   31.913880]   PREFETCH window: f6a00000-f6afffff 
[   31.913905] PCI: Setting latency timer of device 0000:00:1e.0 to 64 
[   31.913946] NET: Registered protocol family 2 
[   31.952246] IP route cache hash table entries: 4096 (order: 2, 16384 bytes) 
[   31.952410] TCP established hash table entries: 16384 (order: 5, 196608 bytes) 
[   31.953034] TCP bind hash table entries: 16384 (order: 5, 131072 bytes) 
[   31.953615] TCP: Hash tables configured (established 16384 bind 16384) 
[   31.953626] TCP reno registered 
[   31.964608] checking if image is initramfs...<6>Switched to high resolution mode on CPU 0 
[   32.835773]  it is 
[   33.900055] Freeing initrd memory: 7338k freed 
[   33.901139] audit: initializing netlink socket (disabled) 
[   33.901186] audit(1192464981.172:1): initialized 
[   33.908273] VFS: Disk quotas dquot_6.5.1 
[   33.908488] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes) 
[   33.908863] io scheduler noop registered 
[   33.908872] io scheduler anticipatory registered 
[   33.908879] io scheduler deadline registered 
[   33.908952] io scheduler cfq registered (default) 
[   33.908993] Boot video device is 0000:00:01.0 
[   33.909604] isapnp: Scanning for PnP cards... 
[   34.263872] isapnp: No Plug & Play device found 
[   34.355458] Real Time Clock Driver v1.12ac 
[   34.355698] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled 
[   34.355852] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A 
[   34.357985] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A 
[   34.360396] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize 
[   34.361057] input: Macintosh mouse button emulation as /class/input/input0 
[   34.361322] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12 
[   34.364541] serio: i8042 KBD port at 0x60,0x64 irq 1 
[   34.364556] serio: i8042 AUX port at 0x60,0x64 irq 12 
[   34.365090] mice: PS/2 mouse device common for all mice 
[   34.365431] EISA: Probing bus 0 at eisa.0 
[   34.365493] EISA: Detected 0 cards. 
[   34.365786] TCP cubic registered 
[   34.365835] NET: Registered protocol family 1 
[   34.365913] Using IPI No-Shortcut mode 
[   34.366322]   Magic number: 11:567:287 
[   34.366374]   hash matches device ttyz1 
[   34.366600]   hash matches device tty20 
[   34.366639]   hash matches device PNP0400:00 
[   34.368076] Freeing unused kernel memory: 364k freed 
[   34.394669] input: AT Translated Set 2 keyboard as /class/input/input1 
[   36.045548] AppArmor: AppArmor initialized<5>audit(1192464983.172:2):  type=1505 info="AppArmor initialized" pid=1163 
[   36.067798] fuse init (API version 7.8) 
[   36.084827] Failure registering capabilities with primary security module. 
[   38.027063] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 3 
[   38.027079] PCI: setting IRQ 3 as level-triggered 
[   38.027088] ACPI: PCI Interrupt 0000:01:0a.0[A] -> Link [LNKC] -> GSI 3 (level, low) -> IRQ 3 
[   38.027110] 3c59x: Donald Becker and others. 
[   38.027124] 0000:01:0a.0: 3Com PCI 3c905B Cyclone 100baseTx at e0814c00. 
[   38.160331] SCSI subsystem initialized 
[   38.189739] libata version 2.21 loaded. 
[   38.198220] ata_piix 0000:00:1f.1: version 2.11 
[   38.198366] PCI: Setting latency timer of device 0000:00:1f.1 to 64 
[   38.198696] scsi0 : ata_piix 
[   38.198826] scsi1 : ata_piix 
[   38.199156] ata1: PATA max UDMA/66 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14 
[   38.199169] ata2: PATA max UDMA/66 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15 
[   38.235122] usbcore: registered new interface driver usbfs 
[   38.235198] usbcore: registered new interface driver hub 
[   38.235264] usbcore: registered new device driver usb 
[   38.239856] USB Universal Host Controller Interface driver v3.0 
[   38.361095] ata1.00: Host Protected Area detected: 
[   38.361101]  current size: 78125000 sectors 
[   38.361105]  native size: 78125040 sectors 
[   38.363171] ata1.00: native size increased to 78125040 sectors 
[   38.363182] ata1.00: ATA-5: WDC WD400BB-75DEA0, 05.03E05, max UDMA/100 
[   38.363192] ata1.00: 78125040 sectors, multi 16: LBA 
[   38.377242] ata1.00: configured for UDMA/66 
[   38.512332] Floppy drive(s): fd0 is 1.44M 
[   38.601238] FDC 0 is a post-1991 82077 
[   38.696061] ata2.00: ATAPI: LITE-ON LTR-40125S, ZS03, max UDMA/33 
[   38.867887] ata2.00: configured for UDMA/33 
[   38.868253] scsi 0:0:0:0: Direct-Access     ATA      WDC WD400BB-75DE 05.0 PQ: 0 ANSI: 5 
[   38.870464] scsi 1:0:0:0: CD-ROM            LITE-ON  LTR-40125S       ZS03 PQ: 0 ANSI: 5 
[   38.881617] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 9 
[   38.881632] PCI: setting IRQ 9 as level-triggered 
[   38.881639] ACPI: PCI Interrupt 0000:00:1f.2[D] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9 
[   38.881668] PCI: Setting latency timer of device 0000:00:1f.2 to 64 
[   38.881679] uhci_hcd 0000:00:1f.2: UHCI Host Controller 
[   38.882006] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1 
[   38.882053] uhci_hcd 0000:00:1f.2: irq 9, io base 0x0000ef80 
[   38.882586] usb usb1: configuration #1 chosen from 1 choice 
[   38.882686] hub 1-0:1.0: USB hub found 
[   38.882710] hub 1-0:1.0: 2 ports detected 
[   38.924955] sd 0:0:0:0: [sda] 78125040 512-byte hardware sectors (40000 MB) 
[   38.925002] sd 0:0:0:0: [sda] Write Protect is off 
[   38.925011] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00 
[   38.925063] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA 
[   38.925251] sd 0:0:0:0: [sda] 78125040 512-byte hardware sectors (40000 MB) 
[   38.925282] sd 0:0:0:0: [sda] Write Protect is off 
[   38.925290] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00 
[   38.925339] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA 
[   38.925358]  sda: sda1 sda2 < sda5 > 
[   39.024366] sd 0:0:0:0: [sda] Attached SCSI disk 
[   39.041304] sd 0:0:0:0: Attached scsi generic sg0 type 0 
[   39.041764] scsi 1:0:0:0: Attached scsi generic sg1 type 5 
[   39.130705] sr0: scsi3-mmc drive: 83x/48x writer cd/rw xa/form2 cdda tray 
[   39.130724] Uniform CD-ROM driver Revision: 3.20 
[   39.131548] sr 1:0:0:0: Attached scsi CD-ROM sr0 
[   39.454744] Attempting manual resume 
[   39.454756] swsusp: Resume From Partition 8:5 
[   39.454762] PM: Checking swsusp image. 
[   39.455130] PM: Resume from disk failed. 
[   39.551417] kjournald starting.  Commit interval 5 seconds 
[   39.551458] EXT3-fs: mounted filesystem with ordered data mode. 
[   53.249477] Linux agpgart interface v0.102 (c) Dave Jones 
[   53.684371] agpgart: Detected an Intel i810 Chipset. 
[   53.690213] agpgart: detected 4MB dedicated video ram. 
[   53.696668] agpgart: AGP aperture is 64M @ 0xf8000000 
[   53.724759] pci_hotplug: PCI Hot Plug PCI Core version: 0.5 
[   53.760074] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4 
[   53.858821] i810_smbus 0000:00:01.0: i810/i815 i2c device found. 
[   53.868602] intel_rng: Firmware space is locked read-only. <4>intel_rng: If you can't or 
[   53.868610]  don't want to <4>intel_rng: disable this in firmware setup, and <4>intel_rng: if 
[   53.868616]  you are certain that your <4>intel_rng: system has a functional 
[   53.868621]  RNG, try<4>intel_rng: using the 'no_fwh_detect' option. 
[   54.296158] iTCO_vendor_support: vendor-support=0 
[   54.300333] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007) 
[   54.300516] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware 
[   54.300533] iTCO_wdt: No card detected 
[   54.473051] input: PC Speaker as /class/input/input2 
[   56.226089] input: ImPS/2 Logitech Wheel Mouse as /class/input/input3 
[   56.230340] parport_pc 00:09: reported by Plug and Play ACPI 
[   56.230387] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP] 
[   57.537878] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10 
[   57.537894] PCI: setting IRQ 10 as level-triggered 
[   57.537902] ACPI: PCI Interrupt 0000:01:09.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10 
[   59.751688] lp0: using parport0 (interrupt-driven). 
[   59.880231] Adding 1502036k swap on /dev/sda5.  Priority:-1 extents:1 across:1502036k 
[   60.349374] EXT3 FS on sda1, internal journal 
[   62.850327] No dock devices found. 
[   63.248124] input: Power Button (FF) as /class/input/input4 
[   63.248842] ACPI: Power Button (FF) [PWRF] 
[   66.945092] eth0:  setting half-duplex. 
[   66.953617] ppdev: user-space parallel port driver 
[   67.723726] audit(1192465014.895:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4374 profile="/usr/sbin/cupsd" 
[   67.850264] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac) 
[   67.850282] apm: overridden by ACPI. 
[   68.362089] Failure registering capabilities with primary security module. 
[   68.782558] Bluetooth: Core ver 2.11 
[   68.782915] NET: Registered protocol family 31 
[   68.782925] Bluetooth: HCI device and connection manager initialized 
[   68.782936] Bluetooth: HCI socket layer initialized 
[   68.819957] Bluetooth: L2CAP ver 2.8 
[   68.819973] Bluetooth: L2CAP socket layer initialized 
[   68.850447] Bluetooth: RFCOMM socket layer initialized 
[   68.850720] Bluetooth: RFCOMM TTY layer initialized 
[   68.850729] Bluetooth: RFCOMM ver 1.8 
[  104.918004] eth0:  setting full-duplex. 
[  107.207521] NET: Registered protocol family 17 
[  151.474657] NET: Registered protocol family 10 
[  151.475287] lo: Disabled Privacy Extensions 
[  162.260749] eth0: no IPv6 routers present 
[  990.243330] usb 1-2: new full speed USB device using uhci_hcd and address 2 
[  990.406449] usb 1-2: configuration #1 chosen from 1 choice 
[  990.653339] usbcore: registered new interface driver libusual 
[  990.731054] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2 
[  990.731078] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx 
[  990.827641] Initializing USB Mass Storage driver... 
[  990.828922] scsi2 : SCSI emulation for USB Mass Storage devices 
[  990.829123] usb-storage: device found at 2 
[  990.829130] usb-storage: waiting for device to settle before scanning 
[  990.829179] usbcore: registered new interface driver usb-storage 
[  990.829191] USB Mass Storage support registered. 
[  995.824915] usb-storage: device scan complete 
[  995.827880] scsi 2:0:0:0: Direct-Access     Generic  USB Flash Disk   0.00 PQ: 0 ANSI: 2 
[  995.834819] sd 2:0:0:0: [sdb] 2015232 512-byte hardware sectors (1032 MB) 
[  995.837798] sd 2:0:0:0: [sdb] Write Protect is off 
[  995.837812] sd 2:0:0:0: [sdb] Mode Sense: 00 00 00 00 
[  995.837820] sd 2:0:0:0: [sdb] Assuming drive cache: write through 
[  995.849790] sd 2:0:0:0: [sdb] 2015232 512-byte hardware sectors (1032 MB) 
[  995.852795] sd 2:0:0:0: [sdb] Write Protect is off 
[  995.852809] sd 2:0:0:0: [sdb] Mode Sense: 00 00 00 00 
[  995.852817] sd 2:0:0:0: [sdb] Assuming drive cache: write through 
[  995.852829]  sdb: sdb1 
[  996.001989] sd 2:0:0:0: [sdb] Attached SCSI removable disk 
[  996.002133] sd 2:0:0:0: Attached scsi generic sg2 type 0 
darin@darin-desktop:~$

---

### Post by DarinB on 2007-10-15
here is the other info i was asked for

darin@darin-desktop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:10:5A:1E:62:46  
          inet6 addr: fe80::210:5aff:fe1e:6246/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:54258 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:3280684 (3.1 MB)  TX bytes:14946 (14.5 KB) 
          Interrupt:3 Base address:0x4c00 

eth0:avah Link encap:Ethernet  HWaddr 00:10:5A:1E:62:46  
          inet addr:169.254.4.5  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          Interrupt:3 Base address:0x4c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:1868 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1868 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:148376 (144.8 KB)  TX bytes:148376 (144.8 KB) 

darin@darin-desktop:~$ sudo dhclient 
There is already a pid file /var/run/dhclient.pid with pid 5548 
killed old client process, removed PID file 
Internet Systems Consortium DHCP Client V3.0.5 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 

Listening on LPF/eth0/00:10:5a:1e:62:46 
Sending on   LPF/eth0/00:10:5a:1e:62:46 
Sending on   Socket/fallback 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11 
No DHCPOFFERS received. 
No working leases in persistent database - sleeping.

---

### Post by nickpaton on 2007-10-17
I would suggest just getting a new card - they're V cheap nowadays.

The other thing you might want to check is to see if you can reach your router via its IP address in your web browser.

I had a similar problem where everything appeared to work, could see the router settings etc, but it would not access the Internet.

Check that Network settings in Sys > Admin are 100% correct.

Then restart the network by 

```
sudo /etc/init.d/networking restart
```

It's a shot in the dark but worth trying


Good luck and let us know here how you're getting on.  Please try not to multipost!:)

---

### Post by DarinB on 2007-10-18
the dhcpdiscover is using subnet mask 255.255.255.255
but my subnetmask is 255.255.240.10
can i change what mask the dhcp discover goes to??

---

### Post by nickpaton on 2007-10-18
I've been reading through all your multithreads again, and because you are trying suggestions from different people in the various threads, it makes it very hard to give you any advice in one thread because of what someone else might have asked you to do in another.

Also, as the longer threads have progressed, you seem to have got into more of a mess, and it then makes it very difficult to help you.

So may I suggest that you start again from the beginning and reinstall with a clean distro.  

Before you do this, set up the modem router with basic simple settings - i.e. no static or reserved addresses etc, and make sure it's set to 'basic' DHCP.  You may even want to consider doing a factory reset of the modem router and set it up in Windows (I assume from some of your posts that Windows still works) with the basic settings to work on Windows.

Next, install Ubuntu with the PC network card connected to the modem router with the Ethernet cable you normally use.
It should then just detect the card and providing your router is set up correctly, simply access the Internet.

Then, when the basic setup works, start making any changes.
I run quite a complex set up here, however my modem router settings are still quite simple and I have no reason for setting static IP's on each PC.
I though need each PC to have the same IP addresses each time it's powered up.
To do this I use a method called address reservation which is carried out by the router - in my case an ordinary Netgear DG834G model.  I believe most popular modem routers can be set up to do this quite simply.

The way it then works is that when each PC is powered up, the router recognises it and gives it the correct 'reserved' IP address.  Thus each PC effectively has a static IP address without me having to do anything to the PC's whether they are Linux, Windows, Mac etc. A neat and simple little trick.

To find out more about address reservation [read this]("http://wejump.ifac.cnr.it/pages/pub/sw/drivers/network/Netgear%20MR814/Documentation/WebDoc/wwhelp/wwhimpl/common/html/wwhelp.htm?context=MR814v2&file=Advanced14.html").

I hope this helps a little; I know it's not the best news you want to hear but it's my best suggestion for you.

Good luck and let us know how you get on

Nick :)

---

### Post by DarinB on 2007-10-18
Thanks this is great info  i will get started on it over the weekend.
i did reinstall feisty from scratch before i did all the ifconfig and the dmesg stuff.
it is interesting that an ip is reserved automatically, i actually have m$ certifications and it seems i have had to throw out all that knowledge and start over re learning how things work.
unfortunately now my feisty laptop won't go on line either.
but my windows lap top will still go on line with the same wire.
i am wondering if the switch/hub is messed up but my main box still goes on line weather i am plug into one port or another or directly into the cable modem.
I think you are right i have a mess and need to start over and reinstall and connect directly to the cable modem.
then i may just get a lynksis router even though i prefer switch/hubs because they are much faster by nature and cheap.
thanks if you have any more ideas let me know i will get back after the weekend and i get it all reinstalled.
DarinB

---

### Post by nickpaton on 2007-10-19
Hi Darin

> **DarinB said:**
> 
it is interesting that an ip is reserved automatically, i actually have m$ certifications and it seems i have had to throw out all that knowledge and start over re learning how things work. 

When you use a modem router 'out-the-box' so to speak, no matter what OS, it will automatically assign IP addresses randomly, but within the range set by the router.
So if the IP of the router (typically for Netgear) is 192.168.0.1, then you will find that it has ports 192.168.0.2 to 254 potentially available.
When a PC of any flavour connects to it, the first one, lets call it PC A, an Ubuntu one, goes for 0.2, the next one PC B, an XP one, goes for  0.3 and so on.
However when you next power everything up, if you switch PC B (XP) on first, then it will be assigned 0.2, and PC A (Ubuntu) 0.3.
With address reservation, you can set PC A to always have 0.2 reserved for it, and PC B 0.3, and that Mac you have (!) 0.4 etc etc.
So you don't need to relearn anything, since the router doesn't care what type of PC is connected to it, since it's only seeing any PC's linked to it which conforms to the standard ethernet protocols.
With this in mind, you see quite a lot of questions here of people saying that I have brand X router and is it compatible with Ubuntu.  Short answer is that Ubuntu doesn't care so long as the network card drivers in Ubuntu are loaded and configured properly.
As in your case, the real question is whether my network card will work in Ubuntu.

Having said all that, I see that you have a cable modem to which you have connected a hub (see below for my thoughts on the hub side of things).
Not knowing too much about the cable modem, I don't think they are that configurable and you will be stuck with the modem automatically assigning addresses, and for most applications this will be fine.  
I only have to set up my router to reserve one address, and that's for the server connected to it because I need it to have a 'static' configuration, but before I had the server I tended to reserve addresses to the PC's here, just because I could do it!

> **DarinB said:**
> 
i am wondering if the switch/hub is messed up but my main box still goes on line weather i am plug into one port or another or directly into the cable modem.
I think you are right i have a mess and need to start over and reinstall and connect directly to the cable modem.
then i may just get a lynksis router even though i prefer switch/hubs because they are much faster by nature and cheap.
thanks if you have any more ideas let me know i will get back after the weekend and i get it all reinstalled.
DarinB 

Going back to basics for a second, a hub or switch is simply an expansion box which allows a number of PC's to be connected to a single Ethernet port, and does not need setting up to do this (I am using one myself in my server / Firewall / multiPC setup here).
However so as to get everything working correctly, I would suggest disconnecting the Ubuntu PC from the hub and plugging it straight into your cable modem (I assume it's got an LAN ethernet connection rather than a USB - sorry, asking a stupid question but worth just checking even so).
That way you remove any potential problems.
Regarding the ethernet cable you are using from the PC to the hub / modem, I assume it is a straight pin to pin one and not a cross over one?  You can sometimes check by looking closely at the individual tiny wires if you have the clear type of LAN plugs to see they all go to the same pins at each end.
  
Finally if you decide to go for a new router (shouldn't be necessary), you say you are on cable, so you will need a broadband router rather than an ADSL router.  See the explanation at the[ top of this page]("http://www.broadbandbuyer.co.uk/default_ShopGroup.asp?ShopGroupID=12").
I'm going to check out your network card to see if there's anything strange with it and will post back.

Cheers  Nick

---

### Post by nickpaton on 2007-10-19
> **DarinB said:**
> here is the other info i was asked for

darin@darin-desktop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:10:5A:1E:62:46  
          inet6 addr: fe80::210:5aff:fe1e:6246/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:54258 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:3280684 (3.1 MB)  TX bytes:14946 (14.5 KB) 
          Interrupt:3 Base address:0x4c00 

eth0:avah Link encap:Ethernet  HWaddr 00:10:5A:1E:62:46  
          inet addr:169.254.4.5  Bcast:169.254.255.255  **[SIZE="3"]Mask:255.255.0.0 [/SIZE]**
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          Interrupt:3 Base address:0x4c00 

Just rechecking some stuff.....

I would expect the network mask to be 255.255.255.0.

Right lets check your network settings.  System > Administration > Network.

Wired connection > properties > Roaming Mode disabled; Configuration Automatic DHCP; close.  Click on Wired connection to tick box to left; wait for it to do it's thing, and close.

reboot. 

Hopefully that's going to tidy up any wrong settings.

After you've done that can you post back ifconfig again or tell me if there are any differences.

If that doesn't work then I'm afraid it's a reinstall.  I can't find anything peculiar about your card, so should be OK

---

### Post by joeytwothumbs on 2007-10-20
I had a similar problem with 

No DHCPOFFERS received.
No working leases in persistent database - sleeping.

I installed dhcpcd and ran 

sudo dhcpcd eth0

in the terminal and was able to connect to the internet then.

---

### Post by DarinB on 2007-10-20
ok i did reinstall feisty with a clean install, and can't go on line when plugged directly in to the cable modem. it seems that my laptop that had feisty on it stopped working as well so i reinstalled a clean feisty on it.
as above. It is very strange how can a good install not work. i even tried new wires. But my main box and windows lap top still work fine and the other two an old p3 box and a Sony laptop don't so i went back to step one and plugged into the cable modem directly with the wire i was using from the switch to the modem. So it is not the wire. i thought it was the hub so i tried a different one a d link switch, (((in the process fried the old hub smoke and all))) Wrong power cable Oh well!!))) and again my main box works and my windows laptop works on the D link switch. and directly to the modem.  But not the Sony laptop or the old p3 box (both had clean reinstalls of fiesty and even installing XP  on the   Sony laptop will not let it get on line directly to the modem. I even added a second nic in the old P3 box and it also doesn't work. I am totally confused. why do two work and two not. is it possible to burn out nic adapters, and three of them. i would love to get the laptop going again. 
i even tried a clean install of gutsy on the Sony laptop but ended up with half the screen black i decided to not deal with that now and reinstalled a clean copy of feisty. 
i summary i have two computers with clean installs of feisty and when i click firefox it says server not found and it won't go online is does say connection enabled.
i am really lost. a wireless usb finds my neighbours wireless but i don't know their password. bummer!!
so now what???
another clean install buy a new nic????

---

