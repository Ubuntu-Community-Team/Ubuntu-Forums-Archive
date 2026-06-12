---
title: "help!!!"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by kamitsukai on 2007-10-25
ok i buggered up my first ubuntu install lol so i partitioned my hardrive so that i could keep my first ubuntu install intact so i could copy files over to the new install but now that i have partitioned and installed ubuntu on the second partition i cant boot either partition and i cant access my first install's files from the ubuntu live cd either!!

can anyone help!! please

---

### Post by twistedbydesign on 2007-10-25
What exactly happens when you try to boot one of them up?

---

### Post by kamitsukai on 2007-10-25
well if i try and boot the new install all i get is a blank screen so i tried to but it in safe graphics mode and then i get i think fdisk error?...hang on ill reboot and and post all the errors....

---

### Post by kamitsukai on 2007-10-25
_OK from the original install_
```
Error 24 attempt to access block outside partition
```

_New install safe graphics_
```
File system check failed please repair system manually
```

---

### Post by taurus on 2007-10-25
Boot with the LiveCD, open a terminal, Applications -> Accessories -> Terminal, and post the output of this command here.

```
sudo fdisk -l
```
That is a lower case letter l, not 1.

---

### Post by twistedbydesign on 2007-10-25
I WOULD say it sounds like a hard drive problem...but you are using windows as well and it boots fine correct? (i just assumed since you were able to get online) If you you are using a separate computer and that one wont boot at all then that's the only thing i can think of. 
I think you need a second opinion though. I don't want to lead you in the wrong direction.
Sorry I couldn't be more help. Good luck!

---

### Post by kamitsukai on 2007-10-25
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf6bca237

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2655        9411    54275602+  83  Linux
/dev/sda2   *           1        2654    21318223+  83  Linux
/dev/sda3            9412        9729     2554335   82  Linux swap / Solaris

Partition table entries are not in disk order

```

thats what i get...

---

### Post by kamitsukai on 2007-10-25
> I WOULD say it sounds like a hard drive problem...but you are using windows as well and it boots fine correct? (i just assumed since you were able to get online) If you you are using a separate computer and that one wont boot at all then that's the only thing i can think of.
I think you need a second opinion though. I don't want to lead you in the wrong direction.
Sorry I couldn't be more help. Good luck!

nah im using the livecd at the moment

thanx anyway :P

---

### Post by ukripper on 2007-10-25
using livecd can you run filesystem check using followng command and paste output here.
```
sudo fsck -v
```

---

### Post by kamitsukai on 2007-10-25
```
fsck 1.40.2 (12-Jul-2007)

```

---

### Post by ukripper on 2007-10-25
Sorry my bad gave you version command.

Can you do following:

Sudo fsck -V

---

### Post by kamitsukai on 2007-10-25
i tried again and thats all i get....that bad?

---

### Post by ukripper on 2007-10-25
Try this  with capital V

```
sudo fsck -V
```

---

### Post by kamitsukai on 2007-10-25
well i got one line more?
```
fsck 1.40.2 (12-Jul-2007)
Checking all file systems.
```

---

### Post by ukripper on 2007-10-25
It is checking filesystem once done post if you get any errors

---

### Post by kamitsukai on 2007-10-25
how come it goes straight back to 
```
ubuntu@ubuntu:~$ 

