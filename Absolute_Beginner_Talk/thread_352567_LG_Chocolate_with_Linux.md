---
title: "LG Chocolate with Linux"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by bobonthenet on 2007-02-03
I just got the new LG chocolate phone for verizon wireless so far I like it.  I have no idea how to get it working on my ubuntu pc to add mp3s to it.  Can someone help me out with this all I want to be able to do is transfer files to and from my phone.  In the meantime I'll be using windows to do what I want but most of my mp3s are on my linux computer.

---

### Post by jm240` on 2007-02-21
Did anyone know the answer to this?

---

### Post by teaker1s on 2007-02-21
if like the 8120 I had it needed a driver for xp to see it, unless you can see it as a removable hard drive in xp without installing the driver-
1)you may either have to find a card reader and copy to memory card
2) plug it in and type```
 lsusb
``` you may be able to find something out about how to interface it by knowing the chipset

---

### Post by jm240` on 2007-02-21
lsusb shows the phone up in the results, can I mount it from there?

---

### Post by teaker1s on 2007-02-21
possibly, like a usb drive or you may just see a chipset and id, I looked on google and found nothing, but maybe it's possible:popcorn:
have you tried plugging in with a memory card in it, if it will take one. 
You may find with a card it appears as removable drive

---

### Post by punx45 on 2007-02-21
verizon phone software is all locked up tight so you spend more money on Vcast crap.   I have a RAZR with Verizon and I had zero success using USB with it in any capacity, including charging with anything other than 'official' chargers.   the only success I had was interfacing with it via bluetooth on my Mac (and only after some config file hacking).   Better yet, i can ONLY do it with my phone, and not with a friends phone who has the same model and firmware.   needless to say, after the contract is up this will be the last verizon phone i ever have.
</rant>

so i would have to say that any woes you are having are software issues on the phone side, and not trouble with anything on the PC side.

---

### Post by ScottFW on 2007-02-21
punx, check out [www.hacktherazr.com](www.hacktherazr.com). They have the Windows drivers (will let you charge via USB from your PC), other free software and guides for doing some basic things like uploading ringers, pics & wallpapers, and other things like seem edits and using it for internet access. Most of those guides are Windows-based though.

I haven't seen anybody mention connecting their Verizon phone to Linux. If it has a removable SD card you might be able to take that out of the phone and put mp3s on the card from Linux. But I don't know if Linux will play nicely with the phone itself.

---

### Post by vicG on 2007-02-22
I have the chocolate, too.  I put the 2gb chip in it, and connect it to a usb port, and it shows up as any mass storage device under Ubuntu, lsusb will show it, lots of ways to deal with it.  

If you just want to dump a pile of mp3's on it, that works fine, just one caveat:
If you've never used the memory chip, stick it into the chocolate, and wait about 10-30 seconds.  The device will format the chip with a FAT32 fs, and toss on a few directories.

One of them is called "My Music" or something like that, and in that subdir is where all your music must go, with no other folder structure -- just a dump of mp3 files.  You can then organize them into playlists on the chocolate itself, but it's tedious.

I haven't had the time, but I'm going to look into synching playlists from amarok down to the chocolate.  Until then, I have had to dual boot for that functionality -- until now, I recently found an app called BitPim on SourceForge, and it can sync playlists, ringtones, get video's taken by the phone -- lots of features.  FOSS uber alles, baby:

