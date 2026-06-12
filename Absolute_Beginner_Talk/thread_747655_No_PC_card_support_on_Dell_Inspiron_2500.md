---
title: "No PC card support on Dell Inspiron 2500"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by jalynn2 on 2008-04-06
I am a Linux noob trying to get Ubuntu going so I can work on getting out of noob status :)

After upgrading my Dell Inspiron 2500 laptop from 128MB to 512MB, I was able to install 7.10 using the safe graphics mode. However, I have no PC card support. Since this laptop does not have built in ethernet, it's use is very limited without PC cards. When I enter a PC card, I get no reaction from the system.

One thing noticed: when booting the live CD and now the installed system, I get these messages displayed to the console:

[16.186261] PCI: 0000:01:03.0 class 7 doesn't match header type 02. Ignoring class.
[16.186349] PCI: 0000:01:03.1 class 7 doesn't match header type 02. Ignoring class.

lspci gives this:
00:00.0 Host bridge: Intel Corporation 82815 Chipset Host Bridge and Memory Controller Hub (rev 11)
00:02.0 VGA compatible controller: Intel Corporation 82815 Chipset Graphics Controller (CGC) (rev 11)
00:le.0 PCI bridge: Intel Corporation 82801 Mobile PCI bridge (rev 03)
00:lf.0 ISA bridge: Intel Corporation 8201BAM ISA Bridge (LPC)  (rev 03)
00:lf.1 IDE interface: Intel Corporation 8201BAM IDE U100 Controller (rev 03)
00:lf.2 USB controller: Intel Corporation 8201BA/BAM USB Controller #1 (rev 03)
00:lf.3 SMBus: Intel Corporation 8201BA/BAM SMBus Controller (rev 03)
00:lf.4 USB controller: Intel Corporation 8201BA/BAM USB Controller #1 (rev 03)
00:lf.5 Multimedia audio controller: Intel Corporation 8201BA/BAM AC'97 Audio Controller (rev 03)
01:03.0 Non-VGA unclassified device: 02 Micro, Inc. Unknown device 0032 (rev 34)
01:03.1 Non-VGA unclassified device: 02 Micro, Inc. Unknown device 0032 (rev 34)

any guidance on where to go from here? I ran a Dell diagnostics disk, and the only problems that show up are the USB controllers. The PCMCIA controller passes.

TIA

---

### Post by dstew on 2008-04-07
Can you give us more information about the PC card? Who is the manufacturer (O2 Micro makes the chipset, but not the whole card). Can you check on the Windows side for more information about the card? In particular, what driver is it using?

On the Ubuntu side, look for a file named **/etc/modprobe.d/blacklist** and see if any of the drivers in there sound like they might be for this card. Look for the name Yenta, because the chipset is Yenta-compatible.

---

### Post by jalynn2 on 2008-04-07
Thanks for replying. The lspci output above is with no cards in the machine. I have tried the following cards:

[LIST]
[*]SMC SMC8041TX 10/100 Ethernet card
[*]Cisco AIR-CB21AG_A_K9 wireless card
[*]Intel Pro Wireless 5000 card WCB5000
[*]3COM Modem card 3CXM356
[/LIST]

When I put in any of these cards, nothing happens. I am not sure what to expect, but the leds do not light on the cards, and nothing shows up in the network connections other than the internal modem for the PC.

Here are the contents of my blacklist file:
[LIST]
[*]evbug
[*]usbmouse
[*]usbkbd
[*]eepro100
[*]de4x5
[*]eth1394
[*]snd_intel8x0m
[*]i2c_i801
[/LIST]

TIA

---

### Post by dstew on 2008-04-08
> When I put in any of these cards, nothing happens.Do you mean that lspci shows nothing when these cards are plugged in?

---

### Post by jalynn2 on 2008-04-08
Yes, when I run lspci with any of the cards in, it reads exactly the same as in my original post. Also, I see no physical reaction on the cards; both the wired and wireless cards have LEDs that should light up. So it seems like Ubuntu does not recognize the card controllers? I'm guessing that is what the Micro Inc entries are?

When I boot  the Dell diagnostics, it tells me that a card is present and fully seated when I insert my card. So it seems that the hardware is OK. Is there anyway to override or diagnose the drivers?

Thanks,
Joe

---

### Post by ugm6hr on 2008-04-08
If you haven;t already tried - make sure that the card is plugged in when you turn the computer on.

The fact that lspci doesn't recognise it is a bit worrying though...

I have never encountered a laptop that didn't have PCMCIA support.

