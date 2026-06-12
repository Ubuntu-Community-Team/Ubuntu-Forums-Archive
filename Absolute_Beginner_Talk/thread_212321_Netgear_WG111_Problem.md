---
title: "Netgear WG111 Problem"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by krasovskya on 2006-07-09
I have spent approximately 4 hours today looking through forum after forum and thread after thread and for some reason I still have no idea of how get this to work. I have done everything that I can possibly find and think of. Okay, so here goes. 

I got myself ndiswrapper and followed all of the steps in [http://www.ubuntuforums.org/showthread.php?t=202254&highlight=wg111+netgear](http://www.ubuntuforums.org/showthread.php?t=202254&highlight=wg111+netgear) (10 steps to get the wg111 to work).

That didn't work. Basically, what is happening is that, yes, the device is recognized in the Windows Wireless Drivers and I have configured everything in the ESSID and set the card as the default and  the only one active. It says Wireless Connection and ETH2 is active. However, the hardware, the actual adapter, is not lit up. So I unplugged it and it said that it is not connected, meaning that it is obviously reading it right, even though the blue light didn't turn on. The blue light blinks once and then goes off.

Okay, so I went to the blacklist and added blacklist acx to the bottom as well as blacklist acx_pci. Neither did anything. Yes, I restarted. So I tried sudo ndiswrapper and sudo modprobe ndiswrapper. Neither did anything really. The  blue light still didn't turn on. I also editted options under modprobe.d under etc in the root folder and added options acx firmware_ver=1.2.1.34. That didn't work so I tried ver=1.2.0.30. Neither did that. I editted modules in the etc folder in the root folder and added ndiswrapper so it started up and restarted. That did nothing. I checked iwconfig but it said that none of the wireless hardware were working or something of the sorts. 

I have called netgear and checked with them and all they could tell me is "linux is not compatible with netgear." Thank you, Mr. Netgear. You really opened my eyes to the truth. Really.

So I tried looking for Ubuntu calling service and it's like 250 bucks for a desktop service (?). So, I wrote myself this essay and maybe someone can help me, I'll try anything =/ lol please help me.

Thank you in advance, I appreciate any help.
Alex

p.s.- oh, and I am new to linux so... just throwing that out there. I'm native-windows, so any help at all would help. Thank you =D

---

### Post by dmizer on 2006-07-09
with the card in place, what is the result of:
```
ndiswrapper -l
```
```
cardctl ident
```
```
dmesg
```
```
lspci
```

---

### Post by krasovskya on 2006-07-09
Okay, for ndiswrapper -l, I got
> installed ndis drivers:
netwg111 drvier present, hardware present

for cardctl ident I get

> no pcmcia driver in /proc/devices

The other 2 were very long system specs or something and it's on my other computer and I have no idea how I'm supposed to transfer all of it, lol. Is there anything specific I should look for?

THANKS =D

---

### Post by dmizer on 2006-07-09
well, i just realized that your card is not a card, but a usb adapter, so cardctl ident really wasn't necessary.

to get the other two, just save the output to a file and take it over to the other computer via a usb drive or the like.  you can get the output into a file by doing the following:
```
echo lspci >> lspci.txt
```
```
echo dmesg >> dmesg.txt
```
after that, you will have two new files in your home directory named lspci.txt, and dmesg.txt ... both containing the contents of the output of the requested commands.

---

### Post by krasovskya on 2006-07-09
Okay just one second, don't leave lol windows just shut down on me so I had to restart and I put the TXT files on it but they aren't showing up so brb.

---

### Post by krasovskya on 2006-07-09
alright, here goes
the result of lspci was
> 0000:00:00.0 Host bridge: Intel Corporation 915G/P/GV/GL/PL/910GL Processor to I/O Controller (rev 04)
0000:00:01.0 PCI bridge: Intel Corporation 915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
0000:00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
0000:00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
0000:00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
0000:01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
0000:03:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 03)



the result of dmesg was

