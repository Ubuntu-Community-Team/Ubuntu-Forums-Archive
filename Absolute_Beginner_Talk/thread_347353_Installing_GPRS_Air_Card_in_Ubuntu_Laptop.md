---
title: "Installing GPRS Air Card in Ubuntu Laptop"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by uk_falang on 2007-01-27
Hi
I am TOTALLY new to Linux, I have a fresh install of Ubuntu which i downloaded and installed yesterday.

I live in Thailand, I work for an NGO. I am trying to set up an Internet Cafe based on Linux to promote free software in Thailand, a place people dont have money to buy licenses etc.  Initially I have one computer and I need to use a GPRS (EDGE) card because there is a waiting list for ADSL connections.

I would really appreciate any help with this...

Hi
I am trying to install Sierra Wireless Aircard into Ubuntu. I am totally new to Linux and am installing from instructions. The Sierra instructions at the bottom of this message. I would greatly appreciate any help to get my computer online with Linux. I have to use Aircard as there is a long wait for ADSL in my area. I cant ask Sierra to help me as they dont offer support in Linux. It seesm they have only tested their card in mandrake and redhat.

I have done the following:

Downloaded and unpacked the drivers

1) sudo -i
2) EnteredPassword
3) Made a directory makedir /etc/pcmcia/cis
3) cp'd the SW_775_SER.dat to root@ubuntumarc:/etc/pcmcia/cis
4) cd to /etc/pcmcia/config.opts...gedit config.opts
5) See file below I added the instructions for Sierra Wireless 775 then saved the config file (just pressed save button) file .
6) Restarted computer
7) Apparently there should have been two short beeps but there were none. This was meant to indicate that the card was found.

I am now trying to understand this (from Sierra Wireless Instruction guide)"The Aircard can be accessed as dev/modem when inserted" What is dev/modem? I cant find this folder and i dont get two beeps when i insert the aircard. Also it mentions minicom - what is minicom?






# Local PCMCIA Configuration File
#
#----------------------------------------------------------------------
#
# System resources available for PCMCIA cards
#
# NOTE: these settings have no effect on resources assigned to a
# CardBus bridge device itself; this file only affects resources
# assigned to cards. Also, interrupt settings here will only affect
# ISA bus interrupts assigned to 16-bit cards. PCI interrupts
# generally can't be reconfigured.
#
# With the kernel PCMCIA subsystem, these settings also have no effect
# at all on resources used for 32-bit CardBus cards. Those are set by
# the PCI hotplug subsystem.
#

include port 0x100-0x3af
include port 0x3e0-0x4ff
include port 0x820-0x8ff
include port 0xc00-0xcf7

include memory 0xc0000-0xfffff
include memory 0xa0000000-0xa0ffffff
include memory 0x60000000-0x60ffffff

card "Sierra Wireless AC775 EDGE Network Adapter R1"
manfid 0x0192, 0x0710
cis "cis/SW_775_SER.dat"
bind "serial_cs"


# These may hurt on FSC.
# include port 0x3c0-0x3d2
# Exclude 0x3d3 as Radeon IGP MCE's if you touch these ports
# include port 0x3d4-0x3df

# High port numbers do not always work...
# include port 0x1000-0x17ff

# Extra port range for IBM Token Ring
include port 0xa00-0xaff


SIERRA INSTRUCTIONS

Guide to Sierra Wireless AirCard 775 for Linux

Question:

Can i use the Sierra Wireless AirCard 775 with a Linux OS?

Answer:


Guide to Sierra Wireless AirCard 775 for Linux

Please note: This guide is unsupported and is provided to the Linux user community as a courtesy. Linux users who would like to install and run the Sierra Wireless 775 on GPRS/EDGE network can use this document as a guide.

This document covers the following product:
Sierra Wireless AirCard® 775

This configuration has been tested on RedHat 7.0, Red Hat 7.3, Red Hat 9.0 and Mandrake 8.1.

Note: You must be logged in as root.

Before You Begin

Click here to download the AirCard_7XX_Linux.tar.gz file. You can extract the files in the AirCard_7XX_Linux.tar.gz by executing the following commands in terminal window:

gunzip AirCard_7XX_Linux.tar.gz

tar - xvf AirCard_7XX_Linux.tar

The AirCard_7XX_Linux.tar contains:

SW_7xx_SER.dat, ac750, ac750chat, SW_775_SER.dat, ac775, ac775chat files

