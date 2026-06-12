---
title: "Help with D-Link AirPlus DWL-650+ card config"
date: 2005-10-02
forum: Apple PPC Users
---

### Post by Adam Boettiger on 2005-10-02
Hello -

I'm trying to get wireless access on my G4 Mac PowerBook laptop that is dual-partitioned with Linux Ubuntu and Mac OS X. The internal Airport Extreme card that comes with the unit is not compatible with Ubuntu, so I reviewed the vendor and device list and selected the PCMCIA card that seemed like it had worked for most people right out of the box. I am having trouble configuring it to work with my home WLAN to give me broadband internet access.

The card I am trying to configure is:

D-Link AirPlus DWL-650+ 2.4GHz Wireless Cardbus Adapter. I've quoted and provided some of the relevant information you requested and included it below. Any help in getting this to work would be greatly appreciated! Thanks in advance.

Adam Boettiger


1. If this is a question about getting a component PCI device working; soundcards, network cards, wireless network cards, video cards, etc... paste in the output of

/sbin/lspci

<output>
boettiger@ubuntu:/sbin$ lspci
0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 AGP
0000:00:10.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 PCI
0001:10:12.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
0001:10:13.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
0001:10:17.0 ff00: Apple Computer Inc. KeyLargo/Intrepid Mac I/O
0001:10:18.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
0001:10:19.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
0001:10:1a.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
0001:10:1b.0 USB Controller: NEC Corporation USB (rev 43)
0001:10:1b.1 USB Controller: NEC Corporation USB (rev 43)
0001:10:1b.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
0001:11:00.0 Network controller: Texas Instruments ACX 100 22Mbps Wireless Interface
0002:24:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 Internal PCI
0002:24:0d.0 ff00: Apple Computer Inc. UniNorth/Intrepid ATA/100
0002:24:0e.0 FireWire (IEEE 1394): Apple Computer Inc. UniNorth 2 FireWire (rev 81)
0002:24:0f.0 ffff: Apple Computer Inc. UniNorth 2 GMAC (Sun GEM) (rev ff)
boettiger@ubuntu:/sbin$

</output>

2. Next up, what kernel AND distro are you using, the VIA 8233 sound card worked in 2.4.16, then disappeared until 2.4.20. This is of course unless you are using Mandrake or SuSe who had working ALSA modules. When in doubt of the kernel:

uname -r

<output>
Linux Ubuntu, Hoary v5.04
boettiger@ubuntu:/$ uname -r
2.6.12-8-powerpc
</output>

3. If the problem stems from a laptop pcmcia card, similar info to /sbin/lspci can be found from:

/sbin/cardctl ident

<output>
boettiger@ubuntu:/sbin$ cardctl ident
Socket 0:
  no product info available
</output>

That is of course unless its a Cardbus card, they're pretty easy to tell apart, it'll be marked on the card, it'll probably be a big selling point on the packing, the manual, etc. too. Cardbus cards appear under /sbin/lspci, pretty neat eh?

5. When in doubt, drop in some logs. For instance, the command: "dmesg", is literally, the kernel ring buffer, its a record of everything the kernel saw as it loaded, in order.

