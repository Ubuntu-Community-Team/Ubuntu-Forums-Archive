---
title: "new laptop hardware woes (multiple problems)"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by KCormier on 2008-02-13
Howdy all.  I'm working on a Toshiba A215-S7437 laptop and I swear the thing is nothing but a headache with ubuntu.  No audio.  No wireless....::dies::  Does anything think it's possible that support could be added in in the future (maybe 8.04?) or should i just quit while I'm ahead.  I've really been pushing ubuntu as it's worked wonderful for the most part.  This still just doesn't wanna go anywhere though!  Any help would be appreciated

-kevin

---

### Post by macogw on 2008-02-13
It'd help if you gave us specifics on what hardware it has.  Can you post the output of ```
lspci
```

As far as future support goes, it's possible that there aren't open source drivers for wireless, meaning the drivers have to be gotten from the company because we can't distribute them.  Windows drivers can be used with ndiswrapper if there are no Linux drivers.  For Audio, if it's HDA, that can be problematic since although there's a "standard" none of the HDA cards seem to actually follow it, making the process of writing drivers for them a bit like herding cats.  If you can tell us what the card is, though, there's chance we can find something for you.  Overall support of devices isn't really up to Ubuntu, though.  That belongs in the realm of the kernel, where all the drivers go.  Audio drivers are written by the [Alsa Project](http://alsa-project.org).  There is, of course, always the possibility of bounties.  If you really want a specific thing to be developed or fixed, you can always pay someone to write the code for you.

---

### Post by KCormier on 2008-02-13
Thanks.  I'm messing with 8.04 now to see if anything changes but it looks like 8.04 doesn't even install on this machine.  I also noticed i put 32 bit ubuntu on a 64 bit machine.  I'm gonna reinstall ubuntu (since i've mucked with this last one so much that it keeps crashing) and then i'll post what you asked for :)  Thanks!!

-Kevin

---

### Post by macogw on 2008-02-13
Be forewarned that 32bit tends to work better than 64bit in the realm of compatibility with userspace stuff.  Though there is [a post with a very easy to use script for installing 64it Flash](http://ubuntuforums.org/showthread.php?t=476924), there could be other programs that are harder to make work or don't work at all (that almost always means commercial/proprietary programs with no 64bit version, though 32bit stuff can be installed on the 64bit OS).  I'm pretty sure Wine doesn't work on 64bit.

---

### Post by KCormier on 2008-02-13
```

00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 7914
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 7915
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon X1200 Series
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
14:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
14:06.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
14:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
14:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
14:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

```

No audio or network... :-\

---

### Post by macogw on 2008-02-13
Huh?  Audio is listed right here:```

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
```
And according to [this thread](http://ubuntuforums.org/showthread.php?p=3983746#post3983746), following [these directions](https://help.ubuntu.com/community/HdaIntelSoundHowto) using [this site](http://www.alsa-project.org/main/index.php/Main_Page) to download the drivers, you should be able to get it working.

And I think one of those two "unknown" lines near the top may be your wireless.  Can you run it again as ```
sudo lspci -vn
``` and post just the parts that go with the two "Unknown device"s?

---

### Post by KCormier on 2008-02-13
```
00:04.0 0604: 1002:7914 (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=07, sec-latency=0
	Capabilities: <access denied>

00:05.0 0604: 1002:7915 (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=0d, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: f8200000-f82fffff
	Prefetchable memory behind bridge: 0000000088000000-00000000880fffff
	Capabilities: <access denied>
```

I'll let you know how the audio works out!  Thanks!

---

