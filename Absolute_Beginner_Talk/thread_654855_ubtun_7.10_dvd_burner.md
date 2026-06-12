---
title: "ubtun 7.10 dvd burner"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by rich79 on 2007-12-31
hello,

i have a dvd burner and ubuntu refuse to recornize it. I can not burn (only iso) i can not read from the cd. 

the cd physically o.k cuz the ubuntu was installed from it! 

Help! Help!

Ohad

---

### Post by pt123 on 2007-12-31
trying installing the application k3b
sudo apt-get install k3b

---

### Post by rich79 on 2008-01-01
Hi,

no good!

error msg:

No CD/DVD writer found.
K3b did not find an optical writing device in your system. Thus, you will not be able to burn CDs or DVDs. However, you can still use other K3b features like audio track extraction or audio transcoding or ISO9660 image creation.

what do I do?? I want to paint my computer to blue and dump it in the see....

Help! Help!
Ohad

---

### Post by Sef on 2008-01-01
How is it set up?  As a primary or secondary master or slave?

---

### Post by BL00dFox on 2008-01-01
> **rich79 said:**
> Hi,

no good!

error msg:

No CD/DVD writer found.
K3b did not find an optical writing device in your system. Thus, you will not be able to burn CDs or DVDs. However, you can still use other K3b features like audio track extraction or audio transcoding or ISO9660 image creation.

what do I do?? I want to paint my computer to blue and dump it in the see....

Help! Help!
Ohad

lol, I like the way you express your frustration.

Post your DVD drive's model here, so we can have a look to see if there are any issues or fixes for it..

---

### Post by rich79 on 2008-01-01
Hi,

I don't know if it is slave or master cuz I have only one!

in any case it doesn't do what it shoud do: 2 work!

It is sumsung dvd burner. 

Ohad 

p.s happy new year

---

### Post by laidback on 2008-01-01
To see whether it's configured to master or slave you'll need to look at the back of the drive to find out how the jumpers are set. This will probably mean taking the drive out of the case. I'm more concerned to find out if it's set to Cable Select rather than master/slave. In my experience Linux doesn't like drives set to Cable Select.

---

### Post by rich79 on 2008-01-01
Hi,

I don't want to open the computer. I will open it only to make it fish food!
I can not even read from the cd nor burn. 
the drive is fine cuz I installed ubuntu from live cd. and it work fine on 7.04. after upgrade to 7.10 It doesn't work. 

Ohad

---

### Post by laidback on 2008-01-01
Could it be that for some reason it just hasn't automounted. Look in Place>Computer to see if you can mount it by hand.

---

### Post by rich79 on 2008-01-01
Hello,

while trying to see a disk content the fish food give me a msg:
Unable to mount the selected volume.
mount: special device /dev/hda does not exist
Help! Help!

Ohad

---

### Post by pt123 on 2008-01-01
in a terminal type: dmesg
and post the output here

---

### Post by rich79 on 2008-01-02
Smart people,
where is my dvd burner???

