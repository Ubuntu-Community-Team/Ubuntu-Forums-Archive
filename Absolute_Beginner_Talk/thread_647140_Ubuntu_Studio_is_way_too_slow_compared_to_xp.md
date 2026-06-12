---
title: "Ubuntu Studio is way too slow compared to xp"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by mark558 on 2007-12-22
Hi,
I just downloaded and installed Ubuntu Studio on my older computer for the sole purpose of having a media editing machine. The machine is an older Pentium 4, an intel motherboard, and an Nvidia MX440 AGP graphics card. When I first booted up, Ubuntu Studio told me that I could install the proprietary nvidia drivers, which I did. When I restarted it, gnome said that it could not fully start up because of a problem, however, when I restarted the computer again, gnome launched just fine. 
On windows xp, navigating around the operating system and clicking on things happened instantly. On ubuntu studio, I can count the time it takes to do mundane things. Also, doing anything in a video editing program immediately crashes the computer.
This is probably only one reason it is slow, but in my system monitor, its says that 90% of the cpu is being used without doing anything. In the processes list, none show up as using that much. 
If anyone has any suggestions on how to fix this, I would greatly appreciate it! Keep in mind that I have no real experience with linux :).

Thanks!

---

### Post by Shazaam on 2007-12-22
For a better clue as to whats running install htop from the repo's. Once it's installed just type htop into terminal. Use the down arrow on your keyboard to see more once it opens.

---

### Post by tgalati4 on 2007-12-22
Your system could be indexing.  With a new install, there are several databases that need to be created--and these are usually created right way, slowing your system down.  Don't kill the processes unless you think they are hung or have good reason to otherwise.  Once the indices are created, your system should speed up.

Also, a real-time kernel will have a laggy mouse and keyboard.  It's designed for real-time recording so the user is low-priority.  Top priority goes to capturing data to disk so you don't get skips in your recording.

---

### Post by mark558 on 2007-12-22
Alright... after installing htop I traced the cpu leak to my external sound card. It is now running much better after removing it. I'll have to run out and get a new soundcard (if anyone knows a good soundcard that works well in ubuntu, I'd love to know). Also, I am still getting that weird gnome error message:
"There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in."

Also, before I get the ubuntu logon screen, it quickly flashes a message saying that the cpu sent back a weird power message and that it is "dazed and confused but will continue on anyways"... I'll look in my bios to see if I have any power saving options set for the cpu, but if anyone knows what is causing that message, I would love to know what the problem is...

Thanks so much!!!

---

### Post by nowshining on 2007-12-22
maybe ur harddrive is going out, ur power supply is too old, computer needs more power, cpu dying......

---

### Post by tgalati4 on 2007-12-22
M-Audio Delta 66 cards work well under Linux.  Those Dazed and Confused messages can be serious because it means that some unexpected hardware response was received to a simple poke.

Clean out the dust bunnies in your machine, reset your RAM and run memtest.  You need ~30 passes to get high confidence in your RAM before you move on to other reliability issues.

---

### Post by mark558 on 2007-12-22
Alright, I ran memtest for 30 passes and there were no errors. What should I do next?

Thanks

---

### Post by fatality_uk on 2007-12-22
> **mark558 said:**
> Alright, I ran memtest for 30 passes and there were no errors. What should I do next? Thanks

As tgalati4 said. I recommend a COMPLETE clean out of the system. Disconnect every thing, and DISCHARGE any staic befroe trying this. If your happy to do it, open the case, take out the RAM, use a non solvent cleaner on the contacts. Also get an air duster can, just a few £'s from a local PC store. Spray around the power supply, remove the dirt in there. The power may be fluctuating which can be a problem. In addition, reset your BIOS! I know it sounds drastic but sometimes people forget they enabled auto overclocking 6 months ago to play that new game :D

---

### Post by tgalati4 on 2007-12-23
Follow fatality's recommendations for a clean-out.  Dust can get in between the I/O and graphics controller chips and cause bus problems.  Reseating power and ribbon cables helps as well.

I'm glad that your memory passed.  We can now move on to other things.

Next time you boot into Ubuntu, press Alt-F1 and carefully watch the messages that scroll by.  If you get a successful boot, then immediately open a terminal and scroll through the following:

>dmesg | more

Make a note of error messages and paste them in your next post.

As you work on your machine, from time to time, run the following:

