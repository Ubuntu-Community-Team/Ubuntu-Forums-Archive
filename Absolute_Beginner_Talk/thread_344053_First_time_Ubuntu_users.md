---
title: "First time Ubuntu users"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by XstatyK on 2007-01-22
If you love Ubuntu but miss playing a 3d game or two then this is definitely worth a peek.  It's a cool 3d game I just found out about and thought I would share.  Package name is tremulous

sudo apt-get install tremulous 

Screenshots can be viewed [HERE]("http://tremulous.net/").

---

### Post by gh0st on 2007-01-22
Thanks for the tip I might install this, I'm not a big PC gamer I'm more of console guy but I wanna make my 3D card do something other than Beryl and Google Earth :D

---

### Post by neoflight on 2007-01-22
awesome...i will check that out...thanks for the link

---

### Post by Carlton1 on 2007-01-22
I've downloaded the game, but when I click on the icon, the screen just goes blank for a second, and nothing else happens.

Any suggestions?

Thanks,

Carlton

---

### Post by pizzutz on 2007-01-22
Sounds like missing/wrong vid card drivers.  What type of hardware do you have?  Which drivers do you have installed?  A post of your /ect/X11/xorg.conf file may help too.

---

### Post by lyceum on 2007-01-22
looks cool. I am finding more free games out there. Now I just need to find time to check them all out. :)

---

### Post by XstatyK on 2007-01-22
> **Carlton1 said:**
> I've downloaded the game, but when I click on the icon, the screen just goes blank for a second, and nothing else happens.

Any suggestions?

Thanks,

Carlton

If you have a Nvidia video card this might be of some help to get the right drivers installed.

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by ljpm on 2007-01-22
I can't seem to install it.

```
sudo apt-get install tremulous
```

and get 

```

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package tremulous

```

I am running Dapper. The only things I have done since fresh install is update, install automatix and video drivers (ati Xpress 200 on board).  I have also enabled all repositories with Package Manager.

Is there another repository that I need to enable or add?

---

### Post by XstatyK on 2007-01-23
I'm using Edgy and it is in the repositories by default but here is a way you can  get it in Dapper.

Method 1  You could get it from the Edgy repository [HERE]("http://archive.ubuntu.com/ubuntu/pool/multiverse/t/tremulous-data/")



Cheers!

---

### Post by davidvasta on 2007-01-23
Nice link. I am getting it now. I am in love with Ubuntu. After 11 years of really bad Linux this is nice. I can't wait for 7 to be out.

---

### Post by carverj on 2007-01-23
> After 11 years of really bad Linux this is nice. I can't wait for 7 to be out.

really bad Linux? I didn't know there was such a thing!  Taken a while to find the right OS huh?

---

### Post by irish_flu on 2007-01-23
Thanks, I'm downloading it as we speak.

---

### Post by XstatyK on 2007-01-23
I would suggest taking a look at the promo video on the front [page]("http://prdownloads.sourceforge.net/tremulous/tremulous-promo-II.avi?download") as it gives you an idea of the different maps, characters, and gameplay.  Also I took a quick 5 minutes to read through the one-page manual to understand the fundamentals of the gameplay because weapons upgrades sure help a lot.:biggrin:

---

### Post by ljpm on 2007-01-23
Thanks XstatyK,

I'll give it a try when I get home.

---

### Post by enopepsoo on 2007-01-23
It is not in Dapper.  That is a shame because the screenshots looked nice.=D>

---

### Post by carverj on 2007-01-23
I didn't see any system requirements on their site?
Do you think I would get away with ATI Radeon 64MB video and only 256 MB RAM?

---

### Post by XstatyK on 2007-01-23
> **enopepsoo said:**
> It is not in Dapper.  That is a shame because the screenshots looked nice.=D>

I didn't know about that until yesterday so here is the way to get it working. (taken from page 1)
> **XstatyK said:**
> I'm using Edgy and it is in the repositories by default but here are different ways you can  get it in Dapper.

Method 1  You could get it from the Edgy repository [HERE]("http://archive.ubuntu.com/ubuntu/pool/multiverse/t/tremulous-data/")

Method 2  Use the binaries some one generously backported to Dapper [HERE]("http://www.madman2k.net/comments/46/")

Method 3  Add the repository to your sources.list file  Instructions found [HERE]("http://www.glug-nith.org/archives/20060919-1330-Tremulous-Arjun.html")

Cheers!

There you go, have fun!

---

### Post by XstatyK on 2007-01-23
> **carverj said:**
> I didn't see any system requirements on their site?
Do you think I would get away with ATI Radeon 64MB video and only 256 MB RAM?

Here is what [wikipedia]("http://en.wikipedia.org/wiki/Tremulous") has the system requirements set as

System Requirements
800 MHz x86 CPU
256 MB RAM
32 MB nVIDIA GeForce2 or ATi Radeon 7000
Stereo sound card
125 MB free hard drive space
56 kbit/s Internet connection

So I think you'll be good on running it.=D>

---

### Post by Snoochi on 2007-01-23
> **XstatyK said:**
> I'm using Edgy and it is in the repositories by default but here are different ways you can  get it in Dapper.

