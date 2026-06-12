---
title: "Why is my computer taking so long to boot? (Boot log attached)"
date: 2012-06-25
forum: Any Other OS
---

### Post by Declanthedork on 2012-06-25
After spending four days straight trying to get my new Linux Mint installation to boot up, I switched to LiLo instead of GRUB and spent another 2 days trying to get that working. I got it, but it's taking a mind numbingly long time to boot. Almost an hour. Somebody said they added this line to their boot instructions (libata.dma=0 libata.noacpi=1) but I don't think it's doing anything. Below is my boot log that I generated using dmesg:

```

] cpuidle: using governor ladder
[    0.542753] cpuidle: using governor menu
[    0.542822] EFI Variables Facility v0.08 2004-May-17
[    0.543176] TCP cubic registered
[    0.543460] NET: Registered protocol family 10
[    0.548422] NET: Registered protocol family 17
[    0.548562] Registering the dns_resolver key type
[    0.548681] Using IPI No-Shortcut mode
[    0.548943] PM: Hibernation image not present or could not be loaded.
[    0.548975] registered taskstats version 1
[    0.561513] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.943710] isapnp: No Plug & Play device found
[    1.087842] Freeing initrd memory: 13796k freed
[    1.128141]   Magic number: 0:791:753
[    1.128281] tty ttyS4: hash matches
[    1.128486] rtc_cmos 00:05: setting system clock to 2012-06-25 21:43:32 UTC (1340660612)
[    1.128569] powernow-k8: Processor cpuid 6a0 not supported
[    1.128667] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.128736] EDD information not available.
[    1.129074] Freeing unused kernel memory: 712k freed
[    1.130262] Write protecting the kernel text: 5628k
[    1.130374] Write protecting the kernel read-only data: 2324k
[    1.160364] udevd[78]: starting version 175
[    1.248079] Refined TSC clocksource calibration: 2166.419 MHz.
[    1.248167] Switching to clocksource tsc
[    1.310262] sata_via 0000:00:0f.0: version 2.6
[    1.310296] sata_via 0000:00:0f.0: PCI INT B -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    1.310465] sata_via 0000:00:0f.0: routed to hard irq line 11
[    1.331180] scsi0 : sata_via
[    1.335915] scsi1 : sata_via
[    1.336175] ata1: SATA max UDMA/133 cmd 0xac00 ctl 0xb000 bmdma 0xbc00 irq 20
[    1.336249] ata2: SATA max UDMA/133 cmd 0xb400 ctl 0xb800 bmdma 0xbc08 irq 20
[    1.336410] pata_via 0000:00:0f.1: version 0.3.4
[    1.336439] pata_via 0000:00:0f.1: PCI INT A -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    1.340126] scsi2 : pata_via
[    1.344098] scsi3 : pata_via
[    1.344296] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xc400 irq 14
[    1.344370] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xc408 irq 15
[    1.422365] via_rhine: v1.10-LK1.5.0 2010-10-09 Written by Donald Becker
[    1.422767] ACPI: PCI Interrupt Link [ALKD] BIOS reported IRQ 0, using IRQ 23
[    1.422839] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
[    1.422932] via-rhine 0000:00:12.0: PCI INT A -> Link[ALKD] -> GSI 23 (level, low) -> IRQ 23
[    1.423655] via-rhine 0000:00:12.0: eth0: VIA Rhine II at 0xe7003000, 00:11:d8:21:9c:18, IRQ 23
[    1.424466] via-rhine 0000:00:12.0: eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1
[    1.536631] ata3.00: ATA-6: HDS722580VLAT20, V32OA6EA, max UDMA/100
[    1.536713] ata3.00: 120103200 sectors, multi 16: LBA48 
[    1.540016] ata1: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    1.564465] ata3.00: configured for PIO4
[    1.752012] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    1.762752] scsi 2:0:0:0: Direct-Access     ATA      HDS722580VLAT20  V32O PQ: 0 ANSI: 5
[    1.763311] sd 2:0:0:0: [sda] 120103200 512-byte logical blocks: (61.4 GB/57.2 GiB)
[    1.763465] sd 2:0:0:0: [sda] Write Protect is off
[    1.763535] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.763568] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.764283] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    1.803673]  sda: sda1 sda2 < sda5 >
[    1.804309] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.932305] firewire_ohci 0000:00:0b.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.996090] firewire_ohci: Added fw-ohci device 0000:00:0b.0, OHCI v1.0, 4 IR + 8 IT contexts, quirks 0x11
[    2.513168] firewire_core: created device fw0: GUID 00e0180000c166db, S400
[    2.539265] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    6.312444] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    6.591931] udevd[283]: starting version 175
[    7.010583] Adding 480252k swap on /dev/sda5.  Priority:-1 extents:1 across:480252k 
[    7.565168] lp: driver loaded but no devices found
[    8.002947] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    8.138589] parport_pc 00:09: reported by Plug and Play ACPI
[    8.138717] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[    8.334846] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    8.379731] lp0: using parport0 (interrupt-driven).
[    8.636261] wmi: Mapper loaded
[    9.084629] psmouse serio1: hgpk: ID: 10 00 64
[    9.318113] [drm] Initialized drm 1.1.0 20060810
[    9.380183] ppdev: user-space parallel port driver
[    9.842209] input: PS/2 Generic Mouse as /devices/platform/i8042/serio1/input/input3
[   10.333131] VGA switcheroo: detected Optimus DSM method \ handle
[   10.333232] nouveau 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.350438] [drm] nouveau 0000:01:00.0: Detected an NV40 generation card (0x04b300a2)
[   10.352632] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PRAMIN
[   10.420199] [drm] nouveau 0000:01:00.0: ... appears to be valid
[   10.420205] [drm] nouveau 0000:01:00.0: BIT BIOS found
[   10.420210] [drm] nouveau 0000:01:00.0: Bios version 05.73.22.51
[   10.420216] [drm] nouveau 0000:01:00.0: TMDS table version 1.1
[   10.420218] [drm] nouveau 0000:01:00.0: TMDS table script pointers not stubbed
[   10.420222] [drm] nouveau 0000:01:00.0: Found Display Configuration Block version 3.0
[   10.420229] [drm] nouveau 0000:01:00.0: Raw DCB entry 0: 01000300 00000028
[   10.420234] [drm] nouveau 0000:01:00.0: Raw DCB entry 1: 03000302 00000000
[   10.420237] [drm] nouveau 0000:01:00.0: Raw DCB entry 2: 04011310 00000028
[   10.420239] [drm] nouveau 0000:01:00.0: Raw DCB entry 3: 020223f1 00c0c080
[   10.420245] [drm] nouveau 0000:01:00.0: DCB connector table: VHER 0x30 5 10 2
[   10.420249] [drm] nouveau 0000:01:00.0:   0: 0x00002030: type 0x30 idx 0 tag 0x08
[   10.420252] [drm] nouveau 0000:01:00.0:   1: 0x00000100: type 0x00 idx 1 tag 0xff
[   10.420256] [drm] nouveau 0000:01:00.0:   2: 0x00000210: type 0x10 idx 2 tag 0xff
[   10.420259] [drm] nouveau 0000:01:00.0:   3: 0x00000211: type 0x11 idx 3 tag 0xff
[   10.420262] [drm] nouveau 0000:01:00.0:   4: 0x00000213: type 0x13 idx 4 tag 0xff
[   10.420273] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 0 at offset 0xCDAD
[   10.420547] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 1 at offset 0xD457
[   10.432683] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 2 at offset 0xDB8B
[   10.432707] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 3 at offset 0xDD0F
[   10.435822] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 4 at offset 0xDF1B
[   10.461785] [drm] nouveau 0000:01:00.0: 1 available performance level(s)
[   10.461797] [drm] nouveau 0000:01:00.0: 0: core 350MHz shader 350MHz memory 333MHz voltage 1100mV fanspeed 100%
[   10.461809] [drm] nouveau 0000:01:00.0: c: core 351MHz shader 351MHz memory 333MHz
[   10.462395] [TTM] Zone  kernel: Available graphics memory: 253930 kiB.
[   10.462398] [TTM] Initializing pool allocator.
[   10.462419] [drm] nouveau 0000:01:00.0: Detected 512MiB VRAM
[   10.462772] agpgart-via 0000:00:00.0: AGP 3.5 bridge
[   10.462795] agpgart: modprobe tried to set rate=x12. Setting to AGP3 x8 mode.
[   10.462805] agpgart-via 0000:00:00.0: putting AGP V3 device into 8x mode
[   10.462873] nouveau 0000:01:00.0: putting AGP V3 device into 8x mode
[   10.462877] [drm] nouveau 0000:01:00.0: 64 MiB GART (aperture)
[   10.463074] [drm] nouveau 0000:01:00.0: Saving VGA fonts
[   10.543192] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   10.543199] [drm] No driver support for vblank timestamp query.
[   10.543210] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on vga encoder (output 0)
[   10.543216] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on tmds encoder (output 1)
[   10.543221] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on vga encoder (output 2)
[   10.543226] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on TV encoder (output 3)
[   10.912512] [drm] nouveau 0000:01:00.0: allocated 1024x768 fb: 0x49000, bo ddc27400
[   10.912947] fbcon: nouveaufb (fb0) is primary device
[   10.927612] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on vga encoder (output 2)
[   10.927620] [drm] nouveau 0000:01:00.0: Output VGA-1 is running on CRTC 0 using output C
[   10.931530] Console: switching to colour frame buffer device 128x48
[   10.932378] fb0: nouveaufb frame buffer device
[   10.932382] drm: registered panic notifier
[   10.932396] [drm] Initialized nouveau 0.0.16 20090420 for 0000:01:00.0 on minor 0
[   12.127256] snd_via82xx_modem 0000:00:11.6: enabling device (0000 -> 0001)
[   12.133140] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
[   12.133147] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[   12.133182] snd_via82xx_modem 0000:00:11.6: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
[   12.884029] snd_via82xx_modem 0000:00:11.6: setting latency timer to 64
[   13.388305] snd_via82xx_modem 0000:00:11.6: PCI INT C disabled
[   13.388328] snd_via82xx_modem: probe of 0000:00:11.6 failed with error -13
[   13.388772] snd_via82xx 0000:00:11.5: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
[   13.388936] snd_via82xx 0000:00:11.5: setting latency timer to 64
[   13.591096] init: failsafe main process (544) killed by TERM signal
[   17.985087] Bluetooth: Core ver 2.16
[   17.985221] NET: Registered protocol family 31
[   17.985224] Bluetooth: HCI device and connection manager initialized
[   17.985230] Bluetooth: HCI socket layer initialized
[   17.985233] Bluetooth: L2CAP socket layer initialized
[   17.986408] Bluetooth: SCO socket layer initialized
[   21.385858] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   21.385865] Bluetooth: BNEP filters: protocol multicast
[   21.386363] Bluetooth: RFCOMM TTY layer initialized
[   21.386369] Bluetooth: RFCOMM socket layer initialized
[   21.386372] Bluetooth: RFCOMM ver 1.11
[   28.593421] via-rhine 0000:00:12.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   36.596964] init: alsa-restore main process (943) terminated with status 99
[   40.305748] eth0: no IPv6 routers present


```

