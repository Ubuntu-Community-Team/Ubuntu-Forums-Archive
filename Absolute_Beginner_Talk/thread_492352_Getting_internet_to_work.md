---
title: "Getting internet to work"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by needhalp on 2007-07-04
I am completely new, just decided to try out ubuntu cause i did not want to upgrade to vista or switch to OSX
i got the partition to work with xp and ubuntu
but i have no idea how to get the internet to work, i read and tried a few of the basic methods but nothing seems to be working.

Verizon is my dsl isp
Router Info
Versalink 327w
model: b90-327w15-

router is at a different place in the house
i use a netgear ethernet to phone line bridge to connecto to internet with xp

Ethernet-Phoneline bridge info
Netgear model PE102


I then have a Netgear usb adapter PA101 to connect from the phone line to my computer

anykind of help would be great

---

### Post by christhemonkey on 2007-07-04
Whats the output of this command?:
```
ifconfig 
```


And what is the output of this command (if you boot up without your usb thing and then insert it):
```
dmesg | tail 
```

---

### Post by needhalp on 2007-07-04
ifconfig
i had to type this out since im using two differnet computers to do this

eth0          Link encap:Ethernet  HWaddr 00:11:11:64:D3:DF
                 UP BROADCAST MULTICAST  MTU:1500  METRIC:1
                 RX packets:0 errors:0 dropped:0 overruns:0 frame:0
                 TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
                 collisions:0 txquelelen:1000
                 RX bytes:0 (0,0 b)  TX bytes:0 (0,0 b)

eth0:avah Link encap:Ethernet  HWaddr 00:11:11:64:D3:DF
                 inet addr:169.254.9.7  Bcast:169.254.255.255  Mask:255.255.0.0
                 UP BROADCAST MULTICAST  MTU:1500  Metric:1

lo              Link encap:Local Loopback
                 inet addr:127.0.0.1  MASK:255.0.0.0
                 inet6 addr:  ::1/128 Scope:Host
                 UP LOOPBACK RUNNING  MTU:16436  Metric:1
                 RX packets:132 errors:0 dropped:0 overruns:0 frame:0
                 TX packets:132 errors:0 dropped:0 overruns:0 carrier:0
                 collisions:0 txqueuelen:0
                 RX bytes:9960 (9.1 KiB)    TX bytes:9960 (9.7 KiB)

ill get to the restarting without usb part

---

### Post by christhemonkey on 2007-07-04
Ok, what happens if you type this into a terminal:
```
ping 72.14.207.99 
```

(use Ctrl+C to stop it) and then post the output here!


That command makes your pc send 64 bytes to one of googles servers and then (hopefully) it should respond with another 64 bytes.

---

### Post by needhalp on 2007-07-04
everysingle one says the following

From 169.254.9.7 icmp_seq=(insert number here) Destination Host Unreachable

---

### Post by christhemonkey on 2007-07-04
See if you can ping your router:
```
ping 192.168.1.1 
```

(that is the defult ip address for your router, if you have changed your routers ip address, ping that address instead!)

---

### Post by needhalp on 2007-07-04
pretty sure i havnt changed my router address since i can configure it by going to that address using xp
samething happens when i try to ping that, it says Destination Host Unreachable


edit
mybad my ip is 192.168.1.47

results is

64 bytes from 192.168.1.47: icmp_seq=(number) ttl=64 time=(0.021-0.030 ma)

---

### Post by christhemonkey on 2007-07-04
Hmm, what is the output from:
```
sudo dhclient eth0 
```
?


Also, do you have any other ethernet ports on your pc?
If so can your provide the output of the 'dmesg | tail (after rebooting without usb thing and then inserting it)' command i asked you for a while back.

---

### Post by needhalp on 2007-07-04
sudo dhclient eth0