> [4294667.296000] Linux version 2.6.15-23-386 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue May 23 13:49:40 UTC 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[4294667.296000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 000000000fe88c00 (usable)
[4294667.296000]  BIOS-e820: 000000000fe88c00 - 000000000fe8ac00 (ACPI NVS)
[4294667.296000]  BIOS-e820: 000000000fe8ac00 - 000000000fe8cc00 (ACPI data)
[4294667.296000]  BIOS-e820: 000000000fe8cc00 - 0000000010000000 (reserved)
[4294667.296000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[4294667.296000]  BIOS-e820: 00000000fec00000 - 00000000fed00400 (reserved)
[4294667.296000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[4294667.296000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 254MB LOWMEM available.
[4294667.296000] found SMP MP-table at 000fe710
[4294667.296000] On node 0 totalpages: 65160
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:0
[4294667.296000]   DMA32 zone: 0 pages, LIFO batch:0
[4294667.296000]   Normal zone: 61064 pages, LIFO batch:15
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:0
[4294667.296000] DMI 2.3 present.
[4294667.296000] ACPI: RSDP (v000 DELL                                  ) @ 0x000fec00
[4294667.296000] ACPI: RSDT (v001 DELL    4700    0x00000007 ASL  0x00000061) @ 0x000fcc12
[4294667.296000] ACPI: FADT (v001 DELL    4700    0x00000007 ASL  0x00000061) @ 0x000fcc52
[4294667.296000] ACPI: SSDT (v001   DELL    st_ex 0x00001000 MSFT 0x0100000d) @ 0xfffc6120
[4294667.296000] ACPI: MADT (v001 DELL    4700    0x00000007 ASL  0x00000061) @ 0x000fccc6
[4294667.296000] ACPI: BOOT (v001 DELL    4700    0x00000007 ASL  0x00000061) @ 0x000fcd38
[4294667.296000] ACPI: ASF! (v016 DELL    4700    0x00000007 ASL  0x00000061) @ 0x000fcd60
[4294667.296000] ACPI: MCFG (v001 DELL    4700    0x00000007 ASL  0x00000061) @ 0x000fcdc7
[4294667.296000] ACPI: HPET (v001 DELL    4700    0x00000007 ASL  0x00000061) @ 0x000fce05
[4294667.296000] ACPI: DSDT (v001   DELL    dt_ex 0x00001000 MSFT 0x0100000d) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x808
[4294667.296000] ACPI: Local APIC address 0xfee00000
[4294667.296000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[4294667.296000] Processor #0 15:3 APIC version 20
[4294667.296000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[4294667.296000] Processor #1 15:3 APIC version 20
[4294667.296000] WARNING: NR_CPUS limit of 1 reached.  Processor ignored.
[4294667.296000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] disabled)
[4294667.296000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x07] disabled)
[4294667.296000] ACPI: LAPIC_NMI (acpi_id[0xff] high level lint[0x1])
[4294667.296000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[4294667.296000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[4294667.296000] ACPI: IRQ0 used by override.
[4294667.296000] ACPI: IRQ2 used by override.
[4294667.296000] ACPI: IRQ9 used by override.
[4294667.296000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[4294667.296000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[4294667.296000] Using ACPI (MADT) for SMP configuration information
[4294667.296000] Allocating PCI resources starting at 20000000 (gap: 10000000:d0000000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/sda1 ro quiet splash
[4294667.296000] mapped APIC to ffffd000 (fee00000)
[4294667.296000] mapped IOAPIC to ffffc000 (fec00000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 1024 (order: 10, 16384 bytes)
[4294667.296000] Console: colour VGA+ 80x25
[4294667.296000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)[4294667.296000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[4294667.296000] Memory: 247732k/260640k available (1976k kernel code, 12372k reserved, 606k data, 288k init, 0k highmem)
[4294667.296000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294667.296000] hpet0: at MMIO 0xfed00000 (virtual 0xd0800000), IRQs 2, 8, 0
[4294667.296000] hpet0: 3 64-bit timers, 14318180 Hz
[4294667.296000] Using HPET for base-timer
[4294667.296000] Using HPET for gettimeofday
[4294667.296000] Detected 2793.362 MHz processor.
[4294667.296000] Using hpet for high-res timesource
[4294667.357000] Calibrating delay using timer specific routine.. 5589.71 BogoMIPS (lpj=2794858)
[4294667.357000] Security Framework v1.0.0 initialized
[4294667.357000] SELinux:  Disabled at boot.
[4294667.357000] Mount-cache hash table entries: 512
[4294667.357000] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000
[4294667.357000] CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000
[4294667.357000] monitor/mwait feature present.
[4294667.357000] using mwait in idle threads.
[4294667.357000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[4294667.357000] CPU: L2 cache: 1024K
[4294667.357000] CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 0000441d 00000000 00000000
[4294667.357000] mtrr: v2.0 (20020519)
[4294667.357000] CPU: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 04
[4294667.357000] Enabling fast FPU save and restore... done.
[4294667.357000] Enabling unmasked SIMD FPU exception support... done.
[4294667.357000] Checking 'hlt' instruction... OK.
[4294667.361000] checking if image is initramfs... it is
[4294667.928000] Freeing initrd memory: 6836k freed
[4294667.935000] ACPI: Looking for DSDT ... not found!
[4294667.966000] ENABLING IO-APIC IRQs
[4294667.966000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[4294668.078000] NET: Registered protocol family 16
[4294668.078000] EISA bus registered
[4294668.078000] ACPI: bus type pci registered
[4294668.078000] PCI: PCI BIOS revision 2.10 entry at 0xfb2ce, last bus=3
[4294668.078000] PCI: Using MMCONFIG
[4294668.078000] ACPI: Subsystem revision 20051216
[4294668.099000] ACPI: Interpreter enabled
[4294668.099000] ACPI: Using IOAPIC for interrupt routing
[4294668.101000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294668.101000] PCI: Probing PCI hardware (bus 00)
[4294668.102000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[4294668.119000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[4294668.119000] Boot video device is 0000:01:00.0
[4294668.119000] PCI: Transparent bridge - 0000:00:1e.0
[4294668.119000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294668.553000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[4294668.559000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI2._PRT]
[4294668.568000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI4._PRT]
[4294668.600000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)[4294668.601000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 9 10 11 12 15)[4294668.602000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 15)[4294668.603000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[4294668.603000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 15)[4294668.604000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 15)[4294668.605000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 15)[4294668.606000] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 9 10 11 12 15)[4294668.606000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294668.606000] pnp: PnP ACPI init
[4294668.636000] pnp: PnP ACPI: found 12 devices
[4294668.636000] PnPBIOS: Disabled by ACPI PNP
[4294668.636000] PCI: Using ACPI for IRQ routing
[4294668.636000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294668.656000] pnp: 00:00: ioport range 0x800-0x85f could not be reserved
[4294668.656000] pnp: 00:00: ioport range 0xc00-0xc7f has been reserved
[4294668.656000] pnp: 00:00: ioport range 0x860-0x8ff has been reserved
[4294668.656000] pnp: 00:0a: ioport range 0x100-0x1fe has been reserved
[4294668.656000] pnp: 00:0a: ioport range 0x200-0x277 has been reserved
[4294668.656000] pnp: 00:0a: ioport range 0x280-0x2e7 has been reserved
[4294668.656000] pnp: 00:0a: ioport range 0x2e8-0x2ef has been reserved
[4294668.656000] pnp: 00:0a: ioport range 0x2f0-0x2f7 has been reserved
[4294668.656000] pnp: 00:0a: ioport range 0x2f8-0x2ff has been reserved
[4294668.656000] pnp: 00:0a: ioport range 0x300-0x377 has been reserved
[4294668.656000] pnp: 00:0a: ioport range 0x380-0x3bb has been reserved
[4294668.656000] PCI: Bridge: 0000:00:01.0
[4294668.656000]   IO window: d000-dfff
[4294668.656000]   MEM window: dfd00000-dfefffff
[4294668.656000]   PREFETCH window: d0000000-d7ffffff
[4294668.656000] PCI: Bridge: 0000:00:1c.0
[4294668.656000]   IO window: disabled.
[4294668.656000]   MEM window: dfc00000-dfcfffff
[4294668.656000]   PREFETCH window: disabled.
[4294668.656000] PCI: Bridge: 0000:00:1e.0
[4294668.656000]   IO window: c000-cfff
[4294668.656000]   MEM window: dfb00000-dfbfffff
[4294668.656000]   PREFETCH window: disabled.
[4294668.656000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[4294668.656000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[4294668.656000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 169
[4294668.656000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[4294668.656000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[4294668.656000] Simple Boot Flag value 0x87 read from CMOS RAM was invalid
[4294668.656000] Simple Boot Flag at 0x7a set to 0x1
[4294668.657000] audit: initializing netlink socket (disabled)
[4294668.657000] audit(1152467210.656:1): initialized
[4294668.657000] VFS: Disk quotas dquot_6.5.1
[4294668.657000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294668.657000] Initializing Cryptographic API
[4294668.657000] io scheduler noop registered
[4294668.657000] io scheduler anticipatory registered
[4294668.657000] io scheduler deadline registered
[4294668.657000] io scheduler cfq registered
[4294668.657000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[4294668.657000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[4294668.657000] assign_interrupt_mode Found MSI capability
[4294668.657000] Allocate Port Service[pcie00]
[4294668.657000] Allocate Port Service[pcie03]
[4294668.657000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 169
[4294668.657000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[4294668.657000] assign_interrupt_mode Found MSI capability
[4294668.657000] Allocate Port Service[pcie00]
[4294668.657000] Allocate Port Service[pcie02]
[4294668.657000] Allocate Port Service[pcie03]
[4294668.657000] isapnp: Scanning for PnP cards...
[4294669.016000] isapnp: No Plug & Play device found
[4294669.032000] hpet_resources: 0xfed00000 is busy
[4294669.032000] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[4294669.036000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294669.037000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294669.037000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294669.037000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294669.039000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294669.039000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294669.040000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294669.040000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294669.040000] mice: PS/2 mouse device common for all mice
[4294669.040000] EISA: Probing bus 0 at eisa.0
[4294669.040000] Cannot allocate resource for EISA slot 2
[4294669.040000] Cannot allocate resource for EISA slot 5
[4294669.040000] Cannot allocate resource for EISA slot 6
[4294669.040000] EISA: Detected 0 cards.
[4294669.040000] NET: Registered protocol family 2
[4294669.050000] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[4294669.050000] TCP established hash table entries: 8192 (order: 3, 32768 bytes)
[4294669.050000] TCP bind hash table entries: 8192 (order: 3, 32768 bytes)
[4294669.050000] TCP: Hash tables configured (established 8192 bind 8192)
[4294669.050000] TCP reno registered
[4294669.050000] TCP bic registered
[4294669.050000] NET: Registered protocol family 1
[4294669.050000] NET: Registered protocol family 8
[4294669.050000] NET: Registered protocol family 20
[4294669.050000] Using IPI Shortcut mode
[4294669.050000] ACPI wakeup devices:
[4294669.050000] VBTN PCI0 PCI1 PCI2 PCI3 PCI4  KBD USB0 USB1 USB2 USB3
[4294669.050000] ACPI: (supports S0 S1 S3 S4 S5)
[4294669.050000] Freeing unused kernel memory: 288k freed
[4294669.081000] input: AT Translated Set 2 keyboard as /class/input/input0
[4294669.096000] vga16fb: initializing
[4294669.096000] vga16fb: mapped to 0xc00a0000
[4294669.213000] Console: switching to colour frame buffer device 80x25
[4294669.213000] fb0: VGA16 VGA frame buffer device
[4294670.393000] Capability LSM initialized
[4294670.927000] ICH6: IDE controller at PCI slot 0000:00:1f.1
[4294670.927000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 169
[4294670.927000] ICH6: chipset revision 3
[4294670.927000] ICH6: not 100% native mode: will probe irqs later
[4294670.927000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pio
[4294670.927000] Probing IDE interface ide0...
[4294671.599000] hda: CR-48X9TE, ATAPI CD/DVD-ROM drive
[4294671.905000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294671.915000] hda: ATAPI 40X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[4294671.915000] Uniform CD-ROM driver Revision: 3.20
[4294671.955000] SCSI subsystem initialized
[4294671.956000] ACPI: bus type scsi registered
[4294671.956000] libata version 1.20 loaded.
[4294671.958000] ata_piix 0000:00:1f.2: version 1.05
[4294671.958000] ata_pci_init_one: pci_dev class+intf: 0x1018f
[4294671.958000] ata_pci_init_one: NO_LEGACY == 0
[4294671.958000] ACPI: PCI Interrupt 0000:00:1f.2[C] -> GSI 20 (level, low) -> IRQ 201
[4294671.958000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[4294671.958000] ata1: PATA max UDMA/133 cmd 0xFE00 ctl 0xFE12 bmdma 0xFEA0 irq 201
[4294671.958000] ata2: PATA max UDMA/133 cmd 0xFE20 ctl 0xFE32 bmdma 0xFEA8 irq 201
[4294672.112000] ata1: dev 0 cfg 00:427a 49:2f00 82:346b 83:5b01 84:4003 85:3469 86:1801 87:4003 88:203f 93:0000
[4294672.112000] ata1: dev 0 ATA-6, max UDMA/100, 156250000 sectors: LBA
[4294672.142000] sata_get_dev_handle: SATA dev addr=0x1f0002, handle=0x00000000
[4294672.143000] ata1: dev 0 configured for UDMA/100
[4294672.173000] sata_get_dev_handle: SATA dev addr=0x1f0002, handle=0x00000000
[4294672.173000] scsi0 : ata_piix
[4294673.479000] ata2: disabling port
[4294673.479000] scsi1 : ata_piix
[4294673.479000]   Vendor: ATA       Model: WDC WD800JD-75JN  Rev: 05.0
[4294673.479000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[4294673.486000] Driver 'sd' needs updating - please use bus_type methods
[4294673.486000] SCSI device sda: 156250000 512-byte hdwr sectors (80000 MB)
[4294673.486000] SCSI device sda: drive cache: write back
[4294673.489000] SCSI device sda: 156250000 512-byte hdwr sectors (80000 MB)
[4294673.489000] SCSI device sda: drive cache: write back
[4294673.489000]  sda: sda1 sda2 < sda5 >
[4294673.537000] sd 0:0:0:0: Attached scsi disk sda
[4294673.728000] usbcore: registered new driver usbfs
[4294673.729000] usbcore: registered new driver hub
[4294673.730000] USB Universal Host Controller Interface driver v2.3
[4294673.731000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 21 (level, low) -> IRQ 209
[4294673.731000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[4294673.731000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[4294673.732000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[4294673.732000] uhci_hcd 0000:00:1d.0: irq 209, io base 0x0000ff80
[4294673.733000] hub 1-0:1.0: USB hub found
[4294673.733000] hub 1-0:1.0: 2 ports detected
[4294673.834000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 22 (level, low) -> IRQ 217
[4294673.834000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[4294673.834000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[4294673.834000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[4294673.834000] uhci_hcd 0000:00:1d.1: irq 217, io base 0x0000ff60
[4294673.834000] hub 2-0:1.0: USB hub found
[4294673.834000] hub 2-0:1.0: 2 ports detected
[4294673.935000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 225
[4294673.935000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[4294673.935000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[4294673.935000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[4294673.935000] uhci_hcd 0000:00:1d.2: irq 225, io base 0x0000ff40
[4294673.935000] hub 3-0:1.0: USB hub found
[4294673.935000] hub 3-0:1.0: 2 ports detected
[4294674.036000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 23 (level, low) -> IRQ 233
[4294674.036000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[4294674.036000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[4294674.036000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[4294674.036000] uhci_hcd 0000:00:1d.3: irq 233, io base 0x0000ff20
[4294674.036000] hub 4-0:1.0: USB hub found
[4294674.036000] hub 4-0:1.0: 2 ports detected
[4294674.139000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 21 (level, low) -> IRQ 209
[4294674.139000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[4294674.139000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[4294674.139000] ehci_hcd 0000:00:1d.7: debug port 1
[4294674.139000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[4294674.139000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[4294674.139000] ehci_hcd 0000:00:1d.7: irq 209, io mem 0xffa80800
[4294674.143000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[4294674.143000] hub 5-0:1.0: USB hub found
[4294674.143000] hub 5-0:1.0: 8 ports detected
[4294674.262000] Probing IDE interface ide1...
[4294674.473000] usb 5-7: new high speed USB device using ehci_hcd and address 2[4294674.799000] Attempting manual resume
[4294674.811000] kjournald starting.  Commit interval 5 seconds
[4294674.811000] EXT3-fs: mounted filesystem with ordered data mode.
[4294681.317000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[4294682.182000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294682.184000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294682.221000] Linux agpgart interface v0.101 (c) Dave Jones
[4294682.223000] agpgart: Detected an Intel 915G Chipset.
[4294682.240000] agpgart: AGP aperture is 256M @ 0x0
[4294682.691000] hw_random: RNG not detected
[4294682.779000] Real Time Clock Driver v1.12
[4294682.832000] input: PC Speaker as /class/input/input1
[4294682.868000] ieee80211_crypt: registered algorithm 'NULL'
[4294682.875000] ieee80211: 802.11 data/management/control stack, git-1.1.7
[4294682.875000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[4294682.908000] islusb: No suitable configuration found, trying 3887 support
[4294682.908000] usbcore: registered new driver islusb
[4294683.006000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 23 (level, low) -> IRQ 233
[4294683.006000] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[4294683.117000] input: ImPS/2 Generic Wheel Mouse as /class/input/input2
[4294683.321000] intel8x0_measure_ac97_clock: measured 50597 usecs
[4294683.321000] intel8x0: clocking to 48000
[4294683.778000] ts: Compaq touchscreen protocol output
[4294683.839000] e100: Intel(R) PRO/100 Network Driver, 3.4.14-k4-NAPI
[4294683.839000] e100: Copyright(c) 1999-2005 Intel Corporation
[4294683.839000] ACPI: PCI Interrupt 0000:03:08.0[A] -> GSI 20 (level, low) -> IRQ 201
[4294684.276000] e100: eth0: e100_probe: addr 0xdfbff000, irq 201, MAC addr 00:11:11:C6:25:88
[4294684.421000] parport: PnPBIOS parport detected.
[4294684.421000] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[4294685.320000] NET: Registered protocol family 17
[4294688.495000] lp0: using parport0 (interrupt-driven).
[4294688.533000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[4294688.567000] usbcore: registered new driver ndiswrapper
[4294688.605000] Adding 746980k swap on /dev/sda5.  Priority:-1 extents:1 across:746980k
[4294688.749000] EXT3 FS on sda1, internal journal
[4294688.879000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294688.879000] md: bitmap version 4.39
[4294689.311000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294689.926000] cdrom: open failed.
[4294694.679000] ACPI: Power Button (FF) [PWRF]
[4294694.679000] ACPI: Power Button (CM) [VBTN]
[4294694.805000] ibm_acpi: ec object not found
[4294694.832000] pcc_acpi: loading...
[4294698.087000] [drm] Initialized drm 1.0.1 20051102
[4294698.093000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 169
[4294698.094000] [drm] Initialized radeon 1.24.0 20060225 on minor 0
[4294698.766000] ppdev: user-space parallel port driver
[4294699.133000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294699.133000] apm: overridden by ACPI.
[4294700.921000] Bluetooth: Core ver 2.8
[4294700.921000] NET: Registered protocol family 31
[4294700.921000] Bluetooth: HCI device and connection manager initialized
[4294700.921000] Bluetooth: HCI socket layer initialized
[4294701.005000] Bluetooth: L2CAP ver 2.8
[4294701.005000] Bluetooth: L2CAP socket layer initialized
[4294701.020000] Bluetooth: RFCOMM socket layer initialized
[4294701.020000] Bluetooth: RFCOMM TTY layer initialized
[4294701.020000] Bluetooth: RFCOMM ver 1.7
[4294703.354000] [drm] Setting GART location based on new memory map
[4294703.355000] [drm] Loading R300 Microcode
[4294703.355000] [drm] writeback test succeeded in 1 usecs
[4294767.574000] NET: Registered protocol family 10
[4294767.574000] lo: Disabled Privacy Extensions
[4294767.574000] ADDRCONF(NETDEV_UP): eth2: link is not ready
[4294767.574000] IPv6 over IPv4 tunneling driver
[4295081.421000] ADDRCONF(NETDEV_UP): eth2: link is not ready
[4295164.744000] usb 5-7: USB disconnect, address 2
[4295176.950000] usb 5-8: new high speed USB device using ehci_hcd and address 3[4295177.069000] islusb: No suitable configuration found, trying 3887 support
[4295178.123000] ADDRCONF(NETDEV_UP): eth2: link is not ready
[4297608.700000] usb 5-5: new high speed USB device using ehci_hcd and address 4[4297608.922000] Initializing USB Mass Storage driver...
[4297608.922000] scsi2 : SCSI emulation for USB Mass Storage devices
[4297608.923000] usb-storage: device found at 4
[4297608.923000] usb-storage: waiting for device to settle before scanning
[4297608.923000] usbcore: registered new driver usb-storage
[4297608.923000] USB Mass Storage support registered.
[4297613.923000]   Vendor: M-SysT5   Model: Dell Memory Key   Rev: 5.05
[4297613.923000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4297613.924000] SCSI device sdb: 249343 512-byte hdwr sectors (128 MB)
[4297613.925000] sdb: Write Protect is off
[4297613.925000] sdb: Mode Sense: 45 00 00 08
[4297613.925000] sdb: assuming drive cache: write through
[4297613.926000] SCSI device sdb: 249343 512-byte hdwr sectors (128 MB)
[4297613.927000] sdb: Write Protect is off
[4297613.927000] sdb: Mode Sense: 45 00 00 08
[4297613.927000] sdb: assuming drive cache: write through
[4297613.927000]  sdb: sdb1
[4297613.928000] sd 2:0:0:0: Attached scsi removable disk sdb
[4297613.928000] sd 2:0:0:0: Attached scsi generic sg1 type 0
[4297613.929000] usb-storage: device scan complete
[4297614.302000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!



a little bit long :D

---

### Post by krasovskya on 2006-07-09
whaddya gather from it?

---

### Post by dmizer on 2006-07-09
not much, but let's start by disabling ipv6:
[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

i'm just kind of fishing here, because i'm not sure of the exact command i need to determine what module is attached to your card, and or how to get ndiswrapper attached instead.  and i'm interested in your case, because i'll need to do something similar here in a bit.

anyway ... looks like you have a wired network adapter.  you had no luck getting it to work?  i mean, i know it sucks to have a wire, but at least you can get connected and work with it directly instead of having to cary files over to a connected computer.

what is the output of these two: ifconfig lsmod

---

### Post by krasovskya on 2006-07-10
Okay, I disabled it.

for ifconfig i got

> eth2      Link encap:Ethernet  HWaddr 00:0F:B5:01:23:9F
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1083 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1083 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:83196 (81.2 KiB)  TX bytes:83196 (81.2 KiB)



for lsmod I got

> Module                  Size  Used by
nls_utf8                2176  1
nls_cp437               5888  1
vfat                   13440  1
fat                    53020  1 vfat
usb_storage            74176  1
ipv6                  265600  6
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
ppdev                   9220  0
radeon                116000  1
drm                    73236  2 radeon
speedstep_lib           4484  0
cpufreq_userspace       4696  0
cpufreq_stats           5636  0
freq_table              4740  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
button                  6672  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
i2c_core               21904  1 i2c_acpi_ec
ac                      5252  1 acpi_sbs
dm_mod                 58936  1
md_mod                 72532  0
ndiswrapper           177364  0
lp                     11844  0
af_packet              22920  2
parport_pc             35780  1
e100                   40580  0
mii                     5888  1 e100
tsdev                   8000  0
parport                36296  3 ppdev,lp,parport_pc
snd_intel8x0           33692  1
snd_ac97_codec         92704  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
serio_raw               7300  0
snd_pcm                89864  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
islsm_usb              32260  0
islsm_device           12040  1 islsm_usb
islsm                  37644  2 islsm_usb,islsm_device
ieee80211softmac       29696  1 islsm
ieee80211              37064  2 islsm,ieee80211softmac
ieee80211_crypt         6272  1 ieee80211
snd                    55268  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
pcspkr                  2180  0
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
psmouse                36228  0
rtc                    13492  0
crc_ccitt               2304  1 islsm
intel_agp              22940  1
agpgart                34888  2 drm,intel_agp
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
evdev                   9856  1
sg                     37920  0
ext3                  135688  1
jbd                    58772  1 ext3
ide_generic             1536  0
ehci_hcd               32008  0
uhci_hcd               33680  0
usbcore               129668  6 usb_storage,ndiswrapper,islsm_usb,ehci_hcd,uhci_hcd
sd_mod                 19984  5
ata_piix               11012  4
libata                 78992  1 ata_piix
scsi_mod              139496  4 usb_storage,sg,sd_mod,libata
ide_cd                 33028  0
cdrom                  38560  1 ide_cd
piix                   11012  1
generic                 5124  0
thermal                13576  0
processor              23360  1 thermal
fan                     4868  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit





Sorry it took so long, my comp crashed last night 'cause of the linux to windows usb.

---

### Post by dmizer on 2006-07-10
well that's good, ndiswrapper is attached to the usb.  so it should be attached to your card if things are set up correctly.

i told you i needed ifconfig ... sorry that was the wrong one :oops: 
i need the output of iwconfig

---

### Post by krasovskya on 2006-07-10
alright. ummmm, I'm at work right now and it's my home computer so I'll be coming home around 6ish and I'll check it out. The problem is getting the TXT file from the linux to the windows because for some strange reason, literally if I bring the usb within 4 inches of the metal in back of my windows it crashes. It goes haywire, lol. It didn't do it before I started connecting the usb from linux to windows but whatever. Maybe microsoft tried to scam the world by not allowing it to transfer files from linux to windows! :-s lol. So I'll try it out later and put in the outcome of iwconfig. Do you see any problems so far? Will there be a way to fix it or should I start looking for a linux compatible USB wireless device?:shock: 

Thanks again.

---

### Post by krasovskya on 2006-07-10
okay, I got it. finally. lol. For iwconfig I got
[QUOTE]
lo        no wireless extensions.

eth2      IEEE 802.11b  ESSID:"pagos"
          Mode:Auto  Channel=1  Access Point: Invalid
          Sensitivity=0/200
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.
[QUOTE]

sorry it took so long. does that help at all? I think it might have to do with it recognizing as eth2 because it isn't ethernet but it does say wireless connection when I check it but I don't know. LoL =D

okay thanks again.

---

### Post by craigles_penguin on 2006-07-10
Well I'm using the same adapter; mine shows up on eth1 and works ok, so I guess yours should too.

Your adapter seems to be working but not finding the network (where it says Access Point: Invalid in the text you quoted.

If you run

```
iwlist eth2 scan
```

What do you get?

---

### Post by dmizer on 2006-07-10
yeah ... looks like you've got it installed and all you need to do is get it configured.  if you look in your network configuration, you don't see your adapter?

are you by chance running wep encryption, or mac filtering from your access point?

---

### Post by krasovskya on 2006-07-10
Okay, uhh when I do the scan it says no scan results. Actually, yes, I have a WEP password, hexadecimal. I only thought WPA was a problem. You said that everything is set up fine... so is it okay that the blue light isn't on on the adapter? =\

Since I have a WEP encryption, do I need to turn it off in order to access it? Sorry, I didn't realize that would be a problem =X

---

### Post by dmizer on 2006-07-11
okay ... try this one:
```
sudo ifdown eth2&& sudo iwlist eth2 scan
```
see if that comes up with results. i'm leery of the blue light being off too, but everything so far points to the fact that ubuntu has this adapter installed and functioning.  wep may or may not be the problem, but it should be easy enough to turn it off for testing.

---

### Post by craigles_penguin on 2006-07-11
The blue light will only actually come on permanantly once you get connected to the network - it'll flash when trying to connect, and then fix at on once connected.  That's probably why yours is flashing once, and then switching off - it's not finding anything.

Mine works with WEP enabled on my network too - we could try this in a slightly different order to what you might have done... how about trying things this way round:

- Get ndiswrapper running the same way you have been (assuming you've not set it up to run automatically yet, in which case it already should be running)

- open up a terminal, and set up your network settings for managed mode + your WEP key:

```
sudo iwconfig eth2 mode managed
sudo iwconfig eth2 key xxxxxxxx
```

(The x's should be replaced with your key in hex)

And then set up your network name

```
sudo iwconfig eth2 essid PAGOS
```

(assuming PAGOS is your essid, seeing that's what you had in a previous post)

The idea here is that the router might be refusing the connection because you're not giving it the encryption it's expecting... maybe setting up the encryption first will help.

---

### Post by krasovskya on 2006-07-11
okay, both changing the ESSID and to mode managed had no response, so I assume they worked. However, the middle one, "sudo iwconfig eth2 key XXXXX" did not. It gave me the error

> Error for wireless request "Set encode" (8B2A) : SET failed on device eth2; unknown error 524


Any ideas??

---

### Post by craigles_penguin on 2006-07-11
To be honest, not much of an idea about that one - wasn't something I came across.

How about

```
sudo iwconfig eth2 key restricted xxxxxxxx
```

(and just to double check - you're using the key in hex digits for the x's, and not the passphrase or anything else that you might have used to generate it? Hex will be 8 letters/numbers, and only 0-9 and A-F... the passphrase would be just a word, or anything else you typed into the router setup to set up the WEP)

If this doesn't work, it may be worth disabling the WEP on your network for a while and see if we can get it working without it, as dmizer suggested.... at least then we'd know the device was definitely and could then work on the WEP seperately.

---

### Post by dmizer on 2006-07-11
just on a whim, try it like this:
```
sudo ifdown eth2
sudo iwlist eth2 scan&& sudo iwconfig eth2 channel 1 essid [youressid] mode Managed key xxxx-xxxx-xxxx-xxxx&& sudo ifup eth2
```
where xxxx is your wep key in hex format.  try it both with and without dashes (but if memory serves me, which sometimes it doesn't, i believe you need the dashes in your wep key).

also, make sure that you replace the channel number (in my example it's 1) to the number that matches your network.

---

### Post by krasovskya on 2006-07-11
my WEP key is not 8 digits, it's 10. it's be27138869. =/

---

### Post by krasovskya on 2006-07-11
I  got the same error I previously quoted for the first two suggestions and then the last one didn't do anything. It just started listing something like DHCPDISCOVER and then it listed port or something strange. =\   I have no idea. lol. Yeah, and the fact that my WEP is 10 digits. LoL

---

### Post by eternalsword on 2006-07-11
did you blacklist bcm43xx?

---

### Post by krasovskya on 2006-07-11
no, lol, should I?

---

### Post by eternalsword on 2006-07-11
yes, it interferes with ndiswrapper.
just do the following in the terminal and reboot


echo 'blacklist bcm43xx' | sudo tee -a /etc modprobe.d/blacklist
sudo rmmod bcm43xx

---

### Post by krasovskya on 2006-07-12
I put 'blacklist bcm43xx' into the blacklist but when I do 'sudo rmmod bcm43xx' it tells me there is not bcm43xx in the /proc/modules directory or something. Should I add it?

---

### Post by eternalsword on 2006-07-12
could you post the result of 
dmesg | grep rtl818

go ahead and blacklist bcm43xx anyways.

---

### Post by krasovskya on 2006-07-12
lol nothing, it doesn't do anything. I put it in and nothing happened.

---

### Post by eternalsword on 2006-07-12
Okay, can you post the full result of
dmesg

and

lsmod

---

### Post by krasovskya on 2006-07-12
I have them both posted on the first page =P check the first page of this thread =D

---

### Post by eternalsword on 2006-07-13
okay, took a look at lsmod.
try this from the terminal

modprobe -r islsm_usb
modprobe -r ndiswrapper
sudo modprobe ndiswrapper

if it starts working, then blacklist islsm_usb and you should be set.

---

### Post by krasovskya on 2006-07-13
Not even close =) lol

> alexkrasovsky@alexkrasovsky-comp:~$ modprobe -r islsm_usb
FATAL: Error removing islsm_usb (/lib/modules/2.6.15-23-386/kernel/drivers/net/wireless/prism54_softmac/islsm_usb.ko): Operation not permitted
alexkrasovsky@alexkrasovsky-comp:~$ modprobe -r ndiswrapper
FATAL: Error removing ndiswrapper (/lib/modules/2.6.15-23-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted
alexkrasovsky@alexkrasovsky-comp:~$ sudo modprobe ndiswrapper


Ummm... next suggestion? lol =/ sorry I feel bad but nothing is working >_<

---

### Post by maniacmusician on 2006-07-13
try:

*sudo* modprobe -r islsm_usb
*sudo* modprobe -r ndiswrapper

whenever it says not permitted or something along those lines, it means you have to run as root. in windows terms, sudo means it will run the command as root (root = administrator)

oh yeah and don't forget:

sudo modprobe ndiswrapper

---

### Post by krasovskya on 2006-07-13
okay, finally we are getting somewhere =D

alright, it blinked a couple of times but then the light goes off. I restarted and as it restarted, the same thing happened as it was testing the hardware. So I assume this means that there is something wrong with my connection??

---

### Post by eternalsword on 2006-07-13
did you blacklist islsm_usb before restarting? if you did, try blacklisting islsm as well

---

### Post by krasovskya on 2006-07-13
you guys are awesome, thank you so much, it's working =D


thanks sooo much!!

hope this helps anyone else with the same problem. =D

---

### Post by eternalsword on 2006-07-13
no problem, I have the same hardware and had to meddle with it last week ;) though the driver ubuntu was using was the rtl8187.  just makes you wonder.  was yours made in taiwan or china.  mine was made in china, so if yours was made in taiwan, that might explain the different default drivers.

---

### Post by nuck on 2006-08-05
I've got a WG111v2 adapter and I can manage to get it to connect to my access point without security, but I'd like to use WPA security.  

Has anybody been able to do this?  Could they explain it to me?

Thanks.

---

