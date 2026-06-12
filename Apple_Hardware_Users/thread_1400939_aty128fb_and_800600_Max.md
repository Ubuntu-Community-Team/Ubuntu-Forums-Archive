---
title: "aty128fb and 800*600 Max"
date: 2010-02-07
forum: Apple Hardware Users
---

### Post by Bq32 on 2010-02-07
As a side note, I couldn't find any answers to these two, except for iMac, and even then, they didn't seem to apply.
------
I had originally Mac OS 9 and OS X 10.3.9 "Panther" on this hard drive, so I installed Xubuntu 9.04 on it (formatting everything on the HDA, but I made a half of the Hard disk for Mac to re-install). Upon install, I had to use "live video=ofonly", thinking it'd fix why my monitor shut down.

When I boot into Xubuntu, I don't see a splash, I see at first something saying how aty128fb (Figuring that's the video card) has "Invalid ROM Contents", or something as such (it goes too quick for me to see all of what it says). After that, my monitor generates a bouncing red box saying "Out of Range" for a minute or two, before going to an 800px*600px screen. Everything runs okay, and I set the "Driver" stat in xorg.conf to "r128", but I still get nothing better than 800px*600px@60Hz.

Would there be anything else to fix this? Would updating to 9.10 fix this?

I have a Power Mac G4 AGP with an ATI Rage 128 (Pro?) with 16MB VRAM. When I had Panther running, I could use 1280px*1024px as my res, but I'm not sure if it'll work with Xubuntu.

---

### Post by linuxopjemac on 2010-02-08
You need to adapt the Xorg.conf file. This file is found in /etc/X11.

```
sudo mv /etc/X11/Xorg.conf /etc/X11/Xorg.conf.bak
```

(we gave the real conf file a backup name for later)

```
sudo nano /etc/X11/Xorg.conf
```

now you enter an editor, paste the following lines in there, then ctrl-X to exit and "y" to write the  file.

then restart X:

```
sudo gdm restart
```

The new Xorg.conf file:

```

Section "ServerLayout"
   Identifier     "X.org Configured"
   Screen      0  "Screen0" 0 0
   InputDevice    "Mouse0" "CorePointer"
   InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
FontPath "/usr/share/fonts/X11/misc"
FontPath "/usr/share/fonts/X11/100dpi"
FontPath "/usr/share/fonts/X11/75dpi"
FontPath "/usr/share/fonts/X11/Type1"
# paths to defoma fonts
FontPath "/var/lib//defoma/x-ttcidfont-conf.d/dirs/TrueType"
FontPath "/var/lib//defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
   Load  "record"
   Load  "glx"
   Load  "extmod"
   Load  "xtrap"
   Load  "GLcore"
   Load  "dri"
   Load  "dbe"
EndSection

Section "InputDevice"
   Identifier  "Keyboard0"
   Driver      "kbd"
EndSection

Section "InputDevice"
   Identifier  "Mouse0"
   Driver      "mouse"
   Option       "Protocol" "auto"
   Option       "Device" "/dev/input/mice"
   Option       "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
   Identifier   "Monitor0"
   VendorName   "Monitor Vendor"
   ModelName    "Monitor Model"
   HorizSync       30 - 121
   VertRefresh     48 - 160
EndSection


EndSection

Section "Device"
   Identifier  "Card0"
   Driver      "ati"
   VendorName  "ATI Technologies Inc"
   BoardName   "Rage 128 PF/PRO AGP 4x TMDS"
   BusID       "PCI:0:16:0"
EndSection

Section "Screen"
   Identifier "Screen0"
   Device     "Card0"
   Monitor    "Monitor0"
   SubSection "Display"
      Viewport   0 0
      Depth     24
   EndSubSection
EndSection
```


Please let us know if it works,.

---

### Post by Bq32 on 2010-02-08
Nope, it still won't work. Now, for some reason, I have to boot into xterm (I somehow unknowingly installed 9.10[?]), and then use "sudo xfce4-session" to log in, and even then, it looks like the default XFCE, not Ubuntu-style. Is this somehow with X11? Or GDM?

When I boot the computer, I go through yaboot, and the little XFCE mouse appears (which is better, considering with 9.04 it said "OUT OF RANGE"), and it boots to GDM. I click my name, and enter in my password,but when "Session" is "XFCE Session", it tries to load but almost immediately resets GDM. It also will automatically choose xterm as the session afterwards, most times.

---

### Post by linuxopjemac on 2010-02-08
you have to edit these things witin a terminal (Applications -> Accessories -> terminal)

---

### Post by Bq32 on 2010-02-08
> **linuxopjemac said:**
> you have to edit these things witin a terminal (Applications -> Acsessories -> terminal)

And I have done so. I've used XFCE-term, by going to xterm and typing:
```
% sudo xfce4-session
```

and then loading into my apps, including XFCE-term.

---

### Post by linuxopjemac on 2010-02-08
so the resolution will not keep in the xfce session, is that what you are saying ? What are the allowable resolutions for your screen ?

---

### Post by Bq32 on 2010-02-08
> **linuxopjemac said:**
> so the resolution will not keep in the xfce session, is that what you are saying ? What are the allowable resolutions for your screen ?

In xrandr and XFCE Control Panel/Display Panel, all I can get is 800x600 and 640x480, 56Hz and 60Hz. On Mac OS X, I can get 1280x1024@75Hz, though.

---

### Post by linuxopjemac on 2010-02-08
try this link on my site
[http://mac.linux.be/content/setting-xorgconf-manually-xrandr#3](http://mac.linux.be/content/setting-xorgconf-manually-xrandr#3)

---

### Post by Bq32 on 2010-02-08
> **linuxopjemac said:**
> try this link on my site
[http://mac.linux.be/content/setting-xorgconf-manually-xrandr#3](http://mac.linux.be/content/setting-xorgconf-manually-xrandr#3)

I can't get that working with X.Org, I'll try restarting again, but it can't find VGA-0, VGA-1, or VGA (in xrandr --addmode)

---

### Post by Bq32 on 2010-02-09
So I figured out to fix the yaboot.conf, and add "video=ofonly", but now: a) I need to use the "fbdev" driver, and b) All color is in 8-bit (256 colors). Is there a way to fix either? (Also, AllowFbDev breaks the driver, too)

