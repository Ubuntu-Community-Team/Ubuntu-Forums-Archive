---
title: "Please Help, TV TUNER"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by nagates on 2006-10-03
[http://www.sinovideo.com.cn/en/p/8/](http://www.sinovideo.com.cn/en/p/8/)

here is a link to my tv tuner could some please help me get this to work in ubuntu 6.06, im afraid if cant my tv tuner to work im gonna have to switch back to windows as i can not afford to buy a new card (plus i just got this card as a gift less then a month)

---

### Post by Jason_25 on 2006-10-03
I just bought a norwood micro tuner with a conexant chipset off of ebay for 9 bucks.  Your probably going to have trouble with that one.

---

### Post by nagates on 2006-10-03
> **nagates said:**
> [http://www.sinovideo.com.cn/en/p/8/](http://www.sinovideo.com.cn/en/p/8/)

here is a link to my tv tuner could some please help me get this to work in ubuntu 6.06, im afraid if cant my tv tuner to work im gonna have to switch back to windows as i can not afford to buy a new card (plus i just got this card as a gift less then a month)

:(

---

### Post by nagates on 2006-10-03
> **Jason_25 said:**
> I just bought a norwood micro tuner with a conexant chipset off of ebay for 9 bucks.  Your probably going to have trouble with that one.

well i think im gonna have to back to windows, because it would be extremely tacky of me to buy a new video card with my parents credit card, soo soon after they bought me one

---

### Post by CarpKing on 2006-10-03
I don't know all that much about such things.  Have you searched around to see if anyone else has got that device or a similar one working with Linux?  The DirectX requirement makes me doubtful though.  Of course, if you don't want to go back to Windows completely, you can always dual boot.

---

### Post by Jose Catre-Vandis on 2006-10-03
> **nagates said:**
> [http://www.sinovideo.com.cn/en/p/8/](http://www.sinovideo.com.cn/en/p/8/)

here is a link to my tv tuner could some please help me get this to work in ubuntu 6.06, im afraid if cant my tv tuner to work im gonna have to switch back to windows as i can not afford to buy a new card (plus i just got this card as a gift less then a month)

Lets do some fact finding and trouble shooting first.

here is a good link about saa7134
[http://gentoo-wiki.com/HARDWARE_saa7134](http://gentoo-wiki.com/HARDWARE_saa7134)
but it looks like it might be bttv
[http://www.linuxquestions.org/questions//showthread.php?t=475319](http://www.linuxquestions.org/questions//showthread.php?t=475319)

1. I assume it works OK in Windows?
   What can you find out about the tuner and chipset?(interrogate Device Manager) / (have a look at the drivers on the install CD)?
2. The Direct X thing is most likely a red herring, probably only to do with supplied software or Windows requirements for playing TV
3. Can't find much on the net about your chipset, but as it is analog it has more chance of working
4. What modules have you tried to get it working, bttv/saa7134 ?
5. Have you got TVTime installed to test it?
6. Does the box show up in command: lsusb or lspci -v ?
7. What is the output of your dmesg?

Give some feed back on these and we might get somewhere?

---

### Post by nagates on 2006-10-03
4. What modules have you tried to get it working, bttv/saa7134 ? - no idea what that is

---

### Post by nagates on 2006-10-03
[17179577.708000] hub 2-0:1.0: USB hub found
[17179577.708000] hub 2-0:1.0: 10 ports detected
[17179577.812000] **** SET: Misaligned resource pointer: dfa5e2c2 Type 07 Len 0
[17179577.812000] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[17179577.812000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [APCH] -> GSI 23 ( level, low) -> IRQ 217
[17179577.812000] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[17179577.812000] forcedeth: using HIGHDMA
[17179578.108000] usb 2-1: new high speed USB device using ehci_hcd and address

---

### Post by Jose Catre-Vandis on 2006-10-04
> **nagates said:**
> [17179577.708000] hub 2-0:1.0: USB hub found
[17179577.708000] hub 2-0:1.0: 10 ports detected
[17179577.812000] **** SET: Misaligned resource pointer: dfa5e2c2 Type 07 Len 0
[17179577.812000] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[17179577.812000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [APCH] -> GSI 23 ( level, low) -> IRQ 217
[17179577.812000] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[17179577.812000] forcedeth: using HIGHDMA
[17179578.108000] usb 2-1: new high speed USB device using ehci_hcd and address

Ok, so the device is there, what does
```

lsusb

```give you, and
```
lspci -v
```

bttv and saa7134 are the two main chipset/drivers used for tv cards. you can try to load them as follows, and then recheck your dmesg

In terminal

```
sudo rmmod saa7134
sudo modprobe saa7134
```

```
sudo rmmod bttv
sudo modprobe bttv
```
Do these one at a time. To remove either module:
```

sudo rmmod saa7134 or sudo rmmod bttv
```

if its an saa7134 card, you will see loads of text something like this:
> [17179590.828000] saa7133[0]: found at 0000:01:06.0, rev: 208, irq: 201, latency: 32, mmio: 0xe8000000
[17179590.828000] saa7133[0]: subsystem: 1043:4857, board: ASUSTeK P7131 Dual [card=78,insmod option]
[17179590.828000] saa7133[0]: board init: gpio is 0
[17179590.904000] ts: Compaq touchscreen protocol output
[17179590.964000] saa7133[0]: i2c eeprom 00: 43 10 57 48 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[17179590.964000] saa7133[0]: i2c eeprom 10: 00 01 20 00 ff 20 ff ff ff ff ff ff ff ff ff ff
[17179590.964000] saa7133[0]: i2c eeprom 20: 01 40 01 02 03 01 01 03 08 ff 00 cb ff ff ff ff
[17179590.964000] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179590.964000] saa7133[0]: i2c eeprom 40: ff 21 00 c2 96 10 03 32 15 00 ff ff ff ff ff ff
[17179590.964000] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179590.964000] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179590.964000] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179591.064000] tuner 2-004b: chip found @ 0x96 (saa7133[0])
[17179591.064000] tuner-core.c: no tuner extensions loaded!
[17179591.064000] tuner-core.c: no tuner extensions loaded!
[17179591.112000] tuner 2-004b: setting tuner address to 61
[17179591.152000] tuner 2-004b: type set to tda8290+75a
[17179591.216000] saa7133[0]: registered device video0 [v4l2]
[17179591.216000] saa7133[0]: registered device vbi0
[17179591.216000] saa7133[0]: registered device radio0
[17179591.232000] saa7134 ALSA driver for DMA sound loaded
[17179591.232000] saa7133[0]/alsa: saa7133[0] at 0xe8000000 irq 201 registered as card -1

---

### Post by nagates on 2006-10-04
buntu@ubuntu:~$ **_lsusb_**
Bus 002 Device 002: ID 6000:0001
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000
ubuntu@ubuntu:~$ _**lspci -v**_
0000:00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 815a
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <available only to root>

0000:00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0

0000:00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: 66MHz, fast devsel, IRQ 12
        I/O ports at e400 [size=32]
        I/O ports at 4c00 [size=64]
        I/O ports at 4c40 [size=64]
        Capabilities: <available only to root>

0000:00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2) (p rog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 50
        Memory at d2004000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3) (p rog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 58
        Memory at feb00000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio C ontroller (rev a2)
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 225
        I/O ports at dc00 [size=256]
        I/O ports at e000 [size=256]
        Memory at d2003000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2) (prog-if 8a [M aster SecP PriP])
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0
        I/O ports at f000 [size=16]
        Capabilities: <available only to root>

0000:00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
        Subsystem: ASUSTeK Computer Inc.: Unknown device 815a
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 217
        I/O ports at 09f0 [size=8]
        I/O ports at 0bf0 [size=4]
        I/O ports at 0970 [size=8]
        I/O ports at 0b70 [size=4]
        I/O ports at d800 [size=16]
        Memory at d2002000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 225
        I/O ports at 09e0 [size=8]
        I/O ports at 0be0 [size=4]
        I/O ports at 0960 [size=8]
        I/O ports at 0b60 [size=4]
        I/O ports at c400 [size=16]
        Memory at d2001000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2) (prog-if 0 1 [Subtractive decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=128
        I/O behind bridge: 00009000-0000afff
        Memory behind bridge: d0000000-d1ffffff
        Prefetchable memory behind bridge: c0000000-cfffffff

0000:00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 217
        Memory at d2000000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at b000 [size=8]
        Capabilities: <available only to root>

0000:00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        Capabilities: <available only to root>

0000:00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Capabilities: <available only to root>

0000:00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Capabilities: <available only to root>

0000:00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Capabilities: <available only to root>

0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Hyp erTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <available only to root>

0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Add ress Map
        Flags: fast devsel

0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRA M Controller
        Flags: fast devsel

0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Mis cellaneous Control
        Flags: fast devsel

0000:05:06.0 VGA compatible controller: ATI Technologies Inc Radeon R200 QM [Rad eon 9100] (prog-if 00 [VGA])
        Subsystem: VISIONTEK: Unknown device 7c15
        Flags: bus master, stepping, medium devsel, latency 32, IRQ 66
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at 9000 [size=256]
        Memory at d1000000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at d0080000 [disabled] [size=128K]
        Capabilities: <available only to root>

0000:05:0a.0 RAID bus controller: Silicon Image, Inc. SiI 3114 [SATALink/SATARai d] Serial ATA Controller (rev 02)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 8167
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 233
        I/O ports at 9400 [size=8]
        I/O ports at 9800 [size=4]
        I/O ports at 9c00 [size=8]
        I/O ports at a000 [size=4]
        I/O ports at a400 [size=16]
        Memory at d1018000 (32-bit, non-prefetchable) [size=1K]
        Expansion ROM at d0000000 [disabled] [size=512K]
        Capabilities: <available only to root>

0000:05:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000  Controller (PHY/Link) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, medium devsel, latency 32, IRQ 66
        Memory at d1019000 (32-bit, non-prefetchable) [size=2K]
        Memory at d1010000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

0000:05:0c.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
        Subsystem: ASUSTeK Computer Inc. Marvell 88E8001 Gigabit Ethernet Contro ller (Asus)
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 74
        Memory at d1014000 (32-bit, non-prefetchable) [size=16K]
        I/O ports at a800 [size=256]
        Expansion ROM at d00a0000 [disabled] [size=128K]
        Capabilities: <available only to root>

ubuntu@ubuntu:~$_** sudo rmmod saa7134**_
ERROR: Module saa7134 does not exist in /proc/modules
ubuntu@ubuntu:~$_** sudo modprobe saa7134**_
ubuntu@ubuntu:~$_** sudo rmmod bttv**_
ERROR: Module bttv does not exist in /proc/modules
ubuntu@ubuntu:~$**_ sudo modprobe bttv_**
ubuntu@ubuntu:~$

---

### Post by Jose Catre-Vandis on 2006-10-04
Ah you didn't say you had a usb mouse :D
```
Bus 001 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
```
Strange though, seems your usb tv card is not showing up at all ? ( You should be seeing "something" in lsusb.)

Can you test your usb ports first to make sure they all work OK? (swap your mouse about the ports, and also try another known working usb device at the same time as the mouse, check lsusb again.

Did your dmesg look any different after you loaded the modules (no errors usually means they loaded ;D), just in case it is managing to by pass hardware checks???

Does the device need power? Or switching on?

Don't despair, it may not be curtains yet. Took me nine months to sort out my tv card :lol:

---

### Post by fragos on 2006-10-04
It looks like you don't have a TV card.  Note the following on my system:

fragos@Geo:~$ lspci|grep media
0000:00:0a.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
0000:00:0a.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
0000:00:0b.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)

The two references to Brooktree are from a WinTV-GO supported by the bttv driver.  The Internext Compression Inc reference is for a second WinTV PVR 150 card which uses the ivtv driver.  The last is my sound support.

---

### Post by nagates on 2006-10-04
> **Jose Catre-Vandis said:**
> Ah you didn't say you had a usb mouse :D
```
Bus 001 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
```
Strange though, seems your usb tv card is not showing up at all ? ( You should be seeing "something" in lsusb.)

Can you test your usb ports first to make sure they all work OK? (swap your mouse about the ports, and also try another known working usb device at the same time as the mouse, check lsusb again.

Did your dmesg look any different after you loaded the modules (no errors usually means they loaded ;D), just in case it is managing to by pass hardware checks???

Does the device need power? Or switching on?

Don't despair, it may not be curtains yet. Took me nine months to sort out my tv card :lol:

sudo modprobe saa7134

[17181564.556000] usb 2-1: USB disconnect, address 2
[17181568.072000] usb 2-2: new high speed USB device using ehci_hcd and address 4
[17181695.592000] Linux video capture interface: v1.00
[17181695.628000] saa7130/34: v4l2 driver version 0.2.14 loaded
[17181695.684000] saa7134 ALSA driver for DMA sound loaded
[17181695.684000] saa7134 ALSA: no saa7134 cards found

$ sudo rmmod saa7134
ERROR: Module saa7134 is in use by saa7134_alsa


sudo modprobe bttv
[17181695.592000] Linux video capture interface: v1.00
[17181695.628000] saa7130/34: v4l2 driver version 0.2.14 loaded
[17181695.684000] saa7134 ALSA driver for DMA sound loaded
[17181695.684000] saa7134 ALSA: no saa7134 cards found
[17182297.360000] bttv: driver version 0.9.16 loaded
[17182297.360000] bttv: using 8 buffers with 2080k (520 pages) each for capture

---

### Post by nagates on 2006-10-12
> **nagates said:**
> sudo modprobe saa7134

[17181564.556000] usb 2-1: USB disconnect, address 2
[17181568.072000] usb 2-2: new high speed USB device using ehci_hcd and address 4
[17181695.592000] Linux video capture interface: v1.00
[17181695.628000] saa7130/34: v4l2 driver version 0.2.14 loaded
[17181695.684000] saa7134 ALSA driver for DMA sound loaded
[17181695.684000] saa7134 ALSA: no saa7134 cards found

$ sudo rmmod saa7134
ERROR: Module saa7134 is in use by saa7134_alsa


sudo modprobe bttv
[17181695.592000] Linux video capture interface: v1.00
[17181695.628000] saa7130/34: v4l2 driver version 0.2.14 loaded
[17181695.684000] saa7134 ALSA driver for DMA sound loaded
[17181695.684000] saa7134 ALSA: no saa7134 cards found
[17182297.360000] bttv: driver version 0.9.16 loaded
[17182297.360000] bttv: using 8 buffers with 2080k (520 pages) each for capture

help please??

---

### Post by nagates on 2006-10-12
> **nagates said:**
> sudo modprobe saa7134

[17181564.556000] usb 2-1: USB disconnect, address 2
[17181568.072000] usb 2-2: new high speed USB device using ehci_hcd and address 4
[17181695.592000] Linux video capture interface: v1.00
[17181695.628000] saa7130/34: v4l2 driver version 0.2.14 loaded
[17181695.684000] saa7134 ALSA driver for DMA sound loaded
[17181695.684000] saa7134 ALSA: no saa7134 cards found

$ sudo rmmod saa7134
ERROR: Module saa7134 is in use by saa7134_alsa


sudo modprobe bttv
[17181695.592000] Linux video capture interface: v1.00
[17181695.628000] saa7130/34: v4l2 driver version 0.2.14 loaded
[17181695.684000] saa7134 ALSA driver for DMA sound loaded
[17181695.684000] saa7134 ALSA: no saa7134 cards found
[17182297.360000] bttv: driver version 0.9.16 loaded
[17182297.360000] bttv: using 8 buffers with 2080k (520 pages) each for capture

?

---

### Post by cpauquez on 2006-10-26
I'm having the same problems.

```
cpauquez@ubx8600:~$ dmesg|tail 
[17179927.816000] usb 4-1: USB disconnect, address 2
[17179967.588000] hub 1-0:1.0: over-current change on port 1
[17179967.692000] hub 4-0:1.0: over-current change on port 1
[17179968.036000] usb 4-1: new high speed USB device using ehci_hcd and address 4
[17179968.176000] usb 4-1: configuration #1 chosen from 1 choice
[17179980.988000] usb 4-1: USB disconnect, address 4
[17179987.748000] hub 1-0:1.0: over-current change on port 1
[17179987.852000] hub 4-0:1.0: over-current change on port 1
[COLOR="Red"][17179988.196000] usb 4-1: new high speed USB device using ehci_hcd and address 5[/COLOR]
[17179988.336000] usb 4-1: configuration #1 chosen from 1 choice

```

I see that there is a new device on address 5. Then I list my connected usb devices:

```
cpauquez@ubx8600:~$ lsusb
[COLOR="Red"]Bus 004 Device 005: ID 6000:0001 [/COLOR] 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```

It don't know what means ID 6000:0001, so I get verbose list:

```
cpauquez@ubx8600:~$ sudo lsusb -v -d6000:0001

Bus 004 Device 005: ID 6000:0001  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x6000 
  idProduct          0x0001 
  bcdDevice            0.01
[COLOR="Red"]  iManufacturer          16 Trident
  iProduct               32 TVBOX[/COLOR]
  iSerial                64 2004090820040908
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           78
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration         48 2.0
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol    255 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol    255 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x1400  3x 0 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       2
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol    255 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x1400  3x 0 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0002
  (Bus Powered)
  Remote Wakeup Enabled

```

Then, I googled for Trident TVBOX, but... nothing.

---

### Post by Zionteam on 2006-11-01
> **cpauquez said:**
> I'm having the same problems.
Then, I googled for Trident TVBOX, but... nothing.

Same here....
any light on this matter???

my tv tunner is a Genius TvGo a03

---

