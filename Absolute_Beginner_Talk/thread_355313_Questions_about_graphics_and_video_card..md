---
title: "Questions about graphics and video card."
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by Xummoner on 2007-02-07
I was looking at the Xorg.log file just to see if there was any warnings or errors, and I found several but I don't know what they mean. 
Everything's working fine, except eye candy related stuff, so I dunno if this might be related to it. 

Here are the errors and warnings on the log. (I won't paste the whole log for space reasons).

```
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(WW) fglrx(0): Bad V_BIOS checksum
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): Specified desktop setup not supported: 8
(WW) fglrx(0): Option "XAANoOffscreenPixmaps" is not used
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used

(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory

(EE) fglrx(0): [agp] Failed to remmap MC AGP aperture base!
```

Another couple of things that might be taken in consideration:

-I thought my video card was AGP, since that's what the box says and it is connected to the AGP port but under the Xorg.conf it is displayed under a PCI port, and then again looking at the log file there's a line saying that the device is AGP version 2.0 or something like that.

-I was trying (for the 1238562th time) to install and run Beryl so I changed some stuff on the xorg.conf file, I used to use the "ati" driver under the device section, then I changed it to "fglrx" and it worked fine, but then I changed it to "ati" again, and X wouldn't start, luckily I kinda remembered how to sudo nano the xorg.conf file and managed to changed "ati" to "fglrx".

-I'm running Dapper, got a Radeon 9200 128MB video card (I think, since the box says something, Ubuntu another, the manual nothing, etc). 

Well, I hope someone can give me some information about this as well as some troubleshooting, thanks in advance. ;)

---

### Post by sunexplodes on 2007-02-07
by default xorg.conf contains settings for wacom graphics tablets. you don't have one.

that's what all that /dev/wacom stuff is about.

the rest i'm not sure of.

---

