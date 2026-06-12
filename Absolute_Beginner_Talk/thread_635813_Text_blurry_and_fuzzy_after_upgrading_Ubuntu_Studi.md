---
title: "Text blurry and fuzzy after upgrading Ubuntu Studio from Feisty to Gutsy"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by seanfitz64 on 2007-12-09
After upgrading from Feisty/7.04 to Gutsy/7.10 text on my laptop's LCD screen is not as crisp as it was. The text in all programs and system text (menus etc.) is blurry and fuzzy and I can see colours around black text. It as if I am no longer displaying at native resolution (but I am - 1024x768 ) and interpolation is occurring. 

When I first installed Ubuntu Studio on my laptop (Fiesty/7.04) I had trouble with my video driver... I couldn't run 3D graphics. After some research I fixed the problem by changing from the intel driver that was chosen at installation to the i810 driver.

I thought my current problem could be related, but my xorg.conf hasn't changed. Here is the relevant section:

```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

```
Just for kicks I changed back to the intel driver, but that didn't fix the problem... and I couldn't run 3D graphics again.

I even tried re-installing xserver-xorg-video-i810 (and xserver-xorg-video-intel for good measure) to no avail.

I don't understand what could have changed during the upgrade.

I've spent a good amount of time in the forums but no-one else seems to have the same problem. Other people report blurry text, but the solution is to change their driver or their settings (bit depth, resolution, refresh rate, font rendering). I have tried these changes wherever I can just to make sure, but to no avail. My situation is different - settings are the same after upgrade, but graphics have changed.

My graphics card is a Mobile 915GM/GMS/910GML Express Graphics Controller.

I saw someone suggest running 'sudo lshw | less' so I did and got this:

```
        *-display:0
             description: VGA compatible controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga bus_master cap_list
             configuration: latency=0

```
Someone else suggested running fglrxinfo and I got this:

```
display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 915GM 20061017 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 7.0.1
```

I hope there is enough info here to give a clue as to what is going on.