If you could take a look and see if anything stands out, it would be greatly appreciated!

---

### Post by matt_symes on 2012-06-25
Hi

> Almost an hour. 

You're serious and this is not a typo ? It's taking an hour to boot up ?

I have a couple of questions.

Why did you decide to use LILO instead of grub ? What problems were you having with grub ?

How long does it take to boot to a console as opposed to a GIU ?

What's it like after it has finally booted up ? Is it quick ?

Can you describe all your hardware please.

Kind regards

---

### Post by oldos2er on 2012-06-25
Moved to Other OS/Distro Talk.

---

### Post by Declanthedork on 2012-06-26
> **matt_symes said:**
> Hi



You're serious and this is not a typo ? It's taking an hour to boot up ?

I have a couple of questions.

Why did you decide to use LILO instead of grub ? What problems were you having with grub ?

How long does it take to boot to a console as opposed to a GIU ?

What's it like after it has finally booted up ? Is it quick ?

Can you describe all your hardware please.

Kind regards

Thank you for replying. It's seriously taking an hour! I used LILO instead of GRUB because when I used GRUB, the monitor would simply go black after the BIOS screen. If I held down shift, it would say "GRUB Loading." but never go past that. The computer was manufactured ~2004. It's an HP Pavillion a810e with about 1.5GB of RAM. Once I actually boot it up, it works absolutely fine, which is the odd part. I made sure that all peripherals except for the hard drive were disconnected to avoid any problems with them.

