---
title: "Sound won't work, as a consequence Totem won't start."
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by Tominator on 2006-09-20
The following is an error message I get when I click on the volume icon on the panel. I don't know how to configure the sound card or determine if I have the correct plugins. I have been to the device manager but could find no course of action to take there.The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu. Thanks for any and all help in advance. Tom

---

### Post by b_martinez on 2006-09-20
Open a terminal.
Type in (no '' marks or the stuff in brackets) 
'sudo dmesg |less'   [<-- the pipeline symbol is  usually found above the \ on US keyboards]
 Use the up/down arrow keys to navigate and look to see if your sound card was recognized. If not , post here. If so, I'll have to re-boot into Kubuntu to help further.
Bill

---

### Post by Tominator on 2006-09-20
sudo dmesg |less        Hey Bill thanks for trying to help. That is the command I used in terminal, tried it twice with the same non-result. I got absolutely nothing. The cursor drops to the left bottom corner and there is no output at all.

---

### Post by b_martinez on 2006-09-20
> **Tominator said:**
> sudo dmesg |less        Hey Bill thanks for trying to help. That is the command I used in terminal, tried it twice with the same non-result. I got absolutely nothing. The cursor drops to the left bottom corner and there is no output at all.

Nothing when you use the up arrow? Sometimes the message tails out. I do not know where it is, but there should be a boot.log. Maybe in /var/log/bootlog.txt?
As usual , I was wrong. The boot log is in 
/var/log/kern.log
So you do this
sudo kate /var/log/kern.log   
to see it. IF you have kate editor . If not, use nano, vi, vim,gedit ....
You should see what it has  discovered/mounted. Be warned, it is a loooooong list.
Bill

---

### Post by Arisna on 2006-09-20
Use simply ```
dmesg | less
```.  It creates a problem when the dmesg part is run as root and the less part isn't I think.

---

### Post by Tominator on 2006-09-20
ltomdaniels@ltomdaniels:~$ sudo kate /var/log/kern.log
Password:
sudo: kate: command not found
ltomdaniels@ltomdaniels:~$ nano, vi, vim,gedit
bash: nano,: command not found
ltomdaniels@ltomdaniels:~$

That did not help me I think, the above is what I got. Thanks, Tom

---

### Post by Arisna on 2006-09-20
See my above post.  Use the original command b_martinez suggested, but take out the "sudo."

Also, it is worth mentioning that if you are a GNOME user, which you probably are if you are using Totem, you likely would not have Kate, a KDE text editor, installed on your system.  Also, if you want to run vim, nano, gedit, etc., which are different text editors, you would run them individual.  Example:

```
username@hostname:~$ vim
```

Finally, if you are going to run a graphical program like Gedit, the basic GNOME text editor, you should use gksudo instead of sudo to run them as root, or else you could end up with some problems with X configuration files.  Example:

```
username@hostname:~$ gksudo gedit
```

Note that this is only if you want to run the program with root (administrator) privileges, which you should not unless it is necessary.  Please also note that vim and nano are command line editors, so running them with sudo is fine.

---

### Post by Tominator on 2006-09-20
Thanks Arisna, here is the output I got using your suggestion........
[17179569.184000] Linux version 2.6.15-27-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000000fffd8c0 (usable)
[17179569.184000]  BIOS-e820: 000000000fffd8c0 - 000000000fffff00 (ACPI data)
[17179569.184000]  BIOS-e820: 000000000fffff00 - 0000000010000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 255MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 65533
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 61437 pages, LIFO batch:15
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI 2.1 present.
[17179569.184000] ACPI: RSDP (v000 IBM                                   ) @ 0x000fdfe0
[17179569.184000] ACPI: RSDT (v001 IBM    CDTPWSNV 0x00001000 IBM  0x00000000) @:

---

### Post by b_martinez on 2006-09-20
Arisna uggests you try demsg |less as non-sudo. Might work. I am new enough at *buntu's to miss the obvious. LOL
 What desktop do you use? If Gnome, then you have gedit. If KDE then it's kedit. Not sure what is in XFCE. I always install nano. Easiest editor for the command line I've used.
Bill

p.s. gotta be in to work in 6 hours. Need to get some sleep. Sorry to abandon you.
B

---

### Post by Arisna on 2006-09-20
Alright, now we're really getting somewhere.  As a quick side note, the editor for XFCE is Mousepad, in case you were curious. :)