Internet Systems COnsortium DHCP Client v3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:11:11:64:d3:df
Sending on   LFP/eth0/00:11:11:64:d3:df
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by needhalp on 2007-07-04
i entered dmesg   tail since i didnt know how to type out the line between them

a huge list of info came up

the last couple about usb ends up being


[  59.227049] lo: Disabled Privacy Extensions
[  59.227138] ADDRCONF (NETDEV_UP): eth0: link is not ready
[255.563356] usb 5-2: new full speed USB device using uhci_hcd and address 2
[222.751285] usb 5-2: configuration #1 chosen from 1 choice
[607.620920] PPP generic driver version 2.4.2

---

### Post by lintoon on 2007-07-04
It looks like you haven't been assigned an IP address by your router.  Do you have a link light on the router. Is DCHP enabled on your router.  Check all your cables.  If all is working in XP but not Ubuntu I think it may be the Netgear PA 101 not installed/recognised in Ubuntu.  Just a guess.

---

### Post by needhalp on 2007-07-04
the light is working 
if netgear pa101 is not recognized what would i have to do, get a new ethernet-phonline bridge?

---

### Post by christhemonkey on 2007-07-04
It would seem that the usb ethernet phone line thing is not supported...


The only way to truly check would be to get the output of that dmesg command though.

Maybe you could save that text to a file and put it on a usb disk or a floppy an then paste it here?

---

### Post by lbelloq on 2007-07-04
My ISP is Surnet DSL, and I had a similar problem. Ubuntu doesn't automatically detect a DSL connection so you'll have to use pppoeconf ("sudo ppoeconf") to work it out. After that, reboot and everything will work ^^

---

### Post by needhalp on 2007-07-04
ok heres the dmesg