Please help... the screen is hurting my eyes and giving me a headache! :(

---

### Post by walkerk on 2007-12-09
If you are going to use the i810 driver you'll need to use 915resolution (available in the repos)... 

You could try this again..
```
sudo apt-get install xserver-xorg-video-intel xserver-xorg-video-all
```

Now ensure that your xorg.conf read similar to this:
> Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/..... Express Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Now reboot. Good luck

---

### Post by seanfitz64 on 2007-12-09
Thanks** walkerk**, but it looks like 915resolution is already installed. This is what I got on running the suggested command:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-intel is already the newest version.
xserver-xorg-video-intel set to manual installed.
xserver-xorg-video-all is already the newest version.
xserver-xorg-video-all set to manual installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by walkerk on 2007-12-09
Ok.. let's try to re-install the packages...

First remove the deb archives:
```
cd /var/cache/apt/archives

sudo rm xserver-xorg-video*

```

Now re-install the packages...
```
sudo apt-get --reinstall install xserver-xorg-video-intel xserver-xorg-video-all
```

Reboot...
```
sudo reboot
```

Once you've done this please post your xorg.conf

---

### Post by seanfitz64 on 2007-12-09
**walkerk**: I've done as you've suggested, but the relevant section of xorg.conf looks the same to me:

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"v4l"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by walkerk on 2007-12-09
If you've installed the xserver-xorg-video like I suggested you need to change your xorg.conf...

First back it up...
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.back
```

Open it...
```
gksu gedit /etc/X11/xorg.conf
```

Now change it from this:
```

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option		"UseFBDev"		"true"
EndSection
```

to this:
```

Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection
```

Now reboot

---

### Post by walkerk on 2007-12-09
Is it working now?

---

### Post by seanfitz64 on 2007-12-09
> **walkerk said:**
> Is it working now?

Umm... nope... quite the opposite... I ended up with "Failed to start X server".

Anyway, I just had a hands-on crash-course in how to operate in the command line only! :)

 I restored the old xorg.conf and saved the Xorg.0.log:

```
X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux SEANSLAPTOP 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Dec 10 01:01:25 2007
(==) Using config file: "/etc/X11/xorg.conf"
Data incomplete in file /etc/X11/xorg.conf
	Undefined Device "Generic Video Card" referenced by Screen "Default Screen".
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal server error:
no screens found
(WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
(WW) xf86CloseConsole: VT_GETMODE failed: Bad file descriptor
(WW) xf86OpenConsole: VT_GETSTATE failed: Bad file descriptor
```

What now? (and I may not respond for a while).

---

### Post by walkerk on 2007-12-09
I think I see the problem.. The Screen was still calling for the "Generic Video Controller" ... Try this...

You should have already backed up your xorg.conf but if not:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.back
```

You know how to restore if it fails :)

Now replace this bit of your xorg.conf:
```

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

with this:
```

Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
EndSection
```

Let me know :)


Also, my Monitor settings are:
```

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

```

Not sure what size monitor you have...

---

### Post by seanfitz64 on 2007-12-09
> **walkerk said:**
> 

Let me know :)

.

X server rebooted successfully, but I don't think it's made a difference. It's hard to say because I'm tired and I've been staring at the screen for hours. And I've forgotten what it was like before. The only way I can be sure it's changed is if I try the old xorg.conf again for comparison.

One thing I do notice is different is that I now have multiple refresh rates to choose from, whereas I only had one before (i.e. no choice). How do I know which one is the best?

> 
Not sure what size monitor you have...

My screen is only 12", that's why my maximum/native resolution is only 1024x768. Are you suggesting I change my HorizSync and VertRefresh rates?

I'm not sure what we are trying to achieve here. What do you think is happening? Can you explain it to me? I still don't understand why the upgrade caused the screen to display differently, even though the xorg.conf settings stayed the same.

I'm tired and it's very late here. I will have to tackle this again tomorrow. Thanks.

---

### Post by walkerk on 2007-12-09
Don't change your monitor settings.. I wasn't sure how big you screen was. The higher the refresh rate the better.

Is 1024x768 an option when you try to change your display using the GUI? Double check to ensure you are not using a widescreen resolution.

As far as why the resolution was messed up all I can tell you is I had a similar problem. I had to mess with my settings a bunch when I upgraded... Similar situation.. used xserver-xorg-video-intel in Feisty w/out issues, but it was messed up by default in Gutsy..

After messing around a bit I got it to work correctly... I'll check back tomorrow to help you out...

---

### Post by seanfitz64 on 2007-12-09
> **walkerk said:**
> 

Is 1024x768 an option when you try to change your display using the GUI? Double check to ensure you are not using a widescreen resolution..

Yes... and I've been using the maximum resolution -  1024x768 - all along.

With fresh eyes I can see the problem is still there unfortunately.

So where to next?

---

### Post by seanfitz64 on 2007-12-15
Well, 5 days have passed and I still have the problem.

Despite **walkerk**'s assistance, which I much appreciate, I am still none the wiser about what is going on, other than it's a problem that involves choice of graphics driver and my settings in xorg.conf. 

I tried doing some more research, but couldn't find anything helpful.

Can anyone else help, or do I have to go back to Feisty?

---

### Post by nunnst on 2007-12-15
Your problem is most likely NOT your video hardware or drivers.  It antiliasing of your fonts.  Search the forums with "Fonts" and u find a solution.

---

### Post by seanfitz64 on 2007-12-15
> **nunnst said:**
> Your problem is most likely NOT your video hardware or drivers.  It antiliasing of your fonts.  Search the forums with "Fonts" and u find a solution.

Thanks **nunnst**. I had been down the fonts and antialiasing path and played with font settings in Preferences > Appearance > Fonts. I made sure that Smoothing and Hinting in Font Rendering were set to Subpixel (LCDs) and Full respectively. This doesn't solve the problem.

This doesn't explain why this problem occurred when I upgraded from Feisty to Gutsy either. The settings were the same as before.

Can you point me in the direction of a specific solution you had in mind?

---

### Post by seanfitz64 on 2007-12-18
Bump.

I'm still having the problems and hoping someone will be able to offer some other suggestions.

---

### Post by TheBoz on 2007-12-19
Bump.

I know... old thread.

May not be the same thing, but coming from XP to Gutsy for my full-time OS, this is the very first thing I've noticed. Nothing is as sharp as it is in XP. I know it's not my hardware and I too have futzed with the font appearance settings to no end. Mine: Nvidia 7600GT

Is anyone else experiencing fuzzy / blurry screens?

---

### Post by macogw on 2007-12-19
I find that setting the anti-aliasing to LCD makes it *more* blurry, not less.  Try "Best Contrast"

---

### Post by TheBoz on 2007-12-19
See. And all I had to do was keep futzing with it until I found something that works.

My impression was that all LCD monitors buzz at about 60Hz, or at least that's what I've been told. So I found it odd that the "Screen and Graphics Preferences" applet actually offered me other freqs. Windows doesn't and that's where I'm coming from. For some reason Gutsy defaults (on my Dell 1704 anyway) to 50Hz. Might have been a long shot, but I changed the freq to 63 and everything is as sharp as I can stand it.

I'm stoked. Thought I was gonna have to give up my first foray into the ya'lls world of X.

Thanks macogw. It was the refresh.

---

### Post by seanfitz64 on 2007-12-20
I don't what's happened, but it seems OK now. 

I ran 'sudo dpkg-reconfigure -phigh xserver-xorg' which allows you to reset xorg.conf with minimal settings and things seemed to have come right. I say 'seemed', because I am not sure -  it may be that I've gotten used to it.... I dunno. But at least the screen isn't bothering me anymore.

I'm not going to mark this thread as solved, as I never really got around to understanding what was going on. 

Thanks for everyone's help.

---

### Post by seanfitz64 on 2008-01-08
Well, I'm back from holidays and with fresh eyes I see that the problem of blurry and fuzzy text surrounded by colours is still there after all. And it's annoying.

So where to now? I've tried everything suggested to no avail.

Do I just give up on Ubuntu and go back to Windows where I know things work?

---

### Post by Minguo on 2008-02-17
I have this problem with Gutsy as well.

It comes and goes and is driving me crazy.   Somedays everything is fine, and then one day blurry like a bad eyetest with ghost shapes behind fonts.

I fiddle with appearances and refresh rates until I can stand to look at the screen, but still don't know what the problem is or how to fix it.

---

### Post by seanfitz64 on 2008-02-17
It comes and goes for me too Minguo. I've just become resigned to it and put up with it. 

One day I will re-install Ubuntu and do a fresh install and see if that works, as I suspect part of the problem comes from upgrading from Feisty to Gutsy under Studio.

Until then I'm just accepting it as an unfortunate fact of life! :(

---

