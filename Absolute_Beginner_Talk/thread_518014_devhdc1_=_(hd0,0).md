---
title: "/dev/hdc1 = (hd0,0)"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by garyed on 2007-08-05
I still have not been able to get into Ubuntu from grub.
Booting from the CD installer 
fdisk -l    returns 
Disk  /dev/hdc   80 gig ...  for  my Primary HD  (Bios Boot Drive)

/dev/hdc1       1     9729    78148161      c     W95 FAT32 (LBA)      


Disk  /dev/hdd    300 gig  ...........    for  my Secondary HD

/dev/hdd1       1    36246  291145963+  83  Linux             
/dev/hdd2              36247......................     5   Extended
/dev/hdd5 .........................................................   Linux swap/Solaris

My grub menu is  (hd0,0)

That my be my problem but I have tried all the grub suggestions & nothing has worked.
Even reinstalling Ubuntu hasn't helped.
I still get "error 15 file not found"  immediately after hitting the enter key at the menu.
Dual booting XP (hd0)  &   Edgy (hd1)

---

### Post by fimbulvetr on 2007-08-05
Please paste the contents of /boot/grub/menu.lst

---

### Post by ron999 on 2007-08-05
Deleted post

---

### Post by garyed on 2007-08-05
> **fimbulvetr said:**
> Please paste the contents of /boot/grub/menu.lst

Can you tell me the commands I need to mount my Linux HD  from the CD so I can do that?
I can't get to my HD to read any files.

---

### Post by fimbulvetr on 2007-08-05
> **garyed said:**
> Can you tell me the commands I need to mount my Linux HD  from the CD so I can do that?
I can't get to my HD to read any files.

Oh, heh, sorry about that. Forgot to think about that.

Boot to your livecd and you should be able to get a terminal up from Applications->Accessories->Terminal.

Do a

```

sudo mkdir /foo
sudo mount /dev/hdd1 /foo

```

And you should find it under /foo/boot/grub/menu.lst

if not, undo the above mount and mount hdd2:

```

sudo umount /dev/hdd1
sudo mount /dev/hdd2 /foo

```

and then try /foo/boot/grub/menu.lst

---

### Post by garyed on 2007-08-05
> **fimbulvetr said:**
> Oh, heh, sorry about that. Forgot to think about that.

Boot to your livecd and you should be able to get a terminal up from Applications->Accessories->Terminal.

Do a

```

sudo mkdir /foo
sudo mount /dev/hdd1 /foo

```

And you should find it under /foo/boot/grub/menu.lst

if not, undo the above mount and mount hdd2:

```

sudo umount /dev/hdd1
sudo mount /dev/hdd2 /foo

```

and then try /foo/boot/grub/menu.lst

I appreciate all the help but I still can't mount the drive with those commands.
When I use the sudo mount  command I get  "can't read superblock"  response.
Keep em coming I'll try anything at this point.

---

### Post by fimbulvetr on 2007-08-05
> **garyed said:**
> I appreciate all the help but I still can't mount the drive with those commands.
When I use the sudo mount  command I get  "can't read superblock"  response.
Keep em coming I'll try anything at this point.

Hmm, ok. Go back into the terminal and paste the output of ```
dmesg
``` here. We'll get to the bottom of this.

---

### Post by ron999 on 2007-08-05
Boot from the LiveCD.
Click on 'Places'.
Then 'Computer'.
Then select the drive.
Then look in Boot folder.
Then look in Grub folder.

---

### Post by fimbulvetr on 2007-08-05
> **ron999 said:**
> Boot from the LiveCD.
Click on 'Places'.
Then 'Computer'.
Then select the drive.
Then look in Boot folder.
Then look in Grub folder.

Oh that's cool. Does the livecd automatically mount existing hard drive partitions? So much for all the extra steps I'm making him do.

---

### Post by garyed on 2007-08-05
> **ron999 said:**
> Boot from the LiveCD.
Click on 'Places'.
Then 'Computer'.
Then select the drive.
Then look in Boot folder.
Then look in Grub folder.

Sorry but that doesn't work either.
In Computer it shows:
2 -  CD drives
1 - Floppy 
1 - File system 

Theres no Grub directory in the Boot directory.
In the file system the Foo directory that I made is there but its empty.

