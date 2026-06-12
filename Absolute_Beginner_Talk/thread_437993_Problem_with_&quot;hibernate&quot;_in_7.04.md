---
title: "Problem with &quot;hibernate&quot; in 7.04"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by JesterGr on 2007-05-09
when the pc hibernates, it freezes and shows some full-screen-console-like screen saying some things. i hope that those are included in the system log. I presume that the hibernation is not complete, so when i power it on again, it crashes while loading (at the beginning of the orange bar)

Any idea ?

```
May  9 17:59:42 Jester gnome-power-manager: (harry) Hibernating computer because the DBUS method Hibernate() was invoked
May  9 17:59:43 Jester NetworkManager: <information>^IGoing to sleep. 
May  9 17:59:43 Jester dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 5057
May  9 17:59:43 Jester dhclient: killed old client process, removed PID file
May  9 17:59:43 Jester avahi-daemon[4971]: Interface eth0.IPv4 no longer relevant for mDNS.
May  9 17:59:43 Jester avahi-daemon[4971]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.101.
May  9 17:59:43 Jester avahi-daemon[4971]: Withdrawing address record for fe80::2e0:18ff:feb5:16fc on eth0.
May  9 17:59:43 Jester avahi-daemon[4971]: Withdrawing address record for 192.168.1.101 on eth0.
May  9 17:59:43 Jester dhclient: DHCPRELEASE on eth0 to 192.168.1.1 port 67
May  9 17:59:43 Jester dhclient: send_packet: Network is unreachable
May  9 17:59:43 Jester dhclient: send_packet: please consult README file regarding broadcast address.
May  9 17:59:43 Jester NetworkManager: <information>^IWill activate wired connection 'eth0' because it now has a link. 
May  9 17:59:43 Jester avahi-autoipd(eth0)[6379]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 110).
May  9 17:59:43 Jester avahi-autoipd(eth0)[6379]: Successfully called chroot().
May  9 17:59:43 Jester avahi-autoipd(eth0)[6379]: Successfully dropped root privileges.
May  9 17:59:43 Jester avahi-autoipd(eth0)[6379]: fopen() failed: Permission denied
May  9 17:59:43 Jester avahi-autoipd(eth0)[6379]: Starting with address 169.254.8.116
May  9 17:59:43 Jester dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
May  9 17:59:43 Jester dhclient: Internet Systems Consortium DHCP Client V3.0.4
May  9 17:59:43 Jester dhclient: Copyright 2004-2006 Internet Systems Consortium.
May  9 17:59:43 Jester dhclient: All rights reserved.
May  9 17:59:43 Jester dhclient: For info, please visit http://www.isc.org/sw/dhcp/
May  9 17:59:43 Jester dhclient: 
May  9 17:59:43 Jester dhclient: Listening on LPF/eth0/00:e0:18:b5:16:fc
May  9 17:59:43 Jester dhclient: Sending on   LPF/eth0/00:e0:18:b5:16:fc
May  9 17:59:43 Jester dhclient: Sending on   Socket/fallback
May  9 17:59:43 Jester dhclient: DHCPRELEASE on eth0 to 192.168.1.1 port 67
May  9 17:59:43 Jester dhclient: send_packet: Network is unreachable
May  9 17:59:43 Jester dhclient: send_packet: please consult README file regarding broadcast address.
May  9 17:59:43 Jester avahi-autoipd(eth0)[6379]: SIOCSIFFLAGS failed: Permission denied
May  9 17:59:43 Jester NetworkManager: <debug info>^I[1178722783.975071] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/net_00_e0_18_b5_16_fc'). 
May  9 17:59:43 Jester NetworkManager: <information>^IDeactivating device eth0. 
May  9 17:59:46 Jester kernel: [ 1664.060425] PM: suspend-to-disk mode set to 'shutdown'
May  9 18:03:38 Jester syslogd 1.4.1#20ubuntu4: restart.
May  9 18:03:38 Jester kernel: Inspecting /boot/System.map-2.6.20-15-generic
May  9 18:03:38 Jester kernel: Loaded 24975 symbols from /boot/System.map-2.6.20-15-generic.
May  9 18:03:38 Jester kernel: Symbols match kernel version 2.6.20.
May  9 18:03:38 Jester kernel: No module symbols loaded - kernel modules not enabled. 
May  9 18:03:38 Jester kernel: [    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
May  9 18:03:38 Jester kernel: [    0.000000] BIOS-provided physical RAM map:
May  9 18:03:38 Jester kernel: [    0.000000] sanitize start
May  9 18:03:38 Jester kernel: [    0.000000] sanitize end
May  9 18:03:38 Jester kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009cc00 end: 000000000009cc00 type: 1
May  9 18:03:38 Jester kernel: [    0.000000] copy_e820_map() type is E820_RAM
May  9 18:03:38 Jester kernel: [    0.000000] copy_e820_map() start: 000000000009cc00 size: 0000000000003400 end: 00000000000a0000 type: 2
May  9 18:03:38 Jester kernel: [    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
May  9 18:03:38 Jester kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 000000005fefc000 end: 000000005fffc000 type: 1
May  9 18:03:38 Jester kernel: [    0.000000] copy_e820_map() type is E820_RAM
May  9 18:03:38 Jester kernel: [    0.000000] copy_e820_map() start: 000000005fffc000 size: 0000000000003000 end: 000000005ffff000 type: 3
May  9 18:03:38 Jester kernel: [    0.000000] copy_e820_map() start: 000000005ffff000 size: 0000000000001000 end: 0000000060000000 type: 4
May  9 18:03:38 Jester kernel: [    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000001000 end: 00000000fec01000 type: 2
May  9 18:03:38 Jester kernel: [    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
May  9 18:03:38 Jester kernel: [    0.000000] copy_e820_map() start: 00000000ffff0000 size: 0000000000010000 end: 0000000100000000 type: 2
May  9 18:03:38 Jester kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009cc00 (usable)
May  9 18:03:38 Jester kernel: [    0.000000]  BIOS-e820: 000000000009cc00 - 00000000000a0000 (reserved)
May  9 18:03:38 Jester kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
May  9 18:03:38 Jester kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000005fffc000 (usable)
May  9 18:03:38 Jester kernel: [    0.000000]  BIOS-e820: 000000005fffc000 - 000000005ffff000 (ACPI data)
May  9 18:03:38 Jester kernel: [    0.000000]  BIOS-e820: 000000005ffff000 - 0000000060000000 (ACPI NVS)
May  9 18:03:38 Jester kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
May  9 18:03:38 Jester kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
May  9 18:03:38 Jester kernel: [    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
May  9 18:03:38 Jester kernel: [    0.000000] 639MB HIGHMEM available.
May  9 18:03:38 Jester kernel: [    0.000000] 896MB LOWMEM available.
May  9 18:03:38 Jester kernel: [    0.000000] Entering add_active_range(0, 0, 393212) 0 entries of 256 used
May  9 18:03:38 Jester kernel: [    0.000000] Zone PFN ranges:
May  9 18:03:38 Jester kernel: [    0.000000]   DMA             0 ->     4096
May  9 18:03:38 Jester kernel: [    0.000000]   Normal       4096 ->   229376
May  9 18:03:38 Jester kernel: [    0.000000]   HighMem    229376 ->   393212
May  9 18:03:38 Jester kernel: [    0.000000] early_node_map[1] active PFN ranges
May  9 18:03:38 Jester kernel: [    0.000000]     0:        0 ->   393212
May  9 18:03:38 Jester kernel: [    0.000000] On node 0 totalpages: 393212
May  9 18:03:38 Jester kernel: [    0.000000]   DMA zone: 32 pages used for memmap
May  9 18:03:38 Jester kernel: [    0.000000]   DMA zone: 0 pages reserved
May  9 18:03:38 Jester kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
May  9 18:03:38 Jester kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
May  9 18:03:38 Jester kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
May  9 18:03:38 Jester kernel: [    0.000000]   HighMem zone: 1279 pages used for memmap
May  9 18:03:38 Jester kernel: [    0.000000]   HighMem zone: 162557 pages, LIFO batch:31
May  9 18:03:38 Jester kernel: [    0.000000] DMI 2.3 present.
May  9 18:03:38 Jester kernel: [    0.000000] ACPI: RSDP (v000 ASUS                                  ) @ 0x000f5810
May  9 18:03:38 Jester kernel: [    0.000000] ACPI: RSDT (v001 ASUS   P4S8X    0x42302e31 MSFT 0x31313031) @ 0x5fffc000
May  9 18:03:38 Jester kernel: [    0.000000] ACPI: FADT (v001 ASUS   P4S8X    0x42302e31 MSFT 0x31313031) @ 0x5fffc0c0
May  9 18:03:38 Jester kernel: [    0.000000] ACPI: BOOT (v001 ASUS   P4S8X    0x42302e31 MSFT 0x31313031) @ 0x5fffc030
May  9 18:03:38 Jester kernel: [    0.000000] ACPI: MADT (v001 ASUS   P4S8X    0x42302e31 MSFT 0x31313031) @ 0x5fffc058
May  9 18:03:38 Jester kernel: [    0.000000] ACPI: DSDT (v001   ASUS P4S8X    0x00001000 MSFT 0x0100000b) @ 0x00000000
May  9 18:03:38 Jester kernel: [    0.000000] ACPI: PM-Timer IO Port: 0xe408
May  9 18:03:38 Jester kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
May  9 18:03:38 Jester kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
May  9 18:03:38 Jester kernel: [    0.000000] Processor #0 15:2 APIC version 20
May  9 18:03:38 Jester kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
May  9 18:03:38 Jester kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
May  9 18:03:38 Jester kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 128, address 0xfec00000, GSI 0-23
May  9 18:03:38 Jester kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl edge)
May  9 18:03:38 Jester kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 20 low level)
May  9 18:03:38 Jester kernel: [    0.000000] ACPI: IRQ0 used by override.
May  9 18:03:38 Jester kernel: [    0.000000] ACPI: IRQ2 used by override.
May  9 18:03:38 Jester kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
May  9 18:03:38 Jester kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
May  9 18:03:38 Jester kernel: [    0.000000] Allocating PCI resources starting at 70000000 (gap: 60000000:9ec00000)
May  9 18:03:38 Jester kernel: [    0.000000] Detected 2628.949 MHz processor.
May  9 18:03:38 Jester kernel: [   34.531089] Built 1 zonelists.  Total pages: 390141
May  9 18:03:38 Jester kernel: [   34.531097] Kernel command line: root=UUID=b9d0b835-5f4e-457b-827f-fcb56a7bdbb6 ro quiet splash
May  9 18:03:38 Jester kernel: [   34.531280] mapped APIC to ffffd000 (fee00000)
May  9 18:03:38 Jester kernel: [   34.531282] mapped IOAPIC to ffffc000 (fec00000)
May  9 18:03:38 Jester kernel: [   34.531287] Enabling fast FPU save and restore... done.
May  9 18:03:38 Jester kernel: [   34.531291] Enabling unmasked SIMD FPU exception support... done.
May  9 18:03:38 Jester kernel: [   34.531308] Initializing CPU#0
May  9 18:03:38 Jester kernel: [   34.531421] PID hash table entries: 4096 (order: 12, 16384 bytes)
May  9 18:03:38 Jester kernel: [   34.532600] Console: colour VGA+ 80x25
May  9 18:03:38 Jester kernel: [   34.533783] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
May  9 18:03:38 Jester kernel: [   34.534882] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
May  9 18:03:38 Jester kernel: [   34.608973] Memory: 1547828k/1572848k available (1992k kernel code, 23788k reserved, 893k data, 328k init, 655344k highmem)
May  9 18:03:38 Jester kernel: [   34.608987] virtual kernel memory layout:
May  9 18:03:38 Jester kernel: [   34.608988]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
May  9 18:03:38 Jester kernel: [   34.608989]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
May  9 18:03:38 Jester kernel: [   34.608990]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
May  9 18:03:38 Jester kernel: [   34.608991]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
May  9 18:03:38 Jester kernel: [   34.608992]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
May  9 18:03:38 Jester kernel: [   34.608993]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
May  9 18:03:38 Jester kernel: [   34.608994]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
May  9 18:03:38 Jester kernel: [   34.608997] Checking if this processor honours the WP bit even in supervisor mode... Ok.
May  9 18:03:38 Jester kernel: [   34.687224] Calibrating delay using timer specific routine.. 5262.22 BogoMIPS (lpj=10524453)
May  9 18:03:38 Jester kernel: [   34.687294] Security Framework v1.0.0 initialized
May  9 18:03:38 Jester kernel: [   34.687310] SELinux:  Disabled at boot.
May  9 18:03:38 Jester kernel: [   34.687333] Mount-cache hash table entries: 512
May  9 18:03:38 Jester kernel: [   34.687589] CPU: After generic identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000
May  9 18:03:38 Jester kernel: [   34.687604] CPU: Trace cache: 12K uops, L1 D cache: 8K
May  9 18:03:38 Jester kernel: [   34.687607] CPU: L2 cache: 512K
May  9 18:03:38 Jester kernel: [   34.687610] CPU: Hyper-Threading is disabled
May  9 18:03:38 Jester kernel: [   34.687613] CPU: After all inits, caps: 3febfbff 00000000 00000000 00003080 00000000 00000000 00000000
May  9 18:03:38 Jester kernel: [   34.687631] Compat vDSO mapped to ffffe000.
May  9 18:03:38 Jester kernel: [   34.687638] Remapping vsyscall page to ffffe000
May  9 18:03:38 Jester kernel: [   34.687658] Checking 'hlt' instruction... OK.
May  9 18:03:38 Jester kernel: [   34.703432] SMP alternatives: switching to UP code
May  9 18:03:38 Jester kernel: [   34.703879] Freeing SMP alternatives: 11k freed
May  9 18:03:38 Jester kernel: [   34.704171] Early unpacking initramfs... done
May  9 18:03:38 Jester kernel: [   35.028145] ACPI: Core revision 20060707
May  9 18:03:38 Jester kernel: [   35.029027] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
May  9 18:03:38 Jester kernel: [   35.030234] CPU0: Intel(R) Pentium(R) 4 CPU 2.40GHz stepping 04
May  9 18:03:38 Jester kernel: [   35.030277] Total of 1 processors activated (5262.22 BogoMIPS).
May  9 18:03:38 Jester kernel: [   35.030391] ENABLING IO-APIC IRQs
May  9 18:03:38 Jester kernel: [   35.030607] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
May  9 18:03:38 Jester kernel: [   35.174653] Brought up 1 CPUs
May  9 18:03:38 Jester kernel: [   35.174966] Booting paravirtualized kernel on bare hardware
May  9 18:03:38 Jester kernel: [   35.175061] Time: 18:03:06  Date: 04/09/107
May  9 18:03:38 Jester kernel: [   35.175109] NET: Registered protocol family 16
May  9 18:03:38 Jester kernel: [   35.175243] EISA bus registered
May  9 18:03:38 Jester kernel: [   35.175250] ACPI: bus type pci registered
May  9 18:03:38 Jester kernel: [   35.176965] PCI: PCI BIOS revision 2.10 entry at 0xf11b0, last bus=1
May  9 18:03:38 Jester kernel: [   35.176967] PCI: Using configuration type 1
May  9 18:03:38 Jester kernel: [   35.176969] Setting up standard PCI resources
May  9 18:03:38 Jester kernel: [   35.190864] ACPI: Interpreter enabled
May  9 18:03:38 Jester kernel: [   35.190868] ACPI: Using IOAPIC for interrupt routing
May  9 18:03:38 Jester kernel: [   35.191621] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
May  9 18:03:38 Jester kernel: [   35.191851] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
May  9 18:03:38 Jester kernel: [   35.192071] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
May  9 18:03:38 Jester kernel: [   35.192292] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
May  9 18:03:38 Jester kernel: [   35.192518] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *9
May  9 18:03:38 Jester kernel: [   35.192741] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *9
May  9 18:03:38 Jester kernel: [   35.192964] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *9
May  9 18:03:38 Jester kernel: [   35.193183] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
May  9 18:03:38 Jester kernel: [   35.193291] ACPI: PCI Root Bridge [PCI0] (0000:00)
May  9 18:03:38 Jester kernel: [   35.193299] PCI: Probing PCI hardware (bus 00)
May  9 18:03:38 Jester kernel: [   35.193649] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
May  9 18:03:38 Jester kernel: [   35.193995] Enabling SiS 96x SMBus.
May  9 18:03:38 Jester kernel: [   35.195162] Boot video device is 0000:01:00.0
May  9 18:03:38 Jester kernel: [   35.195233] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
May  9 18:03:38 Jester kernel: [   35.196885] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
May  9 18:03:38 Jester kernel: [   35.202634] Linux Plug and Play Support v0.97 (c) Adam Belay
May  9 18:03:38 Jester kernel: [   35.202649] pnp: PnP ACPI init
May  9 18:03:38 Jester kernel: [   35.208155] pnp: PnP ACPI: found 17 devices
May  9 18:03:38 Jester kernel: [   35.208163] PnPBIOS: Disabled by ACPI PNP
May  9 18:03:38 Jester kernel: [   35.208238] PCI: Using ACPI for IRQ routing
May  9 18:03:38 Jester kernel: [   35.208243] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
May  9 18:03:38 Jester kernel: [   35.222325] NET: Registered protocol family 8
May  9 18:03:38 Jester kernel: [   35.222328] NET: Registered protocol family 20
May  9 18:03:38 Jester kernel: [   35.222663] pnp: 00:02: ioport range 0xe400-0xe47f could not be reserved
May  9 18:03:38 Jester kernel: [   35.222667] pnp: 00:02: ioport range 0xe480-0xe4ff has been reserved
May  9 18:03:38 Jester kernel: [   35.222670] pnp: 00:02: ioport range 0xe600-0xe61f has been reserved
May  9 18:03:38 Jester kernel: [   35.222672] pnp: 00:02: ioport range 0x480-0x48f has been reserved
May  9 18:03:38 Jester kernel: [   35.222691] pnp: 00:10: ioport range 0x295-0x296 has been reserved
May  9 18:03:38 Jester kernel: [   35.223023] PCI: Bridge: 0000:00:01.0
May  9 18:03:38 Jester kernel: [   35.223028]   IO window: d000-dfff
May  9 18:03:38 Jester kernel: [   35.223035]   MEM window: d7800000-d7ffffff
May  9 18:03:38 Jester kernel: [   35.223041]   PREFETCH window: dff00000-febfffff
May  9 18:03:38 Jester kernel: [   35.223060] PCI: Setting latency timer of device 0000:00:01.0 to 64
May  9 18:03:38 Jester kernel: [   35.223098] NET: Registered protocol family 2
May  9 18:03:38 Jester kernel: [   35.262589] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
May  9 18:03:38 Jester kernel: [   35.262932] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
May  9 18:03:38 Jester kernel: [   35.264536] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
May  9 18:03:38 Jester kernel: [   35.265535] TCP: Hash tables configured (established 131072 bind 65536)
May  9 18:03:38 Jester kernel: [   35.265543] TCP reno registered
May  9 18:03:38 Jester kernel: [   35.274709] checking if image is initramfs... it is
May  9 18:03:38 Jester kernel: [   35.919198] Freeing initrd memory: 6996k freed
May  9 18:03:38 Jester kernel: [   35.919535] Simple Boot Flag at 0x3a set to 0x1
May  9 18:03:38 Jester kernel: [   35.919850] audit: initializing netlink socket (disabled)
May  9 18:03:38 Jester kernel: [   35.919872] audit(1178733787.468:1): initialized
May  9 18:03:38 Jester kernel: [   35.919990] highmem bounce pool size: 64 pages
May  9 18:03:38 Jester kernel: [   35.920075] VFS: Disk quotas dquot_6.5.1
May  9 18:03:38 Jester kernel: [   35.920105] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
May  9 18:03:38 Jester kernel: [   35.920183] io scheduler noop registered
May  9 18:03:38 Jester kernel: [   35.920187] io scheduler anticipatory registered
May  9 18:03:38 Jester kernel: [   35.920189] io scheduler deadline registered
May  9 18:03:38 Jester kernel: [   35.920198] io scheduler cfq registered (default)
May  9 18:03:38 Jester kernel: [   35.920546] isapnp: Scanning for PnP cards...
May  9 18:03:38 Jester kernel: [   36.274101] isapnp: No Plug & Play device found

```
log continued in next post...


