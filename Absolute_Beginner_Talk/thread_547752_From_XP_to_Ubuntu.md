---
title: "From XP to Ubuntu"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by Tessea on 2007-09-10
I am completely new to both Ubuntu and these forums, but am excited about getting started...

Here's the story. I have used a Sony VAIO desktop for the last 4-5 years. When we bought the machine, it was running on Windows ME. We made the switch to XP shortly after it came out, and things were fine for a long time. The computer was only really used for internetting, listening to music, and a small bit of photo editing. However, somewhere along the way things went wrong. XP began to run even more slowly than normal and applications started shutting themselves down for no reason. I could go on and on about the problems, but as this isn't a Windows forum, I won't bother you with them. I'll just say that XP ended up getting stuck on 15-bit and ran more slowly than molasses.

I had a very technology-savvy friend do his best to help me out with the computer. Due to the amount of problems collected on the machine, we both agreed that the best thing to do would be to wipe the harddrive and start over. At his advice, I decided to run Ubuntu once the harddrive was cleaned off. He burned me an Ubuntu OS disc and was prepared to help me do everything I needed to get it installed, but I ended up moving 1,100 miles away the next week. :-| 

So now I am left with a very unhappy Windows XP machine and an Ubuntu OS disc. I ran Ubuntu off the disc for a few weeks and fell in love with it, but because I was running an OS from a CD, it ran very slowly. I want to make the full switch to Ubuntu. I have saved all my music and photos on an external harddrive and need to reformat my harddrive, but alas, I left my Windows XP OS disc at my last location and am not sure if I can recover it. 


Here's my question. Can I use my Ubuntu OS disc to reformat the harddrive? And if so, how do I go about this?

---

### Post by rsambuca on 2007-09-10
The Ubuntu disc has a partitioner on it called gParted which will do everything for you.  However, if you are just going to wipe out XP, during the installation process just select the option to "use the entire disk" and it will set it up for you.

---

### Post by Tessea on 2007-09-10
Ok, so when I boot up my computer with the Ubuntu disc in, I just select 'Start or Install Ubuntu'?

That will take me to the desktop, what do I do from there?

(Thanks for the quick reply, btw :))

---

### Post by Duck2006 on 2007-09-10
Have a read of this it will walk you through the install of ubuntu

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Maestro23 on 2007-09-10
> **Tessea said:**
> Ok, so when I boot up my computer with the Ubuntu disc in, I just select 'Start or Install Ubuntu'?

That will take me to the desktop, what do I do from there?

(Thanks for the quick reply, btw :))

Check the following link.  It has a focus of setting up a dual-boot, but will help you with single install as well.  Welcome to the community.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by bruce2000 on 2007-09-10
There's an icon on the desktop called *Install Ubuntu* or something like that. Double click it and away you go.

---

### Post by Tessea on 2007-09-10
Awesome, thanks a lot, guys. (That tutorial is fantastic, screenshots are always such a great help to me.) I will have a go at this in a little while and I'm sure I'll be back if I have more questions...

---

### Post by chrome307 on 2007-09-10
When you are installing do a 'MANUAL PARTITION' this will allow you specify the size of the partitions that are used by the OS.

The root directory is called /  - this is where you OS resides 

Then you have a HOME folder - this is where you  personal files are stored

Finally you have the SWAP partition - this is Virtual Memory


The reason I have suggested doing a manual partition is that you all your personal files that reside in the HOME folder will not be affected if you have problems with the OS or if you decide to upgrade it to another version.

You should be okay with a 8/12 GB Root directory with a 1GB Swap file ..... the rest of the space can be the Home directory.

This is assuming your using a single HDD soley for the use of Ubuntu.

---

### Post by cc6000 on 2007-09-10
In case you are going to install Ubuntu using your entire disk and not share it with WinXP, I agree with the above post that "manual partition" is the way to go. I am a total noob and wrote up a short blog on hard disk partition for Ubuntu while I was trying to manual partition the system. The link is here:

[Disk Partition Blog]("http://maybe-if-i-sober-up.blogspot.com/2007/08/disk-partition-setup-in-ubuntu.html")