[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:3 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:3 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] Detected 3000.185 MHz processor.
[   22.194413] Built 1 zonelists.  Total pages: 259889
[   22.194416] Kernel command line: root=UUID=e485b028-bd6a-48d1-85d8-b0803da2a3bc ro quiet splash
[   22.194567] mapped APIC to ffffd000 (fee00000)
[   22.194570] mapped IOAPIC to ffffc000 (fec00000)
[   22.194572] Enabling fast FPU save and restore... done.
[   22.194575] Enabling unmasked SIMD FPU exception support... done.
[   22.194583] Initializing CPU#0
[   22.194639] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   22.195642] Console: colour VGA+ 80x25
[   22.195939] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   22.196268] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   22.216636] Memory: 1027304k/1047740k available (1992k kernel code, 19704k reserved, 893k data, 328k init, 130236k highmem)
[   22.216646] virtual kernel memory layout:
[   22.216647]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   22.216648]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   22.216649]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   22.216650]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   22.216651]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   22.216653]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   22.216654]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   22.216657] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   22.294553] Calibrating delay using timer specific routine.. 6005.45 BogoMIPS (lpj=12010912)
[   22.294595] Security Framework v1.0.0 initialized
[   22.294600] SELinux:  Disabled at boot.
[   22.294616] Mount-cache hash table entries: 512
[   22.294748] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000
[   22.294756] monitor/mwait feature present.
[   22.294758] using mwait in idle threads.
[   22.294764] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   22.294767] CPU: L2 cache: 1024K
[   22.294770] CPU: Physical Processor ID: 0
[   22.294772] CPU: After all inits, caps: bfebfbff 00000000 00000000 00003180 0000441d 00000000 00000000
[   22.294783] Compat vDSO mapped to ffffe000.
[   22.294786] Remapping vsyscall page to ffffe000
[   22.294801] Checking 'hlt' instruction... OK.
[   22.310625] SMP alternatives: switching to UP code
[   22.310959] Early unpacking initramfs... done
[   22.592589] ACPI: Core revision 20060707
[   22.593312] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   22.596201] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 04
[   22.596221] SMP alternatives: switching to SMP code
[   22.596303] Booting processor 1/1 eip 3000
[   22.606599] Initializing CPU#1
[   22.686188] Calibrating delay using timer specific routine.. 6000.44 BogoMIPS (lpj=12000896)
[   22.686197] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000
[   22.686204] monitor/mwait feature present.
[   22.686211] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   22.686214] CPU: L2 cache: 1024K
[   22.686216] CPU: Physical Processor ID: 0
[   22.686219] CPU: After all inits, caps: bfebfbff 00000000 00000000 00003180 0000441d 00000000 00000000
[   22.686491] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 04
[   22.686532] Total of 2 processors activated (12005.90 BogoMIPS).
[   22.686680] ENABLING IO-APIC IRQs
[   22.686861] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   22.834063] checking TSC synchronization across 2 CPUs: passed.
[    0.003993] Brought up 2 CPUs
[    0.084874] migration_cost=80
[    0.085158] Booting paravirtualized kernel on bare hardware
[    0.085233] Time: 13:46:25  Date: 06/04/107
[    0.085263] NET: Registered protocol family 16
[    0.085353] EISA bus registered
[    0.085359] ACPI: bus type pci registered
[    0.086601] PCI: Using configuration type 1
[    0.086603] Setting up standard PCI resources
[    2.102382] ACPI: Interpreter enabled
[    2.102386] ACPI: Using IOAPIC for interrupt routing
[    2.102822] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    2.102832] PCI: Probing PCI hardware (bus 00)
[    2.103621] PCI quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[    2.103625] PCI quirk: region 0500-053f claimed by ICH6 GPIO
[    2.103867] Boot video device is 0000:01:00.0
[    2.104452] PCI: Firmware left 0000:06:08.0 e100 interrupts enabled, disabling
[    2.104533] PCI: Transparent bridge - 0000:00:1e.0
[    2.104614] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    2.107769] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    2.108099] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    2.112528] ACPI: Power Resource [URP1] (off)
[    2.112612] ACPI: Power Resource [FDDP] (off)
[    2.112692] ACPI: Power Resource [LPTP] (off)
[    2.112822] ACPI: Power Resource [URP2] (off)
[    2.113645] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
[    2.113972] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
[    2.115278] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    2.115702] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    2.116123] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    2.116543] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    2.116962] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    2.117375] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    2.117796] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[    2.118232] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    2.118603] Linux Plug and Play Support v0.97 (c) Adam Belay
[    2.118614] pnp: PnP ACPI init
[    2.123451] pnp: PnP ACPI: found 14 devices
[    2.123457] PnPBIOS: Disabled by ACPI PNP
[    2.123511] PCI: Using ACPI for IRQ routing
[    2.123515] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    2.123612] NET: Registered protocol family 8
[    2.123615] NET: Registered protocol family 20
[    2.124700] pnp: 00:0c: ioport range 0x400-0x47f could not be reserved
[    2.124703] pnp: 00:0c: ioport range 0x680-0x6ff has been reserved
[    2.124706] pnp: 00:0c: ioport range 0x500-0x53f has been reserved
[    2.125075] PCI: Bridge: 0000:00:01.0
[    2.125079]   IO window: a000-afff
[    2.125083]   MEM window: ff400000-ff4fffff
[    2.125087]   PREFETCH window: bf900000-df9fffff
[    2.125091] PCI: Bridge: 0000:00:1c.0
[    2.125092]   IO window: disabled.
[    2.125098]   MEM window: ff800000-ff8fffff
[    2.125102]   PREFETCH window: dfd00000-dfdfffff
[    2.125107] PCI: Bridge: 0000:00:1c.1
[    2.125108]   IO window: disabled.
[    2.125113]   MEM window: ff700000-ff7fffff
[    2.125117]   PREFETCH window: dfc00000-dfcfffff
[    2.125122] PCI: Bridge: 0000:00:1c.2
[    2.125124]   IO window: disabled.
[    2.125129]   MEM window: ff600000-ff6fffff
[    2.125133]   PREFETCH window: dfb00000-dfbfffff
[    2.125138] PCI: Bridge: 0000:00:1c.3
[    2.125139]   IO window: disabled.
[    2.125144]   MEM window: ff500000-ff5fffff
[    2.125149]   PREFETCH window: dfa00000-dfafffff
[    2.125154] PCI: Bridge: 0000:00:1e.0
[    2.125157]   IO window: b000-bfff
[    2.125162]   MEM window: ff900000-ff9fffff
[    2.125166]   PREFETCH window: dfe00000-dfefffff
[    2.125184] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[    2.125191] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    2.125209] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
[    2.125215] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    2.125233] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 16
[    2.125238] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    2.125257] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[    2.125262] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    2.125281] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 19
[    2.125286] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    2.125298] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    2.125328] NET: Registered protocol family 2
[    2.166026] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    2.166154] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    2.166728] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    2.166977] TCP: Hash tables configured (established 131072 bind 65536)
[    2.166980] TCP reno registered
[    2.178109] checking if image is initramfs... it is
[    2.735667] Freeing initrd memory: 6990k freed
[    2.736260] audit: initializing netlink socket (disabled)
[    2.736276] audit(1183556788.456:1): initialized
[    2.736378] highmem bounce pool size: 64 pages

