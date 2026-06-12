---
title: "Dual Monitor set up with ATI AIW9600"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by XPuntu on 2006-12-12
After searching around everywhere I was about to give up setting up two monitors on my system. But by fluke, I think I've figured it out. So hopefully this will help others too.

I was looking at what packages I had installed with Synaptic because the fglrx-control app wasn't working for me. I uninstalled it and just happened to click on xorg-driver-fglrx (well right clicked on it because it was already installed on my system). Anyway, looking at the properties under "installed files" I saw a file listed in /usr/bin called aticonfig. Since I already backed up my xorg.conf file I figured I'd give it a shot.

The following command set everything up in the first go:

sudo aticonfig --initial=dual-head --screen-layout=horizontal

rebooted the computer and saw one screen black and the other my login. After logging in I saw identical desktops except the taskbars along the top and bottom were a little different. Moving my mouse from right to left, I could see I now had two screens! :mrgreen: 

Now I'm off to tinker a bit more so that my larger monitor is the default monitor.

Here's the important bits from my xorg file. Good luck!

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	Screen         "aticonfig-Screen[1]" LeftOf "aticonfig-Screen[0]"
	InputDevice    "Generic Keyboard"
	InputDevice    "Logitech MX1000" "CorePointer"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 AP [Radeon 9600]"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV350 AP [Radeon 9600]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]"
	Device     "aticonfig-Device[1]"
	Monitor    "aticonfig-Monitor[1]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

---

### Post by Angry on 2006-12-12
How unbelievably timely your post is (not to mention effective).  I had tried without success to set up my two monitors using the sticky 'how-to' about a month ago and decided to give it another try tonight.

Lo and behold, that simple command and a reboot later got me up and running.

The only (non)issue that I have is that I cannot move applications and windows between screens (well, I guess nautilus is an application...).  So, once I start an application in whatever screen "has focus", it stays there.  The only exceptions are files/folders, they can be transferable between screens.

By the way, I have an ATI X700.

---

### Post by bodhi.zazen on 2006-12-13
XPuntu: Nice how to on Dual Monitors.

I wrote one for nVidia cards but I do not ATI.

I added a link in my how-to to this page.

[Bodhi.zazen's how-to dual monitor](http://www.ubuntuforums.org/showthread.php?&p=1401091)

---

### Post by XPuntu on 2006-12-13
Angry,

That's the next step for me. I'm just glad to have the two screens for now and not a broken xorg!

Let you know if I'm successful. (Or you can let me know) 

Cheers!

PS. So now I've noticed I can't have two instances of Firefox unless they are on the same screen. Anyone know a quick fix for that?

---

### Post by bodhi.zazen on 2006-12-13
> **XPuntu said:**
> PS. So now I've noticed I can't have two instances of Firefox unless they are on the same screen. Anyone know a quick fix for that?

LOL

In the firefox menu:

File -> New window

---

### Post by pappabetalar on 2006-12-18
Thanks, finally got my other monitor working!  :)

EDIT:

hmm, weird problem i can't drag any windows to my other monitor, like FF or if i open a picture i can only view it on my first monitor.. :confused:

---

### Post by pappabetalar on 2006-12-18
maybe this will help?
Didn't help me. Anyway.. 

[http://hamzakc.wordpress.com/2006/10/16/dual-monitor-setup-ubuntu-ati/](http://hamzakc.wordpress.com/2006/10/16/dual-monitor-setup-ubuntu-ati/)

---

### Post by mrWoot on 2007-01-10
First of all, I've tried a lot of things.

**Some information about my system.**
[LIST]
[*]**One** video card.
[*]The card is a **ATI Radion 9600**.
[*]**Two** monitor. One 19" and one 17"
[/LIST]

**Problem:**
I get my cursor to go to the "other screen" but there IS NO other screen. My second monitor is cloned. I can't get it NOT to clone.

Here is my ***/etc/X11/xorg.conf***.

```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	Screen         "aticonfig-Screen[1]" RightOf "aticonfig-Screen[0]"
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 51.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 AP [Radeon 9600]"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV350 AP [Radeon 9600]"
	Monitor    "Generic Monitor"
	DefaultDepth     24

	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes     "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes     "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes     "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes     "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes     "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]"
	Device     "aticonfig-Device[1]"
	Monitor    "aticonfig-Monitor[1]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

```

[SIZE="4"]Please help. I've tried over 20 things (real number) and I've had NO luck.[/SIZE]

---

### Post by rbhigday on 2007-01-14
> **XPuntu said:**
> :

sudo aticonfig --initial=dual-head --screen-layout=horizontal


you the MAN!!!!!

glad you found this I am now on dual monitors!!!!

I think they should sticky this!!!!

---

### Post by rbhigday on 2007-01-14
> **pappabetalar said:**
> Thanks, finally got my other monitor working!  :)

