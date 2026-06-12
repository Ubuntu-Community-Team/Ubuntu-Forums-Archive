---
title: "ESSID not loading up!??!"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by Dual Cortex on 2006-10-29
This is my /etc/network/interfaces file, and as you see I'm on a wireless adapter:

```
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

iface eth0 inet dhcp

auto eth1
iface eth1 inet static
wireless-key **********
wireless-essid MGTComputers
address 192.168.0.108
netmask 255.255.255.0
gateway 192.168.0.1


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```


Now, for some reason the ESSID is not loading up when I log on to Kubuntu, and the following is the ouput of 'sudo iwconfig' right when I log on:


```
eth1      802.11g zd1211  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Invalid
          Bit Rate=1 Mb/s
          Encryption key:****-****-**   Security mode:open
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```


Every time I want to go online I must issue the 
```
sudo iwconfig eth1 essid "MGTComputers"
```
command to be able to access the internet.


SOoooo what's wrong?


EDIT: yay! lol, I just noticed my "rank" picture changed \\:D/!

---

### Post by Dual Cortex on 2006-10-29
Well... I guess I'll check back for an answer tomorrow morning.

---

### Post by Dual Cortex on 2006-10-30
I guess I'll check back this afternoon!
\\:D/

---

### Post by dmizer on 2006-10-30
i think they need to be put in the right order and add an option like so:
```
auto eth1
iface eth1 inet static
wireless-mode managed
wireless-essid MGTComputers
wireless-key **********
address 192.168.0.108
netmask 255.255.255.0
gateway 192.168.0.1
```

---

### Post by wieman01 on 2006-10-30
Just noticed that the "auto" line for the loopback-interfaces is missing:
> **[COLOR="Red"]auto lo[/COLOR]**
iface lo inet loopback

---

### Post by dmizer on 2006-10-30
> **wieman01 said:**
> Just noticed that the "auto" line for the loopback-interfaces is missing:

humm, not sure, but i don't think it needs to be auto because he has it statically assigned.

---

### Post by wieman01 on 2006-10-30
> **dmizer said:**
> humm, not sure, but i don't think it needs to be auto because he has it statically assigned.
Not sure either. Was just a shot in the blue frankly speaking.

---

### Post by wieman01 on 2006-10-30
Is this an open network with WEP encryption enabled? Strange... Can you replace the key line with:
> wireless-key open [COLOR="Red"]your_wep_key[/COLOR]
But I reckon the sequence as Dmizer has highlighed will do the trick.

---

### Post by Dual Cortex on 2006-10-30
> **wieman01 said:**
> Just noticed that the "auto" line for the loopback-interfaces is missing:

I actually have that in my interfaces file.... I guess I cut that part out by accident.

> auto eth1
iface eth1 inet static
wireless-mode managed
wireless-essid MGTComputers
wireless-key **********
address 192.168.0.108
netmask 255.255.255.0
gateway 192.168.0.1

That didn't work :(

---

### Post by dmizer on 2006-10-30
> **Dual Cortex said:**
> That didn't work :(

try posting the output of dmesg.  please wrap dmesg in [quote] or [code] tags.

---

