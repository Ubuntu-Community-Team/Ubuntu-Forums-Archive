---
title: "Mutiple Segmentation Faults"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by randomnick on 2007-07-05
OK, Let me first say that I am actually using Debian Etch, Rather than Ubuntu...I have asked this question in the Debian Forums, but unfortunantly there's like 3 people over there, so this led me to attempt to pick the minds of the great Ubuntu collective....It may be a long shot, but here goes;

OK, I installed and have been using etch sucessfully for about a month now, everything was working well untill yesterday when suddenly about 10% of the apps I try and launch end with "Segmentation Fault" with no additional info, here is an example;

```
smith@aurora:~$ beryl
Segmentation fault
smith@aurora:~$ xmms
Segmentation fault
smith@auora:~$ winecfg
Invoking /usr/lib/wine/wine.bin winecfg.exe ...
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/smith', starting in the Windows directory.
/usr/bin/wine: line 396: 8687 Segmentation fault $WINEBIN/$WINE_BIN_NAME "$@"
Wine failed with return code 139
/usr/bin/wine: line 530: 8683 Terminated $XMESSAGE -timeout 30 -buttons " Dismiss ":0," Never display this message again ":3 -title "Wine Launch Window" -default " Dismiss " "Invoking $WINEBIN/$WINE_BIN_NAME $@ ...
This dialog box is a temporary status dialog to let you know
that Wine is attempting to launch your application.

Since Wine is still very much in a development stage,
many applications will fail silently.
This dialog box is your indication
that we're *trying* to run your application.

This dialog box will automatically disappear after 30 seconds,
or after your application finishes.

You can permanently disable this dialog by selecting
the option below.
" 2>/dev/null
Segmentation fault
smith@aurora:~$
```

I have tried "apt-get remove --purge *" and then reinstalling the broken app(s) to no avail. Any Linux guru have insight to lend to issue? 
(Please, No change to Ubuntu posts, they are both great distros, I have used both, but for reasons that are overly long to delve into at the moment I am stuck using Etch)

---

### Post by pbaumgar on 2007-07-05
Type dmesg and tell us the output.  You may have some hard drive issues.

---

### Post by Hobo Joe on 2007-07-05
I'm by no means a Linux guru, and I could be wrong, but it sounds a bit like your hard drive may be corrupted.

---

### Post by randomnick on 2007-07-05
Ok, here is the output from dmesg (and thanks for the help)