EDIT:

hmm, weird problem i can't drag any windows to my other monitor, like FF or if i open a picture i can only view it on my first monitor.. :confused:

I had read somewhere that this was the case, not a perfect dual monitor but better than mirrored monitors

---

### Post by rbhigday on 2007-01-14
> **mrWoot said:**
> Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 AP [Radeon 9600]"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

try changing the driver from ati to vesa that is what mine says and I have dual monitor now thanks to this thread and not mirrored.

It the only difference I saw between yours and mine

---

### Post by oranges2 on 2007-01-16
How do I reverse this command? >_>

---

### Post by oranges2 on 2007-01-16
Bump >_>

---

### Post by rbhigday on 2007-01-16
> **oranges2 said:**
> How do I reverse this command? >_>

reverse what command?

---

### Post by oranges2 on 2007-01-17
> **rbhigday said:**
> reverse what command?

"sudo aticonfig --initial=dual-head --screen-layout=horizontal"

---

### Post by Twin Penguins on 2007-01-17
I would also like to know how to reverse this command. My xserver took a crap directly after I rebooted using it.](*,)

---

### Post by Twin Penguins on 2007-01-18
Not sure if this is the only way to reverse it.. but this is how I got mine working again.


sudo dpkg-reconfigure xserver-xorg

---

### Post by tjb_15 on 2007-03-03
It kind of worked for me but on one monitor the mouse changes to a box

---

### Post by WicKeDcHilD on 2007-04-06
Not sure if this will work for people who have two monitors with different reslutions but for me the guide did help me but i couldnt take one file and drag it to the other window. It got to the window barrier and didnt act like a dual 

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "ServerFlags"
	Option	    "AIGLX" "off"
EndSection

Section "Monitor"
	Identifier   "20WMGX2"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. ATI Default Card"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. ATI Default Card"
	Monitor    "20WMGX2"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "3360x1050" "1440x1440" "1280x800" "1024x768" "760x608" "720x400" "640x480" "248x198"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1680x1050" "1440x1440" "1280x800" "1024x768" "760x608" "720x400" "640x480" "248x198"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1680x1050" "1440x1440" "1280x800" "1024x768" "760x608" "720x400" "640x480" "248x198"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1680x1050" "1440x1440" "1280x800" "1024x768" "760x608" "720x400" "640x480" "248x198"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1680x1050" "1440x1440" "1280x800" "1024x768" "760x608" "720x400" "640x480" "248x198"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1680x1050" "1440x1440" "1280x800" "1024x768" "760x608" "720x400" "640x480" "248x198"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection

Now that my settings look like this instead of how the Op's settings look, my monitors act more like a Dual monitor setup with no barrier in between the two monitors. The only thing it does weird is that when i have say firefox opened on One window and try to open say Terminal it will open on the other window Lol, if i was to do the same thing using the other monitor the terminal now opens on the other monitor :confused: its like it knows the file is open and trying to make it so you can see the files better Lol. it sucks but now i can move files back and forth... The end :) hope it helps!

 Read the settings and you will see all i changed.

---

### Post by L!TH!UM on 2007-04-11
ok im a bit of a newb when it comes to linux... im using ubuntu ultimate 1.3..... i know jack all of commands...... im tryin to get my dual monitors up ... and get all the right drivers for my ATI radeon 9550 ... if anybody could help it would be awsome..... i startin to understand the linux world a bit better... if anyone could give me a bit of a step by step it would be most appreciated... thnx fer ya time

ok i got drivers install with envy...
but now i needa get the dualies running...... my basic goal is to have the ability to drag from one screen to another for more workspace area.... but to not have that effect my gamin.... im a major FPS gamer.... so i can have anything slowin it down or have the screen split down the middle
i wanna be able to have different resolutions on each screen also..
any help would be3 awsome oks i got the Big desktop working :)
now i just needa be able to control their resolutions individualy..

---

### Post by seth556 on 2007-04-23
Used this today. Works OK. I don't like the window barrier. 

Also is there anyway to have a different background on each screen? I hate looking at the same thing twice.

---