### Post by Dual Cortex on 2006-10-30
```
felipe@LinuxDesktop:~$ sudo dmesg
Password:
[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001fe88c00 (usable)
[17179569.184000]  BIOS-e820: 000000001fe88c00 - 000000001fe8ac00 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000001fe8ac00 - 000000001fe8cc00 (ACPI data)
[17179569.184000]  BIOS-e820: 000000001fe8cc00 - 0000000020000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fed00400 (reserved)
[17179569.184000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 510MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000fe710
[17179569.184000] On node 0 totalpages: 130696
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 126600 pages, LIFO batch:31
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 DELL                                  ) @ 0x000fec00
[17179569.184000] ACPI: RSDT (v001 DELL    4700    0x00000007 ASL  0x00000061) @ 0x000fcc12
[17179569.184000] ACPI: FADT (v001 DELL    4700    0x00000007 ASL  0x00000061) @ 0x000fcc52
[17179569.184000] ACPI: SSDT (v001   DELL    st_ex 0x00001000 MSFT 0x0100000d) @ 0xfffc6120
[17179569.184000] ACPI: MADT (v001 DELL    4700    0x00000007 ASL  0x00000061) @ 0x000fccc6
[17179569.184000] ACPI: BOOT (v001 DELL    4700    0x00000007 ASL  0x00000061) @ 0x000fcd38
[17179569.184000] ACPI: ASF! (v016 DELL    4700    0x00000007 ASL  0x00000061) @ 0x000fcd60
[17179569.184000] ACPI: MCFG (v001 DELL    4700    0x00000007 ASL  0x00000061) @ 0x000fcdc7
[17179569.184000] ACPI: HPET (v001 DELL    4700    0x00000007 ASL  0x00000061) @ 0x000fce05
[17179569.184000] ACPI: DSDT (v001   DELL    dt_ex 0x00001000 MSFT 0x0100000d) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x808
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:4 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[17179569.184000] Processor #1 15:4 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] disabled)
[17179569.184000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x07] disabled)
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0xff] high level lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:c0000000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/sda1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[17179569.184000] Console: colour VGA+ 80x25
[17179569.184000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.184000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179569.184000] Memory: 508392k/522784k available (1910k kernel code, 13836k reserved, 1070k data, 308k init, 0k highmem)
[17179569.184000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.184000] hpet0: at MMIO 0xfed00000 (virtual 0xe0800000), IRQs 2, 8, 0
[17179569.184000] hpet0: 3 64-bit timers, 14318180 Hz
[17179569.184000] Using HPET for base-timer
[17179569.184000] Using HPET for gettimeofday
[17179569.184000] Detected 2992.593 MHz processor.
[17179569.184000] Using hpet for high-res timesource
[17179569.268000] Calibrating delay using timer specific routine.. 5990.44 BogoMIPS (lpj=11980897)
[17179569.268000] Security Framework v1.0.0 initialized
[17179569.268000] SELinux:  Disabled at boot.
[17179569.268000] Mount-cache hash table entries: 512
[17179569.268000] CPU: After generic identify, caps: bfebfbff 00100000 00000000 00000000 0000441d 00000000 00000000
[17179569.268000] CPU: After vendor identify, caps: bfebfbff 00100000 00000000 00000000 0000441d 00000000 00000000
[17179569.268000] monitor/mwait feature present.
[17179569.268000] using mwait in idle threads.
[17179569.268000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[17179569.268000] CPU: L2 cache: 1024K
[17179569.268000] CPU: Hyper-Threading is disabled
[17179569.268000] CPU: After all inits, caps: bfebfbff 00100000 00000000 00000180 0000441d 00000000 00000000
[17179569.268000] Checking 'hlt' instruction... OK.
[17179569.284000] SMP alternatives: switching to UP code
[17179569.284000] checking if image is initramfs... it is
[17179569.720000] Freeing initrd memory: 5523k freed
[17179569.720000] ACPI: Core revision 20060707
[17179569.720000] ACPI: Looking for DSDT ... not found!
[17179569.748000] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 01
[17179569.748000] SMP alternatives: switching to SMP code
[17179569.748000] Booting processor 1/1 eip 3000
[17179569.760000] Initializing CPU#1
[17179569.840000] Calibrating delay using timer specific routine.. 5985.14 BogoMIPS (lpj=11970297)
[17179569.840000] CPU: After generic identify, caps: bfebfbff 00100000 00000000 00000000 0000441d 00000000 00000000
[17179569.840000] CPU: After vendor identify, caps: bfebfbff 00100000 00000000 00000000 0000441d 00000000 00000000
[17179569.840000] monitor/mwait feature present.
[17179569.840000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[17179569.840000] CPU: L2 cache: 1024K
[17179569.840000] CPU: Hyper-Threading is disabled
[17179569.840000] CPU: After all inits, caps: bfebfbff 00100000 00000000 00000180 0000441d 00000000 00000000
[17179569.840000] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 01
[17179569.840000] Total of 2 processors activated (11975.59 BogoMIPS).
[17179569.840000] ENABLING IO-APIC IRQs
[17179569.840000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179569.988000] checking TSC synchronization across 2 CPUs: passed.
[17179569.992000] Brought up 2 CPUs
[17179570.096000] migration_cost=4000
[17179570.096000] NET: Registered protocol family 16
[17179570.096000] EISA bus registered
[17179570.096000] ACPI: bus type pci registered
[17179570.096000] PCI: Using MMCONFIG
[17179570.096000] Setting up standard PCI resources
[17179570.116000] ACPI: Interpreter enabled
[17179570.116000] ACPI: Using IOAPIC for interrupt routing
[17179570.120000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.120000] PCI: Probing PCI hardware (bus 00)
[17179570.120000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179570.136000] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[17179570.136000] PCI quirk: region 0880-08bf claimed by ICH6 GPIO
[17179570.136000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179570.136000] Boot video device is 0000:01:00.0
[17179570.136000] PCI: Transparent bridge - 0000:00:1e.0
[17179570.136000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.560000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[17179570.564000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI2._PRT]
[17179570.572000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI4._PRT]
[17179570.604000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[17179570.604000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[17179570.604000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[17179570.608000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[17179570.608000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[17179570.608000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[17179570.608000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[17179570.608000] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 9 10 11 12 15)
[17179570.608000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.608000] pnp: PnP ACPI init
[17179570.644000] pnp: PnP ACPI: found 13 devices
[17179570.644000] PnPBIOS: Disabled by ACPI PNP
[17179570.644000] PCI: Using ACPI for IRQ routing
[17179570.644000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.652000] pnp: 00:01: ioport range 0x800-0x85f could not be reserved
[17179570.652000] pnp: 00:01: ioport range 0xc00-0xc7f has been reserved
[17179570.652000] pnp: 00:01: ioport range 0x860-0x8ff could not be reserved
[17179570.652000] pnp: 00:0b: ioport range 0x100-0x1fe has been reserved
[17179570.652000] pnp: 00:0b: ioport range 0x200-0x277 has been reserved
[17179570.652000] pnp: 00:0b: ioport range 0x280-0x2e7 has been reserved
[17179570.652000] pnp: 00:0b: ioport range 0x2e8-0x2ef has been reserved
[17179570.652000] pnp: 00:0b: ioport range 0x2f0-0x2f7 has been reserved
[17179570.652000] pnp: 00:0b: ioport range 0x2f8-0x2ff has been reserved
[17179570.652000] pnp: 00:0b: ioport range 0x300-0x377 has been reserved
[17179570.652000] pnp: 00:0b: ioport range 0x380-0x3bb has been reserved
[17179570.652000] PCI: Bridge: 0000:00:01.0
[17179570.652000]   IO window: disabled.
[17179570.652000]   MEM window: dd000000-dfefffff
[17179570.652000]   PREFETCH window: c0000000-cfffffff
[17179570.652000] PCI: Bridge: 0000:00:1c.0
[17179570.652000]   IO window: disabled.
[17179570.652000]   MEM window: dcf00000-dcffffff
[17179570.652000]   PREFETCH window: disabled.
[17179570.652000] PCI: Bridge: 0000:00:1e.0
[17179570.652000]   IO window: d000-dfff
[17179570.652000]   MEM window: dce00000-dcefffff
[17179570.652000]   PREFETCH window: disabled.
[17179570.652000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179570.652000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179570.652000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179570.652000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179570.652000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179570.652000] NET: Registered protocol family 2
[17179570.704000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179570.704000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[17179570.704000] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[17179570.704000] TCP: Hash tables configured (established 16384 bind 8192)
[17179570.704000] TCP reno registered
[17179570.704000] Simple Boot Flag value 0x87 read from CMOS RAM was invalid
[17179570.704000] Simple Boot Flag at 0x7a set to 0x1
[17179570.704000] audit: initializing netlink socket (disabled)
[17179570.704000] audit(1162256756.704:1): initialized
[17179570.704000] VFS: Disk quotas dquot_6.5.1
[17179570.704000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.704000] Initializing Cryptographic API
[17179570.704000] io scheduler noop registered
[17179570.704000] io scheduler anticipatory registered
[17179570.704000] io scheduler deadline registered
[17179570.704000] io scheduler cfq registered (default)
[17179570.704000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179570.704000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179570.704000] assign_interrupt_mode Found MSI capability
[17179570.704000] Allocate Port Service[0000:00:01.0:pcie00]
[17179570.704000] Allocate Port Service[0000:00:01.0:pcie03]
[17179570.704000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179570.704000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179570.704000] assign_interrupt_mode Found MSI capability
[17179570.704000] Allocate Port Service[0000:00:1c.0:pcie00]
[17179570.704000] Allocate Port Service[0000:00:1c.0:pcie02]
[17179570.704000] Allocate Port Service[0000:00:1c.0:pcie03]
[17179570.704000] isapnp: Scanning for PnP cards...
[17179571.060000] isapnp: No Plug & Play device found
[17179571.084000] Real Time Clock Driver v1.12ac
[17179571.084000] hpet_resources: 0xfed00000 is busy
[17179571.084000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179571.084000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.084000] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.084000] mice: PS/2 mouse device common for all mice
[17179571.084000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179571.084000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179571.088000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179571.088000] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[17179571.092000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179571.092000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179571.092000] EISA: Probing bus 0 at eisa.0
[17179571.092000] Cannot allocate resource for EISA slot 2
[17179571.092000] Cannot allocate resource for EISA slot 5
[17179571.092000] Cannot allocate resource for EISA slot 6
[17179571.092000] EISA: Detected 0 cards.
[17179571.092000] TCP bic registered
[17179571.092000] NET: Registered protocol family 1
[17179571.092000] NET: Registered protocol family 8
[17179571.092000] NET: Registered protocol family 20
[17179571.092000] Starting balanced_irq
[17179571.092000] Using IPI No-Shortcut mode
[17179571.092000] ACPI: (supports S0 S1 S3 S4 S5)
[17179571.092000] Freeing unused kernel memory: 308k freed
[17179571.128000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179572.164000] Capability LSM initialized
[17179572.544000] ICH6: IDE controller at PCI slot 0000:00:1f.1
[17179572.544000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 169
[17179572.544000] ICH6: chipset revision 3
[17179572.544000] ICH6: not 100% native mode: will probe irqs later
[17179572.544000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:DMA
[17179572.544000] Probing IDE interface ide0...
[17179572.836000] hda: WDC WD800JB-00FMA0, ATA DISK drive
[17179573.288000] hdb: LITE-ON DVDRW SHW-160P6S, ATAPI CD/DVD-ROM drive
[17179573.348000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179573.356000] hda: max request size: 128KiB
[17179573.364000] hda: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(33)
[17179573.364000] hda: cache flushes supported
[17179573.364000]  hda: hda1
[17179573.376000] hdb: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179573.376000] Uniform CD-ROM driver Revision: 3.20
[17179573.568000] SCSI subsystem initialized
[17179573.572000] libata version 1.20 loaded.
[17179573.576000] ata_piix 0000:00:1f.2: version 1.05
[17179573.576000] ACPI: PCI Interrupt 0000:00:1f.2[C] -> GSI 20 (level, low) -> IRQ 201
[17179573.576000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179573.576000] ata1: SATA max UDMA/133 cmd 0xFE00 ctl 0xFE12 bmdma 0xFEA0 irq 201
[17179573.576000] ata2: SATA max UDMA/133 cmd 0xFE20 ctl 0xFE32 bmdma 0xFEA8 irq 201
[17179573.748000] ata1: dev 0 cfg 49:2f00 82:346b 83:7f01 84:4003 85:3469 86:3e01 87:4003 88:207f
[17179573.748000] ata1: dev 0 ATA-6, max UDMA/133, 78125000 sectors: LBA48
[17179573.760000] ata1: dev 0 configured for UDMA/133
[17179573.760000] scsi0 : ata_piix
[17179573.916000] ata2: disabling port
[17179573.916000] scsi1 : ata_piix
[17179573.920000]   Vendor: ATA       Model: ST340014AS        Rev: 8.12
[17179573.920000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179573.924000] SCSI device sda: 78125000 512-byte hdwr sectors (40000 MB)
[17179573.924000] sda: Write Protect is off
[17179573.924000] sda: Mode Sense: 00 3a 00 00
[17179573.924000] SCSI device sda: drive cache: write back
[17179573.924000] SCSI device sda: 78125000 512-byte hdwr sectors (40000 MB)
[17179573.924000] sda: Write Protect is off
[17179573.924000] sda: Mode Sense: 00 3a 00 00
[17179573.924000] SCSI device sda: drive cache: write back
[17179573.924000]  sda: sda1 sda2 < sda5 >
[17179573.968000] sd 0:0:0:0: Attached scsi disk sda
[17179574.124000] Probing IDE interface ide1...
[17179574.160000] usbcore: registered new driver usbfs
[17179574.160000] usbcore: registered new driver hub
[17179574.164000] USB Universal Host Controller Interface driver v3.0
[17179574.164000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 21 (level, low) -> IRQ 209
[17179574.164000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179574.164000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179574.164000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179574.164000] uhci_hcd 0000:00:1d.0: irq 209, io base 0x0000ff80
[17179574.164000] usb usb1: configuration #1 chosen from 1 choice
[17179574.164000] hub 1-0:1.0: USB hub found
[17179574.164000] hub 1-0:1.0: 2 ports detected
[17179574.272000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 22 (level, low) -> IRQ 217
[17179574.272000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179574.272000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179574.272000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179574.272000] uhci_hcd 0000:00:1d.1: irq 217, io base 0x0000ff60
[17179574.272000] usb usb2: configuration #1 chosen from 1 choice
[17179574.272000] hub 2-0:1.0: USB hub found
[17179574.272000] hub 2-0:1.0: 2 ports detected
[17179574.380000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 225
[17179574.380000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179574.380000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179574.380000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179574.380000] uhci_hcd 0000:00:1d.2: irq 225, io base 0x0000ff40
[17179574.380000] usb usb3: configuration #1 chosen from 1 choice
[17179574.380000] hub 3-0:1.0: USB hub found
[17179574.380000] hub 3-0:1.0: 2 ports detected
[17179574.488000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 23 (level, low) -> IRQ 233
[17179574.488000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17179574.488000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[17179574.488000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[17179574.488000] uhci_hcd 0000:00:1d.3: irq 233, io base 0x0000ff20
[17179574.488000] usb usb4: configuration #1 chosen from 1 choice
[17179574.488000] hub 4-0:1.0: USB hub found
[17179574.488000] hub 4-0:1.0: 2 ports detected
[17179574.516000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[17179574.600000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 21 (level, low) -> IRQ 209
[17179574.600000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179574.600000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179574.600000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[17179574.600000] ehci_hcd 0000:00:1d.7: debug port 1
[17179574.600000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[17179574.600000] ehci_hcd 0000:00:1d.7: irq 209, io mem 0xffa80800
[17179574.604000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179574.604000] usb usb5: configuration #1 chosen from 1 choice
[17179574.604000] hub 5-0:1.0: USB hub found
[17179574.604000] hub 5-0:1.0: 8 ports detected
[17179574.776000] Attempting manual resume
[17179574.832000] kjournald starting.  Commit interval 5 seconds
[17179574.832000] EXT3-fs: mounted filesystem with ordered data mode.
[17179575.056000] usb 1-1: device not accepting address 2, error -71
[17179575.820000] usb 5-2: new high speed USB device using ehci_hcd and address 3
[17179575.968000] usb 5-2: configuration #1 chosen from 1 choice
[17179576.396000] usb 1-1: new full speed USB device using uhci_hcd and address 4
[17179576.592000] usb 1-1: configuration #1 chosen from 1 choice
[17179576.836000] usb 2-1: new full speed USB device using uhci_hcd and address 2
[17179577.040000] usb 2-1: configuration #1 chosen from 1 choice
[17179582.704000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179582.708000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179583.164000] input: PC Speaker as /class/input/input1
[17179583.188000] parport: PnPBIOS parport detected.
[17179583.188000] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[17179583.208000] hw_random: RNG not detected
[17179583.228000] Linux agpgart interface v0.101 (c) Dave Jones
[17179583.232000] agpgart: Detected an Intel 915G Chipset.
[17179583.248000] agpgart: AGP aperture is 256M @ 0x0
[17179583.728000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179583.812000] Linux video capture interface: v1.00
[17179584.092000] input: ImPS/2 Logitech Wheel Mouse as /class/input/input2
[17179584.120000] nvidia: module license 'NVIDIA' taints kernel.
[17179584.372000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179584.372000] PCI: Setting latency timer of device 0000:01:00.0 to 64
[17179584.372000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9625  Thu Sep 14 15:33:21 PDT 2006
[17179584.380000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x04B8 pid 0x0808
[17179584.380000] usbcore: registered new driver usblp
[17179584.380000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[17179584.412000] ieee80211_crypt: registered algorithm 'NULL'
[17179584.420000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[17179584.420000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17179584.456000] drivers/media/video/spca5xx/spca5xx-main.c: USB SPCA5XX camera found. Type MicroInnovation IC200 (SPCA508+PB100)
[17179584.484000] e100: Intel(R) PRO/100 Network Driver, 3.5.10-k2-NAPI
[17179584.484000] e100: Copyright(c) 1999-2005 Intel Corporation
[17179584.484000] ACPI: PCI Interrupt 0000:03:08.0[A] -> GSI 20 (level, low) -> IRQ 201
[17179584.512000] e100: eth0: e100_probe: addr 0xdceff000, irq 201, MAC addr 00:11:11:85:BC:93
[17179584.528000] usbcore: registered new driver spca5xx
[17179584.528000] drivers/media/video/spca5xx/spca5xx-main.c: spca5xx driver 00.57.08 registered
[17179584.624000] ts: Compaq touchscreen protocol output
[17179584.680000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 23 (level, low) -> IRQ 233
[17179584.680000] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[17179584.824000] zd1211rw 5-2:1.0: firmware version 4605
[17179584.868000] zd1211rw 5-2:1.0: zd1211 chip 07b8:6001 v4330 high 00-e0-98 AL2230_RF pa0 g--
[17179584.868000] zd1211rw 5-2:1.0: eth1
[17179584.868000] usbcore: registered new driver zd1211rw
[17179584.940000] ieee80211_crypt: registered algorithm 'WEP'
[17179585.004000] intel8x0_measure_ac97_clock: measured 59524 usecs
[17179585.004000] intel8x0: clocking to 48000
[17179585.140000] lp0: using parport0 (interrupt-driven).
[17179585.164000] Adding 1502036k swap on /dev/disk/by-uuid/71ebabe2-506f-4aae-b675-6370c15bc760.  Priority:-1 extents:1 across:1502036k
[17179585.224000] EXT3 FS on sda1, internal journal
[17179585.412000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[17179585.460000] NTFS volume version 3.1.
[17179586.760000] NET: Registered protocol family 17
[17179589.792000] ACPI: Power Button (FF) [PWRF]
[17179589.792000] ACPI: Power Button (CM) [VBTN]
[17179589.936000] ibm_acpi: ec object not found
[17179589.976000] pcc_acpi: loading...
[17179593.432000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179593.432000] apm: disabled - APM is not SMP safe.
[17179598.568000] Bluetooth: Core ver 2.8
[17179598.568000] NET: Registered protocol family 31
[17179598.568000] Bluetooth: HCI device and connection manager initialized
[17179598.568000] Bluetooth: HCI socket layer initialized
[17179598.592000] Bluetooth: L2CAP ver 2.8
[17179598.592000] Bluetooth: L2CAP socket layer initialized
[17179598.648000] Bluetooth: RFCOMM socket layer initialized
[17179598.648000] Bluetooth: RFCOMM TTY layer initialized
[17179598.648000] Bluetooth: RFCOMM ver 1.7
[17179633.220000] NET: Registered protocol family 10
[17179633.220000] lo: Disabled Privacy Extensions
[17179633.220000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17179633.220000] IPv6 over IPv4 tunneling driver
[17179681.920000] SoftMAC: Open Authentication completed with 00:0f:3d:3f:69:32
[17179681.936000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[17179692.124000] eth1: no IPv6 routers present

```

