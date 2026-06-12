---
title: "wireless and sound problems on gutsy"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by Pulka on 2007-11-13
hi!

just did a fresh install of Gutsy in a new machine, and i'm having a few problems. I would appreciate some help, please.

1st - _After the installation, had the sound working_. As soon as i shutdown, no longer have sound. I think the problem is the module is not loading on boot. For what i've seen in previous posts, all it takes is to had a line in /etc/modprobe, but i don't know what to add. How can see it?

2nd - my wireless connection works fine when i turn on the computer, but once in a while it goes down. Sometimes i have to reboot, others it just comes again after a few minutes. Any guess of what's going on?

---

### Post by Pulka on 2007-11-13
anyone?

---

### Post by Thangor on 2007-11-13
what type of sound card? and what type of wireless card? also which desktop environment are you using? kde or gnome?

---

### Post by Pulka on 2007-11-13
sound card = audigy
desktop = gnome
wireless = don't have it here

---

### Post by Pulka on 2007-11-13
ok....can at least someone tell me how i know the name of the module of the sound card?

---

### Post by poudin on 2007-11-13
is this a laptop or desktop used here...reason i ask...[www.linlap.com](www.linlap.com) has a list of laptops and driver resources to resolve issues.

as for the sound card or wirless network adaptor.

what is the output of lspci at command line...should show the models in the machine that are detected.

---

### Post by Pulka on 2007-11-13
it's a desktop....

i'll put the lscpi output as soon as i get to the computer

---

### Post by Pulka on 2007-11-13
About the wireless,there's one thing that might have to do with it. I notice that my wireless connection breaks everytime i open DELUGE (bittorrent client).

The sound, sometimes on, sometimes off


**lspci**

00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88W8310 and 88W8000G [Libertas] 802.11g client chipset (rev 07)
01:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
01:04.0 Mass storage controller: Integrated Technology Express, Inc. IT/ITE8212 Dual channel ATA RAID controller (rev 13)
01:05.0 RAID bus controller: Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller (rev 02)
01:0a.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
01:0a.1 Input device controller: Creative Labs SB Audigy Game Port (rev 03)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 15)
04:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2)


**lspci | grep audio**

01:0a.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)

---

### Post by Pulka on 2007-11-13
**dmesg**