ohad@ohad-desktop:~$ dmesg
[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Dec 18 08:02:57 UTC 2007 (Ubuntu 2.6.22-14.47-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e7000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ffc0000 (usable)
[    0.000000]  BIOS-e820: 000000003ffc0000 - 000000003ffce000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ffce000 - 000000003fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fff0000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 262080) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   262080
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   262080
[    0.000000] On node 0 totalpages: 262080
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 255 pages used for memmap
[    0.000000]   HighMem zone: 32449 pages, LIFO batch:7
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F9A10 checksum 0
[    0.000000] ACPI: RSDP 000F9A10, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 3FFC0000, 0034 (r1 A M I  OEMRSDT   1000703 MSFT       97)
[    0.000000] ACPI: FACP 3FFC0200, 0084 (r2 A M I  OEMFACP   1000703 MSFT       97)
[    0.000000] ACPI: DSDT 3FFC0440, 465E (r1    P31     P31G        0 INTL 20051117)
[    0.000000] ACPI: FACS 3FFCE000, 0040
[    0.000000] ACPI: APIC 3FFC0390, 006C (r1 A M I  OEMAPIC   1000703 MSFT       97)
[    0.000000] ACPI: MCFG 3FFC0400, 003C (r1 A M I  OEMMCFG   1000703 MSFT       97)
[    0.000000] ACPI: OEMB 3FFCE040, 0060 (r1 A M I  AMI_OEM   1000703 MSFT       97)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:6 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:6 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 20, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bee00000)
[    0.000000] Built 1 zonelists.  Total pages: 260033
[    0.000000] Kernel command line: root=UUID=974d414d-7519-4188-9682-e7d46f0c6092 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2999.464 MHz processor.
[   28.249986] Console: colour VGA+ 80x25
[   28.251998] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   28.253718] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   28.309171] Memory: 1027584k/1048320k available (2015k kernel code, 20024k reserved, 916k data, 364k init, 130816k highmem)
[   28.309189] virtual kernel memory layout:
[   28.309190]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   28.309191]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   28.309192]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   28.309193]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   28.309194]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   28.309195]       .data : 0xc02f7de6 - 0xc03dce84   ( 916 kB)
[   28.309196]       .text : 0xc0100000 - 0xc02f7de6   (2015 kB)
[   28.309199] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   28.309279] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   28.389222] Calibrating delay using timer specific routine.. 6004.10 BogoMIPS (lpj=12008218)
[   28.389282] Security Framework v1.0.0 initialized
[   28.389295] SELinux:  Disabled at boot.
[   28.389317] Mount-cache hash table entries: 512
[   28.389588] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e49d 00000000 00000001
[   28.389597] monitor/mwait feature present.
[   28.389599] using mwait in idle threads.
[   28.389611] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   28.389614] CPU: L2 cache: 2048K
[   28.389618] CPU: Physical Processor ID: 0
[   28.389620] CPU: Processor Core ID: 0
[   28.389622] CPU: After all inits, caps: bfebfbff 20000000 00000000 0000b180 0000e49d 00000000 00000001
[   28.389643] Compat vDSO mapped to ffffe000.
[   28.389671] Checking 'hlt' instruction... OK.
[   28.405485] SMP alternatives: switching to UP code
[   28.406594] Early unpacking initramfs... done
[   28.722177] ACPI: Core revision 20070126
[   28.722319] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   28.725200] CPU0: Intel(R) Pentium(R) D CPU 3.00GHz stepping 05
[   28.725220] SMP alternatives: switching to SMP code
[   28.725351] Booting processor 1/1 eip 3000
[   28.735859] Initializing CPU#1
[   28.812708] Calibrating delay using timer specific routine.. 5998.82 BogoMIPS (lpj=11997648)
[   28.812718] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e49d 00000000 00000001
[   28.812724] monitor/mwait feature present.
[   28.812730] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   28.812733] CPU: L2 cache: 2048K
[   28.812735] CPU: Physical Processor ID: 0
[   28.812736] CPU: Processor Core ID: 1
[   28.812738] CPU: After all inits, caps: bfebfbff 20000000 00000000 0000b180 0000e49d 00000000 00000001
[   28.813312] CPU1: Intel(R) Pentium(R) D CPU 3.00GHz stepping 05
[   28.813347] Total of 2 processors activated (12002.93 BogoMIPS).
[   28.813445] ENABLING IO-APIC IRQs
[   28.813612] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   28.853290] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   28.853343] ...trying to set up timer (IRQ0) through the 8259A ...  failed.
[   28.853346] ...trying to set up timer as Virtual Wire IRQ... works.
[   29.000572] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   29.020575] Brought up 2 CPUs
[   29.229400] migration_cost=3637
[   29.229571] Booting paravirtualized kernel on bare hardware
[   29.229646] Time: 19:28:14  Date: 00/02/108
[   29.229670] NET: Registered protocol family 16
[   29.229770] EISA bus registered
[   29.229776] ACPI: bus type pci registered
[   29.231325] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=1
[   29.231328] PCI: Using configuration type 1
[   29.231330] Setting up standard PCI resources
[   29.245740] ACPI: EC: Look up EC in DSDT
[   29.250426] ACPI: Interpreter enabled
[   29.250429] ACPI: (supports S0 S1 S3 S4 S5)
[   29.250453] ACPI: Using IOAPIC for interrupt routing
[   29.258539] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   29.258547] PCI: Probing PCI hardware (bus 00)
[   29.259363] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   29.265476] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 *10 11 12 14 15)
[   29.265601] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 7 10 11 12 14 15)
[   29.265724] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 *11 12 14 15)
[   29.265845] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 7 10 11 12 14 15)
[   29.265967] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 7 10 11 12 14 15)
[   29.266088] ACPI: PCI Interrupt Link [LNKF] (IRQs *3 4 5 7 10 11 12 14 15)
[   29.266209] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 *10 11 12 14 15)
[   29.266331] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 *11 12 14 15)
[   29.266440] Linux Plug and Play Support v0.97 (c) Adam Belay
[   29.266455] pnp: PnP ACPI init
[   29.266465] ACPI: bus type pnp registered
[   29.270504] pnp: PnP ACPI: found 13 devices
[   29.270507] ACPI: ACPI bus type pnp unregistered
[   29.270512] PnPBIOS: Disabled by ACPI PNP
[   29.270563] PCI: Using ACPI for IRQ routing
[   29.270567] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   29.273695] NET: Registered protocol family 8
[   29.273698] NET: Registered protocol family 20
[   29.273761] pnp: 00:08: ioport range 0xa00-0xa0f has been reserved
[   29.273765] pnp: 00:08: ioport range 0xa10-0xa1f has been reserved
[   29.273772] pnp: 00:09: iomem range 0xfff80000-0xffffffff could not be reserved
[   29.273776] pnp: 00:09: iomem range 0xffe80000-0xffefffff could not be reserved
[   29.273779] pnp: 00:09: iomem range 0xfed00000-0xfed003ff has been reserved
[   29.273785] pnp: 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
[   29.273788] pnp: 00:0a: iomem range 0xfee00000-0xfee00fff could not be reserved
[   29.273793] pnp: 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
[   29.273799] pnp: 00:0c: iomem range 0x0-0x9ffff could not be reserved
[   29.273802] pnp: 00:0c: iomem range 0xc0000-0xcffff could not be reserved
[   29.273806] pnp: 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[   29.273809] pnp: 00:0c: iomem range 0x100000-0x3fffffff could not be reserved
[   29.276693] Time: tsc clocksource has been installed.
[   29.304120] PCI: Bridge: 0000:00:01.0
[   29.304124]   IO window: e000-efff
[   29.304130]   MEM window: fa000000-febfffff
[   29.304135]   PREFETCH window: b0000000-bfffffff
[   29.304161] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   29.304173] NET: Registered protocol family 2
[   29.340706] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   29.340801] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   29.341720] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   29.342039] TCP: Hash tables configured (established 131072 bind 65536)
[   29.342042] TCP reno registered
[   29.352893] checking if image is initramfs... it is
[   29.800177] Switched to high resolution mode on CPU 1
[   29.804122] Switched to high resolution mode on CPU 0
[   29.930090] Freeing initrd memory: 7119k freed
[   29.931181] audit: initializing netlink socket (disabled)
[   29.931199] audit(1199302094.312:1): initialized
[   29.931354] highmem bounce pool size: 64 pages
[   29.934501] VFS: Disk quotas dquot_6.5.1
[   29.934576] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   29.934692] io scheduler noop registered
[   29.934696] io scheduler anticipatory registered
[   29.934699] io scheduler deadline registered
[   29.934721] io scheduler cfq registered (default)
[   30.007821] Boot video device is 0000:01:00.0
[   30.007931] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   30.007977] assign_interrupt_mode Found MSI capability
[   30.007980] Allocate Port Service[0000:00:01.0:pcie00]
[   30.008193] isapnp: Scanning for PnP cards...
[   30.359444] isapnp: No Plug & Play device found
[   30.396555] Real Time Clock Driver v1.12ac
[   30.396691] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   30.396790] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   30.397622] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   30.398670] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   30.398845] input: Macintosh mouse button emulation as /class/input/input0
[   30.398971] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   30.398974] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   30.399246] serio: i8042 KBD port at 0x60,0x64 irq 1
[   30.399252] serio: i8042 AUX port at 0x60,0x64 irq 12
[   30.399452] mice: PS/2 mouse device common for all mice
[   30.399631] EISA: Probing bus 0 at eisa.0
[   30.399673] EISA: Detected 0 cards.
[   30.399768] TCP cubic registered
[   30.399788] NET: Registered protocol family 1
[   30.399809] Using IPI No-Shortcut mode
[   30.399976]   Magic number: 8:60:495
[   30.400419] Freeing unused kernel memory: 364k freed
[   30.427330] input: AT Translated Set 2 keyboard as /class/input/input1
[   31.614856] AppArmor: AppArmor initialized<5>audit(1199302095.812:2):  type=1505 info="AppArmor initialized" pid=1202
[   31.623487] fuse init (API version 7.8)
[   31.628548] Failure registering capabilities with primary security module.
[   31.667344] ACPI Warning (tbutils-0217): Incorrect checksum in table [SSDT] -  FD, should be 04 [20070126]
[   31.667355] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  DD, should be D8 [20070126]
[   31.667361] ACPI: SSDT 3FFC4AA0, 02E3 (r1    AMI   CPU1PM        1 INTL 20051117)
[   31.667584] ACPI: Processor [CPU1] (supports 8 throttling states)
[   31.667634] ACPI: SSDT 3FFC4D90, 02DA (r1    AMI   CPU2PM        1 INTL 20051117)
[   31.667791] ACPI: Processor [CPU2] (supports 8 throttling states)
[   31.667805] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   31.667818] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   31.668935] ACPI: Thermal Zone [THRM] (40 C)
[   32.149534] usbcore: registered new interface driver usbfs
[   32.149572] usbcore: registered new interface driver hub
[   32.149604] usbcore: registered new device driver usb
[   32.150463] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   32.150506] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 16
[   32.150521] ohci_hcd 0000:00:03.0: OHCI Host Controller
[   32.150651] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[   32.150667] ohci_hcd 0000:00:03.0: irq 16, io mem 0xf9fff000
[   32.156263] SCSI subsystem initialized
[   32.161707] libata version 2.21 loaded.
[   32.182101] sis900.c: v1.08.10 Apr. 2 2006
[   32.228624] usb usb1: configuration #1 chosen from 1 choice
[   32.228660] hub 1-0:1.0: USB hub found
[   32.228670] hub 1-0:1.0: 3 ports detected
[   32.329133] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 17
[   32.329153] ohci_hcd 0000:00:03.1: OHCI Host Controller
[   32.329185] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[   32.329205] ohci_hcd 0000:00:03.1: irq 17, io mem 0xf9ffe000
[   32.387005] usb usb2: configuration #1 chosen from 1 choice
[   32.387036] hub 2-0:1.0: USB hub found
[   32.387047] hub 2-0:1.0: 3 ports detected
[   32.488893] ACPI: PCI Interrupt 0000:00:03.2[C] -> GSI 22 (level, low) -> IRQ 18
[   32.488903] ohci_hcd 0000:00:03.2: OHCI Host Controller
[   32.488926] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
[   32.488939] ohci_hcd 0000:00:03.2: irq 18, io mem 0xf9ffd000
[   32.546795] usb usb3: configuration #1 chosen from 1 choice
[   32.546825] hub 3-0:1.0: USB hub found
[   32.546834] hub 3-0:1.0: 2 ports detected
[   32.651348] pata_sis 0000:00:02.5: version 0.5.1
[   32.651490] scsi0 : pata_sis
[   32.651811] scsi1 : pata_sis
[   32.651941] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001fff0 irq 14
[   32.651945] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001fff8 irq 15
[   32.952230] usb 3-1: new low speed USB device using ohci_hcd and address 2
[   32.960432] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 19
[   32.971372] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 31.
[   32.971702] 0000:00:04.0: Using transceiver found at address 31 as default
[   32.972454] eth0: SiS 900 PCI Fast Ethernet at 0xd400, IRQ 19, 00:19:21:59:35:b8.
[   32.972489] sata_sis 0000:00:05.0: version 0.8
[   32.972527] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 17 (level, low) -> IRQ 20
[   32.972535] sata_sis 0000:00:05.0: Detected SiS 180/181/964 chipset in SATA mode
[   32.972627] scsi2 : sata_sis
[   32.972676] scsi3 : sata_sis
[   32.972763] ata3: SATA max UDMA/133 cmd 0x0001d000 ctl 0x0001cc02 bmdma 0x0001c000 irq 20
[   32.972769] ata4: SATA max UDMA/133 cmd 0x0001c800 ctl 0x0001c402 bmdma 0x0001c008 irq 20
[   33.156089] usb 3-1: configuration #1 chosen from 1 choice
[   33.169325] usbcore: registered new interface driver hiddev
[   33.174295] input: HID 062a:0001 as /class/input/input2
[   33.174433] input: USB HID v1.10 Mouse [HID 062a:0001] on usb-0000:00:03.2-1
[   33.174448] usbcore: registered new interface driver usbhid
[   33.174452] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   33.447639] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   33.455956] ata3.00: ATA-7: ST3200826AS, 3.06, max UDMA/133
[   33.455960] ata3.00: 390721968 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   33.471894] ata3.00: configured for UDMA/133
[   33.783224] ata4: SATA link down (SStatus 0 SControl 300)
[   33.793617] scsi 2:0:0:0: Direct-Access     ATA      ST3200826AS      3.06 PQ: 0 ANSI: 5
[   33.793999] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 23 (level, low) -> IRQ 21
[   33.794016] ehci_hcd 0000:00:03.3: EHCI Host Controller
[   33.794058] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 4
[   33.794093] PCI: cache line size of 128 is not supported by device 0000:00:03.3
[   33.794105] ehci_hcd 0000:00:03.3: irq 21, io mem 0xf9ffc000
[   33.794114] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   33.794170] usb 3-1: USB disconnect, address 2
[   33.794232] usb usb4: configuration #1 chosen from 1 choice
[   33.794272] hub 4-0:1.0: USB hub found
[   33.794280] hub 4-0:1.0: 8 ports detected
[   33.806828] sd 2:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
[   33.806845] sd 2:0:0:0: [sda] Write Protect is off
[   33.806849] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   33.806869] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   33.806929] sd 2:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
[   33.806942] sd 2:0:0:0: [sda] Write Protect is off
[   33.806945] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   33.806964] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   33.806968]  sda: sda1 sda2 < sda5 >
[   33.849252] sd 2:0:0:0: [sda] Attached SCSI disk
[   33.852953] sd 2:0:0:0: Attached scsi generic sg0 type 0
[   34.124416] Attempting manual resume
[   34.124420] swsusp: Resume From Partition 8:5
[   34.124422] PM: Checking swsusp image.
[   34.124579] PM: Resume from disk failed.
[   34.171037] kjournald starting.  Commit interval 5 seconds
[   34.171049] EXT3-fs: mounted filesystem with ordered data mode.
[   34.394475] usb 3-1: new low speed USB device using ohci_hcd and address 3
[   34.598340] usb 3-1: configuration #1 chosen from 1 choice
[   34.607422] input: HID 062a:0001 as /class/input/input3
[   34.607447] input: USB HID v1.10 Mouse [HID 062a:0001] on usb-0000:00:03.2-1
[   40.958170] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   40.996898] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   41.155459] input: PC Speaker as /class/input/input4
[   41.215747] parport_pc 00:07: reported by Plug and Play ACPI
[   41.215797] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   41.281168] Linux agpgart interface v0.102 (c) Dave Jones
[   41.467133] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 22
[   41.789503] intel8x0_measure_ac97_clock: measured 54890 usecs
[   41.789507] intel8x0: clocking to 48000
[   42.741950] lp0: using parport0 (interrupt-driven).
[   42.792540] Adding 3028212k swap on /dev/sda5.  Priority:-1 extents:1 across:3028212k
[   43.122447] EXT3 FS on sda1, internal journal
[   44.117226] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   44.170321] input: Power Button (FF) as /class/input/input5
[   44.170345] ACPI: Power Button (FF) [PWRF]
[   44.170439] input: Power Button (CM) as /class/input/input6
[   44.170457] ACPI: Power Button (CM) [PWRB]
[   44.227801] No dock devices found.
[   47.639384] eth0: Media Link On 100mbps full-duplex 
[   47.912459] ppdev: user-space parallel port driver
[   48.090875] audit(1199302113.107:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4804 profile="/usr/sbin/cupsd"
[   48.134755] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   48.134763] apm: disabled - APM is not SMP safe.
[   50.010778] Failure registering capabilities with primary security module.
[   50.310645] Bluetooth: Core ver 2.11
[   50.310731] NET: Registered protocol family 31
[   50.310734] Bluetooth: HCI device and connection manager initialized
[   50.310740] Bluetooth: HCI socket layer initialized
[   50.323624] Bluetooth: L2CAP ver 2.8
[   50.323632] Bluetooth: L2CAP socket layer initialized
[   50.377524] Bluetooth: RFCOMM socket layer initialized
[   50.377549] Bluetooth: RFCOMM TTY layer initialized
[   50.377555] Bluetooth: RFCOMM ver 1.8
[   54.564049] NET: Registered protocol family 17
[   55.931448] NET: Registered protocol family 10
[   55.931567] lo: Disabled Privacy Extensions
[   66.491151] eth0: no IPv6 routers present
ohad@ohad-desktop:~$ 
thank you in advance,
Ohad

