---
title: "Dual screen on ati"
date: 2005-12-06
forum: Absolute Beginner Talk
---

### Post by REDISISTone.nl on 2005-12-06
Hello !!

Here is my problem...
I have 2 minitor's, I got a ATI Radeon 9600SE. My drivers are installed (ati) but I got 2 monitor's. Is there a way to get a extended desktop on them, and here come's the hard part...
one of them (main monitor) can handle 1280x1024 but the seccond is a flatscreen that can take only 1024x768.

Sum1 got an idea how I can make this work ?? or is it just not possible??

---

### Post by REDISISTone.nl on 2005-12-06
no one?

---

### Post by fireflymantis on 2005-12-13
I have managed to mostly hack together a working solution for this. It isn't perfect, as it isn't quite the 'extended desktop' way, but if you just want basic dual-monitor setup with different resolutions. (different contents on each screen too) I think this is about as good as it gets for the moment. 

(BTW. I am on a 9600XT)

in a terminal:
```
sudo gedit /etx/X11/xorg.conf
```

replace what you have in here with this, changing the screen resolutions as needed.

```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen "Primary Screen" 0 0
	Screen "Secondary Screen" LeftOf "Primary Screen"
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"

        # paths to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/CID"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load  "GLcore"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "v4l"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
EndSection

Section "Device"
Identifier "ATI0"
Driver "fglrx"
BusID "PCI:1:0:0"
Option "AGPMode" "4"
Option "BusType" "AGP"
Option "EnabledPageFlip" "on"
Option "DesktopSetup" "Horizontal"
Option "MonitorLayout" "CRT, CRT"
Option "MergedFB" "true"
Option "HSync2" "30-95"
Option "VRefresh2" "50-120"
Option "Position2" "RightOf"
Option "NoMergedXinerama" "false"
Option "MetaModes" "1280x1024-1152x864"
Option "UseFastTLS" "0"
Option "BlockSignalOnLock" "on"
Option "UseInternalAGPGART" "no"
Option "ForceGenericCPU" "no"
Option "KernelModuleParm" "agplock=0"
Option "EnablePrivateBackZ" "yes"
Option "Capabilities" "0x00008000"
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
Option "IgnoreEDID" "off"
Option "NoTV" "yes"
Option "no_accel" "no"
Option "no_dri" "no"
Option "mtrr" "off"
Screen 0
EndSection

Section "Device"
Identifier "ATI1"
Driver "fglrx"
BusID "PCI:1:0:0"
Screen 1
EndSection

Section "Monitor"
Identifier "ViewSonic G790"
Option "DPMS"
HorizSync 30-97
VertRefresh 50-120
EndSection

Section "Monitor"
 Identifier "Sceptre P98V"
 Option "DPMS"
 HorizSync 30-95
 VertRefresh 50-75
EndSection

Section "Screen"
Identifier "Primary Screen"
Device "ATI0"
Monitor "ViewSonic G790"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
Viewport 3200 1200
EndSubSection
EndSection

Section " Screen"
 Identifier "Secondary Screen"
 Device "ATI1"
 Monitor "Sceptre P98V"
 DefaultDepth 24
 Subsection "Display"
 Depth 1
 Modes "1152x864" "1024x768" "800x600" "640x480"
 EndSubSection
 SubSection "Display"
 Depth 4
 Modes "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
 Depth 8
 Modes "1152x864" "1024x768" "800x600" "640x480"
 EndSubSection
 SubSection "Display"
 Depth 15
 Modes "1152x864" "1024x768" "800x600" "640x480"
 EndSubSection
 SubSection "Display"
 Depth 16
 Modes "1152x864" "1024x768" "800x600" "640x480"
 EndSubSection
 SubSection "Display"
 Depth 24
 Modes "1152x864" "1024x768" "800x600" "640x480"
 Viewport 3200 1200
 EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

```

If anyone out there has a solution to allow for the 'extended desktop' way, I would be most appreciative.


    --Martin

---

### Post by Darksun on 2005-12-13
Following that method causes mass crashing

---

### Post by fireflymantis on 2005-12-13
Make sure that the 'latest' fglrx drivers are installed

You probably want to be using the fglrx drivers instead of the xorg ati ones.

I am running off the latest fglrx drivers (not in the breezy repos)
A good howto to get these drivers up and running is [here]("http://ubuntuforums.org/showpost.php?p=423584").

Also, you may need to change what modules are loaded. e.g. not everyone needs the v4l module in there.

  --Martin

---

### Post by REDISISTone.nl on 2005-12-14
Thanx its not as easy as expacted but got it up and running now. Thanx m8, have a nice day :D

---

