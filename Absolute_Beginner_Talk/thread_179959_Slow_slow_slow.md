---
title: "Slow slow slow"
date: 2006-05-21
forum: Absolute Beginner Talk
---

### Post by Mangani on 2006-05-21
I've got an old HP omnibook XE3L (20GB HD, 256RAM, 1GHz I think), and installed Ubuntu on it (took a lot of time, since the CD-rom is barely working). 
Now it seem to work, but opening windows (not Windows, that is) literally takes minutes, especially bigger programs like Open Office. Shutting the windows often takes force.
I've searched the web for clues, and tried replacing ubuntu with xubuntu, and installing the linux-686 kernel. But there has been no improvement whatsoever.

I'm reluctant to try another Linux due to my poor CD-ROM, and I'm not even sure of the same problem will arise with other Linux distributions.

](*,) 
Please relieve my aching forehead.

---

### Post by Jussi Kukkonen on 2006-05-21
This is not much help but a datapoint:  I have a Omnibook XE2 (256MB, 400MHz) working fine -- Openoffice is a dog admittedly (might take about a minute to load), but otherwise it's fine. 

Do the problems "feel" like they're rendering related, or is your machine clearly doing some cpu or disk i/o related when it's slow? 

The only explanations (not very good ones, I admit) I can think of:
* display driver is acting up. Do you know what card your omnibook has?
* For some reason you have no swap in use (check with *free*).

---

### Post by gingermark on 2006-05-21
That seems odd. I used to run Kubuntu on a 800MHz Celeron Desktop with 128MB RAM. Sure, OOo took a while to load, and sometimes Konqueror would struggle, but it was usable nontheless.