---

### Post by pt123 on 2008-01-02
is the dvd a sata connection?

If you go into your bios it should tell you how your hard drives & cd/dvd roms are connected

looking at the dmesg you only have one 200GM hard disk connected
> 33.806828] sd 2:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
[ 33.806845] sd 2:0:0:0: [sda] Write Protect is off
[ 33.806849] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 33.806869] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 33.806929] sd 2:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
[ 33.806942] sd 2:0:0:0: [sda] Write Protect is off
[ 33.806945] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 33.806964] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 33.806968] sda: sda1 sda2 < sda5 >

[ 33.806968] sda: sda1 sda2 < sda5 >
[ 33.849252] sd 2:0:0:0: [sda] Attached SCSI disk
[ 33.852953] sd 2:0:0:0: Attached scsi generic sg0 type 0


see on mine it lists the 3 hard drives and the burner
> 
[   51.221124] sd 2:0:0:0: [sdc] Attached SCSI disk
[   51.228219] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   51.228375] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   51.228414] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   51.228446] sr 3:0:0:0: Attached scsi generic sg3 type 5
[   51.269080] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray


---

### Post by rich79 on 2008-01-03
Hi,

I am hopping I'm answering your question.
at the Bios I have the cd rom as IDE master.

and in Places --> Computer I see Cd rom1 but it doesn't work. 

