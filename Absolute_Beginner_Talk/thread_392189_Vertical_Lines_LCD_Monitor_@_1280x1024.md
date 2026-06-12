---
title: "Vertical Lines LCD Monitor @ 1280x1024"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by tbuss on 2007-03-24
I have a Sceptre Xseries 17inch LCD Monitor with a native resolution of 1280x1024.  After installing Ubuntu the highest resolution I could configure was 1024x768. I then ran sudo **dpkg-reconfigure xserver-xorg** to configure my screen. After configuring the xserver, when I try to use a resolution higher than 1024x768 my monitor displays vertical bars. I have tried to use 1280x1024 with different refresh rates ranging from 60Hz to 80Hz; all display vertical bars. The following is my **xorg.conf **file for my video card and screen.
```

Section "Device"
	Identifier	"Intel Corporation 82815 CGC [Chipset Graphics Controller]"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	VideoRam	65536
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Sceptre"
	Option		"DPMS"
	HorizSync	30-81
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82815 CGC [Chipset Graphics Controller]"
	Monitor		"Sceptre"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

---

### Post by bodhi.zazen on 2007-03-24
Try changing your default color depth from:
> DefaultDepth	24

To 
> DefaultDepth	16

If that does not work, what video card are you using ?

---

### Post by tbuss on 2007-03-24
I changed the **DefaultDepth** from **24** to **16**; same result. The video card is onboard. I'm not sure what exactly, this computer was given to me. I've searched for the specs online and I beleive it might be **nVidia TNT2 Pro**. But like I said, I'm not certain. I've tried **LSPCI** to retrieve that info, unsure if the output useful:

tbuss@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82815 CGC [Chipset Graphics Controller] (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 11)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 11)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 11)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 11)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 11)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 11)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 11)
01:0c.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
tbuss@ubuntu:~$ 

Dell Optiplex GX150

---

### Post by bodhi.zazen on 2007-03-24
> **tbuss said:**
> I changed the **DefaultDepth** from **24** to **16**; same result. The video card is onboard. I'm not sure what exactly, this computer was given to me. I've searched for the specs online and I beleive it might be **nVidia TNT2 Pro**. But like I said, I'm not certain. I've tried **LSPCI** to retrieve that info, unsure if the output useful:

Yes, very much so, thanks.

It looks like you have the 815 chipset.

> tbuss@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: **Intel Corporation 82815 CGC [Chipset Graphics Controller] (rev 04)**

<clip>

I have used that chip in the past and reducing the color depth has worked ...

If that fails, first, not to ask the obvious, have you re-started X (Ctrl-Alt-Backspace) ?

If so, There may be an update for the 815, but I think this may be out dated (in favor of 195 resolution), I'm not sure.

Here is a link on that as well : 

[http://www.ubuntuforums.org/showthread.php?t=269052](http://www.ubuntuforums.org/showthread.php?t=269052)

Scroll down to the 815 section for a detailed how-to.

If that fails, try 915resolution (below 815)

[https://help.ubuntu.com/community/i915Driver](https://help.ubuntu.com/community/i915Driver)

[http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28Intel.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28Intel.29)

---

### Post by tbuss on 2007-03-24
Thanks for all your help, it worked! I re-started X and when Gnome initialized I went to system->preferences->screen resoltution and changed it to 1280x1024. I guess I've been using windoze for too long, when something doesn't work I automatically asume the worst. I hate to do this but I have another thread posted in Networking/Wireles. Do you think I should post that thread here as well?

[http://www.ubuntuforums.org/showthread.php?t=391843](http://www.ubuntuforums.org/showthread.php?t=391843)

---

