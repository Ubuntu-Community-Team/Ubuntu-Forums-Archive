---
title: "sound problem"
date: 2005-08-08
forum: Absolute Beginner Talk
---

### Post by LGP on 2005-08-08
i just got ubuntu installed on my computer and the sound quality was bad and everything sounded messed up.  I got that figured out and the poor quality is fixed but now it still isn't right.  when i am listening to music the singing is alot lower than the music and you can barly hear the singing. ](*,)   what should i do to fix this problem?

---

### Post by LGP on 2005-08-08
never mind that i just found out what my problem was ... my speakers were screwed up ... now i really feel dumb.  :-|

---

### Post by KingBahamut on 2005-08-08
[QUOTE=LGP]never mind that i just found out what my problem was ... my speakers were screwed up ... now i really feel dumb.  :-|[/QUOTE]
 No Stupid questions , nor are users who ask such questions themselves stupid or dumb. 

Welcome to the Boards, mate.

---

### Post by LGP on 2005-08-15
ok it turns out it wasn't the speakers because it does that with a few different speakers including my new ones that i know work because i have used them in windows and they are fine.  anybody know why it is so screwed up and the singing is so much lower than the music?

---

### Post by pmjdebruijn on 2005-08-15
Well, not without more information...

What soundcard do you have? (try 'lspci' in the terminal)
Which driver are you using? (try 'lsmod' in the terminal)
What bootup message do you get regarding your sound card? (try 'dmesg' in the terminal)

Please post relevant stuff in here...

Regards,
Pascal de Bruijn

---

### Post by LGP on 2005-08-15
```
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
``` 

```
soundcore               9824  4 snd
``` 