Method 1  You could get it from the Edgy repository [HERE]("http://archive.ubuntu.com/ubuntu/pool/multiverse/t/tremulous-data/")

Method 2  Use the binaries some one generously backported to Dapper [HERE]("http://www.madman2k.net/comments/46/")

Method 3  Add the repository to your sources.list file  Instructions found [HERE]("http://www.glug-nith.org/archives/20060919-1330-Tremulous-Arjun.html")

Cheers!
this may be a dumb question but how do you know which repository file to use , i think im right in saying its the .deb id use for ubuntu  but do i need both as there are 2

---

### Post by jvc26 on 2007-01-23
> **carverj said:**
> really bad Linux? I didn't know there was such a thing!  Taken a while to find the right OS huh?

I think he's talking about the usability of many Linux based OSs over the years - more recently they really have taken a big turn for the better in terms of ease of use and adaption to.
Il

---

### Post by voltare on 2007-01-23
I myself was full windows-only user until yesterday. Now, i'm an ubuntu user exclusively, after studying  which distro was best for me.I got tired of fighting viruses, worms, etc.I'm now installing nvidia drivers, after finding the right way to do it, heh.It just takes a bit of getting used to, for me it's not that hard.Just takes a bit of exploring and clicking on things to see what they do.

I'm also a World of Warcraft nut, and a hopefull indie game maker.I'll be downloading WinE soon, just for WoW, as everything else I need has an equivalent here.(Milkshape3d-----Blender&Wings3d, Beyond Virtual ---Crystal Space, Reality Factory's RFeditpro ----gtkradiant , Paint.net & pixia ----The gimp and all its derivatives.)


Don't feel as if you've lost something, look at it as replacing things.

I've even found 3d games, just using the add/remove button.( Arkhart , Ldoom , WorldForge).


Amazing. Even the browser seems faster than Opera or firefox was on windows.


Very stable OS, and even seems faster than windows.

Just stick with it, I am.


edit: Just now found out that my cd writer that i could not get to work in windows, works now......weird.......but cool!

---

### Post by XstatyK on 2007-01-23
> **Snoochi said:**
> this may be a dumb question but how do you know which repository file to use , i think im right in saying its the .deb id use for ubuntu  but do i need both as there are 2

I think you're referring to the first method, if so the two you are seeing is that one is a slightly newer version (probably bug fixes) than the other one.  The older verson says tremulous-data 1.1.0-1 and the newer one is 1.1.0-2  Both file sizes are 96 MB so it seems that not too many changes were made to it.

I would go with the latest version.
[http://archive.ubuntu.com/ubuntu/pool/multiverse/t/tremulous-data/tremulous-data_1.1.0-2_all.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/t/tremulous-data/tremulous-data_1.1.0-2_all.deb)

---

### Post by carverj on 2007-01-23
> I myself was full windows-only user until yesterday. Now, i'm an ubuntu user exclusively, after studying which distro was best for me.I got tired of fighting viruses, worms, etc.I'm now installing nvidia drivers, after finding the right way to do it, heh.It just takes a bit of getting used to, for me it's not that hard.Just takes a bit of exploring and clicking on things to see what they do.


sounds familiar. The reason I learned to use GNU/Linux in the first place was to avoid the constant critical virus attacks in Windows. I love how you have a variety of choices in this world, not to mention these forums and community spirit!!
I believe it works out of the box AND continues to work as you can help yourself !

---

### Post by XstatyK on 2007-01-24
Has anybody else seen any games that have graphics as good as tremulous or does anyone else know of some good 3d games??

Ok just found out about this other one called Nexuiz and it looks nice.  Check it out here [http://www.alientrap.org/nexuiz/index.php?module=media](http://www.alientrap.org/nexuiz/index.php?module=media)

---

### Post by mikerduffy on 2007-01-28
> **Carlton1 said:**
> I've downloaded the game, but when I click on the icon, the screen just goes blank for a second, and nothing else happens.

Any suggestions?

Thanks,

Carlton

I'm having the same problem.  I click on tremulous in the applications menu, a black window opens, goes full-screen, then disappears.  Here's what happens when I go to look at my xorg.conf

```
mike@mike-laptop:~$ emacs /etc/X11/xorg.conf
Fatal error (11).Segmentation fault
mike@mike-laptop:~$ kate /etc/X11/xorg.conf
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
```???

And here is my actual xorg.conf
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
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
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
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
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
	Option		"SHMConfig"		"on"
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
	Identifier	"ATI RADEON MOBILITY 9600"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Samsung LTN154X1"
	Option		"DPMS"
	HorizSync	31.5-48.5
	VertRefresh	40-70
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI RADEON MOBILITY 9600"
	Monitor		"Samsung LTN154X1"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1024x768" "800x600" "640x480"
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

```

I am running kubuntu 6.10 on an amd64.

**EDIT:** Someone elsewhere pointed me toward this:

```
mike@mike-laptop:~$ glxinfo|grep direct
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect
```

**EDIT2: ** Found a solution here:

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

---