i am a newbie in linux, so say things in a non-complicative way :-)

PS. I have an ATI Radeon 9000 Video card, on a P4 2.4@2.6. Sorry for the length of the logs, but i don't know what is critical and what is not, so i quoted everything from the moment i pressed hibernate till the moment it came back up (that means, incomplete hibernate, crashed recovery from hibernate, and finally typical power on)

---

### Post by Inxsible on 2007-05-09
I have read that if you are using the restricted drivers for you graphics card, then not only Hibernate, but Suspend, Logout and Switch User do not work correctly.
 
I have the same problems !

---

### Post by EXCiD3 on 2007-05-09
I have not tried the Suspend or Hibernate on my DV9000 but Logout seems to work just fine. Lots of people have had problems with Suspend and Hibernate.

---

### Post by Inxsible on 2007-05-09
Are you using the restricted drivers too ?
 
Could you maybe try out the Suspend and Hibernate and Switch User options and let me know what happens ?
 
I am not currently on my Ubuntu machine...so I shall try those later in the evening and let you know what happens on my machine

---

### Post by JesterGr on 2007-05-09
```
May  9 18:03:38 Jester kernel: [   36.304664] Real Time Clock Driver v1.12ac
May  9 18:03:38 Jester kernel: [   36.304729] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
May  9 18:03:38 Jester kernel: [   36.304875] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May  9 18:03:38 Jester kernel: [   36.305124] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
May  9 18:03:38 Jester kernel: [   36.305911] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May  9 18:03:38 Jester kernel: [   36.306275] 00:0c: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
May  9 18:03:38 Jester kernel: [   36.306592] mice: PS/2 mouse device common for all mice
May  9 18:03:38 Jester kernel: [   36.307273] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
May  9 18:03:38 Jester kernel: [   36.307471] input: Macintosh mouse button emulation as /class/input/input0
May  9 18:03:38 Jester kernel: [   36.307519] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
May  9 18:03:38 Jester kernel: [   36.307524] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
May  9 18:03:38 Jester kernel: [   36.307856] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
May  9 18:03:38 Jester kernel: [   36.308081] serio: i8042 KBD port at 0x60,0x64 irq 1
May  9 18:03:38 Jester kernel: [   36.308087] serio: i8042 AUX port at 0x60,0x64 irq 12
May  9 18:03:38 Jester kernel: [   36.308228] EISA: Probing bus 0 at eisa.0
May  9 18:03:38 Jester kernel: [   36.308261] Cannot allocate resource for EISA slot 7
May  9 18:03:38 Jester kernel: [   36.308263] Cannot allocate resource for EISA slot 8
May  9 18:03:38 Jester kernel: [   36.308265] EISA: Detected 0 cards.
May  9 18:03:38 Jester kernel: [   36.338356] TCP cubic registered
May  9 18:03:38 Jester kernel: [   36.338364] NET: Registered protocol family 1
May  9 18:03:38 Jester kernel: [   36.338393] Using IPI No-Shortcut mode
May  9 18:03:38 Jester kernel: [   36.338496] ACPI: (supports S0 S1 S4 S5)
May  9 18:03:38 Jester kernel: [   36.338547]   Magic number: 7:92:89
May  9 18:03:38 Jester kernel: [   36.339401] Freeing unused kernel memory: 328k freed
May  9 18:03:38 Jester kernel: [   36.341074] Time: tsc clocksource has been installed.
May  9 18:03:38 Jester kernel: [   36.354970] input: AT Translated Set 2 keyboard as /class/input/input1
May  9 18:03:38 Jester kernel: [   37.609239] Capability LSM initialized
May  9 18:03:38 Jester kernel: [   37.805511] ACPI: Invalid PBLK length [5]
May  9 18:03:38 Jester kernel: [   37.805557] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
May  9 18:03:38 Jester kernel: [   38.559425] ieee1394: Initialized config rom entry `ip1394'
May  9 18:03:38 Jester kernel: [   38.561089] PCI: Enabling device 0000:00:02.3 (0004 -> 0006)
May  9 18:03:38 Jester kernel: [   38.561105] ACPI: PCI Interrupt 0000:00:02.3[b] -> GSI 17 (level, low) -> IRQ 16
May  9 18:03:38 Jester kernel: [   38.613053] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[16]  MMIO=[d7000000-d70007ff]  Max Packet=[2048]  IR/IT contexts=[4/6]
May  9 18:03:38 Jester kernel: [   38.629104] SCSI subsystem initialized
May  9 18:03:38 Jester kernel: [   38.635639] libata version 2.20 loaded.
May  9 18:03:38 Jester kernel: [   38.637430] pata_sis 0000:00:02.5: version 0.5.1
May  9 18:03:38 Jester kernel: [   38.637480] ACPI: PCI Interrupt 0000:00:02.5[A] -> GSI 16 (level, low) -> IRQ 17
May  9 18:03:38 Jester kernel: [   38.637586] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001a400 irq 14
May  9 18:03:38 Jester kernel: [   38.637628] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001a408 irq 15
May  9 18:03:38 Jester kernel: [   38.637649] scsi0 : pata_sis
May  9 18:03:38 Jester kernel: [   38.659791] usbcore: registered new interface driver usbfs
May  9 18:03:38 Jester kernel: [   38.659824] usbcore: registered new interface driver hub
May  9 18:03:38 Jester kernel: [   38.659850] usbcore: registered new device driver usb
May  9 18:03:38 Jester kernel: [   38.660872] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
May  9 18:03:38 Jester kernel: [   38.708980] sis900.c: v1.08.10 Apr. 2 2006
May  9 18:03:38 Jester kernel: [   38.818954] ata1.00: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360
May  9 18:03:38 Jester kernel: [   38.818960] ata1.00: ATA-5: WDC WD400JB-00ENA0, 05.03E05, max UDMA/100
May  9 18:03:38 Jester kernel: [   38.818963] ata1.00: 78165360 sectors, multi 16: LBA 
May  9 18:03:38 Jester kernel: [   38.819740] ata1.01: ata_hpa_resize 1: sectors = 87930864, hpa_sectors = 87930864
May  9 18:03:38 Jester kernel: [   38.819744] ata1.01: ATA-4: WDC WD450AA, 10.09K11, max UDMA/66
May  9 18:03:38 Jester kernel: [   38.819747] ata1.01: 87930864 sectors, multi 16: LBA 
May  9 18:03:38 Jester kernel: [   38.830899] ata1.00: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360
May  9 18:03:38 Jester kernel: [   38.830906] ata1.00: configured for UDMA/100
May  9 18:03:38 Jester kernel: [   38.842840] ata1.01: ata_hpa_resize 1: sectors = 87930864, hpa_sectors = 87930864
May  9 18:03:38 Jester kernel: [   38.842847] ata1.01: configured for UDMA/66
May  9 18:03:38 Jester kernel: [   38.842866] scsi1 : pata_sis
May  9 18:03:38 Jester kernel: [   38.868525] Floppy drive(s): fd0 is 1.44M
May  9 18:03:38 Jester kernel: [   38.929845] FDC 0 is a post-1991 82077
May  9 18:03:38 Jester kernel: [   39.333356] ata2.00: ATAPI, max UDMA/33
May  9 18:03:38 Jester kernel: [   39.333361] ata2.01: ATAPI, max UDMA/33
May  9 18:03:38 Jester kernel: [   39.501120] ata2.00: configured for UDMA/33
May  9 18:03:38 Jester kernel: [   39.668858] ata2.01: configured for UDMA/33
May  9 18:03:38 Jester kernel: [   39.669028] scsi 0:0:0:0: Direct-Access     ATA      WDC WD400JB-00EN 05.0 PQ: 0 ANSI: 5
May  9 18:03:38 Jester kernel: [   39.669472] scsi 0:0:1:0: Direct-Access     ATA      WDC WD450AA      10.0 PQ: 0 ANSI: 5
May  9 18:03:38 Jester kernel: [   39.671383] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-ROM SR-8588  7Z14 PQ: 0 ANSI: 5
May  9 18:03:38 Jester kernel: [   39.672900] scsi 1:0:1:0: CD-ROM            _NEC     DVD_RW ND-4551A  1-08 PQ: 0 ANSI: 5
May  9 18:03:38 Jester kernel: [   39.681785] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 20
May  9 18:03:38 Jester kernel: [   39.681811] ohci_hcd 0000:00:03.0: OHCI Host Controller
May  9 18:03:38 Jester kernel: [   39.682226] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
May  9 18:03:38 Jester kernel: [   39.682248] ohci_hcd 0000:00:03.0: irq 20, io mem 0xd6800000
May  9 18:03:38 Jester kernel: [   39.694705] SCSI device sda: 78165360 512-byte hdwr sectors (40021 MB)
May  9 18:03:38 Jester kernel: [   39.694721] sda: Write Protect is off
May  9 18:03:38 Jester kernel: [   39.694724] sda: Mode Sense: 00 3a 00 00
May  9 18:03:38 Jester kernel: [   39.694743] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  9 18:03:38 Jester kernel: [   39.694816] SCSI device sda: 78165360 512-byte hdwr sectors (40021 MB)
May  9 18:03:38 Jester kernel: [   39.694827] sda: Write Protect is off
May  9 18:03:38 Jester kernel: [   39.694829] sda: Mode Sense: 00 3a 00 00
May  9 18:03:38 Jester kernel: [   39.694847] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  9 18:03:38 Jester kernel: [   39.694852]  sda: sda1
May  9 18:03:38 Jester kernel: [   39.718734] sd 0:0:0:0: Attached scsi disk sda
May  9 18:03:38 Jester kernel: [   39.718931] SCSI device sdb: 87930864 512-byte hdwr sectors (45021 MB)
May  9 18:03:38 Jester kernel: [   39.718946] sdb: Write Protect is off
May  9 18:03:38 Jester kernel: [   39.718949] sdb: Mode Sense: 00 3a 00 00
May  9 18:03:38 Jester kernel: [   39.718968] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  9 18:03:38 Jester kernel: [   39.719024] SCSI device sdb: 87930864 512-byte hdwr sectors (45021 MB)
May  9 18:03:38 Jester kernel: [   39.719035] sdb: Write Protect is off
May  9 18:03:38 Jester kernel: [   39.719037] sdb: Mode Sense: 00 3a 00 00
May  9 18:03:38 Jester kernel: [   39.719055] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  9 18:03:38 Jester kernel: [   39.719058]  sdb: sdb1 sdb2 sdb3
May  9 18:03:38 Jester kernel: [   39.742637] usb usb1: configuration #1 chosen from 1 choice
May  9 18:03:38 Jester kernel: [   39.742668] hub 1-0:1.0: USB hub found
May  9 18:03:38 Jester kernel: [   39.742682] hub 1-0:1.0: 2 ports detected
May  9 18:03:38 Jester kernel: [   39.759362] sd 0:0:1:0: Attached scsi disk sdb
May  9 18:03:38 Jester kernel: [   39.766721] sd 0:0:0:0: Attached scsi generic sg0 type 0
May  9 18:03:38 Jester kernel: [   39.766865] sd 0:0:1:0: Attached scsi generic sg1 type 0
May  9 18:03:38 Jester kernel: [   39.767002] sr 1:0:0:0: Attached scsi generic sg2 type 5
May  9 18:03:38 Jester kernel: [   39.767132] scsi 1:0:1:0: Attached scsi generic sg3 type 5
May  9 18:03:38 Jester kernel: [   39.806372] sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
May  9 18:03:38 Jester kernel: [   39.806381] Uniform CD-ROM driver Revision: 3.20
May  9 18:03:38 Jester kernel: [   39.806692] sr 1:0:0:0: Attached scsi CD-ROM sr0
May  9 18:03:38 Jester kernel: [   39.815263] sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
May  9 18:03:38 Jester kernel: [   39.815562] sr 1:0:1:0: Attached scsi CD-ROM sr1
May  9 18:03:38 Jester kernel: [   39.848525] ACPI: PCI Interrupt 0000:00:03.1[b] -> GSI 21 (level, low) -> IRQ 18
May  9 18:03:38 Jester kernel: [   39.848551] ohci_hcd 0000:00:03.1: OHCI Host Controller
May  9 18:03:38 Jester kernel: [   39.848604] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
May  9 18:03:38 Jester kernel: [   39.848623] ohci_hcd 0000:00:03.1: irq 18, io mem 0xd6000000
May  9 18:03:38 Jester kernel: [   39.910405] usb usb2: configuration #1 chosen from 1 choice
May  9 18:03:38 Jester kernel: [   39.910438] hub 2-0:1.0: USB hub found
May  9 18:03:38 Jester kernel: [   39.910454] hub 2-0:1.0: 2 ports detected
May  9 18:03:38 Jester kernel: [   40.016298] ACPI: PCI Interrupt 0000:00:03.2[C] -> GSI 22 (level, low) -> IRQ 19
May  9 18:03:38 Jester kernel: [   40.016329] ohci_hcd 0000:00:03.2: OHCI Host Controller
May  9 18:03:38 Jester kernel: [   40.016357] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
May  9 18:03:38 Jester kernel: [   40.016377] ohci_hcd 0000:00:03.2: irq 19, io mem 0xd5800000
May  9 18:03:38 Jester kernel: [   40.078166] usb usb3: configuration #1 chosen from 1 choice
May  9 18:03:38 Jester kernel: [   40.078209] hub 3-0:1.0: USB hub found
May  9 18:03:38 Jester kernel: [   40.078225] hub 3-0:1.0: 2 ports detected
May  9 18:03:38 Jester kernel: [   40.103667] Attempting manual resume
May  9 18:03:38 Jester kernel: [   40.103672] swsusp: Resume From Partition 8:19
May  9 18:03:38 Jester kernel: [   40.103674] PM: Checking swsusp image.
May  9 18:03:38 Jester kernel: [   40.103925] PM: Resume from disk failed.
May  9 18:03:38 Jester kernel: [   40.123218] EXT3-fs: INFO: recovery required on readonly filesystem.
May  9 18:03:38 Jester kernel: [   40.123223] EXT3-fs: write access will be enabled during recovery.
May  9 18:03:38 Jester kernel: [   40.184200] PCI: Enabling device 0000:00:03.3 (0004 -> 0006)
May  9 18:03:38 Jester kernel: [   40.184216] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 23 (level, low) -> IRQ 21
May  9 18:03:38 Jester kernel: [   40.184237] ehci_hcd 0000:00:03.3: EHCI Host Controller
May  9 18:03:38 Jester kernel: [   40.184269] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 4
May  9 18:03:38 Jester kernel: [   40.184320] PCI: cache line size of 128 is not supported by device 0000:00:03.3
May  9 18:03:38 Jester kernel: [   40.184333] ehci_hcd 0000:00:03.3: irq 21, io mem 0xd5000000
May  9 18:03:38 Jester kernel: [   40.184339] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
May  9 18:03:38 Jester kernel: [   40.184426] usb usb4: configuration #1 chosen from 1 choice
May  9 18:03:38 Jester kernel: [   40.184458] hub 4-0:1.0: USB hub found
May  9 18:03:38 Jester kernel: [   40.184469] hub 4-0:1.0: 6 ports detected
May  9 18:03:38 Jester kernel: [   40.292031] PCI: Enabling device 0000:00:04.0 (0004 -> 0007)
May  9 18:03:38 Jester kernel: [   40.292049] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 22
May  9 18:03:38 Jester kernel: [   40.294455] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 1.
May  9 18:03:38 Jester kernel: [   40.310309] 0000:00:04.0: Using transceiver found at address 1 as default
May  9 18:03:38 Jester kernel: [   40.311415] eth0: SiS 900 PCI Fast Ethernet at 0x8800, IRQ 22, 00:e0:18:b5:16:fc.
May  9 18:03:38 Jester kernel: [   40.311533] ACPI: PCI Interrupt 0000:00:0d.0[A] -> GSI 17 (level, low) -> IRQ 16
May  9 18:03:38 Jester kernel: [   40.843002] usb 3-2: new full speed USB device using ohci_hcd and address 2
May  9 18:03:38 Jester kernel: [   41.050826] usb 3-2: configuration #1 chosen from 1 choice
May  9 18:03:38 Jester kernel: [   43.125643] kjournald starting.  Commit interval 5 seconds
May  9 18:03:38 Jester kernel: [   43.125669] EXT3-fs: recovery complete.
May  9 18:03:38 Jester kernel: [   43.132652] EXT3-fs: mounted filesystem with ordered data mode.
May  9 18:03:38 Jester kernel: [   55.307848] scsi2 : Adaptec AIC7XXX EISA/VLB/PCI SCSI HBA DRIVER, Rev 7.0
May  9 18:03:38 Jester kernel: [   55.307851]         <Adaptec 2940A Ultra SCSI adapter>
May  9 18:03:38 Jester kernel: [   55.307852]         aic7860: Ultra Single Channel A, SCSI Id=7, 3/253 SCBs
May  9 18:03:38 Jester kernel: [   55.307853] 
May  9 18:03:38 Jester kernel: [   55.308216] sata_promise 0000:00:0e.0: version 2.01
May  9 18:03:38 Jester kernel: [   55.308246] ACPI: PCI Interrupt 0000:00:0e.0[A] -> GSI 16 (level, low) -> IRQ 17
May  9 18:03:38 Jester kernel: [   55.308261] sata_promise PATA port found
May  9 18:03:38 Jester kernel: [   55.323645] ata3: SATA max UDMA/133 cmd 0xf8880200 ctl 0xf8880238 bmdma 0x00000000 irq 17
May  9 18:03:38 Jester kernel: [   55.327136] ata4: SATA max UDMA/133 cmd 0xf8880280 ctl 0xf88802b8 bmdma 0x00000000 irq 17
May  9 18:03:38 Jester kernel: [   55.327317] ata5: PATA max UDMA/133 cmd 0xf8880300 ctl 0xf8880338 bmdma 0x00000000 irq 17
May  9 18:03:38 Jester kernel: [   55.327338] scsi3 : sata_promise
May  9 18:03:38 Jester kernel: [   55.795072] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
May  9 18:03:38 Jester kernel: [   55.847329] ata3.00: ata_hpa_resize 1: sectors = 625142448, hpa_sectors = 625142448
May  9 18:03:38 Jester kernel: [   55.847339] ata3.00: ATA-7: ST3320620AS, 3.AAK, max UDMA/133
May  9 18:03:38 Jester kernel: [   55.847342] ata3.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 0/32)
May  9 18:03:38 Jester kernel: [   55.913861] ata3.00: ata_hpa_resize 1: sectors = 625142448, hpa_sectors = 625142448
May  9 18:03:38 Jester kernel: [   55.913871] ata3.00: configured for UDMA/133
May  9 18:03:38 Jester kernel: [   55.913886] scsi4 : sata_promise
May  9 18:03:38 Jester kernel: [   56.226385] ata4: SATA link down (SStatus 0 SControl 300)
May  9 18:03:38 Jester kernel: [   56.226407] scsi5 : sata_promise
May  9 18:03:38 Jester kernel: [   56.382252] scsi: waiting for bus probes to complete ...
May  9 18:03:38 Jester kernel: [   56.878858] NET: Registered protocol family 17
May  9 18:03:38 Jester kernel: [   57.146008] scsi 3:0:0:0: Direct-Access     ATA      ST3320620AS      3.AA PQ: 0 ANSI: 5
May  9 18:03:38 Jester kernel: [   57.149987] SCSI device sdc: 625142448 512-byte hdwr sectors (320073 MB)
May  9 18:03:38 Jester kernel: [   57.153159] sdc: Write Protect is off
May  9 18:03:38 Jester kernel: [   57.153163] sdc: Mode Sense: 00 3a 00 00
May  9 18:03:38 Jester kernel: [   57.157135] SCSI device sdc: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  9 18:03:38 Jester kernel: [   57.161145] SCSI device sdc: 625142448 512-byte hdwr sectors (320073 MB)
May  9 18:03:38 Jester kernel: [   57.161994] sdc: Write Protect is off
May  9 18:03:38 Jester kernel: [   57.161999] sdc: Mode Sense: 00 3a 00 00
May  9 18:03:38 Jester kernel: [   57.165970] SCSI device sdc: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  9 18:03:38 Jester kernel: [   57.165978]  sdc: sdc1
May  9 18:03:38 Jester kernel: [   57.184739] sd 3:0:0:0: Attached scsi disk sdc
May  9 18:03:38 Jester kernel: [   57.184837] sd 3:0:0:0: Attached scsi generic sg4 type 0
May  9 18:03:38 Jester kernel: [   57.358366] eth0: Media Link On 100mbps full-duplex 
May  9 18:03:38 Jester kernel: [   57.593372] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
May  9 18:03:38 Jester kernel: [   57.630354] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
May  9 18:03:38 Jester kernel: [   57.660932] Linux video capture interface: v2.00
May  9 18:03:38 Jester kernel: [   57.753258] Linux agpgart interface v0.102 (c) Dave Jones
May  9 18:03:38 Jester kernel: [   57.765890] agpgart: Detected SiS 648 chipset
May  9 18:03:38 Jester kernel: [   57.770057] agpgart: AGP aperture is 64M @ 0xd8000000
May  9 18:03:38 Jester kernel: [   57.939846] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0xe600
May  9 18:03:38 Jester kernel: [   58.007965] bttv: driver version 0.9.16 loaded
May  9 18:03:38 Jester kernel: [   58.007984] bttv: using 8 buffers with 2080k (520 pages) each for capture
May  9 18:03:38 Jester kernel: [   58.008063] bttv: Bt8xx card found (0).
May  9 18:03:38 Jester kernel: [   58.008077] PCI: Enabling device 0000:00:0b.0 (0004 -> 0006)
May  9 18:03:38 Jester kernel: [   58.008087] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 19 (level, low) -> IRQ 22
May  9 18:03:38 Jester kernel: [   58.008103] bttv0: Bt879 (rev 2) at 0000:00:0b.0, irq: 22, latency: 32, mmio: 0xdf000000
May  9 18:03:38 Jester kernel: [   58.008117] bttv0: detected: FlyVideo 98FM (LR50)/ Typhoon TView TV/FM Tuner [card=36], PCI subsystem ID is 1852:1852
May  9 18:03:38 Jester kernel: [   58.008121] bttv0: using: Lifeview FlyVideo 98FM LR50 / Typhoon TView TV/FM Tuner [card=36,autodetected]
May  9 18:03:38 Jester kernel: [   58.008154] bttv0: gpio: en=00000000, out=00000000 in=00f4ff00 [init]
May  9 18:03:38 Jester kernel: [   58.008660] bttv0: FlyVideo Radio=yes RemoteControl=yes Tuner=5 gpio=0xf4ff00
May  9 18:03:38 Jester kernel: [   58.008662] bttv0: FlyVideo  LR90=no  tda9821/tda9820=no  capture_only=no 
May  9 18:03:38 Jester kernel: [   58.008666] bttv0: using tuner=5
May  9 18:03:38 Jester kernel: [   58.008669] bttv0: i2c: checking for MSP34xx @ 0x80... not found
May  9 18:03:38 Jester kernel: [   58.009489] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
May  9 18:03:38 Jester kernel: [   58.010308] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
May  9 18:03:38 Jester kernel: [   58.011119] bttv0: i2c: checking for TDA9887 @ 0x86... not found
May  9 18:03:38 Jester kernel: [   58.040920] tuner 1-0061: chip found @ 0xc2 (bt879 #0 [sw])
May  9 18:03:38 Jester kernel: [   58.040956] tuner 1-0061: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
May  9 18:03:38 Jester kernel: [   58.040960] tuner 1-0061: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
May  9 18:03:38 Jester kernel: [   58.052518] bttv0: registered device video0
May  9 18:03:38 Jester kernel: [   58.052551] bttv0: registered device vbi0
May  9 18:03:38 Jester kernel: [   58.052584] bttv0: registered device radio0
May  9 18:03:38 Jester kernel: [   58.052606] bttv0: PLL: 28636363 => 35468950 .. ok
May  9 18:03:38 Jester kernel: [   58.419711] input: PC Speaker as /class/input/input2
May  9 18:03:38 Jester kernel: [   58.457982] parport: PnPBIOS parport detected.
May  9 18:03:38 Jester kernel: [   58.458104] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
May  9 18:03:38 Jester kernel: [   58.777161] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
May  9 18:03:38 Jester kernel: [   58.787683] cdc_acm 3-2:1.0: ttyACM0: USB ACM device
May  9 18:03:38 Jester kernel: [   58.793190] PCI: Enabling device 0000:00:02.7 (0004 -> 0005)
May  9 18:03:38 Jester kernel: [   58.793206] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 23
May  9 18:03:38 Jester kernel: [   58.793982] usbcore: registered new interface driver cdc_acm
May  9 18:03:38 Jester kernel: [   58.793988] drivers/usb/class/cdc-acm.c: v0.25:USB Abstract Control Model driver for USB modems and ISDN adapters
May  9 18:03:38 Jester kernel: [   59.118483] intel8x0_measure_ac97_clock: measured 58811 usecs
May  9 18:03:38 Jester kernel: [   59.118488] intel8x0: clocking to 48000
May  9 18:03:38 Jester kernel: [   59.518104] fuse init (API version 7.8)
May  9 18:03:38 Jester kernel: [   59.544210] lp0: using parport0 (interrupt-driven).
May  9 18:03:38 Jester kernel: [   59.612113] Adding 1951888k swap on /dev/disk/by-uuid/c5c37104-8d0a-4ffe-9bca-1224b1e99a35.  Priority:-1 extents:1 across:1951888k
May  9 18:03:38 Jester kernel: [   59.802419] EXT3 FS on sdb1, internal journal
May  9 18:03:38 Jester kernel: [   60.363939] NTFS driver 2.1.28 [Flags: R/O MODULE].
May  9 18:03:38 Jester kernel: [   60.412985] NTFS volume version 3.1.
May  9 18:03:38 Jester kernel: [   60.461863] NTFS volume version 3.1.
May  9 18:03:38 Jester kernel: [   60.493936] kjournald starting.  Commit interval 5 seconds
May  9 18:03:38 Jester kernel: [   60.494127] EXT3 FS on sdb2, internal journal
May  9 18:03:38 Jester kernel: [   60.494133] EXT3-fs: mounted filesystem with ordered data mode.
May  9 18:03:38 Jester kernel: [   60.861382] NET: Registered protocol family 10
May  9 18:03:38 Jester kernel: [   60.861507] lo: Disabled Privacy Extensions
May  9 18:03:38 Jester kernel: [   65.965906] No dock devices found.
May  9 18:03:38 Jester kernel: [   65.986841] Using specific hotkey driver
May  9 18:03:38 Jester kernel: [   66.066229] input: Power Button (FF) as /class/input/input4
May  9 18:03:38 Jester kernel: [   66.071616] ACPI: Power Button (FF) [PWRF]
May  9 18:03:38 Jester kernel: [   66.107266] input: Power Button (CM) as /class/input/input5
May  9 18:03:38 Jester kernel: [   66.112598] ACPI: Power Button (CM) [PWRB]
May  9 18:03:38 Jester kernel: [   66.134203] ibm_acpi: ec object not found
May  9 18:03:38 Jester kernel: [   66.297467] pcc_acpi: loading...
May  9 18:03:41 Jester dhcdbd: Started up.
 May  9 18:03:41 Jester NetworkManager: <information>^Istarting... 
 May  9 18:03:41 Jester NetworkManager: <information>^Ieth0: Device is fully-supported using driver 'sis900'. 
 May  9 18:03:41 Jester NetworkManager: <information>^Inm_device_init(): waiting for device's worker thread to start 
 May  9 18:03:41 Jester avahi-daemon[4964]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
 May  9 18:03:41 Jester avahi-daemon[4964]: Successfully dropped root privileges.
 May  9 18:03:41 Jester avahi-daemon[4964]: avahi-daemon 0.6.17 starting up.
 May  9 18:03:41 Jester avahi-daemon[4964]: Successfully called chroot().
 May  9 18:03:41 Jester avahi-daemon[4964]: Successfully dropped remaining capabilities.
 May  9 18:03:41 Jester avahi-daemon[4964]: No service found in /etc/avahi/services.
 May  9 18:03:41 Jester avahi-daemon[4964]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.101.
 May  9 18:03:41 Jester avahi-daemon[4964]: New relevant interface eth0.IPv4 for mDNS.
 May  9 18:03:41 Jester avahi-daemon[4964]: Network interface enumeration completed.
 May  9 18:03:41 Jester avahi-daemon[4964]: Registering new address record for fe80::2e0:18ff:feb5:16fc on eth0.*.
 May  9 18:03:41 Jester avahi-daemon[4964]: Registering new address record for 192.168.1.101 on eth0.IPv4.
 May  9 18:03:41 Jester avahi-daemon[4964]: Registering HINFO record with values 'I686'/'LINUX'.
 May  9 18:03:41 Jester NetworkManager: <information>^Inm_device_init(): device's worker thread started, continuing. 
 May  9 18:03:41 Jester NetworkManager: <information>^INow managing wired Ethernet (802.3) device 'eth0'. 
 May  9 18:03:41 Jester NetworkManager: <information>^IDeactivating device eth0. 
 May  9 18:03:41 Jester avahi-daemon[4964]: Withdrawing address record for 192.168.1.101 on eth0.
 May  9 18:03:41 Jester avahi-daemon[4964]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.101.
 May  9 18:03:41 Jester avahi-daemon[4964]: Interface eth0.IPv4 no longer relevant for mDNS.
 May  9 18:03:41 Jester avahi-daemon[4964]: Withdrawing address record for fe80::2e0:18ff:feb5:16fc on eth0.
 May  9 18:03:42 Jester dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
 May  9 18:03:42 Jester NetworkManager: <information>^IWill activate wired connection 'eth0' because it now has a link. 
 May  9 18:03:42 Jester NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
 May  9 18:03:42 Jester dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
 May  9 18:03:42 Jester NetworkManager: <information>^IWill activate connection 'eth0'. 
 May  9 18:03:42 Jester NetworkManager: <information>^IDevice eth0 activation scheduled... 
 May  9 18:03:42 Jester NetworkManager: <information>^IActivation (eth0) started... 
 May  9 18:03:42 Jester NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
 May  9 18:03:42 Jester NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
 May  9 18:03:42 Jester NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
 May  9 18:03:42 Jester NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
 May  9 18:03:42 Jester NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
 May  9 18:03:42 Jester NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful. 
 May  9 18:03:42 Jester NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
 May  9 18:03:42 Jester NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
 May  9 18:03:42 Jester NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started... 
 May  9 18:03:43 Jester kernel: [   71.662263] [drm] Initialized drm 1.1.0 20060810
 May  9 18:03:43 Jester kernel: [   71.686199] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 17
 May  9 18:03:43 Jester kernel: [   71.689807] [drm] Initialized radeon 1.25.0 20060524 on minor 0
 May  9 18:03:43 Jester NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction. 
 May  9 18:03:43 Jester NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
 May  9 18:03:43 Jester NetworkManager: <information>^IDHCP daemon state is now 12 (successfully started) for interface eth0 
 May  9 18:03:44 Jester kernel: [   72.414141] ppdev: user-space parallel port driver
 May  9 18:03:44 Jester hpiod: 1.7.3 accepting connections at 2208... 
 May  9 18:03:44 Jester kernel: [   73.211773] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
 May  9 18:03:44 Jester kernel: [   73.211938] agpgart: Putting AGP V3 device at 0000:00:00.0 into 4x mode
 May  9 18:03:44 Jester kernel: [   73.211944] agpgart: SiS delay workaround: giving bridge time to recover.
 May  9 18:03:44 Jester kernel: [   73.227661] agpgart: Putting AGP V3 device at 0000:01:00.0 into 4x mode
 May  9 18:03:44 Jester NetworkManager: <information>^IDHCP daemon state is now 1 (starting) for interface eth0 
 May  9 18:03:45 Jester kernel: [   73.465572] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
 May  9 18:03:45 Jester kernel: [   73.465578] apm: overridden by ACPI.
 May  9 18:03:45 Jester kernel: [   73.542606] [drm] Setting GART location based on new memory map
 May  9 18:03:45 Jester kernel: [   73.542625] [drm] Loading R200 Microcode
 May  9 18:03:45 Jester kernel: [   73.542670] [drm] writeback test succeeded in 1 usecs
 May  9 18:03:45 Jester hcid[5243]: Bluetooth HCI daemon
 May  9 18:03:45 Jester kernel: [   73.806034] Bluetooth: Core ver 2.11
 May  9 18:03:45 Jester kernel: [   73.806111] NET: Registered protocol family 31
 May  9 18:03:45 Jester kernel: [   73.806114] Bluetooth: HCI device and connection manager initialized
 May  9 18:03:45 Jester kernel: [   73.806118] Bluetooth: HCI socket layer initialized
 May  9 18:03:45 Jester NetworkManager: <debug info>^I[1178723025.445149] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
 May  9 18:03:45 Jester hcid[5243]: Starting SDP server
 May  9 18:03:45 Jester kernel: [   73.901676] Bluetooth: L2CAP ver 2.8
 May  9 18:03:45 Jester kernel: [   73.901682] Bluetooth: L2CAP socket layer initialized
 May  9 18:03:45 Jester kernel: [   73.969096] Bluetooth: RFCOMM socket layer initialized
 May  9 18:03:45 Jester kernel: [   73.969114] Bluetooth: RFCOMM TTY layer initialized
 May  9 18:03:45 Jester kernel: [   73.969117] Bluetooth: RFCOMM ver 1.8
 May  9 18:03:45 Jester anacron[5283]: Anacron 2.3 started on 2007-05-09
 May  9 18:03:45 Jester anacron[5283]: Normal exit (0 jobs run)
 May  9 18:03:45 Jester /usr/sbin/cron[5310]: (CRON) INFO (pidfile fd = 3)
 May  9 18:03:45 Jester /usr/sbin/cron[5311]: (CRON) STARTUP (fork ok)
 May  9 18:03:45 Jester /usr/sbin/cron[5311]: (CRON) INFO (Running @reboot jobs)
 May  9 18:03:46 Jester dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
 May  9 18:03:46 Jester dhclient: DHCPACK from 192.168.1.1
 May  9 18:03:46 Jester avahi-daemon[4964]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.101.
 May  9 18:03:46 Jester avahi-daemon[4964]: New relevant interface eth0.IPv4 for mDNS.
 May  9 18:03:46 Jester avahi-daemon[4964]: Registering new address record for 192.168.1.101 on eth0.IPv4.
 May  9 18:03:46 Jester NetworkManager: <information>^IDHCP daemon state is now 4 (reboot) for interface eth0 
 May  9 18:03:46 Jester NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
 May  9 18:03:46 Jester NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) started... 
 May  9 18:03:46 Jester dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
 May  9 18:03:46 Jester dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
 May  9 18:03:46 Jester dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
 May  9 18:03:46 Jester NetworkManager: <information>^IRetrieved the following IP4 configuration from the DHCP daemon: 
 May  9 18:03:46 Jester NetworkManager: <information>^I  address 192.168.1.101 
 May  9 18:03:46 Jester NetworkManager: <information>^I  netmask 255.255.255.0 
 May  9 18:03:46 Jester NetworkManager: <information>^I  broadcast 192.168.1.255 
 May  9 18:03:46 Jester NetworkManager: <information>^I  gateway 192.168.1.1 
 May  9 18:03:46 Jester NetworkManager: <information>^I  nameserver 193.92.150.3 
 May  9 18:03:46 Jester NetworkManager: <information>^I  nameserver 194.219.227.1 
 May  9 18:03:46 Jester NetworkManager: <information>^I  nameserver 192.168.1.1 
 May  9 18:03:46 Jester NetworkManager: <information>^I  domain name 'domain_not_set.invalid' 
 May  9 18:03:46 Jester NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
 May  9 18:03:46 Jester NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
 May  9 18:03:46 Jester NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
 May  9 18:03:46 Jester avahi-daemon[4964]: Withdrawing address record for 192.168.1.101 on eth0.
 May  9 18:03:46 Jester avahi-daemon[4964]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.101.
 May  9 18:03:46 Jester avahi-daemon[4964]: Interface eth0.IPv4 no longer relevant for mDNS.
 May  9 18:03:46 Jester avahi-daemon[4964]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.101.
 May  9 18:03:46 Jester avahi-daemon[4964]: New relevant interface eth0.IPv4 for mDNS.
 May  9 18:03:46 Jester avahi-daemon[4964]: Registering new address record for 192.168.1.101 on eth0.IPv4.
 May  9 18:03:46 Jester dhclient: bound to 192.168.1.101 -- renewal in 39748 seconds.
 May  9 18:03:47 Jester NetworkManager: <information>^IClearing nscd hosts cache. 
 May  9 18:03:47 Jester NetworkManager: <WARNING>^I nm_spawn_process (): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
 May  9 18:03:47 Jester NetworkManager: <information>^IActivation (eth0) successful, device activated. 
 May  9 18:03:47 Jester NetworkManager: <information>^IActivation (eth0) Finish handler scheduled. 
 May  9 18:03:47 Jester NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
 May  9 18:03:48 Jester avahi-daemon[4964]: Registering new address record for fe80::2e0:18ff:feb5:16fc on eth0.*.
 May  9 18:03:49 Jester ntpdate[5449]: adjust time server 82.211.81.145 offset -0.201402 sec
 May  9 18:03:53 Jester gconfd (harry-5499): starting (version 2.18.0.1), pid 5499 user 'harry'
 May  9 18:03:53 Jester gconfd (harry-5499): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
 May  9 18:03:53 Jester gconfd (harry-5499): Resolved address "xml:readwrite:/home/harry/.gconf" to a writable configuration source at position 1
 May  9 18:03:53 Jester gconfd (harry-5499): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
 May  9 18:03:53 Jester gconfd (harry-5499): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
 May  9 18:03:53 Jester gconfd (harry-5499): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
 May  9 18:03:57 Jester kernel: [   85.563007] eth0: no IPv6 routers present
 May  9 18:03:59 Jester gconfd (harry-5499): Resolved address "xml:readwrite:/home/harry/.gconf" to a writable configuration source at position 0
 May  9 18:04:00 Jester NetworkManager: <information>^IUpdating allowed wireless network lists. 
 May  9 18:04:01 Jester NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored..