```

when i click enter? and i had it up for 5 min and nothings happened:confused:

---

### Post by ukripper on 2007-10-25
Ok.

Can you type follwoing command and post poutput
```
dmesg | tail
```

---

### Post by kamitsukai on 2007-10-25
thanx for helping and heres what i get

```
ubuntu@ubuntu:~$ dmesg
[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
[    0.000000]  BIOS-e820: 000000003fff0000 - 000000003fffffc0 (ACPI data)
[    0.000000]  BIOS-e820: 000000003fffffc0 - 0000000040000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 262128) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   262128
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   262128
[    0.000000] On node 0 totalpages: 262128
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 255 pages used for memmap
[    0.000000]   HighMem zone: 32497 pages, LIFO batch:7
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00E6010 checksum 0
[    0.000000] ACPI: RSDP 000E6010, 0014 (r0 OID_00)
[    0.000000] ACPI: RSDT 3FFFCF96, 0034 (r1 INSYDE RSDT_000        1 _CSI    10103)
[    0.000000] ACPI: FACP 3FFFFB00, 0074 (r1 INSYDE FACP_000      100 _CSI    10103)
[    0.000000] ACPI: DSDT 3FFFD230, 28CB (r1 INSYDE INTELIC4     1004 INTL  2002025)
[    0.000000] ACPI: FACS 3FFFFFC0, 0040
[    0.000000] ACPI: BOOT 3FFFFB90, 0028 (r1 INSYDE SYS_BOOT      100 _CSI    10103)
[    0.000000] ACPI: DBGP 3FFFFBC0, 0034 (r1 INSYDE DBGP_000      100 _CSI    10103)
[    0.000000] ACPI: SSDT 3FFFCFCA, 010C (r1 INSYDE   GV3Ref     1001 INTL  2012044)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bfb80000)
[    0.000000] Built 1 zonelists.  Total pages: 260081
[    0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffd000 (0180e000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1995.050 MHz processor.
[   31.211262] Console: colour VGA+ 80x25
[   31.211858] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   31.212432] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   31.248889] Memory: 1027624k/1048512k available (2015k kernel code, 20176k reserved, 916k data, 364k init, 131008k highmem)
[   31.248898] virtual kernel memory layout:
[   31.248899]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   31.248900]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   31.248901]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   31.248902]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   31.248903]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   31.248904]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   31.248906]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   31.248909] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   31.248946] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   31.328925] Calibrating delay using timer specific routine.. 3992.70 BogoMIPS (lpj=7985417)
[   31.328951] Security Framework v1.0.0 initialized
[   31.328958] SELinux:  Disabled at boot.
[   31.328972] Mount-cache hash table entries: 512
[   31.329096] CPU: After generic identify, caps: afe9f9bf 00000000 00000000 00000000 00000180 00000000 00000000
[   31.329107] CPU: L1 I cache: 32K, L1 D cache: 32K
[   31.329109] CPU: L2 cache: 2048K
[   31.329112] CPU: After all inits, caps: afe9f9bf 00000000 00000000 00002040 00000180 00000000 00000000
[   31.329121] Compat vDSO mapped to ffffe000.
[   31.329131] Checking 'hlt' instruction... OK.
[   31.344998] SMP alternatives: switching to UP code
[   31.345164] Freeing SMP alternatives: 11k freed
[   31.345393] Early unpacking initramfs... done
[   31.655548] ACPI: Core revision 20070126
[   31.655597] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   31.656527] ACPI: setting ELCR to 0200 (from 0ca8)
[   31.669060] CPU0: Intel(R) Pentium(R) M processor 2.00GHz stepping 06
[   31.669066] SMP motherboard not detected.
[   31.669068] Local APIC not detected. Using dummy APIC emulation.
[   31.669100] Brought up 1 CPUs
[   31.669202] Booting paravirtualized kernel on bare hardware
[   31.669264] Time: 15:36:08  Date: 09/25/107
[   31.669287] NET: Registered protocol family 16
[   31.669358] EISA bus registered
[   31.669376] ACPI: bus type pci registered
[   31.669434] PCI: PCI BIOS revision 2.10 entry at 0xe9854, last bus=2
[   31.669436] PCI: Using configuration type 1
[   31.669438] Setting up standard PCI resources
[   31.673340] ACPI: EC: Look up EC in DSDT
[   31.673758] ACPI: EC: GPE=0x1c, ports=0x66, 0x62
[   31.674365] ACPI: Interpreter enabled
[   31.674367] ACPI: (supports S0 S3 S4 S5)
[   31.674381] ACPI: Using PIC for interrupt routing
[   31.683581] ACPI: EC: GPE=0x1c, ports=0x66, 0x62
[   31.683611] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   31.683617] PCI: Probing PCI hardware (bus 00)
[   31.683921] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[   31.683924] PCI quirk: region 1300-133f claimed by ICH4 GPIO
[   31.684519] PCI: Transparent bridge - 0000:00:1e.0
[   31.684578] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   31.684626] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI2._PRT]
[   31.686339] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 *10)
[   31.686405] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 7 10)
[   31.686469] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10) *11
[   31.686533] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10) *11
[   31.686594] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10) *11
[   31.686652] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 10 11) *0, disabled.
[   31.686712] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 7 10)
[   31.686771] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 *7 10)
[   31.686837] Linux Plug and Play Support v0.97 (c) Adam Belay
[   31.686851] pnp: PnP ACPI init
[   31.686857] ACPI: bus type pnp registered
[   31.691027] pnp: PnP ACPI: found 10 devices
[   31.691029] ACPI: ACPI bus type pnp unregistered
[   31.691032] PnPBIOS: Disabled by ACPI PNP
[   31.691063] PCI: Using ACPI for IRQ routing
[   31.691066] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   31.694333] NET: Registered protocol family 8
[   31.694335] NET: Registered protocol family 20
[   31.694375] pnp: 00:05: iomem range 0xfff80000-0xffffffff could not be reserved
[   31.694380] pnp: 00:07: ioport range 0x680-0x6ff has been reserved
[   31.694382] pnp: 00:07: ioport range 0x200-0x20f has been reserved
[   31.694385] pnp: 00:07: ioport range 0x290-0x297 has been reserved
[   31.694387] pnp: 00:07: ioport range 0x1000-0x107f has been reserved
[   31.694390] pnp: 00:07: ioport range 0x1300-0x133f has been reserved
[   31.694392] pnp: 00:07: ioport range 0x77c-0x77f has been reserved
[   31.697366] Time: tsc clocksource has been installed.
[   31.724609] PCI: Bridge: 0000:00:01.0
[   31.724611]   IO window: c000-dfff
[   31.724614]   MEM window: e0000000-efffffff
[   31.724617]   PREFETCH window: a0000000-afffffff
[   31.724625] PCI: Bus 3, cardbus bridge: 0000:02:04.0
[   31.724627]   IO window: 0000a400-0000a4ff
[   31.724631]   IO window: 0000a800-0000a8ff
[   31.724634]   PREFETCH window: 90000000-93ffffff
[   31.724638]   MEM window: d4000000-d7ffffff
[   31.724642] PCI: Bridge: 0000:00:1e.0
[   31.724644]   IO window: a000-bfff
[   31.724649]   MEM window: d0000000-dfffffff
[   31.724652]   PREFETCH window: 90000000-9fffffff
[   31.724661] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   31.724668] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   31.724785] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[   31.724788] PCI: setting IRQ 5 as level-triggered
[   31.724791] ACPI: PCI Interrupt 0000:02:04.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[   31.724804] NET: Registered protocol family 2
[   31.761361] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   31.761432] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   31.763035] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   31.763736] TCP: Hash tables configured (established 131072 bind 65536)
[   31.763740] TCP reno registered
[   31.773492] checking if image is initramfs... it is
[   32.225132] Switched to high resolution mode on CPU 0
[   32.377278] Freeing initrd memory: 7305k freed
[   32.377442] Simple Boot Flag at 0x37 set to 0x1
[   32.377652] audit: initializing netlink socket (disabled)
[   32.377670] audit(1193326567.940:1): initialized
[   32.377743] highmem bounce pool size: 64 pages
[   32.379317] VFS: Disk quotas dquot_6.5.1
[   32.379360] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   32.379454] io scheduler noop registered
[   32.379457] io scheduler anticipatory registered
[   32.379459] io scheduler deadline registered
[   32.379472] io scheduler cfq registered (default)
[   32.379532] Boot video device is 0000:01:00.0
[   32.379679] isapnp: Scanning for PnP cards...
[   32.733391] isapnp: No Plug & Play device found
[   32.754741] Real Time Clock Driver v1.12ac
[   32.754839] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   32.755440] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[   32.755450] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[   32.755924] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   32.756107] input: Macintosh mouse button emulation as /class/input/input0
[   32.756180] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   32.774809] i8042.c: Detected active multiplexing controller, rev 1.1.
[   32.783803] serio: i8042 KBD port at 0x60,0x64 irq 1
[   32.783808] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   32.783810] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   32.783813] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   32.783815] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   32.783969] mice: PS/2 mouse device common for all mice
[   32.785522] EISA: Probing bus 0 at eisa.0
[   32.785530] Cannot allocate resource for EISA slot 1
[   32.785558] EISA: Detected 0 cards.
[   32.785654] TCP cubic registered
[   32.785669] NET: Registered protocol family 1
[   32.785692] Using IPI No-Shortcut mode
[   32.785856]   Magic number: 11:76:640
[   32.786248] Freeing unused kernel memory: 364k freed
[   32.840848] input: AT Translated Set 2 keyboard as /class/input/input1
[   33.952716] AppArmor: AppArmor initialized<5>audit(1193326569.440:2):  type=1505 info="AppArmor initialized" pid=1178
[   33.959551] fuse init (API version 7.8)
[   33.963992] Failure registering capabilities with primary security module.
[   33.983589] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   33.983593] ACPI: Processor [CPU0] (supports 8 throttling states)
[   34.323551] usbcore: registered new interface driver usbfs
[   34.323573] usbcore: registered new interface driver hub
[   34.323590] usbcore: registered new device driver usb
[   34.324288] USB Universal Host Controller Interface driver v3.0
[   34.324520] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
[   34.324523] PCI: setting IRQ 10 as level-triggered
[   34.324527] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[   34.324538] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   34.324541] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   34.324736] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   34.324758] uhci_hcd 0000:00:1d.0: irq 10, io base 0x00001200
[   34.324855] usb usb1: configuration #1 chosen from 1 choice
[   34.324875] hub 1-0:1.0: USB hub found
[   34.324880] hub 1-0:1.0: 2 ports detected
[   34.388801] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   34.410882] SCSI subsystem initialized
[   34.415375] libata version 2.21 loaded.
[    3.516000] Marking TSC unstable due to: possible TSC halt in C2.
[    3.528000] Time: acpi_pm clocksource has been installed.
[    3.572000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
[    3.572000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[    3.572000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    3.572000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.572000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.572000] uhci_hcd 0000:00:1d.1: irq 10, io base 0x00001600
[    3.572000] usb usb2: configuration #1 chosen from 1 choice
[    3.572000] hub 2-0:1.0: USB hub found
[    3.572000] hub 2-0:1.0: 2 ports detected
[    3.876000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 7
[    3.876000] PCI: setting IRQ 7 as level-triggered
[    3.876000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 7 (level, low) -> IRQ 7
[    3.876000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    3.876000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.876000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 3
[    3.876000] ehci_hcd 0000:00:1d.7: debug port 1
[    3.876000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    3.876000] ehci_hcd 0000:00:1d.7: irq 7, io mem 0xfebff000
[    3.880000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.880000] usb usb3: configuration #1 chosen from 1 choice
[    3.880000] hub 3-0:1.0: USB hub found
[    3.880000] hub 3-0:1.0: 4 ports detected
[    3.984000] 8139cp 0000:02:02.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[    3.984000] 8139cp 0000:02:02.0: Try the "8139too" driver instead.
[    3.984000] 8139too Fast Ethernet driver 0.9.28
[    3.984000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 10
[    3.984000] ACPI: PCI Interrupt 0000:02:02.0[A] -> Link [LNKE] -> GSI 10 (level, low) -> IRQ 10
[    3.984000] PCI: Setting latency timer of device 0000:02:02.0 to 64
[    3.984000] eth0: RealTek RTL8139 at 0xf883eb00, 00:40:d0:6d:4c:58, IRQ 10
[    3.984000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    3.988000] ata_piix 0000:00:1f.1: version 2.11
[    3.988000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[    3.988000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[    3.988000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[    3.988000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    3.988000] scsi0 : ata_piix
[    3.988000] scsi1 : ata_piix
[    3.988000] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011100 irq 14
[    3.988000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011108 irq 15
[    4.152000] ata1.00: ATA-6: FUJITSU MHT2080AT, 0022, max UDMA/100
[    4.152000] ata1.00: 156301488 sectors, multi 16: LBA 
[    4.168000] ata1.00: configured for UDMA/100
[    4.488000] ata2.00: ATAPI: MATSHITAUJ-840D, 1.00, max UDMA/33
[    4.660000] ata2.00: configured for UDMA/33
[    4.660000] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHT2080A 0022 PQ: 0 ANSI: 5
[    4.660000] scsi 1:0:0:0: CD-ROM            MATSHITA UJ-840D          1.00 PQ: 0 ANSI: 5
[    4.660000] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 3
[    4.660000] PCI: setting IRQ 3 as level-triggered
[    4.660000] ACPI: PCI Interrupt 0000:02:05.0[A] -> Link [LNKG] -> GSI 3 (level, low) -> IRQ 3
[    4.660000] PCI: Setting latency timer of device 0000:02:05.0 to 64
[    4.716000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[3]  MMIO=[d0000000-d00007ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    4.732000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    4.732000] sd 0:0:0:0: [sda] Write Protect is off
[    4.732000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.732000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.732000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    4.732000] sd 0:0:0:0: [sda] Write Protect is off
[    4.732000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.732000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.732000]  sda: sda1 sda2 sda3
[    5.140000] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.140000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.140000] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    5.152000] sr0: scsi3-mmc drive: 62x/62x writer cd/rw xa/form2 cdda tray
[    5.152000] Uniform CD-ROM driver Revision: 3.20
[    5.152000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.872000] EXT3-fs: INFO: recovery required on readonly filesystem.
[    5.872000] EXT3-fs: write access will be enabled during recovery.
[    5.944000] kjournald starting.  Commit interval 5 seconds
[    5.944000] EXT3-fs: recovery complete.
[    5.944000] EXT3-fs: mounted filesystem with ordered data mode.
[    5.992000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0040d00100295c8a]
[    8.680000] ISO 9660 Extensions: Microsoft Joliet Level 3
[    8.724000] ISO 9660 Extensions: RRIP_1991A
[    8.956000] Registering unionfs 1.4
[    8.956000] unionfs: debugging is not enabled
[    8.968000] loop: module loaded
[    9.084000] squashfs: version 3.2-UBUNTU (2007/07/26) Phillip Lougher
[   44.784000] Linux agpgart interface v0.102 (c) Dave Jones
[   44.840000] [drm] Initialized drm 1.1.0 20060810
[   44.896000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[   44.896000] [drm] Initialized radeon 1.27.0 20060524 on minor 0
[   46.464000] Clocksource tsc unstable (delta = -272774255 ns)
[   79.280000] agpgart: Detected an Intel 855PM Chipset.
[   79.284000] agpgart: AGP aperture is 64M @ 0xb0000000
[   79.456000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   79.652000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   80.040000] iTCO_vendor_support: vendor-support=0
[   80.040000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   80.040000] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x1060)
[   80.040000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   80.084000] intel_rng: Firmware space is locked read-only. <4>intel_rng: If you can't or
[   80.084000]  don't want to <4>intel_rng: disable this in firmware setup, and <4>intel_rng: if
[   80.084000]  you are certain that your <4>intel_rng: system has a functional
[   80.084000]  RNG, try<4>intel_rng: using the 'no_fwh_detect' option.
[   80.748000] ieee80211_crypt: registered algorithm 'NULL'
[   80.748000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   80.748000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   80.940000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[   80.940000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   80.940000] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[   80.940000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   81.160000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0xf6eb1, caps: 0xa04713/0x0
[   81.220000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[   81.244000] sdhci: Secure Digital Host Controller Interface driver
[   81.244000] sdhci: Copyright(c) Pierre Ossman
[   81.244000] input: PC Speaker as /class/input/input3
[   81.732000] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
[   81.732000] Yenta: CardBus bridge found at 0000:02:04.0 [1071:8052]
[   81.732000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   81.732000] Yenta: Routing CardBus interrupts to PCI
[   81.732000] Yenta TI: socket 0000:02:04.0, mfunc 0x010c1202, devctl 0x44
[   81.964000] Yenta: ISA IRQ mask 0x0050, PCI irq 5
[   81.964000] Socket status: 30000006
[   81.964000] Yenta: Raising subordinate bus# of parent bus (#02) from #03 to #06
[   81.964000] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xbfff
[   81.964000] cs: IO port probe 0xa000-0xbfff: clean.
[   81.964000] pcmcia: parent PCI bridge Memory window: 0xd0000000 - 0xdfffffff
[   81.964000] pcmcia: parent PCI bridge Memory window: 0x90000000 - 0x9fffffff
[   81.964000] sdhci: SDHCI controller found at 0000:02:04.2 [1524:0550] (rev 0)
[   81.964000] ACPI: PCI Interrupt 0000:02:04.2[B] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[   81.964000] PCI: Setting latency timer of device 0000:02:04.2 to 64
[   81.964000] mmc0: SDHCI at 0xd0000900 irq 10 DMA
[   82.336000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[   82.336000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   82.852000] cs: IO port probe 0x100-0x3af: clean.
[   82.852000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   82.856000] cs: IO port probe 0x820-0x8ff: clean.
[   82.856000] cs: IO port probe 0xc00-0xcf7: clean.
[   82.856000] cs: IO port probe 0xa00-0xaff: clean.
[   83.164000] intel8x0_measure_ac97_clock: measured 55515 usecs
[   83.164000] intel8x0: clocking to 48000
[   84.456000] Adding 2554324k swap on /dev/sda3.  Priority:-1 extents:1 across:2554324k
[   87.616000] ACPI: AC Adapter [AC] (on-line)
[   87.692000] ACPI: Battery Slot [BAT0] (battery present)
[   87.712000] No dock devices found.
[   87.780000] input: Power Button (FF) as /class/input/input4
[   87.784000] ACPI: Power Button (FF) [PWRF]
[   87.824000] input: Sleep Button (CM) as /class/input/input5
[   87.824000] ACPI: Sleep Button (CM) [SBTN]
[   87.868000] input: Lid Switch as /class/input/input6
[   87.868000] ACPI: Lid Switch [LID]
[   92.596000] eth0: link down
[   92.596000] lp: driver loaded but no devices found
[   92.784000] ppdev: user-space parallel port driver
[   94.872000] apm: BIOS not found.
[   95.360000] Failure registering capabilities with primary security module.
[   96.500000] Bluetooth: Core ver 2.11
[   96.500000] NET: Registered protocol family 31
[   96.500000] Bluetooth: HCI device and connection manager initialized
[   96.500000] Bluetooth: HCI socket layer initialized
[   96.684000] Bluetooth: L2CAP ver 2.8
[   96.684000] Bluetooth: L2CAP socket layer initialized
[   96.940000] Bluetooth: RFCOMM socket layer initialized
[   96.940000] Bluetooth: RFCOMM TTY layer initialized
[   96.940000] Bluetooth: RFCOMM ver 1.8
[  101.520000] [drm:radeon_cp_init] *ERROR* radeon_cp_init called without lock held
[  101.520000] [drm:drm_unlock] *ERROR* Process 8028 using kernel context 0
[  172.088000] NET: Registered protocol family 17
[  179.920000] NET: Registered protocol family 10
[  179.920000] lo: Disabled Privacy Extensions
[  179.920000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  190.764000] eth1: no IPv6 routers present
[  387.264000] kjournald starting.  Commit interval 5 seconds
[  387.264000] EXT3 FS on sda1, internal journal
[  387.264000] EXT3-fs: mounted filesystem with ordered data mode.

```

---

### Post by ukripper on 2007-10-25
When you boot from your second installation (**not **livecd) what error you receive during boot?

---

### Post by kamitsukai on 2007-10-25
second installation? do you mean the one i just installed?
well i dont get any error all i get is a blank screen but if i boot up in safe graphics i get
```
File system check failed please repair system manually
```

---

### Post by ukripper on 2007-10-25
try this command to manually repair through livecd

If your filesyystem partiton is on sda1 then following :

```
fsck -t ext3 /dev/sda1
```

or if on sda2 then :
```

fsck -t ext3 /dev/sda2
```

---

### Post by kamitsukai on 2007-10-25
```
ubuntu@ubuntu:~$ fsck -t ext3 /dev/sda1
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
fsck.ext3: Permission denied while trying to open /dev/sda1
You must have r/w access to the filesystem or be root

```

and i think my original ubuntu install was reiser4?

---

### Post by ukripper on 2007-10-25
sorry didn't mention sudo 

```
sudo fsck -t ext3 /dev/sda1
```

If it is reiserfs then replace ext3 with that rest remains same

---

### Post by kamitsukai on 2007-10-25
ok i did that and this is what i have

```
ubuntu@ubuntu:~$ sudo fsck -t ext3 /dev/sda1
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
/dev/sda1: clean, 101028/6786080 files, 748795/13568900 blocks
ubuntu@ubuntu:~$ sudo fsck -t reiserfs /dev/sda2
fsck 1.40.2 (12-Jul-2007)
reiserfsck 3.6.19 (2003 www.namesys.com)

*************************************************************
** If you are using the latest reiserfsprogs and  it fails **
** please  email bug reports to reiserfs-list@namesys.com, **
** providing  as  much  information  as  possible --  your **
** hardware,  kernel,  patches,  settings,  all reiserfsck **
** messages  (including version),  the reiserfsck logfile, **
** check  the  syslog file  for  any  related information. **
** If you would like advice on using this program, support **
** is available  for $25 at  www.namesys.com/support.html. **
*************************************************************

Will read-only check consistency of the filesystem on /dev/sda2
Will put log info to 'stdout'

Do you want to run this program?[N/Yes] (note need to type Yes if you do):yes
ubuntu@ubuntu:~$ 

```

---

### Post by ukripper on 2007-10-25
You sure you using reiserfs on sda2 or sda1?

---

### Post by kamitsukai on 2007-10-25
erm..yer i m sure i used reiserfs? should i try ext3 anyway?

---

### Post by kamitsukai on 2007-10-25
is there any kind of restore program which will just recover my files?

---

### Post by ukripper on 2007-10-25
can you do following command :
```
blkid
```

and 

```
cat /etc/fstab
```

---

### Post by ukripper on 2007-10-25
Personally I think your problem may be the changed UUID.

When you created a partition and format it for another installtion it probably changed the UUID and taht is why your filesystem is not being recognised but anyhow once you post output of above commands I can make sure if taht is the case.

---

### Post by kamitsukai on 2007-10-25
```
ubuntu@ubuntu:~$ blkid
/dev/sda1: UUID="0bec010a-6d93-4ac7-a7d3-2ff2675e2d56" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: UUID="ed465c5a-c258-4956-bbc8-1ac1611635e2" TYPE="reiserfs" 

```

and

```
ubuntu@ubuntu:~$ cat /etc/fstab
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda3 swap swap defaults 0 0

```

thnx for this:KS

---

### Post by ukripper on 2007-10-25
> **kamitsukai said:**
> ```
ubuntu@ubuntu:~$ blkid
/dev/sda1: UUID="0bec010a-6d93-4ac7-a7d3-2ff2675e2d56" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: UUID="ed465c5a-c258-4956-bbc8-1ac1611635e2" TYPE="reiserfs" 

```

and

```
ubuntu@ubuntu:~$ cat /etc/fstab
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda3 swap swap defaults 0 0

```

thnx for this:KS

In terminal type following:

```
sudo gedit/etc/fstab
```

and include follwoing 
```
 UUID=0bec010a-6d93-4ac7-a7d3-2ff2675e2d56  /media/sda1     ext3    defaults        0       2
```

and for sda2 add follwoig:
```
 UUID=ed465c5a-c258-4956-bbc8-1ac1611635e2  /media/sda2     reiserfs   defaults        0       2
```


and save the file and exit and then boot again from your hardisk

---

### Post by kamitsukai on 2007-10-25
```
ubuntu@ubuntu:~$ sudo gedit/etc/fstab
sudo: gedit/etc/fstab: command not found

```


did u mean this?
```
sudo gedit /etc/fstab
```

ill try that

---

### Post by Maestro23 on 2007-10-25
> **kamitsukai said:**
> ```
ubuntu@ubuntu:~$ sudo gedit/etc/fstab
sudo: gedit/etc/fstab: command not found

```

(Space) between gedit & /etc/fstab

---

### Post by kamitsukai on 2007-10-25
erm... when you say include it do i just paste it in the file and then save?

oh and for sda2 do i just paste that in the same file as before?

sorry about all the questions but being a noob got me in this mess in the first place and i dont wont to make it worse:(

---

### Post by ukripper on 2007-10-25
Thanks Maestro23 to point that out just another typo.

---

### Post by ukripper on 2007-10-25
> **kamitsukai said:**
> erm... when you say include it do i just paste it in the file and then save?

oh and for sda2 do i just paste that in the same file as before?

sorry about all the questions but being a noob got me in this mess in the first place and i dont wont to make it worse:(

Yes just paste it in same file and save

---

### Post by kamitsukai on 2007-10-25
ok ive done that :)

---

### Post by ukripper on 2007-10-25
have you rebooted not to LIveCD but to your installation?

---

### Post by kamitsukai on 2007-10-25
........no?...do i need to?

_Edit_
oic didnt read your post fully ill reboot now, but which one to reboot into?

---

### Post by ukripper on 2007-10-25
try both

---

### Post by kamitsukai on 2007-10-25
:( neither worked still sam errors

---

### Post by ukripper on 2007-10-26
Can you post output of the follwoing from recovery mode or liveCd

```
cat /etc/fstab
```

```
cat /etc/grub/menu.list
```

```
blkid
```

```
mount
```

---

