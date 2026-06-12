---
title: "cannot mount cdrom"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by broshe on 2007-10-27
Hello
After upgrade from 7.04 to 7.10, the system does not recognize the CD reader.
When I insert a disk, I hear some noise, like it is working.
But, there is no CD icon on the screen.
When I try, in the terminal to give the command:
 sudo mount /media/cdrom
I get the message:
"special device /dev/hdb does not exist"

How can I get the system to recognize the CD, like it did before the upgrade ?

Thanks
Eli

---

### Post by taurus on 2007-10-27
Maybe it is now become /dev/sdb?  Look in dmesg to see if that's the case.

```
dmesg | more
```
Tab the Space bar for the next 24 lines.

---

### Post by broshe on 2007-10-27
I tried 
dmesg | more
I got a huge amount of lines that look like:
[134489.212000] Inbound IN=ppp0 OUT= MAC= SRC=212.235.15.21 DST=89.138.160.243 LEN=60 TOS=0x1C PREC=
0x20 TTL=62 ID=51378 PROTO=TCP SPT=50485 DPT=6662 WINDOW=5840 RES=0x00 SYN URGP=0 
[134490.284000] Unknown OutputIN= OUT=eth0 SRC=10.0.0.1 DST=10.0.0.138 LEN=328 TOS=0x00 PREC=0x00 TT
L=64 ID=0 DF PROTO=UDP SPT=68 DPT=67 LEN=308 


I could not notice anything that can be connected to my CD problem.


What next ?

Thanks
Eli

---

### Post by taurus on 2007-10-27
```
sudo more /var/log/messages
```

---