How to Configure Linux to Recognize AirCard 775

Before you start, make sure that the AirCard is not inserted into the PCMCIA slot.
The following instructions will configure the AirCard as a serial-only device on Linux:

1. Add the following to /etc/pcmcia/config under the Modems and other serial devices:

card "Sierra Wireless AC775 EDGE Network Adapter R1"
manfid 0x0192, 0x0710
cis "cis/SW_775_SER.dat"
bind "serial_cs"

2. Copy the file SW_775_SER.dat in this archive in /etc/pcmcia/cis/
3. Restart computer.
4. Insert the AirCard 775


When the card is inserted two high beeps should be heard, indicating that the AirCard has been recognized and the serial driver has been successfully loaded. The AirCard can be accessed as /dev/modem when inserted. Running minicom should allow access to the AT command interface.

How to Configure Dialup Networking

A valid SIM card, user name, password, and APN are required to configure dialup networking.



1. Copy the files ac775 and ac775chat into /etc/ppp/peers.


2. Edit the existing file /etc/ppp/pap-secrets to add the following line:

"< login>""< login>" "" "*"

Replace < login> with the user name and < password> with the account password.
(e.g. "sierra" "sierra" "mypasswd" "*")

3. Edit the file /etc/ppp/peers/ac775 to replace < login> in the line
"user < login>"with the same < login> name as the previous instruction. (e.g. user sierra)

4. Edit the file /etc/ppp/peers/ac775 so that the second line is:

OK AT+cgdcont= 1,"IP","< APN>"

The < APN> should be replaced with the APN for the network.
(e.g. for Rogers network OK AT+cgdcont=1,"IP","internet.com")

How to Connect to the GPRS Network

Before you start, make sure the LED on the AirCard is flashing green. If there is a problem connecting (dialed too soon after inserting card or other problem) eject and re-insert the card.

1. Connect using PPPD

pppd call ac775

NOTE:
Some pppd version may not correctly set up the dynamic DNS configuration. It may be necessary to copy /etc/ppp/resolv.conf to /etc/resolv.conf.

In order to terminate the connection send pppd the tem signal (Ctrl-C).

2. Connect using KPPP

It is also possible to connect using a dialer (e.g. Kppp in KDE).

1. Run KPPP configuration and click on New
2. Click on Dialog Setup and type in the name of connection.
3. Type *99# for phone number and select PAP for authentication.
4. Select Modem tab and for initialization string type in:

at+cgdcont= 1,"IP","< APN>"
where < APN> is the network APN and click on OK


5. Type in Login ID and Password
Where Login ID and Password are user name and password from your account.
6. Click on Connect.

3. Signal Strength

The RSSI (signal quality) and be read by starting minicom and issuing the command:

at+csq

The first number indicates the signal strength above -109 dBm (in 2 dBm increments). A value of 7 or higher (-95 dBm) can be considered adequate

---

### Post by SqdnGuns on 2007-01-27
After you pop in the Air Card, open a terminal and type "dmesg". If the the card is detected, you will see it in the output of dmesg. Post what your dmesg says here.

