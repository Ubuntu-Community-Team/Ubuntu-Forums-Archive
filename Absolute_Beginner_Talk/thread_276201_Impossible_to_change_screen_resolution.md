---
title: "Impossible to change screen resolution"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by ww2 on 2006-10-12
I'm posting this from Dapper live cd. For some reason, Ubuntu selected 640x480/60 Hz as default screen resolution/refresh rate. When attempting to change it at "System > Preferences > Screen Resolution", I'm presented with no extra options, meaning I can't select something different than the screen mode I'm already at.

I would certainly proceed with the install, but at this resolution I can't see the complete installation wizard window (lower buttons are covered).

From a few minutes of searching, I found out this is a known problem with Dapper, and attemped to follow the instructions available in the following post:

[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

Didn't work (nothing changed, simply). I also tried manually editing /etc/X11/xorg.conf, but there was nothing to edit. Seeing the configuration file, it appears as my vga card and monitor were properly identified, and the 1024x768 mode is available for all bit depths.

From the hardware standpoint, I'm sure everything is proper. I use this PC with Windows XP, in which I had no problems with my vga card or monitor (including playing heavy 3d games at 1024x768@85 Hz, the recommended mode for my Sony monitor).

So, in case it is relevant, the following are my vga and monitor specs, respectively:

Radeon 9600 XT AGP 128 mb
Sony Trinitron Multiscan E200 17"

The "Screen" section in /etc/X11/xorg.conf:

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
	Monitor		"SONY CPD-E20"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection
```

I'm really looking forward trying Ubuntu, so this is really disappointing. Any help you can provide me will be appreciated. Thanks.

---

### Post by petri on 2006-10-12
Try to change the resolution with [SIZE="2"]Ctrl[/SIZE] and [SIZE="2"]Alt[/SIZE] and [SIZE="3"]-[/SIZE] (minus sign)
or with [SIZE="2"]Ctrl[/SIZE] and [SIZE="2"]Alt[/SIZE] and [SIZE="3"]+[/SIZE] (plus sign)

If you can see the buttons it should be safe to install because then you can install drivers with a guide you find here [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

If you can't see the buttons then you should download an Alternate CD, that will work because it does not have a live-session because it has an textbased installation. How to use that one then? You can take a look at Hermans site which has an illustrated installation with the alternate CD: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by ww2 on 2006-10-12
Thanks for answering, Petri.

I tried the Ctrl + Alt + +/- shortcut you suggested, but nothing happened. And I definitely can't see the buttons.

Certainly there's a way other than downloading another iso? I would do that, surely, but fixing this would be more desirable.

---

### Post by MasonM on 2006-10-12
In the xorg.conf file, find the "Device" section that identifies your video card. I'm betting that it is using the "ati" driver. If you change that from "ati" to "vesa" then you should be able to get a good resolution for the installation.

After install use the package manager to install the xorg-fglrx package. Edit the xorg.conf and change "vesa" to "fglrx" and it should be fine.

---

### Post by ww2 on 2006-10-12
Indeed! It said "ati". I changed to "vesa", as you instructed, and restarted X with Ctrl + Alt + Backspace. Screen resolution changed to 1280x1024 immediately, while refresh rate was kept 60 Hz. But if I go to "System > Preferences > Screen Resolution" again, and attempt to change it to 1024x768, which is the recommended setting for my monitor, I get the "out of range" monitor error. Ubuntu gets back to the previous resolution shortly after that.

What would I have to do to fix that behavior while still in the live cd? (Sorry to insist, but 1280x1024 at 60 Hz is a little painful on the eyes).

---

### Post by petri on 2006-10-12
As I understood you are going to install? Do it now and install proper drivers as I linked above and you should be up and running. (can I write that in that way?) :mrgreen: 

If you are doing this DesktopCD installation you can browse the internet at the same time and here you find a goood illustrated howto for it: [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by MasonM on 2006-10-13
I thought your goal was to get a resolution that would allow you to perform the install? 

If you're doing an install and can now see all of the window, just do the install and worry about getting correct driver and resolution once it is completed. When you install the xorg-fglrx package and use fglrx as your video driver you'll be able to set it just as you want.



I also use an ATI card. Trust me, it works fine.

---