I hope this helps.

CC

---

### Post by Tessea on 2007-09-12
Ok, here is my next question:
I coped all my files to an external harddrive (F: ) and wiped the computer, installed Ubuntu. Connected F: again and got all of my photos copied and then started on the music. Ran into an error, disconnected. Reconnected and the computer would not recognize the F: drive no matter how many times I dis/reconnected.
Just now, I reconnected and it gave me this error message:

"Cannot mount volume.
Unable to mount the volume 'GSTOR WAVE.'

Details:
 mount: /dev/sdb1: can't read superblock"

Suggestions?

---

### Post by Duck2006 on 2007-09-12
Have you tryed mounting the drive?

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by Tessea on 2007-09-13
Can you dumb that down for me a little? It IS an external drive, so according to that site, shouldn't it automount?
[quote=]If you plug in an external hard drive with a Linux filesystem, it will automount and show up on your desktop, just like any external media.[/quote]

---

### Post by Tessea on 2007-09-13
bump >_>

---

### Post by overdrank on 2007-09-13
> **Tessea said:**
> Can you dumb that down for me a little? It IS an external drive, so according to that site, shouldn't it automount?

HI, I have seen threads with this sort of issue and the reason behind some were the drive was not shut down properly. If you have another OS like windows or others, maybe try and mount the drive there and then shut down properly. Hope this helps. Good Luck!

---

### Post by Tessea on 2007-09-13
I will give that a try on my roommate's XP computer, thanks a lot!

---

### Post by Tessea on 2007-09-13
OK, the drive is still not automounting. It came up fine on the Windows machine and I double-checked to make sure my files were still ok (they were :)). I reconnected to my computer and the external drive is ON, and I can HEAR it trying to connect (if that makes sense) but it just won't automount. No icon on the desktop, and I can't find it by going into Places > Computer...

How would I go about mounting it otherwise?

---

### Post by Tessea on 2007-09-14
: /

---

### Post by Vadi on 2007-09-14
That's a very good thing that everything is still there, I thought the drive got corrupted when you posted "can't read the superblock".

I'd try booting into the LiveCD, plugging the drive in, and starting gparted (system - administration - gparted in the livecd). Don't do anything with gparted, gparted just starts a mount-check process that'll hopefully detect your drive.

---

### Post by Tessea on 2007-09-14
So I should run the LiveCD even though I have Feisty Fawn installed?

---

### Post by Vadi on 2007-09-14
I'd try it, yes. The LiveCD will also detect your Feisty too, so if it also detects your drive, you could copy from the drive to Feisty.

---