---

### Post by linuxopjemac on 2010-02-10
read some xorg.conf files [here ]("http://mac.linux.be/content/cross-distribution-issues")for inspiration.

---

### Post by Bq32 on 2010-02-10
> **linuxopjemac said:**
> read some xorg.conf files [here]("http://mac.linux.be/content/cross-distribution-issues") for inspiration.

The only thing I saw there that might've helped was "DefaultDepth", but when I add that xorg.conf file, it (the X Server) shuts down, saying FbDev found an incorrect mode. If I have to post my xorg.conf file here, I can.

---

### Post by linuxopjemac on 2010-02-10
do it pls

---

### Post by Bq32 on 2010-02-10
> **linuxopjemac said:**
> do it pls

This is essentially it, right now, because it seems that the FbDev driver is very sensitive:

```
Section "Device"
	Identifier	"ATI Rage 128"
	Driver		"fbdev"
	BusID		"PCI:6:3:0"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"ATI Rage 128"
EndSection

```

Also, for dmesg (won't attach):
```
[    0.000000] Using PowerMac machine description
[    0.000000] Total memory = 768MB; using 2048kB for hash table (at cfe00000)
[    0.000000] Linux version 2.6.28-6-powerpc (buildd@adare) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #20-Ubuntu Fri Apr 17 08:30:40 UTC 2009 (Ubuntu 2.6.28-6.20-powerpc)
[    0.000000] Found initrd at 0xc1a00000:0xc227c000
[    0.000000] Found UniNorth memory controller & host bridge @ 0xf8000000 revision: 0x07
[    0.000000] Mapped at 0xff7c0000
[    0.000000] Found a Keylargo mac-io controller, rev: 2, mapped at 0xff740000
[    0.000000] Processor NAP mode on idle enabled.
[    0.000000] PowerMac motherboard: PowerMac G4 AGP Graphics
[    0.000000] console [udbg0] enabled
[    0.000000] Found UniNorth PCI host bridge at 0x00000000f0000000. Firmware bus number: 0->0
[    0.000000] PCI host bridge /pci@f0000000  ranges:
[    0.000000]  MEM 0x00000000f1000000..0x00000000f1ffffff -> 0x00000000f1000000 
[    0.000000]   IO 0x00000000f0000000..0x00000000f07fffff -> 0x0000000000000000
[    0.000000]  MEM 0x0000000090000000..0x000000009fffffff -> 0x0000000090000000 
[    0.000000] Found UniNorth PCI host bridge at 0x00000000f2000000. Firmware bus number: 0->1
[    0.000000] PCI host bridge /pci@f2000000 (primary) ranges:
[    0.000000]  MEM 0x00000000f3000000..0x00000000f3ffffff -> 0x00000000f3000000 
[    0.000000]   IO 0x00000000f2000000..0x00000000f27fffff -> 0x0000000000000000
[    0.000000]  MEM 0x0000000080000000..0x000000008fffffff -> 0x0000000080000000 
[    0.000000] Found UniNorth PCI host bridge at 0x00000000f4000000. Firmware bus number: 0->0
[    0.000000] PCI host bridge /pci@f4000000  ranges:
[    0.000000]  MEM 0x00000000f5000000..0x00000000f5ffffff -> 0x00000000f5000000 
[    0.000000]   IO 0x00000000f4000000..0x00000000f47fffff -> 0x0000000000000000
[    0.000000] via-pmu: Server Mode is disabled
[    0.000000] PMU driver v2 initialized for Core99, firmware: 0c
[    0.000000] nvram: Checking bank 0...
[    0.000000] nvram: gen0=380, gen1=381
[    0.000000] nvram: Active bank is: 1
[    0.000000] nvram: OF partition at 0x210
[    0.000000] nvram: XP partition at 0x1220
[    0.000000] nvram: NR partition at 0x1320
[    0.000000] Top of RAM: 0x30000000, Total RAM: 0x30000000
[    0.000000] Memory hole size: 0MB
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00030000
[    0.000000]   Normal   0x00030000 -> 0x00030000
[    0.000000]   HighMem  0x00030000 -> 0x00030000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00030000
[    0.000000] On node 0 totalpages: 196608
[    0.000000] free_area_init_node: node 0, pgdat c045c5fc, node_mem_map c04d0000
[    0.000000]   DMA zone: 1536 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 195072 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 195072
[    0.000000] Kernel command line: root=/dev/hda4 ro quiet splash video=ofonly 
[    0.000000] mpic: Setting up MPIC " MPIC 1   " version 1.2 at 80040000, max 4 CPUs
[    0.000000] mpic: ISU size: 64, shift: 6, mask: 3f
[    0.000000] mpic: Initializing for 64 sources
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] GMT Delta read from XPRAM: -240 minutes, DST: on
[    0.000000] time_init: decrementer frequency = 24.907667 MHz
[    0.000000] time_init: processor frequency   = 400.000000 MHz
[    0.000000] clocksource: timebase mult[a097d6d] shift[22] registered
[    0.000000] clockevent: decrementer mult[660] shift[16] cpu[0]
[    0.000151] Console: colour dummy device 80x25
[    0.000165] console handover: boot [udbg0] -> real [tty0]
[    0.001460] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.003629] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.078874] High memory: 0k
[    0.078887] Memory: 763008k/786432k available (4296k kernel code, 23008k reserved, 176k data, 360k bss, 212k init)
[    0.079029] SLUB: Genslabs=12, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.079051] Calibrating delay loop... 49.66 BogoMIPS (lpj=99328)
[    0.156420] Security Framework initialized
[    0.156452] SELinux:  Disabled at boot.
[    0.156552] AppArmor: AppArmor initialized
[    0.156578] Mount-cache hash table entries: 512
[    0.157083] device-tree: Duplicate name in /cpus/PowerPC,G4@0, renamed to "l2-cache#1"
[    0.159999] Initializing cgroup subsys ns
[    0.160012] Initializing cgroup subsys freezer
[    0.160776] net_namespace: 752 bytes
[    0.160905] regulator: core version 0.5
[    0.161008] NET: Registered protocol family 16
[    0.161680] KeyWest i2c @0xf8001003 irq 42 /uni-n@f8000000/i2c@f8001000
[    0.161696]  channel 0 bus <multibus>
[    0.161704]  channel 1 bus <multibus>
[    0.161757] KeyWest i2c @0x80018000 irq 26 /pci@f2000000/pci-bridge@d/mac-io@7/i2c@18000
[    0.161768]  channel 0 bus <multibus>
[    0.161794] PMU i2c /pci@f2000000/pci-bridge@d/mac-io@7/via-pmu@16000
[    0.161804]  channel 1 bus <multibus>
[    0.161811]  channel 2 bus <multibus>
[    0.162041] PCI: Probing PCI hardware
[    0.162263] pci 0000:00:10.0: reg 10 32bit mmio: [0x94000000-0x97ffffff]
[    0.162280] pci 0000:00:10.0: reg 14 io port: [0x400-0x4ff]
[    0.162294] pci 0000:00:10.0: reg 18 32bit mmio: [0x90000000-0x90003fff]
[    0.162320] pci 0000:00:10.0: reg 30 32bit mmio: [0x90020000-0x9003ffff]
[    0.162344] pci 0000:00:10.0: supports D1
[    0.162836] pci 0001:11:04.0: reg 10 io port: [0x1000-0x10ff]
[    0.162852] pci 0001:11:04.0: reg 14 32bit mmio: [0x80083000-0x80083fff]
[    0.162913] pci 0001:11:07.0: reg 10 32bit mmio: [0x80000000-0x8007ffff]
[    0.162970] pci 0001:11:08.0: reg 10 32bit mmio: [0x80082000-0x80082fff]
[    0.163041] pci 0001:11:09.0: reg 10 32bit mmio: [0x80081000-0x80081fff]
[    0.163114] pci 0001:11:0a.0: reg 10 32bit mmio: [0x80080000-0x800807ff]
[    0.163129] pci 0001:11:0a.0: reg 14 32bit mmio: [0x80084000-0x80087fff]
[    0.163168] pci 0001:11:0a.0: supports D2
[    0.163177] pci 0001:11:0a.0: PME# supported from D2 D3hot
[    0.163189] pci 0001:11:0a.0: PME# disabled
[    0.163237] pci 0001:10:0d.0: bridge io port: [0x1000-0x1fff]
[    0.163250] pci 0001:10:0d.0: bridge 32bit mmio: [0x80000000-0x800fffff]
[    0.164150] pci 0002:21:0f.0: reg 10 32bit mmio: [0xf5200000-0xf53fffff]
[    0.164184] pci 0002:21:0f.0: reg 30 32bit mmio: [0xf5000000-0xf50fffff]
[    0.164610] pci 0001:10:0d.0: PCI bridge, secondary bus 0001:11
[    0.164624] pci 0001:10:0d.0:   IO window: 0x1000-0x1fff
[    0.164637] pci 0001:10:0d.0:   MEM window: 0x80000000-0x800fffff
[    0.164648] pci 0001:10:0d.0:   PREFETCH window: disabled
[    0.164682] bus: 00 index 0 io port: [0x802000-0x1001fff]
[    0.164693] bus: 00 index 1 mmio: [0xf1000000-0xf1ffffff]
[    0.164703] bus: 00 index 2 mmio: [0x90000000-0x9fffffff]
[    0.164713] bus: 10 index 0 io port: [0x00-0x7fffff]
[    0.164723] bus: 10 index 1 mmio: [0xf3000000-0xf3ffffff]
[    0.164733] bus: 10 index 2 mmio: [0x80000000-0x8fffffff]
[    0.164743] bus: 11 index 0 io port: [0x1000-0x1fff]
[    0.164753] bus: 11 index 1 mmio: [0x80000000-0x800fffff]
[    0.164763] bus: 11 index 2 mmio: [0x0-0x0]
[    0.164771] bus: 11 index 3 mmio: [0x0-0x0]
[    0.164781] bus: 21 index 0 io port: [0xff7fe000-0xffffdfff]
[    0.164791] bus: 21 index 1 mmio: [0xf5000000-0xf5ffffff]
[    0.167183] usbcore: registered new interface driver usbfs
[    0.167255] usbcore: registered new interface driver hub
[    0.167368] usbcore: registered new device driver usb
[    0.176477] NET: Registered protocol family 8
[    0.176486] NET: Registered protocol family 20
[    0.176653] AppArmor: AppArmor Filesystem Enabled
[    0.177277] NET: Registered protocol family 2
[    0.180491] Switched to high resolution mode on CPU 0
[    0.212556] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.212930] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.215463] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[    0.216293] TCP: Hash tables configured (established 131072 bind 65536)
[    0.216304] TCP reno registered
[    0.224724] NET: Registered protocol family 1
[    0.225247] checking if image is initramfs... it is
[    3.037747] Freeing initrd memory: 8688k freed
[    3.040141] Thermal assist unit using timers, shrink_timer: 500 jiffies
[    3.040880] audit: initializing netlink socket (disabled)
[    3.040942] type=2000 audit(1265820853.040:1): initialized
[    3.067527] VFS: Disk quotas dquot_6.5.1
[    3.067583] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    3.067882] fuse init (API version 7.10)
[    3.068245] msgmni has been set to 1508
[    3.068897] alg: No test for stdrng (krng)
[    3.068952] io scheduler noop registered
[    3.068961] io scheduler anticipatory registered
[    3.068969] io scheduler deadline registered
[    3.069029] io scheduler cfq registered (default)
[    3.069549] Using unsupported 1280x1024 ATY,Rage128Ps at 94008000, depth=8, pitch=1280
[    3.097249] Console: switching to colour frame buffer device 160x64
[    3.123900] fb0: Open Firmware frame buffer device on /pci@f0000000/ATY,Rage128Ps@10
[    3.127957] Generic non-volatile memory driver v1.1
[    3.130625] brd: module loaded
[    3.130799] Fixed MDIO Bus: probed
[    3.130916] MacIO PCI driver attached to Keylargo chipset
[    3.133339] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    3.133769] Uniform Multi-Platform E-IDE driver
[    3.134148] adb: starting probe task...
[    3.134170] adb: finished probe task...
[    4.152484] ide-pmac: Found Apple KeyLargo ATA-4 controller (macio), bus ID 2, irq 19
[    4.152525] Probing IDE interface ide0...
[    4.440781] hda: ST320413A, ATA DISK drive
[    4.720779] hdb: Maxtor 51024U2, ATA DISK drive
[    4.776592] hda: host max PIO4 wanted PIO255(auto-tune) selected PIO4
[    4.776707] hda: UDMA/66 mode selected
[    4.776798] hdb: host max PIO4 wanted PIO255(auto-tune) selected PIO4
[    4.776982] hdb: UDMA/66 mode selected
[    4.777223] ide0 at 0xf101c000-0xf101c070,0xf101c160 on irq 19
[    5.796482] ide-pmac: Found Apple KeyLargo ATA-3 controller (macio), bus ID 0, irq 20
[    5.796507] Probing IDE interface ide1...
[    6.196681] hdc: MATSHITADVD-ROM SR-8585, ATAPI CD/DVD-ROM drive
[    6.532572] hdc: host max PIO4 wanted PIO255(auto-tune) selected PIO4
[    6.532667] hdc: MWDMA2 mode selected
[    6.532791] ide1 at 0xf1024000-0xf1024070,0xf1024160 on irq 20
[    7.552482] ide-pmac: Found Apple KeyLargo ATA-3 controller (macio), bus ID 1, irq 22
[    7.552511] Probing IDE interface ide2...
[    8.120614] ide2 at 0xf102c000-0xf102c070,0xf102c160 on irq 22
[    8.120822] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    8.120922] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    8.121003] ohci_hcd 0001:11:08.0: enabling device (0000 -> 0002)
[    8.121033] ohci_hcd 0001:11:08.0: OHCI Host Controller
[    8.121258] ohci_hcd 0001:11:08.0: new USB bus registered, assigned bus number 1
[    8.121320] ohci_hcd 0001:11:08.0: irq 27, io mem 0x80082000
[    8.196084] usb usb1: configuration #1 chosen from 1 choice
[    8.196208] hub 1-0:1.0: USB hub found
[    8.196250] hub 1-0:1.0: 2 ports detected
[    8.196712] ohci_hcd 0001:11:09.0: enabling device (0000 -> 0002)
[    8.196739] ohci_hcd 0001:11:09.0: OHCI Host Controller
[    8.196945] ohci_hcd 0001:11:09.0: new USB bus registered, assigned bus number 2
[    8.197002] ohci_hcd 0001:11:09.0: irq 28, io mem 0x80081000
[    8.272003] usb usb2: configuration #1 chosen from 1 choice
[    8.272111] hub 2-0:1.0: USB hub found
[    8.272144] hub 2-0:1.0: 2 ports detected
[    8.272516] uhci_hcd: USB Universal Host Controller Interface driver
[    8.272770] usbcore: registered new interface driver libusual
[    8.284600] mice: PS/2 mouse device common for all mice
[    8.284838] platform ppc-rtc.0: rtc core: registered ppc_md as rtc0
[    8.284947] PowerMac i2c bus pmu 2 registered
[    8.285020] PowerMac i2c bus pmu 1 registered
[    8.285093] PowerMac i2c bus mac-io 0 registered
[    8.285172] PowerMac i2c bus uni-n 1 registered
[    8.285262] PowerMac i2c bus uni-n 0 registered
[    8.285773] TCP cubic registered
[    8.286149] registered taskstats version 1
[    8.286656] input: PMU as /devices/virtual/input/input1
[    8.296500] /build/buildd/linux-ports-2.6.28/drivers/rtc/hctosys.c: unable to open rtc device (y)
[    8.296541] Freeing unused kernel memory: 212k init
[    8.644557] usb 2-1: new full speed USB device using ohci_hcd and address 2
[    8.851839] usb 2-1: configuration #1 chosen from 1 choice
[    8.853663] hub 2-1:1.0: USB hub found
[    8.855538] hub 2-1:1.0: 3 ports detected
[    9.157564] usb 2-1.1: new low speed USB device using ohci_hcd and address 3
[    9.273874] usb 2-1.1: configuration #1 chosen from 1 choice
[    9.359896] usb 2-1.3: new low speed USB device using ohci_hcd and address 4
[    9.473884] usb 2-1.3: configuration #1 chosen from 1 choice
[    9.802689] ide-gd driver 1.18
[    9.816362] sungem.c:v0.98 8/24/03 David S. Miller (davem@redhat.com)
[    9.837150] SCSI subsystem initialized
[    9.837228] hda: max request size: 128KiB
[    9.837239] hda: 40011300 sectors (20485 MB) w/2048KiB Cache, CHS=39693/16/63
[    9.837253] hda: cache flushes not supported
[    9.837427]  hda: [mac] hda1 hda2 hda3 hda4 hda5 hda6
[    9.871610] hdb: max request size: 128KiB
[    9.882979] hdb: 20010816 sectors (10245 MB) w/2048KiB Cache, CHS=19852/16/63
[    9.883004] hdb: cache flushes not supported
[    9.883198]  hdb: [mac] hdb1 hdb2 hdb3 hdb4 hdb5 hdb6
[    9.914282] PHY ID: 406212, addr: 0
[    9.915073] eth0: Sun GEM (PCI) 10/100/1000BaseT Ethernet 00:30:65:76:59:96
[    9.915084] eth0: Found BCM5201 PHY
[    9.922516] ide-cd driver 5.00
[    9.953672] ide-cd: hdc: ATAPI 32X DVD-ROM drive, 512kB Cache
[    9.953697] Uniform CD-ROM driver Revision: 3.20
[    9.962920] aic7xxx 0001:11:04.0: enabling device (0014 -> 0017)
[   10.081238] usbcore: registered new interface driver hiddev
[   10.088105] input: Mitsumi Electric Apple USB Keyboard as /devices/pci0001:10/0001:10:0d.0/0001:11:09.0/usb2/2-1/2-1.1/2-1.1:1.0/input/input2
[   10.172795] generic-usb 0003:05AC:0201.0001: input,hidraw0: USB HID v1.00 Keyboard [Mitsumi Electric Apple USB Keyboard] on usb-0001:11:09.0-1.1/input0
[   10.178501] input: Logitech Apple Optical USB Mouse as /devices/pci0001:10/0001:10:0d.0/0001:11:09.0/usb2/2-1/2-1.3/2-1.3:1.0/input/input3
[   10.196834] generic-usb 0003:05AC:0307.0002: input,hidraw1: USB HID v1.10 Mouse [Logitech Apple Optical USB Mouse] on usb-0001:11:09.0-1.3/input0
[   10.196917] usbcore: registered new interface driver usbhid
[   10.196931] usbhid: v2.6:USB HID core driver
[   24.980532] scsi0 : Adaptec AIC7XXX EISA/VLB/PCI SCSI HBA DRIVER, Rev 7.0
[   24.980543]         <Adaptec 2902/04/10/15/20C/30C SCSI adapter>
[   24.980549]         aic7850: Single Channel A, SCSI Id=7, 3/253 SCBs
[   24.980555] 
[   24.984062] ohci1394 0001:11:0a.0: enabling device (0010 -> 0012)
[   25.033713] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[63]  MMIO=[80080000-800807ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   25.295453] PM: Starting manual resume from disk
[   25.471171] kjournald starting.  Commit interval 5 seconds
[   25.471228] EXT3-fs: mounted filesystem with ordered data mode.
[   26.320913] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[003065fffe765996]
[   31.825647] udev: starting version 141
[   32.214948] Linux agpgart interface v0.103
[   32.232699] agpgart-uninorth 0000:00:0b.0: Apple UniNorth chipset
[   32.232912] agpgart-uninorth 0000:00:0b.0: configuring for size idx: 8
[   32.233282] agpgart-uninorth 0000:00:0b.0: AGP aperture is 32M @ 0x0
[   32.377967] pmac_zilog: 0.6 (Benjamin Herrenschmidt <benh@kernel.crashing.org>)
[   32.378090] pmac_zilog: i2c-modem detected, id: 1
[   32.378199] ttyPZ0 at MMIO 0x80013020 (irq = 29) is a Z85c30 ESCC - Internal modem
[   32.378582] ttyPZ1 at MMIO 0x80013000 (irq = 50) is a Z85c30 ESCC - Serial port
[   33.031206] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   33.073244] airport 0.15 (Benjamin Herrenschmidt <benh@kernel.crashing.org>)
[   33.091238] airport: Physical address 80030000
[   34.308237] eth1: Hardware identity 0005:0001:0001:0002
[   34.308371] eth1: Station identity  001f:0001:0008:0046
[   34.308385] eth1: Firmware determined as Lucent/Agere 8.70
[   34.308398] eth1: Attempting to download firmware agere_sta_fw.bin
[   34.308423] hermes_dld: AUX enable returned 0
[   34.309187] hermes_dld: AUX disable returned 0
[   34.309197] hermes_dld: Actual PDA length 998, Max allowed 1000
[   34.309206] eth1: Read PDA returned 0
[   34.309218] airport 0.00030000:radio: firmware: requesting agere_sta_fw.bin
[   34.832187] eth1: Cannot find firmware agere_sta_fw.bin
[   34.832266] eth1: Hardware identity 0005:0001:0001:0002
[   34.832380] eth1: Station identity  001f:0001:0008:0046
[   34.832393] eth1: Firmware determined as Lucent/Agere 8.70
[   34.832402] eth1: Ad-hoc demo mode supported
[   34.832410] eth1: IEEE standard IBSS ad-hoc mode supported
[   34.832419] eth1: WEP supported, 104-bit key
[   34.832536] eth1: MAC address 00:30:65:1f:54:f0
[   34.832627] eth1: Station name "HERMES I"
[   34.833183] eth1: ready
[   34.833807] airport: Card registered for interface eth1
[   36.757623] input: PowerMac Beep as /devices/pci0001:10/0001:10:0d.0/0001:11:07.0/input/input4
[   36.942176] apm_emu: PMU APM Emulation initialized.
[   37.716410] Adding 473624k swap on /dev/hda5.  Priority:-1 extents:1 across:473624k
[   38.626908] EXT3 FS on hda4, internal journal
[   41.182432] type=1505 audit(1265820891.180:2): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1735
[   41.183251] type=1505 audit(1265820891.180:3): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1735
[   41.183543] type=1505 audit(1265820891.180:4): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1735
[   41.183839] type=1505 audit(1265820891.180:5): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1735
[   42.084134] type=1505 audit(1265820892.080:6): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1740
[   42.085407] type=1505 audit(1265820892.084:7): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1740
[   42.264591] type=1505 audit(1265820892.264:8): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1744
[   47.203054] hda: host max PIO4 wanted PIO0 selected PIO0
[   48.009817] input: Mouseemu virtual keyboard as /devices/virtual/input/input5
[   48.038375] input: Mouseemu virtual mouse as /devices/virtual/input/input6
[   48.097642] hda: task_no_data_intr: status=0x51 { DriveReady SeekComplete Error }
[   48.097673] hda: task_no_data_intr: error=0x04 { DriveStatusError }
[   48.097688] ide: failed opcode was: 0xef
[   50.951999] Bluetooth: Core ver 2.13
[   50.952256] NET: Registered protocol family 31
[   50.952266] Bluetooth: HCI device and connection manager initialized
[   50.952279] Bluetooth: HCI socket layer initialized
[   51.047564] Bluetooth: L2CAP ver 2.11
[   51.047584] Bluetooth: L2CAP socket layer initialized
[   51.166887] Bluetooth: SCO (Voice Link) ver 0.6
[   51.166905] Bluetooth: SCO socket layer initialized
[   51.252152] Bluetooth: RFCOMM socket layer initialized
[   51.252206] Bluetooth: RFCOMM TTY layer initialized
[   51.252214] Bluetooth: RFCOMM ver 1.10
[   51.369188] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   51.369207] Bluetooth: BNEP filters: protocol multicast
[   51.552249] Bridge firewalling registered
[   55.693440] lp: driver loaded but no devices found
[   55.725409] ppdev: user-space parallel port driver
[   56.602619] NET: Registered protocol family 10
[   56.603096] lo: Disabled Privacy Extensions
[   59.008402] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   59.029999] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   59.138938] NET: Registered protocol family 17

```

---

### Post by linuxopjemac on 2010-02-10
> Using unsupported 1280x1024 ATY,Rage128Ps at 94008000, depth=8, pitch=1280
[    3.097249] Console: switching to colour frame buffer device 160x64
[    3.123900] fb0: Open Firmware frame buffer device on /pci@f0000000/ATY,Rage128Ps@10


It wants to use an unsupported 1280x1024 resolution. How did you get that strange BusID PCI:6:3:0 ? I have never seen that. Normally it is PCI:0:16:0. 

I would add some preferred color depths and mode lines.

---

### Post by Bq32 on 2010-02-10
> **linuxopjemac said:**
> It wants to use an unsupported 1280x1024 resolution. How did you get that strange BusID PCI:6:3:0 ? I have never seen that. Normally it is PCI:0:16:0.

I might also want to update that dmesg, I thought I'd done so when I changed the driver from "r128".

No clue, that's what Xubuntu wanted? It may also be because I have an AGP Graphics card in a PowerMac G4, instead of the iMac versions...

> I would add some preferred color depths and mode lines.

Already tried that, "FbDev" is very sensitive to modes, and "r128" and "ati" honestly scare me that they're not functioning (especially when I could get 1280x1024 with Mac, and any modeline I try to put in still directs to 1280x1024).

---

### Post by linuxopjemac on 2010-02-10
try:

```
Section "Device"
	Identifier	"ATI Rage 128"
	Driver		"ati"
	BusID		"PCI:0:16:0"
        Option          "UseFBDev" "true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
        HorizSync 50-70
        VertRefresh 75-117
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"ATI Rage 128"
DefaultDepth	24
SubSection "Display"
	Depth		1
	Modes		"1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
	Depth		4
	Modes		"1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
	Depth		8
	Modes		"1024x768" "800x600" "640x480"
	EndSubSection
SubSection "Display"
	Depth		15
	Modes		"1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
	Depth		16
	Modes		"1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
	Depth		24
	Modes		"1024x768" "800x600" "640x480"
EndSubSection

EndSection
```

---

### Post by Bq32 on 2010-02-10
> **linuxopjemac said:**
> try:


Nope, won't work. I got the Xorg log this time, though:

```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.15-51-powerpc64-smp ppc Ubuntu
Current Operating System: Linux Elric 2.6.28-6-powerpc #20-Ubuntu Fri Apr 17 08:30:40 UTC 2009 ppc
Build Date: 09 April 2009  02:10:13AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@ross.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Feb 10 10:22:22 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "ATI Rage 128"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0x1e80
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@0:16:0) ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS rev 0, Mem @ 0x94000000/67108864, 0x90000000/16384, I/O @ 0x00000400/256, BIOS @ 0x????????/131072
(II) Open APM successful
(II) System resource ranges:
	[0] -1	2	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	2	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	2	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	2	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	1	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	1	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	1	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	1	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	2	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	2	0x00000000 - 0x00000000 (0x1) IX[B]
	[14] -1	1	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	1	0x00000000 - 0x00000000 (0x1) IX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 6.12.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "r128"
(II) Loading /usr/lib/xorg/modules/drivers//r128_drv.so
(II) Module r128: vendor="X.Org Foundation"
	compiled for 1.5.99.902, module version = 6.8.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) R128: Driver for ATI Rage 128 chipsets:
	ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
	ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
	ATI Rage 128 Pro GL PA (PCI/AGP), ATI Rage 128 Pro GL PB (PCI/AGP),
	ATI Rage 128 Pro GL PC (PCI/AGP), ATI Rage 128 Pro GL PD (PCI),
	ATI Rage 128 Pro GL PE (PCI/AGP), ATI Rage 128 Pro GL PF (AGP),
	ATI Rage 128 Pro VR PG (PCI/AGP), ATI Rage 128 Pro VR PH (PCI/AGP),
	ATI Rage 128 Pro VR PI (PCI/AGP), ATI Rage 128 Pro VR PJ (PCI/AGP),
	ATI Rage 128 Pro VR PK (PCI/AGP), ATI Rage 128 Pro VR PL (PCI/AGP),
	ATI Rage 128 Pro VR PM (PCI/AGP), ATI Rage 128 Pro VR PN (PCI/AGP),
	ATI Rage 128 Pro VR PO (PCI/AGP), ATI Rage 128 Pro VR PP (PCI),
	ATI Rage 128 Pro VR PQ (PCI/AGP), ATI Rage 128 Pro VR PR (PCI),
	ATI Rage 128 Pro VR PS (PCI/AGP), ATI Rage 128 Pro VR PT (PCI/AGP),
	ATI Rage 128 Pro VR PU (PCI/AGP), ATI Rage 128 Pro VR PV (PCI/AGP),
	ATI Rage 128 Pro VR PW (PCI/AGP), ATI Rage 128 Pro VR PX (PCI/AGP),
	ATI Rage 128 GL RE (PCI), ATI Rage 128 GL RF (AGP),
	ATI Rage 128 RG (AGP), ATI Rage 128 VR RK (PCI),
	ATI Rage 128 VR RL (AGP), ATI Rage 128 4X SE (PCI/AGP),
	ATI Rage 128 4X SF (PCI/AGP), ATI Rage 128 4X SG (PCI/AGP),
	ATI Rage 128 4X SH (PCI/AGP), ATI Rage 128 4X SK (PCI/AGP),
	ATI Rage 128 4X SL (PCI/AGP), ATI Rage 128 4X SM (AGP),
	ATI Rage 128 4X SN (PCI/AGP), ATI Rage 128 Pro ULTRA TF (AGP),
	ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR (AGP),
	ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT (AGP?),
	ATI Rage 128 Pro ULTRA TU (AGP?)
(II) Primary Device is: PCI 00@00:10:0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	2	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	2	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	2	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	2	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	1	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	1	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	1	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	1	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	2	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	2	0x00000000 - 0x00000000 (0x1) IX[B]
	[14] -1	1	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	1	0x00000000 - 0x00000000 (0x1) IX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
	[0] -1	2	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	2	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	2	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	2	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	1	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	1	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	1	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	1	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[13] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[14] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[15] -1	2	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	2	0x00000000 - 0x00000000 (0x1) IX[B]
	[17] -1	1	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	1	0x00000000 - 0x00000000 (0x1) IX[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[21] 0	0	0xf00003b0 - 0xf00003bb (0xc) IS[B]
	[22] 0	0	0xf00003c0 - 0xf00003df (0x20) IS[B]
(II) R128(0): PCI bus 0 card 16 func 0
(**) R128(0): Depth 24, (--) framebuffer bpp 32
(II) R128(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) R128(0): Default visual is TrueColor
(**) R128(0): Option "UseFBDev" "true"
(II) R128(0): VGAAccess option set to FALSE, VGA module load skipped
(==) R128(0): RGB weight 888
(II) R128(0): Using 8 bits per RGB (8 bit DAC)
(**) R128(0): Using framebuffer device
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux//libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.0.2
	ABI class: X.Org Video Driver, version 5.0
(WW) open /dev/fb1: No such file or directory
(WW) open /dev/fb2: No such file or directory
(WW) open /dev/fb3: No such file or directory
(WW) open /dev/fb4: No such file or directory
(WW) open /dev/fb5: No such file or directory
(WW) open /dev/fb6: No such file or directory
(WW) open /dev/fb7: No such file or directory
(EE) Unable to find a valid framebuffer device
(EE) R128(0): Failed to open framebuffer device, consult warnings and/or errors above for possible reasons
	(you may have to look at the server log to see warnings)
(II) UnloadModule: "r128"
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux//libfbdevhw.so
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log

```

---

### Post by linuxopjemac on 2010-02-10
what if you set the following?

```
Option          "UseFBDev" "false"
```


report Xorg.conf.log again pls

---

### Post by Bq32 on 2010-02-10
> **linuxopjemac said:**
> what if you set the following?

```
Option          "UseFBDev" "false"
```


report Xorg.conf.log again pls

```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.15-51-powerpc64-smp ppc Ubuntu
Current Operating System: Linux Elric 2.6.28-6-powerpc #20-Ubuntu Fri Apr 17 08:30:40 UTC 2009 ppc
Build Date: 09 April 2009  02:10:13AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@ross.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Feb 10 10:50:28 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "ATI Rage 128"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0x1e80
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(--) using VT number 7

(--) PCI:*(0@0:16:0) ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS rev 0, Mem @ 0x94000000/67108864, 0x90000000/16384, I/O @ 0x00000400/256, BIOS @ 0x????????/131072
(II) Open APM successful
(II) System resource ranges:
	[0] -1	2	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	2	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	2	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	2	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	1	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	1	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	1	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	1	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	2	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	2	0x00000000 - 0x00000000 (0x1) IX[B]
	[14] -1	1	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	1	0x00000000 - 0x00000000 (0x1) IX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 6.12.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "r128"
(II) Loading /usr/lib/xorg/modules/drivers//r128_drv.so
(II) Module r128: vendor="X.Org Foundation"
	compiled for 1.5.99.902, module version = 6.8.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) R128: Driver for ATI Rage 128 chipsets:
	ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
	ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
	ATI Rage 128 Pro GL PA (PCI/AGP), ATI Rage 128 Pro GL PB (PCI/AGP),
	ATI Rage 128 Pro GL PC (PCI/AGP), ATI Rage 128 Pro GL PD (PCI),
	ATI Rage 128 Pro GL PE (PCI/AGP), ATI Rage 128 Pro GL PF (AGP),
	ATI Rage 128 Pro VR PG (PCI/AGP), ATI Rage 128 Pro VR PH (PCI/AGP),
	ATI Rage 128 Pro VR PI (PCI/AGP), ATI Rage 128 Pro VR PJ (PCI/AGP),
	ATI Rage 128 Pro VR PK (PCI/AGP), ATI Rage 128 Pro VR PL (PCI/AGP),
	ATI Rage 128 Pro VR PM (PCI/AGP), ATI Rage 128 Pro VR PN (PCI/AGP),
	ATI Rage 128 Pro VR PO (PCI/AGP), ATI Rage 128 Pro VR PP (PCI),
	ATI Rage 128 Pro VR PQ (PCI/AGP), ATI Rage 128 Pro VR PR (PCI),
	ATI Rage 128 Pro VR PS (PCI/AGP), ATI Rage 128 Pro VR PT (PCI/AGP),
	ATI Rage 128 Pro VR PU (PCI/AGP), ATI Rage 128 Pro VR PV (PCI/AGP),
	ATI Rage 128 Pro VR PW (PCI/AGP), ATI Rage 128 Pro VR PX (PCI/AGP),
	ATI Rage 128 GL RE (PCI), ATI Rage 128 GL RF (AGP),
	ATI Rage 128 RG (AGP), ATI Rage 128 VR RK (PCI),
	ATI Rage 128 VR RL (AGP), ATI Rage 128 4X SE (PCI/AGP),
	ATI Rage 128 4X SF (PCI/AGP), ATI Rage 128 4X SG (PCI/AGP),
	ATI Rage 128 4X SH (PCI/AGP), ATI Rage 128 4X SK (PCI/AGP),
	ATI Rage 128 4X SL (PCI/AGP), ATI Rage 128 4X SM (AGP),
	ATI Rage 128 4X SN (PCI/AGP), ATI Rage 128 Pro ULTRA TF (AGP),
	ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR (AGP),
	ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT (AGP?),
	ATI Rage 128 Pro ULTRA TU (AGP?)
(II) Primary Device is: PCI 00@00:10:0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	2	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	2	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	2	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	2	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	1	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	1	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	1	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	1	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	2	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	2	0x00000000 - 0x00000000 (0x1) IX[B]
	[14] -1	1	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	1	0x00000000 - 0x00000000 (0x1) IX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
	[0] -1	2	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	2	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	2	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	2	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	1	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	1	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	1	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	1	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[13] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[14] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[15] -1	2	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	2	0x00000000 - 0x00000000 (0x1) IX[B]
	[17] -1	1	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	1	0x00000000 - 0x00000000 (0x1) IX[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[21] 0	0	0xf00003b0 - 0xf00003bb (0xc) IS[B]
	[22] 0	0	0xf00003c0 - 0xf00003df (0x20) IS[B]
(II) R128(0): PCI bus 0 card 16 func 0
(**) R128(0): Depth 24, (--) framebuffer bpp 32
(II) R128(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) R128(0): Default visual is TrueColor
(**) R128(0): Option "UseFBDev" "false"
(II) R128(0): VGAAccess option set to FALSE, VGA module load skipped
(==) R128(0): RGB weight 888
(II) R128(0): Using 8 bits per RGB (8 bit DAC)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) R128(0): initializing int10

Backtrace:
0: X(xorg_backtrace+0x50) [0x101091b0]
1: X(xf86SigHandler+0x70) [0x1008e6a0]
2: [0x100344]
3: /usr/lib/xorg/modules//libint10.so(xf86ExtendedInitInt10+0x2d0) [0xf5d6380]
4: /usr/lib/xorg/modules//libint10.so(xf86InitInt10+0x28) [0xf5d1db8]
5: /usr/lib/xorg/modules/drivers//r128_drv.so(R128PreInit+0x65c) [0xf628ccc]
6: X(InitOutput+0xf90) [0x100735d0]
7: X(main+0x218) [0x100291f8]
8: /lib/libc.so.6 [0xf90fbe4]
9: /lib/libc.so.6 [0xf90fda0]
Saw signal 7.  Server aborting.
 ddxSigGiveUp: Closing log
```

---

### Post by linuxopjemac on 2010-02-10
add the line

```
Option "NoInt10" "true"

```
in the device section

---

### Post by Bq32 on 2010-02-10
> **linuxopjemac said:**
> add the line

```
Option "NoInt10" "true"

```
in the device section

That actually "crashed" X11, causing the OUT OF RANGE box to appear before the splash even did. I had to edit the xorg.conf file on the Live CD (of which I'm on now).

No log is available.

---

### Post by linuxopjemac on 2010-02-10
cannot you let Xorg make an Xorg.conf file for you ?

```
sudo Xorg -configure
```

---

### Post by Bq32 on 2010-02-10
> **linuxopjemac said:**
> cannot you let Xorg make an Xorg.conf file for you ?

```
sudo Xorg -configure
```

I've already done that, and that's when it says "no valid framebuffer device".

---

### Post by linuxopjemac on 2010-02-10
maybe it is 

```
sudo X -reconfigure
```

I am not sure

---

### Post by linuxopjemac on 2010-02-10
do you have a /dev/fb0 there ?

---

### Post by linuxopjemac on 2010-02-10
If your framebuffer device is not there, you might want to load it

```
sudo modprobe ati128fb
```

you should have a framebuffer device after that
then set X automatically

---

### Post by Bq32 on 2010-02-10
> **linuxopjemac said:**
> maybe it is 

```
sudo X -reconfigure
```

I am not sure

I already know the command to configure it (dpkg-reconfigure -phigh xserver-xorg), but it won't configure a framebuffer. 

Do you know if Updating to Karmic would fix things, or worsen it? (I reset to 9.04 to fix video=ofonly). Also, would this still be considered PPC only? I'm wondering about putting it in the Hardware section...

Also, modprobe can't find any framebuffer device named ati128fb. I'll probably reconfig and see if I can use modprobe then.

---

### Post by linuxopjemac on 2010-02-10
I think it will not solve your problem to go to Karmic....

---

### Post by Bq32 on 2010-02-10
> **linuxopjemac said:**
> do you have a /dev/fb0 there ?

In one of the previous logs I posted, X.org said it found no /dev/fb0.

---

### Post by linuxopjemac on 2010-02-10
```
sudo modprobe ati128fb
```

---

### Post by linuxopjemac on 2010-02-10
what is the output of:

```
fbset -iv

```

and

```
ls -al /dev/fb*
```

---

### Post by Bq32 on 2010-02-10
> **linuxopjemac said:**
> what is the output of:

```
fbset -iv

```

and

```
ls -al /dev/fb*
```

```
fbset: command not found
```

and

```
crw-rw---- 1 root video 29, 0 2010-02-10 16:00 /dev/fb0

```

---

### Post by linuxopjemac on 2010-02-10
you could try the post of unclernie [here]("http://ubuntuforums.org/archive/index.php/t-770033.html")

> February 2nd, 2009, 06:50 AM
When I keep banging my head against the wall, sometimes the brick chips a little bit...

I ran `ls -al /dev/fb*`, and discovered only one framebuffer device present, fb0. So I decided to create another. `mknod -m660 /dev/fb1 c 29 1` . Then I tried another startx, and lo and behold, I got a flash of rainbow colors on my screen, followed by a grey screen with an X in the middle. Getting closer...
I went back to xorg.conf and gave it another look. I discovered that I still had in there an 'option usefbdev true' line, so I commented it out. I also had the hunch that the PCI address confusion (0,10,0) vs (0,16,0) might be a simple decimal-hex conversion, so I tried changing to the decimal version (0,16,0). Save, exit, and startx. This time, no flash of random rainbow, but directly to the grey X, and a few seconds later, the Hardy Heron appeared!
But when I tried to launch Firefox, I got a few error dialogs popping up about the 'user switcher' failing, but firefox eventually opened.
I closed it, exited from X, issued a reboot from the shell prompt, and kept my hands off the keyboard. This time, no magic boot incantations, no muss, no fuss, and I got an Ubuntu gdm login! And a few keystrokes later, the full Gnome desktop.
When Synaptic finishes installing the 246 updated packages, I'll shut it down and revert the memory to the 256MB it came with, and see if it still can launch the desktop...

---

### Post by linuxopjemac on 2010-02-10
maybe it's modprobe aty128fb ....

I can't help you anymore, gotta go. If nothing helps you might want to try Karmic with all the tips I gave you. I am pretty sure that you will get your display to work with Debian. So that's also a fall back position.

---

### Post by Bq32 on 2010-02-10
I'm gonna make another thread with a title more relevant, because I have what was the basis of this figured out, and it might be easier to get more answers with what the thread name now should be.

---