[   43.830651] kjournald starting.  Commit interval 5 seconds
[   43.830663] EXT3-fs: mounted filesystem with ordered data mode.
[   46.264672] usb-storage: device scan complete
[   46.265159] scsi scan: INQUIRY result too short (5), using 36
[   46.265165] scsi 4:0:0:0: CD-ROM            Toshiba  USB 2.0 CD-ROM   1.15 PQ: 0 ANSI: 0
[   46.265656] scsi 4:0:0:1: Direct-Access     Toshiba  USB 2.0 Ext. HDD 1.15 PQ: 0 ANSI: 0
[   46.267262] sr2: scsi3-mmc drive: 52x/52x cd/rw xa/form2 cdda tray
[   46.267309] sr 4:0:0:0: Attached scsi CD-ROM sr2
[   46.267355] sr 4:0:0:0: Attached scsi generic sg3 type 5
[   46.268133] sd 4:0:0:1: [sdb] 781371352 512-byte hardware sectors (400062 MB)
[   46.269006] sd 4:0:0:1: [sdb] Write Protect is off
[   46.269010] sd 4:0:0:1: [sdb] Mode Sense: 0b 00 00 08
[   46.269012] sd 4:0:0:1: [sdb] Assuming drive cache: write through
[   46.269877] sd 4:0:0:1: [sdb] 781371352 512-byte hardware sectors (400062 MB)
[   46.270750] sd 4:0:0:1: [sdb] Write Protect is off
[   46.270754] sd 4:0:0:1: [sdb] Mode Sense: 0b 00 00 08
[   46.270756] sd 4:0:0:1: [sdb] Assuming drive cache: write through
[   46.270759]  sdb: sdb1
[   46.271258]  sdb: p1 exceeds device capacity
[   46.271313] sd 4:0:0:1: [sdb] Attached SCSI disk
[   46.271355] sd 4:0:0:1: Attached scsi generic sg4 type 0
[   47.855177] attempt to access beyond end of device
[   47.855185] sdb: rw=0, want=781385395, limit=781371352
[   47.855190] Buffer I/O error on device sdb1, logical block 781384704
[   47.855197] attempt to access beyond end of device
[   47.855202] sdb: rw=0, want=781385396, limit=781371352
[   47.855206] Buffer I/O error on device sdb1, logical block 781384705
[   47.855210] attempt to access beyond end of device
[   47.855214] sdb: rw=0, want=781385397, limit=781371352
[   47.855219] Buffer I/O error on device sdb1, logical block 781384706
[   47.855224] attempt to access beyond end of device
[   47.855229] sdb: rw=0, want=781385398, limit=781371352
[   47.855234] Buffer I/O error on device sdb1, logical block 781384707
[   47.855239] attempt to access beyond end of device
[   47.855243] sdb: rw=0, want=781385399, limit=781371352
[   47.855246] Buffer I/O error on device sdb1, logical block 781384708
[   47.855251] attempt to access beyond end of device
[   47.855255] sdb: rw=0, want=781385400, limit=781371352
[   47.855259] Buffer I/O error on device sdb1, logical block 781384709
[   47.855263] attempt to access beyond end of device
[   47.855267] sdb: rw=0, want=781385401, limit=781371352
[   47.855272] Buffer I/O error on device sdb1, logical block 781384710
[   47.855277] attempt to access beyond end of device
[   47.855281] sdb: rw=0, want=781385402, limit=781371352
[   47.855286] Buffer I/O error on device sdb1, logical block 781384711
[   47.855294] attempt to access beyond end of device
[   47.855298] sdb: rw=0, want=781385395, limit=781371352
[   47.855303] Buffer I/O error on device sdb1, logical block 781384704
[   47.855308] attempt to access beyond end of device
[   47.855311] sdb: rw=0, want=781385396, limit=781371352
[   47.855316] Buffer I/O error on device sdb1, logical block 781384705
[   47.855321] attempt to access beyond end of device
[   47.855325] sdb: rw=0, want=781385397, limit=781371352
[   47.855330] attempt to access beyond end of device
[   47.855333] sdb: rw=0, want=781385398, limit=781371352
[   47.855338] attempt to access beyond end of device
[   47.855343] sdb: rw=0, want=781385399, limit=781371352
[   47.855348] attempt to access beyond end of device
[   47.855352] sdb: rw=0, want=781385400, limit=781371352
[   47.855355] attempt to access beyond end of device
[   47.855359] sdb: rw=0, want=781385401, limit=781371352
[   47.855362] attempt to access beyond end of device
[   47.855366] sdb: rw=0, want=781385402, limit=781371352
[   47.855388] attempt to access beyond end of device
[   47.855392] sdb: rw=0, want=781385515, limit=781371352
[   47.855396] attempt to access beyond end of device
[   47.855400] sdb: rw=0, want=781385516, limit=781371352
[   47.855404] attempt to access beyond end of device
[   47.855407] sdb: rw=0, want=781385517, limit=781371352
[   47.855411] attempt to access beyond end of device
[   47.855414] sdb: rw=0, want=781385518, limit=781371352
[   47.855418] attempt to access beyond end of device
[   47.855422] sdb: rw=0, want=781385519, limit=781371352
[   47.855426] attempt to access beyond end of device
[   47.855429] sdb: rw=0, want=781385520, limit=781371352
[   47.855433] attempt to access beyond end of device
[   47.855437] sdb: rw=0, want=781385521, limit=781371352
[   47.855441] attempt to access beyond end of device
[   47.855444] sdb: rw=0, want=781385522, limit=781371352
[   47.855451] attempt to access beyond end of device
[   47.855455] sdb: rw=0, want=781385515, limit=781371352
[   47.855459] attempt to access beyond end of device
[   47.855462] sdb: rw=0, want=781385516, limit=781371352
[   47.855466] attempt to access beyond end of device
[   47.855470] sdb: rw=0, want=781385517, limit=781371352
[   47.855474] attempt to access beyond end of device
[   47.855477] sdb: rw=0, want=781385518, limit=781371352
[   47.855480] attempt to access beyond end of device
[   47.855484] sdb: rw=0, want=781385519, limit=781371352
[   47.855488] attempt to access beyond end of device
[   47.855492] sdb: rw=0, want=781385520, limit=781371352
[   47.855496] attempt to access beyond end of device
[   47.855499] sdb: rw=0, want=781385521, limit=781371352
[   47.855503] attempt to access beyond end of device
[   47.855506] sdb: rw=0, want=781385522, limit=781371352
[   47.866084] attempt to access beyond end of device
[   47.866092] sdb: rw=0, want=781385531, limit=781371352
[   47.866097] attempt to access beyond end of device
[   47.866102] sdb: rw=0, want=781385532, limit=781371352
[   47.866106] attempt to access beyond end of device
[   47.866110] sdb: rw=0, want=781385533, limit=781371352
[   47.866113] attempt to access beyond end of device
[   47.866117] sdb: rw=0, want=781385534, limit=781371352
[   47.866121] attempt to access beyond end of device
[   47.866124] sdb: rw=0, want=781385535, limit=781371352
[   47.866131] attempt to access beyond end of device
[   47.866134] sdb: rw=0, want=781385531, limit=781371352
[   47.866138] attempt to access beyond end of device
[   47.866141] sdb: rw=0, want=781385532, limit=781371352
[   47.866145] attempt to access beyond end of device
[   47.866148] sdb: rw=0, want=781385533, limit=781371352
[   47.866152] attempt to access beyond end of device
[   47.866155] sdb: rw=0, want=781385534, limit=781371352
[   47.866159] attempt to access beyond end of device
[   47.866162] sdb: rw=0, want=781385535, limit=781371352
[   47.866174] attempt to access beyond end of device
[   47.866178] sdb: rw=0, want=781385531, limit=781371352
[   47.866181] attempt to access beyond end of device
[   47.866185] sdb: rw=0, want=781385532, limit=781371352
[   47.866188] attempt to access beyond end of device
[   47.866192] sdb: rw=0, want=781385533, limit=781371352
[   47.866195] attempt to access beyond end of device
[   47.866199] sdb: rw=0, want=781385534, limit=781371352
[   47.866202] attempt to access beyond end of device
[   47.866206] sdb: rw=0, want=781385535, limit=781371352
[   47.866218] attempt to access beyond end of device
[   47.866222] sdb: rw=0, want=781385531, limit=781371352
[   47.866227] attempt to access beyond end of device
[   47.866230] sdb: rw=0, want=781385532, limit=781371352
[   47.866234] attempt to access beyond end of device
[   47.866237] sdb: rw=0, want=781385533, limit=781371352
[   47.866242] attempt to access beyond end of device
[   47.866245] sdb: rw=0, want=781385534, limit=781371352
[   47.866250] attempt to access beyond end of device
[   47.866253] sdb: rw=0, want=781385535, limit=781371352
[   47.866263] attempt to access beyond end of device
[   47.866268] sdb: rw=0, want=781385531, limit=781371352
[   47.866273] attempt to access beyond end of device
[   47.866276] sdb: rw=0, want=781385532, limit=781371352
[   47.866280] attempt to access beyond end of device
[   47.866283] sdb: rw=0, want=781385533, limit=781371352
[   47.866288] attempt to access beyond end of device
[   47.866292] sdb: rw=0, want=781385534, limit=781371352
[   47.866296] attempt to access beyond end of device
[   47.866300] sdb: rw=0, want=781385535, limit=781371352
[   47.866311] attempt to access beyond end of device
[   47.866315] sdb: rw=0, want=781385531, limit=781371352
[   47.866320] attempt to access beyond end of device
[   47.866324] sdb: rw=0, want=781385532, limit=781371352
[   47.866328] attempt to access beyond end of device
[   47.866331] sdb: rw=0, want=781385533, limit=781371352
[   47.866335] attempt to access beyond end of device
[   47.866339] sdb: rw=0, want=781385534, limit=781371352
[   47.866344] attempt to access beyond end of device
[   47.866348] sdb: rw=0, want=781385535, limit=781371352
[   47.866359] attempt to access beyond end of device
[   47.866363] sdb: rw=0, want=781385531, limit=781371352
[   47.866368] attempt to access beyond end of device
[   47.866371] sdb: rw=0, want=781385532, limit=781371352
[   47.866376] attempt to access beyond end of device
[   47.866379] sdb: rw=0, want=781385533, limit=781371352
[   47.866383] attempt to access beyond end of device
[   47.866387] sdb: rw=0, want=781385534, limit=781371352
[   47.866391] attempt to access beyond end of device
[   47.866395] sdb: rw=0, want=781385535, limit=781371352
[   47.866410] attempt to access beyond end of device
[   47.866415] sdb: rw=0, want=781385467, limit=781371352
[   47.866419] attempt to access beyond end of device
[   47.866423] sdb: rw=0, want=781385468, limit=781371352
[   47.866427] attempt to access beyond end of device
[   47.866431] sdb: rw=0, want=781385469, limit=781371352
[   47.866435] attempt to access beyond end of device
[   47.866439] sdb: rw=0, want=781385470, limit=781371352
[   47.866443] attempt to access beyond end of device
[   47.866446] sdb: rw=0, want=781385471, limit=781371352
[   47.866451] attempt to access beyond end of device
[   47.866454] sdb: rw=0, want=781385472, limit=781371352
[   47.866459] attempt to access beyond end of device
[   47.866463] sdb: rw=0, want=781385473, limit=781371352
[   47.866467] attempt to access beyond end of device
[   47.866470] sdb: rw=0, want=781385474, limit=781371352
[   47.866486] attempt to access beyond end of device
[   47.866490] sdb: rw=0, want=781385523, limit=781371352
[   47.866495] attempt to access beyond end of device
[   47.866499] sdb: rw=0, want=781385524, limit=781371352
[   47.866503] attempt to access beyond end of device
[   47.866507] sdb: rw=0, want=781385525, limit=781371352
[   47.866511] attempt to access beyond end of device
[   47.866515] sdb: rw=0, want=781385526, limit=781371352
[   47.866519] attempt to access beyond end of device
[   47.866522] sdb: rw=0, want=781385527, limit=781371352
[   47.866526] attempt to access beyond end of device
[   47.866530] sdb: rw=0, want=781385528, limit=781371352
[   47.866534] attempt to access beyond end of device
[   47.866538] sdb: rw=0, want=781385529, limit=781371352
[   47.866541] attempt to access beyond end of device
[   47.866545] sdb: rw=0, want=781385530, limit=781371352
[   47.866557] attempt to access beyond end of device
[   47.866561] sdb: rw=0, want=781385531, limit=781371352
[   47.866565] attempt to access beyond end of device
[   47.866568] sdb: rw=0, want=781385532, limit=781371352
[   47.866572] attempt to access beyond end of device
[   47.866576] sdb: rw=0, want=781385533, limit=781371352
[   47.866580] attempt to access beyond end of device
[   47.866583] sdb: rw=0, want=781385534, limit=781371352
[   47.866588] attempt to access beyond end of device
[   47.866591] sdb: rw=0, want=781385535, limit=781371352
[   47.866603] attempt to access beyond end of device
[   47.866607] sdb: rw=0, want=781385531, limit=781371352
[   47.866611] attempt to access beyond end of device
[   47.866615] sdb: rw=0, want=781385532, limit=781371352
[   47.866619] attempt to access beyond end of device
[   47.866622] sdb: rw=0, want=781385533, limit=781371352
[   47.866626] attempt to access beyond end of device
[   47.866630] sdb: rw=0, want=781385534, limit=781371352
[   47.866634] attempt to access beyond end of device
[   47.866637] sdb: rw=0, want=781385535, limit=781371352
[   49.338525] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   49.340835] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   49.352240] intel_rng: FWH not detected
[   49.402410] iTCO_vendor_support: vendor-support=0
[   49.403733] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   49.403823] iTCO_wdt: Found a ICH6 or ICH6R TCO device (Version=2, TCOBASE=0x0860)
[   49.403880] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   49.533556] Linux agpgart interface v0.102 (c) Dave Jones
[   50.007899] logips2pp: Detected unknown logitech mouse model 89
[   50.130024] gameport: EMU10K1 is pci0000:01:0a.1/gameport0, io 0xbc00, speed 917kHz
[   50.439108] nvidia: module license 'NVIDIA' taints kernel.
[   50.695748] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   50.695768] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   50.696035] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.23  Thu Oct  4 10:16:34 PDT 2007
[   50.702223] input: PC Speaker as /class/input/input2
[   50.717732] input: ImExPS/2 Logitech Explorer Mouse as /class/input/input3
[   50.730183] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   50.730200] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   50.730227] sky2 0000:02:00.0: v1.18 addr 0xd2efc000 irq 17 Yukon-EC (0xb6) rev 1
[   50.730376] sky2 eth0: addr 00:11:2f:3c:06:4b
[   50.826712] parport_pc 00:07: reported by Plug and Play ACPI
[   50.826822] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   50.877234] ACPI: PCI Interrupt 0000:01:0a.0[A] -> GSI 21 (level, low) -> IRQ 22
[   50.881432] Installing spdif_bug patch: Audigy 1 ES [SB0160]
[   50.937035] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   50.937056] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   51.754802] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: usb_submit_urb(ctrl) failed
[   51.754816] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: timeout initializing reports
[   51.754898] input: Logitech Logitech Dual Action as /class/input/input4
[   51.754930] input: USB HID v1.10 Joystick [Logitech Logitech Dual Action] on usb-0000:00:1d.3-1
[   51.754948] usbcore: registered new interface driver usbhid
[   51.754953] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   51.818601] usbcore: registered new interface driver xpad
[   51.818606] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[   52.576745] lp0: using parport0 (interrupt-driven).
[   52.653436] ndiswrapper version 1.49 loaded (smp=yes, preempt=no)
[   52.708375] ndiswrapper: driver mrv8ka51 (Marvell,05/20/2004,2.3.0.19) loaded
[   52.708592] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 20 (level, low) -> IRQ 23
[   52.709303] ndiswrapper: using IRQ 23
[   52.970358] wlan0: ethernet device 00:11:2f:3c:12:05 using NDIS driver: mrv8ka51, version: 0x203000c, NDIS version: 0x501, vendor: 'Marvell 802.11 Driver', 11AB:1FA7.5.conf
[   52.970379] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   52.970445] usbcore: registered new interface driver ndiswrapper
[   53.024609] Adding 2088440k swap on /dev/sda2.  Priority:-1 extents:1 across:2088440k
[   53.481968] EXT3 FS on sda4, internal journal
[   53.997597] kjournald starting.  Commit interval 5 seconds
[   53.997837] EXT3 FS on sda8, internal journal
[   53.997843] EXT3-fs: mounted filesystem with ordered data mode.
[   55.221942] input: Power Button (FF) as /class/input/input5
[   55.221971] ACPI: Power Button (FF) [PWRF]
[   55.222082] input: Power Button (CM) as /class/input/input6
[   55.222104] ACPI: Power Button (CM) [PWRB]
[   55.361170] No dock devices found.
[   55.633045] NET: Registered protocol family 17
[   56.524778] ppdev: user-space parallel port driver
[   56.603705] audit(1194981684.873:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5271 profile="/usr/sbin/cupsd"
[   56.711027] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   56.711033] apm: disabled - APM is not SMP safe.
[   56.775015] sky2 eth0: enabling interface
[   57.167206] Failure registering capabilities with primary security module.
[   57.702393] attempt to access beyond end of device
[   57.702402] sdb: rw=0, want=781385395, limit=781371352
[   57.702408] printk: 83 messages suppressed.
[   57.702411] Buffer I/O error on device sdb1, logical block 781384704
[   57.702451] attempt to access beyond end of device
[   57.702458] sdb: rw=0, want=781385396, limit=781371352
[   57.702496] attempt to access beyond end of device
[   57.702503] sdb: rw=0, want=781385397, limit=781371352
[   57.702545] attempt to access beyond end of device
[   57.702551] sdb: rw=0, want=781385398, limit=781371352
[   57.702559] attempt to access beyond end of device
[   57.702565] sdb: rw=0, want=781385399, limit=781371352
[   57.702603] attempt to access beyond end of device
[   57.702608] sdb: rw=0, want=781385400, limit=781371352
[   57.702616] attempt to access beyond end of device
[   57.702622] sdb: rw=0, want=781385401, limit=781371352
[   57.702664] attempt to access beyond end of device
[   57.702671] sdb: rw=0, want=781385402, limit=781371352
[   57.702739] attempt to access beyond end of device
[   57.702745] sdb: rw=0, want=781385395, limit=781371352
[   57.702753] attempt to access beyond end of device
[   57.702759] sdb: rw=0, want=781385396, limit=781371352
[   57.702802] attempt to access beyond end of device
[   57.702807] sdb: rw=0, want=781385397, limit=781371352
[   57.702811] attempt to access beyond end of device
[   57.702814] sdb: rw=0, want=781385398, limit=781371352
[   57.702818] attempt to access beyond end of device
[   57.702822] sdb: rw=0, want=781385399, limit=781371352
[   57.702826] attempt to access beyond end of device
[   57.702829] sdb: rw=0, want=781385400, limit=781371352
[   57.702832] attempt to access beyond end of device
[   57.702836] sdb: rw=0, want=781385401, limit=781371352
[   57.702839] attempt to access beyond end of device
[   57.702842] sdb: rw=0, want=781385402, limit=781371352
[   57.702862] attempt to access beyond end of device
[   57.702866] sdb: rw=0, want=781385515, limit=781371352
[   57.702870] attempt to access beyond end of device
[   57.702874] sdb: rw=0, want=781385516, limit=781371352
[   57.702878] attempt to access beyond end of device
[   57.702882] sdb: rw=0, want=781385517, limit=781371352
[   57.702886] attempt to access beyond end of device
[   57.702890] sdb: rw=0, want=781385518, limit=781371352
[   57.702894] attempt to access beyond end of device
[   57.702897] sdb: rw=0, want=781385519, limit=781371352
[   57.702901] attempt to access beyond end of device
[   57.702905] sdb: rw=0, want=781385520, limit=781371352
[   57.702909] attempt to access beyond end of device
[   57.702912] sdb: rw=0, want=781385521, limit=781371352
[   57.702916] attempt to access beyond end of device
[   57.702920] sdb: rw=0, want=781385522, limit=781371352
[   57.702926] attempt to access beyond end of device
[   57.702931] sdb: rw=0, want=781385515, limit=781371352
[   57.702934] attempt to access beyond end of device
[   57.702938] sdb: rw=0, want=781385516, limit=781371352
[   57.702942] attempt to access beyond end of device
[   57.702945] sdb: rw=0, want=781385517, limit=781371352
[   57.702950] attempt to access beyond end of device
[   57.702955] sdb: rw=0, want=781385518, limit=781371352
[   57.702962] attempt to access beyond end of device
[   57.702969] sdb: rw=0, want=781385519, limit=781371352
[   57.702984] attempt to access beyond end of device
[   57.702991] sdb: rw=0, want=781385520, limit=781371352
[   57.703006] attempt to access beyond end of device
[   57.703013] sdb: rw=0, want=781385521, limit=781371352
[   57.703073] attempt to access beyond end of device
[   57.703079] sdb: rw=0, want=781385522, limit=781371352
[   57.705078] attempt to access beyond end of device
[   57.705085] sdb: rw=0, want=781385531, limit=781371352
[   57.705092] attempt to access beyond end of device
[   57.705096] sdb: rw=0, want=781385532, limit=781371352
[   57.705103] attempt to access beyond end of device
[   57.705107] sdb: rw=0, want=781385533, limit=781371352
[   57.705113] attempt to access beyond end of device
[   57.705119] sdb: rw=0, want=781385534, limit=781371352
[   57.705125] attempt to access beyond end of device
[   57.705131] sdb: rw=0, want=781385535, limit=781371352
[   57.705139] attempt to access beyond end of device
[   57.705144] sdb: rw=0, want=781385531, limit=781371352
[   57.705150] attempt to access beyond end of device
[   57.705155] sdb: rw=0, want=781385532, limit=781371352
[   57.705160] attempt to access beyond end of device
[   57.705164] sdb: rw=0, want=781385533, limit=781371352
[   57.705169] attempt to access beyond end of device
[   57.705174] sdb: rw=0, want=781385534, limit=781371352
[   57.705202] attempt to access beyond end of device
[   57.705205] sdb: rw=0, want=781385535, limit=781371352
[   57.705222] attempt to access beyond end of device
[   57.705228] sdb: rw=0, want=781385531, limit=781371352
[   57.705234] attempt to access beyond end of device
[   57.705238] sdb: rw=0, want=781385532, limit=781371352
[   57.705243] attempt to access beyond end of device
[   57.705248] sdb: rw=0, want=781385533, limit=781371352
[   57.705254] attempt to access beyond end of device
[   57.705259] sdb: rw=0, want=781385534, limit=781371352
[   57.705265] attempt to access beyond end of device
[   57.705268] sdb: rw=0, want=781385535, limit=781371352
[   57.705282] attempt to access beyond end of device
[   57.705287] sdb: rw=0, want=781385531, limit=781371352
[   57.705305] attempt to access beyond end of device
[   57.705310] sdb: rw=0, want=781385532, limit=781371352
[   57.705315] attempt to access beyond end of device
[   57.705320] sdb: rw=0, want=781385533, limit=781371352
[   57.705324] attempt to access beyond end of device
[   57.705329] sdb: rw=0, want=781385534, limit=781371352
[   57.705334] attempt to access beyond end of device
[   57.705338] sdb: rw=0, want=781385535, limit=781371352
[   57.705351] attempt to access beyond end of device
[   57.705357] sdb: rw=0, want=781385531, limit=781371352
[   57.705362] attempt to access beyond end of device
[   57.705366] sdb: rw=0, want=781385532, limit=781371352
[   57.705371] attempt to access beyond end of device
[   57.705375] sdb: rw=0, want=781385533, limit=781371352
[   57.705380] attempt to access beyond end of device
[   57.705384] sdb: rw=0, want=781385534, limit=781371352
[   57.705390] attempt to access beyond end of device
[   57.705393] sdb: rw=0, want=781385535, limit=781371352
[   57.705406] attempt to access beyond end of device
[   57.705411] sdb: rw=0, want=781385531, limit=781371352
[   57.705421] attempt to access beyond end of device
[   57.705426] sdb: rw=0, want=781385532, limit=781371352
[   57.705431] attempt to access beyond end of device
[   57.705435] sdb: rw=0, want=781385533, limit=781371352
[   57.705440] attempt to access beyond end of device
[   57.705444] sdb: rw=0, want=781385534, limit=781371352
[   57.705450] attempt to access beyond end of device
[   57.705454] sdb: rw=0, want=781385535, limit=781371352
[   57.705467] attempt to access beyond end of device
[   57.705472] sdb: rw=0, want=781385531, limit=781371352
[   57.705477] attempt to access beyond end of device
[   57.705481] sdb: rw=0, want=781385532, limit=781371352
[   57.705486] attempt to access beyond end of device
[   57.705490] sdb: rw=0, want=781385533, limit=781371352
[   57.705495] attempt to access beyond end of device
[   57.705499] sdb: rw=0, want=781385534, limit=781371352
[   57.705504] attempt to access beyond end of device
[   57.705508] sdb: rw=0, want=781385535, limit=781371352
[   57.705524] attempt to access beyond end of device
[   57.705529] sdb: rw=0, want=781385467, limit=781371352
[   57.705534] attempt to access beyond end of device
[   57.705539] sdb: rw=0, want=781385468, limit=781371352
[   57.705545] attempt to access beyond end of device
[   57.705549] sdb: rw=0, want=781385469, limit=781371352
[   57.705554] attempt to access beyond end of device
[   57.705558] sdb: rw=0, want=781385470, limit=781371352
[   57.705563] attempt to access beyond end of device
[   57.705567] sdb: rw=0, want=781385471, limit=781371352
[   57.705572] attempt to access beyond end of device
[   57.705577] sdb: rw=0, want=781385472, limit=781371352
[   57.705582] attempt to access beyond end of device
[   57.705586] sdb: rw=0, want=781385473, limit=781371352
[   57.705591] attempt to access beyond end of device
[   57.705595] sdb: rw=0, want=781385474, limit=781371352
[   57.705610] attempt to access beyond end of device
[   57.705615] sdb: rw=0, want=781385523, limit=781371352
[   57.705621] attempt to access beyond end of device
[   57.705624] sdb: rw=0, want=781385524, limit=781371352
[   57.705630] attempt to access beyond end of device
[   57.705633] sdb: rw=0, want=781385525, limit=781371352
[   57.705639] attempt to access beyond end of device
[   57.705642] sdb: rw=0, want=781385526, limit=781371352
[   57.705648] attempt to access beyond end of device
[   57.705651] sdb: rw=0, want=781385527, limit=781371352
[   57.705657] attempt to access beyond end of device
[   57.705661] sdb: rw=0, want=781385528, limit=781371352
[   57.705666] attempt to access beyond end of device
[   57.705671] sdb: rw=0, want=781385529, limit=781371352
[   57.705676] attempt to access beyond end of device
[   57.705681] sdb: rw=0, want=781385530, limit=781371352
[   57.705693] attempt to access beyond end of device
[   57.705698] sdb: rw=0, want=781385531, limit=781371352
[   57.705703] attempt to access beyond end of device
[   57.705707] sdb: rw=0, want=781385532, limit=781371352
[   57.705712] attempt to access beyond end of device
[   57.705716] sdb: rw=0, want=781385533, limit=781371352
[   57.705721] attempt to access beyond end of device
[   57.705725] sdb: rw=0, want=781385534, limit=781371352
[   57.705730] attempt to access beyond end of device
[   57.705734] sdb: rw=0, want=781385535, limit=781371352
[   57.705747] attempt to access beyond end of device
[   57.705752] sdb: rw=0, want=781385531, limit=781371352
[   57.705757] attempt to access beyond end of device
[   57.705761] sdb: rw=0, want=781385532, limit=781371352
[   57.705766] attempt to access beyond end of device
[   57.705770] sdb: rw=0, want=781385533, limit=781371352
[   57.705776] attempt to access beyond end of device
[   57.705779] sdb: rw=0, want=781385534, limit=781371352
[   57.705785] attempt to access beyond end of device
[   57.705788] sdb: rw=0, want=781385535, limit=781371352
[   60.977507] Bluetooth: Core ver 2.11
[   60.977854] NET: Registered protocol family 31
[   60.977862] Bluetooth: HCI device and connection manager initialized
[   60.977866] Bluetooth: HCI socket layer initialized
[   60.990657] Bluetooth: L2CAP ver 2.8
[   60.990663] Bluetooth: L2CAP socket layer initialized
[   61.053974] Bluetooth: RFCOMM socket layer initialized
[   61.054298] Bluetooth: RFCOMM TTY layer initialized
[   61.054306] Bluetooth: RFCOMM ver 1.8
[   83.621103] UDF-fs: No VRS found
[   83.645460] ISO 9660 Extensions: Microsoft Joliet Level 3
[   83.700256] ISO 9660 Extensions: RRIP_1991A