```
Linux version 2.6.10-5-386 (buildd@vernadsky) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Fri Jun 24 16:53:01 UTC 2005
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
 BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
 BIOS-e820: 000000001fff0000 - 000000001fff8000 (ACPI data)
 BIOS-e820: 000000001fff8000 - 0000000020000000 (ACPI NVS)
 BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
 BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
 BIOS-e820: 00000000ffee0000 - 00000000fff00000 (reserved)
 BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
511MB LOWMEM available.
On node 0 totalpages: 131056
  DMA zone: 4096 pages, LIFO batch:1
  Normal zone: 126960 pages, LIFO batch:16
  HighMem zone: 0 pages, LIFO batch:1
DMI 2.3 present.
ACPI: RSDP (v000 AMI                                   ) @ 0x000fa300
ACPI: RSDT (v001 AMIINT SiS735XX 0x00001000 MSFT 0x0100000b) @ 0x1fff0000
ACPI: FADT (v001 AMIINT SiS735XX 0x00001000 MSFT 0x0100000b) @ 0x1fff0030
ACPI: DSDT (v001    SiS      735 0x00000100 MSFT 0x0100000d) @ 0x00000000
ACPI: PM-Timer IO Port: 0x808
Built 1 zonelists
Kernel command line: root=/dev/hda3 ro quiet splash
Local APIC disabled by BIOS -- you can enable it with "lapic"
mapped APIC to ffffd000 (01406000)
Initializing CPU#0
PID hash table entries: 2048 (order: 11, 32768 bytes)
Detected 1145.202 MHz processor.
Using pmtmr for high-res timesource
Console: colour VGA+ 80x25
Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Memory: 511772k/524224k available (1436k kernel code, 11864k reserved, 754k data, 224k init, 0k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay loop... 2277.37 BogoMIPS (lpj=1138688)
Security Framework v1.0.0 initialized
SELinux:  Disabled at boot.
Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
CPU: After generic identify, caps: 0383f9ff c1cbf9ff 00000000 00000000 00000000 00000000
CPU: After vendor identify, caps: 0383f9ff c1cbf9ff 00000000 00000000 00000000 00000000
CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
CPU: L2 Cache: 256K (64 bytes/line)
CPU: After all inits, caps: 0383f9ff c1cbf9ff 00000000 00000020 00000000 00000000
CPU: AMD Athlon(tm) Processor stepping 02
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Checking 'hlt' instruction... OK.
Checking for popad bug... OK.
ACPI: Looking for DSDT in initrd... not found!
ACPI: setting ELCR to 0200 (from 0820)
checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
Freeing initrd memory: 4300k freed
NET: Registered protocol family 16
EISA bus registered
PCI: PCI BIOS revision 2.10 entry at 0xfdb01, last bus=1
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20050211
ACPI: Interpreter enabled
ACPI: Using PIC for interrupt routing
ACPI: PCI Root Bridge [PCI0] (00:00)
PCI: Probing PCI hardware (bus 00)
Uncovering SIS18 that hid as a SIS503 (compatible=1)
Enabling SiS 96x SMBus.
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: Power Resource [URP1] (off)
ACPI: Power Resource [URP2] (off)
ACPI: Power Resource [FDDP] (off)
ACPI: Power Resource [LPTP] (off)
ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 7 10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 *11 12 14 15)
ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 *11 12 14 15)
ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 *11 12 14 15)
ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 *11 12 14 15)
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: PnP ACPI: found 12 devices
PnPBIOS: Disabled by ACPI PNP
PCI: Using ACPI for IRQ routing
** PCI interrupts are no longer routed automatically.  If this
** causes a device to stop working, it is probably because the
** driver failed to call pci_enable_device().  As a temporary
** workaround, the "pci=routeirq" argument restores the old
** behavior.  If this argument makes the device work again,
** please email the output of "lspci" to [email]bjorn.helgaas@hp.com[/email]
** so I can fix the driver.
audit: initializing netlink socket (disabled)
audit(1124117657.355:0): initialized
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
PCI: setting IRQ 11 as level-triggered
ACPI: PCI interrupt 0000:00:02.6[C] -> GSI 11 (level, low) -> IRQ 11
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
input: AT Translated Set 2 keyboard on isa0060/serio0
EISA: Probing bus 0 at eisa0
EISA: Detected 0 cards.
NET: Registered protocol family 2
IP: routing cache hash table of 4096 buckets, 32Kbytes
TCP: Hash tables configured (established 32768 bind 65536)
NET: Registered protocol family 8
NET: Registered protocol family 20
Restarting tasks...<6> Strange, kswapd0 not stopped
 Strange, kseriod not stopped
 done
ACPI wakeup devices:
PCI0 PS2M PS2K UAR1 UAR2 USB1 USB2  LAN  MDM  AUD SLPB
ACPI: (supports S0 S1 S4 S5)
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4300KiB [1 disk] into ram disk... done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 224k freed
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
SIS5513: IDE controller at PCI slot 0000:00:02.5
SIS5513: chipset revision 208
SIS5513: not 100% native mode: will probe irqs later
SIS5513: SiS735 ATA 100 (2nd gen) controller
    ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:DMA, hdb:DMA
    ide1: BM-DMA at 0xff08-0xff0f, BIOS settings: hdc:DMA, hdd:DMA
Probing IDE interface ide0...
hda: MAXTOR 6L040J2, ATA DISK drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 128KiB
hda: 78177792 sectors (40027 MB) w/1819KiB Cache, CHS=65535/16/63, UDMA(33)
hda: cache flushes supported
 /dev/ide/host0/bus0/target0/lun0: p1 p2 p3 p4 < p5 >
Probing IDE interface ide1...
hdc: IDE/ATAPI CD-ROM 40XS, ATAPI CD/DVD-ROM drive
hdd: LITE-ON LTR-40125S, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
EXT3-fs: INFO: recovery required on readonly filesystem.
EXT3-fs: write access will be enabled during recovery.
EXT3-fs: recovery complete.
kjournald starting.  Commit interval 5 seconds
EXT3-fs: mounted filesystem with ordered data mode.
Adding 473876k swap on /dev/hda5.  Priority:-1 extents:1
EXT3 FS on hda3, internal journal
input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
mice: PS/2 mouse device common for all mice
ts: Compaq touchscreen protocol output
hdc: ATAPI 11X CD-ROM drive, 128kB Cache
Uniform CD-ROM driver Revision: 3.20
hdd: ATAPI 48X CD-ROM CD-R/RW drive, 2048kB Cache
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
lp0: using parport0 (interrupt-driven).
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: [email]dm-devel@redhat.com[/email]
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
cdrom: open failed.
cdrom: open failed.
cdrom: open failed.
FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
Real Time Clock Driver v1.12
input: PC Speaker
inserting floppy driver for 2.6.10-5-386
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected SiS 735 chipset
agpgart: Maximum main memory to use for agp memory: 439M
agpgart: AGP aperture is 64M @ 0xd0000000
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
sis630_smbus 0000:00:02.0: SIS630 comp. bus not detected, module not inserted.
i2c-sis96x version 1.0.0
sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x0c00
usbcore: registered new driver usbfs
usbcore: registered new driver hub
ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
ACPI: PCI interrupt 0000:00:02.2[D] -> GSI 11 (level, low) -> IRQ 11
ohci_hcd 0000:00:02.2: Silicon Integrated Systems [SiS] USB 1.0 Controller
ohci_hcd 0000:00:02.2: irq 11, pci mem 0xcfffe000
ohci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 3 ports detected
ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
ACPI: PCI interrupt 0000:00:02.3[A] -> GSI 11 (level, low) -> IRQ 11
ohci_hcd 0000:00:02.3: Silicon Integrated Systems [SiS] USB 1.0 Controller (#2)
ohci_hcd 0000:00:02.3: irq 11, pci mem 0xcffff000
ohci_hcd 0000:00:02.3: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 3 ports detected
ACPI: PCI interrupt 0000:00:02.6[C] -> GSI 11 (level, low) -> IRQ 11
ACPI: PCI interrupt 0000:00:02.7[C] -> GSI 11 (level, low) -> IRQ 11
intel8x0_measure_ac97_clock: measured 49038 usecs
intel8x0: clocking to 48000
sis900.c: v1.08.07 11/02/2003
ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 11
ACPI: PCI interrupt 0000:00:03.0[A] -> GSI 11 (level, low) -> IRQ 11
0000:00:03.0: Realtek RTL8201 PHY transceiver found at address 1.
0000:00:03.0: Using transceiver found at address 1 as default
eth0: SiS 900 PCI Fast Ethernet at 0xcc00, IRQ 11, 00:07:95:aa:b8:a3.
NET: Registered protocol family 17
eth0: Media Link On 100mbps full-duplex
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
ACPI: Power Button (FF) [PWRF]
ACPI: Sleep Button (CM) [SLPB]
ibm_acpi: ec object not found
apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
apm: overridden by ACPI.
[drm] Initialized drm 1.0.0 20040925
ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 5
PCI: setting IRQ 5 as level-triggered
ACPI: PCI interrupt 0000:01:00.0[A] -> GSI 5 (level, low) -> IRQ 5
[drm] Initialized radeon 1.14.0 20050125 on minor 0: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]
agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
eth0: no IPv6 routers present
``` 