The "less" command lets you view text and scroll through it.  The output of dmesg takes up more than one screenfull of space, so you would need to scroll down to see the rest.  You can do that by hitting the "j" key.  Funny keymappings, yeah.  Corresponds to what you get in vi(m).

Anyway, in order to easily post all of the output of dmesg, use this command:

```
dmesg > ~/dmesg.txt
```

Now, fire up your file manager and you should see dmesg.txt sitting in your home folder.  Double click it to open it in that gedit program we've been talking about, copy everything in it, and paste it into a message here.  Apologies for not realizing earlier that it would be tough to copy it out from less. :(

---

### Post by Tominator on 2006-09-20
OK Arisna, thanks for all the help and the following is what I got...
[17179569.184000] Linux version 2.6.15-27-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000000fffd8c0 (usable)
[17179569.184000]  BIOS-e820: 000000000fffd8c0 - 000000000fffff00 (ACPI data)
[17179569.184000]  BIOS-e820: 000000000fffff00 - 0000000010000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 255MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 65533
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 61437 pages, LIFO batch:15
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI 2.1 present.
[17179569.184000] ACPI: RSDP (v000 IBM                                   ) @ 0x000fdfe0
[17179569.184000] ACPI: RSDT (v001 IBM    CDTPWSNV 0x00001000 IBM  0x00000000) @ 0x0ffffe80
[17179569.184000] ACPI: FADT (v001 IBM    CDTPWSNV 0x00001000 IBM  0x00000000) @ 0x0ffffe00
[17179569.184000] ACPI: DSDT (v001 IBM    CDTPWSNV 0x00001000 MSFT 0x01000007) @ 0x00000000
[17179569.184000] ACPI: BIOS age (1999) fails cutoff (2000), acpi=force is required to enable ACPI
[17179569.184000] ACPI: Disabling ACPI support
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 10000000:eec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (01201000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 1024 (order: 10, 16384 bytes)
[    0.000000] Detected 497.924 MHz processor.
[  123.326042] Using tsc for high-res timesource
[  123.327655] Console: colour VGA+ 80x25
[  123.328774] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[  123.329981] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[  123.362094] Memory: 249140k/262132k available (1976k kernel code, 12356k reserved, 606k data, 288k init, 0k highmem)
[  123.362109] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[  123.439063] Calibrating delay using timer specific routine.. 997.13 BogoMIPS (lpj=1994265)
[  123.439173] Security Framework v1.0.0 initialized
[  123.439204] SELinux:  Disabled at boot.
[  123.439253] Mount-cache hash table entries: 512
[  123.439569] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[  123.439596] CPU: After vendor identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[  123.439625] CPU: L1 I cache: 16K, L1 D cache: 16K
[  123.439635] CPU: L2 cache: 512K
[  123.439645] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[  123.439701] mtrr: v2.0 (20020519)
[  123.439717] CPU: Intel Pentium III (Katmai) stepping 03
[  123.439731] Enabling fast FPU save and restore... done.
[  123.439741] Enabling unmasked SIMD FPU exception support... done.
[  123.439754] Checking 'hlt' instruction... OK.
[  123.455663] checking if image is initramfs... it is
[  126.532040] Freeing initrd memory: 6617k freed
[  126.568400] NET: Registered protocol family 16
[  126.568498] EISA bus registered
[  126.569584] PCI: PCI BIOS revision 2.10 entry at 0xfd83c, last bus=1
[  126.569606] PCI: Using configuration type 1
[  126.570991] ACPI: Subsystem revision 20051216
[  126.571001] ACPI: Interpreter disabled.
[  126.571012] Linux Plug and Play Support v0.97 (c) Adam Belay
[  126.571036] pnp: PnP ACPI: disabled
[  126.571048] PnPBIOS: Scanning system for PnP BIOS support...
[  126.571127] PnPBIOS: Found PnP BIOS installation structure at 0xc00fde50
[  126.571141] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x59fe, dseg 0xf0000
[  126.574788] PnPBIOS: 21 nodes reported by PnP BIOS; 21 recorded by driver
[  126.574834] PCI: Probing PCI hardware
[  126.574846] PCI: Probing PCI hardware (bus 00)
[  126.575334] PCI quirk: region fd00-fd3f claimed by PIIX4 ACPI
[  126.575348] PCI quirk: region fe00-fe0f claimed by PIIX4 SMB
[  126.575733] Boot video device is 0000:01:01.0
[  126.577147] PCI: Using IRQ router PIIX/ICH [8086/7110] at 0000:00:02.0
[  126.583342] pnp: 00:0e: ioport range 0x370-0x371 has been reserved
[  126.583356] pnp: 00:0e: ioport range 0x4d0-0x4d1 has been reserved
[  126.583373] pnp: 00:0f: ioport range 0x290-0x297 has been reserved
[  126.583390] pnp: 00:10: ioport range 0xfd00-0xfd3f has been reserved
[  126.583402] pnp: 00:10: ioport range 0xfe00-0xfe0f has been reserved
[  126.584305] PCI: Bridge: 0000:00:01.0
[  126.584315]   IO window: disabled.
[  126.584328]   MEM window: f4000000-f7ffffff
[  126.584340]   PREFETCH window: 20000000-200fffff
[  126.586349] audit: initializing netlink socket (disabled)
[  126.586380] audit(1158768098.040:1): initialized
[  126.586737] VFS: Disk quotas dquot_6.5.1
[  126.586813] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[  126.586997] Initializing Cryptographic API
[  126.587013] io scheduler noop registered
[  126.587035] io scheduler anticipatory registered
[  126.587052] io scheduler deadline registered
[  126.587096] io scheduler cfq registered
[  126.587109] Limiting direct PCI/PCI transfers.
[  126.587647] isapnp: Scanning for PnP cards...
[  126.687089] isapnp: Card 'Crystal Audio'
[  126.687101] isapnp: 1 Plug & Play card detected total
[  126.762843] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[  126.764249] serio: i8042 AUX port at 0x60,0x64 irq 12
[  126.764476] serio: i8042 KBD port at 0x60,0x64 irq 1
[  126.764666] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[  126.764944] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[  126.765205] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[  126.774107] 00:12: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[  126.774631] 00:13: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[  126.776992] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[  126.777193] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[  126.777208] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[  126.777683] mice: PS/2 mouse device common for all mice
[  126.778346] EISA: Probing bus 0 at eisa.0
[  126.778405] Cannot allocate resource for EISA slot 7
[  126.778420] EISA: Detected 0 cards.
[  126.778548] NET: Registered protocol family 2
[  126.800209] input: AT Translated Set 2 keyboard as /class/input/input0
[  126.821950] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[  126.822434] TCP established hash table entries: 16384 (order: 4, 65536 bytes)
[  126.822718] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[  126.823010] TCP: Hash tables configured (established 16384 bind 16384)
[  126.823021] TCP reno registered
[  126.823282] TCP bic registered
[  126.823309] NET: Registered protocol family 1
[  126.823329] NET: Registered protocol family 8
[  126.823338] NET: Registered protocol family 20
[  126.823400] Using IPI Shortcut mode
[  126.823516] Freeing unused kernel memory: 288k freed
[  127.020365] vga16fb: initializing
[  127.020385] vga16fb: mapped to 0xc00a0000
[  127.143832] Console: switching to colour frame buffer device 80x25
[  127.143851] fb0: VGA16 VGA frame buffer device
[  128.282239] Capability LSM initialized
[  129.953459] PIIX4: IDE controller at PCI slot 0000:00:02.1
[  129.953500] PIIX4: chipset revision 1
[  129.953509] PIIX4: not 100% native mode: will probe irqs later
[  129.953533]     ide0: BM-DMA at 0xfff0-0xfff7, BIOS settings: hda:DMA, hdb:pio
[  129.953571]     ide1: BM-DMA at 0xfff8-0xffff, BIOS settings: hdc:DMA, hdd:pio
[  129.953598] Probing IDE interface ide0...
[  130.240613] hda: WDC WD136AA, ATA DISK drive
[  130.577286] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[  130.577752] Probing IDE interface ide1...
[  130.976330] hdc: CRD-8400B, ATAPI CD/DVD-ROM drive
[  131.647965] hdc: Disabling (U)DMA for CRD-8400B (blacklisted)
[  131.648023] ide1 at 0x170-0x177,0x376 on irq 15
[  131.673239] hda: max request size: 128KiB
[  131.706063] hda: 26564832 sectors (13601 MB) w/2048KiB Cache, CHS=26354/16/63, UDMA(33)
[  131.706090] hda: cache flushes not supported
[  131.706553]  hda: hda1 hda2 < hda5 >
[  131.771357] hdc: ATAPI 40X CD-ROM drive, 128kB Cache
[  131.771384] Uniform CD-ROM driver Revision: 3.20
[  132.138461] usbcore: registered new driver usbfs
[  132.139336] usbcore: registered new driver hub
[  132.147137] USB Universal Host Controller Interface driver v2.3
[  132.148093] PCI: Found IRQ 11 for device 0000:00:02.2
[  132.148119] PCI: Sharing IRQ 11 with 0000:00:03.0
[  132.148151] uhci_hcd 0000:00:02.2: UHCI Host Controller
[  132.149160] uhci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 1
[  132.149189] uhci_hcd 0000:00:02.2: irq 11, io base 0x0000ff00
[  132.150163] hub 1-0:1.0: USB hub found
[  132.150203] hub 1-0:1.0: 2 ports detected
[  132.370495] Attempting manual resume
[  132.417920] kjournald starting.  Commit interval 5 seconds
[  132.417960] EXT3-fs: mounted filesystem with ordered data mode.
[  152.320635] Linux agpgart interface v0.101 (c) Dave Jones
[  152.362863] agpgart: Detected an Intel 440BX Chipset.
[  152.370446] agpgart: AGP aperture is 64M @ 0xec000000
[  152.394060] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  152.413590] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  152.466338] piix4_smbus 0000:00:02.3: Found 0000:00:02.3 device
[  152.466357] piix4_smbus 0000:00:02.3: IBM Laptop detected; this module may corrupt your serial eeprom! Refusing to load module!
[  152.466373] piix4_smbus: probe of 0000:00:02.3 failed with error -1
[  153.418619] ieee80211_crypt: registered algorithm 'NULL'
[  153.432431] ieee80211: 802.11 data/management/control stack, git-1.1.7
[  153.432447] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[  153.506938] bcm43xx driver
[  153.507272] PCI: Found IRQ 10 for device 0000:00:10.0
[  153.528115] e100: Intel(R) PRO/100 Network Driver, 3.4.14-k4-NAPI
[  153.528130] e100: Copyright(c) 1999-2005 Intel Corporation
[  153.528294] PCI: Found IRQ 11 for device 0000:00:03.0
[  153.528316] PCI: Sharing IRQ 11 with 0000:00:02.2
[  153.551596] e100: eth1: e100_probe: addr 0xf3dff000, irq 11, MAC addr 00:06:29:B5:64:83
[  154.012717] Real Time Clock Driver v1.12
[  154.076040] input: ImPS/2 Logitech Wheel Mouse as /class/input/input1
[  154.496018] input: PC Speaker as /class/input/input2
[  154.878863] Floppy drive(s): fd0 is 1.44M
[  154.894821] FDC 0 is a post-1991 82077
[  155.777784] parport: PnPBIOS parport detected.
[  155.777868] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[  156.498243] ts: Compaq touchscreen protocol output
[  157.258385] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[  157.623529] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
[  157.634258] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
[  158.091289] lp0: using parport0 (interrupt-driven).
[  158.321473] NET: Registered protocol family 17
[  158.331483] Adding 570268k swap on /dev/hda5.  Priority:-1 extents:1 across:570268k
[  158.522334] EXT3 FS on hda1, internal journal
[  158.994924] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[  158.994940] md: bitmap version 4.39
[  159.971376] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[  160.844521] cdrom: open failed.
[  162.338001] NET: Registered protocol family 10
[  162.338424] lo: Disabled Privacy Extensions
[  162.338986] IPv6 over IPv4 tunneling driver
[  172.980171] eth0: no IPv6 routers present
[  178.246008] ppdev: user-space parallel port driver
[  178.738186] IBM machine detected. Enabling interrupts during APM calls.
[  178.738868] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  182.300602] hdc: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
[  182.300650] hdc: drive_cmd: error=0x04 { AbortedCommand }
[  182.300661] ide: failed opcode was: 0xec
[  187.142512] Non-volatile memory driver v1.2
[  187.164771] input: /usr/sbin/thinkpad-keys as /class/input/input3
[  187.922968] Bluetooth: Core ver 2.8
[  187.922985] NET: Registered protocol family 31
[  187.922993] Bluetooth: HCI device and connection manager initialized
[  187.923022] Bluetooth: HCI socket layer initialized
[  187.998078] Bluetooth: L2CAP ver 2.8
[  187.998093] Bluetooth: L2CAP socket layer initialized
[  188.013696] Bluetooth: RFCOMM socket layer initialized
[  188.013736] Bluetooth: RFCOMM TTY layer initialized
[  188.013744] Bluetooth: RFCOMM ver 1.7