>dmesg | tail -25

To look for new error messages.  Bad keyboard presses, hard disk read errors, USB overcurrent, and other messages will show up.  

If you have a reliable system, then dmesg will only show the last boot messages (typically bluetooth stuff).  

Additional error messages can be found in /var/log.  Look through the files to get a feel what's in there.

You want bullet-proof hardware before you get into serious editing.

If you are running kino for video editing, then try running in a terminal:

>kino --debug

and watch for errors during your edit session.  If it crashes, then you will usually get some sort of crash dump left on the terminal from which you ran it.

Also, how much RAM do you have?  Do you have a swap disk set up that matches or exceeds your RAM.  Lots of RAM and a generous swap disk are needed for serious editing.

---

### Post by mark558 on 2007-12-23
Ok... I first replaced the power supply in the computer with a spare one that I had lying around - I'm not sure of the quality of it, but it didn't seem to do anything for that weird cpu error message. Whats weird is that there is a connector on the power supply that was on the power supply originally in the computer and the one that I just put in that is used by the motherboard, but I haven't seen it on any of the new modern power supplies -> [http://www.pctechguide.com/images/tutorials/Pentium4/Power3.jpg](http://www.pctechguide.com/images/tutorials/Pentium4/Power3.jpg)

I'll post the entire dmesg if I can because there were some messages about the pci bus along with the cpu error

Thanks!

---