I dunno if thats the right stuff because like i said i am new to all of this

---

### Post by pmjdebruijn on 2005-08-15
Well,

You relevant modules don't seem right... if that's the only module, you shouldn't get any sound at all...

When looking at the boot message ('dmesg'), I think your using OSS, but I could be wrong...

Anyway, have you tried modprobing the 'snd-intel8x0' module?

[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=SiS&card=SiS+735.&chip=SI7012&module=intel8x0](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=SiS&card=SiS+735.&chip=SI7012&module=intel8x0)

Regards,
Pascal de Bruijn

---

### Post by LGP on 2005-08-15
um i don't understand at all what that means or what im supposed to do

---

### Post by poofyhairguy on 2005-08-16
[QUOTE=LGP]um i don't understand at all what that means or what im supposed to do[/QUOTE]

Try this command in regular terminal:

> sudo modprobe snd-intel8x0

---

### Post by LGP on 2005-08-16
no that didn't work it is still the same   ](*,)  :? 

```
littlegp@justin:~ $  sudo modprobe snd-intel8x0
Password:
littlegp@justin:~ $
``` 

that is what it looked like when i did the command

---

### Post by jrev on 2005-08-17
[QUOTE=LGP]i just got ubuntu installed on my computer and the sound quality was bad and everything sounded messed up.  I got that figured out and the poor quality is fixed but now it still isn't right.  when i am listening to music the singing is alot lower than the music and you can barly hear the singing. ](*,)   what should i do to fix this problem?[/QUOTE]
 did you install the ubuntuaddon.zip ?
ask google for it

---

### Post by pmjdebruijn on 2005-08-17
[QUOTE=jrev]did you install the ubuntuaddon.zip ?
ask google for it[/QUOTE]

No offense, but what does that have to do with anything?

Regards,
Pascal de Bruijn

---

### Post by pmjdebruijn on 2005-08-17
Anyway,

Maybe this can be of any help:
[http://opensrc.org/alsa/index.php?page=intel8x0](http://opensrc.org/alsa/index.php?page=intel8x0)

Also there is an OpenSoundSystem driver for the intel8x0 ac97 soundchip, I'm not sure about it's name... But generally the OSS drivers are more reliable...

Regards,
Pascal de Bruijn

---

### Post by LGP on 2005-08-26
I'm sorry but i am realy new to this stuff and I don't get what I am supposed to do with that.

---

### Post by pmjdebruijn on 2005-08-27
Try

```
sudo modprobe i810_audio
```

Regards,
Pascal de Bruijn

---

### Post by LGP on 2005-09-17
I did that and it didn't change anything.  It still sounds bad and the music is louder than the singing and i can barely hear the singing.   ](*,)

---

### Post by pmjdebruijn on 2005-09-17
Yes, that's right... Your 'dmesg' should now say it found the card. (type 'dmesg' into a terminal).

Have you retried the sound?

Regards,
Pascal de Bruijn

---

