---
title: "Poor sound on iMac 7,1"
date: 2009-10-24
forum: Apple Hardware Users
---

### Post by Mike54 on 2009-10-24
I have used Ubuntu off and on until recently installing Jaunty on a PC.  Everything worked so well, I decided to do a dual boot on my iMac 7,1.  I installed rEFIt and got Jaunty running with a couple of issues.

The primary issue was no sound.  I looked the forums and the wiki over and managed to get sound, albeit very poor quality, by adding the line 'options snd-hda-intel model=imac24' to */etc/modprobe.d/options*

I now have sound, but it is faintly reminiscent of the quality of a pocket transistor AM radio, in the late 60's.  I upgraded to Karmic in the hopes I might find a fix, but no hope.

As mentioned, I looked through these forums to no avail.  I've scoured the Kubuntu forums, the Mint forums and other Linux forums, but cannot seem to find a solution.  It seems there are others having the same problem, but there are no apparent solutions.

I never really cared for OS X and this machine was a bit of a bald-headed step-child until I got Ubuntu running on it.  I've been around long enough to know Ubuntu requires some tweaks to get things working, so I am hoping someone might be able to provide a bit of help.  I would ask you to assume I know nothing about Ubuntu and provide assistance in that manner.  I will provide as much information as I know to provide.

Aluminum iMac 7,1
Dual boot OS X Snow Leopard and Karmic Koala using rEFIt

Output of lspci -

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon HD 2400 XT
03:00.0 FireWire (IEEE 1394): Agere Systems FW643 PCI Express1394b Controller (PHY/Link) (rev 05)
04:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
05:00.0 Ethernet controller: Marvell Technology Group Ltd. Marvell Yukon 88E8058 PCI-E Gigabit Ethernet Controller (rev 13)
```

utput of lspci -l

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```output of aplay -l

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```output of hwinfo --sound

```
12: PCI 1b.0: 0403 Audio device                                 
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_284b
  Unique ID: u1Nb.2frKzjmhZt4
  SysFS ID: /devices/pci0000:00/0000:00:1b.0
  SysFS BusID: 0000:00:1b.0
  Hardware Class: sound
  Model: "Intel 82801H (ICH8 Family) HD Audio Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x284b "82801H (ICH8 Family) HD Audio Controller"
  SubVendor: pci 0x106b "Apple Computer Inc."
  SubDevice: pci 0x00a0 
  Revision: 0x03
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0x50700000-0x50703fff (rw,non-prefetchable)
  IRQ: 20 (2957 events)
  Module Alias: "pci:v00008086d0000284Bsv0000106Bsd000000A0bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```Output of lsusb -

```
Bus 002 Device 003: ID 05ac:8502 Apple, Inc. Built-in iSight
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 05ac:8242 Apple, Inc. 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c044 Logitech, Inc. LX3 Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 05ac:0220 Apple, Inc. Aluminum Keyboard
Bus 001 Device 003: ID 05ac:1006 Apple, Inc. Hub in Aluminum Keyboard
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 05ac:8206 Apple, Inc. Bluetooth HCI
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```Any help will be deeply appreciated.  I'm confident there has to be a fix for this, I'm just not savvy enough to sort it myself.

---

### Post by Eadz on 2009-10-24
Hi there,

In my macbook ( 5.1 ) I have the same sound card as you I think. ( 889A). 

this is my output of aplay -a 

> 
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



I am having some issues but I have 2 things to suggest. 

Check alsamixer in the console, possibly change the number of channels. 

Try without model=imac24, and also maybe model=mbp3. 889A support is quite new i think.. 

With model=mbp3 I only get sound out of one speaker. I think apple may have a bass speaker and a tweeter as left and right speakers. 

So i think the trick is to find the driver that was autodetected for my machine. 

/usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz 

contains all the hardware models, now 889A is not listed!! 

imac24 is a setting for ALC882/885 not 889A. I'm not an expert at this stuff, as I am using mbp3 which is also for the ALC882. 

However, maybe one of the other ALC882 codes might work. 

The ideal solution is for there to be a 889A driver listed!

---

### Post by Mike54 on 2009-10-24
Thanks for the reply, Eadz.

I removed *model=imac24* and was back to no sound.

I added *model=mbp3* and got the same tinny sound as I had with *model=imac24*.

Maybe that will help someone understand what is happening a bit more?

I feel like a kid with a new toy, running Ubuntu on the iMac and I don't want to throw in the towel and go back to OS X.  But the rotten sound quality has got to improve, by hook or by crook.

---

### Post by Eadz on 2009-10-24
This really is a bug so I would file a bug report- missing support for 889A - it's not in the list of cards in the alsa documentation so I think that's a clue that this support is missing.

update - I reccomend googling "ALC889A alsa"  - there is lots of stuff. It seems that it is intentional that the card is mis-recognised as 882.

---

