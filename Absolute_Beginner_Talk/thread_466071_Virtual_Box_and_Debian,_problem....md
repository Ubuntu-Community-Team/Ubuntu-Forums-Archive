---
title: "Virtual Box and Debian, problem..."
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by starcraft.man on 2007-06-06
Hi there. I'm taking debian for a spin in Virtual Box, mostly out of curiosity. The installation went fine, I picked the Testing version since I wanted the kinda mid road between stable and unstable. When I booted up I promptly added myself to the sudoers file, then I updated it, was small. After that I installed build essential and then installed the latest linux headers for Debian (uname -r, then isntalled those headers). After all that I gave it a reset and when I got back in I mounted the VBoxaddition image and copied the files to my desktop, cd'ed to the container and then ran the install script as follows... can someone tell me what it means and what I have to install/do? I've never seen it before...

```
sudo sh ./VBoxLinuxAdditions.run
Verifying archive integrity... All good.
Uncompressing VirtualBox 1.3.8 Guest Additions for Linux installation..................................................................................................................................
VirtualBox 1.3.8 Guest Additions installation
Unable to insert a test module into your Linux kernel.  This may be because
the kernel was built with a different version of GCC to the one which is
currently installed, or because the kernel header files are incorrectly
installed.  The command 'dmesg' may provide you with more information.
Problems were found which would prevent the Guest Additions from installing.
Please correct these problems and try again.
```

I hope someone can help, I'll be back after lunch. It's probably something simple I didn't follow... Thanks in advance.

---

### Post by Seisen on 2007-06-06
What did dmesg say when you put it in the terminal also you can check out the virtual box forums and see if anybody else had the same problem.

---

### Post by starcraft.man on 2007-06-06
Here is the dmesg output, really just seems to be a hardware readout of the virtual machine. I dunno how helpful that is...