---

### Post by Tominator on 2006-09-20
duplicate entry deleted

---

### Post by Arisna on 2006-09-21
Sorry for disappearing there for a while.  I have poked through that dmesg log and noted the following key lines:

```
[ 126.687089] isapnp: Card 'Crystal Audio'
 [ 126.687101] isapnp: 1 Plug & Play card detected total
```

Further poking around on the Internet revealed these pages:

[http://eclipse.byelex.net/eclipse/bss.html](http://eclipse.byelex.net/eclipse/bss.html)
[https://help.ubuntu.com/community/HowToSetupSoundCards](https://help.ubuntu.com/community/HowToSetupSoundCards)

I can tell from the dmesg output that you're on an IBM laptop, and chances are good that your sound card has a CS4232 chipset based on what I read at the above links, which is likely being recognized incorrectly as a CS4610.  To check, run the following command and see what it tells you about your sound card:

```
sudo lspci -v
```

You'll need to type your password in and hit enter.  Nothing will be echoed on the screen when you type the password, but have faith--the terminal **is** accepting your input.

If this is the sound card you have, we'll be following the instructions from the first link from here on out, except no kernel recompile and a few other minor differences.  The module you would need to load in Ubuntu would be "snd-cs4232", but now I'm getting ahead of myself. ;)

---

### Post by Tominator on 2006-09-21
Please don't apologize for helping me too slowly, lol. All help is greatly appreciated. I will do as you suggested. I have spent the past couple of hours learning some basic linux commands. I started another thread and got some interesting feedback concerning the proc directory. So far I havn't been able to act on the advice, damned ignorance, lol. Anyway I would appreciate if you would check it out and let me know what you think.
Regards, tom
here is the title of that thread,,
 dmesg output, is my sound card configured?

---

### Post by Tominator on 2006-09-21
P.S. it is an I.B.M.but it is a desktop model if that makes a difference.. Thanks

---

### Post by Tominator on 2006-09-21
ltomdaniels@ltomdaniels:~$ sudo lspci -v
Password:
0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
        Flags: bus master, medium devsel, latency 32
        Memory at ec000000 (32-bit, prefetchable) [size=64M]
        Capabilities: [a0] AGP version 1.0

0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        Memory behind bridge: f4000000-f7ffffff
        Prefetchable memory behind bridge: 20000000-200fffff

0000:00:02.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
        Flags: bus master, medium devsel, latency 0

0000:00:02.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
        Flags: bus master, medium devsel, latency 32
        I/O ports at fff0 [size=16]

0000:00:02.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])
        Flags: bus master, medium devsel, latency 48, IRQ 11
        I/O ports at ff00 [size=32]