---

### Post by dmizer on 2006-10-30
well, there's your problem.  according to dmesg, there is no such thing as eth1.  are you using ndiswrapper to drive your wireless card by chance?

---

### Post by wieman01 on 2006-10-30
Mmm... This bit looks a bit odd:
> [17179633.220000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17179633.220000] IPv6 over IPv4 tunneling driver
[17179681.920000] SoftMAC: Open Authentication completed with 00:0f:3d:3f:69:32
[17179681.936000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Not sure what it tells us...

_**EDIT:**_
Does not look like "ndiswrapper"... Otherwise the alias would be "wlan0" & dmesg would mention it.

What wireless card are you using?

---

### Post by wieman01 on 2006-10-30
One more question: Do you have "open authentication" or "restricted access"? What are the exact WEP/wireless security settings? I think that may be your problem.

---

### Post by dmizer on 2006-10-30
> **wieman01 said:**
> Does not look like "ndiswrapper"... Otherwise the alias would be "wlan0" & dmesg would mention it.
quite ... i was thinking that maybe the ndiswrapper module wasn't loading at boot, but it would still show up as wlan0 or the like.

it's really strange, according to dmesg, the only adapter module loaded is for eth0, and eth1 suddenly appears at the end of dmesg with no module loaded.

you didn't happen to compile the driver module for your wirless card yourself did you?

---

### Post by wieman01 on 2006-10-30
> **dmizer said:**
> it's really strange, according to dmesg, the only adapter module loaded is for eth0, and eth1 suddenly appears at the end of dmesg with no module loaded.
Yes, I tend to agree. Pretty strange. Perhaps there is a driver issue. Depending on what card it is... "ndiswrapper" may be the best option at the end of the day as you have suggested. Let's wait  & see what card/chipset he is using.

---

### Post by Dual Cortex on 2006-10-30
I believe it is a Hawking HWU54G.
My computer also has an ethernet network device, but I have it disabled.
I'm using open system authentication, with a 64Bit hex key.

---

### Post by wieman01 on 2006-10-30
Ok, would you mind trying out WEP-128 bit with restricted authentication (authentication enabled) for a minute? Just want to rule this out...

If this does not work, we may have to focus on the driver as Dmizer has pointed out.

---

### Post by dmizer on 2006-10-30
> **Dual Cortex said:**
> I believe it is a Hawking HWU54G.

the output of lspci should satisfy any doubt.  please post this as well as the output of [FONT="Impact"]_sudo iwlist eth1 scan_[/FONT] if changing the encryption strength, like wieman01 suggested, doesn't work.

---

### Post by Dual Cortex on 2006-10-30
> **wieman01 said:**
> Ok, would you mind trying out WEP-128 bit with restricted authentication (authentication enabled) for a minute? Just want to rule this out...

If this does not work, we may have to focus on the driver as Dmizer has pointed out.

How would I edit /.../interfaces to use restricted/shared mode?
would I just replace 'open' with 'restricted'? or 'shared'?

---

### Post by wieman01 on 2006-10-30
Just change the router settings, update the key in "interfaces", save the file & restart the computer. "interfaces" will look the exactly same, only the key is a bit different & longer. 

If that doesn't do the trick, please follow Dmizer's suggestion.

---

### Post by Dual Cortex on 2006-10-31
hmmm... well I was expecting I would have to add something to interfaces to let it know it's supposed to use restricted authentication, but anyway, that'll be the first thing I do when I get home.

---

### Post by wieman01 on 2006-10-31
You only change the key... because you'll choose WEP-128 rather than WEP-64. That is why. The rest remains the same.

Let us know how you go & post your "interfaces" file after the update.

---

### Post by Dual Cortex on 2006-10-31
> **wieman01 said:**
> You only change the key... because you'll choose WEP-128 rather than WEP-64. That is why. The rest remains the same.

Let us know how you go & post your "interfaces" file after the update.

As I expected, simply typing the longer key to the interfaces file did not work. I also had to add 'restricted' as you will see below:

INTERFACES:```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

iface eth0 inet dhcp

auto eth1
iface eth1 inet static
wireless-mode managed
wireless-essid MGTComputers
wireless-key restricted 12345678912345678912345678
address 192.168.0.108
netmask 255.255.255.0
gateway 192.168.0.1

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```

So, after adding that, I rebooted Kubuntu (maybe /etc/init.d/networking restart might have given the same results... but I want to do this just as if I were a newbie following instructions from Bellsouth's customer-support ;) ).

Right when I logged in, I opened a Konsole window and issued the following command and receiving the following output:

```
felipe@LinuxDesktop:~$ sudo iwconfig
Password:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      802.11g zd1211  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Invalid
          Bit Rate=1 Mb/s
          Encryption key:1234-5678-9123-4567-8912-3456-78   Security mode:restricted
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

felipe@LinuxDesktop:~$ sudo iwconfig eth1 essid "MGTComputers"
felipe@LinuxDesktop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      802.11g zd1211  ESSID:"MGTComputers"
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:0F:3D:3F:69:32
          Bit Rate=11 Mb/s
          Encryption key:1234-5678-9123-4567-8912-3456-78   Security mode:restricted
          Link Quality=93/100  Signal level=88/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

felipe@LinuxDesktop:~$
```

As you see, the problem persists and the ESSID didn't load with the other configurations (therefore, I wasn't accessing the internet), so I issued the *sudo ... essid "MGTComputers"* command to acces my network.



Now, complying with dmizer's request:

```
felipe@LinuxDesktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 915G/P/GV/GL/PL/910GL Express Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 915G/P/GV/GL/PL/910GL Express PCI Express Root Port (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 01d1 (rev a1)
03:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 03)
felipe@LinuxDesktop:~$    
```

AND

```
felipe@LinuxDesktop:~$ sudo iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:0F:3D:3F:69:32
                    ESSID:"MGTComputers"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:10
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=100/100
                    Extra: Last beacon: 8ms ago

felipe@LinuxDesktop:~$          
```

---

### Post by dmizer on 2006-10-31
at this point, all i can say is that you appear to be damn lucky that the thing works at all.  there is nothing anywhere that's indicating that:
1) you have a wireless card
2) the wireless card is on eth1
3) there is a module loading for your card