---

### Post by matt_symes on 2012-06-26
Hi

> **Declanthedork said:**
> Thank you for replying. It's seriously taking an hour! I used LILO instead of GRUB because when I used GRUB, the monitor would simply go black after the BIOS screen. If I held down shift, it would say "GRUB Loading." but never go past that. The computer was manufactured ~2004. It's an HP Pavillion a810e with about 1.5GB of RAM. Once I actually boot it up, it works absolutely fine, which is the odd part. I made sure that all peripherals except for the hard drive were disconnected to avoid any problems with them.

That is a bit odd. The time stamps the on the dmesg output finish at 40 seconds.

There are a number of things i would try to identify the area causing the problems. These will require editing the LILO kernel command line options.

The first thing i would do is boot to a root shell by-passing the init functionality.

You can do this by configuring LILO to boot with

```
init=/bin/bash
```

(i'm assuming you know how to do this because you said you edited them in the first post)

Take a note of how long that takes to boot. If it takes ages then i would be looking at the kernel or a driver maybe. Post back here if it takes a long time at this step.

Shutdown at this point with

```
/sbin/shutdown -h now
```

The second thing i would do is boot into single user mode. This will run the init scripts for the single user mode and no others. 

You can do this by editing the LILO and adding 

```
single
```

to the kernel boot line. If this stage takes ages then post back.

Shutdown at this point with

```
shutdown -h now
```

Thirdly i would boot into multiuser text mode. This will run all of the init script but will not start X etc. Post back if this is the stage where it's taking ages to boot. You should be able to do this from the recovery kernel (assuming you configured it).

If not you will need to edit LILO kernel boot options again and add this.

```
ro recovery nomodeset
```

Shutdown at this point with

```
sudo shutdown -h now
```

If all of the steps above are quick but the last one is slow then post back with that information.

If booting to a GUI (the windowed logon environment) is the step taking the time then post back this information.

Trying to identify where the problem step is will help reduce the areas to look at.

The fact that it's booting very slow and you had problems with GRUB is, itself, interesting.

1. Can you supply the make and model of the hard drive.
2. What filing system are you using on the drive ?
3. Is it slow (did you have any problems) when booting from a LiveCD/USB ?
4. Remove ALL cards and unplug all devices (DVD/CD/extra hard drives) from inside the machine, leaving only the graphics, memory and hard drive, and then boot. How long does this take to boot ? (If your not confident with this step then bypass it)
5. Have you ran a memory test from a LiceCD/USB ?

Kind regards

---

