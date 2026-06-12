---
title: "The Tricky Business of Installing Linux on a Mac... (sound +external video)"
date: 2011-11-29
forum: Apple Hardware Users
---

### Post by nahoskins on 2011-11-29
I have installed various operating systems on my poor macbook pro over the last few months, from Back Track 5 (which simply REFUSED to cooperate with my broadcom driver! Finicky bitch that it is.) to Open Suse, Puppy, Windows 7, Lion... It's a bit of a ****.

It's been a fun ride and all, but I'm running into two seemingly innocuous problems for which I have been unable to find a viable solution, on Ubuntu of all things.

The first is a simple audio problem. The right channel is the only one that works, this is presumably the reason all sound on the system is almost impossible to hear. I have tried AlsaMixer, which is what I have been repeatedly told to use to fix the problem, to no avail.

The second is something also quite simple but perplexedly difficult to solve. You know those funny Apple Display ports we keep getting forced on us? The Mini Display Port. Yeah, well whatever I plug into it (VGA, HDMI) is having difficulty playing ball with my Display Manager, it simply cant see it!

I am attaching my lspci output below:
$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 18)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 06)
00:1a.7 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 06)
00:1d.7 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
01:00.0 VGA compatible controller: nVidia Corporation GT216 [GeForce GT 330M] (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe (rev 10)
03:00.0 Network controller: Broadcom Corporation BCM43224 802.11a/b/g/n (rev 01)
04:00.0 FireWire (IEEE 1394): Agere Systems FW643 PCI Express1394b Controller (PHY/Link) (rev 08)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)


I am running Ubuntu 11.1 on Intel® Core™ i5 CPU M 520 @ 2.40GHz × 4 with 3.7 GB Memory.

Please Ubuntu Forums, you're my only hope.

---