if i were you ... at this point, i'd do this:
```
gksudo gedit /etc/rc.local
```
and add these two lines:
> iwconfig eth1 essid "MGTComputers"
/etc/init.d/networking restart

if that gets you working, i'd recommend leaving it at that.  my reasoning is that there's nothing at all anywhere i see that indicates that you should have a working wireless adapter.  so, if i were you, i would simply be thankful that the thing worked at all.

it's not currently "broke" as in doesn't work at all, so i think messing with things further might render you disconnected.  the above work around should connect you on log in, so the problem should be transparent, but also could break completely without warning.

---

### Post by wieman01 on 2006-10-31
Hang on... This is impossible... It must show somewhere. Is your device PCI or USB? If USB, this is the right command:
> lsusb
This is spooky...

As for "wireless-essid", yes, there 3 two options:
1. wireless-essid [COLOR="Red"]your_essid[/COLOR]
2. wireless-essid open [COLOR="Red"]your_essid[/COLOR]
3. wireless-essid restricted [COLOR="Red"]your_essid[/COLOR]

But you have figured that out yourself. 

BTW: Same issue if you turn encryption off? If so, Dmizer's suggestion is your last resort.

---

### Post by dmizer on 2006-11-01
> **wieman01 said:**
> Hang on... This is impossible... It must show somewhere. Is your device PCI or USB? If USB, this is the right command:

