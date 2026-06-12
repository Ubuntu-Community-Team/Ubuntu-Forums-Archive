---
title: "So am I pretty much screwed here?"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by Grundalizer on 2007-06-04
When i was trying to install Ubuntu the first time, i wanted to partition my hard drive so I could keep windows as one OS, and Ubuntu as another.  It ended up giving me a bunch of errors and crap when I tried to do the first selection, to use free space as a second partition for Ubuntu, so i ended up choosing the second choice, replacing the entire single hard drive with Ubuntu.  So right now im pretty sure ubuntu/kubuntu are my only OS.

Is there any way, even with the windows recovery cd that came with this laptop, to revert back to windows?  

i really like ubuntu and have not regretted the switch at all except for the random freezes i am getting while doing next to nothing every hour or two, and not being able to use some open source games i am finding.  Not knowing any commands sucks and I am trying  to read and find some but all i see is dpkg, i can figure out how to copy and paste command lines people tell me online but i would have no idea how to do this stuff on my own.

---

### Post by 13warrior on 2007-06-04
If you used the second option of ersaing the entire HD with and install Ubuntu, then i think its tough (nearly impossible) to restore windows with the recovery cd. Ubuntu uses a different FS compared to Windows . if you still want windows , then you got to reinstall it. 

But I doubt you would that as Ubuntu is much better and stable than windows.

---

### Post by John.Michael.Kane on 2007-06-04
Your windows recovery cd that came with this laptop will erase ubuntu, and bring the machine back to factory default. After which you can try the method below.

[WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot?action=show&redirect=WindowsDualBootHowTo")

---

### Post by Grundalizer on 2007-06-04
Well I installed Ubuntu feisty yesterday and so far it has locked up 12 times.  Lockups happen when i open a new website, i open terminal, i try and move a window, anything random. I may have open only 1 or 2 web pages and if i click to open another sometimes things just lock up, i can still move my mouse around, then when i click somthing everything freezes.  I cannot fix the lockups, tried ctr alt backspace and that just kills everything and leaves me with with blank desktop and a mouse.  I then have to hold down my power button.  I wouldn't mind the not know how to run the OS yet if it wasn't for all the frigging lockups for no reason

---

### Post by LaRoza on 2007-06-04
This could be a hardware problem, what version of Windows was on the computer and how well did it run.

With my computer, I use Beryl, and open a lot of Windows at once, and Feisty never crashed, but I have the CPU and RAM for that.

---

### Post by rich.bradshaw on 2007-06-04
Yeah, it doesn't normally lock up. What's your hardware? What's the output of dmesg when it crashes?

i.e. wait for it to crash, try ctrl-alt-f1, if it gets to a terminal, log in and type dmesg, otherwise restart, and type dmesg in a terminal - try and find the bit at the time it crashes...

if you type dmesg > filename.txt it will put it into a file you can upload here, as it's probably very very very long!

---

### Post by Grundalizer on 2007-06-04
I ran windows xp and it was fine, i could have 10 browsers open and nothing would happen.  I have a pentium 4 2.8 ghz processor and although toshiba advertised 512 mb ram, i only have 376.3 mb available in the system screen.

so would it help the community if i filed bug reports on when these freezes occur? or do you have to know a little bit about what your doing to help with filing bug reports.

second, to keep from starting another thread, im in Ubuntu right now but all the applications are the KDE ones from Kubuntu, how the heck do i get back to Ubuntu only.  I tried doing some GDM dpkg thing but it never worked out.

ok i will try the dmesg thing, thanks for the replies.

---

### Post by Grundalizer on 2007-06-04
i just tried ctr alt F1, got to a black MS DOS looking screen, typed in dmesg, entered password, wait 3 seconds, login incorrect

---

### Post by blackened on 2007-06-04
You don't need to go to another tty, instead click on Applications -> Accessories -> Terminal, then in the terminal window that opens type dmesg. Cut and paste the results of that command here (wrap it in CODE tags using the advanced editor please).

If you were to do it from a different tty (ctrl+alt+F1-6), then you would first have to log in using your regular username and password.

---

### Post by Outrunner on 2007-06-04
> **Grundalizer said:**
> i just tried ctr alt F1, got to a black MS DOS looking screen, typed in dmesg, entered password, wait 3 seconds, login incorrect

lol, I'm sorry but that was really funny. I think you typed 'dmesg' instead of your username. You have to login first to get to the actual command prompt.

EDIT: Sorry, looks like blackened edited his post while I was posting this.

---

### Post by Grundalizer on 2007-06-04
i just did this after my computer froze again, after clicking on the Wine HQ link from google, i ran this as soon as i booted up

> god@Gods-laptop:~$ dmesg
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Wed May 23 01:46:23 UTC 2007 (Ubuntu 2.6.20-16.28-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000d0000 size: 0000000000008000 end: 00000000000d8000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e4000 size: 000000000001c000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 0000000017e70000 end: 0000000017f70000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 0000000017f70000 size: 000000000000b000 end: 0000000017f7b000 type: 3
[    0.000000] copy_e820_map() start: 0000000017f7b000 size: 0000000000005000 end: 0000000017f80000 type: 4
[    0.000000] copy_e820_map() start: 0000000017f80000 size: 0000000000080000 end: 0000000018000000 type: 2
[    0.000000] copy_e820_map() start: 0000000027f80000 size: 0000000000080000 end: 0000000028000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000fff80000 size: 0000000000080000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 00000000000d8000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000017f70000 (usable)
[    0.000000]  BIOS-e820: 0000000017f70000 - 0000000017f7b000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000017f7b000 - 0000000017f80000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000017f80000 - 0000000018000000 (reserved)
[    0.000000]  BIOS-e820: 0000000027f80000 - 0000000028000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 383MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f6ae0
[    0.000000] Entering add_active_range(0, 0, 98160) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    98160
[    0.000000]   HighMem     98160 ->    98160
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    98160
[    0.000000] On node 0 totalpages: 98160
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 734 pages used for memmap
[    0.000000]   Normal zone: 93330 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6b40
[    0.000000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x17f75dd2
[    0.000000] ACPI: FADT (v001 TOSCPL Chinook  0x06040000 ATI  0x00000003) @ 0x17f7af24
[    0.000000] ACPI: MADT (v001 PTLTD    APIC   0x06040000  LTP 0x00000000) @ 0x17f7af98
[    0.000000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20030224) @ 0x17f75e02
[    0.000000] ACPI: DSDT (v001 TOSCPL    SB200 0x06040000 MSFT 0x0100000e) @ 0x00000000
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:3 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:3 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 28000000:d6c00000)
[    0.000000] Detected 2800.335 MHz processor.
[   16.044679] Built 1 zonelists.  Total pages: 97394
[   16.044686] Kernel command line: root=UUID=25035697-3e97-4899-a5e0-2b724556f6dd ro quiet splash
[   16.044862] mapped APIC to ffffd000 (fee00000)
[   16.044865] mapped IOAPIC to ffffc000 (fec00000)
[   16.044868] Enabling fast FPU save and restore... done.
[   16.044872] Enabling unmasked SIMD FPU exception support... done.
[   16.044888] Initializing CPU#0
[   16.044981] PID hash table entries: 2048 (order: 11, 8192 bytes)
[   16.046025] Console: colour VGA+ 80x25
[   16.046532] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   16.046913] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   16.055418] Memory: 378040k/392640k available (1992k kernel code, 13992k reserved, 896k data, 328k init, 0k highmem)
[   16.055430] virtual kernel memory layout:
[   16.055431]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   16.055432]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   16.055433]     vmalloc : 0xd8800000 - 0xff7fe000   ( 623 MB)
[   16.055434]     lowmem  : 0xc0000000 - 0xd7f70000   ( 383 MB)
[   16.055435]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   16.055436]       .data : 0xc02f2354 - 0xc03d26d4   ( 896 kB)
[   16.055438]       .text : 0xc0100000 - 0xc02f2354   (1992 kB)
[   16.055441] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   16.132822] Calibrating delay using timer specific routine.. 5603.59 BogoMIPS (lpj=11207189)
[   16.132867] Security Framework v1.0.0 initialized
[   16.132873] SELinux:  Disabled at boot.
[   16.132892] Mount-cache hash table entries: 512
[   16.133042] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000459d 00000000 00000000
[   16.133051] monitor/mwait feature present.
[   16.133053] using mwait in idle threads.
[   16.133060] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   16.133063] CPU: L2 cache: 1024K
[   16.133066] CPU: Physical Processor ID: 0
[   16.133069] CPU: After all inits, caps: bfebfbff 00000000 00000000 00003180 0000459d 00000000 00000000
[   16.133080] Compat vDSO mapped to ffffe000.
[   16.133084] Remapping vsyscall page to ffffe000
[   16.133101] Checking 'hlt' instruction... OK.
[   16.148888] SMP alternatives: switching to UP code
[   16.149250] Early unpacking initramfs... done
[   16.441167] ACPI: Core revision 20060707
[   16.463882] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   16.469686] CPU0: Intel Mobile Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 04
[   16.469719] SMP alternatives: switching to SMP code
[   16.469858] Booting processor 1/1 eip 3000
[   16.480179] Initializing CPU#1
[   16.560024] Calibrating delay using timer specific routine.. 5600.66 BogoMIPS (lpj=11201333)
[   16.560036] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000459d 00000000 00000000
[   16.560044] monitor/mwait feature present.
[   16.560052] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   16.560055] CPU: L2 cache: 1024K
[   16.560058] CPU: Physical Processor ID: 0
[   16.560061] CPU: After all inits, caps: bfebfbff 00000000 00000000 00003180 0000459d 00000000 00000000
[   16.560456] CPU1: Intel Mobile Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 04
[   16.560501] Total of 2 processors activated (11204.26 BogoMIPS).
[   16.560569] ENABLING IO-APIC IRQs
[   16.560745] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   16.600382] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   16.600417] ...trying to set up timer (IRQ0) through the 8259A ...  failed.
[   16.600421] ...trying to set up timer as Virtual Wire IRQ... works.
[   16.747682] checking TSC synchronization across 2 CPUs: passed.
[    0.003992] Brought up 2 CPUs
[    0.361427] migration_cost=176
[    0.361765] Booting paravirtualized kernel on bare hardware
[    0.361841] Time: 14:03:33  Date: 05/04/107
[    0.361879] NET: Registered protocol family 16
[    0.361990] EISA bus registered
[    0.361997] ACPI: bus type pci registered
[    0.393204] PCI: PCI BIOS revision 2.10 entry at 0xfd958, last bus=2
[    0.393207] PCI: Using configuration type 1
[    0.393209] Setting up standard PCI resources
[    0.406260] ACPI: Interpreter enabled
[    0.406265] ACPI: Using IOAPIC for interrupt routing
[    0.406929] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.406936] PCI: Probing PCI hardware (bus 00)
[    0.408231] Boot video device is 0000:01:05.0
[    0.408492] PCI: Transparent bridge - 0000:00:14.4
[    0.408581] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.410781] ACPI: PCI Interrupt Link [LNK0] (IRQs 10 11) *0, disabled.
[    0.411026] ACPI: PCI Interrupt Link [LNK1] (IRQs 10 11) *0, disabled.
[    0.411278] ACPI: PCI Interrupt Link [LNK2] (IRQs 10 11) *0, disabled.
[    0.411520] ACPI: PCI Interrupt Link [LNK3] (IRQs 10 11) *0, disabled.
[    0.455255] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.456353] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.456848] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.456866] pnp: PnP ACPI init
[    0.479218] pnp: PnP ACPI: found 10 devices
[    0.479223] PnPBIOS: Disabled by ACPI PNP
[    0.479288] PCI: Using ACPI for IRQ routing
[    0.479293] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.483453] NET: Registered protocol family 8
[    0.483455] NET: Registered protocol family 20
[    0.483676] pnp: 00:07: ioport range 0x1080-0x1080 has been reserved
[    0.483680] pnp: 00:07: ioport range 0x220-0x22f has been reserved
[    0.483683] pnp: 00:07: ioport range 0x40b-0x40b has been reserved
[    0.483686] pnp: 00:07: ioport range 0x4d0-0x4d1 has been reserved
[    0.484065] PCI: Bridge: 0000:00:01.0
[    0.484069]   IO window: 9000-9fff
[    0.484073]   MEM window: d0100000-d01fffff
[    0.484077]   PREFETCH window: e0000000-efffffff
[    0.484089] PCI: Bus 3, cardbus bridge: 0000:02:04.0
[    0.484093]   IO window: 0000a400-0000a4ff
[    0.484098]   IO window: 0000a800-0000a8ff
[    0.484103]   PREFETCH window: 30000000-33ffffff
[    0.484109]   MEM window: 34000000-37ffffff
[    0.484114] PCI: Bridge: 0000:00:14.4
[    0.484118]   IO window: a000-afff
[    0.484123]   MEM window: d0200000-d02fffff
[    0.484128]   PREFETCH window: 30000000-33ffffff
[    0.484161] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 16 (level, low) -> IRQ 16
[    0.484204] NET: Registered protocol family 2
[    0.527107] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.527217] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.527325] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.527380] TCP: Hash tables configured (established 16384 bind 8192)
[    0.527384] TCP reno registered
[    0.539132] checking if image is initramfs... it is
[    1.120364] Freeing initrd memory: 6790k freed
[    1.121174] audit: initializing netlink socket (disabled)
[    1.121208] audit(1180965813.868:1): initialized
[    1.121431] VFS: Disk quotas dquot_6.5.1
[    1.121461] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.121541] io scheduler noop registered
[    1.121544] io scheduler anticipatory registered
[    1.121547] io scheduler deadline registered
[    1.121562] io scheduler cfq registered (default)
[    1.649211] isapnp: Scanning for PnP cards...
[    2.000282] isapnp: No Plug & Play device found
[    2.029787] Real Time Clock Driver v1.12ac
[    2.029858] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    2.030553] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 17
[    2.030561] ACPI: PCI interrupt for device 0000:00:14.6 disabled
[    2.030646] mice: PS/2 mouse device common for all mice
[    2.031403] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    2.031597] input: Macintosh mouse button emulation as /class/input/input0
[    2.031642] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    2.031647] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    2.031861] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    2.032149] i8042.c: Detected active multiplexing controller, rev 1.1.
[    2.032258] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.032264] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    2.032269] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    2.032273] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    2.032277] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    2.032846] EISA: Probing bus 0 at eisa.0
[    2.032863] Cannot allocate resource for EISA slot 1
[    2.032884] Cannot allocate resource for EISA slot 8
[    2.032886] EISA: Detected 0 cards.
[    2.062937] TCP cubic registered
[    2.062948] NET: Registered protocol family 1
[    2.062978] Starting balanced_irq
[    2.062988] Using IPI No-Shortcut mode
[    2.063087] input: AT Translated Set 2 keyboard as /class/input/input1
[    2.063184] ACPI: (supports S0 S3 S4 S5)
[    2.063265]   Magic number: 11:296:80
[    2.063916] Freeing unused kernel memory: 328k freed
[    2.064147] Time: tsc clocksource has been installed.
[    3.297633] Capability LSM initialized
[    3.343850] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Ist] [20060707]
[    3.344029] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Cst] [20060707]
[    3.344698] ACPI: Processor [CPU0] (supports 8 throttling states)
[    3.344988] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Ist] [20060707]
[    3.345148] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Cst] [20060707]
[    3.345261] ACPI: Processor [CPU1] (supports 8 throttling states)
[    3.867615] usbcore: registered new interface driver usbfs
[    3.867664] usbcore: registered new interface driver hub
[    3.968055] usbcore: registered new device driver usb
[    3.969387] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.969435] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 18
[    3.969452] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    3.969625] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[    3.969647] ohci_hcd 0000:00:13.0: irq 18, io mem 0xd0001000
[    4.032722] usb usb1: configuration #1 chosen from 1 choice
[    4.032791] hub 1-0:1.0: USB hub found
[    4.032815] hub 1-0:1.0: 3 ports detected
[    4.064004] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    4.140417] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 18
[    4.140443] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    4.140479] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[    4.140503] ohci_hcd 0000:00:13.1: irq 18, io mem 0xd0002000
[    4.204229] usb usb2: configuration #1 chosen from 1 choice
[    4.204274] hub 2-0:1.0: USB hub found
[    4.204288] hub 2-0:1.0: 3 ports detected
[    4.312231] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 18
[    4.312257] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    4.312315] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[    4.312388] ehci_hcd 0000:00:13.2: irq 18, io mem 0xd0003000
[    4.312402] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.312537] usb usb3: configuration #1 chosen from 1 choice
[    4.312585] hub 3-0:1.0: USB hub found
[    4.312598] hub 3-0:1.0: 6 ports detected
[    4.420013] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[    4.420037] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[    4.420053] ATIIXP: chipset revision 0
[    4.420056] ATIIXP: not 100% native mode: will probe irqs later
[    4.420068]     ide0: BM-DMA at 0x8070-0x8077, BIOS settings: hda:DMA, hdb:pio
[    4.420090]     ide1: BM-DMA at 0x8078-0x807f, BIOS settings: hdc:DMA, hdd:pio
[    4.420111] Probing IDE interface ide0...
[    4.711349] hda: IC25N060ATMR04-0, ATA DISK drive
[    4.998621] usb 1-2: new low speed USB device using ohci_hcd and address 3
[    5.243241] usb 1-2: configuration #1 chosen from 1 choice
[    5.257518] usbcore: registered new interface driver hiddev
[    5.262263] input: USB OpticalWheel Mouse as /class/input/input2
[    5.262305] input: USB HID v1.10 Mouse [USB OpticalWheel Mouse] on usb-0000:00:13.0-2
[    5.262328] usbcore: registered new interface driver usbhid
[    5.262333] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[    5.386165] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    5.408590] Probing IDE interface ide1...
[    6.144664] hdc: TOSHIBA DVD-ROM SD-R2512, ATAPI CD/DVD-ROM drive
[    6.835912] ide1 at 0x170-0x177,0x376 on irq 15
[    6.843824] 8139cp 0000:02:03.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[    6.843830] 8139cp 0000:02:03.0: Try the "8139too" driver instead.
[    6.847059] 8139too Fast Ethernet driver 0.9.28
[    6.847136] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 19 (level, low) -> IRQ 18
[    6.847653] eth0: RealTek RTL8139 at 0xd8850000, 00:02:3f:d6:27:c9, IRQ 18
[    6.847658] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    6.856052] SCSI subsystem initialized
[    6.864586] libata version 2.20 loaded.
[    6.875517] hda: max request size: 512KiB
[    6.883049] hda: 117210240 sectors (60011 MB) w/7884KiB Cache, CHS=16383/255/63, UDMA(100)
[    6.883327] hda: cache flushes supported
[    6.883396]  hda: hda1 hda2 < hda5 >
[    6.947812] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[    6.947826] Uniform CD-ROM driver Revision: 3.20
[    7.283054] Attempting manual resume
[    7.283059] swsusp: Resume From Partition 3:5
[    7.283061] PM: Checking swsusp image.
[    7.312602] PM: Resume from disk failed.
[    7.351414] EXT3-fs: INFO: recovery required on readonly filesystem.
[    7.351418] EXT3-fs: write access will be enabled during recovery.
[   12.796471] kjournald starting.  Commit interval 5 seconds
[   12.796487] EXT3-fs: hda1: orphan cleanup on readonly fs
[   12.796497] ext3_orphan_cleanup: deleting unreferenced inode 2932781
[   12.796533] ext3_orphan_cleanup: deleting unreferenced inode 6540950
[   12.840724] ext3_orphan_cleanup: deleting unreferenced inode 6640571
[   13.120855] ext3_orphan_cleanup: deleting unreferenced inode 32845
[   13.120883] EXT3-fs: hda1: 4 orphan inodes deleted
[   13.120885] EXT3-fs: recovery complete.
[   13.135908] EXT3-fs: mounted filesystem with ordered data mode.
[   26.803110] eth0: link down
[   28.082568] NET: Registered protocol family 17
[   28.277079] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   28.346779] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   28.379458] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   28.699522] input: PC Speaker as /class/input/input3
[   28.701674] ath_hal: module license 'Proprietary' taints kernel.
[   28.702868] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   29.059257] wlan: 0.8.4.2 (0.9.3)
[   29.112628] Linux agpgart interface v0.102 (c) Dave Jones
[   29.114809] agpgart: Detected Ati IGP9100/M chipset
[   29.123659] agpgart: AGP aperture is 32M @ 0xd2000000
[   29.275150] Yenta: CardBus bridge found at 0000:02:04.0 [1179:ff00]
[   29.275178] Yenta: Using CSCINT to route CSC interrupts to PCI
[   29.275182] Yenta: Routing CardBus interrupts to PCI
[   29.275189] Yenta TI: socket 0000:02:04.0, mfunc 0x00111c12, devctl 0x44
[   29.352293] ath_pci: 0.9.4.5 (0.9.3)
[   29.367838] input: PS/2 Mouse as /class/input/input4
[   29.375327] parport: PnPBIOS parport detected.
[   29.375358] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   29.386587] input: AlpsPS/2 ALPS GlidePoint as /class/input/input5
[   29.509396] Yenta: ISA IRQ mask 0x0c68, PCI irq 16
[   29.509401] Socket status: 30000006
[   29.509407] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[   29.509410] cs: IO port probe 0xa000-0xafff: clean.
[   29.509698] pcmcia: parent PCI bridge Memory window: 0xd0200000 - 0xd02fffff
[   29.509701] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[   29.510028] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 18 (level, low) -> IRQ 19
[   30.108364] ath_rate_sample: 1.2 (0.9.3)
[   30.108832] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   30.108843] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   30.108863] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   30.108875] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   30.108884] wifi0: mac 5.9 phy 4.3 radio 4.6
[   30.108892] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   30.108896] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   30.108900] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   30.108903] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   30.108906] wifi0: Use hw queue 8 for CAB traffic
[   30.108909] wifi0: Use hw queue 9 for beacons
[   30.221746] wifi0: Atheros 5212: mem=0xd0200000, irq=19
[   30.221992] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 17
[   30.278252] atiixp-modem: codec reset timeout
[   30.343200] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 17
[   30.663599] cs: IO port probe 0x100-0x3af: clean.
[   30.673992] cs: IO port probe 0x3e0-0x4ff: clean.
[   30.674545] cs: IO port probe 0x820-0x8ff: clean.
[   30.675012] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcd7
[   30.675582] cs: IO port probe 0xa00-0xaff: clean.
[   30.998029] fuse init (API version 7.8)
[   31.025106] lp0: using parport0 (interrupt-driven).
[   31.060478] Adding 1124508k swap on /dev/disk/by-uuid/e1ef8f30-5989-4e57-a003-db174fbc170c.  Priority:-1 extents:1 across:1124508k
[   31.210588] EXT3 FS on hda1, internal journal
[   32.539579] NET: Registered protocol family 10
[   32.539736] lo: Disabled Privacy Extensions
[   32.539815] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   35.453532] No dock devices found.
[   35.475078] ACPI: AC Adapter [ACAD] (on-line)
[   35.505651] ACPI: Battery Slot [BAT1] (battery present)
[   35.513082] Using specific hotkey driver
[   35.645262] ibm_acpi: ec object not found
[   35.696411] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   35.755999] input: Power Button (FF) as /class/input/input6
[   35.756041] ACPI: Power Button (FF) [PWRF]
[   35.756110] input: Lid Switch as /class/input/input7
[   35.756131] ACPI: Lid Switch [LID]
[   35.756184] input: Power Button (CM) as /class/input/input8
[   35.756230] ACPI: Power Button (CM) [PWRB]
[   35.863014] pcc_acpi: loading...
[   41.367497] [drm] Initialized drm 1.1.0 20060810
[   41.427918] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 16 (level, low) -> IRQ 16
[   41.428552] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[   42.035945] ppdev: user-space parallel port driver
[   44.741265] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   44.741294] agpgart: Putting AGP V3 device at 0000:00:00.0 into 4x mode
[   44.741550] agpgart: Putting AGP V3 device at 0000:01:05.0 into 4x mode
[   44.890950] [drm] Setting GART location based on new memory map
[   44.890966] [drm] Loading R200 Microcode
[   44.891025] [drm] writeback test succeeded in 1 usecs
[   45.689405] apm: BIOS not found.
[   46.272377] Bluetooth: Core ver 2.11
[   46.272490] NET: Registered protocol family 31
[   46.272494] Bluetooth: HCI device and connection manager initialized
[   46.272500] Bluetooth: HCI socket layer initialized
[   46.318005] Bluetooth: L2CAP ver 2.8
[   46.318014] Bluetooth: L2CAP socket layer initialized
[   46.387575] Bluetooth: RFCOMM socket layer initialized
[   46.387598] Bluetooth: RFCOMM TTY layer initialized
[   46.387604] Bluetooth: RFCOMM ver 1.8
[   80.329665] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[   95.892161] ath0: no IPv6 routers present
god@Gods-laptop:~$ 


