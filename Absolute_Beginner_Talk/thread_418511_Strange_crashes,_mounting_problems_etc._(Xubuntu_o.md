---
title: "Strange crashes, mounting problems etc. (Xubuntu on Samsung X11)"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by LinuxVictim on 2007-04-22
Hi there,
so far, xubuntu has been relatively nice to me.
But there are some really strange things going on on my system:
[LIST=1]
[*]When I boot it tells me about some PCI Bridge resource problem, but that doesnt seem to be fatal
[*]During boot i get "BUG:Soft lockup detected on CPU#0" during different stages:
[*]During filesystem mount
[*]During fsck run (very frequently)
[*]During Network (possibly WiFi) startup
[*]Or simply not
[/LIST]

I have to boot 3 times on the average, to manage it into X.

I know this list is crude. What other Information shall I provide?
I am a total linux newbie.

Well I'll give it a try:

Samsung X11 T5500 "CeSeba" 
Intel Core2Duo T5500 Processor
1Gig of slow RAM
80Gig HD
NVIDIA 7400 Go

With xubuntu (is that feisty fawn???)

I installed the smp package, but I dont know if it really did something.

Here's my dmesg output:
17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[17179569.184000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000003fe90000 (usable)
[17179569.184000]  BIOS-e820: 000000003fe90000 - 000000003fe9a000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000003fe9a000 - 000000003ff00000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000003ff00000 - 0000000040000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[17179569.184000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[17179569.184000] 126MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f7610
[17179569.184000] On node 0 totalpages: 261776
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 32400 pages, LIFO batch:7
[17179569.184000] DMI present.
[17179569.184000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f7580
[17179569.184000] ACPI: RSDT (v001 PTLTD  Capell00 0x06040000  LTP 0x00000000) @ 0x3fe92380
[17179569.184000] ACPI: FADT (v001 INTEL  CALISTGA 0x06040000 LOHR 0x0000005a) @ 0x3fe99e20
[17179569.184000] ACPI: MADT (v001 INTEL  CALISTGA 0x06040000 LOHR 0x0000005a) @ 0x3fe99e94
[17179569.184000] ACPI: HPET (v001 INTEL  CALISTGA 0x06040000 LOHR 0x0000005a) @ 0x3fe99efc
[17179569.184000] ACPI: MCFG (v001 INTEL  CALISTGA 0x06040000 LOHR 0x0000005a) @ 0x3fe99f34
[17179569.184000] ACPI: MADT (v001 PTLTD  	 APIC   0x06040000  LTP 0x00000000) @ 0x3fe99f70
[17179569.184000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x3fe99fd8
[17179569.184000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20050624) @ 0x3fe923c0
[17179569.184000] ACPI: DSDT (v001 INTEL  CALISTGA 0x06040000 INTL 0x20050624) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: 2 duplicate APIC table ignored.
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:15 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[17179569.184000] Processor #1 6:15 APIC version 20
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda6 ro nosplash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[17179569.184000] Console: colour VGA+ 80x25
[17179569.184000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179569.184000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.184000] Memory: 1027980k/1047104k available (1910k kernel code, 18428k reserved, 1070k data, 308k init, 129600k highmem)
[17179569.184000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.184000] hpet0: at MMIO 0xfed00000 (virtual 0xf8800000), IRQs 2, 8, 0
[17179569.184000] hpet0: 3 64-bit timers, 14318180 Hz
[17179569.184000] Using HPET for base-timer
[17179569.184000] Using HPET for gettimeofday
[17179569.184000] Detected 1662.588 MHz processor.
[17179569.184000] Using hpet for high-res timesource
[17179569.268000] Calibrating delay using timer specific routine.. 3329.10 BogoMIPS (lpj=6658200)
[17179569.268000] Security Framework v1.0.0 initialized
[17179569.268000] SELinux:  Disabled at boot.
[17179569.268000] Mount-cache hash table entries: 512
[17179569.268000] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e39d 00000000 00000001
[17179569.268000] CPU: After vendor identify, caps: bfebfbff 20000000 00000000 00000000 0000e39d 00000000 00000001
[17179569.268000] monitor/mwait feature present.
[17179569.268000] using mwait in idle threads.
[17179569.268000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179569.268000] CPU: L2 cache: 2048K
[17179569.268000] CPU: Hyper-Threading is disabled
[17179569.268000] CPU: After all inits, caps: bfebfbff 20000000 00000000 00000140 0000e39d 00000000 00000001
[17179569.268000] Checking 'hlt' instruction... OK.
[17179569.284000] SMP alternatives: switching to UP code
[17179569.284000] checking if image is initramfs... it is
[17179569.796000] Freeing initrd memory: 5626k freed
[17179569.796000] ACPI: Core revision 20060707
[17179569.796000] ACPI: Looking for DSDT ... not found!
[17179569.832000] CPU0: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz stepping 06
[17179569.832000] SMP alternatives: switching to SMP code
[17179569.832000] Booting processor 1/1 eip 3000
[17179569.840000] Initializing CPU#1
[17179569.924000] Calibrating delay using timer specific routine.. 3325.07 BogoMIPS (lpj=6650149)
[17179569.924000] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e39d 00000000 00000001
[17179569.924000] CPU: After vendor identify, caps: bfebfbff 20000000 00000000 00000000 0000e39d 00000000 00000001
[17179569.924000] monitor/mwait feature present.
[17179569.924000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179569.924000] CPU: L2 cache: 2048K
[17179569.924000] CPU: Hyper-Threading is disabled
[17179569.924000] CPU: After all inits, caps: bfebfbff 20000000 00000000 00000140 0000e39d 00000000 00000001
[17179569.924000] CPU1: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz stepping 06
[17179569.924000] Total of 2 processors activated (6654.17 BogoMIPS).
[17179569.924000] ENABLING IO-APIC IRQs
[17179569.924000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179570.072000] checking TSC synchronization across 2 CPUs: passed.
[17179570.076000] Brought up 2 CPUs
[17179570.340000] migration_cost=4000
[17179570.340000] NET: Registered protocol family 16
[17179570.340000] EISA bus registered
[17179570.340000] ACPI: bus type pci registered
[17179570.340000] PCI: Using MMCONFIG
[17179570.340000] Setting up standard PCI resources
[17179570.344000] mtrr: your CPUs had inconsistent variable MTRR settings
[17179570.344000] mtrr: probably your BIOS does not setup all CPUs.
[17179570.344000] mtrr: corrected configuration.
[17179570.348000] ACPI: Interpreter enabled
[17179570.348000] ACPI: Using IOAPIC for interrupt routing

---

### Post by LinuxVictim on 2007-04-25
Er... did I do something wrong?

No replies? not even something along the lines of: I dont know?
I hope I didn't offend anyone??

---

### Post by LinuxVictim on 2007-05-07
Ok I solved it.

During my previous debian installation on the system,
(somewhere half through a pack of nerve pills)
I changed the BIOS setting "Disk geometry" from DOS to unix and totally forgot about it.
Interestingly Windows didnt seem to take any offense, but fsck choked heavily on that.

So once upon a time when I ambled through my BIOS settings, I stumbled over
the setting again, and changed it back to DOS.

Everything seems to be fine now.

I hope others who run into the same problem find this post.
(I searched for quite a while and found _nothing_)

OT:
Excuse my scorn when I say "thanks for all the help",
but I just can't help it.

I know that obviously some knowledgeable people have read this post,
thought about it and didn't answer because they didn't know a solution.
The unanswered posts button makes this a sensible course of action.
But not getting ANY response, not even sympathy spam (explicitly asked for),
 for weeks, in an obviously active forum, is extremely disappointing.
Haven't felt that let down in all my net-life.

---