```
aurora:/home/smith# dmesg
Linux version 2.6.18-4-686 (Debian 2.6.18.dfsg.1-12etch2) (dannf@debian.org) (gcc version 4.1.2 20061115 (prerelease) (Debian 4.1.1-21)) #1 SMP Wed May 9 23:03:12 UTC 2007
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
 BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 000000007ff71000 (usable)
 BIOS-e820: 000000007ff71000 - 000000007ff73000 (ACPI NVS)
 BIOS-e820: 000000007ff73000 - 000000007ff94000 (ACPI data)
 BIOS-e820: 000000007ff94000 - 0000000080000000 (reserved)
 BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
 BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
 BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
1151MB HIGHMEM available.
896MB LOWMEM available.
found SMP MP-table at 000fe710
On node 0 totalpages: 524145
  DMA zone: 4096 pages, LIFO batch:0
  Normal zone: 225280 pages, LIFO batch:31
  HighMem zone: 294769 pages, LIFO batch:31
DMI 2.3 present.
ACPI: RSDP (v000 DELL                                  ) @ 0x000feba0
ACPI: RSDT (v001 DELL    GX260   0x00000009 ASL  0x00000061) @ 0x000fd509
ACPI: FADT (v001 DELL    GX260   0x00000009 ASL  0x00000061) @ 0x000fd541
ACPI: SSDT (v001   DELL    st_ex 0x00001000 MSFT 0x0100000d) @ 0xfffdaccc
ACPI: MADT (v001 DELL    GX260   0x00000009 ASL  0x00000061) @ 0x000fd5b5
ACPI: BOOT (v001 DELL    GX260   0x00000009 ASL  0x00000061) @ 0x000fd621
ACPI: ASF! (v016 DELL    GX260   0x00000009 ASL  0x00000061) @ 0x000fd649
ACPI: DSDT (v001   DELL    dt_ex 0x00001000 MSFT 0x0100000d) @ 0x00000000
ACPI: PM-Timer IO Port: 0x808
ACPI: Local APIC address 0xfee00000
ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Processor #0 15:2 APIC version 20
ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] disabled)
ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] disabled)
ACPI: LAPIC (acpi_id[0x04] lapic_id[0x07] disabled)
ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
ACPI: IRQ0 used by override.
ACPI: IRQ2 used by override.
ACPI: IRQ9 used by override.
Enabling APIC mode:  Flat.  Using 1 I/O APICs
Using ACPI (MADT) for SMP configuration information
Allocating PCI resources starting at 88000000 (gap: 80000000:7ec00000)
Detected 2524.130 MHz processor.
Built 1 zonelists.  Total pages: 524145
Kernel command line: root=/dev/hdd2 ro
mapped APIC to ffffd000 (fee00000)
mapped IOAPIC to ffffc000 (fec00000)
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Initializing CPU#0
PID hash table entries: 4096 (order: 12, 16384 bytes)
Console: colour VGA+ 80x25
Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Memory: 2071092k/2096580k available (1544k kernel code, 24300k reserved, 577k data, 196k init, 1179076k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay using timer specific routine.. 5052.33 BogoMIPS (lpj=10104667)Security Framework v1.0.0 initialized
SELinux:  Disabled at boot.
Capability LSM initialized
Mount-cache hash table entries: 512
CPU: After generic identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000
CPU: After vendor identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000
CPU: Trace cache: 12K uops, L1 D cache: 8K
CPU: L2 cache: 512K
CPU: Hyper-Threading is disabled
CPU: After all inits, caps: 3febfbff 00000000 00000000 00000080 00000000 00000000 00000000
Intel machine check architecture supported.
Intel machine check reporting enabled on CPU#0.
CPU0: Intel P4/Xeon Extended MCE MSRs (12) available
CPU0: Thermal monitoring enabled
Compat vDSO mapped to ffffe000.
Checking 'hlt' instruction... OK.
SMP alternatives: switching to UP code
Freeing SMP alternatives: 16k freed
ACPI: Core revision 20060707
CPU0: Intel(R) Pentium(R) 4 CPU 2.53GHz stepping 04
Total of 1 processors activated (5052.33 BogoMIPS).
ENABLING IO-APIC IRQs
..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Brought up 1 CPUs
migration_cost=0
checking if image is initramfs... it is
Freeing initrd memory: 4406k freed
NET: Registered protocol family 16
ACPI: bus type pci registered
PCI: PCI BIOS revision 2.10 entry at 0xfbdea, last bus=2
PCI: Using configuration type 1
Setting up standard PCI resources
ACPI: Interpreter enabled
ACPI: Using IOAPIC for interrupt routing
ACPI: PCI Root Bridge [PCI0] (0000:00)
PCI: Probing PCI hardware (bus 00)
ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
* The chipset may have PM-Timer Bug. Due to workarounds for a bug,
* this clock source is slow. If you are sure your timer does not have
* this bug, please use "acpi_pm_good" to disable the workaround
PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
PCI quirk: region 0880-08bf claimed by ICH4 GPIO
PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
Boot video device is 0000:02:08.0
PCI: Transparent bridge - 0000:00:1e.0
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 12 15)
ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 15)
ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 15)
ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 9 10 11 12 15)
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: PnP ACPI: found 12 devices
PnPBIOS: Disabled by ACPI PNP
PCI: Using ACPI for IRQ routing
PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
pnp: 00:0b: ioport range 0x800-0x85f could not be reserved
pnp: 00:0b: ioport range 0xc00-0xc7f has been reserved
pnp: 00:0b: ioport range 0x860-0x8ff could not be reserved
PCI: Bridge: 0000:00:01.0
  IO window: disabled.
  MEM window: fc000000-fdffffff
  PREFETCH window: e8000000-efffffff
PCI: Bridge: 0000:00:1e.0
  IO window: e000-efff
  MEM window: fa000000-fbffffff
  PREFETCH window: d0000000-dfffffff
PCI: Setting latency timer of device 0000:00:1e.0 to 64
NET: Registered protocol family 2
IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
TCP: Hash tables configured (established 131072 bind 65536)
TCP reno registered
Simple Boot Flag value 0x87 read from CMOS RAM was invalid
Simple Boot Flag at 0x7a set to 0x1
audit: initializing netlink socket (disabled)
audit(1183585682.276:1): initialized
highmem bounce pool size: 64 pages
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Initializing Cryptographic API
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered (default)
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
mice: PS/2 mouse device common for all mice
TCP bic registered
NET: Registered protocol family 1
NET: Registered protocol family 17
NET: Registered protocol family 8
NET: Registered protocol family 20
Using IPI No-Shortcut mode
ACPI: (supports S0 S1 S3 S4 S5)
Freeing unused kernel memory: 196k freed
Time: tsc clocksource has been installed.
input: AT Translated Set 2 keyboard as /class/input/input0
ACPI Exception (acpi_processor-0681): AE_NOT_FOUND, Processor Device is not present [20060707]
ACPI: Getting cpuindex for acpiid 0x2
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v3.0
ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 169
PCI: Setting latency timer of device 0000:00:1d.0 to 64
uhci_hcd 0000:00:1d.0: UHCI Host Controller
uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
uhci_hcd 0000:00:1d.0: irq 169, io base 0x0000ff80
usb usb1: configuration #1 chosen from 1 choice
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 177
PCI: Setting latency timer of device 0000:00:1d.1 to 64
uhci_hcd 0000:00:1d.1: UHCI Host Controller
uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
uhci_hcd 0000:00:1d.1: irq 177, io base 0x0000ff60
usb usb2: configuration #1 chosen from 1 choice
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Intel(R) PRO/1000 Network Driver - version 7.1.9-k4-NAPI
Copyright (c) 1999-2006 Intel Corporation.
ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 185
PCI: Setting latency timer of device 0000:00:1d.2 to 64
uhci_hcd 0000:00:1d.2: UHCI Host Controller
uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
uhci_hcd 0000:00:1d.2: irq 185, io base 0x0000ff40
usb usb3: configuration #1 chosen from 1 choice
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 193
PCI: Setting latency timer of device 0000:00:1d.7 to 64
ehci_hcd 0000:00:1d.7: EHCI Host Controller
ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
ehci_hcd 0000:00:1d.7: debug port 1
PCI: cache line size of 128 is not supported by device 0000:00:1d.7
ehci_hcd 0000:00:1d.7: irq 193, io mem 0xfe100000
ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
usb usb4: configuration #1 chosen from 1 choice
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 6 ports detected
ICH4: IDE controller at PCI slot 0000:00:1f.1
PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 185
ICH4: chipset revision 1
ICH4: not 100% native mode: will probe irqs later
    ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:DMA
    ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:DMA
Probing IDE interface ide0...
hda: SAMSUNG CDRW/DVD SM-332B, ATAPI CD/DVD-ROM drive
hdb: LITE-ON DVDRW SOHW-1693S, ATAPI CD/DVD-ROM drive
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Probing IDE interface ide1...
hdc: WDC WD800JB-00FMA0, ATA DISK drive
hdd: HDT722516DLAT80, ATA DISK drive
ide1 at 0x170-0x177,0x376 on irq 15
ACPI: PCI Interrupt 0000:02:0c.0[A] -> GSI 18 (level, low) -> IRQ 185
e1000: 0000:02:0c.0: e1000_probe: (PCI:33MHz:32-bit) 00:08:74:0e:24:fa
e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
hda: ATAPI 40X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
Uniform CD-ROM driver Revision: 3.20
hdb: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(66)
hdc: max request size: 128KiB
hdc: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(100)
hdc: cache flushes supported
 hdc: hdc1
hdd: max request size: 512KiB
hdd: 321672960 sectors (164696 MB) w/7674KiB Cache, CHS=20023/255/63, UDMA(100)
hdd: cache flushes supported
 hdd: hdd1 hdd2 hdd3 < hdd5 >
Attempting manual resume
kjournald starting.  Commit interval 5 seconds
EXT3-fs: mounted filesystem with ordered data mode.
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
intel_rng: FWH not detected
Linux agpgart interface v0.101 (c) Dave Jones
agpgart: Detected an Intel 845G Chipset.
agpgart: AGP aperture is 128M @ 0xe0000000
input: PC Speaker as /class/input/input1
ACPI: PCI Interrupt 0000:00:1f.3[B] -> GSI 17 (level, low) -> IRQ 201
gameport: EMU10K1 is pci0000:02:0a.1/gameport0, io 0xecd8, speed 1046kHz
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
Real Time Clock Driver v1.12ac
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
ACPI: PCI Interrupt 0000:02:0a.0[A] -> GSI 19 (level, low) -> IRQ 177
input: ImExPS/2 Generic Explorer Mouse as /class/input/input2
ts: Compaq touchscreen protocol output
Adding 3044276k swap on /dev/hdd5.  Priority:-1 extents:1 across:3044276k
EXT3 FS on hdd2, internal journal
loop: loaded (max 8 devices)
device-mapper: ioctl: 4.7.0-ioctl (2006-06-24) initialised: dm-devel@redhat.com
e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex
ACPI: Power Button (FF) [PWRF]
ACPI: Power Button (CM) [VBTN]
NET: Registered protocol family 10
lo: Disabled Privacy Extensions
IPv6 over IPv4 tunneling driver
ip_tables: (C) 2000-2006 Netfilter Core Team
Netfilter messages via NETLINK v0.30.
ip_conntrack version 2.4 (8192 buckets, 65536 max) - 224 bytes per conntrack
eth0: no IPv6 routers present
Inbound IN=eth0 OUT= MAC=00:08:74:0e:24:fa:00:14:6c:50:11:92:08:00 SRC=85.10.198.236 DST=192.168.1.8 LEN=626 TOS=0x00 PREC=0x20 TTL=41 ID=25663 DF PROTO=TCP SPT=9001 DPT=44501 WINDOW=18752 RES=0x00 ACK PSH URGP=0
Inbound IN=eth0 OUT= MAC=00:08:74:0e:24:fa:00:14:6c:50:11:92:08:00 SRC=85.10.198.236 DST=192.168.1.8 LEN=626 TOS=0x00 PREC=0x20 TTL=41 ID=25664 DF PROTO=TCP SPT=9001 DPT=44501 WINDOW=18752 RES=0x00 ACK PSH URGP=0
Inbound IN=eth0 OUT= MAC=00:08:74:0e:24:fa:00:14:6c:50:11:92:08:00 SRC=85.10.198.236 DST=192.168.1.8 LEN=626 TOS=0x00 PREC=0x20 TTL=41 ID=25665 DF PROTO=TCP SPT=9001 DPT=44501 WINDOW=18752 RES=0x00 ACK PSH URGP=0
Inbound IN=eth0 OUT= MAC=00:08:74:0e:24:fa:00:14:6c:50:11:92:08:00 SRC=85.10.198.236 DST=192.168.1.8 LEN=626 TOS=0x00 PREC=0x20 TTL=41 ID=25666 DF PROTO=TCP SPT=9001 DPT=44501 WINDOW=18752 RES=0x00 ACK PSH URGP=0
Inbound IN=eth0 OUT= MAC=00:08:74:0e:24:fa:00:14:6c:50:11:92:08:00 SRC=85.10.198.236 DST=192.168.1.8 LEN=626 TOS=0x00 PREC=0x20 TTL=41 ID=25667 DF PROTO=TCP SPT=9001 DPT=44501 WINDOW=18752 RES=0x00 ACK PSH URGP=0
Inbound IN=eth0 OUT= MAC=00:08:74:0e:24:fa:00:14:6c:50:11:92:08:00 SRC=85.10.198.236 DST=192.168.1.8 LEN=626 TOS=0x00 PREC=0x20 TTL=41 ID=25668 DF PROTO=TCP SPT=9001 DPT=44501 WINDOW=18752 RES=0x00 ACK PSH URGP=0
Inbound IN=eth0 OUT= MAC=00:08:74:0e:24:fa:00:14:6c:50:11:92:08:00 SRC=85.10.198.236 DST=192.168.1.8 LEN=626 TOS=0x00 PREC=0x20 TTL=41 ID=25669 DF PROTO=TCP SPT=9001 DPT=44501 WINDOW=18752 RES=0x00 ACK PSH URGP=0
Inbound IN=eth0 OUT= MAC=00:08:74:0e:24:fa:00:14:6c:50:11:92:08:00 SRC=85.10.198.236 DST=192.168.1.8 LEN=626 TOS=0x00 PREC=0x20 TTL=41 ID=25670 DF PROTO=TCP SPT=9001 DPT=44501 WINDOW=18752 RES=0x00 ACK PSH URGP=0
Inbound IN=eth0 OUT= MAC=00:08:74:0e:24:fa:00:14:6c:50:11:92:08:00 SRC=85.10.198.236 DST=192.168.1.8 LEN=626 TOS=0x00 PREC=0x20 TTL=41 ID=25671 DF PROTO=TCP SPT=9001 DPT=44501 WINDOW=18752 RES=0x00 ACK PSH URGP=0
Inbound IN=eth0 OUT= MAC=00:08:74:0e:24:fa:00:14:6c:50:11:92:08:00 SRC=85.10.198.236 DST=192.168.1.8 LEN=626 TOS=0x00 PREC=0x20 TTL=41 ID=25672 DF PROTO=TCP SPT=9001 DPT=44501 WINDOW=18752 RES=0x00 ACK PSH URGP=0
Inbound IN=eth0 OUT= MAC=00:08:74:0e:24:fa:00:14:6c:50:11:92:08:00 SRC=85.10.198.236 DST=192.168.1.8 LEN=626 TOS=0x00 PREC=0x20 TTL=41 ID=25673 DF PROTO=TCP SPT=9001 DPT=44501 WINDOW=18752 RES=0x00 ACK PSH URGP=0
Inbound IN=eth0 OUT= MAC= SRC=192.168.1.8 DST=234.21.81.1 LEN=78 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=24239 DPT=6347 LEN=58
Inbound IN=eth0 OUT= MAC=00:08:74:0e:24:fa:00:14:6c:50:11:92:08:00 SRC=85.10.198.236 DST=192.168.1.8 LEN=626 TOS=0x00 PREC=0x20 TTL=41 ID=25674 DF PROTO=TCP SPT=9001 DPT=44501 WINDOW=18752 RES=0x00 ACK PSH URGP=0
Inbound IN=eth0 OUT= MAC=00:08:74:0e:24:fa:00:14:6c:50:11:92:08:00 SRC=85.10.198.236 DST=192.168.1.8 LEN=626 TOS=0x00 PREC=0x20 TTL=41 ID=25675 DF PROTO=TCP SPT=9001 DPT=44501 WINDOW=18752 RES=0x00 ACK PSH URGP=0
Inbound IN=eth0 OUT= MAC=00:08:74:0e:24:fa:00:14:6c:50:11:92:08:00 SRC=85.10.198.236 DST=192.168.1.8 LEN=626 TOS=0x00 PREC=0x20 TTL=41 ID=25676 DF PROTO=TCP SPT=9001 DPT=44501 WINDOW=18752 RES=0x00 ACK PSH URGP=0
Inbound IN=eth0 OUT= MAC=00:08:74:0e:24:fa:00:14:6c:50:11:92:08:00 SRC=85.10.198.236 DST=192.168.1.8 LEN=626 TOS=0x00 PREC=0x20 TTL=41 ID=25677 DF PROTO=TCP SPT=9001 DPT=44501 WINDOW=18752 RES=0x00 ACK PSH URGP=0
Inbound IN=eth0 OUT= MAC=00:08:74:0e:24:fa:00:14:6c:50:11:92:08:00 SRC=85.10.198.236 DST=192.168.1.8 LEN=626 TOS=0x00 PREC=0x20 TTL=41 ID=25678 DF PROTO=TCP SPT=9001 DPT=44501 WINDOW=18752 RES=0x00 ACK PSH URGP=0
aurora:/home/smith#
```

---

### Post by randomnick on 2007-07-05
Hobo Joe,

Its a newer hard drive...I ran fsck and everything checked out all right, thanks for the suggestion though : )

---

### Post by randomnick on 2007-07-05
*bump* um,...anyone? [-o<

---