How  come??

Ohad 

p.s thank you for your piation.

---

### Post by pt123 on 2008-01-03
> **rich79 said:**
> Hi,

I am hopping I'm answering your question.
at the Bios I have the cd rom as IDE master.

Does it say primary ? or secondary?Maybe you can list all the hard drives & roms listed.

> 
and in Places --> Computer I see Cd rom1 but it doesn't work. 

How  come??

I think that is there by default.

---

### Post by mc4man on 2008-01-03
> 
the drive is fine cuz I installed ubuntu from live cd. and it work fine on 7.04. after upgrade to 7.10 It doesn't work. 
if this means you upgraded 7.04 to 7.10 from the update manager at some point consider a fresh gutsy install. 
You could try booting up to whatever live cd you have and then running dmesg and see what shows up

---

### Post by rich79 on 2008-01-04
Hi,

From live cd: 

ubuntu@ubuntu:~$ dmesg
[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc
version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC
2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size:
000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size:
0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e7000 size:
0000000000019000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size:
000000003fec0000 end: 000000003ffc0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000003ffc0000 size:
000000000000e000 end: 000000003ffce000 type: 3
[    0.000000] copy_e820_map() start: 000000003ffce000 size:
0000000000022000 end: 000000003fff0000 type: 4
[    0.000000] copy_e820_map() start: 000000003fff0000 size:
0000000000010000 end: 0000000040000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size:
0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000ff780000 size:
0000000000880000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e7000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ffc0000 (usable)
[    0.000000]  BIOS-e820: 000000003ffc0000 - 000000003ffce000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ffce000 - 000000003fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fff0000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 262080) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   262080
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   262080
[    0.000000] On node 0 totalpages: 262080
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 255 pages used for memmap
[    0.000000]   HighMem zone: 32449 pages, LIFO batch:7
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 ACPIAM                                )
@ 0x000f9a10
[    0.000000] ACPI: RSDT (v001 A M I  OEMRSDT  0x01000703 MSFT
0x00000097) @ 0x3ffc0000
[    0.000000] ACPI: FADT (v002 A M I  OEMFACP  0x01000703 MSFT
0x00000097) @ 0x3ffc0200
[    0.000000] ACPI: MADT (v001 A M I  OEMAPIC  0x01000703 MSFT
0x00000097) @ 0x3ffc0390
[    0.000000] ACPI: MCFG (v001 A M I  OEMMCFG  0x01000703 MSFT
0x00000097) @ 0x3ffc0400
[    0.000000] ACPI: OEMB (v001 A M I  AMI_OEM  0x01000703 MSFT
0x00000097) @ 0x3ffce040
[    0.000000] ACPI: DSDT (v001    P31     P31G 0x00000000 INTL
0x20051117) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:6 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:6 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 20, address 0xfec00000, GSI
0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap:
40000000:bee00000)
[    0.000000] Detected 2999.505 MHz processor.
[   52.205383] Built 1 zonelists.  Total pages: 260033
[   52.205394] Kernel command line: BOOT_IMAGE=/casper/vmlinuz
file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz
quiet splash --
[   52.205644] mapped APIC to ffffd000 (fee00000)
[   52.205648] mapped IOAPIC to ffffc000 (fec00000)
[   52.205653] Enabling fast FPU save and restore... done.
[   52.205657] Enabling unmasked SIMD FPU exception support... done.
[   52.205691] Initializing CPU#0
[   52.205871] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   52.207954] Console: colour VGA+ 80x25
[   52.210026] Dentry cache hash table entries: 131072 (order: 7, 524288
bytes)
[   52.211733] Inode-cache hash table entries: 65536 (order: 6, 262144
bytes)
[   52.264783] Memory: 1028020k/1048320k available (1992k kernel code,
19680k reserved, 893k data, 328k init, 130816k highmem)
[   52.264799] virtual kernel memory layout:
[   52.264800]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   52.264801]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   52.264802]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   52.264803]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   52.264804]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   52.264805]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   52.264806]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   52.264809] Checking if this processor honours the WP bit even in
supervisor mode... Ok.
[   52.341713] Calibrating delay using timer specific routine.. 6003.76
BogoMIPS (lpj=12007528)
[   52.341778] Security Framework v1.0.0 initialized
[   52.341792] SELinux:  Disabled at boot.
[   52.341816] Mount-cache hash table entries: 512
[   52.342075] CPU: After generic identify, caps: bfebfbff 20000000
00000000 00000000 0000e49d 00000000 00000001
[   52.342084] monitor/mwait feature present.
[   52.342086] using mwait in idle threads.
[   52.342096] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   52.342099] CPU: L2 cache: 2048K
[   52.342103] CPU: Physical Processor ID: 0
[   52.342105] CPU: Processor Core ID: 0
[   52.342107] CPU: After all inits, caps: bfebfbff 20000000 00000000
00003180 0000e49d 00000000 00000001
[   52.342128] Compat vDSO mapped to ffffe000.
[   52.342136] Remapping vsyscall page to ffffe000
[   52.342159] Checking 'hlt' instruction... OK.
[   52.357969] SMP alternatives: switching to UP code
[   52.358958] Early unpacking initramfs... done
[   52.669920] ACPI: Core revision 20060707
[   52.670938] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not
found, using machine DSDT.
[   52.673870] CPU0: Intel(R) Pentium(R) D CPU 3.00GHz stepping 05
[   52.673894] SMP alternatives: switching to SMP code
[   52.674020] Booting processor 1/1 eip 3000
[   52.684573] Initializing CPU#1
[   52.765200] Calibrating delay using timer specific routine.. 5998.84
BogoMIPS (lpj=11997696)
[   52.765209] CPU: After generic identify, caps: bfebfbff 20000000
00000000 00000000 0000e49d 00000000 00000001
[   52.765216] monitor/mwait feature present.
[   52.765222] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   52.765224] CPU: L2 cache: 2048K
[   52.765226] CPU: Physical Processor ID: 0
[   52.765228] CPU: Processor Core ID: 1
[   52.765230] CPU: After all inits, caps: bfebfbff 20000000 00000000
00003180 0000e49d 00000000 00000001
[   52.765771] CPU1: Intel(R) Pentium(R) D CPU 3.00GHz stepping 05
[   52.765806] Total of 2 processors activated (12002.61 BogoMIPS).
[   52.765903] ENABLING IO-APIC IRQs
[   52.766071] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   52.805747] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   52.805801] ...trying to set up timer (IRQ0) through the 8259A ... 
failed.
[   52.805804] ...trying to set up timer as Virtual Wire IRQ... works.
[   52.952980] checking TSC synchronization across 2 CPUs: passed.
[    0.003999] Brought up 2 CPUs
[    0.258161] migration_cost=3394
[    0.258473] Booting paravirtualized kernel on bare hardware
[    0.258558] Time: 15:25:02  Date: 00/04/108
[    0.258593] NET: Registered protocol family 16
[    0.258689] EISA bus registered
[    0.258695] ACPI: bus type pci registered
[    0.260249] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=1
[    0.260252] PCI: Using configuration type 1
[    0.260253] Setting up standard PCI resources
[    0.279565] ACPI: Interpreter enabled
[    0.279568] ACPI: Using IOAPIC for interrupt routing
[    0.280256] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.280261] PCI: Probing PCI hardware (bus 00)
[    0.281208] Boot video device is 0000:01:00.0
[    0.281278] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.298388] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 *10 11 12
14 15)
[    0.298661] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 7 10 11 12
14 15)
[    0.298932] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 *11 12
14 15)
[    0.299203] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 7 10 11 12
14 15)
[    0.299532] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 7 10 11 12
14 15)
[    0.299805] ACPI: PCI Interrupt Link [LNKF] (IRQs *3 4 5 7 10 11 12
14 15)
[    0.300076] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 *10 11 12
14 15)
[    0.300473] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 *11 12
14 15)
[    0.300658] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.300668] pnp: PnP ACPI init
[    0.305790] pnp: PnP ACPI: found 13 devices
[    0.305794] PnPBIOS: Disabled by ACPI PNP
[    0.305842] PCI: Using ACPI for IRQ routing
[    0.305845] PCI: If a device doesn't work, try "pci=routeirq".  If it
helps, post a report
[    0.308979] NET: Registered protocol family 8
[    0.308981] NET: Registered protocol family 20
[    0.309866] pnp: 00:08: ioport range 0xa00-0xa0f has been reserved
[    0.309870] pnp: 00:08: ioport range 0xa10-0xa1f has been reserved
[    0.310354] PCI: Bridge: 0000:00:01.0
[    0.310358]   IO window: e000-efff
[    0.310364]   MEM window: fa000000-febfffff
[    0.310369]   PREFETCH window: b0000000-bfffffff
[    0.310395] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    0.310430] NET: Registered protocol family 2
[    0.352630] IP route cache hash table entries: 32768 (order: 5,
131072 bytes)
[    0.352809] TCP established hash table entries: 131072 (order: 8,
1048576 bytes)
[    0.353392] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.353710] TCP: Hash tables configured (established 131072 bind 65536)
[    0.353713] TCP reno registered
[    0.364716] checking if image is initramfs... it is
[    0.931512] Freeing initrd memory: 6966k freed
[    0.932241] audit: initializing netlink socket (disabled)
[    0.932257] audit(1199460302.728:1): initialized
[    0.932435] highmem bounce pool size: 64 pages
[    0.932589] VFS: Disk quotas dquot_6.5.1
[    0.932623] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.932698] io scheduler noop registered
[    0.932702] io scheduler anticipatory registered
[    0.932710] io scheduler deadline registered
[    0.932740] io scheduler cfq registered (default)
[    0.995643] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    0.995688] assign_interrupt_mode Found MSI capability
[    0.995691] Allocate Port Service[0000:00:01.0:pcie00]
[    0.995863] isapnp: Scanning for PnP cards...
[    1.347129] isapnp: No Plug & Play device found
[    1.373518] Real Time Clock Driver v1.12ac
[    1.373580] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ
sharing enabled
[    1.373702] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.374371] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.374569] mice: PS/2 mouse device common for all mice
[    1.375261] RAMDISK driver initialized: 16 RAM disks of 65536K size
1024 blocksize
[    1.375518] input: Macintosh mouse button emulation as
/class/input/input0
[    1.375564] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.375569] ide: Assuming 33MHz system bus speed for PIO modes;
override with idebus=xx
[    1.375804] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.375807] PNP: PS/2 controller doesn't have AUX irq; using default 12
[    1.376006] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.376012] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.376125] EISA: Probing bus 0 at eisa.0
[    1.376168] EISA: Detected 0 cards.
[    1.406338] TCP cubic registered
[    1.406358] NET: Registered protocol family 1
[    1.406395] Starting balanced_irq
[    1.406403] Using IPI No-Shortcut mode
[    1.406490] input: AT Translated Set 2 keyboard as /class/input/input1
[    1.406535] ACPI: (supports S0 S1 S3 S4 S5)
[    1.406585]   Magic number: 8:233:436
[    1.407043] Freeing unused kernel memory: 328k freed
[    1.410288] Time: tsc clocksource has been installed.
[    2.626760] Capability LSM initialized
[    2.670604] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [   AMI]
OemTableId [  CPU1PM] [20060707]
[    2.670669] ACPI: Processor [CPU1] (supports 8 throttling states)
[    2.670872] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [   AMI]
OemTableId [  CPU2PM] [20060707]
[    2.670912] ACPI: Processor [CPU2] (supports 8 throttling states)
[    2.670923] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND,
Processor Device is not present [20060707]
[    2.670930] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND,
Processor Device is not present [20060707]
[    2.671966] ACPI: Thermal Zone [THRM] (40 C)
[    3.077197] usbcore: registered new interface driver usbfs
[    3.077223] usbcore: registered new interface driver hub
[    3.077248] usbcore: registered new device driver usb
[    3.077962] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller
(OHCI) Driver
[    3.078001] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level,
low) -> IRQ 16
[    3.078015] ohci_hcd 0000:00:03.0: OHCI Host Controller
[    3.078163] ohci_hcd 0000:00:03.0: new USB bus registered, assigned
bus number 1
[    3.078180] ohci_hcd 0000:00:03.0: irq 16, io mem 0xf9fff000
[    3.116249] sis900.c: v1.08.10 Apr. 2 2006
[    3.158341] usb usb1: configuration #1 chosen from 1 choice
[    3.158372] hub 1-0:1.0: USB hub found
[    3.158384] hub 1-0:1.0: 3 ports detected
[    3.260282] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level,
low) -> IRQ 17
[    3.260303] ohci_hcd 0000:00:03.1: OHCI Host Controller
[    3.260333] ohci_hcd 0000:00:03.1: new USB bus registered, assigned
bus number 2
[    3.260352] ohci_hcd 0000:00:03.1: irq 17, io mem 0xf9ffe000
[    3.318144] usb usb2: configuration #1 chosen from 1 choice
[    3.318172] hub 2-0:1.0: USB hub found
[    3.318183] hub 2-0:1.0: 3 ports detected
[    3.420160] ACPI: PCI Interrupt 0000:00:03.2[C] -> GSI 22 (level,
low) -> IRQ 18
[    3.420174] ohci_hcd 0000:00:03.2: OHCI Host Controller
[    3.420196] ohci_hcd 0000:00:03.2: new USB bus registered, assigned
bus number 3
[    3.420209] ohci_hcd 0000:00:03.2: irq 18, io mem 0xf9ffd000
[    3.426805] SCSI subsystem initialized
[    3.433231] libata version 2.20 loaded.
[    3.478110] usb usb3: configuration #1 chosen from 1 choice
[    3.478141] hub 3-0:1.0: USB hub found
[    3.478151] hub 3-0:1.0: 2 ports detected
[    3.580083] SIS5513: IDE controller at PCI slot 0000:00:02.5
[    3.580128] SIS5513: chipset revision 1
[    3.580130] SIS5513: not 100% native mode: will probe irqs later
[    3.580143] SIS5513: SiS 962/963 MuTIOL IDE UDMA133 controller
[    3.580160]     ide0: BM-DMA at 0xfff0-0xfff7, BIOS settings:
hda:DMA, hdb:DMA
[    3.580176]     ide1: BM-DMA at 0xfff8-0xffff, BIOS settings:
hdc:DMA, hdd:DMA
[    3.580188] Probing IDE interface ide0...
[    3.761803] hda: probing with STATUS(0x50) instead of ALTSTATUS(0x00)
[    3.883755] usb 3-1: new low speed USB device using ohci_hcd and
address 2
[    3.929628] hda: probing with STATUS(0x51) instead of ALTSTATUS(0x00)
[    4.093378] usb 3-1: configuration #1 chosen from 1 choice
[    4.105652] usbcore: registered new interface driver hiddev
[    4.110485] input: HID 062a:0001 as /class/input/input2
[    4.110599] input: USB HID v1.10 Mouse [HID 062a:0001] on
usb-0000:00:03.2-1
[    4.110614] usbcore: registered new interface driver usbhid
[    4.110618] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[    4.209383] hda: probing with STATUS(0x51) instead of ALTSTATUS(0x00)
[    4.321446] hda: TSSTcorpCD/DVDW SH-S182F, ATAPI CD/DVD-ROM drive
[    4.656941] hdb: probing with STATUS(0x01) instead of ALTSTATUS(0x00)
[    4.824798] hdb: probing with STATUS(0x01) instead of ALTSTATUS(0x00)
[    4.992868] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    4.995850] Probing IDE interface ide1...
[    5.568162] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 23 (level,
low) -> IRQ 19
[    5.568181] ehci_hcd 0000:00:03.3: EHCI Host Controller
[    5.568314] ehci_hcd 0000:00:03.3: new USB bus registered, assigned
bus number 4
[    5.568349] PCI: cache line size of 128 is not supported by device
0000:00:03.3
[    5.568356] ehci_hcd 0000:00:03.3: irq 19, io mem 0xf9ffc000
[    5.568365] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver
10 Dec 2004
[    5.568392] usb 3-1: USB disconnect, address 2
[    5.572137] usb usb4: configuration #1 chosen from 1 choice
[    5.572287] hub 4-0:1.0: USB hub found
[    5.572296] hub 4-0:1.0: 8 ports detected
[    5.677630] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level,
low) -> IRQ 20
[    5.689075] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at
address 31.
[    5.689434] 0000:00:04.0: Using transceiver found at address 31 as
default
[    5.690189] eth0: SiS 900 PCI Fast Ethernet at 0xd400, IRQ 20,
00:19:21:59:35:b8.
[    5.691704] sata_sis 0000:00:05.0: version 0.7
[    5.691734] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 17 (level,
low) -> IRQ 21
[    5.691748] sata_sis 0000:00:05.0: Detected SiS 180/181/964 chipset
in SATA mode
[    5.691814] ata1: SATA max UDMA/133 cmd 0x0001d000 ctl 0x0001cc02
bmdma 0x0001c000 irq 21
[    5.691844] ata2: SATA max UDMA/133 cmd 0x0001c800 ctl 0x0001c402
bmdma 0x0001c008 irq 21
[    5.691858] scsi0 : sata_sis
[    5.709646] hda: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB
Cache, UDMA(33)
[    5.709658] Uniform CD-ROM driver Revision: 3.20
[    6.158112] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    6.166396] ata1.00: ata_hpa_resize 1: sectors = 390721968,
hpa_sectors = 390721968
[    6.166406] ata1.00: ATA-7: ST3200826AS, 3.06, max UDMA/133
[    6.166410] ata1.00: 390721968 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    6.175980] ata1.00: ata_hpa_resize 1: sectors = 390721968,
hpa_sectors = 390721968
[    6.175986] ata1.00: configured for UDMA/133
[    6.176004] scsi1 : sata_sis
[    6.183697] usb 3-1: new low speed USB device using ohci_hcd and
address 3
[    6.298984] ISO 9660 Extensions: Microsoft Joliet Level 3
[    6.367067] ISO 9660 Extensions: RRIP_1991A
[    6.379571] usb 3-1: configuration #1 chosen from 1 choice
[    6.388558] input: HID 062a:0001 as /class/input/input3
[    6.388587] input: USB HID v1.10 Mouse [HID 062a:0001] on
usb-0000:00:03.2-1
[    6.406479] Registering unionfs 20060916-2203
[    6.406483] unionfs: debugging is not enabled
[    6.413587] loop: loaded (max 8 devices)
[    6.486155] ata2: SATA link down (SStatus 0 SControl 300)
[    6.496299] ATA: abnormal status 0x7F on port 0x0001c807
[    6.496423] scsi 0:0:0:0: Direct-Access     ATA      ST3200826AS    
 3.06 PQ: 0 ANSI: 5