/dev is the directory for all the devices on your box. Read more here - [http://www.oreilly.com/catalog/debian/chapter/book/ch11_02.html](http://www.oreilly.com/catalog/debian/chapter/book/ch11_02.html)

Where in Thailand are you? I am moving there next week, up near Surin.

---

### Post by uk_falang on 2007-01-27
I forgot to mention...

I tried to use the command line to extract the tar ball, the second line of the extraction command (see instructions by sierra) didnt work so i used the provided packager program to do this

---

### Post by uk_falang on 2007-01-27
> **SqdnGuns said:**
> After you pop in the Air Card, open a terminal and type "dmesg". If the the card is detected, you will see it in the output of dmesg. Post what your dmesg says here.

/dev is the directory for all the devices on your box. Read more here - [http://www.oreilly.com/catalog/debian/chapter/book/ch11_02.html](http://www.oreilly.com/catalog/debian/chapter/book/ch11_02.html)

Where in Thailand are you? I am moving there next week, up near Surin.

thanks for your reply
I am in Chiang Rai

Here is the dmseg

#02) (try 'pci=assign-busses')
[17179570.432000] Please report the result to linux-kernel to fix this permanently
[17179570.432000] PCI: Bus #07 (-#0a) is hidden behind transparent bridge #02 (-#02) (try 'pci=assign-busses')
[17179570.432000] Please report the result to linux-kernel to fix this permanently
[17179570.432000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.440000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[17179570.440000] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *5
[17179570.440000] ACPI: PCI Interrupt Link [LNKB] (IRQs *10 11)
[17179570.440000] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *4
[17179570.440000] ACPI: PCI Interrupt Link [LNKD] (IRQs *11)
[17179570.440000] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[17179570.440000] ACPI: PCI Interrupt Link [LNKF] (IRQs *10 11)
[17179570.444000] ACPI: PCI Interrupt Link [LNKG] (IRQs *10 11)
[17179570.444000] ACPI: PCI Interrupt Link [LNKH] (IRQs *10 11)
[17179570.444000] ACPI: Embedded Controller [EC] (gpe 28) interrupt mode.
[17179570.448000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.448000] pnp: PnP ACPI init
[17179570.652000] pnp: PnP ACPI: found 10 devices
[17179570.652000] PnPBIOS: Disabled by ACPI PNP
[17179570.652000] PCI: Using ACPI for IRQ routing
[17179570.652000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.656000] pnp: 00:04: ioport range 0x600-0x60f has been reserved
[17179570.656000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[17179570.656000] PCI: Bus 3, cardbus bridge: 0000:02:04.0
[17179570.656000]   IO window: 00003400-000034ff
[17179570.656000]   IO window: 00003800-000038ff
[17179570.656000]   PREFETCH window: 20000000-21ffffff
[17179570.656000]   MEM window: 26000000-27ffffff
[17179570.656000] PCI: Bus 7, cardbus bridge: 0000:02:04.1
[17179570.656000]   IO window: 00003c00-00003cff
[17179570.656000]   IO window: 00001400-000014ff
[17179570.656000]   PREFETCH window: 22000000-23ffffff
[17179570.656000]   MEM window: 28000000-29ffffff
[17179570.656000] PCI: Bridge: 0000:00:1e.0
[17179570.656000]   IO window: 3000-3fff
[17179570.656000]   MEM window: e0200000-e02fffff
[17179570.656000]   PREFETCH window: 20000000-24ffffff
[17179570.656000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179570.656000] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 10
[17179570.656000] PCI: setting IRQ 10 as level-triggered
[17179570.656000] ACPI: PCI Interrupt 0000:02:04.0[A] -> Link [LNKF] -> GSI 10 (level, low) -> IRQ 10
[17179570.656000] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 10
[17179570.656000] ACPI: PCI Interrupt 0000:02:04.1[B] -> Link [LNKG] -> GSI 10 (level, low) -> IRQ 10
[17179570.656000] NET: Registered protocol family 2
[17179570.692000] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[17179570.692000] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[17179570.692000] TCP bind hash table entries: 4096 (order: 3, 32768 bytes)
[17179570.692000] TCP: Hash tables configured (established 8192 bind 4096)
[17179570.692000] TCP reno registered
[17179570.692000] Simple Boot Flag at 0x3c set to 0x1
[17179570.692000] audit: initializing netlink socket (disabled)
[17179570.692000] audit(1169918752.692:1): initialized
[17179570.692000] VFS: Disk quotas dquot_6.5.1
[17179570.692000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.692000] Initializing Cryptographic API
[17179570.692000] io scheduler noop registered
[17179570.692000] io scheduler anticipatory registered
[17179570.692000] io scheduler deadline registered
[17179570.692000] io scheduler cfq registered (default)
[17179570.692000] isapnp: Scanning for PnP cards...
[17179571.048000] isapnp: No Plug & Play device found
[17179571.148000] Real Time Clock Driver v1.12ac
[17179571.148000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179571.152000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[17179571.152000] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[17179571.152000] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[17179571.152000] mice: PS/2 mouse device common for all mice
[17179571.152000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179571.156000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179571.156000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179571.156000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179571.156000] i8042.c: Detected active multiplexing controller, rev 1.1.
[17179571.156000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[17179571.160000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[17179571.160000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[17179571.160000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[17179571.160000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179571.160000] EISA: Probing bus 0 at eisa.0
[17179571.160000] Cannot allocate resource for EISA slot 1
[17179571.160000] Cannot allocate resource for EISA slot 2
[17179571.160000] Cannot allocate resource for EISA slot 3
[17179571.160000] EISA: Detected 0 cards.
[17179571.160000] TCP bic registered
[17179571.160000] NET: Registered protocol family 1
[17179571.160000] NET: Registered protocol family 8
[17179571.160000] NET: Registered protocol family 20
[17179571.160000] Using IPI No-Shortcut mode
[17179571.160000] ACPI: (supports S0 S3 S4 S5)
[17179571.160000] Freeing unused kernel memory: 308k freed
[17179571.320000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179572.396000] Capability LSM initialized
[17179572.460000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[17179572.512000] ACPI: Thermal Zone [THRS] (47 C)
[17179572.560000] ACPI: Thermal Zone [THRC] (41 C)
[17179573.404000] ICH4: IDE controller at PCI slot 0000:00:1f.1
[17179573.404000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[17179573.404000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[17179573.404000] PCI: setting IRQ 11 as level-triggered
[17179573.404000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179573.404000] ICH4: chipset revision 3
[17179573.404000] ICH4: not 100% native mode: will probe irqs later
[17179573.404000]     ide0: BM-DMA at 0x1810-0x1817, BIOS settings: hda:DMA, hdb:pio
[17179573.404000]     ide1: BM-DMA at 0x1818-0x181f, BIOS settings: hdc:DMA, hdd:pio
[17179573.404000] Probing IDE interface ide0...
[17179573.692000] hda: IC25N030ATMR04-0, ATA DISK drive
[17179574.364000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179574.384000] Probing IDE interface ide1...
[17179575.120000] hdc: QSI CD-RW/DVD-ROM SBW-242, ATAPI CD/DVD-ROM drive
[17179575.792000] ide1 at 0x170-0x177,0x376 on irq 15
[17179575.800000] hda: max request size: 512KiB
[17179575.816000] hda: 58605120 sectors (30005 MB) w/1740KiB Cache, CHS=16383/255/63, UDMA(100)
[17179575.816000] hda: cache flushes supported
[17179575.816000]  hda: hda1 hda2 hda3 hda4 < hda5 hda6 hda7 >
[17179575.908000] hdc: ATAPI 8X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179575.908000] Uniform CD-ROM driver Revision: 3.20
[17179576.528000] usbcore: registered new driver usbfs
[17179576.528000] usbcore: registered new driver hub
[17179576.532000] USB Universal Host Controller Interface driver v3.0
[17179576.536000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[17179576.536000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179576.536000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179576.536000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179576.536000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179576.536000] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00001820
[17179576.536000] usb usb1: configuration #1 chosen from 1 choice
[17179576.540000] hub 1-0:1.0: USB hub found
[17179576.540000] hub 1-0:1.0: 2 ports detected
[17179576.644000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[17179576.644000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179576.644000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179576.644000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179576.644000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179576.644000] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001840
[17179576.644000] usb usb2: configuration #1 chosen from 1 choice
[17179576.644000] hub 2-0:1.0: USB hub found
[17179576.644000] hub 2-0:1.0: 2 ports detected
[17179576.748000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179576.748000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179576.748000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179576.748000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179576.748000] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001860
[17179576.748000] usb usb3: configuration #1 chosen from 1 choice
[17179576.748000] hub 3-0:1.0: USB hub found
[17179576.748000] hub 3-0:1.0: 2 ports detected
[17179576.856000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10
[17179576.856000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 10 (level, low) -> IRQ 10
[17179576.856000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179576.856000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179576.856000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[17179576.856000] ehci_hcd 0000:00:1d.7: debug port 1
[17179576.856000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[17179576.856000] ehci_hcd 0000:00:1d.7: irq 10, io mem 0xe0100000
[17179576.860000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179576.860000] usb usb4: configuration #1 chosen from 1 choice
[17179576.860000] hub 4-0:1.0: USB hub found
[17179576.860000] hub 4-0:1.0: 6 ports detected
[17179577.044000] Attempting manual resume
[17179577.124000] kjournald starting.  Commit interval 5 seconds
[17179577.124000] EXT3-fs: mounted filesystem with ordered data mode.
[17179592.280000] Floppy drive(s): fd0 is 1.44M
[17179592.296000] FDC 0 is a National Semiconductor PC87306
[17179592.948000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179592.960000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179593.032000] hw_random: RNG not detected
[17179593.156000] Linux agpgart interface v0.101 (c) Dave Jones
[17179593.164000] agpgart: Detected an Intel 855 Chipset.
[17179593.164000] agpgart: Detected 16252K stolen memory.
[17179593.172000] agpgart: AGP aperture is 128M @ 0xe8000000
[17179593.340000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[17179593.340000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[17179593.496000] parport: PnPBIOS parport detected.
[17179593.496000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[17179593.624000] 8139too Fast Ethernet driver 0.9.27
[17179593.800000] Synaptics Touchpad, model: 1, fw: 5.8, id: 0x9248b1, caps: 0x904713/0x4000
[17179593.844000] input: SynPS/2 Synaptics TouchPad as /class/input/input1
[17179593.904000] ts: Compaq touchscreen protocol output
[17179594.760000] intel8x0_measure_ac97_clock: measured 55324 usecs
[17179594.760000] intel8x0: clocking to 48000
[17179594.760000] ACPI: PCI Interrupt 0000:02:04.0[A] -> Link [LNKF] -> GSI 10 (level, low) -> IRQ 10
[17179594.760000] Yenta: CardBus bridge found at 0000:02:04.0 [1025:0039]
[17179594.764000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179594.764000] Yenta: Routing CardBus interrupts to PCI
[17179594.764000] Yenta TI: socket 0000:02:04.0, mfunc 0x00921b22, devctl 0x64
[17179594.996000] Yenta: ISA IRQ mask 0x0038, PCI irq 10
[17179594.996000] Socket status: 30000006
[17179594.996000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[17179594.996000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[17179594.996000] cs: IO port probe 0x3000-0x3fff: clean.
[17179594.996000] pcmcia: parent PCI bridge Memory window: 0xe0200000 - 0xe02fffff
[17179594.996000] pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x24ffffff
[17179594.996000] ACPI: PCI Interrupt 0000:02:0a.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179594.996000] eth0: RealTek RTL8139 at 0xcf9f4000, 00:0a:e4:44:81:0b, IRQ 11
[17179594.996000] eth0:  Identified 8139 chip type 'RTL-8101'
[17179595.004000] ACPI: PCI Interrupt 0000:02:04.1[B] -> Link [LNKG] -> GSI 10 (level, low) -> IRQ 10
[17179595.004000] Yenta: CardBus bridge found at 0000:02:04.1 [1025:0039]
[17179595.004000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179595.004000] Yenta: Routing CardBus interrupts to PCI
[17179595.004000] Yenta TI: socket 0000:02:04.1, mfunc 0x00921b22, devctl 0x64
[17179595.004000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179595.236000] Yenta: ISA IRQ mask 0x0038, PCI irq 10
[17179595.236000] Socket status: 30000006
[17179595.236000] Yenta: Raising subordinate bus# of parent bus (#02) from #06 to #0a
[17179595.236000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[17179595.236000] cs: IO port probe 0x3000-0x3fff: clean.
[17179595.236000] pcmcia: parent PCI bridge Memory window: 0xe0200000 - 0xe02fffff
[17179595.236000] pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x24ffffff
[17179595.868000] cs: IO port probe 0x100-0x3af: clean.
[17179595.880000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179595.880000] cs: IO port probe 0x820-0x8ff: clean.
[17179595.880000] cs: IO port probe 0xc00-0xcf7: clean.
[17179595.884000] cs: IO port probe 0x100-0x3af: clean.
[17179595.884000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179595.884000] cs: IO port probe 0x820-0x8ff: clean.
[17179595.888000] cs: IO port probe 0xc00-0xcf7: clean.
[17179595.996000] lp0: using parport0 (interrupt-driven).
[17179596.048000] Adding 353388k swap on /dev/disk/by-uuid/01ffcebb-972f-498f-9c82-ad0fb018e8ce.  Priority:-1 extents:1 across:353388k
[17179596.116000] EXT3 FS on hda6, internal journal
[17179597.952000] ACPI: AC Adapter [AC] (on-line)
[17179598.604000] ACPI: Battery Slot [BAT0] (battery present)
[17179598.624000] ACPI: Power Button (FF) [PWRF]
[17179598.624000] ACPI: Lid Switch [LID]
[17179598.624000] ACPI: Sleep Button (CM) [SLP2]
[17179598.812000] ibm_acpi: ec object not found
[17179598.848000] pcc_acpi: loading...
[17179598.984000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[17179601.516000] [drm] Initialized drm 1.0.1 20051102
[17179601.520000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179601.520000] [drm] Initialized i915 1.5.0 20060119 on minor 0
[17179601.524000] [drm] Initialized i915 1.5.0 20060119 on minor 1
[17179603.156000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179603.156000] apm: overridden by ACPI.
[17179615.168000] NET: Registered protocol family 10
[17179615.168000] lo: Disabled Privacy Extensions
[17179615.168000] IPv6 over IPv4 tunneling driver
[17179618.124000] Bluetooth: Core ver 2.8
[17179618.124000] NET: Registered protocol family 31
[17179618.124000] Bluetooth: HCI device and connection manager initialized
[17179618.124000] Bluetooth: HCI socket layer initialized
[17179618.660000] Bluetooth: L2CAP ver 2.8
[17179618.660000] Bluetooth: L2CAP socket layer initialized
[17179618.892000] Bluetooth: RFCOMM socket layer initialized
[17179618.892000] Bluetooth: RFCOMM TTY layer initialized
[17179618.892000] Bluetooth: RFCOMM ver 1.7
[17179622.688000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17179623.016000] ISOFS: changing to secondary root
[17179642.616000] pccard: PCMCIA card inserted into slot 1
[17179642.616000] cs: memory probe 0xe0200000-0xe02fffff: excluding 0xe0200000-0xe020ffff
[17179642.620000] pcmcia: registering new device pcmcia1.0
[17179788.852000] pccard: card ejected from slot 1
[17183350.400000] usb 4-5: new high speed USB device using ehci_hcd and address 2
[17183350.532000] usb 4-5: configuration #1 chosen from 1 choice
[17183350.684000] usbcore: registered new driver libusual
[17183350.784000] SCSI subsystem initialized
[17183350.788000] Initializing USB Mass Storage driver...
[17183350.788000] scsi0 : SCSI emulation for USB Mass Storage devices
[17183350.792000] usbcore: registered new driver usb-storage
[17183350.792000] USB Mass Storage support registered.
[17183350.792000] usb-storage: device found at 2
[17183350.792000] usb-storage: waiting for device to settle before scanning
[17183355.792000] usb-storage: device scan complete
[17183355.792000]   Vendor: Generic   Model: USB SD Reader     Rev: 1.00
[17183355.792000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17183355.792000]   Vendor: Generic   Model: USB CF Reader     Rev: 1.01
[17183355.792000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17183355.792000]   Vendor: Generic   Model: USB SM Reader     Rev: 1.02
[17183355.792000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17183355.792000]   Vendor: Generic   Model: USB MS Reader     Rev: 1.03
[17183355.792000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17183356.624000] SCSI device sda: 498176 512-byte hdwr sectors (255 MB)
[17183356.624000] sda: Write Protect is off
[17183356.624000] sda: Mode Sense: 03 00 00 00
[17183356.624000] sda: assuming drive cache: write through
[17183356.624000] SCSI device sda: 498176 512-byte hdwr sectors (255 MB)
[17183356.628000] sda: Write Protect is off
[17183356.628000] sda: Mode Sense: 03 00 00 00
[17183356.628000] sda: assuming drive cache: write through
[17183356.628000]  sda: sda1
[17183356.628000] sd 0:0:0:0: Attached scsi removable disk sda
[17183356.668000] sd 0:0:0:1: Attached scsi removable disk sdb
[17183356.708000] sd 0:0:0:2: Attached scsi removable disk sdc
[17183356.740000] sd 0:0:0:3: Attached scsi removable disk sdd
[17183356.780000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17183356.780000] sd 0:0:0:1: Attached scsi generic sg1 type 0
[17183356.780000] sd 0:0:0:2: Attached scsi generic sg2 type 0
[17183356.784000] sd 0:0:0:3: Attached scsi generic sg3 type 0
[17183357.340000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17184471.488000] usb 4-5: USB disconnect, address 2
[17184471.532000]  0:0:0:1: rejecting I/O to dead device
[17184471.532000]  0:0:0:1: rejecting I/O to dead device
[17184471.532000]  0:0:0:1: rejecting I/O to dead device
[17184471.532000]  0:0:0:1: rejecting I/O to dead device
[17184471.532000] sdb : READ CAPACITY failed.
[17184471.532000] sdb : status=0, message=00, host=1, driver=00 
[17184471.532000] sdb : sense not available. 
[17184471.532000]  0:0:0:1: rejecting I/O to dead device
[17184471.532000] sdb: Write Protect is off
[17184471.532000] sdb: Mode Sense: 00 00 00 00
[17184471.532000] sdb: assuming drive cache: write through
[17184471.532000]  0:0:0:1: rejecting I/O to dead device
[17184471.532000]  0:0:0:1: rejecting I/O to dead device
[17184471.532000]  0:0:0:1: rejecting I/O to dead device
[17184471.532000]  0:0:0:1: rejecting I/O to dead device
[17184471.532000]  0:0:0:1: rejecting I/O to dead device
[17184471.532000] sdb : READ CAPACITY failed.
[17184471.532000] sdb : status=0, message=00, host=1, driver=00 
[17184471.532000] sdb : sense not available. 
[17184471.532000]  0:0:0:1: rejecting I/O to dead device
[17184471.532000] sdb: Write Protect is off
[17184471.532000] sdb: Mode Sense: 00 00 00 00
[17184471.532000] sdb: assuming drive cache: write through
[17184471.532000]  sdb:<3> 0:0:0:1: rejecting I/O to dead device
[17184471.532000] Buffer I/O error on device sdb, logical block 0
[17184471.532000]  0:0:0:1: rejecting I/O to dead device
[17184471.532000] Buffer I/O error on device sdb, logical block 0
[17184471.532000]  unable to read partition table
[17184471.532000]  0:0:0:1: rejecting I/O to dead device
[17184471.532000]  0:0:0:0: rejecting I/O to dead device
[17184471.532000]  0:0:0:0: rejecting I/O to dead device
[17184471.532000]  0:0:0:0: rejecting I/O to dead device
[17184471.532000]  0:0:0:0: rejecting I/O to dead device
[17184471.532000] sda : READ CAPACITY failed.
[17184471.532000] sda : status=0, message=00, host=1, driver=00 
[17184471.532000] sda : sense not available. 
[17184471.532000]  0:0:0:0: rejecting I/O to dead device
[17184471.532000] sda: Write Protect is off
[17184471.532000] sda: Mode Sense: 00 00 00 00
[17184471.532000] sda: assuming drive cache: write through
[17184471.532000]  0:0:0:0: rejecting I/O to dead device
[17184471.532000]  0:0:0:0: rejecting I/O to dead device
[17184471.532000]  0:0:0:0: rejecting I/O to dead device
[17184471.532000]  0:0:0:0: rejecting I/O to dead device
[17184471.532000] sda : READ CAPACITY failed.
[17184471.532000] sda : status=0, message=00, host=1, driver=00 
[17184471.532000] sda : sense not available. 
[17184471.532000]  0:0:0:0: rejecting I/O to dead device
[17184471.532000] sda: Write Protect is off
[17184471.532000] sda: Mode Sense: 00 00 00 00
[17184471.532000] sda: assuming drive cache: write through
[17184471.532000]  sda:<3> 0:0:0:0: rejecting I/O to dead device
[17184471.532000] Buffer I/O error on device sda, logical block 0
[17184471.532000]  0:0:0:0: rejecting I/O to dead device
[17184471.532000] Buffer I/O error on device sda, logical block 0
[17184471.532000]  unable to read partition table
[17184494.668000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17184494.668000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17184494.672000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17184494.672000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17184494.676000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[17184494.676000] psmouse.c: issuing reconnect request
[17184674.684000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[17184674.684000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17184674.696000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[17184764.696000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[17184764.700000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17184764.708000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[17184794.768000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17184794.768000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17184794.768000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17184794.772000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17184794.772000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17184794.772000] psmouse.c: issuing reconnect request
[17184854.696000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17184854.696000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17184854.700000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17184854.700000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17184854.704000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17184854.704000] psmouse.c: issuing reconnect request
[17184974.708000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[17184974.708000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17184974.720000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[17185004.688000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[17185004.692000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17185004.700000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[17185214.712000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17185214.712000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17185214.716000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17185214.716000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17185214.716000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17185214.716000] psmouse.c: issuing reconnect request
[17185364.692000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17185364.692000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17185364.696000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17185364.696000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17185364.696000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17185364.696000] psmouse.c: issuing reconnect request
[17186294.696000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[17186294.700000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17186294.708000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[17186504.700000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17186504.704000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17186504.704000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17186504.704000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17186504.708000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17186504.708000] psmouse.c: issuing reconnect request
[17186654.700000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17186654.700000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17186654.704000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17186654.704000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17186654.704000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17186654.704000] psmouse.c: issuing reconnect request
[17191210.892000] pccard: PCMCIA card inserted into slot 1
[17191210.892000] pcmcia: registering new device pcmcia1.0
marc@ubuntumarc:~$

---