---

### Post by needhalp on 2007-07-04
[    2.736471] VFS: Disk quotas dquot_6.5.1
[    2.736494] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.736542] io scheduler noop registered
[    2.736545] io scheduler anticipatory registered
[    2.736548] io scheduler deadline registered
[    2.736561] io scheduler cfq registered (default)
[    2.736786] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    2.736828] assign_interrupt_mode Found MSI capability
[    2.736831] Allocate Port Service[0000:00:01.0:pcie00]
[    2.736928] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    2.736972] assign_interrupt_mode Found MSI capability
[    2.736976] Allocate Port Service[0000:00:1c.0:pcie00]
[    2.737015] Allocate Port Service[0000:00:1c.0:pcie02]
[    2.737123] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    2.737166] assign_interrupt_mode Found MSI capability
[    2.737169] Allocate Port Service[0000:00:1c.1:pcie00]
[    2.737206] Allocate Port Service[0000:00:1c.1:pcie02]
[    2.737311] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    2.737354] assign_interrupt_mode Found MSI capability
[    2.737357] Allocate Port Service[0000:00:1c.2:pcie00]
[    2.737394] Allocate Port Service[0000:00:1c.2:pcie02]
[    2.737508] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    2.737552] assign_interrupt_mode Found MSI capability
[    2.737554] Allocate Port Service[0000:00:1c.3:pcie00]
[    2.737592] Allocate Port Service[0000:00:1c.3:pcie02]
[    2.737770] isapnp: Scanning for PnP cards...
[    3.089120] isapnp: No Plug & Play device found
[    3.116296] Real Time Clock Driver v1.12ac
[    3.116352] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    3.116474] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    3.117168] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    3.117395] mice: PS/2 mouse device common for all mice
[    3.118048] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    3.118209] input: Macintosh mouse button emulation as /class/input/input0
[    3.118251] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    3.118255] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    3.118462] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    3.118464] PNP: PS/2 controller doesn't have AUX irq; using default 12
[    3.121361] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.121368] serio: i8042 AUX port at 0x60,0x64 irq 12
[    3.121497] EISA: Probing bus 0 at eisa.0
[    3.121529] EISA: Detected 0 cards.
[    3.151584] TCP cubic registered
[    3.151593] NET: Registered protocol family 1
[    3.151618] Starting balanced_irq
[    3.151627] Using IPI No-Shortcut mode
[    3.151732] input: AT Translated Set 2 keyboard as /class/input/input1
[    3.151815] ACPI: (supports S0 S1 S3 S4 S5)
[    3.151873]   Magic number: 15:917:785
[    3.151962]   hash matches device ptyq7
[    3.152142] Freeing unused kernel memory: 328k freed
[    3.153066] Time: tsc clocksource has been installed.
[    4.376293] Capability LSM initialized
[    4.419688] ACPI: Processor [CPU1] (supports 8 throttling states)
[    4.419711] ACPI: Processor [CPU2] (supports 8 throttling states)
[    4.921553] usbcore: registered new interface driver usbfs
[    4.921582] usbcore: registered new interface driver hub
[    4.960224] SCSI subsystem initialized
[    4.968638] libata version 2.20 loaded.
[    4.974391] ata_piix 0000:00:1f.1: version 2.10ac1
[    4.974409] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[    4.974432] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    4.974490] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
[    4.974544] usbcore: registered new device driver usb
[    5.020101] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
[    5.020128] scsi0 : ata_piix
[    5.040927] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k2-NAPI
[    5.040932] e100: Copyright(c) 1999-2006 Intel Corporation
[    5.042356] USB Universal Host Controller Interface driver v3.0
[    5.049405] ieee1394: Initialized config rom entry `ip1394'
[    5.198707] FDC 0 is a post-1991 82077
[    5.523081] ata1.00: ATAPI, max UDMA/33
[    5.523084] ata1.01: ATAPI, max UDMA/33
[    5.694935] ata1.00: configured for UDMA/33
[    5.866746] ata1.01: configured for UDMA/33
[    5.866759] scsi1 : ata_piix
[    6.036466] ATA: abnormal status 0x7F on port 0x00010177
[    6.037442] scsi 0:0:0:0: CD-ROM            _NEC     DVD_RW ND-2510A  2.0T PQ: 0 ANSI: 5
[    6.040099] scsi 0:0:1:0: CD-ROM            HL-DT-ST CD-ROM GCR-8483B 1.00 PQ: 0 ANSI: 5
[    6.040385] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    6.040413] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[    6.040430] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    6.040470] ata3: SATA max UDMA/133 cmd 0x0001ec00 ctl 0x0001e802 bmdma 0x0001dc00 irq 19
[    6.040503] ata4: SATA max UDMA/133 cmd 0x0001e400 ctl 0x0001e002 bmdma 0x0001dc08 irq 19
[    6.040516] scsi2 : ata_piix
[    6.211699] ata3.00: ata_hpa_resize 1: sectors = 390721968, hpa_sectors = 390721968
[    6.211703] ata3.00: ATA-6: WDC WD2000JD-22HBB0, 08.02D08, max UDMA/133
[    6.211706] ata3.00: 390721968 sectors, multi 16: LBA48 
[    6.223671] ata3.00: ata_hpa_resize 1: sectors = 390721968, hpa_sectors = 390721968
[    6.223674] ata3.00: configured for UDMA/133
[    6.223682] scsi3 : ata_piix
[    6.392163] ATA: abnormal status 0x7F on port 0x0001e407
[    6.392285] scsi 2:0:0:0: Direct-Access     ATA      WDC WD2000JD-22H 08.0 PQ: 0 ANSI: 5
[    6.392685] ACPI: PCI Interrupt 0000:06:08.0[A] -> GSI 20 (level, low) -> IRQ 20
[    6.392710] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 21
[    6.392730] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    6.392735] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    6.392857] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    6.392893] ehci_hcd 0000:00:1d.7: debug port 1
[    6.392900] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[    6.392912] ehci_hcd 0000:00:1d.7: irq 21, io mem 0xffafbc00
[    6.396785] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    6.396896] usb usb1: configuration #1 chosen from 1 choice
[    6.396931] hub 1-0:1.0: USB hub found
[    6.396939] hub 1-0:1.0: 8 ports detected
[    6.421443] e100: eth0: e100_probe: addr 0xff9ee000, irq 20, MAC addr 00:11:11:64:D3:DF
[    6.425896] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    6.425903] Uniform CD-ROM driver Revision: 3.20
[    6.425991] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    6.434277] sr1: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[    6.434335] sr 0:0:1:0: Attached scsi CD-ROM sr1
[    6.434776] SCSI device sda: 390721968 512-byte hdwr sectors (200050 MB)
[    6.434796] sda: Write Protect is off
[    6.434800] sda: Mode Sense: 00 3a 00 00
[    6.439959] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    6.439988] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    6.440016] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    6.440447] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.440519] SCSI device sda: 390721968 512-byte hdwr sectors (200050 MB)
[    6.440535] sda: Write Protect is off
[    6.440538] sda: Mode Sense: 00 3a 00 00
[    6.440566] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.440573]  sda: sda1 sda2 sda3 < sda5 sda6 > sda4
[    6.472333] sd 2:0:0:0: Attached scsi disk sda
[    6.502102] ACPI: PCI Interrupt 0000:06:05.0[A] -> GSI 17 (level, low) -> IRQ 17
[    6.502176] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 21
[    6.502192] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    6.502200] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    6.502239] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    6.502272] uhci_hcd 0000:00:1d.0: irq 21, io base 0x0000cc00
[    6.502415] usb usb2: configuration #1 chosen from 1 choice
[    6.502461] hub 2-0:1.0: USB hub found
[    6.502469] hub 2-0:1.0: 2 ports detected
[    6.554074] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[17]  MMIO=[ff9ef000-ff9ef7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    6.609937] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[    6.609950] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    6.609955] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    6.609980] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    6.610005] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d000
[    6.610101] usb usb3: configuration #1 chosen from 1 choice
[    6.610130] hub 3-0:1.0: USB hub found
[    6.610138] hub 3-0:1.0: 2 ports detected
[    6.717821] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[    6.717836] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    6.717842] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    6.717874] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    6.717906] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d400
[    6.718064] usb usb4: configuration #1 chosen from 1 choice
[    6.718117] hub 4-0:1.0: USB hub found
[    6.718129] hub 4-0:1.0: 2 ports detected
[    6.775022] Attempting manual resume
[    6.775026] swsusp: Resume From Partition 8:6
[    6.775028] PM: Checking swsusp image.
[    6.775191] PM: Resume from disk failed.
[    6.800763] kjournald starting.  Commit interval 5 seconds
[    6.800774] EXT3-fs: mounted filesystem with ordered data mode.
[    6.825732] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[    6.825744] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    6.825748] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    6.825774] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    6.825802] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d800
[    6.825897] usb usb5: configuration #1 chosen from 1 choice
[    6.825925] hub 5-0:1.0: USB hub found
[    6.825932] hub 5-0:1.0: 2 ports detected
[    6.937502] usb 1-5: new high speed USB device using ehci_hcd and address 3
[    7.078471] usb 1-5: configuration #1 chosen from 1 choice
[    7.504967] usb 2-2: new full speed USB device using uhci_hcd and address 2
[    7.690233] usb 2-2: configuration #1 chosen from 1 choice
[    7.840799] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001111000064d3df]
[    8.064439] usb 4-2: new low speed USB device using uhci_hcd and address 2
[    8.253509] usb 4-2: configuration #1 chosen from 1 choice
[   15.405331] NET: Registered protocol family 17
[   15.632781] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   15.642770] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.050864] input: PC Speaker as /class/input/input2
[   16.149445] iTCO_vendor_support: vendor-support=0
[   16.151035] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   16.151154] iTCO_wdt: Found a ICH6 or ICH6R TCO device (Version=2, TCOBASE=0x0460)
[   16.151208] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   16.169190] intel_rng: FWH not detected
[   16.554233] Linux agpgart interface v0.102 (c) Dave Jones
[   16.681713] parport: PnPBIOS parport detected.
[   16.681781] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   16.695786] agpgart: Detected an Intel 915G Chipset.
[   16.712825] agpgart: AGP aperture is 256M @ 0x0
[   16.746848] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x03F0 pid 0x2212
[   16.842003] usbcore: registered new interface driver libusual
[   16.842027] usbcore: registered new interface driver hiddev
[   16.971932] Initializing USB Mass Storage driver...
[   16.980030] scsi4 : SCSI emulation for USB Mass Storage devices
[   16.980165] usb-storage: device found at 3
[   16.980169] usb-storage: waiting for device to settle before scanning
[   16.980207] scsi5 : SCSI emulation for USB Mass Storage devices
[   16.980288] usb-storage: device found at 2
[   16.980292] usb-storage: waiting for device to settle before scanning
[   16.982066] input: Microsoft Microsoft Optical Mouse with Tilt Wheel as /class/input/input3
[   16.982235] input: USB HID v1.11 Mouse [Microsoft Microsoft Optical Mouse with Tilt Wheel] on usb-0000:00:1d.2-2
[   16.982259] usbcore: registered new interface driver usbhid
[   16.982264] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   16.982311] usbcore: registered new interface driver usb-storage
[   16.982317] USB Mass Storage support registered.
[   16.982896] usbcore: registered new interface driver usblp
[   16.982902] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   17.033382] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   17.033403] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   17.400995] fuse init (API version 7.8)
[   17.421164] lp0: using parport0 (interrupt-driven).
[   17.472845] Adding 3028180k swap on /dev/disk/by-uuid/0e70911a-9c98-4699-8aa4-10431e62e1d5.  Priority:-1 extents:1 across:3028180k
[   17.661706] EXT3 FS on sda4, internal journal
[   21.975505] usb-storage: device scan complete
[   21.975884] scsi 4:0:0:0: Direct-Access     HP       Officejet Pro L7 1.00 PQ: 0 ANSI: 2
[   21.977161] sd 4:0:0:0: Attached scsi removable disk sdb
[   21.977219] sd 4:0:0:0: Attached scsi generic sg3 type 0
[   21.980932] usb-storage: device scan complete
[   21.983924] scsi 5:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[   21.986925] scsi 5:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[   21.989921] scsi 5:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[   21.992918] scsi 5:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[   22.036945] sd 5:0:0:0: Attached scsi removable disk sdc
[   22.037009] sd 5:0:0:0: Attached scsi generic sg4 type 0
[   22.079891] sd 5:0:0:1: Attached scsi removable disk sdd
[   22.079963] sd 5:0:0:1: Attached scsi generic sg5 type 0
[   22.122870] sd 5:0:0:2: Attached scsi removable disk sde
[   22.122934] sd 5:0:0:2: Attached scsi generic sg6 type 0
[   22.166814] sd 5:0:0:3: Attached scsi removable disk sdf
[   22.166881] sd 5:0:0:3: Attached scsi generic sg7 type 0
[   23.055422] input: Power Button (FF) as /class/input/input4
[   23.055460] ACPI: Power Button (FF) [PWRF]
[   23.055548] input: Power Button (CM) as /class/input/input5
[   23.055577] ACPI: Power Button (CM) [PWRB]
[   23.206045] No dock devices found.
[   23.240816] ibm_acpi: ec object not found
[   23.275235] Using specific hotkey driver
[   23.338927] pcc_acpi: loading...
[   28.844536] [drm] Initialized drm 1.1.0 20060810
[   28.858683] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   28.859200] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[   29.624557] ppdev: user-space parallel port driver
[   30.336941] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   30.336948] apm: disabled - APM is not SMP safe.
[   30.520155] Bluetooth: Core ver 2.11
[   30.520227] NET: Registered protocol family 31
[   30.520230] Bluetooth: HCI device and connection manager initialized
[   30.520234] Bluetooth: HCI socket layer initialized
[   30.546422] [drm] Setting GART location based on new memory map
[   30.546843] [drm] Loading R300 Microcode
[   30.546891] [drm] writeback test succeeded in 1 usecs
[   30.609447] Bluetooth: L2CAP ver 2.8
[   30.609453] Bluetooth: L2CAP socket layer initialized
[   30.698338] Bluetooth: RFCOMM socket layer initialized
[   30.698354] Bluetooth: RFCOMM TTY layer initialized
[   30.698357] Bluetooth: RFCOMM ver 1.8
[   59.226920] NET: Registered protocol family 10
[   59.227049] lo: Disabled Privacy Extensions
[   59.227138] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  222.563356] usb 5-2: new full speed USB device using uhci_hcd and address 2
[  222.751285] usb 5-2: configuration #1 chosen from 1 choice
[  607.620920] PPP generic driver version 2.4.2
[  607.626163] NET: Registered protocol family 24
[ 1039.007602] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1106.838930] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1119.035597] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2922.161895] ADDRCONF(NETDEV_UP): eth0: link is not ready

---

### Post by needhalp on 2007-07-04
ive tried using sudo pppoeconf but it always says it either cant find a working ethernet or another computer is controlling the ethernet

---

### Post by lintoon on 2007-07-04
I think I get your set up.  You use the netgear equipment to extend your network from the router to your PC via your telephone cables??
-If this is the case you could carry on posting and hope someone can hep you with your USB adapter.
-Buy a compatible USB adapter??
-Install a long ethernet cable from your router to your PC.
-Use wireless.
-Maybe even sheck this device out.  It extends your network over your electricity cables in the house (It's safe):  It's the Netgear XE102.

[http://www.netgear.com/Products/PowerlineNetworking/PowerlineEthernetAdapters/XE102G.aspx?detail=Specifications](http://www.netgear.com/Products/PowerlineNetworking/PowerlineEthernetAdapters/XE102G.aspx?detail=Specifications)

I'd keep posting for now.  There are a lot of clever people in here.

---

### Post by needhalp on 2007-07-04
hmm i have those also, i used to use it for my ps2 but notanymore, its just lying there in a box
ill go try it out and see if it works

---

### Post by needhalp on 2007-07-04
hmm currently i have that and the netgear usb adapter plugged in(for windows) ive tried using dchp, static and the other one in the wired connection configuration and non seems to work still

---

### Post by lintoon on 2007-07-04
If it was me, I would keep it basic at first.  Eg take everything in between your pc and the router out of the equation.  If possible plug your pc directly into your router with an ethernet cable.  If it works plug your other equipment in and troubleshoot.  

I've just re-read your post and found that XP works with your existing setup (sorry I should have noticed that earlier) so I imagine Ubuntu will be fine when plugged directly into the router and the problem will be with your usb adapter.  I would still try plugging it in directly just so you can see it working for peace of mind.

---

### Post by needhalp on 2007-07-04
hmm I am currently trying to get that to work
first I have to get internet on xp with the netgear xe102, seems like my computer is lacking a ethernet controller so i have to fix that first

---

### Post by needhalp on 2007-07-04
well it seems like I dont have a ethernet controller driver on my computer, i cant determine the model using everesthome,  so it seems like the XE102 powerline connection does not work.

I am currently still using the PA101 Phoneline 10x USB adapter to connect to internet on XP

i think the only thing i need now is somehow getting the XE102 powerline adapter to work

---

### Post by christhemonkey on 2007-07-05
Do you have an ethernet port on the back of your pc?


I dont think your usb - phoneline adapter works with ubuntu im afraid, blame the vendor for not providing drivers.


Though i may be wrong.

---

### Post by needhalp on 2007-07-05
well since im just trying out ubuntu, it didnt really matter which pc i installed it on
so i switched a computer that used a ethernet cable to connect to the router and everyworks fine now

---

### Post by christhemonkey on 2007-07-06
Cool, sorry that you had to start with that negative experience, hope you enjoy ubuntu!

---