98 & Edgy were doing fine, but this all happened after an XP install.
Let me also say that my first XP install was succesful & could dual boot fine on this computer.
But XP was missing some things so I decided to reformat my first HD & reinstall XP.
That's when all this started.  I might have to have windows reformat my Linux drive & then try to install edgy again. I'll try anything at this point.

---

### Post by garyed on 2007-08-05
> **fimbulvetr said:**
> Hmm, ok. Go back into the terminal and paste the output of ```
dmesg
``` here. We'll get to the bottom of this.
I'm sorry I didn't see your reply.
Here's my output its long:

[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 0000000027f87000 (usable)
[17179569.184000]  BIOS-e820: 0000000027f87000 - 0000000027fa6000 (ACPI data)
[17179569.184000]  BIOS-e820: 0000000027fa6000 - 0000000028000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 639MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 163719
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 159623 pages, LIFO batch:31
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 DELL                                  ) @ 0x000fd730
[17179569.184000] ACPI: RSDT (v001 DELL   DIM 8100 0x00000005 ASL  0x00000061) @ 0x000fd744
[17179569.184000] ACPI: FADT (v001 DELL   DIM 8100 0x00000005 ASL  0x00000061) @ 0x000fd774
[17179569.184000] ACPI: SSDT (v001   DELL    st_ex 0x00001000 MSFT 0x0100000d) @ 0xfffe7158
[17179569.184000] ACPI: BOOT (v001 DELL    8100    0x00000005 ASL  0x00000061) @ 0x000fd7e8
[17179569.184000] ACPI: DSDT (v001   DELL    dt_ex 0x00001000 MSFT 0x0100000d) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x808
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 28000000:d7b00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash --
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (0150c000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[17179569.184000] Detected 1894.565 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179570.568000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179570.568000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179570.592000] Memory: 639080k/654876k available (1910k kernel code, 15272k reserved, 1070k data, 308k init, 0k highmem)
[17179570.592000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179570.672000] Calibrating delay using timer specific routine.. 3794.13 BogoMIPS (lpj=7588261)
[17179570.672000] Security Framework v1.0.0 initialized
[17179570.672000] SELinux:  Disabled at boot.
[17179570.672000] Mount-cache hash table entries: 512
[17179570.672000] CPU: After generic identify, caps: 3febf9ff 00000000 00000000 00000000 00000000 00000000 00000000
[17179570.672000] CPU: After vendor identify, caps: 3febf9ff 00000000 00000000 00000000 00000000 00000000 00000000
[17179570.672000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[17179570.672000] CPU: L2 cache: 256K
[17179570.672000] CPU: Hyper-Threading is disabled
[17179570.672000] CPU: After all inits, caps: 3febf9ff 00000000 00000000 00000080 00000000 00000000 00000000
[17179570.672000] Checking 'hlt' instruction... OK.
[17179570.688000] SMP alternatives: switching to UP code
[17179570.688000] Freeing SMP alternatives: 16k freed
[17179570.688000] checking if image is initramfs... it is
[17179571.400000] Freeing initrd memory: 5564k freed
[17179571.400000] ACPI: Core revision 20060707
[17179571.404000] ACPI: Looking for DSDT ... not found!
[17179571.428000] ACPI: setting ELCR to 0200 (from 0e08)
[17179571.428000] CPU0: Intel(R) Pentium(R) 4 CPU 1.90GHz stepping 02
[17179571.428000] SMP motherboard not detected.
[17179571.428000] Local APIC not detected. Using dummy APIC emulation.
[17179571.428000] Brought up 1 CPUs
[17179571.428000] migration_cost=0
[17179571.428000] NET: Registered protocol family 16
[17179571.428000] EISA bus registered
[17179571.428000] ACPI: bus type pci registered
[17179571.444000] PCI: PCI BIOS revision 2.10 entry at 0xfc10e, last bus=2
[17179571.444000] PCI: Using configuration type 1
[17179571.444000] Setting up standard PCI resources
[17179571.464000] ACPI: Interpreter enabled
[17179571.464000] ACPI: Using PIC for interrupt routing
[17179571.468000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179571.468000] PCI: Probing PCI hardware (bus 00)
[17179571.468000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179571.476000] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[17179571.476000] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
[17179571.476000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179571.480000] Boot video device is 0000:01:00.0
[17179571.480000] PCI: Transparent bridge - 0000:00:1e.0
[17179571.480000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179571.500000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[17179571.516000] ACPI: PCI Interrupt Link [LNKA] (IRQs *3 4 5 6 7 9 10 11 12 15)
[17179571.516000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[17179571.516000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[17179571.520000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[17179571.520000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[17179571.520000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[17179571.520000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[17179571.520000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[17179571.520000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179571.520000] pnp: PnP ACPI init
[17179571.548000] pnp: PnP ACPI: found 11 devices
[17179571.548000] PnPBIOS: Disabled by ACPI PNP
[17179571.548000] PCI: Using ACPI for IRQ routing
[17179571.548000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179571.560000] pnp: 00:0a: ioport range 0x800-0x85f could not be reserved
[17179571.560000] pnp: 00:0a: ioport range 0xc00-0xc7f has been reserved
[17179571.560000] pnp: 00:0a: ioport range 0x860-0x8ff could not be reserved
[17179571.564000] PCI: Bridge: 0000:00:01.0
[17179571.564000]   IO window: disabled.
[17179571.564000]   MEM window: fd000000-feffffff
[17179571.564000]   PREFETCH window: f0000000-f7ffffff
[17179571.564000] PCI: Bridge: 0000:00:1e.0
[17179571.564000]   IO window: e000-efff
[17179571.564000]   MEM window: ff100000-ff2fffff
[17179571.564000]   PREFETCH window: f8000000-f8ffffff
[17179571.564000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179571.564000] NET: Registered protocol family 2
[17179571.600000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179571.600000] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[17179571.600000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[17179571.600000] TCP: Hash tables configured (established 131072 bind 65536)
[17179571.600000] TCP reno registered
[17179571.600000] Simple Boot Flag at 0x7d set to 0x1
[17179571.604000] audit: initializing netlink socket (disabled)
[17179571.604000] audit(1186287546.604:1): initialized
[17179571.604000] VFS: Disk quotas dquot_6.5.1
[17179571.604000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179571.604000] Initializing Cryptographic API
[17179571.604000] io scheduler noop registered
[17179571.604000] io scheduler anticipatory registered
[17179571.604000] io scheduler deadline registered
[17179571.604000] io scheduler cfq registered (default)
[17179571.604000] isapnp: Scanning for PnP cards...
[17179571.956000] isapnp: No Plug & Play device found
[17179572.020000] Real Time Clock Driver v1.12ac
[17179572.020000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179572.020000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179572.024000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179572.024000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[17179572.024000] PCI: setting IRQ 11 as level-triggered
[17179572.024000] ACPI: PCI Interrupt 0000:02:09.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179572.024000] ACPI: PCI interrupt for device 0000:02:09.0 disabled
[17179572.024000] mice: PS/2 mouse device common for all mice
[17179572.024000] RAMDISK driver initialized: 16 RAM disks of 1048576K size 1024 blocksize
[17179572.024000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179572.024000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179572.024000] PNP: PS/2 Controller [PNP0303:KBD] at 0x60,0x64 irq 1
[17179572.024000] PNP: PS/2 controller doesn't have AUX irq; using default 12
[17179572.028000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179572.028000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179572.028000] EISA: Probing bus 0 at eisa.0
[17179572.028000] EISA: Detected 0 cards.
[17179572.028000] TCP bic registered
[17179572.028000] NET: Registered protocol family 1
[17179572.028000] NET: Registered protocol family 8
[17179572.028000] NET: Registered protocol family 20
[17179572.028000] Using IPI No-Shortcut mode
[17179572.028000] ACPI: (supports S0 S1 S3 S4 S5)
[17179572.028000] Freeing unused kernel memory: 308k freed
[17179572.152000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179573.168000] Capability LSM initialized
[17179574.080000] ICH2: IDE controller at PCI slot 0000:00:1f.1
[17179574.080000] ICH2: chipset revision 4
[17179574.080000] ICH2: not 100% native mode: will probe irqs later
[17179574.080000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:DMA
[17179574.080000]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:DMA
[17179574.080000] Probing IDE interface ide0...
[17179574.820000] hda: SAMSUNG DVD-ROM SD-612, ATAPI CD/DVD-ROM drive
[17179575.604000] hdb: LG CD-RW CED-8120B, ATAPI CD/DVD-ROM drive
[17179575.660000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179575.664000] Probing IDE interface ide1...
[17179575.952000] hdc: WDC WD800BB-00CAA0, ATA DISK drive
[17179576.232000] hdd: ST3300631A, ATA DISK drive
[17179576.288000] ide1 at 0x170-0x177,0x376 on irq 15
[17179576.308000] hda: ATAPI 32X DVD-ROM drive, 512kB Cache, UDMA(33)
[17179576.308000] Uniform CD-ROM driver Revision: 3.20
[17179576.312000] hdb: ATAPI 32X CD-ROM CD-R/RW drive, 8192kB Cache, DMA
[17179576.352000] hdc: max request size: 128KiB
[17179576.368000] hdc: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[17179576.368000] hdc: cache flushes not supported
[17179576.368000]  hdc: hdc1
[17179576.380000] hdd: max request size: 512KiB
[17179576.380000] hdd: 586072368 sectors (300069 MB) w/16384KiB Cache, CHS=36481/255/63, UDMA(100)
[17179576.380000] hdd: cache flushes supported
[17179576.380000]  hdd: hdd1 hdd2 < hdd5 >
[17179576.988000] usbcore: registered new driver usbfs
[17179576.988000] usbcore: registered new driver hub
[17179576.988000] USB Universal Host Controller Interface driver v3.0
[17179576.992000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[17179576.992000] ACPI: PCI Interrupt 0000:00:1f.2[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179576.992000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179576.992000] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[17179576.992000] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[17179576.992000] uhci_hcd 0000:00:1f.2: irq 11, io base 0x0000ff80
[17179576.992000] usb usb1: configuration #1 chosen from 1 choice
[17179576.992000] hub 1-0:1.0: USB hub found
[17179576.992000] hub 1-0:1.0: 2 ports detected
[17179577.096000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 9
[17179577.096000] PCI: setting IRQ 9 as level-triggered
[17179577.096000] ACPI: PCI Interrupt 0000:00:1f.4[C] -> Link [LNKH] -> GSI 9 (level, low) -> IRQ 9
[17179577.096000] PCI: Setting latency timer of device 0000:00:1f.4 to 64
[17179577.096000] uhci_hcd 0000:00:1f.4: UHCI Host Controller
[17179577.096000] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 2
[17179577.096000] uhci_hcd 0000:00:1f.4: irq 9, io base 0x0000ff60
[17179577.096000] usb usb2: configuration #1 chosen from 1 choice
[17179577.096000] hub 2-0:1.0: USB hub found
[17179577.096000] hub 2-0:1.0: 2 ports detected
[17179577.336000] usb 1-2: new low speed USB device using uhci_hcd and address 2
[17179577.508000] usb 1-2: configuration #1 chosen from 1 choice
[17179577.524000] usbcore: registered new driver hiddev
[17179577.540000] input: Logitech Optical USB Mouse as /class/input/input1
[17179577.540000] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1f.2-2
[17179577.540000] usbcore: registered new driver usbhid
[17179577.540000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179584.952000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17179585.012000] ISO 9660 Extensions: RRIP_1991A
[17179585.084000] Registering unionfs 1.1.4
[17179585.100000] loop: loaded (max 8 devices)
[17179585.236000] squashfs: version 3.0 (2006/03/15) Phillip Lougher
[17179622.304000] ACPI: PCI Interrupt 0000:02:0c.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179622.304000] 3c59x: Donald Becker and others. [www.scyld.com/network/vortex.html](www.scyld.com/network/vortex.html)
[17179622.304000] 0000:02:0c.0: 3Com PCI 3c905C Tornado at e8884c00.
[17179635.016000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179635.148000] Linux agpgart interface v0.101 (c) Dave Jones
[17179635.192000] input: PC Speaker as /class/input/input2
[17179635.616000] Floppy drive(s): fd0 is 1.44M
[17179635.632000] FDC 0 is a National Semiconductor PC87306
[17179635.732000] agpgart: Detected an Intel i850 Chipset.
[17179635.740000] agpgart: AGP aperture is 128M @ 0xe8000000
[17179635.880000] parport: PnPBIOS parport detected.
[17179635.880000] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,EPP,ECP]
[17179635.980000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179636.036000] hw_random: RNG not detected
[17179636.896000] ts: Compaq touchscreen protocol output
[17179636.928000] gameport: EMU10K1 is pci0000:02:0a.1/gameport0, io 0xecd8, speed 932kHz
[17179637.672000] ACPI: PCI Interrupt 0000:02:0a.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179637.924000] ACPI: PCI Interrupt 0000:02:0c.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179637.924000] eth0:  setting full-duplex.
[17179639.000000] NET: Registered protocol family 17
[17179641.220000] NET: Registered protocol family 10
[17179641.220000] lo: Disabled Privacy Extensions
[17179641.220000] IPv6 over IPv4 tunneling driver
[17179648.456000] ACPI: Power Button (FF) [PWRF]
[17179648.456000] ACPI: Power Button (CM) [VBTN]
[17179648.660000] ibm_acpi: ec object not found
[17179648.728000] pcc_acpi: loading...
[17179651.980000] eth0: no IPv6 routers present
[17179653.652000] lp0: using parport0 (interrupt-driven).
[17179653.784000] ppdev: user-space parallel port driver
[17179665.400000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179665.400000] apm: overridden by ACPI.
[17179684.896000] Bluetooth: Core ver 2.8
[17179684.896000] NET: Registered protocol family 31
[17179684.896000] Bluetooth: HCI device and connection manager initialized
[17179684.896000] Bluetooth: HCI socket layer initialized
[17179685.612000] Bluetooth: L2CAP ver 2.8
[17179685.612000] Bluetooth: L2CAP socket layer initialized
[17179685.880000] Bluetooth: RFCOMM socket layer initialized
[17179685.880000] Bluetooth: RFCOMM TTY layer initialized
[17179685.880000] Bluetooth: RFCOMM ver 1.7
[17180063.184000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[17180063.380000] JFS: nTxBlock = 5039, nTxLock = 40319
[17180063.616000] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[17180063.616000] SGI XFS Quota Management subsystem
[17180063.924000] end_request: I/O error, dev fd0, sector 0
[17180063.948000] end_request: I/O error, dev fd0, sector 0
[17189836.832000] end_request: I/O error, dev fd0, sector 0
[17190175.112000] end_request: I/O error, dev fd0, sector 0
[17190186.764000] end_request: I/O error, dev fd0, sector 0
[17195513.100000] FAT: Filesystem panic (dev hdd1)
[17195513.100000]     invalid access to FAT (entry 0x00c00015)
[17195513.100000]     File system has been set read-only
[17195657.288000] cramfs: wrong magic
[17195657.292000] attempt to access beyond end of device
[17195657.292000] hdd2: rw=0, want=66, limit=2
[17195657.292000] isofs_fill_super: bread failed, dev=hdd2, iso_blknum=16, block=32
[17195657.292000] SQUASHFS error: Can't find a SQUASHFS superblock on hdd2
[17195657.292000] attempt to access beyond end of device
[17195657.292000] hdd2: rw=0, want=4, limit=2
[17195657.296000] EXT2-fs: unable to read superblock
[17195657.296000] FAT: bogus number of reserved sectors
[17195657.296000] VFS: Can't find a valid FAT filesystem on dev hdd2.
[17195657.296000] NTFS-fs error (device hdd2): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17195657.296000] NTFS-fs error (device hdd2): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17195657.296000] NTFS-fs error (device hdd2): ntfs_fill_super(): Not an NTFS volume.
[17195657.300000] attempt to access beyond end of device
[17195657.300000] hdd2: rw=0, want=4, limit=2
[17195657.300000] EXT3-fs: unable to read superblock
[17195657.300000] attempt to access beyond end of device
[17195657.300000] hdd2: rw=0, want=72, limit=2
[17195657.300000] attempt to access beyond end of device
[17195657.300000] hdd2: rw=0, want=128, limit=2
[17195657.300000] attempt to access beyond end of device
[17195657.300000] hdd2: rw=0, want=18, limit=2
[17195657.300000] ReiserFS: hdd2: warning: sh-2006: read_super_block: bread failed (dev hdd2, block 8, size 1024)
[17195657.300000] attempt to access beyond end of device
[17195657.300000] hdd2: rw=0, want=130, limit=2
[17195657.300000] ReiserFS: hdd2: warning: sh-2006: read_super_block: bread failed (dev hdd2, block 64, size 1024)
[17195657.300000] ReiserFS: hdd2: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on hdd2
[17195657.304000] attempt to access beyond end of device
[17195657.304000] hdd2: rw=0, want=8, limit=2
ubuntu@ubuntu:~$

---

