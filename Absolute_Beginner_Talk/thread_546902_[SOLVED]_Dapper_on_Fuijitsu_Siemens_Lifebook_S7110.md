---
title: "[SOLVED] Dapper on Fuijitsu Siemens Lifebook S7110 upgrade from default drivers"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by RockyRoads on 2007-09-09
Hello - as stated in the title I'm looking for help upgrading from the default drivers that were installed with kubuntu - dapper.

I just started using ubuntu it's my first foray into the linux world and I love it :cool:
Just to be clear on my user level I can run commands from the terminal and use apt from the terminal or gui but that's about it...so any help will be greatly appreciated.

My hardware is as follows:
Graphics - Mobile Intel 945GM Express Chipset Family - currently using the i810 driver but I've read posts that say the intel driver is better only I can't find it in adept even with the backports, universe and multiverse repositories enabled.
Sound - Realtek HD Audio 
Atheros AR5006EG Wireless Network Adapter
Marvell Yukon 88E8055 PCI-E Gigabit Ethernet Controller

Here's a screen dump of my xorg.conf file
```
cat /etc/X11/xorg.conf | less
```

 [INDENT]Section "Files"
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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
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
	Identifier	"Intel Corporation Mobile Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
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
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
[/INDENT]

Theres doesn't seem to be any listing for the wired or wireless card, (I know the wired works I'm using it now). The soundcard doesn't seem to be listed either.

If anyone can offer any advice or point me in the right direction on installing the appropriate drivers I greatly appreciate the help.

---

### Post by overdrank on 2007-09-09
HI this is the thread i used to install the 
Atheros AR5006EG Wireless Network Adapter
[http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)
If you would like to try the 915 resolution fix you can find it here But** BACK UP** your xorg first
[http://roland-lopez.blogspot.com/2007/03/auto915resolution-ubuntu-resolution-fix.html](http://roland-lopez.blogspot.com/2007/03/auto915resolution-ubuntu-resolution-fix.html)
And you can always use the command 
```
lspci
```
In the terminal located under applications, accessories, Terminal to verify you hardware on the system. Good luck!

---

### Post by RockyRoads on 2007-09-09
Thanks for the quick reply...I'll check those out know! :)

---

### Post by RockyRoads on 2007-09-09
> **overdrank said:**
> HI this is the thread i used to install the 
Atheros AR5006EG Wireless Network Adapter
[http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)

Thanks overdrank my wireless works like a charm now!!!

Just a quick not for anyone else using the above link to install Atheros wireless card at the very end of the install my system hung on the reboot at the loading essential drivers section, just switched off and back on again and I'm wireless now :)

Trying the resolution fix you suggested now...

---

### Post by RockyRoads on 2007-09-09
Tried the 915 resolution fix but unforetunately the link to the file on Rolands page [http://roland-lopez.blogspot.com/2007/03/auto915resolution-ubuntu-resolution-fix.html]("http://roland-lopez.blogspot.com/2007/03/auto915resolution-ubuntu-resolution-fix.html") is dead. Looked like a great fix.
I installed the 915resolution using apt apt and am happy enough.

If anyone has the xorg...intel driver or knows where you get it please let me know as I'm doing my fourth year project at the moment which uses digital photogrammetry which is highly dependent on my graphics being as good as they can be.

Anyone any suggestions on how to install the Realtek HD Audio Driver?

Thanks

---

### Post by overdrank on 2007-09-09
> **RockyRoads said:**
> Tried the 915 resolution fix but unforetunately the link to the file on Rolands page [http://roland-lopez.blogspot.com/2007/03/auto915resolution-ubuntu-resolution-fix.html]("http://roland-lopez.blogspot.com/2007/03/auto915resolution-ubuntu-resolution-fix.html") is dead. Looked like a great fix.
I installed the 915resolution using apt apt and am happy enough.

If anyone has the xorg...intel driver or knows where you get it please let me know as I'm doing my fourth year project at the moment which uses digital photogrammetry which is highly dependent on my graphics being as good as they can be.

Anyone any suggestions on how to install the Realtek HD Audio Driver?

Thanks

Hi you could start here
[http://ubuntuforums.org/showthread.php?t=205449&highlight=Realtek+HD+Audio](http://ubuntuforums.org/showthread.php?t=205449&highlight=Realtek+HD+Audio)

---

### Post by RockyRoads on 2007-09-12
A few quick updates:
Have changed from dapper to edgy :)

> HI this is the thread i used to install the 
 Atheros AR5006EG Wireless Network Adapter
 [http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)

The wireless install suggested above did work initially in dapper but after I shut the laptop down it stopped working. Two possible reasons for this the driver was actually for the AR5007 not AR5006 but I didn't notice this until after it stopped working properly and the guide was for Feisty.

So I looked around and found a nice script that installed madwifi and sets everything up on stchman's website [http://www.stchman.com/ath_drv.html]("http://www.stchman.com/ath_drv.html")
Wireless works even after I shutdown now...do have to wait a few minutes before I can successfully connect to anything but I'll live!
It's nice and easy to use and very well explained if you want to do it manually.

overdrank thanks for the help with this I was feeling pretty lost until you pointed me in the right direction, also getting a lot more comfortable installing and removing various things using the terminal and having fun while I'm at it :)

Next on my list: 
 upgrade from the i810 with the 915 resolution tool? to the intel driver :confused:

---

### Post by RockyRoads on 2007-09-25
It's been a while since I started this post and I've since upgraded to fiesty where everything works out of the box wireless included.

So I've no longer any need for this and no one else seems to either so thanks to those who helped with driver installs and all the rest.

With fiesty the problems raised above have been solved so cheers :-)

---