Xubuntu might be the way to go. If you have a broadband internet connection, you can install it by typing (or copying) the following into Terminal (which is in your System menu I think, I don't use Ubuntu, so...) ```
sudo aptitude update
sudo aptitude install xubuntu-desktop
```

You might also want to look at other Window Managers. [This article](http://ubuntuforums.org/showthread.php?t=87276) should give you an idea of what is available, although I'd recommend using aptitude instead of apt-get here. It makes their removal easier if you don't like them.

I like "Window Maker" - it might take a bit of getting used to, but is very light.

Do keep in mind that the applications you run will have the biggest impact on your computer- and OOo is one if the most RAM intensive everyday applications there is! Maybe try Abiword instead of OOo Writer for example.

Hope that helps.

---

### Post by macdo on 2006-05-21
[QUOTE=gingermark]
Xubuntu might be the way to go. If you have a broadband internet connection, you can install it by typing (or copying) the following into Terminal (which is in your System menu I think, I don't use Ubuntu, so...) [/QUOTE]
[QUOTE=Mangani]I've searched the web for clues, and tried replacing ubuntu with xubuntu, and installing the linux-686 kernel. But there has been no improvement whatsoever.[/quote]
...

Sorry, I couldn't resist :twisted: 
Try running ```
top
``` at the command line, and see what using up all the memory (hint: to quit, use ctrl+c). Use ```
man top
``` for instructions.

---

### Post by Mangani on 2006-05-21
Thanks to all of you for quick response.

Jussi - I don't have a great intuition about these things. But the "thinking circle" icon is only visible for 20 seconds, then I get a barely responsive arrow the remaining 4 or 5 minutes. The HD-icon is lit the whole time. 
I've checked the swap, and it was about 345', which should be adequate.
I think the graphics are handled by a Intel i830 MG.

gingermark - maybe a new window manager is the way to go. When Firefox finally starts, surfing is a bit slow, but acceptable.

macdo - the top command showed something like this:
...
Cpu(s): 0.7%us 0.3%sy 0.0%ni 99.0%id 0,0%wa 0.0%hi 0.0%si
Mem:  117340k total, 113384k used, 3956k free, 856k buffers
Swap: 345356k total, 97512k used, 247844k free, 16164k cached

I don't know if the "99%id" is a symptom of something, but the figure for total memory seemed small didn't it? And it mentions 2 users?

---

### Post by macdo on 2006-05-21
Let's find out more about the second user - if you had two human users, then you should really know about it...
Run the command 'users' at the CL. See what that gives you. 
Also run 'who', which will give you a bit of detail (login date/time).

Post output?

---

### Post by Mangani on 2006-05-21
2 users is definitely odd, since I'm the only one messing with this old thing.
Not familiar enough with ubuntu to understand what "CL" means, but "who" in terminal gave:

kaare    :0         2006-05-21 22:24
kaare    pts/0     2006-05-21 22:28 (:0.0)

and "users" gave
kaare kaare

Am I running two identical users simultanously?

---

### Post by Mustard on 2006-05-21
The two users is because you have a terminal open.  One user is you with the GUI desktop running, and the other is you with the terminal running.  If you open another terminal window in addition to the one you have open now, you will notice that there are now three users.

---

### Post by Jussi Kukkonen on 2006-05-21
Mustard is right about users.
```
Jussi - I don't have a great intuition about these things. But the "thinking circle" icon is only visible for 20 seconds, then I get a barely responsive arrow the remaining 4 or 5 minutes. The HD-icon is lit the whole time.
```

That certainly isn't normal. If this thread happens to go nowhere in helping you, I think you ought to file a bug -- there won't be much data to file, but the problem is serious...

Hey... that *top* output you pasted -- it seems to say you have 115 MB of memory. I believe we found the problem. Does *free* say the same?

---

### Post by Niranjan81 on 2006-05-21
ok... so i did the 2 commands given above ...the 'aptitude install kubuntu-desktop' n the other one before it.... but how do i see the hcanges that r being done to the system.... its all installed n stuff thru the terminal..... but where do i see the changes???? thats been the problem with me throughout....i install something ...it installs... n then i don't know where to go n get it or how to start it.... i am new here n know the problem is my lack of knowledge ... please advise. Thanks.

---

### Post by rahelvey on 2006-05-21
sudo aptitude update
sudo aptitude install xubuntu-desktop

should have beem x not k buntu supposed to be a very light fast desktop I have not tryed it yet but will soon my old box is a relic.

---

### Post by Mangani on 2006-05-22
[QUOTE=Jussi Kukkonen]
Hey... that *top* output you pasted -- it seems to say you have 115 MB of memory. I believe we found the problem. Does *free* say the same?[/QUOTE]

Yes. - It didn't strike me as an impressive amount. Could it be that ubuntu only partitioned 115MB for itself?

---

### Post by 3rdalbum on 2006-05-22
On my computer with 256 megs of RAM, I'm running Firefox, Gaim and Dnetc and it's only using 20 megs of swap, so I wouldn't have thought that a lack of swap space would be causing such slowdown.

However, the Ubuntu partitioner does make some questionable choices about swap space. It allocated over 600 megs of swap for this computer, but for my other computer it allocated less than its real memory.

---

### Post by dmizer on 2006-05-22
[QUOTE=Mangani](took a lot of time, since the CD-rom is barely working).[/QUOTE]
^ is most likely the source of your problems.  even though you are not using the cdrom when using the os, it is still a part of your ide controller which is linked to your hard drive.

i believe your speed issue here is hardware related rather than software related.

to confirm this, you might post the output of your dmesg.

i had similar problems with an ailing hdd which did not have any bad sectors, but something was definatly wrong with it.  as soon as i replaced the drive, i had no more problems.

---

### Post by Mangani on 2006-05-22
Dmizer, here is my dmesg:

[4294667.296000] Linux version 2.6.15-23-686 (buildd@vernadsky) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Thu May 18 17:31:41 UTC 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009e800 (usable)
[4294667.296000]  BIOS-e820: 000000000009e800 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000ce000 - 00000000000d0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 00000000076f0000 (usable)
[4294667.296000]  BIOS-e820: 00000000076f0000 - 00000000076ff000 (ACPI data)
[4294667.296000]  BIOS-e820: 00000000076ff000 - 0000000007700000 (ACPI NVS)
[4294667.296000]  BIOS-e820: 0000000007700000 - 0000000007780000 (usable)
[4294667.296000]  BIOS-e820: 0000000007780000 - 0000000008000000 (reserved)
[4294667.296000]  BIOS-e820: 00000000ffb80000 - 00000000ffc00000 (reserved)
[4294667.296000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 119MB LOWMEM available.
[4294667.296000] On node 0 totalpages: 30592
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:0
[4294667.296000]   DMA32 zone: 0 pages, LIFO batch:0
[4294667.296000]   Normal zone: 26496 pages, LIFO batch:7
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:0
[4294667.296000] DMI present.
[4294667.296000] ACPI: RSDP (v000 HP-MCD                                ) @ 0x000f6190
[4294667.296000] ACPI: RSDT (v001 HP-MCD   RSDT   0x06040000  LTP 0x00000000) @ 0x076f9cf3
[4294667.296000] ACPI: FADT (v001 HP-MCD GF DSDT  0x06040000 PTL  0x00000001) @ 0x076fef8c
[4294667.296000] ACPI: DSDT (v001 HP-MCD GF DSDT  0x06040000 MSFT 0x0100000d) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x1008
[4294667.296000] Allocating PCI resources starting at 10000000 (gap: 08000000:f7b80000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda1 ro quiet splash
[4294667.296000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[4294667.296000] mapped APIC to ffffd000 (0114e000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 512 (order: 9, 8192 bytes)
[4294667.296000] Detected 1130.102 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294669.215000] Dentry cache hash table entries: 16384 (order: 4, 65536 bytes)
[4294669.215000] Inode-cache hash table entries: 8192 (order: 3, 32768 bytes)
[4294669.223000] Memory: 110260k/122368k available (2095k kernel code, 11496k reserved, 591k data, 332k init, 0k highmem)
[4294669.223000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294669.283000] Calibrating delay using timer specific routine.. 2260.48 BogoMIPS (lpj=1130241)
[4294669.283000] Security Framework v1.0.0 initialized
[4294669.283000] SELinux:  Disabled at boot.
[4294669.283000] Mount-cache hash table entries: 512
[4294669.283000] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[4294669.283000] CPU: After vendor identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[4294669.283000] CPU: L1 I cache: 16K, L1 D cache: 16K
[4294669.283000] CPU: L2 cache: 256K
[4294669.283000] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[4294669.283000] mtrr: v2.0 (20020519)
[4294669.283000] Enabling fast FPU save and restore... done.
[4294669.283000] Enabling unmasked SIMD FPU exception support... done.
[4294669.283000] Checking 'hlt' instruction... OK.
[4294669.287000] SMP alternatives: switching to UP code
[4294669.287000] checking if image is initramfs... it is
[4294670.185000] Freeing initrd memory: 6590k freed
[4294670.205000] ACPI: Looking for DSDT ... not found!
[4294670.208000] ACPI: setting ELCR to 0200 (from 0620)
[4294670.215000] CPU0: Intel(R) Celeron(TM) CPU                1133MHz stepping 01
[4294670.215000] SMP motherboard not detected.
[4294670.215000] Local APIC not detected. Using dummy APIC emulation.
[4294670.215000] Brought up 1 CPUs
[4294670.215000] NET: Registered protocol family 16
[4294670.216000] EISA bus registered
[4294670.216000] ACPI: bus type pci registered
[4294670.216000] PCI: PCI BIOS revision 2.10 entry at 0xfd98a, last bus=2
[4294670.216000] PCI: Using configuration type 1
[4294670.217000] ACPI: Subsystem revision 20051216
[4294670.221000] ACPI: Interpreter enabled
[4294670.221000] ACPI: Using PIC for interrupt routing
[4294670.222000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294670.222000] PCI: Probing PCI hardware (bus 00)
[4294670.228000] Boot video device is 0000:00:02.0
[4294670.228000] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[4294670.228000] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[4294670.228000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[4294670.229000] PCI: Transparent bridge - 0000:00:1e.0
[4294670.229000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294670.234000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[4294670.235000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[4294670.236000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[4294670.236000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[4294670.237000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[4294670.237000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[4294670.237000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[4294670.238000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[4294670.238000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[4294670.243000] ACPI: Embedded Controller [EC0] (gpe 28) interrupt mode.
[4294670.244000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294670.244000] pnp: PnP ACPI init
[4294670.250000] pnp: PnP ACPI: found 9 devices
[4294670.250000] PnPBIOS: Disabled by ACPI PNP
[4294670.250000] PCI: Using ACPI for IRQ routing
[4294670.250000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294670.254000] pnp: 00:03: ioport range 0x580-0x587 has been reserved
[4294670.254000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[4294670.254000] PCI: Bus 3, cardbus bridge: 0000:02:04.0
[4294670.254000]   IO window: 00002800-000028ff
[4294670.254000]   IO window: 00002c00-00002cff
[4294670.254000]   PREFETCH window: 10000000-11ffffff
[4294670.254000]   MEM window: 14000000-15ffffff
[4294670.254000] PCI: Bus 7, cardbus bridge: 0000:02:04.1
[4294670.254000]   IO window: 00001400-000014ff
[4294670.254000]   IO window: 00001c00-00001cff
[4294670.254000]   PREFETCH window: 12000000-13ffffff
[4294670.254000]   MEM window: 16000000-17ffffff
[4294670.254000] PCI: Bridge: 0000:00:1e.0
[4294670.254000]   IO window: 2000-2fff
[4294670.254000]   MEM window: e0200000-e02fffff
[4294670.254000]   PREFETCH window: 10000000-13ffffff
[4294670.254000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[4294670.254000] PCI: Enabling device 0000:02:04.0 (0081 -> 0083)
[4294670.254000] **** SET: Misaligned resource pointer: c7669b62 Type 07 Len 0
[4294670.255000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 9
[4294670.255000] PCI: setting IRQ 9 as level-triggered
[4294670.255000] ACPI: PCI Interrupt 0000:02:04.0[A] -> Link [LNKA] -> GSI 9 (level, low) -> IRQ 9
[4294670.255000] PCI: Setting latency timer of device 0000:02:04.0 to 64
[4294670.255000] PCI: Enabling device 0000:02:04.1 (0081 -> 0083)
[4294670.255000] **** SET: Misaligned resource pointer: c7669b62 Type 07 Len 0
[4294670.255000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 9
[4294670.255000] ACPI: PCI Interrupt 0000:02:04.1[B] -> Link [LNKB] -> GSI 9 (level, low) -> IRQ 9
[4294670.255000] PCI: Setting latency timer of device 0000:02:04.1 to 64
[4294670.256000] audit: initializing netlink socket (disabled)
[4294670.256000] audit(1148288709.254:1): initialized
[4294670.256000] VFS: Disk quotas dquot_6.5.1
[4294670.256000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294670.256000] Initializing Cryptographic API
[4294670.256000] io scheduler noop registered
[4294670.256000] io scheduler anticipatory registered
[4294670.256000] io scheduler deadline registered
[4294670.256000] io scheduler cfq registered
[4294670.257000] isapnp: Scanning for PnP cards...
[4294670.613000] isapnp: No Plug & Play device found
[4294670.646000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[4294670.649000] i8042.c: Detected active multiplexing controller, rev 1.1.
[4294670.652000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[4294670.652000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[4294670.652000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[4294670.653000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[4294670.653000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294670.653000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294670.659000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294670.659000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294670.659000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294670.659000] mice: PS/2 mouse device common for all mice
[4294670.661000] EISA: Probing bus 0 at eisa.0
[4294670.661000] Cannot allocate resource for EISA slot 1
[4294670.661000] Cannot allocate resource for EISA slot 2
[4294670.661000] EISA: Detected 0 cards.
[4294670.661000] NET: Registered protocol family 2
[4294670.670000] IP route cache hash table entries: 1024 (order: 0, 4096 bytes)
[4294670.670000] TCP established hash table entries: 4096 (order: 3, 49152 bytes)
[4294670.670000] TCP bind hash table entries: 4096 (order: 3, 49152 bytes)
[4294670.670000] TCP: Hash tables configured (established 4096 bind 4096)
[4294670.670000] TCP reno registered
[4294670.670000] TCP bic registered
[4294670.671000] NET: Registered protocol family 1
[4294670.671000] NET: Registered protocol family 8
[4294670.671000] NET: Registered protocol family 20
[4294670.671000] Using IPI No-Shortcut mode
[4294670.671000] ACPI wakeup devices:
[4294670.671000] ILAN MIN1 USB0 USB1 USB2
[4294670.671000] ACPI: (supports S0 S1 S3 S4 S5)
[4294670.671000] Freeing unused kernel memory: 332k freed
[4294670.800000] vga16fb: initializing
[4294670.800000] vga16fb: mapped to 0xc00a0000
[4294670.921000] Console: switching to colour frame buffer device 80x25
[4294670.921000] fb0: VGA16 VGA frame buffer device
[4294671.880000] input: AT Translated Set 2 keyboard as /class/input/input0
[4294671.898000] input: AT Translated Set 2 keyboard as /class/input/input1
[4294672.082000] Capability LSM initialized
[4294672.146000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[4294672.146000] ACPI: Processor [CPU0] (supports 8 throttling states)
[4294673.184000] ICH3M: IDE controller at PCI slot 0000:00:1f.1
[4294673.184000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[4294673.184000] **** SET: Misaligned resource pointer: c717ab62 Type 07 Len 0
[4294673.185000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 5
[4294673.185000] PCI: setting IRQ 5 as level-triggered
[4294673.185000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[4294673.185000] ICH3M: chipset revision 2
[4294673.185000] ICH3M: not 100% native mode: will probe irqs later
[4294673.185000]     ide0: BM-DMA at 0x1860-0x1867, BIOS settings: hda:DMA, hdb:pio
[4294673.185000]     ide1: BM-DMA at 0x1868-0x186f, BIOS settings: hdc:DMA, hdd:pio
[4294673.185000] Probing IDE interface ide0...
[4294673.449000] hda: HITACHI_DK23DA-20, ATA DISK drive
[4294674.061000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294674.454000] Probing IDE interface ide1...
[4294675.126000] hdc: QSI CD-ROM SCR-242, ATAPI CD/DVD-ROM drive
[4294675.432000] ide1 at 0x170-0x177,0x376 on irq 15
[4294675.445000] hda: max request size: 128KiB
[4294675.461000] hda: 39070080 sectors (20003 MB) w/2048KiB Cache, CHS=38760/16/63, UDMA(100)
[4294675.461000] hda: cache flushes supported
[4294675.462000]  hda: hda1 hda2 < hda5 >
[4294675.509000] hdc: ATAPI 24X CD-ROM drive, 128kB Cache, UDMA(33)
[4294675.509000] Uniform CD-ROM driver Revision: 3.20
[4294675.764000] usbcore: registered new driver usbfs
[4294675.765000] usbcore: registered new driver hub
[4294675.769000] USB Universal Host Controller Interface driver v2.3
[4294675.770000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 9 (level, low) -> IRQ 9
[4294675.770000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[4294675.770000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[4294675.771000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[4294675.771000] uhci_hcd 0000:00:1d.0: irq 9, io base 0x00001800
[4294675.772000] hub 1-0:1.0: USB hub found
[4294675.772000] hub 1-0:1.0: 2 ports detected
[4294675.873000] **** SET: Misaligned resource pointer: c717a0e2 Type 07 Len 0
[4294675.874000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 5
[4294675.874000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[4294675.874000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[4294675.874000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[4294675.874000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[4294675.874000] uhci_hcd 0000:00:1d.1: irq 5, io base 0x00001820
[4294675.875000] hub 2-0:1.0: USB hub found
[4294675.875000] hub 2-0:1.0: 2 ports detected
[4294675.976000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[4294675.976000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[4294675.976000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[4294675.976000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[4294675.976000] uhci_hcd 0000:00:1d.2: irq 5, io base 0x00001840
[4294675.977000] hub 3-0:1.0: USB hub found
[4294675.977000] hub 3-0:1.0: 2 ports detected
[4294676.200000] Attempting manual resume
[4294676.247000] EXT3-fs: mounted filesystem with ordered data mode.
[4294676.250000] kjournald starting.  Commit interval 5 seconds
[4294693.821000] Linux agpgart interface v0.101 (c) Dave Jones
[4294693.825000] agpgart: Detected an Intel 830M Chipset.
[4294693.826000] agpgart: Detected 8060K stolen memory.
[4294693.835000] agpgart: AGP aperture is 128M @ 0xe8000000
[4294694.390000] Real Time Clock Driver v1.12
[4294694.900000] Floppy drive(s): fd0 is 1.44M
[4294694.914000] FDC 0 is a National Semiconductor PC87306
[4294694.946000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294694.955000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294694.988000] hw_random: RNG not detected
[4294695.153000] parport: PnPBIOS parport detected.
[4294695.153000] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,EPP,ECP]
[4294695.616000] ACPI: PCI Interrupt 0000:02:03.0[A] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[4294695.770000] e100: Intel(R) PRO/100 Network Driver, 3.4.14-k4-NAPI
[4294695.770000] e100: Copyright(c) 1999-2005 Intel Corporation
[4294696.083000] Synaptics Touchpad, model: 1, fw: 5.1, id: 0x8f40b1, caps: 0x80471b/0x0
[4294696.123000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[4294696.166000] ts: Compaq touchscreen protocol output
[4294696.597000] ACPI: PCI Interrupt 0000:02:04.0[A] -> Link [LNKA] -> GSI 9 (level, low) -> IRQ 9
[4294696.597000] Yenta: CardBus bridge found at 0000:02:04.0 [103c:0021]
[4294696.597000] Yenta O2: res at 0x94/0xD4: c8/00
[4294696.597000] Yenta O2: enabling read prefetch/write burst
[4294696.719000] Yenta: ISA IRQ mask 0x0c18, PCI irq 9
[4294696.719000] Socket status: 30000006
[4294696.719000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[4294696.719000] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[4294696.719000] cs: IO port probe 0x2000-0x2fff: clean.
[4294696.720000] pcmcia: parent PCI bridge Memory window: 0xe0200000 - 0xe02fffff
[4294696.720000] pcmcia: parent PCI bridge Memory window: 0x10000000 - 0x13ffffff
[4294696.733000] ACPI: PCI Interrupt 0000:02:04.1[B] -> Link [LNKB] -> GSI 9 (level, low) -> IRQ 9
[4294696.733000] Yenta: CardBus bridge found at 0000:02:04.1 [103c:0021]
[4294696.855000] Yenta: ISA IRQ mask 0x0c18, PCI irq 9
[4294696.855000] Socket status: 30000006
[4294696.855000] Yenta: Raising subordinate bus# of parent bus (#02) from #06 to #0a
[4294696.855000] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[4294696.855000] cs: IO port probe 0x2000-0x2fff: clean.
[4294696.856000] pcmcia: parent PCI bridge Memory window: 0xe0200000 - 0xe02fffff
[4294696.856000] pcmcia: parent PCI bridge Memory window: 0x10000000 - 0x13ffffff
[4294696.868000] **** SET: Misaligned resource pointer: c2e69f62 Type 07 Len 0
[4294696.868000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 10
[4294696.868000] PCI: setting IRQ 10 as level-triggered
[4294696.868000] ACPI: PCI Interrupt 0000:02:08.0[A] -> Link [LNKE] -> GSI 10 (level, low) -> IRQ 10
[4294696.892000] e100: eth0: e100_probe: addr 0xe0200000, irq 10, MAC addr 00:02:3F:3B:3B:98
[4294697.624000] cs: IO port probe 0x100-0x3af: clean.
[4294697.625000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[4294697.626000] cs: IO port probe 0x820-0x8ff: clean.
[4294697.627000] cs: IO port probe 0xc00-0xcf7: clean.
[4294697.628000] cs: IO port probe 0xa00-0xaff: clean.
[4294697.629000] cs: IO port probe 0x100-0x3af: clean.
[4294697.631000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[4294697.632000] cs: IO port probe 0x820-0x8ff: clean.
[4294697.632000] cs: IO port probe 0xc00-0xcf7: clean.
[4294697.633000] cs: IO port probe 0xa00-0xaff: clean.
[4294698.048000] lp0: using parport0 (interrupt-driven).
[4294698.161000] Adding 345356k swap on /dev/hda5.  Priority:-1 extents:1 across:345356k
[4294698.238000] NET: Registered protocol family 17
[4294698.355000] EXT3 FS on hda1, internal journal
[4294698.675000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294698.675000] md: bitmap version 4.39
[4294699.649000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294700.543000] hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
[4294700.543000] hdc: packet command error: error=0x50 { LastFailedSense=0x05 }
[4294700.543000] ide: failed opcode was: unknown
[4294700.543000] cdrom: open failed.
[4294702.551000] ACPI: AC Adapter [ACAD] (on-line)
[4294702.555000] ACPI: Battery Slot [BAT1] (battery present)
[4294702.689000] ACPI: Power Button (FF) [PWRF]
[4294702.689000] ACPI: Lid Switch [LID]
[4294702.689000] ACPI: Power Button (CM) [PWRB]
[4294702.689000] ACPI: Sleep Button (CM) [SLPB]
[4294702.867000] ibm_acpi: ec object not found
[4294702.906000] pcc_acpi: loading...
[4294703.072000] ACPI: Video Device [GRFX] (multi-head: yes  rom: no  post: no)
[4294709.919000] [drm] Initialized drm 1.0.1 20051102
[4294709.924000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 9 (level, low) -> IRQ 9
[4294709.926000] [drm] Initialized i915 1.4.0 20060119 on minor 0
[4294709.928000] [drm] Initialized i915 1.4.0 20060119 on minor 1
[4294720.489000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294720.490000] apm: overridden by ACPI.
[4294730.517000] hdc: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
[4294730.517000] hdc: drive_cmd: error=0x04 { AbortedCommand }
[4294730.517000] ide: failed opcode was: 0xec
[4294730.545000] hdc: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
[4294730.545000] hdc: drive_cmd: error=0x04 { AbortedCommand }
[4294730.545000] ide: failed opcode was: 0xec
[4294731.359000] Bluetooth: Core ver 2.8
[4294731.359000] NET: Registered protocol family 31
[4294731.359000] Bluetooth: HCI device and connection manager initialized
[4294731.359000] Bluetooth: HCI socket layer initialized
[4294731.427000] Bluetooth: L2CAP ver 2.8
[4294731.427000] Bluetooth: L2CAP socket layer initialized
[4294731.434000] Bluetooth: RFCOMM socket layer initialized
[4294731.434000] Bluetooth: RFCOMM TTY layer initialized
[4294731.434000] Bluetooth: RFCOMM ver 1.7
[4294743.205000] NET: Registered protocol family 10
[4294743.206000] lo: Disabled Privacy Extensions
[4294743.206000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[4294743.206000] IPv6 over IPv4 tunneling driver

---

### Post by dmizer on 2006-05-22
[QUOTE=Mangani] [snip] [4294730.517000] hdc: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
[4294730.517000] hdc: drive_cmd: error=0x04 { AbortedCommand }
[4294730.517000] ide: failed opcode was: 0xec
[4294730.545000] hdc: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
[4294730.545000] hdc: drive_cmd: error=0x04 { AbortedCommand }
[4294730.545000] ide: failed opcode was: 0xec[/QUOTE]
sure enough.  that bad cdrom drive is what's causing your problem.

if it's a swapout device that you can remove from a bay or something, it would be wise to do so.  otherwise, your only other option for salvage here is to open up the box and physically disconnect the thing.

edit:
actually, is there something specific that makes you say that the drive is bad?  i mean, it could be a function of an elderly computer on a newer kernel.  i searched a bit in google for "ide: failed opcode was: 0xec" and got several hits.

you might want to try knoppix and see if that boots without errors ... some people were having this error while booting in ubuntu, but not in knoppix.  if that's the case, then there may be a fix for this problem.

---

### Post by Mangani on 2006-05-22
I was kind of hoping you wouldn't say that;)
The drive crashes often, and is very picky about CDs. It has been this way for a long time, but it never caused problems with XP. The previous owner was surprised I managed making it read my ubuntu installation-disc at all.
The drive needs to be physically removed, so I'll try the knoppix first ("apt-get knoppix"?).

---

### Post by dmizer on 2006-05-22
no ... knoppix is a full os that runs from a cd.  [www.knopper.net](www.knopper.net)

but since you are sure that the drive is bad, then there may not be any hope.  it's just that knoppix has a better track record of detecting oddball hardware because that's what its design is.  unfortunately knoppix design is to run from a cd only.  you can install it, but installing knoppix to a hdd will bring you more problems than you can imagine.

knoppix is however, a fantastic tool that you should keep around in case of a myriad computer problems.

---

### Post by LorandKA on 2006-05-22
Hello! I Am an absolute newbie, and i'm not assahmed of. Really want to install Ubuntu on my home machine, (at work, it runs fine, on an athlon xp) but I kinda have an old machine: Intel Pentium3 866, 256m ram (thinking on upgrading to 512), riva tnt2 32m + voodoo2 12m, 2x 3com nic's, 20g + 40g drives. Does the latest Ubuntu will run adequate on this machine? also i'm using an usb irDA adapter, with my mobile. Does this kind of hardware will work? I am using my machine mostly for browsing, chatting, multimedia (movies, music). Aslo I have a server, with DHCP/windows ICS. + 80 client LAN, do I will have acces to shared resources? (eg. shared folders on win machines? ) Do I need extra configuration, for it? I told you, i'm a newbie.

---

### Post by dmizer on 2006-05-22
[QUOTE=LorandKA]Hello! I Am an absolute newbie, and i'm not assahmed of. Really want to install Ubuntu on my home machine, (at work, it runs fine, on an athlon xp) but I kinda have an old machine: Intel Pentium3 866, 256m ram (thinking on upgrading to 512), riva tnt2 32m + voodoo2 12m, 2x 3com nic's, 20g + 40g drives. Does the latest Ubuntu will run adequate on this machine? also i'm using an usb irDA adapter, with my mobile. Does this kind of hardware will work? I am using my machine mostly for browsing, chatting, multimedia (movies, music). Aslo I have a server, with DHCP/windows ICS. + 80 client LAN, do I will have acces to shared resources? (eg. shared folders on win machines? ) Do I need extra configuration, for it? I told you, i'm a newbie.[/QUOTE]
your computer should have no problem with it.  it's about the same as what i'm using ... speed wise.  not sure about the rest of your hardware though.

as for the rest of your concerns, what you've posted here isn't really related to the rest of the thread, you might consider starting a new topic for yourself regarding the conserns you have in installing ubuntu.

---

### Post by LorandKA on 2006-05-22
[QUOTE=dmizer]your computer should have no problem with it.  it's about the same as what i'm using ... speed wise.  not sure about the rest of your hardware though.[/QUOTE]

thank you! if you think that, I will have no problem, I will try it.

---

### Post by Mangani on 2006-05-22
[QUOTE=dmizer]
but since you are sure that the drive is bad, then there may not be any hope.  [/QUOTE]

And there is no way of disabling the CD-rom by terminal or something? I'm pretty sure I'll break something if I go in there, I usually do.

---

### Post by dmizer on 2006-05-22
you *might* be able to disable it by commenting it out in fstab ... 
```
sudo nano /etc/fstab
```
then put a pound (#) in front of the line that has your cdrom in it.  mine looks like this:
```
/dev/hdb        /media/cdrom0   udf,iso9660 user,unhide,noauto     0       0
```
then ctrl x > type the letter y > and enter.  then reboot.  but i really don't know if that will completely disable the cdrom or not, just keep it from mounting, which may or may not be just as effective.

---

### Post by supsup on 2006-05-24
Check this link, maybe it is laptop-mode related problem 
[http://www.xs4all.nl/~bsamwel/laptop_mode/tools/faq.html](http://www.xs4all.nl/~bsamwel/laptop_mode/tools/faq.html)

---

### Post by Mangani on 2006-05-24
dmizer - just checking in to fill you up on my progress, or rather the lack of.
I tried the fstab, but with no effect, as you suspected. 

Sort of gave up on coffee and drums, and tried the SuSE. Spent 2 whole days messing with network installation, before I succeeded. But - still slow, minutes are ticking while it loads OOo.

supsup - thanks for the link. The laptop-mode seems to be about saving power, but I'm never on batterypower (I have barely 30 minutes run-time), and don't think it can be of any help to me.

---

### Post by dmizer on 2006-05-26
well, if SuSE does it, and "coffee and drums" ;) does it ... as i suggested, you could try knoppix and mepis ... both of which do not require installs.

anyone around know how to disable a hardware device on boot?

you MIGHT be able to accomplish something via your bios config.  that's the best i can do by pulling things from where the light don't shine.

---

### Post by dmizer on 2006-05-26
took some time out with google ... you might be successful in simply disabling dma (direct memory access) for your cdrom drive to free up the memory your bad cdrom has cornered.

edit fstab as previously shown, and add "-d0" like so:
```
dev/hdb        /media/cdrom0   udf,iso9660 user,unhide,noauto,[COLOR="Red"]-d0[/COLOR]     0       0
```

edit:
found a better way ...

1. Backup the file we'll be editing:
```
sudo cp /etc/hdparm.conf /etc/hdparm.conf.backup
```
2. Open it for editing
```
sudo gedit /etc/hdparm.conf
```
3. Add an entry like this (assuming /dev/hdc is the device you're interested in)
```
/dev/hdc { dma = off }
```
4. Save it and reboot.

above was shamelessly stolen from [this]("http://ubuntuforums.org/showthread.php?t=176436&highlight=disable+dma") thread.

---

### Post by Mangani on 2006-05-26
Thanks dmizer, I think I'll install ubuntu and give it another go with these dma commands. I actually succeeded increasing suse's speed considerably by enabling dma in yast (both HDD and CD-rom, the CD-rom wouldn't allow turning DMA off), but it still barely handles more than one open window at the same time.
If ubuntu responds a little better than suse to dma, I think I'll settle with it. If not, I'll read up on knoppix and metis.
Incidentally, a local computer-salesman made me aware that my XE3 didn't have 256MB of ram, but rather 128. :) Guess that explains a bit too.

---

### Post by dmizer on 2006-05-26
[QUOTE=Mangani]Incidentally, a local computer-salesman made me aware that my XE3 didn't have 256MB of ram, but rather 128. :) Guess that explains a bit too.[/QUOTE]
it still should be more than enough computer to run ubuntu.

lol, knoppix and mepis run from the cd rather than from the hdd, so they would merely be a test to see if your cdrom is bad or not.  but i'm pretty sure it's been decided that it is so ...

if you were able to disable your cdrom somehow without pulling the machine apart, that would be idea ... but i've been searching for a while, and i haven't found anything suggesting that it's possible.

---

### Post by Mangani on 2006-05-27
Hm,
apparently I never installed xubuntu properly, and was actually working in ubuntu the whole time. Now I installed the server from the boot CD-rom, and went to xubuntu from there. Much, much better. 
I followed your recipe for disabling cd-rom dma, dmizer, and it seemed to speed things up additionally (altered "gedit" to "mousepad").
Now all I have to do is install the open office word processor (if it won't slow things down too much), and find a way to play the odd mp3 file.

---

### Post by Mangani on 2007-03-24
Turns out - it's still too slow. In and out of storage, installed edubuntu, and put it my son's room. But he is about as patient as me, and prefers the old desk-top with WinNT.
So, I finally mustered the courage to go in, and I succesfully removed the CD-rom. But I can't say I notice any difference speedwise.

Time to throw in the towel? Or wipe my forehead with it, and try again?

---

### Post by ZeroWing on 2007-03-24
Wrong topic...

---

### Post by Mangani on 2007-03-24
Oh...what have I missed?

---

### Post by cowlip on 2007-03-24
[http://beuno.com.ar/?p=4](http://beuno.com.ar/?p=4)

Have you tried doing this in edgy or feisty?  What about using Abiword + Gnumeric or KOffice instead of OpenOffice?

> Performance tip for Edgy and Feisty users

I&#8217;ve been following a thread in the forums that refers to a very simple change in Ubuntu that actually is improving the responsiveness of many Edgy and Feisty users (including me).
I have no idea why this is, or if it has any side effects, to be careful.

Edit your &#8220;/etc/hosts&#8221; file:
$ sudo gedit /etc/hosts

You should see something like this:

127.0.0.1 localhost
127.0.1.1 martin-laptop
(and if your in Feisty, some lines about IPV6

Now, add the following:

127.0.0.1 localhost martin-laptop
127.0.1.1 martin-laptop
(Replace &#8220;martin-laptop&#8221; with your hostname)

Save. Should work instantly, or sometimes on reboot.

The forum thread is: [http://ubuntuforums.org/showthread.php?t=388765](http://ubuntuforums.org/showthread.php?t=388765).


---

### Post by Mangani on 2007-03-25
Thanks, cowlip.Tried it, and I think things have speeded up a little bit.
But it is still rather syrupy. I suspect it is a hardware problem, and that Dmizer was correct in blaming the cd-rom. Do I need to free up the memory after removing the unit? Or somehow reinstall without the cd-rom in place?

---