[    6.505011] SCSI device sda: 390721968 512-byte hdwr sectors (200050 MB)
[    6.505026] sda: Write Protect is off
[    6.505029] sda: Mode Sense: 00 3a 00 00
[    6.505049] SCSI device sda: write cache: enabled, read cache:
enabled, doesn't support DPO or FUA
[    6.505099] SCSI device sda: 390721968 512-byte hdwr sectors (200050 MB)
[    6.505111] sda: Write Protect is off
[    6.505114] sda: Mode Sense: 00 3a 00 00
[    6.505133] SCSI device sda: write cache: enabled, read cache:
enabled, doesn't support DPO or FUA
[    6.505136]  sda: sda1 sda2 < sda5 >
[    6.550680] sd 0:0:0:0: Attached scsi disk sda
[    6.554456] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    6.774694] squashfs: version 3.2-r2 (2007/01/15) Phillip Lougher
[   62.989685] Linux agpgart interface v0.102 (c) Dave Jones
[   63.270859] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   63.536217] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   63.655117] input: PC Speaker as /class/input/input4
[   63.657346] parport: PnPBIOS parport detected.
[   63.657393] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   64.104871] eth0: Media Link On 100mbps full-duplex 
[   64.392280] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level,
low) -> IRQ 22
[   64.427610] NET: Registered protocol family 17
[   64.706282] intel8x0_measure_ac97_clock: measured 54880 usecs
[   64.706286] intel8x0: clocking to 48000
[   65.321939] fuse init (API version 7.8)
[   66.317710] Adding 3028212k swap on /dev/sda5.  Priority:-1 extents:1
across:3028212k
[   66.741974] NET: Registered protocol family 10
[   66.742091] lo: Disabled Privacy Extensions
[   73.042763] input: Power Button (FF) as /class/input/input5
[   73.042938] ACPI: Power Button (FF) [PWRF]
[   73.043767] input: Power Button (CM) as /class/input/input6
[   73.043914] ACPI: Power Button (CM) [PWRB]
[   73.084210] No dock devices found.
[   73.103197] Using specific hotkey driver
[   73.161600] ibm_acpi: ec object not found
[   73.260069] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   73.328246] pcc_acpi: loading...
[   77.568089] eth0: no IPv6 routers present
[   85.470759] lp0: using parport0 (interrupt-driven).
[   85.707800] ppdev: user-space parallel port driver
[   93.007947] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   93.007952] apm: disabled - APM is not SMP safe.
[   93.584498] eth0: no IPv6 routers present
[   95.081596] Bluetooth: Core ver 2.11
[   95.081669] NET: Registered protocol family 31
[   95.081671] Bluetooth: HCI device and connection manager initialized
[   95.081675] Bluetooth: HCI socket layer initialized
[   95.308018] Bluetooth: L2CAP ver 2.8
[   95.308025] Bluetooth: L2CAP socket layer initialized
[   95.442819] Bluetooth: RFCOMM socket layer initialized
[   95.442838] Bluetooth: RFCOMM TTY layer initialized
[   95.442841] Bluetooth: RFCOMM ver 1.8
ubuntu@ubuntu:~$ 