This is spooky...

you can say that again.

i thought i read somewhere earlier that this was an internal wireless adapter, but i don't see it now.  i might have picked that up from another thread.

---

### Post by Dual Cortex on 2006-11-01
It's USB. I should have mentioned that before 8-[.
I'll do that this afternoon. I'm at school... well, actually college... right now.

---

### Post by dmizer on 2006-11-01
ha!  i'll be, you were right weiman01, it shows up as usb!  found it in the dmesg:
> [17179584.824000] zd1211rw 5-2:1.0: firmware version 4605
[17179584.868000] zd1211rw 5-2:1.0: zd1211 chip 07b8:6001 v4330 high 00-e0-98 AL2230_RF pa0 g--
[17179584.868000] zd1211rw 5-2:1.0: eth1 <<<---- how did i miss that? ;)
[17179584.868000] usbcore: registered new driver zd1211rw

here's your bug report: nope ... wrong ... sorry, i should read more carefully when i'm falling asleep.

i found this:
> This [not loading essid] is because you didn't use "the firmware" as described in the ZD1211
kernel help text which is [http://zd1211.ath.cx/get-firmware](http://zd1211.ath.cx/get-firmware)

Instead you used the firmware which belongs to Debian's fork of the
ZD1211 vendor driver.

However, using hacks like the above *should* work OK (although you are
probably running different firmware from what zd1211rw is currently
designed for). 
here: [http://www.nabble.com/UntestedWithRewrite:-Zyxel-G-220-v2---failure--t2406722.html](http://www.nabble.com/UntestedWithRewrite:-Zyxel-G-220-v2---failure--t2406722.html)

looks like a firmware update.  i'm hoping weiman01 can help you with that because i've never worked one of those out myself.

text of "the hack" as described in the quote above as follows:
> This distribution contains the firmware files for the
ZD1211 chip, which is used in WLAN USB sticks. Copy these files to
/lib/firmware/zd1211, where it can be loaded by the rewritten
zd1211 driver.

---

### Post by Dual Cortex on 2006-11-01
LSUSB 
```
felipe@LinuxDesktop:~$ lsusb
Bus 005 Device 003: ID 07b8:6001 D-Link Corp.
Bus 005 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 004: ID 0461:0815 Primax Electronics, Ltd Micro Innovations WebCam
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 002 Device 002: ID 04b8:0808 Seiko Epson Corp.
Bus 002 Device 001: ID 0000:0000
felipe@LinuxDesktop:~$

```

mY lib/firmware directory contained a directory called 2.6.17-10-generic. Inside the 2.6.17... directory there are many files including a zd1211 directory which included 10 files with the same name as those of the files I downloaded from the website you gave me. Here's a pic of the 2.6... directory:

[[IMG]http://img404.imageshack.us/img404/2299/snapshot4dc3.th.png[/IMG]](http://img404.imageshack.us/my.php?image=snapshot4dc3.png)

Sooo, I made a backup of the original files and erased them. Then I copied the files downloaded and pasted them onto that folder.
I rebooted Kubuntu... and nothing seems to be fixed.

---

### Post by wieman01 on 2006-11-01
Check out Dmizer's post (#25) and let us know how it goes.

For your information... I am using WPA2 as encryption/authentication method and I have to restart my network as well at startup. Does not annoy me much because I have created a startup script which does that for me. So just to underline that this issue is fairly common...

---

### Post by Dual Cortex on 2006-11-01
btw... dmesg shows the same firmware version... do I need to do anything else for the 'firmware upgrade'?

EDIT: Actually it seems like I already had the latest firmware version. Both, the downloaded files and the original files, are exactly 45,924 B.

---

### Post by dmizer on 2006-11-01
according to the thread i linked to earlier, the problem is that the firmware for the debian branch (including ubuntu) doesn't work right.  so even though the firmware is the same version, the debian version is broken (at least where essid is concerned).

again, i've not done firmware changes or updates, so i'm not too sure where to tell you to put the stuff, but it should work correctly once the correct firmware is in place.

---

### Post by wieman01 on 2006-11-01
My suggestion is: Try the startup script. If that does not resolve your problems or in case you don't like the solution, I suggest to make use of "ndiswrapper" for your card. "ndiswrapper" let's you deploy the native Windows driver & works well with a number of wireless devices. 

Should you decide to give "ndiswrapper" a go, we can guide you through the process.

---

### Post by Dual Cortex on 2006-11-01
I would sure like to give ndiswrapper a change. Seems like a better solution, and, even better, I'll probably gain some knowledge too.
Thanks to both of you!

---

### Post by Dual Cortex on 2006-11-01
Another question: can I delete the wlan0, eth2, ath0 that appear in my Interface file? Whenever I do a networking restart I get 'NO such device' errors
```
felipe@LinuxDesktop:~$ sudo /etc/init.d/networking restart
Password:
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
                                                                         [ ok ]
felipe@LinuxDesktop:~$    
```

Maybe startup also takes longer because of this... just a wild guess :P

---

### Post by wieman01 on 2006-11-01
Yes, you can delete them. No problem.

"ndiswrapper" then? Can you get hold of the Windows drivers for your device? I can write you a summary tonight.

---

