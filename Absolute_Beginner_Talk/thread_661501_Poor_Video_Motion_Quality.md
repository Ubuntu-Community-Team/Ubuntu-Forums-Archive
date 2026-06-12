---
title: "Poor Video Motion Quality"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by imaginal on 2008-01-08
I have a dual-boot hp dv2550se laptop, Vista and Gusty.

I can watch dvds in vista, and the output quality is perfect.
I can watch dvds in gusty, but there are subtle lines (refresh?) and blocky sections when things move rapidly. Something isn't quite what it should be...

```
lspci
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
```

I can't view movies fullscreen. It hurts. What am I missing?

---

### Post by kpkeerthi on 2008-01-08
Do you have compiz (desktop effects) enabled? What player are you using?

---

### Post by imaginal on 2008-01-08
I currently have compiz running, as well as xserver-xgl... but the problem is still quite noticeable when I run metacity and uninstall xgl.

---

### Post by peabody on 2008-01-08
I would guess that you might be watching a DVD with interlaced video and don't have deinterlacing turned on in whatever program you're using to watch DVDs in Linux

In VLC you can turn interlacing on in Settings -> Preferences...-> Video -> Filters.

My $0.02 anyway.

---

### Post by imaginal on 2008-01-08
I do have deinterlacing turned on in my primary viewer, gxine. It is not just with dvds. It is with anything that moves quickly on my screen. Including, but not limited to: compiz, screensavers, dvds, avis, flash video, scrolling images in firefox...

---

### Post by peabody on 2008-01-08
What video card do you have?

---

### Post by imaginal on 2008-01-08
The best I can tell, it is an integrated Intel card. That is what I could find through lspci, anyway. It is working, but not quite what it should be at.

---

### Post by peabody on 2008-01-08
Why don't you post the output of lspci here and let us help?  I have an integrated intel i950 (945GM chipset) working with the xserver-xorg-video-intel driver and the video playback is smooth as silk on this machine.

---

### Post by imaginal on 2008-01-08
Silky smoothness is what I'm looking for. ;)

```
travis@travis-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

```

---

### Post by peabody on 2008-01-08
There's the magic:

```
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
```

965GM chipset, now, could you post the output of your /etc/X11/xorg.conf file so we can determine what video driver you're using.

---

### Post by imaginal on 2008-01-08
Just the contents of the file?

```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
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
	Option		"HorizEdgeScroll"	"0"
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
	Identifier	"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection
```

---

### Post by peabody on 2008-01-08
Everything seems to check out there.

At this point it's time to test the output settings of your video players.  The effect you describe sounds like sheering, are you using opengl output or xv?

---

### Post by imaginal on 2008-01-08
Sheering sounds accurate, but remember, I get the effect when anything moves on my screen, including windows. For example, if I grab the terminal window in metacity (or compiz) and quickly draw a circle with it, I can see multiple iterations of the same window.

I don't know whether my video uses opengl or xv though. My bet is xv? Thanks again for your patience!

---

### Post by imaginal on 2008-01-08
Also potentially helpful, metacity run in terminal gives this error frequently...
```
Window manager warning: Log level 8: gtk_paint_arrow: assertion `style->depth == gdk_drawable_get_depth (window)' failed

```

---

### Post by peabody on 2008-01-08
In vlc it should be under Settings -> Preferences...-> Video -> Output modules.  Click the advanced options check box and a video output module selection should appear.  Select XVideo and see if anything changes.  Try others as well, like OpenGL.

---

### Post by imaginal on 2008-01-08
I will continue to tinker. Thanks again for all of your help! ^_^

---

### Post by ammazza on 2008-01-14
Hi, I have the same problems in watching videos of any kind on my notebook: Toshiba Satellite A200-1GD, which uses Intel GM965.

I am really busy at the moment and I just abandoned the topic, but I have intention to solve it. One of my guesses was an incorrect reading of the EDID of the LCD monitor. Could you please try this command:

```

sudo get-edid |parse-edid