```How do i check for the drivers?

edit: Installed ati drivers (open source) and still same problems

---

### Post by JesterGr on 2007-05-10
bump. Only 10 or 20 users have this problem? no news till now?

---

### Post by gohanssjn on 2007-05-10
> **Inxsible said:**
> Are you using the restricted drivers too ?
 
Could you maybe try out the Suspend and Hibernate and Switch User options and let me know what happens ?
 
I am not currently on my Ubuntu machine...so I shall try those later in the evening and let you know what happens on my machine

Same issues here with Nvidia restricted drivers.  I pray for a fix soon.  I hate having to open every program each time I restart :(

---

### Post by dlugidll on 2007-05-10
sory for my english
i have Video intel card 852GM in notebook toshiba 150-106 
and the same problem whit suspend
*not syncing fatal exception in interrupt *
and i use wifi card on PCMCIA Orinoco Gold 8470-wd
i use restricted drivers

maby it is solution for this problem ??

---

### Post by Inxsible on 2007-05-10
> **gohanssjn said:**
> Same issues here with Nvidia restricted drivers. I pray for a fix soon. I hate having to open every program each time I restart :(
 
We need to actually find out if it is because of the restricted drivers..I plan to disable my restricted drivers and then try to see if Hibernate, Logout work. If they do, then atleast we can find out the source of the problem !
 
So lets take a step back before we criticize the NVidia drivers.
 
 
Until later....

---

### Post by JesterGr on 2007-05-10
>  So lets take a step back before we criticize the NVidia drivers.
as i said, i have the same problem with ATI, so i don't think it's nVidia 's fault

---

### Post by Inxsible on 2007-05-10
Check this post started by me..
 
[http://ubuntuforums.org/showthread.php?t=431792](http://ubuntuforums.org/showthread.php?t=431792)
 
The last couple of posts have outlined "somewhat of a solution" even on the next page there is 1.
 
But I think they entail you to STOP using the restricted drivers. I would rather prefer not doing that, coz I can live with my Hibernate and Logout buttons not working rather than taking a performance hit on my graphics.
 
I paid extra for the NVidia card...i might as well use it !

---

### Post by gohanssjn on 2007-05-10
> **Inxsible said:**
> We need to actually find out if it is because of the restricted drivers..I plan to disable my restricted drivers and then try to see if Hibernate, Logout work. If they do, then atleast we can find out the source of the problem !
 
So lets take a step back before we criticize the NVidia drivers.
 
 
Until later....

I am pretty sure I tried that before and the Hibernation was successful actually.  I don't want to really critisize them, I just want a work around :D

---

### Post by gohanssjn on 2007-05-10
Ok, disabled nvidia-glx and hibernated, everything worked great.

Definately my issue is with that package...

---

### Post by dlugidll on 2007-05-11
maby µswsusp will be work too
[http://suspend.sourceforge.net/index.shtml](http://suspend.sourceforge.net/index.shtml)
i use **s2ram -f** and **s2disk**
works fine


**sudo apt-get install uswsusp**
pls copy text from this site
[http://ubuntu.zamber.net/hibernacja/hal-system-power-hibernate-linux](http://ubuntu.zamber.net/hibernacja/hal-system-power-hibernate-linux)
and save as file 
hal-system-power-hibernate-linux

copy text from this site
[http://ubuntu.zamber.net/hibernacja/hal-system-power-suspend-linux](http://ubuntu.zamber.net/hibernacja/hal-system-power-suspend-linux)
and save as file 
hal-system-power-suspend-linux

then
sudo cp hal-system-* /usr/lib/hal/scripts/linux/
sudo chmod 755 /usr/lib/hal/scripts/linux/*

i need change line 84 in file 
/usr/lib/hal/scripts/linux/hal-system-power-suspend-linux
from /sbin/s2ram to /sbin/s2ram -f

works fine for me
on this site you can find few special steps for machine with NVidia card and ATI
[http://en.opensuse.org/S2ram](http://en.opensuse.org/S2ram)


works for mee bether, then after install Kubuntu 7.04 and 6.10

i copy this instruction from 
[http://zamber.net/hibernacja-pod-ubuntu](http://zamber.net/hibernacja-pod-ubuntu)

---

### Post by dc. on 2007-05-16
When I hibernate and then resume my hard-disk is switched from udma5 (correct) to udma2 (not so good!)
Also my parallel port stops working, so that I'm unable to print after every resume and have to reboot!

I'm using the ati not restricted drivers.

---

