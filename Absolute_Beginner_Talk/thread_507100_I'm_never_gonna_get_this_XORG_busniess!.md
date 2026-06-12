---
title: "I'm never gonna get this XORG busniess!"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2007-07-22
I'm following this tutorial in order to fix my resolution so that it just work.
[http://doc.gwos.org/index.php/ChangeResolution#Howto:_change_resolution.2Frefresh_rate_in_Xorg](http://doc.gwos.org/index.php/ChangeResolution#Howto:_change_resolution.2Frefresh_rate_in_Xorg)
So far I've only gotten to 
       # 1.2 How to reconfigure Xorg
doing the commandline.  But it says I didn't use the right login info or something :confused:
```
sudo dpkg-reconfigure xserver-xorg
```

Now what am I supposed to do?  I'm pretty sure that I've spelt everything right when doing that command.
Help plz, I'm starting to get annoyed at my nemesis XORG :mad:

---

### Post by annda on 2007-07-22
what exactly was the error message?

also, it's always a good idea to copy & paste commands, just in case.

---

### Post by cawill on 2007-07-22
EDIT: sorry didn't read you're post fully, if login in fails then in GRUB select recovery mode and this should log you in as root.

Then do this:
Try this command instead: '(sudo) dpkg-reconfigure -phigh xserver-xorg'.

From my experience all I had to do was select a driver and select resolutions, so you can select the resolution you want.

Then just restart X, 'startx' in the shell or CTRL + ALT + Backspace

Hope this works.

---

### Post by jingo811 on 2007-07-22
I seem to have forgotten to login with my user account before doing the command line.  Anyhow all possible resolutions is now unlocked on Ubuntu.  I just need to configure the horizontal and vertical refresh rate in XORG later.
But I have a new problem. :(
From following the guide and doing things without knowing what they do.  I recklessly tried every shortcut commands they suggested.  Now I broke my keyboard functions for instance if I wanted to type.

&dev&sda1 

you see my keys are shuffled.  How can I fix this_  (I can\t even  find the question mark to finish this sentence)

---

### Post by annda on 2007-07-22
oops, looks like you have changes the keyboard layout while reconfiguring xorg... you can solve the problem with the mouse. right-click on the panel and add a keyboard switcher applet  (i'm in KDE now, so not sure what exactly it is called, but you will find it out) from there you can configure the layout - right click i think.

---

### Post by w4ett on 2007-07-22
Try System>Preferences>Keyboard Preferences

---

### Post by jingo811 on 2007-07-22
tnx /dev/gurus!  You solved my ? keyboard questionmarks ?
I'll be back tommorrow with more whining when I fail at editing my Horizontal and Vertical rate in xorg.conf :-)

---

### Post by jingo811 on 2007-07-23
Yeah so I'm having problem with XORG again this time it's the refresh rate originally you could only choose 50 Hz.  Now when I have configured it I only was able to unlock 54 and 55 Hz.  My monitor can handle 75 Hz.
Here's how I did thing, can you see what I've done wrong?

```
gksudo gedit /etc/X11/xorg.conf
```

_HP vs173_
1280 x1024 @ 75 Hz max
0.264 mm dot pitch
horizontal = 30-81 kHz
vertical = 56-76 Hz
[http://h10010.www1.hp.com/wwpc/ie/en/ho/WF06a/20491-314293-314303-314303-314303-12314696.html](http://h10010.www1.hp.com/wwpc/ie/en/ho/WF06a/20491-314293-314303-314303-314303-12314696.html)

> Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	BusID		"PCI:6:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	**30-81**
	VertRefresh	**56-76**
[B]# V-freq: 75.00 Hz  // h-freq: 80.42 KHz
Modeline "1280x1024" 151.83  1280 1360 1544 1888  1024 1024 1027 1072 [/B]
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

The highlighted part of the xorg.conf is what I changed and added.
Help plz?
By the way I got the modeline from
[http://www.bohne-lang.de/spec/linux/modeline/](http://www.bohne-lang.de/spec/linux/modeline/)
by choosing 1280 x 1024, 75 Hz.

---

### Post by jingo811 on 2007-07-23
Anybody who's experienced in tweaking xorg.conf file I'm stuck don't know what else to do :confused:

---

### Post by Jon@bayleys.org.uk on 2007-07-23
Are you using a TV for output? If not, chances are you don't need to bother with custom modelines. I would suggest that first of all, have a look at the bottom end of /var/log/Xorg.0.log and see if you can see what the problem is there. also find out what graphics card you have, search on these forums for the driver you should be using. If you haven't got it, download it (Mainly this happens if you've got an ATI card), next run the command 'sudo dpkg-reconfigure -phigh xserver-xorg' No quotes. If that doesn't work, and you get an error, press ctrl alt and F1, which will kill your xserver, log in and try 'sudo dpkg-reconfigure xserver-xorg' (Again no quotes). In terms of monitor settings, go for simple, unless you want to access a certain resolution/refresh rate, this is much the easier way. Once you've got your new xorg.conf, run 'sudo /etc/init.d/gdm restart' (No quotes), if that doesn't work, come back and try again. Good luck!

---

### Post by MrHippocampus on 2007-07-23
First thing I would do is comment out the "ModeLine" line by putting a hash in front of it. Then restart X and run "nvidia-settings" and go to the display configuration page, see if you can select the resolution/vsync there. Whenever ive used the dpkg-reconfigure stuff it has only made things worse :(

---

### Post by jcronkhite on 2007-07-23
[http://www.linux.com/feature/118108]("http://www.linux.com/feature/118108")

---

### Post by jingo811 on 2007-07-24
[SIZE="4"]1.[/SIZE]
> First thing I would do is comment out the [COLOR="Olive"]"ModeLine"[/COLOR] line by putting a hash in front of it. Then restart X and run [COLOR="Olive"]"nvidia-settings"[/COLOR] and go to the display configuration page, see if you can select the resolution/vsync there. Whenever ive used the dpkg-reconfigure stuff it has only made things worse 

I've commented out "ModeLine" now!  Nvidia-settings program which got installed by Automatix2 which won't go away even when uninstalling it has never really helped me when it comes to changing things.  Also it sees my[COLOR="Olive"] 17" TFT[/COLOR] as a[COLOR="Olive"] CRT screen[/COLOR] and there's no buttons to change that.
The resolution changing in this program was only unlocked after I had done the
[COLOR="Olive"]dpkg-reconfigure stuff.[/COLOR]

[SIZE="4"]2.[/SIZE]
> Are you using a TV for output? If not, chances are you don't need to bother with custom modelines. 
No I don't use TV for output, ModeLines is commented out now.

[SIZE="4"]3.[/SIZE]
> I would suggest that first of all, have a look at the bottom end of /var/log/Xorg.0.log and see if you can see what the problem is there.
It's a pretty long list I'm not sure what to look for?

Starting on line: 333
```
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) NVIDIA dlloader X Driver  1.0-9755  Mon Feb 26 23:23:13 PST 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 06:00:0
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
[COLOR="Red"](WW) Warning, couldn't open module wfb[/COLOR]
(II) UnloadModule: "wfb"
[COLOR="Red"](EE) Failed to load module "wfb" (module does not exist, 0)[/COLOR]
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
```

Starting on line: 456
```

(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
[COLOR="Red"](WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0[/COLOR]
[COLOR="Olive"](II) NVIDIA(0): NVIDIA GPU GeForce 6200 LE at PCI:6:0:0 (GPU-0)[/COLOR]
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.44.02.62.00
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6200 LE at PCI:6:0:0:
(--) NVIDIA(0):     CRT-0
(--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
[COLOR="Olive"](II) NVIDIA(0):     "1280x1024"[/COLOR]
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
[COLOR="Red"](WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from CRT-0's EDID.[/COLOR]
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
```

[SIZE="4"]4.[/SIZE]
> also find out what graphics card you have, search on these forums for the driver you should be using. If you haven't got it, download it (Mainly this happens if you've got an ATI card), next run the command 'sudo dpkg-reconfigure -phigh xserver-xorg' No quotes. 

[COLOR="Olive"](II) NVIDIA(0): NVIDIA GPU GeForce 6200 LE at PCI:6:0:0 (GPU-0)[/COLOR]

I did this before I started this thread.
```
1. sudo /etc/init.d/gdm stop
2. Ctrl+ Alt+ F1
3. logged in with user account.
4. sudo dpkg-reconfigure -phigh Xserver-xorg
5. sudo /etc/init.d/gdm start
6. Ctrl+ Alt+ Backspace

```

[SIZE="4"]5.[/SIZE]
> If that doesn't work, and you get an error, press ctrl alt and F1, which will kill your xserver, log in and try 'sudo dpkg-reconfigure xserver-xorg' (Again no quotes). In terms of monitor settings, go for simple, unless you want to access a certain resolution/refresh rate, this is much the easier way. Once you've got your new xorg.conf, run 'sudo /etc/init.d/gdm restart' (No quotes), if that doesn't work, come back and try again. Good luck!

Yeah I prefered to do it this way.  When using that
sudo dpkg-reconfigure -phigh Xserver-xorg
I choose the [COLOR="Olive"]nvidia driver alternative[/COLOR].

[SIZE="4"]6.[/SIZE]
My resolution settings is satisfactory **I just want to adjust the Refresh rate to 75 Hz** right now only 50 and 54 Hz are available in Ubuntu's resolution settings program.

---

### Post by MrHippocampus on 2007-07-24
```

(WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0

```
Well, theres your main problem, the monitor isnt giving out EDID information so the driver doesnt know what the monitor is capable of (btw, your TFT is recognised as a CRT because it is using a VGA cable, theres nothing you can do about this).

You could try telling the nvidia driver to completely ignore the EDID information, not sure how much this will help though.
```

Section "Device"
     Identifier "Generic Video Card"
     Driver "nvidia"
     BusID "PCI:6:0:0"
     Option		"UseEDID" "FALSE"
EndSection

```

---

### Post by jingo811 on 2007-07-24
Nah I don't think that option line did anything.  But fortunately it seems like I've missed something on the Nvidia settings program :)  There was a drop down list for refresh rate which I missed.
But when comparing the effects of Nvidia settings and Ubuntu resolution program there's a frequency difference :confused:
When running 60 Hz in Nvidia Ubuntu shows 54 Hz
When running 75 Hz in Nvidia Ubuntu shows 90 Hz	:shock: That could FRY my monitor right?
So I'm gueesing I can't reach 75 Hz with Feisty on this PC??

[IMG]http://i10.tinypic.com/4lq457d.png[/IMG]
[IMG]http://i18.tinypic.com/4mss7bt.png[/IMG]

---

### Post by MrHippocampus on 2007-07-24
To be honest I would trust what the nvidia driver says over what the screen resolution preferences says. Besides, most modern monitors will restrict the Hz of the input signal, so even if you did try to pump 90Hz through it the screen would probably just say "input not supported" or something similar.

---

### Post by jingo811 on 2007-07-24
Allright captain, I'll pump it up to warp speed 90 Hz then :)

---