0000:00:02.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
        Flags: medium devsel, IRQ 9

0000:00:03.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 05)
        Subsystem: IBM: Unknown device 00d7
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at f3dff000 (32-bit, prefetchable) [size=4K]
        I/O ports at 7c60 [size=32]
        Memory at f3f00000 (32-bit, non-prefetchable) [size=1M]
        Capabilities: [dc] Power Management version 1

0000:00:10.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
        Subsystem: Motorola: Unknown device 7010
        Flags: bus master, fast devsel, latency 32, IRQ 10
        Memory at f3efe000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: [40] Power Management version 2

0000:01:01.0 VGA compatible controller: S3 Inc. Trio 64 3D (rev 01) (prog-if 00 [VGA])
        Subsystem: IBM Integrated Trio3D
        Flags: bus master, medium devsel, latency 32, IRQ 9
        Memory at f4000000 (32-bit, non-prefetchable) [size=64M]
        Expansion ROM at 20000000 [disabled] [size=64K]
        Capabilities: [44] Power Management version 1

ltomdaniels@ltomdaniels:~$ sudo ls
That's what I got, what's it mean, lol. Thanks, Tom

---

### Post by Arisna on 2006-09-21
With that other thread, we're into topics about proc that I am unfamiliar with myself.  For anyone who comes across this in a few years, the other thread is here:

[http://www.ubuntuforums.org/showthread.php?t=262160](http://www.ubuntuforums.org/showthread.php?t=262160)

Let's move the discussion there now.

---