### Post by Tessea on 2007-09-14
Ok, great. I will give that a try. Thanks (:

---

### Post by cc6000 on 2007-09-14
in case the LiveCD idea does not work..
it may be a hardware issue..

try plugging the usb hard drive into another usb port. try using the usb ports in the back of the pc and not in the front and not using a usb hub and also remove other usb devices such as printers, etc.

i have a similar problem with an XP system and it turns out the hard drive only worked if i plug it into an usb port in the back of the pc and not the front.

good luck.

---

### Post by Tessea on 2007-09-15
Have not given the LiveCD a shot yet, however - 
I have only 3 USB ports (one in front, two in back) and I have tried all. There's nothing plugged into any of the other ports...so looks like that solution is out. :/

---

### Post by gigaferz on 2007-09-15
go to applications, then click on terminal, once the screen appears  type "dmesg" and press enter.

it will give more information about the error...., 

have it ready or if you wish post it , hopefully somebody will be asking for that shortly...

ALso!! if you can on windows right click your drive and check the properties.. and figure out the file system..... that will help too...

always make sure you do the right thing when unplugging your drive, in windows and ubuntu I guess is something like "safely remove hardware/disk"

---

### Post by Tessea on 2007-09-15
Here's what I got, it's quite long

> **]tess@tess-desktop:~$ dmesg
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Fri Aug 31 00:55:27 UTC 2007 (Ubuntu 2.6.20-16.31-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000000fefc000 end: 000000000fffc000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000fffc000 size: 0000000000003000 end: 000000000ffff000 type: 3
[    0.000000] copy_e820_map() start: 000000000ffff000 size: 0000000000001000 end: 0000000010000000 type: 4
[    0.000000] copy_e820_map() start: 00000000ffff0000 size: 0000000000010000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000fffc000 (usable)
[    0.000000]  BIOS-e820: 000000000fffc000 - 000000000ffff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000000ffff000 - 0000000010000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 255MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 65532) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    65532
[    0.000000]   HighMem     65532 ->    65532
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    65532
[    0.000000] On node 0 totalpages: 65532
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 479 pages used for memmap
[    0.000000]   Normal zone: 60957 pages, LIFO batch:15
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 ASUS                                  ) @ 0x000f5b30
[    0.000000] ACPI: RSDT (v001 ASUS   CUSL-LX  0x30303031 MSFT 0x31313031) @ 0x0fffc000
[    0.000000] ACPI: FADT (v001 ASUS   CUSL-LX  0x30303031 MSFT 0x31313031) @ 0x0fffc080
[    0.000000] ACPI: BOOT (v001 ASUS   CUSL-LX  0x30303031 MSFT 0x31313031) @ 0x0fffc040
[    0.000000] ACPI: DSDT (v001   ASUS CUSL-LX  0x00001000 MSFT 0x0100000b) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0xe408
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 10000000:efff0000)
[    0.000000] Detected 1002.322 MHz processor.
[   15.008860] Built 1 zonelists.  Total pages: 65021
[   15.008869] Kernel command line: root=UUID=d0ec5ad3-6ae2-4693-bbf2-891c83aa601c ro quiet splash
[   15.009272] Local APIC disabled by BIOS -- you can enable it with "lapic"
[   15.009291] mapped APIC to ffffd000 (0120a000)
[   15.009299] Enabling fast FPU save and restore... done.
[   15.009304] Enabling unmasked SIMD FPU exception support... done.
[   15.009324] Initializing CPU#0
[   15.009415] PID hash table entries: 1024 (order: 10, 4096 bytes)
[   15.010792] Console: colour VGA+ 80x25
[   15.011235] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[   15.011657] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[   15.032432] Memory: 248888k/262128k available (1993k kernel code, 12736k reserved, 900k data, 328k init, 0k highmem)
[   15.032456] virtual kernel memory layout:
[   15.032458]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   15.032461]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   15.032464]     vmalloc : 0xd0800000 - 0xff7fe000   ( 751 MB)
[   15.032467]     lowmem  : 0xc0000000 - 0xcfffc000   ( 255 MB)
[   15.032470]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   15.032472]       .data : 0xc02f2434 - 0xc03d36d4   ( 900 kB)
[   15.032475]       .text : 0xc0100000 - 0xc02f2434   (1993 kB)
[   15.032482] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   15.109359] Calibrating delay using timer specific routine.. 2006.19 BogoMIPS (lpj=4012387)
[   15.109443] Security Framework v1.0.0 initialized
[   15.109458] SELinux:  Disabled at boot.
[   15.109492] Mount-cache hash table entries: 512
[   15.109753] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   15.109774] CPU: L1 I cache: 16K, L1 D cache: 16K
[   15.109780] CPU: L2 cache: 256K
[   15.109786] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[   15.109807] Compat vDSO mapped to ffffe000.
[   15.109821] Remapping vsyscall page to ffffe000
[   15.109840] Checking 'hlt' instruction... OK.
[   15.125524] SMP alternatives: switching to UP code
[   15.125834] Freeing SMP alternatives: 11k freed
[   15.126205] Early unpacking initramfs... done
[   15.770563] ACPI: Core revision 20060707
[   15.771453] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   15.773902] ACPI: setting ELCR to 0200 (from 0a08)
[   15.774128] CPU0: Intel Pentium III (Coppermine) stepping 06
[   15.774140] SMP motherboard not detected.
[   15.774145] Local APIC not detected. Using dummy APIC emulation.
[   15.774236] Brought up 1 CPUs
[   15.774771] Booting paravirtualized kernel on bare hardware
[   15.774901] Time: 15:38:28  Date: 08/15/107
[   15.774969] NET: Registered protocol family 16
[   15.775185] EISA bus registered
[   15.775196] ACPI: bus type pci registered
[   15.776369] PCI: PCI BIOS revision 2.10 entry at 0xf0900, last bus=2
[   15.776374] PCI: Using configuration type 1
[   15.776378] Setting up standard PCI resources
[   15.785889] ACPI: Interpreter enabled
[   15.785898] ACPI: Using PIC for interrupt routing
[   15.787170] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   15.787614] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[   15.788053] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   15.788493] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   15.790827] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   15.790840] PCI: Probing PCI hardware (bus 00)
[   15.791239] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[   15.791699] PCI quirk: region e400-e47f claimed by ICH4 ACPI/GPIO/TCO
[   15.791708] PCI quirk: region ec00-ec3f claimed by ICH4 GPIO
[   15.792029] Boot video device is 0000:01:00.0
[   15.792319] PCI: Transparent bridge - 0000:00:1e.0
[   15.792352] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   15.840737] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[   15.843124] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI2._PRT]
[   15.854378] Linux Plug and Play Support v0.97 (c) Adam Belay
[   15.854404] pnp: PnP ACPI init
[   15.861173] pnp: PnP ACPI: found 15 devices
[   15.861186] PnPBIOS: Disabled by ACPI PNP
[   15.861310] PCI: Using ACPI for IRQ routing
[   15.861317] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   15.865716] NET: Registered protocol family 8
[   15.865721] NET: Registered protocol family 20
[   15.866236] pnp: 00:03: ioport range 0xe400-0xe47f could not be reserved
[   15.866244] pnp: 00:03: ioport range 0xec00-0xec3f has been reserved
[   15.866250] pnp: 00:03: ioport range 0x290-0x297 has been reserved
[   15.866853] PCI: Bridge: 0000:00:01.0
[   15.866859]   IO window: disabled.
[   15.866867]   MEM window: d6000000-d7efffff
[   15.866873]   PREFETCH window: d7f00000-e3ffffff
[   15.866880] PCI: Bridge: 0000:00:1e.0
[   15.866886]   IO window: c000-dfff
[   15.866893]   MEM window: d4000000-d5ffffff
[   15.866899]   PREFETCH window: disabled.
[   15.866916] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   15.866927] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   15.866982] NET: Registered protocol family 2
[   15.905050] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[   15.905220] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[   15.905396] TCP bind hash table entries: 4096 (order: 3, 32768 bytes)
[   15.905489] TCP: Hash tables configured (established 8192 bind 4096)
[   15.905495] TCP reno registered
[   15.917134] checking if image is initramfs... it is
[   17.128960] Freeing initrd memory: 6783k freed
[   17.129450] Simple Boot Flag at 0x3a set to 0x1
[   17.129837] audit: initializing netlink socket (disabled)
[   17.129867] audit(1189870709.304:1): initialized
[   17.130152] VFS: Disk quotas dquot_6.5.1
[   17.130198] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   17.130319] io scheduler noop registered
[   17.130325] io scheduler anticipatory registered
[   17.130330] io scheduler deadline registered
[   17.130352] io scheduler cfq registered (default)
[   17.130863] isapnp: Scanning for PnP cards...
[   17.484479] isapnp: No Plug & Play device found
[   17.543299] Real Time Clock Driver v1.12ac
[   17.543410] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   17.543577] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   17.544997] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   17.545516] mice: PS/2 mouse device common for all mice
[   17.546713] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   17.547245] input: Macintosh mouse button emulation as /class/input/input0
[   17.547323] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   17.547332] ide: Assuming 33MHz system bus speed for PIO modes said:**
>  PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   17.551137] serio: i8042 KBD port at 0x60,0x64 irq 1
[   17.551152] serio: i8042 AUX port at 0x60,0x64 irq 12
[   17.551470] EISA: Probing bus 0 at eisa.0
[   17.551527] EISA: Detected 0 cards.
[   17.581689] TCP cubic registered
[   17.581706] NET: Registered protocol family 1
[   17.581751] Using IPI No-Shortcut mode
[   17.581876] ACPI: (supports S0 S1 S3 S4 S5)
[   17.581965]   Magic number: 7:317:639
[   17.583020] Freeing unused kernel memory: 328k freed
[   17.583866] Time: tsc clocksource has been installed.
[   17.601300] input: AT Translated Set 2 keyboard as /class/input/input1
[   19.128200] Capability LSM initialized
[   19.217930] ACPI: Invalid PBLK length [5]
[   20.359128] SCSI subsystem initialized
[   20.377734] libata version 2.20 loaded.
[   20.390055] ata_piix 0000:00:1f.1: version 2.10ac1
[   20.390103] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   20.390220] ata1: PATA max UDMA/66 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001b800 irq 14
[   20.390278] ata2: PATA max UDMA/66 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001b808 irq 15
[   20.390312] scsi0 : ata_piix
[   20.423052] usbcore: registered new interface driver usbfs
[   20.423100] usbcore: registered new interface driver hub
[   20.423151] usbcore: registered new device driver usb
[   20.481734] USB Universal Host Controller Interface driver v3.0
[   20.535667] 8139too Fast Ethernet driver 0.9.28
[   20.554527] ata1.00: ata_hpa_resize 1: sectors = 120060864, hpa_sectors = 120060864
[   20.554539] ata1.00: ATA-6: Maxtor 96147H8, BAC51KJ0, max UDMA/100
[   20.554545] ata1.00: 120060864 sectors, multi 16: LBA 
[   20.562540] ata1.00: ata_hpa_resize 1: sectors = 120060864, hpa_sectors = 120060864
[   20.562552] ata1.00: configured for UDMA/66
[   20.562575] scsi1 : ata_piix
[   20.605072] ieee1394: Initialized config rom entry `ip1394'
[   20.764477] Floppy drive(s): fd0 is 1.44M
[   20.824718] FDC 0 is a post-1991 82077
[   21.045985] ata2.00: ATAPI, max UDMA/33
[   21.045994] ata2.01: ATAPI, max UDMA/33
[   21.209900] ata2.00: configured for UDMA/33
[   21.373755] ata2.01: configured for UDMA/33
[   21.374015] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 96147H8   BAC5 PQ: 0 ANSI: 5
[   21.381592] scsi 1:0:0:0: CD-ROM            PIONEER  DVD-ROM DVD-115R 1.25 PQ: 0 ANSI: 5
[   21.384754] scsi 1:0:1:0: CD-ROM            SONY     CD-RW  CRX140E   1.1a PQ: 0 ANSI: 5
[   21.392191] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 9
[   21.392201] PCI: setting IRQ 9 as level-triggered
[   21.392206] ACPI: PCI Interrupt 0000:00:1f.2[D] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[   21.392226] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   21.392233] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[   21.392444] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[   21.392480] uhci_hcd 0000:00:1f.2: irq 9, io base 0x0000b400
[   21.392730] usb usb1: configuration #1 chosen from 1 choice
[   21.392785] hub 1-0:1.0: USB hub found
[   21.392802] hub 1-0:1.0: 2 ports detected
[   21.440620] SCSI device sda: 120060864 512-byte hdwr sectors (61471 MB)
[   21.442138] sda: Write Protect is off
[   21.442146] sda: Mode Sense: 00 3a 00 00
[   21.443836] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.443961] SCSI device sda: 120060864 512-byte hdwr sectors (61471 MB)
[   21.443983] sda: Write Protect is off
[   21.443988] sda: Mode Sense: 00 3a 00 00
[   21.444020] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.444028]  sda: sda1 sda2 <ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 3
[   21.494505] PCI: setting IRQ 3 as level-triggered
[   21.494512] ACPI: PCI Interrupt 0000:02:0d.0[A] -> Link [LNKB] -> GSI 3 (level, low) -> IRQ 3
[   21.494534] PCI: Setting latency timer of device 0000:02:0d.0 to 64
[   21.494890] eth0: RealTek RTL8139 at 0xd0820000, 00:e0:18:c5:1f:8a, IRQ 3
[   21.494895] eth0:  Identified 8139 chip type 'RTL-8139C'
[   21.499645] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   21.500590] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 9
[   21.500599] ACPI: PCI Interrupt 0000:02:0e.0[A] -> Link [LNKC] -> GSI 9 (level, low) -> IRQ 9
[   21.500612] PCI: Setting latency timer of device 0000:02:0e.0 to 64
[   21.552195] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[9]  MMIO=[d4800000-d48007ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   21.561485]  sda5 >
[   21.561727] sd 0:0:0:0: Attached scsi disk sda
[   21.565969] sr0: scsi3-mmc drive: 16x/40x cd/rw xa/form2 cdda tray
[   21.565982] Uniform CD-ROM driver Revision: 3.20
[   21.566102] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   21.577192] sr1: scsi3-mmc drive: 32x/32x writer cd/rw xa/form2 cdda tray
[   21.577764] sr 1:0:1:0: Attached scsi CD-ROM sr1
[   21.607263] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   21.607526] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   21.607765] sr 1:0:1:0: Attached scsi generic sg2 type 5
[   21.757355] usb 1-2: new full speed USB device using uhci_hcd and address 2
[   21.925381] usb 1-2: configuration #1 chosen from 1 choice
[   21.930257] hub 1-2:1.0: USB hub found
[   21.932161] hub 1-2:1.0: 2 ports detected
[   21.970295] Attempting manual resume
[   21.970303] swsusp: Resume From Partition 8:5
[   21.970307] PM: Checking swsusp image.
[   21.970830] PM: Resume from disk failed.
[   22.055944] kjournald starting.  Commit interval 5 seconds
[   22.055975] EXT3-fs: mounted filesystem with ordered data mode.
[   22.825099] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[08004603005f0687]
[   36.606778] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   38.323811] NET: Registered protocol family 17
[   39.460134] intel_rng: FWH not detected
[   39.530922] iTCO_vendor_support: vendor-support=0
[   39.557057] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   39.557222] iTCO_wdt: Found a ICH TCO device (Version=1, TCOBASE=0x6460)
[   39.557246] iTCO_wdt: heartbeat value must be 2<heartbeat<39 (TCO v1) or 613 (TCO v2), using 30
[   39.557304] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   39.793481] Linux agpgart interface v0.102 (c) Dave Jones
[   40.131502] agpgart: Detected an Intel i815 Chipset.
[   40.135618] agpgart: AGP aperture is 64M @ 0xe4000000
[   40.162479] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   40.211569] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   40.855565] input: PC Speaker as /class/input/input2
[   40.919373] parport: PnPBIOS parport detected.
[   40.919420] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   41.714654] input: ImExPS/2 Generic Explorer Mouse as /class/input/input3
[   42.258484] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 3 (level, low) -> IRQ 3
[   42.258523] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   42.572700] intel8x0_measure_ac97_clock: measured 52877 usecs
[   42.572710] intel8x0: clocking to 48000
[   42.841887] fuse init (API version 7.8)
[   42.868822] lp0: using parport0 (interrupt-driven).
[   42.965728] Adding 746980k swap on /dev/disk/by-uuid/a9e7c4df-0095-4aaa-8c1f-d2f3c5d034d0.  Priority:-1 extents:1 across:746980k
[   43.141862] EXT3 FS on sda1, internal journal
[   49.948257] input: Power Button (FF) as /class/input/input4
[   49.956596] ACPI: Power Button (FF) [PWRF]
[   50.012257] input: Power Button (CM) as /class/input/input5
[   50.012723] ACPI: Power Button (CM) [PWRB]
[   50.058875] No dock devices found.
[   50.097977] Using specific hotkey driver
[   50.245748] ibm_acpi: ec object not found
[   50.319567] pcc_acpi: loading...
[   58.188409] ppdev: user-space parallel port driver
[   59.688667] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   59.688679] apm: overridden by ACPI.
[   59.899590] sonypi: Sony Programmable I/O Controller Driver v1.26.
[   60.304498] Bluetooth: Core ver 2.11
[   60.305797] NET: Registered protocol family 31
[   60.305810] Bluetooth: HCI device and connection manager initialized
[   60.305818] Bluetooth: HCI socket layer initialized
[   61.057392] Bluetooth: L2CAP ver 2.8
[   61.057402] Bluetooth: L2CAP socket layer initialized
[   61.086071] Bluetooth: RFCOMM socket layer initialized
[   61.086102] Bluetooth: RFCOMM TTY layer initialized
[   61.086106] Bluetooth: RFCOMM ver 1.8
[   63.146489] NET: Registered protocol family 10
[   63.146690] lo: Disabled Privacy Extensions
[   73.601863] eth0: no IPv6 routers present
[ 4191.141019] usb 1-2.2: new full speed USB device using uhci_hcd and address 3
[ 4191.375983] usb 1-2.2: configuration #1 chosen from 1 choice
[ 4192.546601] usbcore: registered new interface driver libusual
[ 4192.608251] Initializing USB Mass Storage driver...
[ 4192.608392] scsi2 : SCSI emulation for USB Mass Storage devices
[ 4192.608495] usbcore: registered new interface driver usb-storage
[ 4192.608502] USB Mass Storage support registered.
[ 4192.608739] usb-storage: device found at 3
[ 4192.608744] usb-storage: waiting for device to settle before scanning
[ 4197.604711] usb-storage: device scan complete
[ 4197.640689] scsi 2:0:0:0: Direct-Access     FUJITSU  MHW2080AT        0000 PQ: 0 ANSI: 0
[ 4197.647595] SCSI device sdb: 156301488 512-byte hdwr sectors (80026 MB)
[ 4197.652633] sdb: Write Protect is off
[ 4197.652647] sdb: Mode Sense: 03 00 00 00
[ 4197.652651] sdb: assuming drive cache: write through
[ 4197.657583] SCSI device sdb: 156301488 512-byte hdwr sectors (80026 MB)
[ 4197.662586] sdb: Write Protect is off
[ 4197.662595] sdb: Mode Sense: 03 00 00 00
[ 4197.662599] sdb: assuming drive cache: write through
[ 4197.662608]  sdb:<6>usb 1-2.2: reset full speed USB device using uhci_hcd and address 3
[ 4228.793712] usb 1-2.2: device descriptor read/64, error -71
[ 4228.981562] usb 1-2.2: device descriptor read/64, error -71
[ 4229.157411] usb 1-2.2: reset full speed USB device using uhci_hcd and address 3
[ 4229.241344] usb 1-2.2: device descriptor read/64, error -71
[ 4229.429191] usb 1-2.2: device descriptor read/64, error -71
[ 4229.605062] usb 1-2.2: reset full speed USB device using uhci_hcd and address 3
[ 4230.015430] usb 1-2.2: device not accepting address 3, error -71
[ 4230.088642] usb 1-2.2: reset full speed USB device using uhci_hcd and address 3
[ 4230.499132] usb 1-2.2: device not accepting address 3, error -71
[ 4230.501322] sd 2:0:0:0: scsi: Device offlined - not ready after error recovery
[ 4230.501346] sd 2:0:0:0: SCSI error: return code = 0x00050000
[ 4230.501351] end_request: I/O error, dev sdb, sector 0
[ 4230.501361] Buffer I/O error on device sdb, logical block 0
[ 4230.501441] sd 2:0:0:0: rejecting I/O to offline device
[ 4230.501448] Buffer I/O error on device sdb, logical block 0
[ 4230.501480] sd 2:0:0:0: rejecting I/O to offline device
[ 4230.501487] Buffer I/O error on device sdb, logical block 0
[ 4230.501502] sd 2:0:0:0: rejecting I/O to offline device
[ 4230.501507] Buffer I/O error on device sdb, logical block 0
[ 4230.501522] sd 2:0:0:0: rejecting I/O to offline device
[ 4230.501528] Buffer I/O error on device sdb, logical block 0
[ 4230.501536] ldm_validate_partition_table(): Disk read failed.
[ 4230.501549] sd 2:0:0:0: rejecting I/O to offline device
[ 4230.501555] Buffer I/O error on device sdb, logical block 0
[ 4230.501569] sd 2:0:0:0: rejecting I/O to offline device
[ 4230.501575] Buffer I/O error on device sdb, logical block 0
[ 4230.501589] sd 2:0:0:0: rejecting I/O to offline device
[ 4230.501595] Buffer I/O error on device sdb, logical block 0
[ 4230.501609] sd 2:0:0:0: rejecting I/O to offline device
[ 4230.501615] Buffer I/O error on device sdb, logical block 0
[ 4230.501623] Dev sdb: unable to read RDB block 0
[ 4230.501635] sd 2:0:0:0: rejecting I/O to offline device
[ 4230.501641] Buffer I/O error on device sdb, logical block 0
[ 4230.501655] sd 2:0:0:0: rejecting I/O to offline device
[ 4230.501683] sd 2:0:0:0: rejecting I/O to offline device
[ 4230.501697] sd 2:0:0:0: rejecting I/O to offline device
[ 4230.501712] sd 2:0:0:0: rejecting I/O to offline device
[ 4230.501720]  unknown partition table
[ 4230.501854] sd 2:0:0:0: Attached scsi disk sdb
[ 4230.501948] sd 2:0:0:0: Attached scsi generic sg3 type 0
[ 4230.502278] usb 1-2.2: USB disconnect, address 3
[ 4230.576247] usb 1-2.2: new full speed USB device using uhci_hcd and address 4
[ 4230.660165] usb 1-2.2: device descriptor read/64, error -71
[ 4230.848005] usb 1-2.2: device descriptor read/64, error -71
[ 4231.024862] usb 1-2.2: new full speed USB device using uhci_hcd and address 5
[ 4231.112791] usb 1-2.2: device descriptor read/64, error -71
[ 4231.300633] usb 1-2.2: device descriptor read/64, error -71
[ 4231.476485] usb 1-2.2: new full speed USB device using uhci_hcd and address 6
[ 4231.886293] usb 1-2.2: device not accepting address 6, error -71
[ 4231.960082] usb 1-2.2: new full speed USB device using uhci_hcd and address 7
[ 4232.369996] usb 1-2.2: device not accepting address 7, error -71
tess@tess-desktop:~$ 



Nevermind though guys, thanks for all your help...however, it seems that my roommate has deleted my files from his external harddrive because he needed the space. Not a big deal, I'll just have to spend a lot of time redownloading my music now :):(

I do have one quick question though. I have only one stick of 256 RAM in my machine right now, should I go ahead and get another 256? Ubuntu is running fine (faster than Windows ever was) but all the same...

---

### Post by Tyke91 on 2007-09-15
it depends on what you want to do with it

256 should be fine for just internet surfing and such, but if you want to run alot of things at the same time then you maybe would want another stick of 256

(example, i am running amaroK [a good music player], firefox, gimp, and auto update at the same time... it's using 240 mb of ram.)



EDIT: sorry to hear about your music :(, i was going to suggest that if you could mount it in windows, to transfer it to a different device like a flashdrive, and try it again.

---

### Post by Tessea on 2007-09-15
Yeah, it's going to be a pain to redownload everything, I had somewhere around 20 gigs haha :(

Speaking of which, what do you suggest for downloading music files? I used soulseek on windows and loved it. Noticed that Ubuntu comes with BitTorrent, which with I have NO experience...

On the RAM - I will be doing mostly just that, music/internet/easy stuff, though I will be running Photoshop (or the equivalent) soon...but I have another stick of RAM that I bought for the computer awhile ago, I think Im just going to go ahead and install that since I already have it.

---

### Post by Vadi on 2007-09-15
Extra ram doesn't hurt.

I'm not much into this torrenting stuff, but when you download a .torrent file with firefox, it asks you if you want to open it right away with bittorrent. They take ages though to finish :(

Search in add/remove, there are tons of torrent applications.

By the way, if you look at the log you posted, starting from ~4,000th second after you boot, is the part where you inserted the HD... looks like there were some errors reading :|

---