---

### Post by Pulka on 2007-11-13
about the wireless problem, now i´m sure the problem is everytime i open Deluge. Somehow it disconnects my wireless connection. Why does it happen?

---

### Post by Pulka on 2007-11-13
please...can anyone tell me how to see the sound module to put on modprobe??

---

### Post by skymera on 2007-11-13
i have no idea about the sound.

but the wireless issue isnt uncommon.

happens to me all the bloody time =@ >:(

i usually:

sudo /etc/init.d/networking restart

thought you might like to know

---

### Post by Pulka on 2007-11-13
just found this...try it

[http://ubuntuforums.org/showpost.php?p=3755385&postcount=3](http://ubuntuforums.org/showpost.php?p=3755385&postcount=3)

---

### Post by 99bluefoxx on 2007-12-03
> **Pulka said:**
> **dmesg**
```

[   43.830651] kjournald starting.  Commit interval 5 seconds
[   43.830663] EXT3-fs: mounted filesystem with ordered data mode.
[   46.264672] usb-storage: device scan complete
[   46.265159] scsi scan: INQUIRY result too short (5), using 36
[   46.265165] scsi 4:0:0:0: CD-ROM            Toshiba  USB 2.0 CD-ROM   1.15 PQ: 0 ANSI: 0
[   46.265656] scsi 4:0:0:1: Direct-Access     Toshiba  USB 2.0 Ext. HDD 1.15 PQ: 0 ANSI: 0
[   46.267262] sr2: scsi3-mmc drive: 52x/52x cd/rw xa/form2 cdda tray
[   46.267309] sr 4:0:0:0: Attached scsi CD-ROM sr2
[   46.267355] sr 4:0:0:0: Attached scsi generic sg3 type 5
[   46.268133] sd 4:0:0:1: [sdb] 781371352 512-byte hardware sectors (400062 MB)
[   46.269006] sd 4:0:0:1: [sdb] Write Protect is off
[   46.269010] sd 4:0:0:1: [sdb] Mode Sense: 0b 00 00 08
[   46.269012] sd 4:0:0:1: [sdb] Assuming drive cache: write through
[   46.269877] sd 4:0:0:1: [sdb] 781371352 512-byte hardware sectors (400062 MB)
[   46.270750] sd 4:0:0:1: [sdb] Write Protect is off
[   46.270754] sd 4:0:0:1: [sdb] Mode Sense: 0b 00 00 08
[   46.270756] sd 4:0:0:1: [sdb] Assuming drive cache: write through
[   46.270759]  sdb: sdb1
[   46.271258]  sdb: p1 exceeds device capacity
[   46.271313] sd 4:0:0:1: [sdb] Attached SCSI disk
[   46.271355] sd 4:0:0:1: Attached scsi generic sg4 type 0
[   47.855177] attempt to access beyond end of device
[   47.855185] sdb: rw=0, want=781385395, limit=781371352
[   47.855190] Buffer I/O error on device sdb1, logical block 781384704
[   47.855197] attempt to access beyond end of device
[   47.855202] sdb: rw=0, want=781385396, limit=781371352
[   47.855206] Buffer I/O error on device sdb1, logical block 781384705
[   47.855210] attempt to access beyond end of device
[   47.855214] sdb: rw=0, want=781385397, limit=781371352
[   47.855219] Buffer I/O error on device sdb1, logical block 781384706
[   47.855224] attempt to access beyond end of device
[   47.855229] sdb: rw=0, want=781385398, limit=781371352
[   47.855234] Buffer I/O error on device sdb1, logical block 781384707
[   47.855239] attempt to access beyond end of device
[   47.855243] sdb: rw=0, want=781385399, limit=781371352
[   47.855246] Buffer I/O error on device sdb1, logical block 781384708
[   47.855251] attempt to access beyond end of device
[   47.855255] sdb: rw=0, want=781385400, limit=781371352
[   47.855259] Buffer I/O error on device sdb1, logical block 781384709
[   47.855263] attempt to access beyond end of device
[   47.855267] sdb: rw=0, want=781385401, limit=781371352
[   47.855272] Buffer I/O error on device sdb1, logical block 781384710
[   47.855277] attempt to access beyond end of device
[   47.855281] sdb: rw=0, want=781385402, limit=781371352
[   47.855286] Buffer I/O error on device sdb1, logical block 781384711
[   47.855294] attempt to access beyond end of device
[   47.855298] sdb: rw=0, want=781385395, limit=781371352
[   47.855303] Buffer I/O error on device sdb1, logical block 781384704
[   47.855308] attempt to access beyond end of device
[   47.855311] sdb: rw=0, want=781385396, limit=781371352
[   47.855316] Buffer I/O error on device sdb1, logical block 781384705
[   47.855321] attempt to access beyond end of device
[   47.855325] sdb: rw=0, want=781385397, limit=781371352
[   47.855330] attempt to access beyond end of device
[   47.855333] sdb: rw=0, want=781385398, limit=781371352
[   47.855338] attempt to access beyond end of device
[   47.855343] sdb: rw=0, want=781385399, limit=781371352
[   47.855348] attempt to access beyond end of device
[   47.855352] sdb: rw=0, want=781385400, limit=781371352
[   47.855355] attempt to access beyond end of device
[   47.855359] sdb: rw=0, want=781385401, limit=781371352
[   47.855362] attempt to access beyond end of device
[   47.855366] sdb: rw=0, want=781385402, limit=781371352
[   47.855388] attempt to access beyond end of device
[   47.855392] sdb: rw=0, want=781385515, limit=781371352
[   47.855396] attempt to access beyond end of device
[   47.855400] sdb: rw=0, want=781385516, limit=781371352
[   47.855404] attempt to access beyond end of device
[   47.855407] sdb: rw=0, want=781385517, limit=781371352
[   47.855411] attempt to access beyond end of device
[   47.855414] sdb: rw=0, want=781385518, limit=781371352
[   47.855418] attempt to access beyond end of device
[   47.855422] sdb: rw=0, want=781385519, limit=781371352
[   47.855426] attempt to access beyond end of device
[   47.855429] sdb: rw=0, want=781385520, limit=781371352
[   47.855433] attempt to access beyond end of device
[   47.855437] sdb: rw=0, want=781385521, limit=781371352
[   47.855441] attempt to access beyond end of device
[   47.855444] sdb: rw=0, want=781385522, limit=781371352
[   47.855451] attempt to access beyond end of device
[   47.855455] sdb: rw=0, want=781385515, limit=781371352
[   47.855459] attempt to access beyond end of device
[   47.855462] sdb: rw=0, want=781385516, limit=781371352
[   47.855466] attempt to access beyond end of device
[   47.855470] sdb: rw=0, want=781385517, limit=781371352
[   47.855474] attempt to access beyond end of device
[   47.855477] sdb: rw=0, want=781385518, limit=781371352
[   47.855480] attempt to access beyond end of device
[   47.855484] sdb: rw=0, want=781385519, limit=781371352
[   47.855488] attempt to access beyond end of device
[   47.855492] sdb: rw=0, want=781385520, limit=781371352
[   47.855496] attempt to access beyond end of device
[   47.855499] sdb: rw=0, want=781385521, limit=781371352
[   47.855503] attempt to access beyond end of device
[   47.855506] sdb: rw=0, want=781385522, limit=781371352
[   47.866084] attempt to access beyond end of device
[   47.866092] sdb: rw=0, want=781385531, limit=781371352
[   47.866097] attempt to access beyond end of device
[   47.866102] sdb: rw=0, want=781385532, limit=781371352
[   47.866106] attempt to access beyond end of device
[   47.866110] sdb: rw=0, want=781385533, limit=781371352
[   47.866113] attempt to access beyond end of device
[   47.866117] sdb: rw=0, want=781385534, limit=781371352
[   47.866121] attempt to access beyond end of device
[   47.866124] sdb: rw=0, want=781385535, limit=781371352
[   47.866131] attempt to access beyond end of device
[   47.866134] sdb: rw=0, want=781385531, limit=781371352
[   47.866138] attempt to access beyond end of device
[   47.866141] sdb: rw=0, want=781385532, limit=781371352
[   47.866145] attempt to access beyond end of device
[   47.866148] sdb: rw=0, want=781385533, limit=781371352
[   47.866152] attempt to access beyond end of device
[   47.866155] sdb: rw=0, want=781385534, limit=781371352
[   47.866159] attempt to access beyond end of device
[   47.866162] sdb: rw=0, want=781385535, limit=781371352
[   47.866174] attempt to access beyond end of device
[   47.866178] sdb: rw=0, want=781385531, limit=781371352
[   47.866181] attempt to access beyond end of device
[   47.866185] sdb: rw=0, want=781385532, limit=781371352
[   47.866188] attempt to access beyond end of device
[   47.866192] sdb: rw=0, want=781385533, limit=781371352
[   47.866195] attempt to access beyond end of device
[   47.866199] sdb: rw=0, want=781385534, limit=781371352
[   47.866202] attempt to access beyond end of device
[   47.866206] sdb: rw=0, want=781385535, limit=781371352
[   47.866218] attempt to access beyond end of device
[   47.866222] sdb: rw=0, want=781385531, limit=781371352
[   47.866227] attempt to access beyond end of device
[   47.866230] sdb: rw=0, want=781385532, limit=781371352
[   47.866234] attempt to access beyond end of device
[   47.866237] sdb: rw=0, want=781385533, limit=781371352
[   47.866242] attempt to access beyond end of device
[   47.866245] sdb: rw=0, want=781385534, limit=781371352
[   47.866250] attempt to access beyond end of device
[   47.866253] sdb: rw=0, want=781385535, limit=781371352
[   47.866263] attempt to access beyond end of device
[   47.866268] sdb: rw=0, want=781385531, limit=781371352
[   47.866273] attempt to access beyond end of device
[   47.866276] sdb: rw=0, want=781385532, limit=781371352
[   47.866280] attempt to access beyond end of device
[   47.866283] sdb: rw=0, want=781385533, limit=781371352
[   47.866288] attempt to access beyond end of device
[   47.866292] sdb: rw=0, want=781385534, limit=781371352
[   47.866296] attempt to access beyond end of device
[   47.866300] sdb: rw=0, want=781385535, limit=781371352
[   47.866311] attempt to access beyond end of device
[   47.866315] sdb: rw=0, want=781385531, limit=781371352
[   47.866320] attempt to access beyond end of device
[   47.866324] sdb: rw=0, want=781385532, limit=781371352
[   47.866328] attempt to access beyond end of device
[   47.866331] sdb: rw=0, want=781385533, limit=781371352
[   47.866335] attempt to access beyond end of device
[   47.866339] sdb: rw=0, want=781385534, limit=781371352
[   47.866344] attempt to access beyond end of device
[   47.866348] sdb: rw=0, want=781385535, limit=781371352
[   47.866359] attempt to access beyond end of device
[   47.866363] sdb: rw=0, want=781385531, limit=781371352
[   47.866368] attempt to access beyond end of device
[   47.866371] sdb: rw=0, want=781385532, limit=781371352
[   47.866376] attempt to access beyond end of device
[   47.866379] sdb: rw=0, want=781385533, limit=781371352
[   47.866383] attempt to access beyond end of device
[   47.866387] sdb: rw=0, want=781385534, limit=781371352
[   47.866391] attempt to access beyond end of device
[   47.866395] sdb: rw=0, want=781385535, limit=781371352
[   47.866410] attempt to access beyond end of device
[   47.866415] sdb: rw=0, want=781385467, limit=781371352
[   47.866419] attempt to access beyond end of device
[   47.866423] sdb: rw=0, want=781385468, limit=781371352
[   47.866427] attempt to access beyond end of device
[   47.866431] sdb: rw=0, want=781385469, limit=781371352
[   47.866435] attempt to access beyond end of device
[   47.866439] sdb: rw=0, want=781385470, limit=781371352
[   47.866443] attempt to access beyond end of device
[   47.866446] sdb: rw=0, want=781385471, limit=781371352
[   47.866451] attempt to access beyond end of device
[   47.866454] sdb: rw=0, want=781385472, limit=781371352
[   47.866459] attempt to access beyond end of device
[   47.866463] sdb: rw=0, want=781385473, limit=781371352
[   47.866467] attempt to access beyond end of device
[   47.866470] sdb: rw=0, want=781385474, limit=781371352
[   47.866486] attempt to access beyond end of device
[   47.866490] sdb: rw=0, want=781385523, limit=781371352
[   47.866495] attempt to access beyond end of device
[   47.866499] sdb: rw=0, want=781385524, limit=781371352
[   47.866503] attempt to access beyond end of device
[   47.866507] sdb: rw=0, want=781385525, limit=781371352
[   47.866511] attempt to access beyond end of device
[   47.866515] sdb: rw=0, want=781385526, limit=781371352
[   47.866519] attempt to access beyond end of device
[   47.866522] sdb: rw=0, want=781385527, limit=781371352
[   47.866526] attempt to access beyond end of device
[   47.866530] sdb: rw=0, want=781385528, limit=781371352
[   47.866534] attempt to access beyond end of device
[   47.866538] sdb: rw=0, want=781385529, limit=781371352
[   47.866541] attempt to access beyond end of device
[   47.866545] sdb: rw=0, want=781385530, limit=781371352
[   47.866557] attempt to access beyond end of device
[   47.866561] sdb: rw=0, want=781385531, limit=781371352
[   47.866565] attempt to access beyond end of device
[   47.866568] sdb: rw=0, want=781385532, limit=781371352
[   47.866572] attempt to access beyond end of device
[   47.866576] sdb: rw=0, want=781385533, limit=781371352
[   47.866580] attempt to access beyond end of device
[   47.866583] sdb: rw=0, want=781385534, limit=781371352
[   47.866588] attempt to access beyond end of device
[   47.866591] sdb: rw=0, want=781385535, limit=781371352
[   47.866603] attempt to access beyond end of device
[   47.866607] sdb: rw=0, want=781385531, limit=781371352
[   47.866611] attempt to access beyond end of device
[   47.866615] sdb: rw=0, want=781385532, limit=781371352
[   47.866619] attempt to access beyond end of device
[   47.866622] sdb: rw=0, want=781385533, limit=781371352
[   47.866626] attempt to access beyond end of device
[   47.866630] sdb: rw=0, want=781385534, limit=781371352
[   47.866634] attempt to access beyond end of device
[   47.866637] sdb: rw=0, want=781385535, limit=781371352
[   49.338525] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   49.340835] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   49.352240] intel_rng: FWH not detected
[   49.402410] iTCO_vendor_support: vendor-support=0
[   49.403733] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   49.403823] iTCO_wdt: Found a ICH6 or ICH6R TCO device (Version=2, TCOBASE=0x0860)
[   49.403880] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   49.533556] Linux agpgart interface v0.102 (c) Dave Jones
[   50.007899] logips2pp: Detected unknown logitech mouse model 89
[   50.130024] gameport: EMU10K1 is pci0000:01:0a.1/gameport0, io 0xbc00, speed 917kHz
[   50.439108] nvidia: module license 'NVIDIA' taints kernel.
[   50.695748] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   50.695768] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   50.696035] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.23  Thu Oct  4 10:16:34 PDT 2007
[   50.702223] input: PC Speaker as /class/input/input2
[   50.717732] input: ImExPS/2 Logitech Explorer Mouse as /class/input/input3
[   50.730183] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   50.730200] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   50.730227] sky2 0000:02:00.0: v1.18 addr 0xd2efc000 irq 17 Yukon-EC (0xb6) rev 1
[   50.730376] sky2 eth0: addr 00:11:2f:3c:06:4b
[   50.826712] parport_pc 00:07: reported by Plug and Play ACPI
[   50.826822] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   50.877234] ACPI: PCI Interrupt 0000:01:0a.0[A] -> GSI 21 (level, low) -> IRQ 22
[   50.881432] Installing spdif_bug patch: Audigy 1 ES [SB0160]
[   50.937035] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   50.937056] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   51.754802] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: usb_submit_urb(ctrl) failed
[   51.754816] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: timeout initializing reports
[   51.754898] input: Logitech Logitech Dual Action as /class/input/input4
[   51.754930] input: USB HID v1.10 Joystick [Logitech Logitech Dual Action] on usb-0000:00:1d.3-1
[   51.754948] usbcore: registered new interface driver usbhid
[   51.754953] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   51.818601] usbcore: registered new interface driver xpad
[   51.818606] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[   52.576745] lp0: using parport0 (interrupt-driven).
[   52.653436] ndiswrapper version 1.49 loaded (smp=yes, preempt=no)
[   52.708375] ndiswrapper: driver mrv8ka51 (Marvell,05/20/2004,2.3.0.19) loaded
[   52.708592] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 20 (level, low) -> IRQ 23
[   52.709303] ndiswrapper: using IRQ 23
[   52.970358] wlan0: ethernet device 00:11:2f:3c:12:05 using NDIS driver: mrv8ka51, version: 0x203000c, NDIS version: 0x501, vendor: 'Marvell 802.11 Driver', 11AB:1FA7.5.conf
[   52.970379] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   52.970445] usbcore: registered new interface driver ndiswrapper
[   53.024609] Adding 2088440k swap on /dev/sda2.  Priority:-1 extents:1 across:2088440k
[   53.481968] EXT3 FS on sda4, internal journal
[   53.997597] kjournald starting.  Commit interval 5 seconds
[   53.997837] EXT3 FS on sda8, internal journal
[   53.997843] EXT3-fs: mounted filesystem with ordered data mode.
[   55.221942] input: Power Button (FF) as /class/input/input5
[   55.221971] ACPI: Power Button (FF) [PWRF]
[   55.222082] input: Power Button (CM) as /class/input/input6
[   55.222104] ACPI: Power Button (CM) [PWRB]
[   55.361170] No dock devices found.
[   55.633045] NET: Registered protocol family 17
[   56.524778] ppdev: user-space parallel port driver
[   56.603705] audit(1194981684.873:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5271 profile="/usr/sbin/cupsd"
[   56.711027] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   56.711033] apm: disabled - APM is not SMP safe.
[   56.775015] sky2 eth0: enabling interface
[   57.167206] Failure registering capabilities with primary security module.
[   57.702393] attempt to access beyond end of device
[   57.702402] sdb: rw=0, want=781385395, limit=781371352
[   57.702408] printk: 83 messages suppressed.
[   57.702411] Buffer I/O error on device sdb1, logical block 781384704
[   57.702451] attempt to access beyond end of device
[   57.702458] sdb: rw=0, want=781385396, limit=781371352
[   57.702496] attempt to access beyond end of device
[   57.702503] sdb: rw=0, want=781385397, limit=781371352
[   57.702545] attempt to access beyond end of device
[   57.702551] sdb: rw=0, want=781385398, limit=781371352
[   57.702559] attempt to access beyond end of device
[   57.702565] sdb: rw=0, want=781385399, limit=781371352
[   57.702603] attempt to access beyond end of device
[   57.702608] sdb: rw=0, want=781385400, limit=781371352
[   57.702616] attempt to access beyond end of device
[   57.702622] sdb: rw=0, want=781385401, limit=781371352
[   57.702664] attempt to access beyond end of device
[   57.702671] sdb: rw=0, want=781385402, limit=781371352
[   57.702739] attempt to access beyond end of device
[   57.702745] sdb: rw=0, want=781385395, limit=781371352
[   57.702753] attempt to access beyond end of device
[   57.702759] sdb: rw=0, want=781385396, limit=781371352
[   57.702802] attempt to access beyond end of device
[   57.702807] sdb: rw=0, want=781385397, limit=781371352
[   57.702811] attempt to access beyond end of device
[   57.702814] sdb: rw=0, want=781385398, limit=781371352
[   57.702818] attempt to access beyond end of device
[   57.702822] sdb: rw=0, want=781385399, limit=781371352
[   57.702826] attempt to access beyond end of device
[   57.702829] sdb: rw=0, want=781385400, limit=781371352
[   57.702832] attempt to access beyond end of device
[   57.702836] sdb: rw=0, want=781385401, limit=781371352
[   57.702839] attempt to access beyond end of device
[   57.702842] sdb: rw=0, want=781385402, limit=781371352
[   57.702862] attempt to access beyond end of device
[   57.702866] sdb: rw=0, want=781385515, limit=781371352
[   57.702870] attempt to access beyond end of device
[   57.702874] sdb: rw=0, want=781385516, limit=781371352
[   57.702878] attempt to access beyond end of device
[   57.702882] sdb: rw=0, want=781385517, limit=781371352
[   57.702886] attempt to access beyond end of device
[   57.702890] sdb: rw=0, want=781385518, limit=781371352
[   57.702894] attempt to access beyond end of device
[   57.702897] sdb: rw=0, want=781385519, limit=781371352
[   57.702901] attempt to access beyond end of device
[   57.702905] sdb: rw=0, want=781385520, limit=781371352
[   57.702909] attempt to access beyond end of device
[   57.702912] sdb: rw=0, want=781385521, limit=781371352
[   57.702916] attempt to access beyond end of device
[   57.702920] sdb: rw=0, want=781385522, limit=781371352
[   57.702926] attempt to access beyond end of device
[   57.702931] sdb: rw=0, want=781385515, limit=781371352
[   57.702934] attempt to access beyond end of device
[   57.702938] sdb: rw=0, want=781385516, limit=781371352
[   57.702942] attempt to access beyond end of device
[   57.702945] sdb: rw=0, want=781385517, limit=781371352
[   57.702950] attempt to access beyond end of device
[   57.702955] sdb: rw=0, want=781385518, limit=781371352
[   57.702962] attempt to access beyond end of device
[   57.702969] sdb: rw=0, want=781385519, limit=781371352
[   57.702984] attempt to access beyond end of device
[   57.702991] sdb: rw=0, want=781385520, limit=781371352
[   57.703006] attempt to access beyond end of device
[   57.703013] sdb: rw=0, want=781385521, limit=781371352
[   57.703073] attempt to access beyond end of device
[   57.703079] sdb: rw=0, want=781385522, limit=781371352
[   57.705078] attempt to access beyond end of device
[   57.705085] sdb: rw=0, want=781385531, limit=781371352
[   57.705092] attempt to access beyond end of device
[   57.705096] sdb: rw=0, want=781385532, limit=781371352
[   57.705103] attempt to access beyond end of device
[   57.705107] sdb: rw=0, want=781385533, limit=781371352
[   57.705113] attempt to access beyond end of device
[   57.705119] sdb: rw=0, want=781385534, limit=781371352
[   57.705125] attempt to access beyond end of device
[   57.705131] sdb: rw=0, want=781385535, limit=781371352
[   57.705139] attempt to access beyond end of device
[   57.705144] sdb: rw=0, want=781385531, limit=781371352
[   57.705150] attempt to access beyond end of device
[   57.705155] sdb: rw=0, want=781385532, limit=781371352
[   57.705160] attempt to access beyond end of device
[   57.705164] sdb: rw=0, want=781385533, limit=781371352
[   57.705169] attempt to access beyond end of device
[   57.705174] sdb: rw=0, want=781385534, limit=781371352
[   57.705202] attempt to access beyond end of device
[   57.705205] sdb: rw=0, want=781385535, limit=781371352
[   57.705222] attempt to access beyond end of device
[   57.705228] sdb: rw=0, want=781385531, limit=781371352
[   57.705234] attempt to access beyond end of device
[   57.705238] sdb: rw=0, want=781385532, limit=781371352
[   57.705243] attempt to access beyond end of device
[   57.705248] sdb: rw=0, want=781385533, limit=781371352
[   57.705254] attempt to access beyond end of device
[   57.705259] sdb: rw=0, want=781385534, limit=781371352
[   57.705265] attempt to access beyond end of device
[   57.705268] sdb: rw=0, want=781385535, limit=781371352
[   57.705282] attempt to access beyond end of device
[   57.705287] sdb: rw=0, want=781385531, limit=781371352
[   57.705305] attempt to access beyond end of device
[   57.705310] sdb: rw=0, want=781385532, limit=781371352
[   57.705315] attempt to access beyond end of device
[   57.705320] sdb: rw=0, want=781385533, limit=781371352
[   57.705324] attempt to access beyond end of device
[   57.705329] sdb: rw=0, want=781385534, limit=781371352
[   57.705334] attempt to access beyond end of device
[   57.705338] sdb: rw=0, want=781385535, limit=781371352
[   57.705351] attempt to access beyond end of device
[   57.705357] sdb: rw=0, want=781385531, limit=781371352
[   57.705362] attempt to access beyond end of device
[   57.705366] sdb: rw=0, want=781385532, limit=781371352
[   57.705371] attempt to access beyond end of device
[   57.705375] sdb: rw=0, want=781385533, limit=781371352
[   57.705380] attempt to access beyond end of device
[   57.705384] sdb: rw=0, want=781385534, limit=781371352
[   57.705390] attempt to access beyond end of device
[   57.705393] sdb: rw=0, want=781385535, limit=781371352
[   57.705406] attempt to access beyond end of device
[   57.705411] sdb: rw=0, want=781385531, limit=781371352
[   57.705421] attempt to access beyond end of device
[   57.705426] sdb: rw=0, want=781385532, limit=781371352
[   57.705431] attempt to access beyond end of device
[   57.705435] sdb: rw=0, want=781385533, limit=781371352
[   57.705440] attempt to access beyond end of device
[   57.705444] sdb: rw=0, want=781385534, limit=781371352
[   57.705450] attempt to access beyond end of device
[   57.705454] sdb: rw=0, want=781385535, limit=781371352
[   57.705467] attempt to access beyond end of device
[   57.705472] sdb: rw=0, want=781385531, limit=781371352
[   57.705477] attempt to access beyond end of device
[   57.705481] sdb: rw=0, want=781385532, limit=781371352
[   57.705486] attempt to access beyond end of device
[   57.705490] sdb: rw=0, want=781385533, limit=781371352
[   57.705495] attempt to access beyond end of device
[   57.705499] sdb: rw=0, want=781385534, limit=781371352
[   57.705504] attempt to access beyond end of device
[   57.705508] sdb: rw=0, want=781385535, limit=781371352
[   57.705524] attempt to access beyond end of device
[   57.705529] sdb: rw=0, want=781385467, limit=781371352
[   57.705534] attempt to access beyond end of device
[   57.705539] sdb: rw=0, want=781385468, limit=781371352
[   57.705545] attempt to access beyond end of device
[   57.705549] sdb: rw=0, want=781385469, limit=781371352
[   57.705554] attempt to access beyond end of device
[   57.705558] sdb: rw=0, want=781385470, limit=781371352
[   57.705563] attempt to access beyond end of device
[   57.705567] sdb: rw=0, want=781385471, limit=781371352
[   57.705572] attempt to access beyond end of device
[   57.705577] sdb: rw=0, want=781385472, limit=781371352
[   57.705582] attempt to access beyond end of device
[   57.705586] sdb: rw=0, want=781385473, limit=781371352
[   57.705591] attempt to access beyond end of device
[   57.705595] sdb: rw=0, want=781385474, limit=781371352
[   57.705610] attempt to access beyond end of device
[   57.705615] sdb: rw=0, want=781385523, limit=781371352
[   57.705621] attempt to access beyond end of device
[   57.705624] sdb: rw=0, want=781385524, limit=781371352
[   57.705630] attempt to access beyond end of device
[   57.705633] sdb: rw=0, want=781385525, limit=781371352
[   57.705639] attempt to access beyond end of device
[   57.705642] sdb: rw=0, want=781385526, limit=781371352
[   57.705648] attempt to access beyond end of device
[   57.705651] sdb: rw=0, want=781385527, limit=781371352
[   57.705657] attempt to access beyond end of device
[   57.705661] sdb: rw=0, want=781385528, limit=781371352
[   57.705666] attempt to access beyond end of device
[   57.705671] sdb: rw=0, want=781385529, limit=781371352
[   57.705676] attempt to access beyond end of device
[   57.705681] sdb: rw=0, want=781385530, limit=781371352
[   57.705693] attempt to access beyond end of device
[   57.705698] sdb: rw=0, want=781385531, limit=781371352
[   57.705703] attempt to access beyond end of device
[   57.705707] sdb: rw=0, want=781385532, limit=781371352
[   57.705712] attempt to access beyond end of device
[   57.705716] sdb: rw=0, want=781385533, limit=781371352
[   57.705721] attempt to access beyond end of device
[   57.705725] sdb: rw=0, want=781385534, limit=781371352
[   57.705730] attempt to access beyond end of device
[   57.705734] sdb: rw=0, want=781385535, limit=781371352
[   57.705747] attempt to access beyond end of device
[   57.705752] sdb: rw=0, want=781385531, limit=781371352
[   57.705757] attempt to access beyond end of device
[   57.705761] sdb: rw=0, want=781385532, limit=781371352
[   57.705766] attempt to access beyond end of device
[   57.705770] sdb: rw=0, want=781385533, limit=781371352
[   57.705776] attempt to access beyond end of device
[   57.705779] sdb: rw=0, want=781385534, limit=781371352
[   57.705785] attempt to access beyond end of device
[   57.705788] sdb: rw=0, want=781385535, limit=781371352
[   60.977507] Bluetooth: Core ver 2.11
[   60.977854] NET: Registered protocol family 31
[   60.977862] Bluetooth: HCI device and connection manager initialized
[   60.977866] Bluetooth: HCI socket layer initialized
[   60.990657] Bluetooth: L2CAP ver 2.8
[   60.990663] Bluetooth: L2CAP socket layer initialized
[   61.053974] Bluetooth: RFCOMM socket layer initialized
[   61.054298] Bluetooth: RFCOMM TTY layer initialized
[   61.054306] Bluetooth: RFCOMM ver 1.8
[   83.621103] UDF-fs: No VRS found
[   83.645460] ISO 9660 Extensions: Microsoft Joliet Level 3
[   83.700256] ISO 9660 Extensions: RRIP_1991A

```

can you put that whole chunk in [ CODE ] and [/ CODE ] tags, removing the spaces, so that it doesnt take forever to scroll down to the rest of the page please?
thanks
i was just wondering, would a linksys wireless g 2.4 ghz 802.11g PCMCIA notebook adaptorfrom about 2003ish work in linux automatically?or would i have to manually configure it
im considering getting a barebones second hand laptop and installing this thing in it, and using it for on-the-fly stuff like, short music videos, music ideas that may come to mind, and other such things[playing stepmania, music, movies with friends] i figured i should start checking hardware compatability before i buy it now.

---