```

and post the result? You might need to install the edid utilities...
Thanks.

---

### Post by wheezer on 2008-01-16
> **peabody said:**
> In vlc it should be under Settings -> Preferences...-> Video -> Output modules.  Click the advanced options check box and a video output module selection should appear.  Select XVideo and see if anything changes.  Try others as well, like OpenGL.



Ok... X11 works, but OpenGL results in the player closing the minute it opens

BUt overall, the quality is better.  Nowhere near as good as Windows Media player on my XP machine though. That really upsets me.  Does all Linux video suck, or just video on my ATI X1600 card?

PS
What do I do if I try another output, and the VLC won't open again? Is there a way I can reset back to X11 so I can at least open the app again, using Terminal?

---

### Post by wheezer on 2008-01-16
THis is so frustrating.,


Now i have VLC working "fairly" well, but Totem looks horrible.  I use totem for things needing playlists, and it looks just horrible.  It doesn't seem to have many video out modules like VLC.

So how to do I improve its qualty?

---

### Post by imaginal on 2008-01-16
> **ammazza said:**
> Could you please try this command:

```

sudo get-edid |parse-edid

```

and post the result? You might need to install the edid utilities...
Thanks.

```
travis@travis-laptop:~$ sudo get-edid |parse-edid
parse-edid: parse-edid version 1.4.1
get-edid: get-edid version 1.4.1

        Performing real mode VBE call
        Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
        Function supported
        Call successful

        VBE version 300
        VBE string at 0x11110 "Intel(r)Crestline Graphics Chip Accelerated VGA BIOS"

VBE/DDC service about to be called
        Report DDC capabilities

        Performing real mode VBE call
        Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
        Function supported
        Call successful

        Monitor and video card combination does not support DDC1 transfers
        Monitor and video card combination supports DDC2 transfers
        0 seconds per 128 byte EDID block transfer
        Screen is not blanked during DDC transfer

Reading next EDID block

VBE/DDC service about to be called
        Read EDID

        Performing real mode VBE call
        Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
        Function supported
        Call successful

parse-edid: EDID checksum passed.

        # EDID version 1 revision 3
Section "Monitor"
        # Block type: 2:0 3:f
        # Block type: 2:0 3:fe
        # Block type: 2:0 3:fe
        Identifier "AUO:4444"
        VendorName "AUO"
        ModelName "AUO:4444"
        # Block type: 2:0 3:f
        # Block type: 2:0 3:fe
        # Block type: 2:0 3:fe
        # DPMS capabilities: Active off:no  Suspend:no  Standby:no

        Mode    "1280x800"      # vfreq 60.005Hz, hfreq 49.324kHz
                DotClock        69.300000
                HTimings        1280 1328 1360 1405
                VTimings        800 803 809 822
                Flags   "-HSync" "-VSync"
        EndMode
        # Block type: 2:0 3:f
        # Block type: 2:0 3:fe
        # Block type: 2:0 3:fe
EndSection

```

Hopefully this helps!

---

### Post by imaginal on 2008-01-27
A Bump and Update:

The same HD NASA JPL video downloaded and played in Miro on Vista and Ubuntu 7.10 are noticeably different. Linux isn't as good.

I've spent a lot of time trying to figure out what isn't right. In some spots of video motion, you can briefly see the horizontal refresh line on the screen. i.e. the top half of the video is a split-second faster than the bottom.

This isn't a video player problem. Does anyone have any ideas? This is confusing me...

---

### Post by peabody on 2008-01-27
Out of curiosity, what's your resolution.

---

### Post by imaginal on 2008-01-28
Resolution: 1280x80
Refresh rate: 60hz

This is the resolution the monitor was built for, and uses in vista.

---

### Post by Che.SSL on 2008-03-07
I have exactly the same problem running on a nVidia 8400GS.
Everything which moves quickly on a horizontal direction is showing huge distortion effects! Messing aroung with this prob for weeks now, no solution found yet.

[Screenshot]("http://img212.imageshack.us/my.php?image=screenshotcp1.png")

---

### Post by sloggerkhan on 2008-03-07
> **wheezer said:**
> Ok... X11 works, but OpenGL results in the player closing the minute it opens

BUt overall, the quality is better.  Nowhere near as good as Windows Media player on my XP machine though. That really upsets me.  Does all Linux video suck, or just video on my ATI X1600 card?

PS
What do I do if I try another output, and the VLC won't open again? Is there a way I can reset back to X11 so I can at least open the app again, using Terminal?

Just for reference, since you have an ATI card, these problems were caused be the older fglrx driver. They are nearly gone with 8.03 fglrx release. I suggest you give it a try. On my x700 mobility, the video playback was amazing with that driver, especially the open gl playback. Not sure how it is with compiz, though. Usually you have to use xv/x11 overlay with compiz on fglrx, and IMO they're pretty good, but slightly worse than opengl's quality with the newer ati drivers. Of course the opengl overlay also has much much more cpu load.

Don't know what to say to those of you with the older intel integrated.

---

