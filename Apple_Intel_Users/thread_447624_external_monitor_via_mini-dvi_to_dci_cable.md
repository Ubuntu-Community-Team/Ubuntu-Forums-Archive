---
title: "external monitor via mini-dvi to dci cable"
date: 2007-05-18
forum: Apple Intel Users
---

### Post by krangnes on 2007-05-18
I'm having major difficulties getting my Toshiba 37WL66 to work. II run Feisty on my Macbook. It works just fine under OS X, so the hardware is able to run it. I have a mini-dvi to dvi adapter that I want to connect through.

The documentation says that it's a WXGA 1366 x 768 pixels, but from what I could find out, X labels it as 1360x768 pix. OS X runs it at 1366 x 768. It can play 720p 1080i from my DVD as well. But I can't seem to get it to work at all under Ubuntu. The best I've got is a black screen...I've read alot about the resolutons 915resolution and what the intel driver can support, but I can't seem to figure it out.

lspci -x gives me:
```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00: 86 80 a0 27 06 00 90 20 03 00 00 06 00 00 00 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 86 80 70 72
30: 00 00 00 00 e0 00 00 00 00 00 00 00 00 00 00 00

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00: 86 80 a2 27 07 00 90 00 03 00 00 03 00 00 80 00
10: 00 00 38 90 f1 20 00 00 08 00 00 80 00 00 40 90
20: 00 00 00 00 00 00 00 00 00 00 00 00 86 80 70 72
30: 00 00 00 00 90 00 00 00 00 00 00 00 0a 01 00 00

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00: 86 80 a6 27 07 00 90 00 03 00 80 03 00 00 80 00
10: 00 00 30 90 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 86 80 70 72
30: 00 00 00 00 d0 00 00 00 00 00 00 00 00 00 00 00

```

I start X with only the Laptop LCD running, and I run ddcprobe and I get this in return:
```

vbe: VESA 3.0 detected.
oem: Intel(r) 82945GM Chipset Family Graphics Chip Accelerated VGA BIOS
vendor: Intel Corporation
product: Intel(r) 82945GM Chipset Family Graphics Controller Hardware Version 0.0
memory: 16064kb
mode: 1280x1024x256
mode: 1280x1024x64k
mode: 1280x1024x16m
mode: 1024x768x256
mode: 1024x768x64k
mode: 1024x768x16m
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 640x480x256
mode: 800x600x256
mode: 640x480x64k
edid: 
edid: 1 3
id: 0104
eisa: TSB0104
serial: 00000000
manufacture: 0 2006
input: analog signal.
screensize: 196 142
gamma: 1.000000
dpms: RGB, no active off, no suspend, no standby
dtiming: 1920x540@62
dtiming: 720x576@50
monitorname: TOSHIBA-TV
monitorrange: 15-46, 49-61

```

With the help of google I found the following page (in finish): [http://www.dvdplaza.fi/forums/showthread.php?t=49803&page=9](http://www.dvdplaza.fi/forums/showthread.php?t=49803&page=9) . I don't understand a word of it, but it seem to agree with my assumptions concerning the TV.

720p seems to be supported, as well as 1080i. I need to add additional resolutions to it, so I made a script that run straight after 915resolution in /etc/rc.local
```

#!/bin/bash

915resolution 30 720 576 8
915resolution 41 720 576 16
915resolution 50 720 576 32

915resolution 38 1920 540 8
915resolution 49 1920 540 16
915resolution 58 1920 540 32

exit 0

```

915resolution -l seems to register the new reslutions:
```

Chipset: 945GM
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 36

Mode 30 : 720x576, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1920x540, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1280x800, 8 bits/pixel
Mode 41 : 720x576, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1920x540, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1280x800, 16 bits/pixel
Mode 50 : 720x576, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1920x540, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1280x800, 32 bits/pixel

```

I used the "default" xorg.conf found here: [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook) as a reference and added a TV server to it with these settings. When I start X again, it fails. From the log, I find something interesting:
```

(II) intel(0): Attempting memory allocation with tiled buffers and 
	       large DRI memory manager reservation:
(WW) intel(0): xf86AllocateGARTMemory: allocation of 10 pages failed
	(Cannot allocate memory)

```

I then genriously gave it some VideoRAM in the device sections, but alas. To no avail. But it says that there is memory available, the driver doesn't seem to be able to allocate it:
```

(II) intel(0): I830CheckAvailableMemory: 931836 kB available
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with tiled buffers and 
	       large DRI memory manager reservation:
(WW) intel(0): xf86AllocateGARTMemory: allocation of 10 pages failed
	(Cannot allocate memory)
(II) intel(1): Allocating 0 scanlines for pixmap cache

```

I then played around with the BusID, and set the following:
```

Section "Device"
        Identifier      "TV Device (2)"
        Driver          "intel"
        BusID           "PCI:0:2:1"
        Screen          1
        Option          "MonitorLayout" "DFP"
EndSection

```

That resulted in the Macbook Screen having vertical colored lines. I assume it tried to apply the TV's resolution to the macbook.

I've attaced my xorg.conf 

Does anybody have a clue what's going on? is 1920x540 and 720x576 viable options? How about the 1360x760 resolution? Also, how does the BusID stuff work? I thought maybe 0:2:1 was the external head, but for the clone and xinerama server, they both use PCI:0:2:0. I don't get it.... Any help appriciated.

---

### Post by veloce on 2007-05-23
I'm wrestling with the same issues.  

To get your system working with two monitors, I suggest you switch to the "i810" driver rather than "intel".  It doesn't crash when it can't allocate enough memory (it just turns off 3d acceleration).  If you switch to this driver, you will need 915resolution (it is not required with "intel" driver).

I'm searching for a way to overcome the issues with this hardware's DVMT - which doesn't seem to be working with any flavour of linux.

---

### Post by krangnes on 2007-05-28
it works just fine with external vga clone or xinerama, intel or i810 driver or whatnot. I just can't seem to make the DVI work. But I guess it some sort of 915 resolution issue, with resolutions not being registered by X or something. The log at least seems to think so

---

### Post by veloce on 2007-05-29
> **krangnes said:**
> it works just fine with external vga clone or xinerama, intel or i810 driver or whatnot. I just can't seem to make the DVI work. But I guess it some sort of 915 resolution issue, with resolutions not being registered by X or something. The log at least seems to think so

Are you saying you can get dual head working with the intel driver rather than i810?  If so, I'd really like to hear details of your setup and see your xorg.conf?

---