### Post by mark558 on 2007-12-23
[    0.000000] Linux version 2.6.22-14-rt (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) 
(Ubuntu 4.1.2-16ubuntu2)) #1 SMP PREEMPT RT Mon Oct 15 01:05:51 GMT 2007 (Unofficial) 
[    0.000000] BIOS-provided physical RAM map: 
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable) 
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved) 
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved) 
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000ffc0000 (usable) 
[    0.000000]  BIOS-e820: 000000000ffc0000 - 000000000fff8000 (ACPI data) 
[    0.000000]  BIOS-e820: 000000000fff8000 - 0000000010000000 (ACPI NVS) 
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved) 
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved) 
[    0.000000]  BIOS-e820: 00000000ffb80000 - 00000000ffc00000 (reserved) 
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved) 
[    0.000000] 0MB HIGHMEM available. 
[    0.000000] 255MB LOWMEM available. 
[    0.000000] Entering add_active_range(0, 0, 65472) 0 entries of 256 used 
[    0.000000] Zone PFN ranges: 
[    0.000000]   DMA             0 ->     4096 
[    0.000000]   Normal       4096 ->    65472 
[    0.000000]   HighMem     65472 ->    65472 
[    0.000000] early_node_map[1] active PFN ranges 
[    0.000000]     0:        0 ->    65472 
[    0.000000] On node 0 totalpages: 65472 
[    0.000000]   DMA zone: 56 pages used for memmap 
[    0.000000]   DMA zone: 0 pages reserved 
[    0.000000]   DMA zone: 4040 pages, LIFO batch:0 
[    0.000000]   Normal zone: 839 pages used for memmap 
[    0.000000]   Normal zone: 60537 pages, LIFO batch:15 
[    0.000000]   HighMem zone: 0 pages used for memmap 
[    0.000000] DMI 2.3 present. 
[    0.000000] ACPI: RSDP signature @ 0xC00FF980 checksum 0 
[    0.000000] ACPI: RSDP 000FF980, 0014 (r0 AMI   ) 
[    0.000000] ACPI: RSDT 0FFF0000, 0028 (r1 D850GB G285010A 20010718 MSFT     1011) 
[    0.000000] ACPI: FACP 0FFF1000, 0074 (r1 D850GB GB85010A 20010718 MSFT     1011) 
[    0.000000] ACPI: DSDT 0FFE0000, 2E5B (r1 D850GB GB85010A        2 MSFT  100000B) 
[    0.000000] ACPI: FACS 0FFF8000, 0040 
[    0.000000] ACPI: PM-Timer IO Port: 0x408 
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 10000000:eec00000) 
[    0.000000] Real-Time Preemption Support (C) 2004-2007 Ingo Molnar 
[    0.000000] Built 1 zonelists.  Total pages: 64577 
[    0.000000] Kernel command line: root=UUID=182ff63f-237e-43ae-9fa5-45a764722d29 ro quiet splash 
[    0.000000] Found and enabled local APIC! 
[    0.000000] mapped APIC to ffffd000 (fee00000) 
[    0.000000] Enabling fast FPU save and restore... done. 
[    0.000000] Enabling unmasked SIMD FPU exception support... done. 
[    0.000000] Initializing CPU#0 
[    0.000000] WARNING: experimental RCU implementation. 
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes) 
[    0.000000] Detected 1521.266 MHz processor. 
[   17.779813] Console: colour VGA+ 80x25 
[   17.779990] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes) 
[   17.780172] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes) 
[   17.792329] Memory: 246288k/261888k available (2056k kernel code, 14940k reserved, 970k data, 364k init, 0k highmem) 
[   17.792345] virtual kernel memory layout: 
[   17.792347]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB) 
[   17.792349]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB) 
[   17.792351]     vmalloc : 0xd0800000 - 0xff7fe000   ( 751 MB) 
[   17.792353]     lowmem  : 0xc0000000 - 0xcffc0000   ( 255 MB) 
[   17.792356]       .init : 0xc03fb000 - 0xc0456000   ( 364 kB) 
[   17.792359]       .data : 0xc03022ec - 0xc03f4b44   ( 970 kB) 
[   17.792361]       .text : 0xc0100000 - 0xc03022ec   (2056 kB) 
[   17.792367] Checking if this processor honours the WP bit even in supervisor mode... Ok. 
[   17.851616] Calibrating delay using timer specific routine.. 2992.87 BogoMIPS (lpj=1496436) 
[   17.851686] Security Framework v1.0.0 initialized 
[   17.851696] SELinux:  Disabled at boot. 
[   17.851728] Mount-cache hash table entries: 512 
[   17.852009] CPU: After generic identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000 
[   17.852031] CPU: Trace cache: 12K uops, L1 D cache: 8K 
[   17.852037] CPU: L2 cache: 256K 
[   17.852041] CPU: Hyper-Threading is disabled 
[   17.852045] CPU: After all inits, caps: 3febfbff 00000000 00000000 0000b080 00000000 00000000 00000000 
[   17.852065] Compat vDSO mapped to ffffe000. 
[   17.852088] Checking 'hlt' instruction... OK. 
[   17.855786] SMP alternatives: switching to UP code 
[   17.856083] Freeing SMP alternatives: 9k freed 
[   17.856595] Early unpacking initramfs... done 
[   18.426616] ACPI: Core revision 20070126 
[   18.426720] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found. 
[   18.428904] ACPI: setting ELCR to 0200 (from 0e28) 
[   18.429689] CPU0: Intel(R) Pentium(R) 4 CPU 1500MHz stepping 07 
[   18.429699] SMP motherboard not detected. 
[   18.430727] Uhhuh. NMI received for unknown reason 2d on CPU 0. 
[   18.430785] Do you have a strange power saving mode enabled? 
[   18.430836] Dazed and confused, but trying to continue 
[   18.530423] Brought up 1 CPUs 
[   18.530651] Booting paravirtualized kernel on bare hardware 
[   18.530788] Time:  2:39:16  Date: 11/24/107 
[   18.530832] NET: Registered protocol family 16 
[   18.531039] EISA bus registered 
[   18.531079] ACPI: bus type pci registered 
[   18.531286] PCI: PCI BIOS revision 2.10 entry at 0xfda95, last bus=2 
[   18.531290] PCI: Using configuration type 1 
[   18.531294] Setting up standard PCI resources 
[   18.536172] ACPI: EC: Look up EC in DSDT 
[   18.541827] ACPI: Interpreter enabled 
[   18.541836] ACPI: (supports S0 S1 S4 S5) 
[   18.541867] ACPI: Using PIC for interrupt routing 
[   18.551533] ACPI: PCI Root Bridge [PCI0] (0000:00) 
[   18.551567] PCI: Probing PCI hardware (bus 00) 
[   18.551912] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO 
[   18.551920] PCI quirk: region 0500-053f claimed by ICH4 GPIO 
[   18.552635] PCI: Transparent bridge - 0000:00:1e.0 
[   18.552691] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT] 
[   18.552854] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT] 
[   18.555184] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15) 
[   18.555394] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15) 
[   18.555560] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled. 
[   18.555729] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 14 15) 
[   18.555883] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled. 
[   18.556040] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled. 
[   18.556197] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 6 7 9 10 11 12 14 15) 
[   18.556387] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 12 14 15) 
[   18.556654] ACPI: Power Resource [FDDP] (off) 
[   18.556705] ACPI: Power Resource [URP1] (off) 
[   18.556754] ACPI: Power Resource [URP2] (off) 
[   18.556804] ACPI: Power Resource [LPTP] (off) 
[   18.556829] Linux Plug and Play Support v0.97 (c) Adam Belay 
[   18.556852] pnp: PnP ACPI init 
[   18.556880] ACPI: bus type pnp registered 
[   18.561729] pnp: PnP ACPI: found 12 devices 
[   18.561736] ACPI: ACPI bus type pnp unregistered 
[   18.561744] PnPBIOS: Disabled by ACPI PNP 
[   18.561863] PCI: Using ACPI for IRQ routing 
[   18.561868] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report 
[   18.565324] NET: Registered protocol family 8 
[   18.565329] NET: Registered protocol family 20 
[   18.565538] pnp: 00:0b: iomem range 0x0-0x9ffff could not be reserved 
[   18.565546] pnp: 00:0b: iomem range 0xe0000-0xfffff could not be reserved 
[   18.565551] pnp: 00:0b: iomem range 0x100000-0xfffffff could not be reserved 
[   18.565556] pnp: 00:0b: iomem range 0x0-0x0 could not be reserved 
[   18.595941] PCI: Bridge: 0000:00:01.0 
[   18.595946]   IO window: disabled. 
[   18.595954]   MEM window: fc900000-fe9fffff 
[   18.595960]   PREFETCH window: e4500000-f46fffff 
[   18.595970] PCI: Bridge: 0000:00:1e.0 
[   18.595975]   IO window: d000-dfff 
[   18.595983]   MEM window: fea00000-feafffff 
[   18.595990]   PREFETCH window: f4700000-f47fffff 
[   18.596014] PCI: Setting latency timer of device 0000:00:1e.0 to 64 
[   18.596062] NET: Registered protocol family 2 
[   18.601524] IP route cache hash table entries: 2048 (order: 1, 8192 bytes) 
[   18.601615] TCP established hash table entries: 8192 (order: 6, 360448 bytes) 
[   18.602010] TCP bind hash table entries: 8192 (order: 6, 294912 bytes) 
[   18.602409] TCP: Hash tables configured (established 8192 bind 8192) 
[   18.602415] TCP reno registered 
[   18.604645] checking if image is initramfs... it is 
[   19.729654] Freeing initrd memory: 7147k freed 
[   19.730373] audit: initializing netlink socket (disabled) 
[   19.730397] audit(1198463956.685:1): initialized 
[   19.730743] VFS: Disk quotas dquot_6.5.1 
[   19.730761] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes) 
[   19.730845] io scheduler noop registered 
[   19.730850] io scheduler anticipatory registered 
[   19.730853] io scheduler deadline registered 
[   19.730874] io scheduler cfq registered (default) 
[   19.730939] Boot video device is 0000:01:00.0 
[   19.732018] isapnp: Scanning for PnP cards... 
[   20.086301] isapnp: No Plug & Play device found 
[   20.196965] Real Time Clock Driver v1.12ac 
[   20.197213] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled 
[   20.197349] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A 
[   20.199709] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A 
[   20.201771] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize 
[   20.202107] input: Macintosh mouse button emulation as /class/input/input0 
[   20.202333] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12 
[   20.205240] serio: i8042 KBD port at 0x60,0x64 irq 1 
[   20.205384] serio: i8042 AUX port at 0x60,0x64 irq 12 
[   20.205732] mice: PS/2 mouse device common for all mice 
[   20.206050] EISA: Probing bus 0 at eisa.0 
[   20.206129] EISA: Detected 0 cards. 
[   20.206263] TCP cubic registered 
[   20.206283] NET: Registered protocol family 1 
[   20.206417] Testing NMI watchdog ... <6>input: AT Translated Set 2 keyboard as /class/input/input1 
[   20.305016] CPU#0: NMI appears to be stuck (2->2)! 
[   20.305022] Using IPI No-Shortcut mode 
[   20.305307]   Magic number: 3:183:663 
[   20.305426]   hash matches device ptyee 
[   20.306089] Freeing unused kernel memory: 364k freed 
[   21.766936] AppArmor: AppArmor initialized<5>audit(1198463958.685:2):  type=1505 info="AppArmor initialized" pid=1134 
[   21.780935] fuse init (API version 7.8) 
[   21.793535] Failure registering capabilities with primary security module. 
[   23.433236] SCSI subsystem initialized 
[   23.490703] usbcore: registered new interface driver usbfs 
[   23.493063] usbcore: registered new interface driver hub 
[   23.502517] usbcore: registered new device driver usb 
[   23.511543] Floppy drive(s): fd0 is 1.44M 
[   23.530731] FDC 0 is a post-1991 82077 
[   23.591078] libata version 2.21 loaded. 
[   23.597143] Linux Tulip driver version 1.1.15 (Feb 27, 2007) 
[   23.598862] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 3 
[   23.598871] PCI: setting IRQ 3 as level-triggered 
[   23.598876] ACPI: PCI Interrupt 0000:02:0a.0[A] -> Link [LNKG] -> GSI 3 (level, low) -> IRQ 3 
[   23.600490] USB Universal Host Controller Interface driver v3.0 
[   23.605201] tulip0:  MII transceiver #1 config 3000 status 786d advertising 01e1. 
[   23.616218] eth0: ADMtek Comet rev 17 at Port 0xd800, 00:50:BF:1E:BB:82, IRQ 3. 
[   23.617276] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 5 
[   23.617284] PCI: setting IRQ 5 as level-triggered 
[   23.617290] ACPI: PCI Interrupt 0000:00:1f.2[D] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5 
[   23.617308] PCI: Setting latency timer of device 0000:00:1f.2 to 64 
[   23.617314] uhci_hcd 0000:00:1f.2: UHCI Host Controller 
[   23.617528] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1 
[   23.619215] uhci_hcd 0000:00:1f.2: irq 5, io base 0x0000ef40 
[   23.619452] usb usb1: configuration #1 chosen from 1 choice 
[   23.619506] hub 1-0:1.0: USB hub found 
[   23.619521] hub 1-0:1.0: 2 ports detected 
[   23.728609] ata_piix 0000:00:1f.1: version 2.11 
[   23.728679] PCI: Setting latency timer of device 0000:00:1f.1 to 64 
[   23.728914] scsi0 : ata_piix 
[   23.729444] scsi1 : ata_piix 
[   23.730016] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14 
[   23.730024] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15 
[   23.896362] ata1.01: ATA-7: Maxtor 6Y060L0, YAR41BW0, max UDMA/133 
[   23.896370] ata1.01: 120103200 sectors, multi 16: LBA 
[   23.902359] ata1.01: configured for UDMA/100 
[   23.925966] usb 1-2: new full speed USB device using uhci_hcd and address 2 
[   24.236562] usb 1-2: configuration #1 chosen from 1 choice 
[   24.239432] hub 1-2:1.0: USB hub found 
[   24.242344] hub 1-2:1.0: 4 ports detected 
[   24.393300] ata2.00: ATAPI: CD-ROM CCD-52X6D, YSQ4, max UDMA/33 
[   24.393312] ata2.01: ATAPI: TSSTcorpCD/DVDW SH-W162C, TS10, max UDMA/33 
[   24.526314] usb 1-2.1: new low speed USB device using uhci_hcd and address 3 
[   24.547316] ata2.00: configured for UDMA/33 
[   24.656175] usb 1-2.1: configuration #1 chosen from 1 choice 
[   24.739175] ata2.01: configured for UDMA/33 
[   24.739389] scsi 0:0:1:0: Direct-Access     ATA      Maxtor 6Y060L0   YAR4 PQ: 0 ANSI: 5 
[   24.740602] scsi 1:0:0:0: CD-ROM            CD-ROM   CCD-52X6D        YSQ4 PQ: 0 ANSI: 5 
[   24.742426] scsi 1:0:1:0: CD-ROM            TSSTcorp CD/DVDW SH-W162C TS10 PQ: 0 ANSI: 5 
[   24.743605] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 9 
[   24.743613] PCI: setting IRQ 9 as level-triggered 
[   24.743618] ACPI: PCI Interrupt 0000:00:1f.4[C] -> Link [LNKH] -> GSI 9 (level, low) -> IRQ 9 
[   24.743637] PCI: Setting latency timer of device 0000:00:1f.4 to 64 
[   24.743643] uhci_hcd 0000:00:1f.4: UHCI Host Controller 
[   24.743964] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 2 
[   24.744004] uhci_hcd 0000:00:1f.4: irq 9, io base 0x0000ef80 
[   24.744221] usb usb2: configuration #1 chosen from 1 choice 
[   24.744272] hub 2-0:1.0: USB hub found 
[   24.744288] hub 2-0:1.0: 2 ports detected 
[   24.837824] usb 1-2.3: new low speed USB device using uhci_hcd and address 4 
[   24.945960] usb 1-2.3: config 1 interface 1 altsetting 0 endpoint 0x2 has an invalid bInterval 0, changing to 32 
[   24.959978] sd 0:0:1:0: [sda] 120103200 512-byte hardware sectors (61493 MB) 
[   24.960007] sd 0:0:1:0: [sda] Write Protect is off 
[   24.960012] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00 
[   24.961929] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[   24.963927] sd 0:0:1:0: [sda] 120103200 512-byte hardware sectors (61493 MB) 
[   24.963962] sd 0:0:1:0: [sda] Write Protect is off 
[   24.963967] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00 
[   24.964003] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[   24.964011]  sda:<6>usb 1-2.3: configuration #1 chosen from 1 choice 
[   24.981032]  sda1 sda2 < sda5 > 
[   25.002600] sd 0:0:1:0: [sda] Attached SCSI disk 
[   25.020029] sr0: scsi3-mmc drive: 52x/52x cd/rw xa/form2 cdda tray 
[   25.020039] Uniform CD-ROM driver Revision: 3.20 
[   25.020137] sr 1:0:0:0: Attached scsi CD-ROM sr0 
[   25.041969] sr1: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray 
[   25.042064] sr 1:0:1:0: Attached scsi CD-ROM sr1 
[   25.049042] usbcore: registered new interface driver hiddev 
[   25.065046] input: Logitech Logitech USB Keyboard as /class/input/input2 
[   25.065070] input: USB HID v1.10 Keyboard [Logitech Logitech USB Keyboard] on usb-0000:00:1f.2-2.1 
[   25.085088] sd 0:0:1:0: Attached scsi generic sg0 type 0 
[   25.085125] sr 1:0:0:0: Attached scsi generic sg1 type 5 
[   25.085164] sr 1:0:1:0: Attached scsi generic sg2 type 5 
[   25.104290] input: Logitech Logitech USB Keyboard as /class/input/input3 
[   25.104345] input: USB HID v1.10 Mouse [Logitech Logitech USB Keyboard] on usb-0000:00:1f.2-2.1 
[   25.127858] input: No brand HA2 1.0 as /class/input/input4 
[   25.127880] input: USB HID v1.10 Keyboard [No brand HA2 1.0] on usb-0000:00:1f.2-2.3 
[   25.136731] /build/buildd/linux-source-2.6.22-2.6.22/debian/build/custom-source-rt/drivers/hid/usbhid/hid-core.c: coul 
dn't find an input interrupt endpoint 
[   25.136772] usbcore: registered new interface driver usbhid 
[   25.136779] /build/buildd/linux-source-2.6.22-2.6.22/debian/build/custom-source-rt/drivers/hid/usbhid/hid-core.c: v2.6 
:USB HID core driver 
[   25.556997] Attempting manual resume 
[   25.557004] swsusp: Resume From Partition 8:5 
[   25.557007] PM: Checking swsusp image. 
[   25.557270] PM: Resume from disk failed. 
[   25.597035] kjournald starting.  Commit interval 5 seconds 
[   25.597059] EXT3-fs: mounted filesystem with ordered data mode. 
[   34.577516] NET: Registered protocol family 17 
[   35.851689] 0000:02:0a.0: tulip_stop_rxtx() failed (CSR5 0xfc06c012 CSR6 0xff970115) 
[   35.851705] eth0: Setting full-duplex based on MII#1 link partner capability of cde1. 
[   35.853117] 0000:02:0a.0: tulip_stop_rxtx() failed (CSR5 0xfc06c012 CSR6 0xff970115) 
[   35.985731] input: PC Speaker as /class/input/input5 
[   36.533025] iTCO_vendor_support: vendor-support=0 
[   36.549141] Linux agpgart interface v0.102 (c) Dave Jones 
[   36.578201] pci_hotplug: PCI Hot Plug PCI Core version: 0.5 
[   36.600528] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007) 
[   36.600689] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware 
[   36.600701] iTCO_wdt: No card detected 
[   36.604140] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4 
[   36.610686] agpgart: Detected an Intel i850 Chipset. 
[   36.670948] agpgart: AGP aperture is 64M @ 0xf8000000 
[   36.741991] intel_rng: Firmware space is locked read-only. <4>intel_rng: If you can't or 
[   36.741997]  don't want to <4>intel_rng: disable this in firmware setup, and <4>intel_rng: if 
[   36.742001]  you are certain that your <4>intel_rng: system has a functional 
[   36.742004]  RNG, try<4>intel_rng: using the 'no_fwh_detect' option. 
[   37.499714] input: ImPS/2 Logitech Wheel Mouse as /class/input/input6 
[   37.949748] usbcore: registered new interface driver xpad 
[   37.949757] /build/buildd/linux-source-2.6.22-2.6.22/debian/build/custom-source-rt/drivers/input/joystick/xpad.c: driv 
er for Xbox controllers v0.1.6 
[   38.004677] parport_pc 00:09: reported by Plug and Play ACPI 
[   38.004714] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP] 
[   38.186400] nvidia: module license 'NVIDIA' taints kernel. 
[   38.529789] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11 
[   38.529798] PCI: setting IRQ 11 as level-triggered 
[   38.529804] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11 
[   38.530158] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9639  Mon Apr 16 20:20:06 PDT 2007 
[   39.043084] loop: module loaded 
[   39.085979] lp0: using parport0 (interrupt-driven). 
[   39.212444] Adding 746980k swap on /dev/sda5.  Priority:-1 extents:1 across:746980k 
[   39.497155] EXT3 FS on sda1, internal journal 
[   40.029649] NET: Registered protocol family 10 
[   40.029784] lo: Disabled Privacy Extensions 
[   41.226229] input: Power Button (FF) as /class/input/input7 
[   41.226266] ACPI: Power Button (FF) [PWRF] 
[   41.229166] input: Sleep Button (CM) as /class/input/input8 
[   41.229664] ACPI: Sleep Button (CM) [SBTN] 
[   41.452624] No dock devices found. 
[   43.071447] ppdev: user-space parallel port driver 
[   43.251363] audit(1198463981.168:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name=" 
/dev/tty" pid=4614 profile="/usr/sbin/cupsd" 
[   43.385316] apm: BIOS version 1.2 Flags 0x0b (Driver version 1.16ac) 
[   43.385326] apm: overridden by ACPI. 
[   43.714307] Failure registering capabilities with primary security module. 
[   46.138054] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0. 
[   46.138084] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode 
[   46.138115] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode

---

### Post by tgalati4 on 2007-12-23
The only strange error that I see:

[ 18.429689] CPU0: Intel(R) Pentium(R) 4 CPU 1500MHz stepping 07
[ 18.429699] SMP motherboard not detected.
[ 18.430727] Uhhuh. NMI received for unknown reason 2d on CPU 0.
[ 18.430785] Do you have a strange power saving mode enabled?
[ 18.430836] Dazed and confused, but trying to continue
[ 18.530423] Brought up 1 CPUs 

NMI is a non-maskable interrupt.  Basically an exception code that the operating system doesn't recognize.  Usually nmi's occur when you have a RAM error.  But you ruled that out with memtest.

Look in your BIOS and turn off all powersaving features.  The P4 processor runs full bore all the time so perhaps the kernel got confused thinking it was a speed-step processor.

Video editing on a 1.5 GHz P4 is painful.  3 GHz dual processor is closer to what you need to keep from pulling your hair out.

Of course if Windows works better then use it.  That's the purpose of dual-boot.

The realtime kernel is helpful for realtime audio and video recording to harddisk.  It's less helpful for human interaction with a program.  Only testing will tell what works for you.

Give Dynebolic a spin (dynebolic.org).  It's a Live CD that is slimmed down for single-purpose realtime editing.  You can save a "nest" on your harddisk and use it for your editing sessions.  Now you have a triple-boot system:  Windows, Ubuntu, Dynebolic.

---

### Post by mark558 on 2007-12-25
Thanks for your help.... I'll try messing with the cpu settings in the bios, and if that doesn't work, then I'll check out dyne. Since its a live cd, then it should be a good solution for running it on my main system (a E6600 core 2 duo), which will be much better for editing :)

---