### Post by broshe on 2007-10-27
I tried:
sudo more /var/log/messges
Again, I got a huge amount of data. 
I restarted the computer and tried again. The last lines below seem to be somehow connected to the booting procedure:
Oct 27 22:48:45 ebrosh kernel: [   41.756000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [C187] -> GSI 11 (level, low) -> IRQ 11
Oct 27 22:48:45 ebrosh kernel: [   42.360000] es1968: clocking to 48000
Oct 27 22:48:45 ebrosh kernel: [   42.540000] Linux video capture interface: v2.00
Oct 27 22:48:45 ebrosh kernel: [   43.488000] lp0: using parport0 (interrupt-driven).
Oct 27 22:48:45 ebrosh kernel: [   43.664000] Adding 297160k swap on /dev/sda5.  Priority:-1 extents:1 across:297160k
Oct 27 22:48:45 ebrosh kernel: [   44.172000] EXT3 FS on sda2, internal journal
Oct 27 22:48:45 ebrosh kernel: [   46.376000] NET: Registered protocol family 10
Oct 27 22:48:45 ebrosh kernel: [   46.376000] lo: Disabled Privacy Extensions
Oct 27 22:48:45 ebrosh kernel: [   48.324000] ACPI: Battery Slot [C124] (battery present)
Oct 27 22:48:45 ebrosh kernel: [   48.324000] ACPI: Battery Slot [C125] (battery absent)
Oct 27 22:48:45 ebrosh kernel: [   48.324000] ACPI: Battery Slot [C126] (battery absent)
Oct 27 22:48:45 ebrosh kernel: [   48.812000] ACPI: ACPI Dock Station Driver 
Oct 27 22:48:45 ebrosh kernel: [   49.036000] input: Power Button (FF) as /class/input/input5
Oct 27 22:48:45 ebrosh kernel: [   49.036000] ACPI: Power Button (FF) [PWRF]
Oct 27 22:48:45 ebrosh kernel: [   49.072000] input: Sleep Button (CM) as /class/input/input6
Oct 27 22:48:45 ebrosh kernel: [   49.072000] ACPI: Sleep Button (CM) [C057]
Oct 27 22:48:45 ebrosh kernel: [   49.088000] input: Lid Switch as /class/input/input7
Oct 27 22:48:45 ebrosh kernel: [   49.088000] ACPI: Lid Switch [C1A5]
Oct 27 22:48:45 ebrosh kernel: [   49.884000] ACPI: AC Adapter [C11C] (on-line)
Oct 27 22:48:51 ebrosh kernel: [   57.644000] ppdev: user-space parallel port driver
Oct 27 22:48:52 ebrosh kernel: [   58.616000] audit(1193518131.928:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5122 profile="/usr/sbin/cupsd"
Oct 27 22:48:52 ebrosh kernel: [   59.052000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Oct 27 22:48:52 ebrosh kernel: [   59.052000] apm: overridden by ACPI.
Oct 27 22:49:12 ebrosh kernel: [   78.544000] Failure registering capabilities with primary security module.
Oct 27 22:49:12 ebrosh dhcdbd: Started up.


Can you see something there related to the cdrom ?


Thanks
Eli

---

### Post by taurus on 2007-10-27
Is that the whole /var/log/messages?  Looks kind of short (way short) to me.  Remember, you need to hit the Space bar to see the next 24 lines.

---

### Post by broshe on 2007-10-27
No, this is not the whole message.
I tried to post it all but it is too long.
I opened the /var/log/message file and I tried to search it for "cdrom" or "hdb".
I found nothing.

What do you suggest ?

Thanks
Eli

---

### Post by taurus on 2007-10-27
Probably sdb.  Look at each line and somewhere in there, there should be a few lines saying something about the make and model of your CD-ROM.

And if it is too long, maybe you want to clean it up and have the most recent version on it.

```
sudo echo /dev/null > sudo /var/log/messages
```
That would empty /var/log/messages so when you boot up, you have the latest message about your system.

---

### Post by broshe on 2007-10-27
I cleaned the messages, rebooted and here is the new /var/log/messages file:
Oct 27 23:42:35 ebrosh syslogd 1.4.1#21ubuntu3: restart.
Oct 27 23:42:36 ebrosh kernel: Inspecting /boot/System.map-2.6.22-14-generic
Oct 27 23:42:36 ebrosh kernel: Loaded 25445 symbols from /boot/System.map-2.6.22-14-generic.
Oct 27 23:42:36 ebrosh kernel: Symbols match kernel version 2.6.22.
Oct 27 23:42:36 ebrosh kernel: No module symbols loaded - kernel modules not enabled. 
Oct 27 23:42:36 ebrosh kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
Oct 27 23:42:36 ebrosh kernel: [    0.000000] BIOS-provided physical RAM map:
Oct 27 23:42:36 ebrosh kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Oct 27 23:42:36 ebrosh kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Oct 27 23:42:36 ebrosh kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Oct 27 23:42:36 ebrosh kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000000bff0000 (usable)
Oct 27 23:42:36 ebrosh kernel: [    0.000000]  BIOS-e820: 000000000bff0000 - 000000000bff3800 (reserved)
Oct 27 23:42:36 ebrosh kernel: [    0.000000]  BIOS-e820: 000000000bff3800 - 000000000c000000 (ACPI NVS)
Oct 27 23:42:36 ebrosh kernel: [    0.000000] 0MB HIGHMEM available.
Oct 27 23:42:36 ebrosh kernel: [    0.000000] 191MB LOWMEM available.
Oct 27 23:42:36 ebrosh kernel: [    0.000000] Zone PFN ranges:
Oct 27 23:42:36 ebrosh kernel: [    0.000000]   DMA             0 ->     4096
Oct 27 23:42:36 ebrosh kernel: [    0.000000]   Normal       4096 ->    49136
Oct 27 23:42:36 ebrosh kernel: [    0.000000]   HighMem     49136 ->    49136
Oct 27 23:42:36 ebrosh kernel: [    0.000000] early_node_map[1] active PFN ranges
Oct 27 23:42:36 ebrosh kernel: [    0.000000]     0:        0 ->    49136
Oct 27 23:42:36 ebrosh kernel: [    0.000000] DMI 2.3 present.
Oct 27 23:42:36 ebrosh kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F9970 checksum 0
Oct 27 23:42:36 ebrosh kernel: [    0.000000] ACPI: RSDP 000F9970, 0014 (r0 COMPAQ)
Oct 27 23:42:36 ebrosh kernel: [    0.000000] ACPI: RSDT 0BFF4800, 0028 (r1 COMPAQ RSDTBL          1 CPQ         1)
Oct 27 23:42:36 ebrosh kernel: [    0.000000] ACPI: FACP 0BFF4828, 0074 (r1 COMPAQ CPQB151  20000601 CPQ         1)
Oct 27 23:42:36 ebrosh kernel: [    0.000000] ACPI: DSDT 0BFF48A0, 856E (r1 COMPAQ ARMADAE7    10000 MSFT  100000C)
Oct 27 23:42:36 ebrosh kernel: [    0.000000] ACPI: FACS 0BFFFE80, 0040
Oct 27 23:42:36 ebrosh kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x5008
Oct 27 23:42:36 ebrosh kernel: [    0.000000] Allocating PCI resources starting at 10000000 (gap: 0c000000:f4000000)
Oct 27 23:42:36 ebrosh kernel: [    0.000000] Built 1 zonelists.  Total pages: 48753
Oct 27 23:42:36 ebrosh kernel: [    0.000000] Kernel command line: root=UUID=c7bf1617-b021-46a4-a700-919efd5135ea ro quiet splash
Oct 27 23:42:36 ebrosh kernel: [    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
Oct 27 23:42:36 ebrosh kernel: [    0.000000] Enabling fast FPU save and restore... done.
Oct 27 23:42:36 ebrosh kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Oct 27 23:42:36 ebrosh kernel: [    0.000000] Initializing CPU#0
Oct 27 23:42:36 ebrosh kernel: [    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
Oct 27 23:42:36 ebrosh kernel: [    0.000000] Detected 596.936 MHz processor.
Oct 27 23:42:36 ebrosh kernel: [   20.115224] Console: colour VGA+ 80x25
Oct 27 23:42:36 ebrosh kernel: [   20.115719] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
Oct 27 23:42:36 ebrosh kernel: [   20.116249] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
Oct 27 23:42:36 ebrosh kernel: [   20.137378] Memory: 183308k/196544k available (2015k kernel code, 12740k reserved, 916k data, 364k init, 0k highmem)
Oct 27 23:42:36 ebrosh kernel: [   20.137414] virtual kernel memory layout:
Oct 27 23:42:36 ebrosh kernel: [   20.137418]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
Oct 27 23:42:36 ebrosh kernel: [   20.137423]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Oct 27 23:42:36 ebrosh kernel: [   20.137428]     vmalloc : 0xcc800000 - 0xff7fe000   ( 815 MB)
Oct 27 23:42:36 ebrosh kernel: [   20.137433]     lowmem  : 0xc0000000 - 0xcbff0000   ( 191 MB)
Oct 27 23:42:36 ebrosh kernel: [   20.137438]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
Oct 27 23:42:36 ebrosh kernel: [   20.137443]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
Oct 27 23:42:36 ebrosh kernel: [   20.137448]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
Oct 27 23:42:36 ebrosh kernel: [   20.137459] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Oct 27 23:42:36 ebrosh kernel: [   20.137572] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Oct 27 23:42:36 ebrosh kernel: [   20.217589] Calibrating delay using timer specific routine.. 1194.98 BogoMIPS (lpj=2389979)
Oct 27 23:42:36 ebrosh kernel: [   20.217665] Security Framework v1.0.0 initialized
Oct 27 23:42:36 ebrosh kernel: [   20.217686] SELinux:  Disabled at boot.
Oct 27 23:42:36 ebrosh kernel: [   20.217734] Mount-cache hash table entries: 512
Oct 27 23:42:36 ebrosh kernel: [   20.218107] CPU: L1 I cache: 16K, L1 D cache: 16K
Oct 27 23:42:36 ebrosh kernel: [   20.218116] CPU: L2 cache: 256K
Oct 27 23:42:36 ebrosh kernel: [   20.218157] Compat vDSO mapped to ffffe000.
Oct 27 23:42:36 ebrosh kernel: [   20.218195] Checking 'hlt' instruction... OK.
Oct 27 23:42:36 ebrosh kernel: [   20.233858] SMP alternatives: switching to UP code
Oct 27 23:42:36 ebrosh kernel: [   20.234327] Freeing SMP alternatives: 11k freed
Oct 27 23:42:36 ebrosh kernel: [   20.235166] Early unpacking initramfs... done
Oct 27 23:42:36 ebrosh kernel: [   21.302786] ACPI: Core revision 20070126
Oct 27 23:42:36 ebrosh kernel: [   21.303258] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Oct 27 23:42:36 ebrosh kernel: [   21.312423] ACPI: setting ELCR to 0200 (from 0800)
Oct 27 23:42:36 ebrosh kernel: [   21.315943] CPU0: Intel Pentium III (Coppermine) stepping 03
Oct 27 23:42:36 ebrosh kernel: [   21.315962] SMP motherboard not detected.
Oct 27 23:42:36 ebrosh kernel: [   21.315970] Local APIC not detected. Using dummy APIC emulation.
Oct 27 23:42:36 ebrosh kernel: [   21.316086] Brought up 1 CPUs
Oct 27 23:42:36 ebrosh kernel: [   21.316446] Booting paravirtualized kernel on bare hardware
Oct 27 23:42:36 ebrosh kernel: [   21.316579] Time: 23:41:44  Date: 09/27/107
Oct 27 23:42:36 ebrosh kernel: [   21.316657] NET: Registered protocol family 16
Oct 27 23:42:36 ebrosh kernel: [   21.316957] EISA bus registered
Oct 27 23:42:36 ebrosh kernel: [   21.316986] ACPI: bus type pci registered
Oct 27 23:42:36 ebrosh kernel: [   21.320939] PCI: PCI BIOS revision 2.10 entry at 0xf0478, last bus=1
Oct 27 23:42:36 ebrosh kernel: [   21.320948] PCI: Using configuration type 1
Oct 27 23:42:36 ebrosh kernel: [   21.320955] Setting up standard PCI resources
Oct 27 23:42:36 ebrosh kernel: [   21.367874] ACPI: Interpreter enabled
Oct 27 23:42:36 ebrosh kernel: [   21.367890] ACPI: (supports S0 S1 S3 S4 S5)
Oct 27 23:42:36 ebrosh kernel: [   21.367951] ACPI: Using PIC for interrupt routing
Oct 27 23:42:36 ebrosh kernel: [   21.407348] ACPI: PCI Root Bridge [C005] (0000:00)
Oct 27 23:42:36 ebrosh kernel: [   21.407926] PCI quirk: region 5000-503f claimed by PIIX4 ACPI
Oct 27 23:42:36 ebrosh kernel: [   21.407939] PCI quirk: region 4000-400f claimed by PIIX4 SMB
Oct 27 23:42:36 ebrosh kernel: [   21.407954] PIIX4 devres I PIO at 00e0-00e3
Oct 27 23:42:36 ebrosh kernel: [   21.407963] PIIX4 devres J PIO at 00f8-00fb
Oct 27 23:42:36 ebrosh kernel: [   21.408078] PCI: Firmware left 0000:00:09.0 e100 interrupts enabled, disabling
Oct 27 23:42:36 ebrosh kernel: [   21.452731] ACPI: PCI Interrupt Link [C180] (IRQs *11)
Oct 27 23:42:36 ebrosh kernel: [   21.453201] ACPI: PCI Interrupt Link [C186] (IRQs 11) *0, disabled.
Oct 27 23:42:36 ebrosh kernel: [   21.453746] ACPI: PCI Interrupt Link [C187] (IRQs *11)
Oct 27 23:42:36 ebrosh kernel: [   21.454266] ACPI: PCI Interrupt Link [C188] (IRQs *11)
Oct 27 23:42:36 ebrosh kernel: [   21.454743] ACPI: Power Resource [C147] (on)
Oct 27 23:42:36 ebrosh kernel: [   21.454904] ACPI: Power Resource [C0FC] (on)
Oct 27 23:42:36 ebrosh kernel: [   21.455218] ACPI: Power Resource [C1CE] (on)
Oct 27 23:42:36 ebrosh kernel: [   21.455457] ACPI: Power Resource [C1D4] (on)
Oct 27 23:42:36 ebrosh kernel: [   21.457310] ACPI: Power Resource [C19C] (off)
Oct 27 23:42:36 ebrosh kernel: [   21.459288] ACPI: Power Resource [C19E] (off)
Oct 27 23:42:36 ebrosh kernel: [   21.461382] ACPI: Power Resource [C1A0] (off)
Oct 27 23:42:36 ebrosh kernel: [   21.461410] Linux Plug and Play Support v0.97 (c) Adam Belay
Oct 27 23:42:36 ebrosh kernel: [   21.461465] pnp: PnP ACPI init
Oct 27 23:42:36 ebrosh kernel: [   21.461499] ACPI: bus type pnp registered
Oct 27 23:42:36 ebrosh kernel: [   21.497531] pnp: Device 00:03 disabled.
Oct 27 23:42:36 ebrosh kernel: [   21.507054] pnp: Device 00:03 activated.
Oct 27 23:42:36 ebrosh kernel: [   21.513545] pnp: Device 00:03 disabled.
Oct 27 23:42:36 ebrosh kernel: [   21.522958] pnp: Device 00:03 activated.
Oct 27 23:42:36 ebrosh kernel: [   21.537154] pnp: PnP ACPI: found 15 devices
Oct 27 23:42:36 ebrosh kernel: [   21.537165] ACPI: ACPI bus type pnp unregistered
Oct 27 23:42:36 ebrosh kernel: [   21.537177] PnPBIOS: Disabled by ACPI PNP
Oct 27 23:42:36 ebrosh kernel: [   21.537386] PCI: Using ACPI for IRQ routing
Oct 27 23:42:36 ebrosh kernel: [   21.537397] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Oct 27 23:42:36 ebrosh kernel: [   21.580251] NET: Registered protocol family 8
Oct 27 23:42:36 ebrosh kernel: [   21.580260] NET: Registered protocol family 20
Oct 27 23:42:36 ebrosh kernel: [   21.580508] pnp: 00:0c: ioport range 0x4d0-0x4d1 has been reserved
Oct 27 23:42:36 ebrosh kernel: [   21.580520] pnp: 00:0c: ioport range 0x800-0x87f has been reserved
Oct 27 23:42:36 ebrosh kernel: [   21.580531] pnp: 00:0c: ioport range 0x4000-0x400f has been reserved
Oct 27 23:42:36 ebrosh kernel: [   21.580542] pnp: 00:0c: ioport range 0x5000-0x5063 could not be reserved
Oct 27 23:42:36 ebrosh kernel: [   21.580552] pnp: 00:0c: ioport range 0x6004-0x6005 has been reserved
Oct 27 23:42:36 ebrosh kernel: [   21.580563] pnp: 00:0c: ioport range 0xf000-0xf0cf has been reserved
Oct 27 23:42:36 ebrosh kernel: [   21.580581] pnp: 00:0d: iomem range 0xd1800-0xd3fff has been reserved
Oct 27 23:42:36 ebrosh kernel: [   21.580592] pnp: 00:0d: iomem range 0xfff80000-0xffffffff has been reserved
Oct 27 23:42:36 ebrosh kernel: [   21.580611] pnp: 00:0e: iomem range 0x0-0x9ffff could not be reserved
Oct 27 23:42:36 ebrosh kernel: [   21.580622] pnp: 00:0e: iomem range 0xf0000-0xfffff could not be reserved
Oct 27 23:42:36 ebrosh kernel: [   21.580633] pnp: 00:0e: iomem range 0x100000-0xbffffff could not be reserved
Oct 27 23:42:36 ebrosh kernel: [   21.581293] Time: tsc clocksource has been installed.
Oct 27 23:42:36 ebrosh kernel: [   21.611652] PCI: Bridge: 0000:00:01.0
Oct 27 23:42:36 ebrosh kernel: [   21.611662]   IO window: 2000-2fff
Oct 27 23:42:36 ebrosh kernel: [   21.611674]   MEM window: 40000000-410fffff
Oct 27 23:42:36 ebrosh kernel: [   21.611684]   PREFETCH window: 20000000-200fffff
Oct 27 23:42:36 ebrosh kernel: [   21.611695] PCI: Bus 2, cardbus bridge: 0000:00:04.0
Oct 27 23:42:36 ebrosh kernel: [   21.611703]   IO window: 00001000-000010ff
Oct 27 23:42:36 ebrosh kernel: [   21.611713]   IO window: 00001400-000014ff
Oct 27 23:42:36 ebrosh kernel: [   21.611723]   PREFETCH window: 10000000-13ffffff
Oct 27 23:42:36 ebrosh kernel: [   21.611733]   MEM window: 14000000-17ffffff
Oct 27 23:42:36 ebrosh kernel: [   21.611742] PCI: Bus 6, cardbus bridge: 0000:00:04.1
Oct 27 23:42:36 ebrosh kernel: [   21.611750]   IO window: 00001800-000018ff
Oct 27 23:42:36 ebrosh kernel: [   21.611759]   IO window: 00001c00-00001cff
Oct 27 23:42:36 ebrosh kernel: [   21.611769]   PREFETCH window: 18000000-1bffffff
Oct 27 23:42:36 ebrosh kernel: [   21.611780]   MEM window: 1c000000-1fffffff
Oct 27 23:42:36 ebrosh kernel: [   21.612672] ACPI: PCI Interrupt Link [C180] enabled at IRQ 11
Oct 27 23:42:36 ebrosh kernel: [   21.612692] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [C180] -> GSI 11 (level, low) -> IRQ 11
Oct 27 23:42:36 ebrosh kernel: [   21.612725] ACPI: PCI Interrupt 0000:00:04.1[A] -> Link [C180] -> GSI 11 (level, low) -> IRQ 11
Oct 27 23:42:36 ebrosh kernel: [   21.612773] NET: Registered protocol family 2
Oct 27 23:42:36 ebrosh kernel: [   21.649410] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
Oct 27 23:42:36 ebrosh kernel: [   21.649529] TCP established hash table entries: 8192 (order: 4, 98304 bytes)
Oct 27 23:42:36 ebrosh kernel: [   21.649799] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
Oct 27 23:42:36 ebrosh kernel: [   21.649995] TCP: Hash tables configured (established 8192 bind 8192)
Oct 27 23:42:36 ebrosh kernel: [   21.650004] TCP reno registered
Oct 27 23:42:36 ebrosh kernel: [   21.661700] checking if image is initramfs...<6>Switched to high resolution mode on CPU 0
Oct 27 23:42:36 ebrosh kernel: [   22.600247]  it is
Oct 27 23:42:36 ebrosh kernel: [   23.710902] Freeing initrd memory: 7122k freed
Oct 27 23:42:36 ebrosh kernel: [   23.713360] audit: initializing netlink socket (disabled)
Oct 27 23:42:36 ebrosh kernel: [   23.713398] audit(1193528506.448:1): initialized
Oct 27 23:42:36 ebrosh kernel: [   23.720900] VFS: Disk quotas dquot_6.5.1
Oct 27 23:42:36 ebrosh kernel: [   23.721130] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Oct 27 23:42:36 ebrosh kernel: [   23.721462] io scheduler noop registered
Oct 27 23:42:36 ebrosh kernel: [   23.721471] io scheduler anticipatory registered
Oct 27 23:42:36 ebrosh kernel: [   23.721479] io scheduler deadline registered
Oct 27 23:42:36 ebrosh kernel: [   23.721551] io scheduler cfq registered (default)
Oct 27 23:42:36 ebrosh kernel: [   23.721580] Limiting direct PCI/PCI transfers.
Oct 27 23:42:36 ebrosh kernel: [   23.722093] isapnp: Scanning for PnP cards...
Oct 27 23:42:36 ebrosh kernel: [   24.075323] isapnp: No Plug & Play device found
Oct 27 23:42:36 ebrosh kernel: [   24.172347] Real Time Clock Driver v1.12ac
Oct 27 23:42:36 ebrosh kernel: [   24.172811] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Oct 27 23:42:36 ebrosh kernel: [   24.172973] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Oct 27 23:42:36 ebrosh kernel: [   24.174832] 00:01: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Oct 27 23:42:36 ebrosh kernel: [   24.176993] ACPI: PCI Interrupt Link [C187] enabled at IRQ 11
Oct 27 23:42:36 ebrosh kernel: [   24.177007] ACPI: PCI Interrupt 0000:00:09.1[A] -> Link [C187] -> GSI 11 (level, low) -> IRQ 11
Oct 27 23:42:36 ebrosh kernel: [   24.179518] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Oct 27 23:42:36 ebrosh kernel: [   24.180168] input: Macintosh mouse button emulation as /class/input/input0
Oct 27 23:42:36 ebrosh kernel: [   24.180561] PNP: PS/2 Controller [PNP0303:C0F9,PNP0f0e:C0FA] at 0x60,0x64 irq 1,12
Oct 27 23:42:36 ebrosh kernel: [   24.182777] i8042.c: Detected active multiplexing controller, rev 1.0.
Oct 27 23:42:36 ebrosh kernel: [   24.183862] serio: i8042 KBD port at 0x60,0x64 irq 1
Oct 27 23:42:36 ebrosh kernel: [   24.183877] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Oct 27 23:42:36 ebrosh kernel: [   24.183887] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Oct 27 23:42:36 ebrosh kernel: [   24.183897] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Oct 27 23:42:36 ebrosh kernel: [   24.183907] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Oct 27 23:42:36 ebrosh kernel: [   24.184531] mice: PS/2 mouse device common for all mice
Oct 27 23:42:36 ebrosh kernel: [   24.185049] EISA: Probing bus 0 at eisa.0
Oct 27 23:42:36 ebrosh kernel: [   24.185071] Cannot allocate resource for EISA slot 1
Oct 27 23:42:36 ebrosh kernel: [   24.185080] Cannot allocate resource for EISA slot 2
Oct 27 23:42:36 ebrosh kernel: [   24.185088] Cannot allocate resource for EISA slot 3
Oct 27 23:42:36 ebrosh kernel: [   24.185097] Cannot allocate resource for EISA slot 4
Oct 27 23:42:36 ebrosh kernel: [   24.185105] Cannot allocate resource for EISA slot 5
Oct 27 23:42:36 ebrosh kernel: [   24.185113] Cannot allocate resource for EISA slot 6
Oct 27 23:42:36 ebrosh kernel: [   24.185129] EISA: Detected 0 cards.
Oct 27 23:42:36 ebrosh kernel: [   24.185432] TCP cubic registered
Oct 27 23:42:36 ebrosh kernel: [   24.185480] NET: Registered protocol family 1
Oct 27 23:42:36 ebrosh kernel: [   24.185556] Using IPI No-Shortcut mode
Oct 27 23:42:36 ebrosh kernel: [   24.186067]   Magic number: 11:627:707
Oct 27 23:42:36 ebrosh kernel: [   24.187623] Freeing unused kernel memory: 364k freed
Oct 27 23:42:36 ebrosh kernel: [   24.220606] input: AT Translated Set 2 keyboard as /class/input/input1
Oct 27 23:42:36 ebrosh kernel: [   25.858123] AppArmor: AppArmor initialized<5>audit(1193528508.448:2):  type=1505 info="AppArmor initialized" pid=1195
Oct 27 23:42:36 ebrosh kernel: [   26.185770] fuse init (API version 7.8)
Oct 27 23:42:36 ebrosh kernel: [   26.336326] Failure registering capabilities with primary security module.
Oct 27 23:42:36 ebrosh kernel: [   26.369676] ACPI: Transitioning device [C19A] to D3
Oct 27 23:42:36 ebrosh kernel: [   26.369688] ACPI: Transitioning device [C19A] to D3
Oct 27 23:42:36 ebrosh kernel: [   26.369701] ACPI: Fan [C19A] (off)
Oct 27 23:42:36 ebrosh kernel: [   26.373717] ACPI: Transitioning device [C19D] to D3
Oct 27 23:42:36 ebrosh kernel: [   26.373727] ACPI: Transitioning device [C19D] to D3
Oct 27 23:42:36 ebrosh kernel: [   26.373737] ACPI: Fan [C19D] (off)
Oct 27 23:42:36 ebrosh kernel: [   26.377740] ACPI: Transitioning device [C19F] to D3
Oct 27 23:42:36 ebrosh kernel: [   26.377749] ACPI: Transitioning device [C19F] to D3
Oct 27 23:42:36 ebrosh kernel: [   26.377760] ACPI: Fan [C19F] (off)
Oct 27 23:42:36 ebrosh kernel: [   26.396649] ACPI: CPU0 (power states: C1[C1] C2[C2])
Oct 27 23:42:36 ebrosh kernel: [   26.396666] ACPI: Processor [C0D5] (supports 8 throttling states)
Oct 27 23:42:36 ebrosh kernel: [   26.417882] ACPI: Thermal Zone [C19B] (60 C)
Oct 27 23:42:36 ebrosh kernel: [   28.547461] SCSI subsystem initialized
Oct 27 23:42:36 ebrosh kernel: [   28.587491] scsi0 : ata_piix
Oct 27 23:42:36 ebrosh kernel: [   28.587627] scsi1 : ata_piix
Oct 27 23:42:36 ebrosh kernel: [   28.587845] ata1: PATA max UDMA/33 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00013420 irq 14
Oct 27 23:42:36 ebrosh kernel: [   28.587859] ata2: PATA max UDMA/33 cmd 0x00010170 ctl 0x00010376 bmdma 0x00013428 irq 15
Oct 27 23:42:36 ebrosh kernel: [   28.621208] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k4-NAPI
Oct 27 23:42:36 ebrosh kernel: [   28.621220] e100: Copyright(c) 1999-2006 Intel Corporation
Oct 27 23:42:36 ebrosh kernel: [   28.718910] usbcore: registered new interface driver usbfs
Oct 27 23:42:36 ebrosh kernel: [   28.718982] usbcore: registered new interface driver hub
Oct 27 23:42:36 ebrosh kernel: [   28.719055] usbcore: registered new device driver usb
Oct 27 23:42:36 ebrosh kernel: [   28.723675] USB Universal Host Controller Interface driver v3.0
Oct 27 23:42:36 ebrosh kernel: [   29.125304] Floppy drive(s): fd0 is 1.44M
Oct 27 23:42:36 ebrosh kernel: [   29.282808] FDC 0 is a post-1991 82077
Oct 27 23:42:36 ebrosh kernel: [   29.364338] ata1.00: ATA-4: IBM-DARA-212000, AR4OA5AA, max UDMA/66
Oct 27 23:42:36 ebrosh kernel: [   29.364354] ata1.00: 23579136 sectors, multi 16: LBA 
Oct 27 23:42:36 ebrosh kernel: [   29.407123] ata1.00: configured for UDMA/33
Oct 27 23:42:36 ebrosh kernel: [   29.415008] scsi 0:0:0:0: Direct-Access     ATA      IBM-DARA-212000  AR4O PQ: 0 ANSI: 5
Oct 27 23:42:36 ebrosh kernel: [   29.423840] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [C187] -> GSI 11 (level, low) -> IRQ 11
Oct 27 23:42:36 ebrosh kernel: [   29.512427] e100: eth0: e100_probe: addr 0x41280000, irq 11, MAC addr 00:D0:59:1B:4F:BF
Oct 27 23:42:36 ebrosh kernel: [   29.513564] ACPI: PCI Interrupt Link [C188] enabled at IRQ 11
Oct 27 23:42:36 ebrosh kernel: [   29.513576] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [C188] -> GSI 11 (level, low) -> IRQ 11
Oct 27 23:42:36 ebrosh kernel: [   29.513604] uhci_hcd 0000:00:07.2: UHCI Host Controller
Oct 27 23:42:36 ebrosh kernel: [   29.513991] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
Oct 27 23:42:36 ebrosh kernel: [   29.514040] uhci_hcd 0000:00:07.2: irq 11, io base 0x00003400
Oct 27 23:42:36 ebrosh kernel: [   29.514437] usb usb1: configuration #1 chosen from 1 choice
Oct 27 23:42:36 ebrosh kernel: [   29.514541] hub 1-0:1.0: USB hub found
Oct 27 23:42:36 ebrosh kernel: [   29.514567] hub 1-0:1.0: 2 ports detected
Oct 27 23:42:36 ebrosh kernel: [   29.661283] sd 0:0:0:0: [sda] 23579136 512-byte hardware sectors (12073 MB)
Oct 27 23:42:36 ebrosh kernel: [   29.661359] sd 0:0:0:0: [sda] Write Protect is off
Oct 27 23:42:36 ebrosh kernel: [   29.661426] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 27 23:42:36 ebrosh kernel: [   29.661593] sd 0:0:0:0: [sda] 23579136 512-byte hardware sectors (12073 MB)
Oct 27 23:42:36 ebrosh kernel: [   29.661627] sd 0:0:0:0: [sda] Write Protect is off
Oct 27 23:42:36 ebrosh kernel: [   29.661691] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 27 23:42:36 ebrosh kernel: [   29.661707]  sda: sda1 sda2 sda3 < sda5 >
Oct 27 23:42:36 ebrosh kernel: [   29.739174] sd 0:0:0:0: [sda] Attached SCSI disk
Oct 27 23:42:36 ebrosh kernel: [   29.758515] sd 0:0:0:0: Attached scsi generic sg0 type 0
Oct 27 23:42:36 ebrosh kernel: [   29.854784] usb 1-1: new full speed USB device using uhci_hcd and address 2
Oct 27 23:42:36 ebrosh kernel: [    9.724000] Marking TSC unstable due to: possible TSC halt in C2.
Oct 27 23:42:36 ebrosh kernel: [    9.728000] Time: acpi_pm clocksource has been installed.
Oct 27 23:42:36 ebrosh kernel: [    9.884000] usb 1-1: configuration #1 chosen from 1 choice
Oct 27 23:42:36 ebrosh kernel: [    9.936000] usbcore: registered new interface driver libusual
Oct 27 23:42:36 ebrosh kernel: [    9.968000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Oct 27 23:42:36 ebrosh kernel: [    9.968000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Oct 27 23:42:36 ebrosh kernel: [    9.976000] Clocksource tsc unstable (delta = -103918991 ns)
Oct 27 23:42:36 ebrosh kernel: [    9.984000] Initializing USB Mass Storage driver...
Oct 27 23:42:36 ebrosh kernel: [    9.984000] scsi2 : SCSI emulation for USB Mass Storage devices
Oct 27 23:42:36 ebrosh kernel: [    9.984000] usbcore: registered new interface driver usb-storage
Oct 27 23:42:36 ebrosh kernel: [    9.984000] USB Mass Storage support registered.
Oct 27 23:42:36 ebrosh kernel: [   10.344000] Attempting manual resume
Oct 27 23:42:36 ebrosh kernel: [   10.440000] kjournald starting.  Commit interval 5 seconds
Oct 27 23:42:36 ebrosh kernel: [   10.440000] EXT3-fs: mounted filesystem with ordered data mode.
Oct 27 23:42:36 ebrosh kernel: [   14.988000] scsi 2:0:0:0: Direct-Access     Ut163    USB2FlashStorage 1.00 PQ: 0 ANSI: 2
Oct 27 23:42:36 ebrosh kernel: [   14.992000] sd 2:0:0:0: [sdb] 2015231 512-byte hardware sectors (1032 MB)
Oct 27 23:42:36 ebrosh kernel: [   14.996000] sd 2:0:0:0: [sdb] Write Protect is off
Oct 27 23:42:36 ebrosh kernel: [   15.008000] sd 2:0:0:0: [sdb] 2015231 512-byte hardware sectors (1032 MB)
Oct 27 23:42:36 ebrosh kernel: [   15.012000] sd 2:0:0:0: [sdb] Write Protect is off
Oct 27 23:42:36 ebrosh kernel: [   15.012000]  sdb: sdb1
Oct 27 23:42:36 ebrosh kernel: [   15.124000] sd 2:0:0:0: [sdb] Attached SCSI removable disk
Oct 27 23:42:36 ebrosh kernel: [   15.124000] sd 2:0:0:0: Attached scsi generic sg1 type 0
Oct 27 23:42:36 ebrosh kernel: [   30.292000] ip_tables: (C) 2000-2006 Netfilter Core Team
Oct 27 23:42:36 ebrosh kernel: [   30.388000] Netfilter messages via NETLINK v0.30.
Oct 27 23:42:36 ebrosh kernel: [   30.424000] nf_conntrack version 0.5.0 (1535 buckets, 12280 max)
Oct 27 23:42:36 ebrosh kernel: [   32.144000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
Oct 27 23:42:36 ebrosh kernel: [   34.128000] NET: Registered protocol family 17
Oct 27 23:42:36 ebrosh kernel: [   35.368000] Yenta: CardBus bridge found at 0000:00:04.0 [0e11:b121]
Oct 27 23:42:36 ebrosh kernel: [   35.368000] Yenta: Using CSCINT to route CSC interrupts to PCI
Oct 27 23:42:36 ebrosh kernel: [   35.368000] Yenta: Routing CardBus interrupts to PCI
Oct 27 23:42:36 ebrosh kernel: [   35.368000] Yenta TI: socket 0000:00:04.0, mfunc 0x01001c72, devctl 0x64
Oct 27 23:42:36 ebrosh kernel: [   35.392000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Oct 27 23:42:36 ebrosh kernel: [   35.600000] Yenta: ISA IRQ mask 0x04b8, PCI irq 11
Oct 27 23:42:36 ebrosh kernel: [   35.600000] Socket status: 30000006
Oct 27 23:42:36 ebrosh kernel: [   35.600000] Yenta: CardBus bridge found at 0000:00:04.1 [0e11:b121]
Oct 27 23:42:36 ebrosh kernel: [   35.600000] Yenta: Using CSCINT to route CSC interrupts to PCI
Oct 27 23:42:36 ebrosh kernel: [   35.600000] Yenta: Routing CardBus interrupts to PCI
Oct 27 23:42:36 ebrosh kernel: [   35.600000] Yenta TI: socket 0000:00:04.1, mfunc 0x01001c72, devctl 0x64
Oct 27 23:42:36 ebrosh kernel: [   35.736000] Linux agpgart interface v0.102 (c) Dave Jones
Oct 27 23:42:36 ebrosh kernel: [   35.840000] Yenta: ISA IRQ mask 0x04b8, PCI irq 11
Oct 27 23:42:36 ebrosh kernel: [   35.840000] Socket status: 30000006
Oct 27 23:42:36 ebrosh kernel: [   35.864000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Oct 27 23:42:36 ebrosh kernel: [   35.880000] agpgart: Detected an Intel 440BX Chipset.
Oct 27 23:42:36 ebrosh kernel: [   35.884000] agpgart: AGP aperture is 64M @ 0x50000000
Oct 27 23:42:36 ebrosh kernel: [   39.248000] input: ImPS/2 Generic Wheel Mouse as /class/input/input2
Oct 27 23:42:36 ebrosh kernel: [   39.328000] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
Oct 27 23:42:36 ebrosh kernel: [   39.884000] Synaptics Touchpad, model: 1, fw: 5.1, id: 0x1640b1, caps: 0x804713/0x0
Oct 27 23:42:36 ebrosh kernel: [   39.912000] NET: Registered protocol family 23
Oct 27 23:42:36 ebrosh kernel: [   39.944000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
Oct 27 23:42:36 ebrosh kernel: [   39.984000] parport_pc 00:04: reported by Plug and Play ACPI
Oct 27 23:42:36 ebrosh kernel: [   39.984000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
Oct 27 23:42:36 ebrosh kernel: [   39.996000] input: PC Speaker as /class/input/input4
Oct 27 23:42:36 ebrosh kernel: [   40.024000] found SMC SuperIO Chip (devid=0x0a rev=00 base=0x00e0): FDC37N971
Oct 27 23:42:36 ebrosh kernel: [   40.024000] smsc_ircc_present(), addr 0x03e8 - no device found!
Oct 27 23:42:36 ebrosh kernel: [   42.180000] cs: IO port probe 0x100-0x3af: clean.
Oct 27 23:42:36 ebrosh kernel: [   42.184000] cs: IO port probe 0x3e0-0x4ff: clean.
Oct 27 23:42:36 ebrosh kernel: [   42.184000] cs: IO port probe 0x820-0x8ff: clean.
Oct 27 23:42:36 ebrosh kernel: [   42.184000] cs: IO port probe 0xc00-0xcf7: clean.
Oct 27 23:42:36 ebrosh kernel: [   42.184000] cs: IO port probe 0xa00-0xaff: clean.
Oct 27 23:42:36 ebrosh kernel: [   42.184000] cs: IO port probe 0x100-0x3af: clean.
Oct 27 23:42:36 ebrosh kernel: [   42.188000] cs: IO port probe 0x3e0-0x4ff: clean.
Oct 27 23:42:36 ebrosh kernel: [   42.188000] cs: IO port probe 0x820-0x8ff: clean.
Oct 27 23:42:36 ebrosh kernel: [   42.188000] cs: IO port probe 0xc00-0xcf7: clean.
Oct 27 23:42:36 ebrosh kernel: [   42.188000] cs: IO port probe 0xa00-0xaff: clean.
Oct 27 23:42:36 ebrosh kernel: [   42.788000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [C187] -> GSI 11 (level, low) -> IRQ 11
Oct 27 23:42:36 ebrosh kernel: [   43.392000] es1968: clocking to 48000
Oct 27 23:42:36 ebrosh kernel: [   43.588000] Linux video capture interface: v2.00
Oct 27 23:42:36 ebrosh kernel: [   44.640000] lp0: using parport0 (interrupt-driven).
Oct 27 23:42:36 ebrosh kernel: [   44.812000] Adding 297160k swap on /dev/sda5.  Priority:-1 extents:1 across:297160k
Oct 27 23:42:36 ebrosh kernel: [   45.320000] EXT3 FS on sda2, internal journal
Oct 27 23:42:36 ebrosh kernel: [   47.512000] NET: Registered protocol family 10
Oct 27 23:42:36 ebrosh kernel: [   47.512000] lo: Disabled Privacy Extensions
Oct 27 23:42:36 ebrosh kernel: [   49.452000] ACPI: Battery Slot [C124] (battery present)
Oct 27 23:42:36 ebrosh kernel: [   49.452000] ACPI: Battery Slot [C125] (battery absent)
Oct 27 23:42:36 ebrosh kernel: [   49.452000] ACPI: Battery Slot [C126] (battery absent)
Oct 27 23:42:36 ebrosh kernel: [   50.000000] ACPI: ACPI Dock Station Driver 
Oct 27 23:42:36 ebrosh kernel: [   50.236000] input: Power Button (FF) as /class/input/input5
Oct 27 23:42:36 ebrosh kernel: [   50.236000] ACPI: Power Button (FF) [PWRF]
Oct 27 23:42:36 ebrosh kernel: [   50.276000] input: Sleep Button (CM) as /class/input/input6
Oct 27 23:42:36 ebrosh kernel: [   50.276000] ACPI: Sleep Button (CM) [C057]
Oct 27 23:42:36 ebrosh kernel: [   50.296000] input: Lid Switch as /class/input/input7
Oct 27 23:42:36 ebrosh kernel: [   50.296000] ACPI: Lid Switch [C1A5]
Oct 27 23:42:36 ebrosh kernel: [   50.972000] ACPI: AC Adapter [C11C] (on-line)
Oct 27 23:42:41 ebrosh kernel: [   57.944000] ppdev: user-space parallel port driver
Oct 27 23:42:43 ebrosh kernel: [   59.492000] audit(1193521362.827:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5107 profile="/usr/sbin/cupsd"
Oct 27 23:42:43 ebrosh kernel: [   59.884000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Oct 27 23:42:43 ebrosh kernel: [   59.884000] apm: overridden by ACPI.
Oct 27 23:43:04 ebrosh kernel: [   80.504000] Failure registering capabilities with primary security module.
Oct 27 23:43:04 ebrosh dhcdbd: Started up.


I could not find any mention of the cdrom.
can you ?

Thanks 
Eli

---

### Post by adlerschrei on 2007-11-01
Similar problem here. Trying a new install of ubuntu 7.10 server. After picking keyboard configuration the cdrom cannot be mounted and the installation aborts.

Also tried the regular ubuntu and xubuntu 7.10 install CD - same problem. CD drive works fine under XP and used to run Fedora on the same machine without problem. Checked that CD is configured correctly as secondary master.

The terminal window ls command from the install menu finds a  /dev/scd0 .

The computer is an ancient HP Celeron that I am planning to use as file server [Model HP Pavilion 6642F]. CDRW drive is a Sony .

Any help is highly appreciated.

FYI: Have ubuntu 7.10 running on a Dell D600 since yesterday. NO PROBLEM!

---

### Post by philinux on 2007-11-01
MY cdrw is now listed as /dev/scd1

Edit - have you looked in here

---

### Post by adlerschrei on 2007-11-02
Thanks for your response. 

ls /dev/scd*

only lists one drive, scd0

I cannot get to the point of the user interface that was attached.

PS: I am new to the forum and later realized that I should probably have posted a new thread, which I did at [http://ubuntuforums.org/showthread.php?p=3685337#post3685337](http://ubuntuforums.org/showthread.php?p=3685337#post3685337) . Still looking for a solution.

---