At the Bios next to the cd rom is writen primely. 
thank you in advance.
Ohad
P.s I can not install ubuntu 7.10 from disk cuz the dvd burner isn't working!

---

### Post by LowSky on 2008-01-04
does the DVD/RW work ok with regular CDs/DVDs, if it does it could be bad media yoor using.

---

### Post by rich79 on 2008-01-04
Hi,

The fish food in the future is not responding to any cd with data or not. and if I try to burn I have a msg : No burner. 

Ohad

---

### Post by pt123 on 2008-01-04
You are going to have to change the jumper settings on the CD drive to slave. Because Ubuntu is getting confused. Not sure between which releases but they changed all the drive lettering to sdx from hdx. This caused many problems on upgrades. 

Also have you updated the kernel using the update manager. Because once (not sure when) fixed a lot of the issues because of the lettering problem. 

On your LiveCD dmesg it is listing your hard disk as hda and your cd rom as sda.

---

### Post by rich79 on 2008-01-05
Hi,

I changed the ide slot to secondary place and changed the jumper on the dvd burner. 
NO CHANGE at ubuntu.

Ohad

---

### Post by pt123 on 2008-01-05
Damn, maybe you could try posting this in the installation section.

[http://ubuntuforums.org/forumdisplay.php?f=140](http://ubuntuforums.org/forumdisplay.php?f=140)

---

### Post by rich79 on 2008-01-05
Hi,

o.k no problem.

Ohad

p.s if it will not solve in 1 week it is  going to be fish food.

---

### Post by toallpointswest on 2008-02-09
I think I ran into the same problem you just did. You try to burn a cd/dvd with K3b in Ubuntu 7.10 (Gutsy) and it tells you it can't find your drive. 

Problem is the /dev/hdx links are owned by root with a group of cdrom,  this command should fix the problem

sudo usermod -G cdrom * username*

Good luck

---

### Post by jamaisvu on 2008-04-19
> **toallpointswest said:**
> I think I ran into the same problem you just did. You try to burn a cd/dvd with K3b in Ubuntu 7.10 (Gutsy) and it tells you it can't find your drive. 

Problem is the /dev/hdx links are owned by root with a group of cdrom,  this command should fix the problem

sudo usermod -G cdrom * username*

Good luck

[FONT=Book Antiqua] This appears to be back in Hardy, but with a twist -- the admin group seems to be messed up too, so [FONT=Courier New]sudo[/FONT] doesn't work. However, [FONT=Courier New]su && usermod -G admin *username* && usermod -G cdrom *username*[/FONT] does indeed work, so long as you've remembered to set your root password before upgrading!
[/FONT]

---