---

### Post by Grundalizer on 2007-06-04
ah i see i will log in first next time, but ctr alt f1 never works when i get these lockups. i was just running ubuntu for 4 minutes and i had another freeze, nothing is working.  could installing kubuntu be a problem?  i am running ubuntu but kdm seems to be the platform or somthing because all the applications are kubuntu ones, how the hell do i get rid of kubuntu completely.

---

### Post by phidia on 2007-06-04
It would be helpful to have the complete system specs or at least know what video card your computer is using. 
Maybe you have an onboard video card/gpu? That could be the factor in the difference you mentioned between the listed ram and the ram the system reports _if_ you have an onboard gpu _and_ it uses system ram.

---

### Post by Bartender on 2007-06-04
Just a thought -
I get the impression that in some ways Linux is less tolerant of hardware problems than Windows. 

Toss your LiveCD in and run the memtest function.  Let it run for at least an hour or two.  if you get any faults your RAM is failing.  If you have two sticks of RAM inside open up the shell and identify the #1 memory slot.  Pull the #2 piece of RAM and run memtest again.  If no problems pull the good RAM out of #1 slot and put the other piece in #1.  Run memtest again.  You may have to replace both sticks if they're running as dual-channel.  It can be risky trying to find an exact match. 

Also, did you check your LiveCD for errors before installing?

---

### Post by Grundalizer on 2007-06-04
video card is a Radeon 9100 IGP mobility

---

### Post by Grundalizer on 2007-06-04
i just checked my cd and it is fine.  this freezing is driving me #$^%ing nuts.  i just uninstalled Kubuntu maybe that will help.  when i start up everytime for a milisecond i see somthing that says bios bug (numbers) disconnected from (numbers) think that has anything to do with it?

---

### Post by ccfjeff on 2007-06-04
> **Grundalizer said:**
> video card is a Radeon 9100 IGP mobility

Did the card and memory come packaged with the computer?  Radeon has a page about compatibilities/incompatibilities with different memory modules:

[http://ati.amd.com/products/mobilityradeon9100igp/memvendor.html]("http://ati.amd.com/products/mobilityradeon9100igp/memvendor.html")

---

