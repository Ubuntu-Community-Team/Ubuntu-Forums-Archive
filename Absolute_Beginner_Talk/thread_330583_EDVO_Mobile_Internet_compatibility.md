---
title: "EDVO Mobile Internet compatibility"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by Praxicoide on 2007-01-03
Hi,

I have a laptop, but don't have Internet because I don't have a phone.

There's this new Internet service here which is a card that connects directly via G3 Cellphone, called EDVO.

In the current circumstances, it's the only way I could connect to the Internet, so I would really like to know if it could be compatible with Ubuntu.

It's a Kyocera KCP 650 

Dual Band CDMA 800MHz/1.9GHz 3G EDVO

PCMCIA Type II

Compatible OS: Windows 2000 and Windows XP :( 

I guess the last bit would mean that I won't get any support from them.

---

### Post by Praxicoide on 2007-01-03
UPDATE:

I've just visited the service provider (Iusacell) during lunch. His first question, after the look of puzzlement disappeared, was why did I use linux. Was I a developer or something?

I had to explain him, that I just preferred linux. He told me they only gave support to Mac and Window.

I then told him that I just wanted to find out if there was a driver. He seemed to understand and started looking at  the company's website, which of course, stated it supported only windows (not even mac).

Fortunately, he searched for the driver used, which is a verizon EDVO, and found [This Page]("http://www.linux.com/article.pl?sid=06/03/08/2138237").

After that he became very friendly, offering me help installing and setting up the card.

I'll go try it after work.

---

### Post by Praxicoide on 2007-01-03
Here is this [other page]("http://kenkinder.com/evdo-pc5740/"), which is where the first got part of its information from, and its a Kubuntu install!

However:
> I suspect that you need to get the card working in Windows before Linux. There is an "activation" step and it seems like a good idea from a troubleshooting point of view to make sure it works in Windows. It will ask you to download the latest coverage maps. I'm not sure, but I think when you do that it actually reflashes the card with some information about signals to broadcast. The coverage map update is superstition on my part, but I think you do need to activate the card in Windows before it will even work in Linux. Correct me if I'm wrong (or not) on the requirement of Windows activation and setup.

If this is true, then I'm stuck, because I don't have windows.  Would it work in another computer?

What a mess.

---

### Post by Praxicoide on 2007-01-03
I just realized that I messed up the links. They should work now.

---

### Post by chuvisco on 2007-01-03
> **Praxicoide said:**
> If this is true, then I'm stuck, because I don't have windows.  Would it work in another computer?

I won't be much help to you, but I will add a few comments here.  I haven't made the jump to EVDO yet, but I use 1xRTT through my cell phone (also Verizon) occasionally.  I've never used one of these cards, but I'm guessing that you will need a Windows computer to activate your card.  I think any Windows computer should work--you just need to find someone that won't mind you temporarily installing the Verizon software.

---

### Post by Praxicoide on 2007-01-04
OK, thanks for the advise. The computer tech will be here in an hour.

---

### Post by Praxicoide on 2007-01-04
Iusacell didn't send me a computer tech. They sent me a salesman who just knew how to insert the windows CD and watch the thing configure itself.

I had to go to their offices, where I was greeted by another salesman, who after getting over the Ubuntu SE desktop, went on to insert the windows CD and look with bewilderment when it didn't work.

Actually, the install program executed itself thanks to WINE, and it set up the desktop icons and everything, but it couldn't detect the card.

I told them about activation, but they didn't know what I was talking about. I followed the How  To in this forum, only got as far as the modprobe step.

In the end, they told me they get support from a guy who runs an Internet café. I'm going to see him after work and see what can be done.

In the end, I might have to buy a mobile wi-fi, but that's US$400!

---

### Post by chuvisco on 2007-01-04
I find it surprising that they are not willing to activate the card for you.  I have heard of Mac users that had to get their cards activated at the store.

---

### Post by Praxicoide on 2007-01-04
They tell me their cards come activated, so who knows. They were pretty clueless.

Here's the vendor Id:

 vendor=0c88 product=17da

I wish I could show you the dmegs, but my computer is still w/o internet.

---

### Post by dannyboy79 on 2007-01-04
you don;t have an ethernet port or a wireless card built into your laptop? you could always go to the library and take a ethernet plug and plug it into your computer to post your dmesg or even go to a free wireless cafe or whatever. I know an arbys by me just recently got wireless. pretty neat.

---

### Post by Praxicoide on 2007-01-05
I brought the computer to my job. Yesterday I had a bit of a scare with the wireless. It turns out that  since it worked right out of the box, I never configured it. Even now, if I go to Networking, it states this. But the network manager works perfectly. It's strange, but if it ain't broke...

Anyways, the card is a Kyocera KPC650, and it plugs in the PCIA port. The vendor ID is already posted. my dmesg is as follows (although the stupid card isn't plugged in right now, because I haven't bought it):

```
[17179569.184000] Linux version 2.6.17-10-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Tue Dec 5 22:28:26 UTC 2006 (Ubuntu 2.6.17-10.34-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001eee0000 (usable)
[17179569.184000]  BIOS-e820: 000000001eee0000 - 000000001eeeb000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000001eeeb000 - 000000001ef00000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000001ef00000 - 0000000020000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ff800000 - 00000000ffc00000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fffffc00 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 494MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 126688
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 122592 pages, LIFO batch:31
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6cd0
[17179569.184000] ACPI: RSDT (v001 PTLTD  Montara  0x06040000  LTP 0x00000000) @ 0x1eee5c9b
[17179569.184000] ACPI: FADT (v001 INTEL  MONTARAG 0x06040000 PTL  0x00000050) @ 0x1eeeaa2d
[17179569.184000] ACPI: SSDT (v001 INTEL    GV3Ref 0x06040000 MSFT 0x0100000e) @ 0x1eeeaaa1
[17179569.184000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x1eeeafd8
[17179569.184000] ACPI: DSDT (v001 INTEL  MONTARAG 0x06040000 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:df800000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (013eb000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[17179569.184000] Detected 1594.990 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.348000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.348000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179569.364000] Memory: 492392k/506752k available (1910k kernel code, 13792k reserved, 1069k data, 308k init, 0k highmem)
[17179569.364000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.444000] Calibrating delay using timer specific routine.. 3210.19 BogoMIPS (lpj=6420381)
[17179569.444000] Security Framework v1.0.0 initialized
[17179569.444000] SELinux:  Disabled at boot.
[17179569.444000] Mount-cache hash table entries: 512
[17179569.444000] CPU: After generic identify, caps: afe9f9bf 00000000 00000000 00000000 00000180 00000000 00000000
[17179569.444000] CPU: After vendor identify, caps: afe9f9bf 00000000 00000000 00000000 00000180 00000000 00000000
[17179569.444000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179569.444000] CPU: L2 cache: 2048K
[17179569.444000] CPU: After all inits, caps: afe9f9bf 00000000 00000000 00000040 00000180 00000000 00000000
[17179569.444000] Checking 'hlt' instruction... OK.
[17179569.460000] SMP alternatives: switching to UP code
[17179569.460000] Freeing SMP alternatives: 16k freed
[17179569.460000] checking if image is initramfs... it is
[17179570.012000] Freeing initrd memory: 5636k freed
[17179570.012000] ACPI: Core revision 20060707
[17179570.016000] ACPI: Looking for DSDT ... not found!
[17179570.016000] ACPI: setting ELCR to 0200 (from 0c00)
[17179570.040000] CPU0: Intel(R) Pentium(R) M processor 1.60GHz stepping 06
[17179570.040000] SMP motherboard not detected.
[17179570.040000] Local APIC not detected. Using dummy APIC emulation.
[17179570.040000] Brought up 1 CPUs
[17179570.040000] migration_cost=0
[17179570.040000] NET: Registered protocol family 16
[17179570.040000] EISA bus registered
[17179570.040000] ACPI: bus type pci registered
[17179570.040000] PCI: PCI BIOS revision 2.10 entry at 0xfd812, last bus=2
[17179570.040000] PCI: Using configuration type 1
[17179570.040000] Setting up standard PCI resources
[17179570.076000] ACPI: Interpreter enabled
[17179570.076000] ACPI: Using PIC for interrupt routing
[17179570.080000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.080000] PCI: Probing PCI hardware (bus 00)
[17179570.088000] Boot video device is 0000:00:02.0
[17179570.088000] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[17179570.088000] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[17179570.088000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179570.092000] PCI: Transparent bridge - 0000:00:1e.0
[17179570.092000] PCI: Bus #03 (-#06) is hidden behind transparent bridge #02 (-#02) (try 'pci=assign-busses')
[17179570.092000] Please report the result to linux-kernel to fix this permanently
[17179570.092000] PCI: Bus #07 (-#0a) is hidden behind transparent bridge #02 (-#02) (try 'pci=assign-busses')
[17179570.092000] Please report the result to linux-kernel to fix this permanently
[17179570.092000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.096000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[17179570.096000] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 *11)
[17179570.096000] ACPI: PCI Interrupt Link [LNKB] (IRQs *10 11)
[17179570.096000] ACPI: PCI Interrupt Link [LNKC] (IRQs *10 11)
[17179570.096000] ACPI: PCI Interrupt Link [LNKD] (IRQs *10 11)
[17179570.100000] ACPI: PCI Interrupt Link [LNKE] (IRQs *10 11)
[17179570.100000] ACPI: PCI Interrupt Link [LNKF] (IRQs *10 11)
[17179570.100000] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[17179570.100000] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 *11)
[17179570.100000] ACPI: Embedded Controller [EC0] (gpe 28) interrupt mode.
[17179570.124000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.124000] pnp: PnP ACPI init
[17179570.140000] pnp: PnP ACPI: found 9 devices
[17179570.140000] PnPBIOS: Disabled by ACPI PNP
[17179570.140000] PCI: Using ACPI for IRQ routing
[17179570.140000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.144000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[17179570.144000] PCI: Bus 3, cardbus bridge: 0000:02:04.0
[17179570.144000]   IO window: 00003000-000030ff
[17179570.144000]   IO window: 00003400-000034ff
[17179570.144000]   PREFETCH window: 30000000-31ffffff
[17179570.144000]   MEM window: 36000000-37ffffff
[17179570.144000] PCI: Bus 7, cardbus bridge: 0000:02:04.1
[17179570.144000]   IO window: 00003800-000038ff
[17179570.144000]   IO window: 00003c00-00003cff
[17179570.144000]   PREFETCH window: 32000000-33ffffff
[17179570.144000]   MEM window: 38000000-39ffffff
[17179570.144000] PCI: Bridge: 0000:00:1e.0
[17179570.144000]   IO window: 3000-3fff
[17179570.144000]   MEM window: e0200000-e02fffff
[17179570.144000]   PREFETCH window: 30000000-33ffffff
[17179570.144000] PCI: Enabling device 0000:00:1e.0 (0005 -> 0007)
[17179570.144000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179570.144000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[17179570.144000] PCI: setting IRQ 10 as level-triggered
[17179570.144000] ACPI: PCI Interrupt 0000:02:04.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[17179570.144000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[17179570.144000] ACPI: PCI Interrupt 0000:02:04.1[B] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[17179570.144000] NET: Registered protocol family 2
[17179570.180000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179570.180000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[17179570.180000] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[17179570.180000] TCP: Hash tables configured (established 16384 bind 8192)
[17179570.180000] TCP reno registered
[17179570.180000] Simple Boot Flag at 0x36 set to 0x1
[17179570.180000] audit: initializing netlink socket (disabled)
[17179570.180000] audit(1168015166.180:1): initialized
[17179570.180000] VFS: Disk quotas dquot_6.5.1
[17179570.180000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.180000] Initializing Cryptographic API
[17179570.180000] io scheduler noop registered
[17179570.180000] io scheduler anticipatory registered
[17179570.180000] io scheduler deadline registered
[17179570.180000] io scheduler cfq registered (default)
[17179570.180000] isapnp: Scanning for PnP cards...
[17179570.536000] isapnp: No Plug & Play device found
[17179570.556000] Real Time Clock Driver v1.12ac
[17179570.556000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179570.560000] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[17179570.560000] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[17179570.560000] mice: PS/2 mouse device common for all mice
[17179570.560000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179570.560000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179570.560000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179570.560000] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179570.560000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179570.560000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179570.564000] EISA: Probing bus 0 at eisa.0
[17179570.564000] Cannot allocate resource for EISA slot 1
[17179570.564000] Cannot allocate resource for EISA slot 2
[17179570.564000] Cannot allocate resource for EISA slot 3
[17179570.564000] EISA: Detected 0 cards.
[17179570.564000] TCP bic registered
[17179570.564000] NET: Registered protocol family 1
[17179570.564000] NET: Registered protocol family 8
[17179570.564000] NET: Registered protocol family 20
[17179570.564000] Using IPI No-Shortcut mode
[17179570.564000] ACPI: (supports S0 S3 S4 S5)
[17179570.564000] Freeing unused kernel memory: 308k freed
[17179570.596000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179571.740000] Capability LSM initialized
[17179571.768000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[17179571.768000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179571.808000] ACPI: Thermal Zone [THRC] (27 C)
[17179571.848000] ACPI: Thermal Zone [THRS] (25 C)
[17179572.112000] ICH4: IDE controller at PCI slot 0000:00:1f.1
[17179572.112000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[17179572.112000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[17179572.112000] ICH4: chipset revision 3
[17179572.112000] ICH4: not 100% native mode: will probe irqs later
[17179572.112000]     ide0: BM-DMA at 0x1810-0x1817, BIOS settings: hda:DMA, hdb:pio
[17179572.112000]     ide1: BM-DMA at 0x1818-0x181f, BIOS settings: hdc:DMA, hdd:pio
[17179572.112000] Probing IDE interface ide0...
[17179572.400000] hda: HTS548040M9AT00, ATA DISK drive
[17179573.072000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179573.104000] Probing IDE interface ide1...
[17179573.840000] hdc: PHILIPS CD-RW/DVD-ROM CDD5263, ATAPI CD/DVD-ROM drive
[17179574.512000] ide1 at 0x170-0x177,0x376 on irq 15
[17179574.520000] hda: max request size: 512KiB
[17179574.528000] hda: 78140160 sectors (40007 MB) w/7877KiB Cache, CHS=16383/255/63, UDMA(100)
[17179574.528000] hda: cache flushes supported
[17179574.528000]  hda: hda1 hda2 < hda5 >
[17179574.612000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179574.612000] Uniform CD-ROM driver Revision: 3.20
[17179574.952000] usbcore: registered new driver usbfs
[17179574.952000] usbcore: registered new driver hub
[17179574.952000] USB Universal Host Controller Interface driver v3.0
[17179574.952000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[17179574.952000] PCI: setting IRQ 11 as level-triggered
[17179574.952000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179574.952000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179574.952000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179574.952000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179574.952000] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00001820
[17179574.952000] usb usb1: configuration #1 chosen from 1 choice
[17179574.952000] hub 1-0:1.0: USB hub found
[17179574.952000] hub 1-0:1.0: 2 ports detected
[17179575.016000] ieee1394: Initialized config rom entry `ip1394'
[17179575.056000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
[17179575.056000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[17179575.056000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179575.056000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179575.056000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179575.056000] uhci_hcd 0000:00:1d.1: irq 10, io base 0x00001840
[17179575.056000] usb usb2: configuration #1 chosen from 1 choice
[17179575.056000] hub 2-0:1.0: USB hub found
[17179575.056000] hub 2-0:1.0: 2 ports detected
[17179575.160000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[17179575.160000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179575.160000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179575.160000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179575.160000] uhci_hcd 0000:00:1d.2: irq 10, io base 0x00001860
[17179575.160000] usb usb3: configuration #1 chosen from 1 choice
[17179575.160000] hub 3-0:1.0: USB hub found
[17179575.160000] hub 3-0:1.0: 2 ports detected
[17179575.264000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[17179575.264000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
[17179575.264000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179575.264000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179575.264000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[17179575.264000] ehci_hcd 0000:00:1d.7: debug port 1
[17179575.264000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[17179575.264000] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xe0100000
[17179575.268000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179575.292000] usb usb4: configuration #1 chosen from 1 choice
[17179575.292000] hub 4-0:1.0: USB hub found
[17179575.292000] hub 4-0:1.0: 5 ports detected
[17179575.404000] PCI: Enabling device 0000:02:04.2 (0000 -> 0002)
[17179575.404000] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 10
[17179575.404000] ACPI: PCI Interrupt 0000:02:04.2[C] -> Link [LNKF] -> GSI 10 (level, low) -> IRQ 10
[17179575.452000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[10]  MMIO=[e0208000-e02087ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[17179575.512000] kjournald starting.  Commit interval 5 seconds
[17179575.512000] EXT3-fs: mounted filesystem with ordered data mode.
[17179576.724000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[811f0f00525ab100]
[17179587.180000] Linux agpgart interface v0.101 (c) Dave Jones
[17179587.336000] pnp: Device 00:06 activated.
[17179587.336000] parport: PnPBIOS parport detected.
[17179587.336000] pnp: Device 00:06 disabled.
[17179587.392000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179587.396000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179587.412000] hw_random hardware driver 1.0.0 loaded
[17179587.576000] agpgart: Detected an Intel 855 Chipset.
[17179587.576000] agpgart: Detected 16252K stolen memory.
[17179587.584000] agpgart: AGP aperture is 128M @ 0xe8000000
[17179587.708000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[17179587.708000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[17179587.872000] ieee80211_crypt: registered algorithm 'NULL'
[17179587.876000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[17179587.876000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17179587.932000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq
[17179587.932000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[17179587.932000] Driver 'ipw2200' needs updating - please use bus_type methods
[17179588.272000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xa560b1, caps: 0xa04713/0x0
[17179588.312000] input: SynPS/2 Synaptics TouchPad as /class/input/input1
[17179588.344000] ts: Compaq touchscreen protocol output
[17179588.532000] intel8x0_measure_ac97_clock: measured 55505 usecs
[17179588.532000] intel8x0: clocking to 48000
[17179588.532000] ACPI: PCI Interrupt 0000:02:04.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[17179588.532000] Yenta: CardBus bridge found at 0000:02:04.0 [1028:018d]
[17179588.532000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179588.532000] Yenta: Routing CardBus interrupts to PCI
[17179588.532000] Yenta TI: socket 0000:02:04.0, mfunc 0x01021b22, devctl 0x64
[17179588.764000] Yenta: ISA IRQ mask 0x00f8, PCI irq 10
[17179588.764000] Socket status: 30000006
[17179588.764000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[17179588.764000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[17179588.764000] cs: IO port probe 0x3000-0x3fff: clean.
[17179588.764000] pcmcia: parent PCI bridge Memory window: 0xe0200000 - 0xe02fffff
[17179588.764000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[17179588.764000] ACPI: PCI Interrupt 0000:02:04.1[B] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[17179588.764000] Yenta: CardBus bridge found at 0000:02:04.1 [1028:018d]
[17179588.764000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179588.764000] Yenta: Routing CardBus interrupts to PCI
[17179588.764000] Yenta TI: socket 0000:02:04.1, mfunc 0x01021b22, devctl 0x64
[17179588.996000] Yenta: ISA IRQ mask 0x00f8, PCI irq 10
[17179588.996000] Socket status: 30000006
[17179588.996000] Yenta: Raising subordinate bus# of parent bus (#02) from #06 to #0a
[17179588.996000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[17179588.996000] cs: IO port probe 0x3000-0x3fff: clean.
[17179588.996000] pcmcia: parent PCI bridge Memory window: 0xe0200000 - 0xe02fffff
[17179588.996000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[17179589.004000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 10
[17179589.004000] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKE] -> GSI 10 (level, low) -> IRQ 10
[17179589.004000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[17179589.252000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[17179589.252000] b44.c:v1.00 (Apr 7, 2006)
[17179589.252000] ACPI: PCI Interrupt 0000:02:05.0[A] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[17179589.256000] eth1: Broadcom 4400 10/100BaseT Ethernet 00:0f:1f:b1:5a:52
[17179589.580000] cs: IO port probe 0x100-0x3af: clean.
[17179589.580000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179589.584000] cs: IO port probe 0x820-0x8ff: clean.
[17179589.584000] cs: IO port probe 0xc00-0xcf7: clean.
[17179589.584000] cs: IO port probe 0xa00-0xaff: clean.
[17179589.584000] cs: IO port probe 0x100-0x3af: clean.
[17179589.584000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179589.588000] cs: IO port probe 0x820-0x8ff: clean.
[17179589.588000] cs: IO port probe 0xc00-0xcf7: clean.
[17179589.588000] cs: IO port probe 0xa00-0xaff: clean.
[17179589.688000] lp: driver loaded but no devices found
[17179589.740000] SCSI subsystem initialized
[17179589.744000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179589.744000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179589.864000] EXT3 FS on hda1, internal journal
[17179590.400000] NET: Registered protocol family 17
[17179592.336000] b44: eth0: Link is up at 100 Mbps, full duplex.
[17179592.336000] b44: eth0: Flow control is off for TX and off for RX.
[17179593.604000] NET: Registered protocol family 10
[17179593.604000] lo: Disabled Privacy Extensions
[17179593.604000] IPv6 over IPv4 tunneling driver
[17179595.708000] ACPI: AC Adapter [ADP1] (on-line)
[17179595.748000] ACPI: Battery Slot [BAT0] (battery absent)
[17179595.764000] ACPI: Power Button (FF) [PWRF]
[17179595.764000] ACPI: Lid Switch [LID0]
[17179595.764000] ACPI: Sleep Button (CM) [SLPB]
[17179595.912000] ibm_acpi: ec object not found
[17179595.940000] pcc_acpi: loading...
[17179596.048000] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[17179598.368000] [drm] Initialized drm 1.0.1 20051102
[17179598.372000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179598.372000] [drm] Initialized i915 1.5.0 20060119 on minor 0
[17179598.372000] [drm] Initialized i915 1.5.0 20060119 on minor 1
[17179599.580000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179599.580000] apm: overridden by ACPI.
[17179603.664000] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[17179603.864000] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[17179603.880000] NFSD: starting 90-second grace period
[17179604.452000] eth0: no IPv6 routers present
[17179605.920000] Bluetooth: Core ver 2.8
[17179605.920000] NET: Registered protocol family 31
[17179605.920000] Bluetooth: HCI device and connection manager initialized
[17179605.920000] Bluetooth: HCI socket layer initialized
[17179605.960000] Bluetooth: L2CAP ver 2.8
[17179605.960000] Bluetooth: L2CAP socket layer initialized
[17179606.004000] Bluetooth: RFCOMM socket layer initialized
[17179606.004000] Bluetooth: RFCOMM TTY layer initialized
[17179606.004000] Bluetooth: RFCOMM ver 1.7
[17179620.872000] eth0: no IPv6 routers present

```

Sorry for posting the whole thing, but I don't know what's relevant and what's not.  

Also, it says "please report this to the linux kernel" a couple of times.

---

### Post by chuvisco on 2007-01-05
I guess I'm not clear on where you ran into problems.  You are following the Kubuntu HOWTO that you linked to, right?  How far did you get and what problem did you have?

---

### Post by Praxicoide on 2007-01-05
OK, sorry for not being clear.

I got as far as:

```
sudo modprobe usbserial vendor=0c88 product=17da

```

I then tried ls: /dev/ttyACM0, but got "no such file or directory".

And that's as far as I got.

Would this have anything to do with it?:

```
[17179570.092000] PCI: Transparent bridge - 0000:00:1e.0
[17179570.092000] PCI: Bus #03 (-#06) is hidden behind transparent bridge #02 (-#02) (try 'pci=assign-busses')
[17179570.092000] Please report the result to linux-kernel to fix this permanently
[17179570.092000] PCI: Bus #07 (-#0a) is hidden behind transparent bridge #02 (-#02) (try 'pci=assign-busses')
[17179570.092000] Please report the result to linux-kernel to fix this permanently
```

---

### Post by Praxicoide on 2007-01-06
I found a linux driver for the EDVO card! 

[http://wireless-internet-broadband-service.com/evdo-linux-kpc650-v650-driver.doc]("http://wireless-internet-broadband-service.com/evdo-linux-kpc650-v650-driver.doc")

The only problem is I don't understand the directions.
> Ok - so what you do is put this in your 
/usr/src/linux/drivers/usb/serial/ directory 
then you go to /usr/src/linux and make modules && make modules_install

What does make modules & make modules_install mean?
 
> then to load this up: 
you have to do a lsusb and get the vendor/product id such as: 
$lsusb 
Bus 005 Device 002: ID 0c88:17da Kyocera Wireless Corp. 
then modprobe your new usbserial module (rmmod any if they are already 
loaded) 
modprobe usbserial vendor=0xc88 product=0x17da maxSize=2048 

I think I've done this, except for the maxSize thing. 

> then if it doesn't create /dev/ttyUSB0 and /dev/ttyUSB1 on it's own you do: 
mknod /dev/ttyUSB0 c 188 0 
mknod /dev/ttyUSB1 c 188 1 
and then if pppd needs to be configured: 
mknod /dev/ppp c 108 0 
after that load up kppp 
and basically you set up your modem to /dev/ttyUSB0 
then the phone number is #777 
login and pass is the same as windows so [email]number@vzw3g.com[/email] and vzw as pass. 
Hit dial and tada you are connected. 

:confused: 

Well, at least this offers me hope. I was depressed as hell because I don't want to leave Ubuntu, but I need to have Internet.


EDIT:

Oh, what am I supposed to call the driver?

---

### Post by Praxicoide on 2007-01-06
Now I'm in trouble and I don't know what to do.

I pasted the driver named above on gedit and placed it in the /usr/src/linux/drivers/usb/serial/ directory.

Next I tried make modules, and it told me no directions were given to make, and so, another attempt at getting the card to work failed miserably.

But now, I rebooted and the computer has no audio and the touchpad doesn't work either!

Argh! what can I do? I'm getting desperate.

---

### Post by Praxicoide on 2007-01-06
OK, the driver was a complete crash and burn incident for me. I began to fear for my life, and in the end had to make a full reinstall.

Now I'm going to try this how to:

[http://www.ubuntuforums.org/showthread.php?t=77364](http://www.ubuntuforums.org/showthread.php?t=77364)

What's scary for me is the fact that I have to set the maxSize using this patch:

[http://www.junxion.com/opensource/linux_highspeed_usbserial.html](http://www.junxion.com/opensource/linux_highspeed_usbserial.html)

But I don't want to break the computer again. :???: 

I'll also have to set up the kernel, thunderbird, wine, the codecs, 915resolution, and a few other things I'm sure I'm forgetting now. :mad:

---

### Post by chuvisco on 2007-01-07
Sorry, I didn't get a chance to check the forum yesterday.  That's great that you found a HOWTO for your specific card.  My understanding is that the kernel patch corrects the network stall problem that seems to happen a few minutes after connecting.  So you should be able to go through the first five steps of that HOWTO and check that you are able to get connected (for a few minutes, at least).  If it is not working at that point, it would probably mean that the card is in fact not activated.  If it does connect, but then disconnects after a few minutes, then you will need to apply the kernel patch.  I did a search and found [this page]("http://wildbill.nulldevice.net/wordpress/?p=144"), which may be useful to you.  There is actually a patched kernel there (.deb packaged and everything) that you could probably download and try.

---

### Post by Praxicoide on 2007-01-07
Thank you very much, you're a showing me light at the end of the tunnel.

Yesterday the guy at the store asked me if I would be willing to switch to Windows.

I don't know what look I gave him, but he didn't ask again.

I began to use Ubuntu since last October, I think, and I love it. It's just so much leaner, intuitive and easy to use. The terminal is a joy.

I had problems setting things up, but I always found the solutions at this forum, even if it took me a while to find what I was doing wrong.

It's Sunday, so I'll have to wait until tomorrow to test this. Cheers.

---

### Post by Praxicoide on 2007-01-07
One thing though, If I do end up applying the patch, where do I make it?  I'm asking because my /usr/src directory shows two folder: linux 2.6 something (I'm not at my computer right now) and linux 2.6.something-generic.

---

### Post by Praxicoide on 2007-01-08
OK, I went back to the service provider today, and told them to give me the card and let me figure it out.

The card didn't even light up, and doing lsusb gave me a bunch of zeroes.

I downloaded the kernel patch, which took care of itself, and the other files, which are still sitting in the desktop.

I asked them about activation again, and they told me it was already activated. I then made up that it needed to be updated, but no, the same reply.

"I asked a technician and he said the problem is that you have Linux; you should switch to Windows," one of the guys told me.

At that point I lost my patience and told them the problem was not my computer, but the card. They got defensive and said they use them all the time.

"Show me."

And so they did, one of them went to the back to fetch his mac and plugged the card in.

"See, there's no problem, I just click here and it connects"

So, of course, I took the card, put it in my laptop again, and lo and behold! it lit up, and the terminal recognized it as a Kyocera device.

The funny thing is that they still didn't believe me when I said that the card needed to be activated. :rolleyes: 

OK, I had to leave for work, but I'm going back, after I install the drivers given above (I still don't know where to put them, linux 2.6 or 2.6 generic). The computer recognized the card, but I still didn't know how to connect to the Internet through it. The network manager didn't show it. It should appear as a modem, right?

I'm not too computer savvy, so any guidance, regardless of how obvious it seems, is more than welcome.

---

### Post by Praxicoide on 2007-01-08
I've just copied the files downloaded from the link given by chuvisco. I decided to put them in the linux-headers2.6.17-10 file instead of the generic (don't ask me why), I hope my computer still works after I reboot. I figured that I broke the computer the last time because I simply copied the last driver on a "linux" folder that the system had to create, but which had no additional drivers. Perhaps If I had deleted it, and typed make modules for one of the two existing folders, things would have been back to normal.

The only strange thing, but which is unrelated is that I got the following error:

```
 SPLIT   include/linux/autoconf.h -> include/config/*
make[2]: *** No hay ninguna regla para construir el objetivo `drivers/acpi/sony_acpi.c', necesario para `drivers/acpi/sony_acpi.o'.  Alto.
make[1]: *** [drivers/acpi] Error 2
make: *** [drivers] Error 2
/[CODE]

It's in Spanish, but it says there's no rule to build "drivers/acpi/sony_acpi.c;" Does this mean that I have a piece of hardware that doesn't work? I thought I had enough with this card and the 3-D driver (which might explain why Beryl slows my computer so much, perhaps) *sigh*

When I type "wvdial verizon" I get the following

[CODE]wvdial verizon
--> WvDial: Internet dialer version 1.56
--> Warning: section [Dialer verizon] does not exist in wvdial.conf.
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory

```

But then, I don't have the card in (would you believe the guys wouldn't sell me the activated card, because that's a sample card!). I'll just have to take a leap of faith and buy it, even though I have yet to see it connected.

It's been I don't know how many days now with this card, and even though I see plenty of testimonials from Linux users, even Ubuntu users, using this thing, I'm still not certain it will work for me, because of some error somewhere that no one will be able to figure out for me.

---

### Post by Praxicoide on 2007-01-08
Three pages, and nearly all the replies are mine...

Help, anybody?

And how does one go about editing the title? I made a typo and can't fix it.

---

### Post by chuvisco on 2007-01-08
Yeah, technology salespersons are generally pretty clueless.  As far as activation, why not buy a card and then ask them to stick it in their laptop for activation?   

Ok, I think I know what drivers you're talking about.  The ones in the verizonCDMA.tar.gz file, right?  You don't need to do anything with those.  As far as getting connected, you can use pppd or wvdial (the pages linked in this thread vary as to which one they use).  But you need to connect to lusacell, and the wvdial (or pppd) configuration files will be specific to lusacell.  They will probably be similar to the Verizon ones, but you will need to make some modifications.  You will have to do some research here.

This card will not show up in the GUI network tools.  wvdial and pppd are command-line tools.

WildBill's kernel (kernel-image-2.6.12speedstep2_10.00.Custom_i386.deb) is a bit older than the one included in Edgy (2.6.17), so I don't know for sure that it will work, but it's easy enough to install it and try.  After installation you should see the 2.6.12 kernel as an option in your grub menu when you reboot your computer.  You can always revert back to Edgy's 2.6.17 kernel by choosing it in the grub menu.  

As far as the sony error, it seems to be referring to ACPI (power management) drivers for Sony Vaio computers.

---

### Post by kd7swh on 2007-01-09
here is a forum article, it is for gentoo linux but it maybe helpful to you.

[https://forums.gentoo.org/viewtopic-t-427992.html](https://forums.gentoo.org/viewtopic-t-427992.html)

It says it is Specifically for Verizon EVDO using the Keyocera KPC650 EVDO PCMCIA card.

---

### Post by Praxicoide on 2007-01-09
Thank you for replying!

First, I couldn't get the computer to boot using the kernel patch. So I guess I'll have to do this the hard way and compile the patch. :-? (how do I remove the kernel, BTW?)

You can see that I've tried Wvdial, and although the card wasn't present, it said that no Dialer verizon is configured. However If I cd to linux-headers2.17-10 directory and make modules & modules_install, it won't say the dialer isn't present, but it will still say that no /dev/modem exist.

Also, the dmesg changes all the time.  After I do the modprobe, it will show the new usbserial (but only then).  after I try pppd, adding a line for the pppd driver. As for the maxSize thing. After I modprobe WITHOUT the maxsize parameter (if I add it it won't recognize it and no usbserial will be listed), I can modprobe again WITH the maxSize, and it won't complain at all:confused: 

All this means that I have to configure this stuff every time I boot the computer. Does this mean that I messed up and should have made everything in the linux-headers2.17-10-generic? 

Here's the dmesg, after I cd and make modules & make modules_install,  modprobe without and with the maxsize and pppd:

```
[17179620.412000] eth1: no IPv6 routers present
[17179620.700000] NET: Registered protocol family 17
[17179620.832000] ieee80211_crypt: registered algorithm 'WEP'
[17179642.840000] eth1: no IPv6 routers present
[17179847.132000] CSLIP: code copyright 1989 Regents of the University of California
[17179847.144000] PPP generic driver version 2.4.2
[17179876.720000] usbcore: registered new driver usbserial
[17179876.724000] drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[17179876.724000] usbcore: registered new driver usbserial_generic
[17179876.724000] drivers/usb/serial/usb-serial.c: USB Serial Driver core

```

The one that says "support registered for generic" appears after the second modprobe.

You're right, of course, in that I need to configure that dialer,  or rather modify an already existing file, which is I guess what the files in the tar are. The problem, of course, is that nobody at Iusacell can give me any useful information. I asked them about the number used by the card, but they said that it doesn't use any number, it "just connects." They did tell me that the driver they use is indeed a verizon.

Another strange thing, I opened the wvdial.conf and:

```
 gksudo gedit wvdial.conf
(gedit:4654): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
ALSA lib pcm_dmix.c:862:(snd_pcm_dmix_open) unable to open slave

```

gedit stills opens, but its a warning nonetheless. I hope it doesn't give me future troubles.

---

### Post by Praxicoide on 2007-01-09
> **kd7swh said:**
> here is a forum article, it is for gentoo linux but it maybe helpful to you.

[https://forums.gentoo.org/viewtopic-t-427992.html](https://forums.gentoo.org/viewtopic-t-427992.html)

It says it is Specifically for Verizon EVDO using the Keyocera KPC650 EVDO PCMCIA card.

Thank you very much, studying all these HOWTOs helps me try to grasp things a little bit better (actually, a little less foggier).

I'm buying the card tomorrow. The problem is that I'm not the only user for this computer, so if I can't connect with the card by tomorrow, I'll be in trouble for switching the computer to Linux.

I have NO IDEA how to patch the kernel. This page says that the junxion patch will not work with 2.6, so I think I should try this one. What am I supposed to do with this text?:

```

--- usb-serial.c.orig   2006-03-12 21:25:43.000000000 -0800
+++ usb-serial.c        2006-03-12 23:32:20.000000000 -0800
@@ -55,6 +55,7 @@
    drivers depend on it.
 */

+static ushort maxSize = 0;
 static int debug;
 static struct usb_serial *serial_table[SERIAL_TTY_MINORS];     /* initially all NULL */
 static LIST_HEAD(usb_serial_driver_list);
@@ -755,7 +756,7 @@
                        dev_err(&interface->dev, "No free urbs available\n");
                        goto probe_error;
                }
-               buffer_size = le16_to_cpu(endpoint->wMaxPacketSize);
+               buffer_size = (endpoint->wMaxPacketSize > maxSize)?endpoint->wMaxPacketSize:maxSize;
                port->bulk_in_size = buffer_size;
                port->bulk_in_endpointAddress = endpoint->bEndpointAddress;
                port->bulk_in_buffer = kmalloc (buffer_size, GFP_KERNEL);
@@ -1130,3 +1131,5 @@

 module_param(debug, bool, S_IRUGO | S_IWUSR);
 MODULE_PARM_DESC(debug, "Debug enabled or not");
+module_param(maxSize, ushort,0);
+MODULE_PARM_DESC(maxSize,"User specified USB endpoint size"); 
```

use gedit to add it someplace?

---

### Post by Praxicoide on 2007-01-09
> **chuvisco said:**
> 
As far as the sony error, it seems to be referring to ACPI (power management) drivers for Sony Vaio computers.

Oh, yeah! Thanks for pointing this out. My computer is not a Vaio, it's a Dell. Like many Dell computers, the battery is busted. So that would explain the driver error, I guess.

---

### Post by kd7swh on 2007-01-09
Check out these pages. They will help you patch your kernel:

[http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/](http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/) - 
How to Customize Your Ubuntu Kernel

[http://doc.gwos.org/index.php/Kernel_Compilation_Dapper](http://doc.gwos.org/index.php/Kernel_Compilation_Dapper) - 
Kernel Compilation for Newbies

---

### Post by Praxicoide on 2007-01-09
Thanks! I'll have a look at these. ;)

One thing that jumped off the page right away was this:



>     
To start, we need to figure out what version of the kernel we are currently running. We’ll use the uname command for that
$ uname -r
2.6.17-10-generic
 

That's exactly my output too, meaning that I should have placed the drivers on the generic folder. That's why I have to redo everything after each boot.

Thank you for pointing that out for me.

---

### Post by Jim March on 2007-06-16
I know this is late but for anybody wrestling with this, there's another way to skin this cat:

[http://3gstore.com/index.php?main_page=product_info&cPath=35&products_id=99](http://3gstore.com/index.php?main_page=product_info&cPath=35&products_id=99)

Yes, it's $200 bucks.  But it TOTALLY solves EVDO/Linux issues, in a hurry.

This thing has it's own PCMCIA slot, and also has a USB port for some USB modems and even a few cellphones.

Mine has the KPC650 in it's PCMCIA slot.  The router turns that into my choice of WiFi (including WEP or WPA encryption) and standard Ethernet cable.  Which means Linux can work with it with ZERO drivers, straight DHCP plain Ethernet until you get WiFi sorted out.

It gives you the following other benefits:

* You can create a WiFi hotspot off your EVDO signal anywhere and share the connection.

* It moves that high-powered cellphone signal (the KPC650 is a pretty healthy signal) away from...well...your reproductive organs.  Look, I dunno 'bout y'all but I use my laptop a LOT.  And on my lap.  Having that beefy an RF signal that close to my nuts eight hours a day is...welll...maybe not cool, y'know?

* If you're in a weak cellphone signal area, you can position the router with KPC650 or similar next to a window and have it send WiFi deeper into the building.  In that sense it acts as a serious antenna upgrade.

* All that kernel patch, modprobe etc. bullhonky just goes away :).  To me that alone is worth $200.

Jim

---