Not really sure, but if the PCMCIA card controller is recognised, it should appear in:
```
lshw -C system
```

---

### Post by jalynn2 on 2008-04-08
It seems that the controller is not being recognized correctly. Here's the  partial output from lshw. Note the entries for Generic UNCLAIMED at the end. I found some other posts regarding this PC and the Micro 02 at those bus addresses are the controllers. Any ideas on how to fix this?:

dell-linux
    description: Computer
    product: Inspiron 2500
    vendor: Dell Computer Corporation
    version: Revision A0
    serial: 5J82W01
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: administrator_password=enabled boot=oem-specific frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=44454C4C-4A00-1238-8532-35C04F573031
  *-core
       description: Motherboard
       product: Inspiron 2500
       vendor: Dell Computer Corporation
       physical id: 0
       version: None
       serial: None
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 4
          version: A15 (11/05/2002)
          size: 106KB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd usb smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Celeron (Coppermine)
          vendor: Intel Corp.
          physical id: 8
          bus info: cpu@0
          version: 6.8.10
          slot: U1
          size: 800MHz
          capacity: 1GHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: L1 Cache
             size: 32KB
             capabilities: asynchronous internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: a
             slot: L2 Cache
             size: 128KB
             capacity: 512KB
             capabilities: burst external write-back unified
     *-memory
          description: System Memory
          physical id: 16
          slot: System board or motherboard
          size: 512MB
          capacity: 512MB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: M1
             size: 256MB
             width: 32 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: M2
             size: 256MB
             width: 32 bits
     *-pci
          description: Host bridge
          product: 82815 815 Chipset Host Bridge and Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 11
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display
             description: VGA compatible controller
             product: 82815 Chipset Graphics Controller (CGC)
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: pm vga bus_master cap_list
             configuration: driver=i810_smbus latency=0 module=i2c_i810
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-generic:0 UNCLAIMED
                description: Unclassified device
                product: O2 Micro, Inc.
                vendor: O2 Micro, Inc.
                physical id: 3
                bus info: pci@0000:01:03.0
                version: 34
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0 mingnt=128
           *-generic:1 UNCLAIMED
                description: Unclassified device
                product: O2 Micro, Inc.
                vendor: O2 Micro, Inc.
                physical id: 3.1
                bus info: pci@0000:01:03.1
                version: 34
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0 mingnt=128

<snip>

---

### Post by dstew on 2008-04-09
Try this:```
lspci -n
```This gives the full PCI ID code, including vendor code, of each item. This might help.

---

### Post by jalynn2 on 2008-04-09
Here is the output of ls pci-n for the last two entries:

01:03.0 0000: 1217:0032 (rev 34)
01:03.1 0000: 1217:0032 (rev 34)

When I look this up on pci.sourceforge.net, I see that 1217 points to 02 Micro, Inc., but 0032 is not a valid device for that vender. Also, the 0000 code seems to be invalid too. I am guessing that this might be related to the "class 7 doesn't match header type 02. Ignoring class" messages I am getting on boot up. Does anyone know what generates that message? Is there a way I can see what message come from the hardware?

---

### Post by jalynn2 on 2008-04-09
Here's the result of lspci -s 01:03.0 -vvv

01:03.0 Non-VGA unclassified device: O2 Micro, Inc. Unknown Device 0032 (rev 34)
     !!! Invalid class 0000 for header type 02
     Subsystem: Dell Unknown device 00c9
     Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B-
     Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
     Latency: 64
     Interrupt: pin A routed to IRQ 0
     Bus: primary=01, secondary=02, subordinate=05, sec-latency=0
     Memory window 0: 00000000-00000000
     Memory window 1: 00000000-00000000
     I/O window 0: 00000000-00000003
     I/O window 1: 00000000-00000003
     BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset- 16bInt+ PostWrite-
     16-bit legacy interface ports at 03e1

---

### Post by dstew on 2008-04-09
> I see that 1217 points to 02 Micro, Inc., but 0032 is not a valid device for that vender.I don't know how to help you from here. As a last ditch effort you might try ndiswrapper with the Windows drivers. It might work for some PCMCIA cards.

---

### Post by DellCA on 2008-04-16
Jalynn2,  The Inspiron 2500 uses the "O2 Micro OZ6933 CardBus Controller".  From what you have posted it looks like you do not have the correct module loaded for that specific controller.  I don't know which specific driver you will need for linux to read it correctly, but with the full name you should be able to find it.

If you have other questions about the hardware in the 2500, I'll be happy to answer them.

Larry
Dell Customer Advocate

---