```
dmesg
Linux version 2.6.18-4-686 (Debian 2.6.18.dfsg.1-12) (waldi@debian.org) (gcc ver sion 4.1.2 20061115 (prerelease) (Debian 4.1.1-21)) #1 SMP Mon Mar 26 17:17:36 U TC 2007
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
 BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
 BIOS-e820: 000000001fff0000 - 0000000020000000 (ACPI data)
 BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
0MB HIGHMEM available.
511MB LOWMEM available.
On node 0 totalpages: 131056
  DMA zone: 4096 pages, LIFO batch:0
  Normal zone: 126960 pages, LIFO batch:31
DMI 2.3 present.
ACPI: RSDP (v002 VBox                                  ) @ 0x000e0000
ACPI: XSDT (v001 VBOX   VBOXXSDT 0x00000001 ASL  0x00000061) @ 0x1fff0030
ACPI: FADT (v004 VBOX   VBOXFACP 0x00000001 ASL  0x00000061) @ 0x1fff0060
ACPI: DSDT (v001  VBOXB VBOXBIOS 0x00000002 INTL 0x20060912) @ 0x00000000
ACPI: PM-Timer IO Port: 0x4008
Allocating PCI resources starting at 30000000 (gap: 20000000:dffc0000)
Detected 2391.916 MHz processor.
Built 1 zonelists.  Total pages: 131056
Kernel command line: root=/dev/hda1 ro
Found and enabled local APIC!
mapped APIC to ffffd000 (fee00000)
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Initializing CPU#0
PID hash table entries: 2048 (order: 11, 8192 bytes)
Console: colour VGA+ 80x25
Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Memory: 511408k/524224k available (1544k kernel code, 12176k reserved, 577k data , 196k init, 0k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay using timer specific routine.. 4332.11 BogoMIPS (lpj=8664236)
Security Framework v1.0.0 initialized
SELinux:  Disabled at boot.
Capability LSM initialized
Mount-cache hash table entries: 512
CPU: After generic identify, caps: 0780a3bd 00000000 00000000 00000000 00000000 00000000 00000000
CPU: After vendor identify, caps: 0780a3bd 00000000 00000000 00000000 00000000 0 0000000 00000000
CPU: Trace cache: 12K uops, L1 D cache: 8K
CPU: L2 cache: 512K
CPU: After all inits, caps: 0780a3bd 00000000 00000000 00000080 00000000 0000000 0 00000000
Intel machine check architecture supported.
Intel machine check reporting enabled on CPU#0.
Compat vDSO mapped to ffffe000.
Checking 'hlt' instruction... OK.
SMP alternatives: switching to UP code
Freeing SMP alternatives: 16k freed
ACPI: Core revision 20060707
ACPI: setting ELCR to 0200 (from 0e00)
CPU0: Intel(R) Pentium(R) 4 CPU 2.40GHz stepping 04
SMP motherboard not detected.
Brought up 1 CPUs
migration_cost=0
checking if image is initramfs... it is
Freeing initrd memory: 4999k freed
NET: Registered protocol family 16
ACPI: bus type pci registered
PCI: PCI BIOS revision 2.10 entry at 0xfbb30, last bus=0
PCI: Using configuration type 1
Setting up standard PCI resources
ACPI: Interpreter enabled
ACPI: Using PIC for interrupt routing
ACPI: PCI Root Bridge [PCI0] (0000:00)
PCI: Probing PCI hardware (bus 00)
Boot video device is 0000:00:02.0
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Link [LNKA] (IRQs 5 *9 10 11)
ACPI: PCI Interrupt Link [LNKB] (IRQs 5 9 10 11) *0, disabled.
ACPI: PCI Interrupt Link [LNKC] (IRQs 5 9 10 *11)
ACPI: PCI Interrupt Link [LNKD] (IRQs 5 9 *10 11)
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: PnP ACPI: found 5 devices
PnPBIOS: Disabled by ACPI PNP
PCI: Using ACPI for IRQ routing
PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
NET: Registered protocol family 2
IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
TCP established hash table entries: 16384 (order: 5, 131072 bytes)
TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
TCP: Hash tables configured (established 16384 bind 8192)
TCP reno registered
audit: initializing netlink socket (disabled)
audit(1181134523.712:1): initialized
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Initializing Cryptographic API
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered (default)
Limiting direct PCI/PCI transfers.
Activating ISA DMA hang workarounds.
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
mice: PS/2 mouse device common for all mice
TCP bic registered
NET: Registered protocol family 1
NET: Registered protocol family 17
NET: Registered protocol family 8
NET: Registered protocol family 20
Using IPI No-Shortcut mode
Time: tsc clocksource has been installed.
input: AT Translated Set 2 keyboard as /class/input/input0
ACPI: (supports S0 S5)
Freeing unused kernel memory: 196k freed
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
PIIX3: IDE controller at PCI slot 0000:00:01.1
PIIX3: chipset revision 0
PIIX3: not 100% native mode: will probe irqs later
    ide0: BM-DMA at 0xc000-0xc007, BIOS settings: hda:DMA, hdb:pio
    ide1: BM-DMA at 0xc008-0xc00f, BIOS settings: hdc:DMA, hdd:pio
Probing IDE interface ide0...
pcnet32.c:v1.32 18.Mar.2006 tsbogend@alpha.franken.de
Floppy drive(s): fd0 is 1.44M
FDC 0 is a S82078B
hda: VBOX HARDDISK, ATA DISK drive
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Probing IDE interface ide1...
hdc: VBOX CD-ROM, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
PCI: setting IRQ 11 as level-triggered
ACPI: PCI Interrupt 0000:00:03.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ  11
PCI: Setting latency timer of device 0000:00:03.0 to 64
pcnet32: PCnet/FAST III 79C973 at 0xc020, 08 00 27 e6 f9 9e assigned IRQ 11.
pcnet32: Found PHY 0000:0000 at address 0.
eth0: registered as PCnet/FAST III 79C973
pcnet32: 1 cards_found.
hda: max request size: 128KiB
hda: 16777216 sectors (8589 MB) w/256KiB Cache, CHS=16644/16/63, (U)DMA
hda: set_multmode: status=0x41 { DriveReady Error }
hda: set_multmode: error=0x04 { DriveStatusError }
ide: failed opcode was: 0xef
hda: cache flushes supported
 hda: hda1 hda2 < hda5 >
hdc: ATAPI 32X DVD-ROM drive, 128kB Cache, (U)DMA
Uniform CD-ROM driver Revision: 3.20
Attempting manual resume
kjournald starting.  Commit interval 5 seconds
EXT3-fs: mounted filesystem with ordered data mode.
input: PC Speaker as /class/input/input1
input: ImExPS/2 Generic Explorer Mouse as /class/input/input2
ts: Compaq touchscreen protocol output
ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 9
PCI: setting IRQ 9 as level-triggered
ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [LNKA] -> GSI 9 (level, low) -> IRQ 9
PCI: Setting latency timer of device 0000:00:05.0 to 64
intel8x0_measure_ac97_clock: measured 63838 usecs
intel8x0: measured clock 148328 rejected
intel8x0: clocking to 48000
Adding 1060248k swap on /dev/hda5.  Priority:-1 extents:1 across:1060248k
EXT3 FS on hda1, internal journal
loop: loaded (max 8 devices)
device-mapper: ioctl: 4.7.0-ioctl (2006-06-24) initialised: dm-devel@redhat.com
atkbd.c: Spurious NAK on isa0060/serio0. Some program might be trying access har dware directly.
eth0: link up, 100Mbps, full-duplex
NET: Registered protocol family 10
lo: Disabled Privacy Extensions
IPv6 over IPv4 tunneling driver
ACPI: AC Adapter [AC] (on-line)
ACPI: Power Button (FF) [PWRF]
lp: driver loaded but no devices found
ppdev: user-space parallel port driver
eth0: no IPv6 routers present
eth0: no IPv6 routers present
```

As for checking the forums, I did give em a quick look over and didn't see anyone really mentioning debian in any way, nor my particular problem... Maybe I will post there as well just to see if I get a response.

I'm sure I'm not the only person though thats tried Debian in VBox, no one else had this problem?

---