<output>
boettiger@ubuntu:/$ dmesg
.au)
[   77.146067] devfs: boot_options: 0x0
[   77.146105] Initializing Cryptographic API
[   77.146358] PCI: Enabling device 0000:00:10.0 (0006 -> 0007)
[   77.346795] radeonfb (0000:00:10.0): Invalid ROM signature 303 should be0xaa55
[   77.346806] radeonfb: Retreived PLL infos from Open Firmware
[   77.346811] radeonfb: Reference=27.00 MHz (RefDiv=12) Memory=200.00 Mhz, System=300.00 MHz
[   77.346816] radeonfb: PLL min 12000 max 35000
[   77.917419] radeonfb: Monitor 1 type LCD found
[   77.917424] radeonfb: EDID probed
[   77.917427] radeonfb: Monitor 2 type no found
[   77.917438] radeonfb: Using Firmware dividers 0x00040080 from PPLL 0
[   77.917492] radeonfb: Dynamic Clock Power Management enabled
[   77.975779] Console: switching to colour frame buffer device 180x56
[   77.975839] Registered "mnca" backlight controller,level: 15/15
[   77.975843] radeonfb (0000:00:10.0): ATI Radeon NP
[   77.977821] Generic RTC Driver v1.07
[   77.977862] Macintosh non-volatile memory driver v1.1
[   77.977892] serial8250_init: nothing to do on PowerMac
[   77.977938] pmac_zilog: 0.6 (Benjamin Herrenschmidt <benh@kernel.crashing.org>)
[   77.977951] ttyS0 at MMIO 0x80013020 (irq = 22) is a Z85c30 ESCC - Serial port
[   77.977991] ttyS1 at MMIO 0x80013000 (irq = 23) is a Z85c30 ESCC - Serial port
[   77.978045] io scheduler noop registered
[   77.978065] io scheduler anticipatory registered
[   77.978071] io scheduler deadline registered
[   77.978083] io scheduler cfq registered
[   77.978567] RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
[   77.978678] MacIO PCI driver attached to Intrepid chipset
[   77.979198] input: Macintosh mouse button emulation
[   77.979288] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   77.979296] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   77.979376] adb: starting probe task...
[   77.980243] PCI: Enabling device 0002:24:0d.0 (0000 -> 0002)
[   78.234049] adb devices: [2]: 2 c3 [3]: 3 1 [7]: 7 1f
[   78.240559] ADB keyboard at 2, handler 1
[   78.240567] Detected ADB keyboard, type ANSI.
[   78.240608] input: ADB keyboard on adb2:2.c3/input
[   78.240636] input: ADB Powerbook buttons on adb7:7.1f/input
[   78.255763] ADB mouse at 3, handler set to 4 (trackpad)
[   78.315363] input: ADB mouse on adb3:3.01/input
[   78.315366] adb: finished probe task...
[   78.992404] ide0: Found Apple UniNorth ATA-6 controller, bus ID 3, irq 39
[   78.992417] Probing IDE interface ide0...
[   79.256582] hda: FUJITSU MHT2080AT, ATA DISK drive
[   79.868401] hda: Enabling Ultra DMA 5
[   79.871456] ide0 at 0xf101a000-0xf101a007,0xf101a160 on irq 39
[   80.883383] ide1: Found Apple KeyLargo ATA-3 controller, bus ID 0, irq 24
[   80.883395] Probing IDE interface ide1...
[   81.249556] hdc: MATSHITADVD-R UJ-816, ATAPI CD/DVD-ROM drive
[   81.555392] ide1 at 0xf100e000-0xf100e007,0xf100e160 on irq 24
[   81.555584] mice: PS/2 mouse device common for all mice
[   81.555694] Found KeyWest i2c on "uni-n", 2 channels, stepping: 4 bits
[   81.555777] Found KeyWest i2c on "mac-io", 1 channel, stepping: 4 bits
[   81.555814] NET: Registered protocol family 2
[   81.564441] IP: routing cache hash table of 8192 buckets, 64Kbytes
[   81.564789] TCP established hash table entries: 262144 (order: 9, 2097152 bytes)
[   81.570599] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[   81.570945] TCP: Hash tables configured (established 262144 bind 65536)
[   81.571056] Freeing unused kernel memory: 172k init 4k chrp 32k prep
[   81.639572] NET: Registered protocol family 1
[   81.760022] usbcore: registered new driver usbfs
[   81.760066] usbcore: registered new driver hub
[   81.761483] ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[   81.761542] Apple USB OHCI 0001:10:18.0 disabled by firmware
[   81.761552] Apple USB OHCI 0001:10:19.0 disabled by firmware
[   81.761563] PCI: Enabling device 0001:10:1a.0 (0000 -> 0002)
[   81.761581] ohci_hcd 0001:10:1a.0: Apple Computer Inc. KeyLargo/Intrepid USB (#3)
[   81.761663] ohci_hcd 0001:10:1a.0: new USB bus registered, assigned bus number 1
[   81.761676] ohci_hcd 0001:10:1a.0: irq 29, io mem 0xa0003000
[   81.792501] hub 1-0:1.0: USB hub found
[   81.792517] hub 1-0:1.0: 2 ports detected
[   81.813407] PCI: Enabling device 0001:10:1b.0 (0000 -> 0002)
[   81.813419] ohci_hcd 0001:10:1b.0: NEC Corporation USB
[   81.813479] ohci_hcd 0001:10:1b.0: new USB bus registered, assigned bus number 2
[   81.813489] ohci_hcd 0001:10:1b.0: irq 63, io mem 0xa0002000
[   81.844465] hub 2-0:1.0: USB hub found
[   81.844477] hub 2-0:1.0: 3 ports detected
[   81.865392] PCI: Enabling device 0001:10:1b.1 (0000 -> 0002)
[   81.865402] ohci_hcd 0001:10:1b.1: NEC Corporation USB (#2)
[   81.865446] ohci_hcd 0001:10:1b.1: new USB bus registered, assigned bus number 3
[   81.865454] ohci_hcd 0001:10:1b.1: irq 63, io mem 0xa0001000
[   81.896415] usb 1-1: new full speed USB device using ohci_hcd and address 2
[   81.896493] hub 3-0:1.0: USB hub found
[   81.896508] hub 3-0:1.0: 2 ports detected
[   81.997848] PCI: Enabling device 0001:10:1b.2 (0004 -> 0006)
[   81.997868] ehci_hcd 0001:10:1b.2: NEC Corporation USB 2.0
[   82.018429] ehci_hcd 0001:10:1b.2: new USB bus registered, assigned bus number 4
[   82.018444] ehci_hcd 0001:10:1b.2: irq 63, io mem 0xa0000000
[   82.018487] ehci_hcd 0001:10:1b.2: park 0
[   82.018496] ehci_hcd 0001:10:1b.2: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[   82.018630] hub 4-0:1.0: USB hub found
[   82.018645] hub 4-0:1.0: 5 ports detected
[   82.105504] sungem.c:v0.98 8/24/03 David S. Miller (davem@redhat.com)
[   82.167727] PHY ID: 1410cc1, addr: 0
[   82.168114] eth0: Sun GEM (PCI) 10/100/1000BaseT Ethernet 00:0a:95:97:32:d8
[   82.168122] eth0: Found Marvell 88E1101 PHY
[   83.042363] usb 2-1: new full speed USB device using ohci_hcd and address 2
[   83.149424] hub 2-1:1.0: USB hub found
[   83.152383] hub 2-1:1.0: 4 ports detected
[   83.442378] usb 2-1.1: new full speed USB device using ohci_hcd and address 3[   83.489379] usb 2-1.1: not running at top speed; connect to a high speed hub
[   83.655377] usb 2-1.3: new low speed USB device using ohci_hcd and address 4
[   84.277593] SCSI subsystem initialized
[   84.281295] Initializing USB Mass Storage driver...
[   84.283405] scsi0 : SCSI emulation for USB Mass Storage devices
[   84.283485] usb-storage: device found at 3
[   84.283489] usb-storage: waiting for device to settle before scanning
[   84.283501] usbcore: registered new driver usb-storage
[   84.283505] USB Mass Storage support registered.
[   84.302285] usbcore: registered new driver hiddev
[   84.311459] input: USB HID v1.10 Mouse [Logitech USB Trackball] on usb-0001:10:1b.0-1.3
[   84.311470] usbcore: registered new driver usbhid
[   84.311474] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
[   84.382377] hda: max request size: 1024KiB
[   84.445880] hda: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
[   84.448845] hda: cache flushes supported
[   84.448941]  /dev/ide/host0/bus0/target0/lun0: [mac] p1 p2 p3 p4 p5 p6
[   84.463041] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
[   84.463052] Uniform CD-ROM driver Revision: 3.20
[   84.942118] Attempting manual resume
[   84.963381] swsusp: Suspend partition has wrong signature?
[   85.016055] kjournald starting.  Commit interval 5 seconds
[   85.016073] EXT3-fs: mounted filesystem with ordered data mode.
[   86.126770] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[   89.303336]   Vendor: I0MEGA    Model: Mini512MB*IOM2A3  Rev: 4.70
[   89.303356]   Type:   Direct-Access                      ANSI SCSI revision: 00
[   89.324506] usb-storage: device scan complete
[   89.458400] Adding 657072k swap on /dev/hda5.  Priority:-1 extents:1
[   89.666399] EXT3 FS on hda3, internal journal
[   93.842296] SCSI device sda: 1019392 512-byte hdwr sectors (522 MB)
[   93.848302] sda: Write Protect is off
[   93.848308] sda: Mode Sense: 45 00 00 08
[   93.848311] sda: assuming drive cache: write through
[   93.868292] SCSI device sda: 1019392 512-byte hdwr sectors (522 MB)
[   93.875306] sda: Write Protect is off
[   93.875310] sda: Mode Sense: 45 00 00 08
[   93.875313] sda: assuming drive cache: write through
[   93.875322]  /dev/scsi/host0/bus0/target0/lun0: p1
[   93.889326] Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0[   95.455344] apm_emu: APM Emulation 0.5 initialized.
[   95.762028] ieee1394: Initialized config rom entry `ip1394'
[   95.771807] sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
[   96.813847] adt746x: version 1 (supported)
[   96.813857] adt746x: Thermostat bus: 1, address: 0x2e, limit_adjust: 0, fan_speed: -1
[   96.813863] sensor 0: CPU/INTREPID BOTTOMSIDE
[   96.813867] sensor 1: CPU BOTTOMSIDE
[   96.813871] sensor 2: PWR SUPPLY BOTTOMSIDE
[   96.842549] adt746x: ADT7460 initializing
[   96.845240] adt746x: Lowering max temperatures from 73, 73, 73 to 70, 50, 70
[   96.847385] adt746x: Setting speed to 0 for CPU BOTTOMSIDE fan.
[   96.864269] adt746x: Setting speed to 0 for PWR SUPPLY BOTTOMSIDE fan.
[   99.380351] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[  100.166050] hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
[  100.166061] hdc: packet command error: error=0x50 { LastFailedSense=0x05 }
[  100.166067] ide: failed opcode was: unknown
[  100.166798] cdrom: open failed.
[  102.322088] Linux agpgart interface v0.101 (c) Dave Jones
[  102.338021] agpgart: Detected Apple UniNorth 2 chipset
[  102.338114] agpgart: configuring for size idx: 4
[  102.351872] agpgart: AGP aperture is 16M @ 0x0
[  102.657089] Linux Kernel Card Services
[  102.657100]   options:  [pci] [cardbus] [pm]
[  102.682062] Yenta: CardBus bridge found at 0001:10:13.0 [0000:0000]
[  102.682103] Yenta: Enabling burst memory read transactions
[  102.682109] Yenta: Using CSCINT to route CSC interrupts to PCI
[  102.682113] Yenta: Routing CardBus interrupts to PCI
[  102.682119] Yenta TI: socket 0001:10:13.0, mfunc 0x00001002, devctl 0x60
[  102.782178] Yenta: ISA IRQ mask 0x0000, PCI irq 53
[  102.782182] Socket status: 30000020
[  103.738668] acx100: It looks like you've been coaxed into buying a wireless network card
[  103.738678] acx100: that uses the mysterious ACX100/ACX111 chip from Texas Instruments.
[  103.738681] acx100: You should better have bought e.g. a PRISM(R) chipset based card,
[  103.738684] acx100: since that would mean REAL vendor Linux support.
[  103.738687] acx100: Given this info, it's evident that this driver is still EXPERIMENTAL,
[  103.738690] acx100: thus your mileage may vary. Reading README file and/or Craig's HOWTO is
[  103.738693] recommended, visit [http://acx100.sf.net](http://acx100.sf.net) in case of further questions/discussion.
[  103.738704] acx100: Warning: compiled to use 16bit I/O access only (compatibility mode). Set Makefile ACX_IO_WIDTH=32 to use slightly problematic 32bit mode
[  103.738710] Running on a BIG-ENDIAN CPU
[  103.738713] acx_init_module: dev_info is: TI acx_pci
[  103.738717] acx_init_module: TI acx_pci.o: Ver 0.2.0pre8 driver initialized, waiting for cards to probe...
[  103.746019] PCI: Enabling device 0001:11:00.0 (0000 -> 0003)
[  103.746064] Found ACX100-based wireless network card at 0001:11:00.0, irq:53, phymem1:0xf3010000, phymem2:0xf3000000, mem1:0xf25b6000, mem1_size:4096, mem2:0xf2680000, mem2_size:65536
[  103.746071] initial debug setting is 0x001b
[  103.746088] acx_select_io_register_set: using ACX100 io resource addresses (size: 56)
[  103.746092] hw_unavailable = 1
[  103.746098] acx_probe_pci: TI acx_pci: Using IRQ 53
[  103.746121] reset hw_unavailable++
[  103.746128] acx_reset_mac: enable soft reset...
[  103.746133] acx_reset_mac: disable soft reset and go to init mode...
[  103.763250] Requesting firmware image 'WLANGEN.BIN'
[  103.867120] not using auto increment for firmware loading
[  103.939124] acx_write_fw: firmware written
[  104.008558] acx_write_fw (firmware): 0, acx_validate_fw: 0
[  104.018151] acx_reset_dev: boot up eCPU and wait for complete...
[  104.218150] acx_reset_dev: Received signal that card is ready to be configured :) (the eCPU has woken up)
[  104.236733] reset hw_unavailable--
[  104.236749] acx100: allocated net device wlan0, driver compiled against wireless extensions v17 and Linux 2.6.12-8-powerpc
[  104.237161] ******************************************
[  104.237164] ************* acx_init_mac_1 *************
[  104.237168] ******************************************
[  104.237171] ==> Get the mailbox pointers from the scratch pad registers
[  104.237180] CmdMailboxOffset = fdc8
[  104.237181] InfoMailboxOffset = ff4c
[  104.237183] <== Get the mailbox pointers from the scratch pad registers
[  104.237189] CommandParameters = [ 0xf268fdcc ]
[  104.237190] InfoParameters = [ 0xf268ff50 ]
[  104.237290] Requesting firmware image 'RADIO0d.BIN'
[  104.305237] not using auto increment for firmware loading
[  104.305994] acx_write_fw: firmware written
[  104.306706] acx_write_fw (radio): 0, acx_validate_fw: 0
[  104.454348] CodeEnd:50A20000
[  104.454438] acx100_init_wep: writing WEP options.
[  104.457668] get_mask 0x00004d82, set_mask 0x00000000
[  104.457739] Got sensitivity value 176
[  104.457802] Got antenna value 0x8D
[  104.457866] Got Energy Detect (ED) threshold 112
[  104.457929] Got Channel Clear Assessment (CCA) value 13
[  104.457989] Got regulatory domain 0x10
[  104.457995] get_mask 0x00000000, set_mask 0x00000000 - after update
[  104.458408] new ratevector: 82 84 0b 16 2c
[  104.458415] setting RXconfig to 2000:0000
[  104.458478] Beacon length:59
[  104.458640] hw_unavailable--
[  104.458718] acx100: form factor 0x01 ((mini-)PCI / CardBus), radio type 0x0d (Maxim), EEPROM version 0x05. Uploaded firmware 'Rev 1.9.8.b' (0x01030505).
[  104.460467] creating /proc entry driver/acx_wlan0
[  104.460484] creating /proc entry driver/acx_wlan0_diag
[  104.460489] creating /proc entry driver/acx_wlan0_eeprom
[  104.460494] creating /proc entry driver/acx_wlan0_phy
[  104.460499] acx_probe_pci: TI acx_pci.o: Ver 0.2.0pre8 loaded successfully
[  104.470604] ohci1394: $Rev: 1250 $ Ben Collins <bcollins@debian.org>
[  104.470638] PCI: Enabling device 0002:24:0e.0 (0000 -> 0002)
[  104.473808] ohci1394: fw-host0: Unexpected PCI resource length of 1000!
[  104.526095] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[40]  MMIO=[f5000000-f50007ff]  Max Packet=[4096]
[  105.797580] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000a95fffe9732d8]
[  105.876458] Bluetooth: Core ver 2.7
[  105.876473] NET: Registered protocol family 31
[  105.876476] Bluetooth: HCI device and connection manager initialized
[  105.876492] Bluetooth: HCI socket layer initialized
[  105.879968] Bluetooth: HCI USB driver ver 2.8
[  105.883622] usbcore: registered new driver hci_usb
[  107.018627] ts: Compaq touchscreen protocol output
[  121.829439] Bluetooth: L2CAP ver 2.7
[  121.829449] Bluetooth: L2CAP socket layer initialized
[  121.918892] Bluetooth: RFCOMM ver 1.5
[  121.918910] Bluetooth: RFCOMM socket layer initialized
[  121.918925] Bluetooth: RFCOMM TTY layer initialized
[  154.398093] NET: Registered protocol family 10
[  154.398318] Disabled Privacy Extensions on device c026ad58(lo)
[  154.398523] IPv6 over IPv4 tunneling driver
[  165.803624] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[ 1020.181484] cs: memory probe 0x80000000-0x80ffffff: excluding 0x80000000-0x80ffffff
boettiger@ubuntu:/$
</output>

Other good ones, bits of /var/log/messages 

Couldn't get an output, but here is the ls directory:

<output>
boettiger@ubuntu:/var/log$ messages
bash: messages: command not found
boettiger@ubuntu:/var/log$ ls
aptitude                debug              fontconfig.log  scrollkeeper.log
aptitude.1.gz           debug.0            gdm             scrollkeeper.log.1
auth.log                dmesg              installer       syslog
auth.log.0              dpkg.log           kern.log        syslog.0
base-config.log.1       dpkg.log.1         kern.log.0      syslog.1.gz
base-config-pkgsel.log  evms-engine.1.log  lastlog         syslog.2.gz
base-config.timings.1   evms-engine.2.log  lpr.log         syslog.3.gz
bootstrap.log           evms-engine.3.log  mail.err        user.log
btmp                    evms-engine.4.log  mail.info       user.log.0
btmp.1                  evms-engine.5.log  mail.log        uucp.log
cups                    evms-engine.6.log  mail.warn       wtmp
daemon.log              evms-engine.7.log  messages        wtmp.1
daemon.log.0            evms-engine.log    messages.0      Xorg.0.log
debian-installer        faillog            news            Xorg.0.log.old
boettiger@ubuntu:/var/log$
</output>

Thank you.

Adam Boettiger
Portland, Oregon

---

### Post by refdoc on 2005-10-03
dmesg - seesm to recognise teh card as one poorly supported, but then moves on to configure it as wlan0

It also suggest you looking at it [http://acx100.sf.net](http://acx100.sf.net),

Please give the output of 'ifconfig' and 'iwconfig'

---

### Post by Adam Boettiger on 2005-10-09
oettiger@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b+  ESSID:"STA89FE0A"  Nickname:"acx100 v0.2.0pre8"
          Mode:Auto  Channel:1  Access Point: 00:00:00:00:00:00
          Bit Rate=22 Mb/s   Tx-Power=18 dBm   Sensitivity=176/255
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

boettiger@ubuntu:~$

---

### Post by Adam Boettiger on 2005-10-09
boettiger@ubuntu:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1636 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1636 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:147347 (143.8 KiB)  TX bytes:147347 (143.8 KiB)

boettiger@ubuntu:~$

seems like the card is not powering up (no lights)

---

### Post by transactionlogfiller on 2005-11-10
You may find this site helpfull

[http://www.houseofcraig.net/acx100_howto.php](http://www.houseofcraig.net/acx100_howto.php)

---

### Post by spacey on 2005-11-29
Hi!
I've got this card working by disabling the acx100 module, and using ndiswrapper with the Windows drivers.

---