[http://www.bitpim.org/help/phone-lgvx8500.htm](http://www.bitpim.org/help/phone-lgvx8500.htm)

Hope that helps

---

### Post by Salarzae on 2007-06-04
I've LG Chocolate KG800. I can upload vids, pix, and mp3's but I can't use the pix as wallpapers. What do I do?

:(

---

### Post by Salarzae on 2007-06-10
I got rid of it... now I got SE K800i. I'm loving it. It works fine and as u'd expect it to be.

---

### Post by rmannon on 2007-06-13
I have bitpim working with Linux and  LG Chocolate.  It's pretty easy.

1.  Go to bitpim and download bitpim.deb version 1.0.  I have attached a link to the file to use.  

[http://prdownloads.sourceforge.net/bitpim/bitpim_1.0.0_i386.deb?download](http://prdownloads.sourceforge.net/bitpim/bitpim_1.0.0_i386.deb?download)

2. install .deb file.  Double click the .deb file.  GDebi will install file after you give it your password.

3.  Thats it! I haven't set up a short cut for this yet...But i did figure out you have to use sudo when starting bitpim  to gain access to your phone.  Something about the USB ports not being accessible to a regular user.   Does anybody know how to fix this?

I had problems with other versions of bitpim and Linux.  I actually loaded an old hard drive with windows just so I could use LGdownloader to access this phone.  I just loathe the thought of having to pay verizon to use my phone in the way it was intended to be used.  But I learned a whole heck of a lot at this forum about how this phone works:  [http://howardforums.com/showthread.php?t=1008084](http://howardforums.com/showthread.php?t=1008084)

Hope that helps.
-r

---

### Post by bbarcelo on 2007-06-13
> **vicG said:**
> I have the chocolate, too.  I put the 2gb chip in it, and connect it to a usb port, and it shows up as any mass storage device under Ubuntu, lsusb will show it, lots of ways to deal with it.  

If you just want to dump a pile of mp3's on it, that works fine, just one caveat:
If you've never used the memory chip, stick it into the chocolate, and wait about 10-30 seconds.  The device will format the chip with a FAT32 fs, and toss on a few directories.

One of them is called "My Music" or something like that, and in that subdir is where all your music must go, with no other folder structure -- just a dump of mp3 files.  You can then organize them into playlists on the chocolate itself, but it's tedious.

I haven't had the time, but I'm going to look into synching playlists from amarok down to the chocolate.  Until then, I have had to dual boot for that functionality -- until now, I recently found an app called BitPim on SourceForge, and it can sync playlists, ringtones, get video's taken by the phone -- lots of features.  FOSS uber alles, baby:

[http://www.bitpim.org/help/phone-lgvx8500.htm](http://www.bitpim.org/help/phone-lgvx8500.htm)

Hope that helps

Bitpim in Wine. That would be my answer to this. Perhaps use ndisgtk to install the proper Windows drivers for your cell phone and then use Bitpim in Wine to access your phone. I have the VX8500, but I use it in Windows. There might actually be a Linux-compat. version of Bitpim, but you'll have to figure out getting your phone detected (though Bitpim might handle it).

---

### Post by slimdog360 on 2007-06-13
I was looking at that phone, whats it like? would you recommend it? I heard that the buttons are annoying and that its a fingerprint magnet, other then that it looks good.

---

### Post by bbarcelo on 2007-06-13
It is a fingerprint magnet but the "buttons" are actually rather slick once you get used to them. The phone is feature rich and really quite good. I had my doubts before buying it, especially since I have large hands, but I really haven't had any trouble with it. The voice-recognition isn't the greatest, but that's really the only technical downfall I've found so far. I'd recommend it 7 days a week and there's really nothing quite like hearing your phone ring, getting it out of your pocket, and sliding it open. It's like the Matrix.

---

### Post by rmannon on 2007-06-13
I could never get wine to work with bitpim.  The new .deb file at [www.bitpim.org](www.bitpim.org) is compiled on fiesty so I assume it will work with most of your installs.  

I like this phone.  Especially since I now have open access under linux.  It does take a bit of getting used to how the buttons work.  But after 3 days I was rockin Contra on it.  So I guess it is fairly easy to use.

---

### Post by dawna_2001 on 2007-06-28
I get an error when trying to install the DEB file:

---

### Post by Megaqwerty on 2007-07-18
> **dawna_2001 said:**
> I get an error when trying to install the DEB file:
You need the libatk-1.0-0 library. It is avaliable in Feisty. I'm not sure if it would be advisable, but you could try to download and install it from [http://packages.ubuntu.com/feisty/libs/libatk1.0-0](http://packages.ubuntu.com/feisty/libs/libatk1.0-0) you may also need [http://packages.ubuntu.com/feisty/misc/libatk1.0-data](http://packages.ubuntu.com/feisty/misc/libatk1.0-data)

Hope that helps,

Megaqwerty

---

### Post by deadlikeoscar on 2007-07-19
I have gotten BitPim to work but it is incredibly slow to try and transfer music to it. Is there a way to mount the card directly without buying a card reader? I have a screenshot of what BitPim says about the phone.

Here is dmesg:

```
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 00000000000a0000 end: 00000000000a0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000002fd74000 end: 000000002fe74000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000002fe74000 size: 0000000000002000 end: 000000002fe76000 type: 4
[    0.000000] copy_e820_map() start: 000000002fe76000 size: 0000000000021000 end: 000000002fe97000 type: 3
[    0.000000] copy_e820_map() start: 000000002fe97000 size: 0000000000069000 end: 000000002ff00000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000010000 end: 00000000fee10000 type: 2
[    0.000000] copy_e820_map() start: 00000000ffb00000 size: 0000000000500000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000002fe74000 (usable)
[    0.000000]  BIOS-e820: 000000002fe74000 - 000000002fe76000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000002fe76000 - 000000002fe97000 (ACPI data)
[    0.000000]  BIOS-e820: 000000002fe97000 - 000000002ff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 766MB LOWMEM available.
[    0.000000] found SMP MP-table at 000fe710
[    0.000000] Entering add_active_range(0, 0, 196212) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   196212
[    0.000000]   HighMem    196212 ->   196212
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   196212
[    0.000000] On node 0 totalpages: 196212
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1500 pages used for memmap
[    0.000000]   Normal zone: 190616 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 DELL                                  ) @ 0x000feb80
[    0.000000] ACPI: RSDT (v001 DELL    2400    0x00000007 ASL  0x00000061) @ 0x000fd22a
[    0.000000] ACPI: FADT (v001 DELL    2400    0x00000007 ASL  0x00000061) @ 0x000fd25e
[    0.000000] ACPI: SSDT (v001   DELL    st_ex 0x00001000 MSFT 0x0100000d) @ 0xfffce4f5
[    0.000000] ACPI: MADT (v001 DELL    2400    0x00000007 ASL  0x00000061) @ 0x000fd2d2
[    0.000000] ACPI: BOOT (v001 DELL    2400    0x00000007 ASL  0x00000061) @ 0x000fd33e
[    0.000000] ACPI: DSDT (v001   DELL    dt_ex 0x00001000 MSFT 0x0100000d) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 2ff00000:ced00000)
[    0.000000] Detected 2658.163 MHz processor.
[   21.165802] Built 1 zonelists.  Total pages: 194680
[   21.165807] Kernel command line: root=UUID=c12c3a1e-15fc-4079-8c45-6843970a27d1 ro quiet splash
[   21.165969] mapped APIC to ffffd000 (fee00000)
[   21.165972] mapped IOAPIC to ffffc000 (fec00000)
[   21.165975] Enabling fast FPU save and restore... done.
[   21.165979] Enabling unmasked SIMD FPU exception support... done.
[   21.165992] Initializing CPU#0
[   21.166087] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   21.167989] Console: colour VGA+ 80x25
[   21.168748] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   21.169511] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   21.185200] Memory: 766776k/784848k available (1992k kernel code, 17424k reserved, 900k data, 328k init, 0k highmem)
[   21.185211] virtual kernel memory layout:
[   21.185212]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   21.185213]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   21.185214]     vmalloc : 0xf0800000 - 0xff7fe000   ( 239 MB)
[   21.185215]     lowmem  : 0xc0000000 - 0xefe74000   ( 766 MB)
[   21.185216]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   21.185217]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[   21.185218]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[   21.185221] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   21.262039] Calibrating delay using timer specific routine.. 5320.56 BogoMIPS (lpj=10641122)
[   21.262084] Security Framework v1.0.0 initialized
[   21.262092] SELinux:  Disabled at boot.
[   21.262110] Mount-cache hash table entries: 512
[   21.262260] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[   21.262272] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   21.262275] CPU: L2 cache: 512K
[   21.262277] CPU: Hyper-Threading is disabled
[   21.262279] CPU: After all inits, caps: bfebfbff 00000000 00000000 00003080 00004400 00000000 00000000
[   21.262292] Compat vDSO mapped to ffffe000.
[   21.262296] Remapping vsyscall page to ffffe000
[   21.262308] Checking 'hlt' instruction... OK.
[   21.278125] SMP alternatives: switching to UP code
[   21.278315] Freeing SMP alternatives: 11k freed
[   21.278529] Early unpacking initramfs... done
[   21.568061] ACPI: Core revision 20060707
[   21.568539] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   21.591441] CPU0: Intel(R) Pentium(R) 4 CPU 2.66GHz stepping 09
[   21.591485] Total of 1 processors activated (5320.56 BogoMIPS).
[   21.591621] ENABLING IO-APIC IRQs
[   21.591813] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   21.737813] Brought up 1 CPUs
[   21.738068] Booting paravirtualized kernel on bare hardware
[   21.738148] Time:  2:17:56  Date: 06/19/107
[   21.738181] NET: Registered protocol family 16
[   21.738285] EISA bus registered
[   21.738290] ACPI: bus type pci registered
[   21.738380] PCI: PCI BIOS revision 2.10 entry at 0xfbbbf, last bus=1
[   21.738382] PCI: Using configuration type 1
[   21.738384] Setting up standard PCI resources
[   21.758602] ACPI: Interpreter enabled
[   21.758606] ACPI: Using IOAPIC for interrupt routing
[   21.762925] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   21.762934] PCI: Probing PCI hardware (bus 00)
[   21.762953] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[   21.765202] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[   21.765204] * this clock source is slow. If you are sure your timer does not have
[   21.765205] * this bug, please use "acpi_pm_good" to disable the workaround
[   21.765250] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[   21.765254] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
[   21.765501] Boot video device is 0000:01:05.0
[   21.765583] PCI: Transparent bridge - 0000:00:1e.0
[   21.765606] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   21.979521] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[   22.004633] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[   22.005350] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 15)
[   22.006075] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[   22.006787] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[   22.007524] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[   22.008261] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[   22.008991] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[   22.009715] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[   22.009873] Linux Plug and Play Support v0.97 (c) Adam Belay
[   22.009886] pnp: PnP ACPI init
[   22.038939] pnp: PnP ACPI: found 12 devices
[   22.038945] PnPBIOS: Disabled by ACPI PNP
[   22.039002] PCI: Using ACPI for IRQ routing
[   22.039005] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   22.043550] NET: Registered protocol family 8
[   22.043552] NET: Registered protocol family 20
[   22.049998] pnp: 00:0b: ioport range 0x800-0x85f could not be reserved
[   22.050002] pnp: 00:0b: ioport range 0xc00-0xc7f has been reserved
[   22.050004] pnp: 00:0b: ioport range 0x860-0x8ff could not be reserved
[   22.050317] PCI: Bridge: 0000:00:1e.0
[   22.050319]   IO window: disabled.
[   22.050325]   MEM window: fd000000-feafffff
[   22.050330]   PREFETCH window: e0000000-efffffff
[   22.050345] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   22.050380] NET: Registered protocol family 2
[   22.089670] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   22.089902] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   22.091035] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   22.091763] TCP: Hash tables configured (established 131072 bind 65536)
[   22.091768] TCP reno registered
[   22.101744] checking if image is initramfs... it is
[   22.673007] Freeing initrd memory: 6778k freed
[   22.673274] Simple Boot Flag value 0x87 read from CMOS RAM was invalid
[   22.673277] Simple Boot Flag at 0x7a set to 0x1
[   22.673531] audit: initializing netlink socket (disabled)
[   22.673547] audit(1184811476.592:1): initialized
[   22.673705] VFS: Disk quotas dquot_6.5.1
[   22.673730] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   22.673785] io scheduler noop registered
[   22.673788] io scheduler anticipatory registered
[   22.673790] io scheduler deadline registered
[   22.673801] io scheduler cfq registered (default)
[   22.674076] isapnp: Scanning for PnP cards...
[   23.028166] isapnp: No Plug & Play device found
[   23.056271] Real Time Clock Driver v1.12ac
[   23.056321] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   23.056441] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   23.057349] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   23.057618] mice: PS/2 mouse device common for all mice
[   23.058213] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   23.058478] input: Macintosh mouse button emulation as /class/input/input0
[   23.058516] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   23.058520] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   23.058774] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[   23.062331] serio: i8042 KBD port at 0x60,0x64 irq 1
[   23.062338] serio: i8042 AUX port at 0x60,0x64 irq 12
[   23.062511] EISA: Probing bus 0 at eisa.0
[   23.062547] EISA: Detected 0 cards.
[   23.092637] TCP cubic registered
[   23.092646] NET: Registered protocol family 1
[   23.092674] Using IPI No-Shortcut mode
[   23.092746] ACPI: (supports S0 S1 S3 S4 S5)
[   23.092794]   Magic number: 15:361:258
[   23.092838]   hash matches device ttyx0
[   23.093008] Time: tsc clocksource has been installed.
[   23.093376] Freeing unused kernel memory: 328k freed
[   23.107373] input: AT Translated Set 2 keyboard as /class/input/input1
[   24.327096] Capability LSM initialized
[   24.368563] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   24.892798] usbcore: registered new interface driver usbfs
[   24.892828] usbcore: registered new interface driver hub
[   24.892854] usbcore: registered new device driver usb
[   24.893789] USB Universal Host Controller Interface driver v3.0
[   24.893846] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   24.893859] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   24.893863] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   24.894021] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   24.894049] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000ff80
[   24.894167] usb usb1: configuration #1 chosen from 1 choice
[   24.894196] hub 1-0:1.0: USB hub found
[   24.894203] hub 1-0:1.0: 2 ports detected
[   25.000012] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[   25.000025] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   25.000029] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   25.000051] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   25.000079] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000ff60
[   25.000181] usb usb2: configuration #1 chosen from 1 choice
[   25.000212] hub 2-0:1.0: USB hub found
[   25.000221] hub 2-0:1.0: 2 ports detected
[   25.048833] Floppy drive(s): fd0 is 1.44M
[   25.080215] FDC 0 is a post-1991 82077
[   25.107965] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   25.107978] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   25.107982] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   25.108005] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   25.108034] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ff40
[   25.108137] usb usb3: configuration #1 chosen from 1 choice
[   25.108163] hub 3-0:1.0: USB hub found
[   25.108173] hub 3-0:1.0: 2 ports detected
[   25.216913] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
[   25.216933] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   25.216937] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   25.216982] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[   25.217023] ehci_hcd 0000:00:1d.7: debug port 1
[   25.217029] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   25.217040] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xffa80800
[   25.220915] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   25.221034] usb usb4: configuration #1 chosen from 1 choice
[   25.221062] hub 4-0:1.0: USB hub found
[   25.221071] hub 4-0:1.0: 6 ports detected
[   25.334634] SCSI subsystem initialized
[   25.340182] b44.c:v1.01 (Jun 16, 2006)
[   25.340207] ACPI: PCI Interrupt 0000:01:09.0[A] -> GSI 17 (level, low) -> IRQ 20
[   25.343651] eth0: Broadcom 4400 10/100BaseT Ethernet 00:0f:1f:46:73:cc
[   25.343966] libata version 2.20 loaded.
[   25.347860] ata_piix 0000:00:1f.1: version 2.10ac1
[   25.347878] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   25.347898] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   25.347952] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
[   25.347987] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
[   25.348009] scsi0 : ata_piix
[   25.531897] ata1.00: ata_hpa_resize 1: sectors = 156250000, hpa_sectors = 156250000
[   25.531902] ata1.00: ATA-7: Maxtor 6Y080L0, YAR41BW0, max UDMA/133
[   25.531905] ata1.00: 156250000 sectors, multi 8: LBA 
[   25.533447] ata1.01: ata_hpa_resize 1: sectors = 398297088, hpa_sectors = 398297088
[   25.533450] ata1.01: ATA-7: Maxtor 6L200R0, BAJ41G20, max UDMA/133
[   25.533452] ata1.01: 398297088 sectors, multi 8: LBA48 
[   25.543892] ata1.00: ata_hpa_resize 1: sectors = 156250000, hpa_sectors = 156250000
[   25.543895] ata1.00: configured for UDMA/100
[   25.557282] ata1.01: ata_hpa_resize 1: sectors = 398297088, hpa_sectors = 398297088
[   25.557285] ata1.01: configured for UDMA/100
[   25.557298] scsi1 : ata_piix
[   25.855339] usb 2-2: new full speed USB device using uhci_hcd and address 2
[   25.883549] ata2.00: ATAPI, max UDMA/33
[   26.036389] usb 2-2: configuration #1 chosen from 1 choice
[   26.055551] ata2.00: configured for UDMA/33
[   26.059364] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6Y080L0   YAR4 PQ: 0 ANSI: 5
[   26.063358] scsi 0:0:1:0: Direct-Access     ATA      Maxtor 6L200R0   BAJ4 PQ: 0 ANSI: 5
[   26.072551] scsi 1:0:0:0: CD-ROM            TEAC     DVD+RW DV-W58E   D.0N PQ: 0 ANSI: 5
[   26.085776] usbcore: registered new interface driver hiddev
[   26.095624] SCSI device sda: 156250000 512-byte hdwr sectors (80000 MB)
[   26.095641] sda: Write Protect is off
[   26.095644] sda: Mode Sense: 00 3a 00 00
[   26.095662] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.095738] SCSI device sda: 156250000 512-byte hdwr sectors (80000 MB)
[   26.095749] sda: Write Protect is off
[   26.095751] sda: Mode Sense: 00 3a 00 00
[   26.095769] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.095772]  sda: sda1 sda2 sda3 sda4 <<6>hiddev96: USB HID v1.00 Device [Dell Dell A940] on usb-0000:00:1d.1-2
[   26.115457] usbcore: registered new interface driver usbhid
[   26.115462] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   26.127651]  sda5 >
[   26.128320] sd 0:0:0:0: Attached scsi disk sda
[   26.128484] SCSI device sdb: 398297088 512-byte hdwr sectors (203928 MB)
[   26.128499] sdb: Write Protect is off
[   26.128501] sdb: Mode Sense: 00 3a 00 00
[   26.128520] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.128569] SCSI device sdb: 398297088 512-byte hdwr sectors (203928 MB)
[   26.128580] sdb: Write Protect is off
[   26.128583] sdb: Mode Sense: 00 3a 00 00
[   26.128600] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.128603]  sdb: sdb1 < sdb5 >
[   26.144803] sd 0:0:1:0: Attached scsi disk sdb
[   26.149911] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   26.150027] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   26.150136] sr 1:0:0:0: Attached scsi generic sg2 type 5
[   26.171867] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   26.171873] Uniform CD-ROM driver Revision: 3.20
[   26.172143] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   26.484409] Attempting manual resume
[   26.484413] swsusp: Resume From Partition 8:5
[   26.484415] PM: Checking swsusp image.
[   26.484654] PM: Resume from disk failed.
[   26.501038] EXT3-fs: INFO: recovery required on readonly filesystem.
[   26.501043] EXT3-fs: write access will be enabled during recovery.
[   29.677784] kjournald starting.  Commit interval 5 seconds
[   29.677806] EXT3-fs: sda3: orphan cleanup on readonly fs
[   29.696828] ext3_orphan_cleanup: deleting unreferenced inode 98255
[   29.728718] ext3_orphan_cleanup: deleting unreferenced inode 2256585
[   29.740470] ext3_orphan_cleanup: deleting unreferenced inode 2812751
[   29.767299] ext3_orphan_cleanup: deleting unreferenced inode 2077776
[   29.809828] ext3_orphan_cleanup: deleting unreferenced inode 2260032
[   29.825141] ext3_orphan_cleanup: deleting unreferenced inode 2260031
[   29.834401] ext3_orphan_cleanup: deleting unreferenced inode 2259866
[   29.834415] ext3_orphan_cleanup: deleting unreferenced inode 2259861
[   29.834425] ext3_orphan_cleanup: deleting unreferenced inode 2259847
[   29.834434] ext3_orphan_cleanup: deleting unreferenced inode 2259846
[   29.842632] ext3_orphan_cleanup: deleting unreferenced inode 2259834
[   29.850074] ext3_orphan_cleanup: deleting unreferenced inode 2259392
[   29.850087] ext3_orphan_cleanup: deleting unreferenced inode 2259391
[   29.856339] EXT3-fs: sda3: 13 orphan inodes deleted
[   29.856341] EXT3-fs: recovery complete.
[   30.088369] EXT3-fs: mounted filesystem with ordered data mode.
[   44.358242] NET: Registered protocol family 17
[   44.828348] Linux agpgart interface v0.102 (c) Dave Jones
[   44.830814] agpgart: Detected an Intel 845G Chipset.
[   44.830937] agpgart: Detected 892K stolen memory.
[   44.859938] agpgart: AGP aperture is 128M @ 0xd0000000
[   45.290139] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   45.292190] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   45.312969] iTCO_vendor_support: vendor-support=0
[   45.314160] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   45.314253] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x0860)
[   45.314295] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   45.333505] intel_rng: FWH not detected
[   45.361980] input: PC Speaker as /class/input/input2
[   45.405083] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x413C pid 0x5103
[   45.405096] usbcore: registered new interface driver usblp
[   45.405099] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   45.536562] i810_smbus 0000:00:02.0: i810/i815 i2c device found.
[   45.548492] parport: PnPBIOS parport detected.
[   45.548543] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   45.658399] nvidia: module license 'NVIDIA' taints kernel.
[   45.920326] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 20
[   45.920604] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
[   45.972785] usbcore: registered new interface driver xpad
[   45.972790] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6
[   46.184269] input: ImPS/2 Logitech Wheel Mouse as /class/input/input3
[   46.222466] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 20
[   46.222492] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   46.543034] intel8x0_measure_ac97_clock: measured 58176 usecs
[   46.543038] intel8x0: clocking to 48000
[   46.660747] lp0: using parport0 (interrupt-driven).
[   46.683102] b44: eth0: Link is up at 10 Mbps, half duplex.
[   46.683107] b44: eth0: Flow control is off for TX and off for RX.
[   46.768462] fuse init (API version 7.8)
[   46.805173] Adding 1100412k swap on /dev/disk/by-uuid/32be1e5a-9dd6-421d-9094-08fd5b6aa5d1.  Priority:-1 extents:1 across:1100412k
[   46.909829] EXT3 FS on sda3, internal journal
[   47.743318] NET: Registered protocol family 10
[   47.743421] lo: Disabled Privacy Extensions
[   48.387458] input: Power Button (FF) as /class/input/input4
[   48.392527] ACPI: Power Button (FF) [PWRF]
[   48.424300] input: Power Button (CM) as /class/input/input5
[   48.429238] ACPI: Power Button (CM) [VBTN]
[   48.439517] No dock devices found.
[   48.571992] ibm_acpi: ec object not found
[   48.636711] Using specific hotkey driver
[   48.705503] pcc_acpi: loading...
[   52.978354] ppdev: user-space parallel port driver
[   55.053755] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   55.053762] apm: overridden by ACPI.
[   56.689060] device eth0 entered promiscuous mode
[   56.689071] audit(1184825911.215:2): dev=eth0 prom=256 old_prom=0 auid=4294967295
[   58.286648] vboxdrv: Trying to deactivate NMI watchdog permanently...
[   58.286654] vboxdrv: Successfully done.
[   59.067172] Bluetooth: Core ver 2.11
[   59.067242] NET: Registered protocol family 31
[   59.067244] Bluetooth: HCI device and connection manager initialized
[   59.067248] Bluetooth: HCI socket layer initialized
[   59.193518] Bluetooth: L2CAP ver 2.8
[   59.193522] Bluetooth: L2CAP socket layer initialized
[   59.248434] Bluetooth: RFCOMM socket layer initialized
[   59.248449] Bluetooth: RFCOMM TTY layer initialized
[   59.248451] Bluetooth: RFCOMM ver 1.8
[   68.657894] eth0: no IPv6 routers present
[  372.094572] device eth0 left promiscuous mode
[  372.094585] audit(1184826239.518:3): dev=eth0 prom=0 old_prom=256 auid=4294967295
[  372.125562] device eth0 entered promiscuous mode
[  372.125574] audit(1184826239.550:4): dev=eth0 prom=256 old_prom=0 auid=4294967295
[51311.682229] usb 2-1: new full speed USB device using uhci_hcd and address 3
[51311.864638] usb 2-1: configuration #1 chosen from 1 choice
[51312.344494] usbcore: registered new interface driver libusual
[51312.362826] Initializing USB Mass Storage driver...
[51312.362902] scsi2 : SCSI emulation for USB Mass Storage devices
[51312.362959] usbcore: registered new interface driver usb-storage
[51312.362962] USB Mass Storage support registered.
[51312.363094] usb-storage: device found at 3
[51312.363096] usb-storage: waiting for device to settle before scanning
[51317.360241] usb-storage: device scan complete
[51317.363239] scsi 2:0:0:0: Direct-Access              Digtal Camera    0101 PQ: 0 ANSI: 0 CCS
[51317.368209] SCSI device sdc: 2011968 512-byte hdwr sectors (1030 MB)
[51317.371206] sdc: Write Protect is off
[51317.371210] sdc: Mode Sense: 00 46 00 00
[51317.371212] sdc: assuming drive cache: write through
[51317.383196] SCSI device sdc: 2011968 512-byte hdwr sectors (1030 MB)
[51317.386193] sdc: Write Protect is off
[51317.386196] sdc: Mode Sense: 00 46 00 00
[51317.386198] sdc: assuming drive cache: write through
[51317.386203]  sdc: sdc1
[51317.395207]  sdc: p1 exceeds device capacity
[51317.395282] sd 2:0:0:0: Attached scsi removable disk sdc
[51317.395330] sd 2:0:0:0: Attached scsi generic sg3 type 0
[51317.522876] attempt to access beyond end of device
[51317.522884] sdc: rw=0, want=2012020, limit=2011968
[51317.522888] Buffer I/O error on device sdc1, logical block 2011776
[51317.523394] attempt to access beyond end of device
[51317.523398] sdc: rw=0, want=2012021, limit=2011968
[51317.523400] Buffer I/O error on device sdc1, logical block 2011777
[51317.523813] attempt to access beyond end of device
[51317.523817] sdc: rw=0, want=2012022, limit=2011968
[51317.523820] Buffer I/O error on device sdc1, logical block 2011778
[51317.524207] attempt to access beyond end of device
[51317.524210] sdc: rw=0, want=2012023, limit=2011968
[51317.524213] Buffer I/O error on device sdc1, logical block 2011779
[51317.524589] attempt to access beyond end of device
[51317.524593] sdc: rw=0, want=2012024, limit=2011968
[51317.524595] Buffer I/O error on device sdc1, logical block 2011780
[51317.524970] attempt to access beyond end of device
[51317.524974] sdc: rw=0, want=2012025, limit=2011968
[51317.524976] Buffer I/O error on device sdc1, logical block 2011781
[51317.525348] attempt to access beyond end of device
[51317.525352] sdc: rw=0, want=2012026, limit=2011968
[51317.525355] Buffer I/O error on device sdc1, logical block 2011782
[51317.525819] attempt to access beyond end of device
[51317.525824] sdc: rw=0, want=2012027, limit=2011968
[51317.525826] Buffer I/O error on device sdc1, logical block 2011783
[51317.526222] attempt to access beyond end of device
[51317.526226] sdc: rw=0, want=2012020, limit=2011968
[51317.526228] Buffer I/O error on device sdc1, logical block 2011776
[51317.526604] attempt to access beyond end of device
[51317.526608] sdc: rw=0, want=2012021, limit=2011968
[51317.526611] Buffer I/O error on device sdc1, logical block 2011777
[51317.526993] attempt to access beyond end of device
[51317.526997] sdc: rw=0, want=2012022, limit=2011968
[51317.527251] attempt to access beyond end of device
[51317.527255] sdc: rw=0, want=2012023, limit=2011968
[51317.527507] attempt to access beyond end of device
[51317.527510] sdc: rw=0, want=2012024, limit=2011968
[51317.527762] attempt to access beyond end of device
[51317.527766] sdc: rw=0, want=2012025, limit=2011968
[51317.528127] attempt to access beyond end of device
[51317.528131] sdc: rw=0, want=2012026, limit=2011968
[51317.528385] attempt to access beyond end of device
[51317.528389] sdc: rw=0, want=2012027, limit=2011968
[51317.528666] attempt to access beyond end of device
[51317.528670] sdc: rw=0, want=2012156, limit=2011968
[51317.528931] attempt to access beyond end of device
[51317.528935] sdc: rw=0, want=2012157, limit=2011968
[51317.529188] attempt to access beyond end of device
[51317.529192] sdc: rw=0, want=2012158, limit=2011968
[51317.529445] attempt to access beyond end of device
[51317.529448] sdc: rw=0, want=2012159, limit=2011968
[51317.529707] attempt to access beyond end of device
[51317.529711] sdc: rw=0, want=2012160, limit=2011968
[51317.529981] attempt to access beyond end of device
[51317.529985] sdc: rw=0, want=2012156, limit=2011968
[51317.530240] attempt to access beyond end of device
[51317.530244] sdc: rw=0, want=2012157, limit=2011968
[51317.530496] attempt to access beyond end of device
[51317.530500] sdc: rw=0, want=2012158, limit=2011968
[51317.530846] attempt to access beyond end of device
[51317.530851] sdc: rw=0, want=2012159, limit=2011968
[51317.531112] attempt to access beyond end of device
[51317.531116] sdc: rw=0, want=2012160, limit=2011968
[51317.531385] attempt to access beyond end of device
[51317.531389] sdc: rw=0, want=2012156, limit=2011968
[51317.531645] attempt to access beyond end of device
[51317.531649] sdc: rw=0, want=2012157, limit=2011968
[51317.531902] attempt to access beyond end of device
[51317.531906] sdc: rw=0, want=2012158, limit=2011968
[51317.532159] attempt to access beyond end of device
[51317.532163] sdc: rw=0, want=2012159, limit=2011968
[51317.532432] attempt to access beyond end of device
[51317.532436] sdc: rw=0, want=2012160, limit=2011968
[51317.532711] attempt to access beyond end of device
[51317.532715] sdc: rw=0, want=2012156, limit=2011968
[51317.532972] attempt to access beyond end of device
[51317.532975] sdc: rw=0, want=2012157, limit=2011968
[51317.533226] attempt to access beyond end of device
[51317.533230] sdc: rw=0, want=2012158, limit=2011968
[51317.533486] attempt to access beyond end of device
[51317.533490] sdc: rw=0, want=2012159, limit=2011968
[51317.533741] attempt to access beyond end of device
[51317.533745] sdc: rw=0, want=2012160, limit=2011968
[51317.534004] attempt to access beyond end of device
[51317.534008] sdc: rw=0, want=2012156, limit=2011968
[51317.534393] attempt to access beyond end of device
[51317.534398] sdc: rw=0, want=2012157, limit=2011968
[51317.534655] attempt to access beyond end of device
[51317.534659] sdc: rw=0, want=2012158, limit=2011968
[51317.534916] attempt to access beyond end of device
[51317.534919] sdc: rw=0, want=2012159, limit=2011968
[51317.535169] attempt to access beyond end of device
[51317.535173] sdc: rw=0, want=2012160, limit=2011968
[51317.535433] attempt to access beyond end of device
[51317.535437] sdc: rw=0, want=2012156, limit=2011968
[51317.535688] attempt to access beyond end of device
[51317.535692] sdc: rw=0, want=2012157, limit=2011968
[51317.535941] attempt to access beyond end of device
[51317.535944] sdc: rw=0, want=2012158, limit=2011968
[51317.536193] attempt to access beyond end of device
[51317.536197] sdc: rw=0, want=2012159, limit=2011968
[51317.536462] attempt to access beyond end of device
[51317.536466] sdc: rw=0, want=2012160, limit=2011968
[51317.536728] attempt to access beyond end of device
[51317.536732] sdc: rw=0, want=2012092, limit=2011968
[51317.536987] attempt to access beyond end of device
[51317.536990] sdc: rw=0, want=2012093, limit=2011968
[51317.537241] attempt to access beyond end of device
[51317.537244] sdc: rw=0, want=2012094, limit=2011968
[51317.537498] attempt to access beyond end of device
[51317.537501] sdc: rw=0, want=2012095, limit=2011968
[51317.537751] attempt to access beyond end of device
[51317.537755] sdc: rw=0, want=2012096, limit=2011968
[51317.538004] attempt to access beyond end of device
[51317.538008] sdc: rw=0, want=2012097, limit=2011968
[51317.538257] attempt to access beyond end of device
[51317.538261] sdc: rw=0, want=2012098, limit=2011968
[51317.538510] attempt to access beyond end of device
[51317.538514] sdc: rw=0, want=2012099, limit=2011968
[51317.538791] attempt to access beyond end of device
[51317.538795] sdc: rw=0, want=2012148, limit=2011968
[51317.539060] attempt to access beyond end of device
[51317.539064] sdc: rw=0, want=2012149, limit=2011968
[51317.539314] attempt to access beyond end of device
[51317.539318] sdc: rw=0, want=2012150, limit=2011968
[51317.539567] attempt to access beyond end of device
[51317.539571] sdc: rw=0, want=2012151, limit=2011968
[51317.539819] attempt to access beyond end of device
[51317.539823] sdc: rw=0, want=2012152, limit=2011968
[51317.540073] attempt to access beyond end of device
[51317.540076] sdc: rw=0, want=2012153, limit=2011968
[51317.540325] attempt to access beyond end of device
[51317.540329] sdc: rw=0, want=2012154, limit=2011968
[51317.540578] attempt to access beyond end of device
[51317.540582] sdc: rw=0, want=2012155, limit=2011968
[51317.540842] attempt to access beyond end of device
[51317.540846] sdc: rw=0, want=2012156, limit=2011968
[51317.541099] attempt to access beyond end of device
[51317.541103] sdc: rw=0, want=2012157, limit=2011968
[51317.541454] attempt to access beyond end of device
[51317.541458] sdc: rw=0, want=2012158, limit=2011968
[51317.541712] attempt to access beyond end of device
[51317.541716] sdc: rw=0, want=2012159, limit=2011968
[51317.541968] attempt to access beyond end of device
[51317.541972] sdc: rw=0, want=2012160, limit=2011968
[51317.542231] attempt to access beyond end of device
[51317.542235] sdc: rw=0, want=2012156, limit=2011968
[51317.542487] attempt to access beyond end of device
[51317.542491] sdc: rw=0, want=2012157, limit=2011968
[51317.542759] attempt to access beyond end of device
[51317.542763] sdc: rw=0, want=2012158, limit=2011968
[51317.543015] attempt to access beyond end of device
[51317.543018] sdc: rw=0, want=2012159, limit=2011968
[51317.543269] attempt to access beyond end of device
[51317.543273] sdc: rw=0, want=2012160, limit=2011968
[51317.708523] attempt to access beyond end of device
[51317.708533] sdc: rw=0, want=2012020, limit=2011968
[51317.708901] attempt to access beyond end of device
[51317.708905] sdc: rw=0, want=2012021, limit=2011968
[51317.709179] attempt to access beyond end of device
[51317.709183] sdc: rw=0, want=2012022, limit=2011968
[51317.709450] attempt to access beyond end of device
[51317.709454] sdc: rw=0, want=2012023, limit=2011968
[51317.709714] attempt to access beyond end of device
[51317.709717] sdc: rw=0, want=2012024, limit=2011968
[51317.709983] attempt to access beyond end of device
[51317.709987] sdc: rw=0, want=2012025, limit=2011968
[51317.710283] attempt to access beyond end of device
[51317.710287] sdc: rw=0, want=2012026, limit=2011968
[51317.710549] attempt to access beyond end of device
[51317.710553] sdc: rw=0, want=2012027, limit=2011968
[51317.710844] attempt to access beyond end of device
[51317.710848] sdc: rw=0, want=2012020, limit=2011968
[51317.711109] attempt to access beyond end of device
[51317.711113] sdc: rw=0, want=2012021, limit=2011968
[51317.711373] attempt to access beyond end of device
[51317.711377] sdc: rw=0, want=2012022, limit=2011968
[51317.711637] attempt to access beyond end of device
[51317.711640] sdc: rw=0, want=2012023, limit=2011968
[51317.711900] attempt to access beyond end of device
[51317.711904] sdc: rw=0, want=2012024, limit=2011968
[51317.712163] attempt to access beyond end of device
[51317.712166] sdc: rw=0, want=2012025, limit=2011968
[51317.712426] attempt to access beyond end of device
[51317.712430] sdc: rw=0, want=2012026, limit=2011968
[51317.712690] attempt to access beyond end of device
[51317.712694] sdc: rw=0, want=2012027, limit=2011968
[51317.712974] attempt to access beyond end of device
[51317.712978] sdc: rw=0, want=2012156, limit=2011968
[51317.713244] attempt to access beyond end of device
[51317.713248] sdc: rw=0, want=2012157, limit=2011968
[51317.713512] attempt to access beyond end of device
[51317.713515] sdc: rw=0, want=2012158, limit=2011968
[51317.713794] attempt to access beyond end of device
[51317.713798] sdc: rw=0, want=2012159, limit=2011968
[51317.714060] attempt to access beyond end of device
[51317.714064] sdc: rw=0, want=2012160, limit=2011968
[51317.714325] attempt to access beyond end of device
[51317.714329] sdc: rw=0, want=2012156, limit=2011968
[51317.714718] attempt to access beyond end of device
[51317.714722] sdc: rw=0, want=2012157, limit=2011968
[51317.714984] attempt to access beyond end of device
[51317.714988] sdc: rw=0, want=2012158, limit=2011968
[51317.715250] attempt to access beyond end of device
[51317.715254] sdc: rw=0, want=2012159, limit=2011968
[51317.715514] attempt to access beyond end of device
[51317.715518] sdc: rw=0, want=2012160, limit=2011968
[51317.715792] attempt to access beyond end of device
[51317.715796] sdc: rw=0, want=2012156, limit=2011968
[51317.716059] attempt to access beyond end of device
[51317.716063] sdc: rw=0, want=2012157, limit=2011968
[51317.716323] attempt to access beyond end of device
[51317.716327] sdc: rw=0, want=2012158, limit=2011968
[51317.716587] attempt to access beyond end of device
[51317.716591] sdc: rw=0, want=2012159, limit=2011968
[51317.716879] attempt to access beyond end of device
[51317.716882] sdc: rw=0, want=2012160, limit=2011968
[51317.717153] attempt to access beyond end of device
[51317.717157] sdc: rw=0, want=2012156, limit=2011968
[51317.717424] attempt to access beyond end of device
[51317.717428] sdc: rw=0, want=2012157, limit=2011968
[51317.717687] attempt to access beyond end of device
[51317.717691] sdc: rw=0, want=2012158, limit=2011968
[51317.717951] attempt to access beyond end of device
[51317.717955] sdc: rw=0, want=2012159, limit=2011968
[51317.718215] attempt to access beyond end of device
[51317.718220] sdc: rw=0, want=2012160, limit=2011968
[51317.718571] attempt to access beyond end of device
[51317.718575] sdc: rw=0, want=2012156, limit=2011968
[51317.718850] attempt to access beyond end of device
[51317.718854] sdc: rw=0, want=2012157, limit=2011968
[51317.719113] attempt to access beyond end of device
[51317.719117] sdc: rw=0, want=2012158, limit=2011968
[51317.719376] attempt to access beyond end of device
[51317.719380] sdc: rw=0, want=2012159, limit=2011968
[51317.719639] attempt to access beyond end of device
[51317.719643] sdc: rw=0, want=2012160, limit=2011968
[51317.719911] attempt to access beyond end of device
[51317.719915] sdc: rw=0, want=2012156, limit=2011968
[51317.720177] attempt to access beyond end of device
[51317.720180] sdc: rw=0, want=2012157, limit=2011968
[51317.720457] attempt to access beyond end of device
[51317.720461] sdc: rw=0, want=2012158, limit=2011968
[51317.720722] attempt to access beyond end of device
[51317.720725] sdc: rw=0, want=2012159, limit=2011968
[51317.720984] attempt to access beyond end of device
[51317.720988] sdc: rw=0, want=2012160, limit=2011968
[51317.721259] attempt to access beyond end of device
[51317.721263] sdc: rw=0, want=2012092, limit=2011968
[51317.721530] attempt to access beyond end of device
[51317.721534] sdc: rw=0, want=2012093, limit=2011968
[51317.721795] attempt to access beyond end of device
[51317.721799] sdc: rw=0, want=2012094, limit=2011968
[51317.722057] attempt to access beyond end of device
[51317.722060] sdc: rw=0, want=2012095, limit=2011968
[51317.722319] attempt to access beyond end of device
[51317.722323] sdc: rw=0, want=2012096, limit=2011968
[51317.722582] attempt to access beyond end of device
[51317.722586] sdc: rw=0, want=2012097, limit=2011968
[51317.722849] attempt to access beyond end of device
[51317.722853] sdc: rw=0, want=2012098, limit=2011968
[51317.723125] attempt to access beyond end of device
[51317.723129] sdc: rw=0, want=2012099, limit=2011968
[51317.723413] attempt to access beyond end of device
[51317.723418] sdc: rw=0, want=2012148, limit=2011968
[51317.723683] attempt to access beyond end of device
[51317.723687] sdc: rw=0, want=2012149, limit=2011968
[51317.723947] attempt to access beyond end of device
[51317.723951] sdc: rw=0, want=2012150, limit=2011968
[51317.724211] attempt to access beyond end of device
[51317.724215] sdc: rw=0, want=2012151, limit=2011968
[51317.724475] attempt to access beyond end of device
[51317.724479] sdc: rw=0, want=2012152, limit=2011968
[51317.724739] attempt to access beyond end of device
[51317.724742] sdc: rw=0, want=2012153, limit=2011968
[51317.725002] attempt to access beyond end of device
[51317.725006] sdc: rw=0, want=2012154, limit=2011968
[51317.725265] attempt to access beyond end of device
[51317.725269] sdc: rw=0, want=2012155, limit=2011968
[51317.725541] attempt to access beyond end of device
[51317.725545] sdc: rw=0, want=2012156, limit=2011968
[51317.725806] attempt to access beyond end of device
[51317.725810] sdc: rw=0, want=2012157, limit=2011968
[51317.726070] attempt to access beyond end of device
[51317.726073] sdc: rw=0, want=2012158, limit=2011968
[51317.726333] attempt to access beyond end of device
[51317.726337] sdc: rw=0, want=2012159, limit=2011968
[51317.726596] attempt to access beyond end of device
[51317.726600] sdc: rw=0, want=2012160, limit=2011968
[51317.726888] attempt to access beyond end of device
[51317.726892] sdc: rw=0, want=2012156, limit=2011968
[51317.727155] attempt to access beyond end of device
[51317.727159] sdc: rw=0, want=2012157, limit=2011968
[51317.727419] attempt to access beyond end of device
[51317.727422] sdc: rw=0, want=2012158, limit=2011968
[51317.727683] attempt to access beyond end of device
[51317.727687] sdc: rw=0, want=2012159, limit=2011968
[51317.728042] attempt to access beyond end of device
[51317.728046] sdc: rw=0, want=2012160, limit=2011968
[51849.434567] usb 2-1: USB disconnect, address 3
[61075.173902] usb 3-2: new full speed USB device using uhci_hcd and address 2
[61075.337827] usb 3-2: configuration #1 chosen from 1 choice
[61075.964304] cdc_acm 3-2:1.0: ttyACM0: USB ACM device
[61075.968368] usbcore: registered new interface driver cdc_acm
[61075.968635] drivers/usb/class/cdc-acm.c: v0.25:USB Abstract Control Model driver for USB modems and ISDN adapters
[62315.721120] usb 2-2: usbfs: interface 1 claimed by usblp while 'bitpim' sets config #1
[62315.738069] usb 2-2: usbfs: interface 1 claimed by usblp while 'bitpim' sets config #1
[62315.754948] usb 3-2: usbfs: interface 0 claimed by cdc_acm while 'bitpim' sets config #1
[62315.764606] usb 3-2: usbfs: interface 0 claimed by cdc_acm while 'bitpim' sets config #1
[62316.012686] usb 3-2: usbfs: interface 0 claimed by cdc_acm while 'bitpim' sets config #1
[62316.345758] usb 3-2: usbfs: interface 0 claimed by cdc_acm while 'bitpim' sets config #1
[62316.421914] usb 3-2: usbfs: interface 0 claimed by cdc_acm while 'bitpim' sets config #1
[62316.496570] usb 3-2: usbfs: interface 0 claimed by cdc_acm while 'bitpim' sets config #1
[62316.524132] usb 3-2: usbfs: interface 0 claimed by cdc_acm while 'bitpim' sets config #1
[62316.683663] usb 3-2: usbfs: interface 0 claimed by cdc_acm while 'bitpim' sets config #1
[62316.717814] usb 3-2: usbfs: interface 0 claimed by cdc_acm while 'bitpim' sets config #1
[62316.801534] usb 3-2: usbfs: interface 0 claimed by cdc_acm while 'bitpim' sets config #1
[62316.831960] usb 3-2: usbfs: interface 0 claimed by cdc_acm while 'bitpim' sets config #1
[62316.974508] usb 3-2: usbfs: interface 0 claimed by cdc_acm while 'bitpim' sets config #1
[62317.004593] usb 3-2: usbfs: interface 0 claimed by cdc_acm while 'bitpim' sets config #1
[62317.256080] usb 3-2: usbfs: interface 0 claimed by cdc_acm while 'bitpim' sets config #1
[62317.274550] usb 3-2: usbfs: interface 0 claimed by cdc_acm while 'bitpim' sets config #1
[62317.300116] usb 3-2: usbfs: interface 0 claimed by cdc_acm while 'bitpim' sets config #1
[62317.648316] usb 3-2: usbfs: interface 0 claimed by cdc_acm while 'bitpim' sets config #1
[62317.714172] usb 3-2: usbfs: interface 0 claimed by cdc_acm while 'bitpim' sets config #1
[62317.721111] usb 3-2: usbfs: interface 0 claimed by cdc_acm while 'bitpim' sets config #1
[62317.737673] usb 3-2: usbfs: interface 0 claimed by cdc_acm while 'bitpim' sets config #1
[62317.777434] usb 3-2: usbfs: interface 0 claimed by cdc_acm while 'bitpim' sets config #1
[62317.801791] usb 3-2: usbfs: interface 0 claimed by cdc_acm while 'bitpim' sets config #1
[62318.080258] usb 3-2: usbfs: interface 0 claimed by cdc_acm while 'bitpim' sets config #1
[62363.576626] usb 2-2: usbfs: interface 1 claimed by usblp while 'bitpim' sets config #1
[62363.648566] usb 2-2: usbfs: interface 1 claimed by usblp while 'bitpim' sets config #1
[62363.700487] usb 3-2: usbfs: interface 0 claimed by cdc_acm while 'bitpim' sets config #1
[62363.728387] usb 3-2: usbfs: interface 0 claimed by cdc_acm while 'bitpim' sets config #1
```

Here is df:
```

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda3             23924508   9240308  13468888  41% /
varrun                  387080       116    386964   1% /var/run
varlock                 387080         0    387080   0% /var/lock
procbususb              387080       116    386964   1% /proc/bus/usb
udev                    387080       116    386964   1% /dev
devshm                  387080         0    387080   0% /dev/shm
lrm                     387080     33788    353292   9% /lib/modules/2.6.20-16-generic/volatile
/dev/sdb5            199133672 170653524  28480148  86% /media/media
/dev/sda2             52428124  17235828  35192296  33% /media/windows
```

I have a Verizon Chocolate phone with a 256 MB microSD card. Any help would be appreciated. If not, I will go the card reader route. I just don't have any need for one because my digital camera is detected automatically and I can access my 1GB card easily. That may be in the dmesg in case it throws you off or something.

---

### Post by linkunderscore on 2008-07-17
bitpim is only working for me if I run it as root. Is there a way to correct this? I guess it doesn't really matter to me if i have to run it as root, but it would be nice to run it as a regular user.

---

