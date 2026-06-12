---
title: "Installation problems on G4 eMac"
date: 2006-10-24
forum: Apple PPC Users
---

### Post by Tzustrategy on 2006-10-24
Hello everyone. I searched the forums for a thread that might address my specific problem, but unfortunatly I couldn't find one. 

I'm using a PowerPC eMac. The specs are as follows:

 Machine Model:	eMac
  CPU Type:	PowerPC G4  (2.1)
  Number Of CPUs:	1
  CPU Speed:	700 MHz
  L2 Cache (per CPU):	256 KB
  Memory:	640 MB
  Bus Speed:	100 MHz
  Boot ROM Version:	4.4.2f1

I downloaded the PPC Drake .iso file, and burned it as an image to a CD. I insert the CD into the drive and restart my machine and hold the "C" key down to boot from the disk. The computer makes the normal OSX starting chime, then the screen switches from white to black and back to white again. Then, it goes to a black DOS which tells me I can press "Enter" to start the process. It also says I can press "tab" to see more starting options. I've tried every single option they've listed, and the results are always the same: It goes to a miscolored splash of the Ubuntu logo and begins scrolling different checks it says it is doing (Loading Essential Drivers...OK). There is also a blue/red progress bar that is supposed to show where the process stands. After the checks are complete, the screen blacks out again, and there is a 20 second pause while my CD drive starts spinning very quickly. The computer plays a chime, and then sits with a black screen for another solid minute. Afterwards, the CD drive stops spinning, and the computer sits there frozen. I've tried different install disks, and the results are the same. 

Any suggestions? Thanks in advance!

---

### Post by bodek on 2006-10-24
Hi,
If I remember I've seen similar problem on my computer. Just check the link and try if you can find a solution. It seems that the Xserver is not configured properly.

[http://www.ubuntuforums.org/showthread.php?t=246129&page=2]("http://www.ubuntuforums.org/showthread.php?t=246129&page=2")

Hope it will help,
bdk

---

### Post by Tzustrategy on 2006-10-24
So you think my problem stems from not having my computer display the installer properly? If so, where should I enter those commands? Thanks!

EDIT: It's not taking me to a desktop at all, by the way. It doesn't even ask for me to select a language. It just freezes after the chime.

---

### Post by bodek on 2006-10-25
When the computer boots to the black screen, press control+option+F2 and see if this will take you to the console. If that works then you can use the link in the previous post to edit your xorg.conf file.

---

### Post by Tzustrategy on 2006-10-25
See post below! :D

---

### Post by Tzustrategy on 2006-10-25
Alright! I did press control+option+F2, and it brought me up to the command line. I changed the HorizSync and the VertRefresh like the other thread said, and I pressed control X, Y, then Return to save and exit. Once I was at the prompt, I entered "startx" and waited for magic to happen...but it didnt. ](*,) 

What I got instead was:
--------------------------

Fatal Server Error:
     Server is already active for display 0
          If this server is no longer running,
          remove /tmp/ .XO-lock and start again

Ubuntu@Ubuntu:~$

---------------------

"Whoa," I thought to myself, "What's going on?!" I thought it would probably be better to boot back into OSX, post about it, then make my next move. :mrgreen: 

So, what's next? :confused:

---

### Post by bodek on 2006-10-25
So, we are getting somewhere.
Now we have to 'kill' the xserver before we can restart it with new values.
Control+option+backspace should do it, after which you can start the new server with: sudo startx

Let's hope this time it will work.

---

### Post by linear on 2006-10-25
You can also do this, after setting up xorg.conf:

**sudo killall -HUP gdm**

---

### Post by Tzustrategy on 2006-10-25
Alright! Now we're getting somewhere! So I typed in "sudo killall -HUP gdm" and it booted to a black screen and played the chime again. However, this time it booted to a start up screen (orange/white) instead of just sitting there. Now here's the problem: The screen is so distorted I can't make anything out. Scratching my head, I pressed control+option+F2 and went back to the console, and typed "sudo killall -HUP gdm" in again. It booted to the black screen, played the chime, but then this time just stayed at a black screen. Arg! 

Any suggestions? Thanks a million in advance!

---

### Post by Tzustrategy on 2006-10-25
Any ideas?

---

### Post by bodek on 2006-10-26
Hi, I still think it is a problem with the xserver configuration, only can't now get a closer idea. 

Here I put my xorg.conf file, can compare with yours, might come up with something. For the time being forget the modes in the monitor section, don't put them there.

Also tell us what graphic card and monitor you have and if there are any errors you can get from the xserver (might be useful).

So here is my conf.
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"false"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. RV280 [Radeon 9200]"
	Driver		"ati"
	BusID		"PCI:0:16:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	71-73
	VertRefresh	70-140
	# 1024x768 @ 89 Hz hsync: 72.086 kHz; pclk: 99.190000 MHz
  	Modeline "1024x768_89.00"  99.190000  1024 1072 1168 1376  768 769 772 810 +hsync +vsync
	# 1280x960 @ 72 Hz hsync: 72.075 kHz; pclk: 122.240000 MHz
  	Modeline "1280x960_72.00" 122.240000  1280 1328 1424 1696  960 961 964 1002 +hsync +vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. RV280 [Radeon 9200]"
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
		Modes		"1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

Hope it will help.

---

### Post by mph66 on 2006-10-26
Hi,

I'm coming to you live and direct from Dapper installed on an eMac.  I went through your pain just two weeks ago.  Here's what I've discovered:

The refresh rate is VERY specific.  The horizontal refresh range needs to be set from 71-73.  Vertical needs to be 70-140.  If you set these values in xorg.conf, all will be well.  I tried other refresh rates and got the "acid kool aid" screen you're talking about.  Hope this helps.

-Marc

---

### Post by Tzustrategy on 2006-10-26
Yeah thanks a million! The refresh ranges you gave me moved us on to another step. Now it's saying that display :0 is being used and it asks if I want to use another display. When I hit Control+option+F7, i get a quick flash of a desktop, then it goes black again. Next step?

---

### Post by Tzustrategy on 2006-10-27
Any suggestions?

---

### Post by godard on 2006-10-27
This sounds like the classic dapper install problem on G4's, more here [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34508](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34508)

---

