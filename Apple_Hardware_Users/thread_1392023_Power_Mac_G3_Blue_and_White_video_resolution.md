---
title: "Power Mac G3 Blue and White video resolution"
date: 2010-01-27
forum: Apple Hardware Users
---

### Post by UniverseA7X on 2010-01-27
Hi guys, haven't been around here in a while, seems that the other OS section is completely gone, so I assume this would be the most appropriate place to ask this, since Debian and Ubuntu are similar enough.

Okay, so I installed Debian Lenny on my Power Mac G3. 450MHz, 1GB RAM, and an ATI Rage128, the stock video card. It also has a Linksys WMP54G Wireless card which I got working effortlessly enough.

My issue is with the screen resolution. The driver for the graphics card is installed, but I'm only getting a 800x600 resolution. My Monitor is a 1440x900 screen, so everything's quite out of proportion. I assume I may have to go into xorg.conf to tweak things, but I wouldn't know what to tweak.

This is the only thing I need to do to make this my full time OS on this machine. Your help is greatly appreciated. :D


Brandon

---

### Post by linuxopjemac on 2010-01-27
please post your Xorg.conf file...

---

### Post by UniverseA7X on 2010-01-27
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	BusID		"PCI:0:16:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
EndSection

```

---

### Post by linuxopjemac on 2010-01-27
I think you can use the ATI driver instead of framebuffer...I will post another Xorg.conf for you, just make your existing Xorg.conf a backup one:

```
sudo mv /etc/X11/Xorg.conf /etc/X11/Xorg.conf.old

sudo /etc/X11/Xorg.conf
```

now paste the following Xorg.conf in there



```
Section "Files"
        RgbPath      "/usr/X11R6/lib/X11/rgb"
        ModulePath   "/usr/X11R6/lib/modules"
        FontPath     "/usr/X11R6/lib/X11/fonts/misc/"
        FontPath     "/usr/X11R6/lib/X11/fonts/TTF/"
        FontPath     "/usr/X11R6/lib/X11/fonts/Type1/"
        FontPath     "/usr/X11R6/lib/X11/fonts/CID/"
        FontPath     "/usr/X11R6/lib/X11/fonts/75dpi/"
        FontPath     "/usr/X11R6/lib/X11/fonts/100dpi/"
EndSection

Section "Module"
        Load  "dbe"
        Load  "extmod"
        Load  "glx"
        Load  "record"
        Load  "xtrap"
        Load  "freetype"
        Load  "type1"
EndSection

Section "InputDevice"
        Identifier  "Keyboard0"
        Driver      "kbd"
	Option	    "XkbRules"	"xorg"
	Option	    "XkbModel"	"pc104"
	Option	    "XkbLayout"	"us"
EndSection

Section "InputDevice"
        Identifier  "Mouse0"
        Driver      "mouse"
EndSection

Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
        HorizSync    30-107
        VertRefresh  48-120
EndSection

Section "Device"
        Identifier  "Card0"
        Driver      "ati"
        VendorName  "ATI Technologies Inc"
        BoardName   "Rage 128 RE/SG"
        BusID       "PCI:0:16:0"
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        DefaultDepth 24
        SubSection "Display"
                Viewport   0 0
                Depth     1
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     4
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     8
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     15
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     16
                Modes "1440x900" "1280x1024" "1024x768"
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes "1440x900" "1280x1024" "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier     "X.org Configured"
        Screen      0  "Screen0" 0 0
        InputDevice    "Mouse0" "CorePointer"
        InputDevice    "Keyboard0" "CoreKeyboard"
EndSection
```

---

### Post by linuxopjemac on 2010-01-27
then you go to a TTY:

ctrl-alt-F1

login as root

then

```
/etc/init.d/gdm stop
/etc/init.d/gdm start
```

then post me the results of the Xorg log file
```

cat /var/log/Xorg.0.log
```

---

### Post by linuxopjemac on 2010-01-27
I edited the Xorg.conf file, it had a mistake in there, in the modes section of default depth 24

---

### Post by UniverseA7X on 2010-01-28
Upon restarting GDM, I'm getting an Xorg error, telling me xorg can't start:

```

Module Loader preset
Markers: (--) probed, (**) from config file, (==) default setting,
              (++) from command line, (!!) notice, (II) informational,
              (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Jan 27 23:58:23 2010
(==) Using config file: "/etc/X11/xorg.conf"
(EE) Failed to load module "pcidata" (module does not exist, 0)

Fatal server error:
Unable to load required base modules, Exiting...

```

Here are other warnings I get in the extended readout using the same key as in the above notice: 

```

(WW)The directory "/usr/X11R6/lib/X11/fonts/misc/" does not exist. 
Entry deleted from font path

The same notice for the following directories:

/usr/X11R6/lib/X11/fonts/TFF/
/usr/X11R6/lib/X11/fonts/Type1/
/usr/X11R6/lib/X11/fonts/CID/
/usr/X11R6/lib/X11/fonts/75dpi/
/usr/X11R6/lib/X11/fonts/100dpi/

(WW) FontPath is completely invalid. Using compiled in default.
(==) FontPath set to:
/usr/share/fonts/X11/misc
/usr/share/fonts/X11/cyrillic
/usr/share/fonts/X11/100dpi/:unscaled
/usr/share/fonts/X11/75dpi/:unscaled
/usr/share/fonts/X11/Type1
/usr/share/fonts/X11/100dpi
/usr/share/fonts/X11/75dpi
/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType


```

I'm typing all of this, if you need an entire read out of the file, I can run a reconfig of the xorg server and copy paste the entire file here. These were just the errors and warnings.

And thank you for already creating an xorg file, that was beyond what I expected.

---

### Post by linuxopjemac on 2010-01-28
Presuming you typed the whole error message we will delete the font stuff from your Xorg.conf file as probably the paths do not fit...you can try to find out later


```
Section "Module"
        Load  "dbe"
        Load  "extmod"
        Load  "glx"
        Load  "record"
        Load  "xtrap"
        Load  "freetype"
        Load  "type1"
EndSection

Section "InputDevice"
        Identifier  "Keyboard0"
        Driver      "kbd"
	Option	    "XkbRules"	"xorg"
	Option	    "XkbModel"	"pc104"
	Option	    "XkbLayout"	"us"
EndSection

Section "InputDevice"
        Identifier  "Mouse0"
        Driver      "mouse"
EndSection

Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
        HorizSync    30-107
        VertRefresh  48-120
EndSection

Section "Device"
        Identifier  "Card0"
        Driver      "ati"
        VendorName  "ATI Technologies Inc"
        BoardName   "Rage 128 RE/SG"
        BusID       "PCI:0:16:0"
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        DefaultDepth 24
        SubSection "Display"
                Viewport   0 0
                Depth     1
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     4
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     8
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     15
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     16
                Modes "1440x900" "1280x1024" "1024x768"
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes "1440x900" "1280x1024" "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier     "X.org Configured"
        Screen      0  "Screen0" 0 0
        InputDevice    "Mouse0" "CorePointer"
        InputDevice    "Keyboard0" "CoreKeyboard"
EndSection
```

---

### Post by UniverseA7X on 2010-01-28
That worked, sort of. The correct resolution now appears, and I was able to set it to the display's native 1440x900, but there's still a quirk.

There are vertical soft lines that run across the screen, and the fonts aren't smooth. It looks like maybe a refresh rate issue? I'm not sure. The only refresh rate I'm able to pick is 60Hz, and I know that the monitor is capable of 75Hz.

Also, there's a resolution available higher than 1440x900, and it's 1440x1024.

Don't know if this has any relevance, I just thought it was odd since it wasn't in the Xorg.conf.

---

### Post by linuxopjemac on 2010-01-28
maybe HorizSync    30-107
        VertRefresh  48-120
is not correct. What happens if you delete that section ?

---

### Post by UniverseA7X on 2010-01-28
Just a quick note, 

It seems that the vertical lines disappear when I use other lower resolutions, and the picture is smoother. 

I know this monitor works with this computer as well, it was fine with Mac OS X. 

Just some extra information.

EDIT: The widescreen resolutions have the vertical lines. 1200x800, 1440x900, etc.

---

### Post by linuxopjemac on 2010-01-28
what if you try 1440x1024 ?

---

### Post by linuxopjemac on 2010-01-28
for even more tweaking:

[http://mac.linux.be/content/set-xorgconf-manually-xrandr](http://mac.linux.be/content/set-xorgconf-manually-xrandr)

---

### Post by linuxopjemac on 2010-01-28
m,onitor setting:

read from fbset to find the right modelines...

[http://mac.linux.be/content/black-screen-or-missing-gui](http://mac.linux.be/content/black-screen-or-missing-gui)

---

### Post by UniverseA7X on 2010-01-28
> **linuxopjemac said:**
> maybe HorizSync    30-107
        VertRefresh  48-120
is not correct. What happens if you delete that section ?

My ability to pick different resolutions disappears and I'm only left with the option of 800x600.

1440x1024 will show up, but things like the taskbars will be out of reach on the screen due the resolution being too large for the screen.

---

### Post by linuxopjemac on 2010-01-28
to find the exact modelines (refresh rates), you can try fbset as in the link.

---

### Post by UniverseA7X on 2010-01-28
Output from fbset:

```

Mode "1440x900"
    # D: 108.849 MHz, H: 56.930 kHz, V: 60.179 Hz
    DotClock 108.850
    HTimings 1440 1472 1880 1912
    VTimings 900 918 927 946
    Flags    "+HSync" "+VSync"
EndMode

```

With the horizontal and vertical refresh rates, what would I do with those? Would the HorizSync and VertRefresh change or stay the same? If they change, to those values?

This is what my monitors section looks like using the link you provided as a reference.

```

Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
	HorizSync    30-107
	VertRefresh  48-120
	Mode "1440x900"
		# D: 108.849 MHz, H: 56.930 kHz, V: 60.179 Hz
		DotClock 108.850
		HTimings 1440 1472 1880 1912
		VTimings 900 918 927 946
		Flags    "+HSync" "+VSync"
	EndMode
	
EndSection

```

---

### Post by UniverseA7X on 2010-01-28
On a resolution that doesn't have vertical lines, the horizontal refresh is slightly higher while the vertical is nearly identical. 

```

Mode "1280x1024"
    # D: 108.003 MHz, H: 63.983 kHz, V: 60.021 Hz
    DotClock 108.004
    HTimings 1280 1328 1440 1688
    VTimings 1024 1025 1028 1066
    Flags    "+HSync" "+VSync"
EndMode

```

---

### Post by linuxopjemac on 2010-01-28
I don't know if setting it to that exact frequency will make any difference to be honest. Your monitor will pick up any Horiz freq between 30 and 107 KHz, so it will probably find 56.93 kHz. I think you can make the window smaller, say 50-70 KHz. For the vertical you could also take 50-70. But again, I don't know if it makes any difference.

Try also with the 

```
Option "MonitorLayout" "TMDS"
```

in the Ati Device section...maybe it will improve.

so, you'll get this:

```
Section "Device"
        Identifier  "Card0"
        Driver      "ati"
        VendorName  "ATI Technologies Inc"
        BoardName   "Rage 128 RE/SG"
        BusID       "PCI:0:16:0"
        Option "MonitorLayout" "TMDS"
EndSection
```

---

### Post by UniverseA7X on 2010-01-28
I did try the extra string in the Device section, no change.

---

### Post by linuxopjemac on 2010-01-28
to find 75 Hz stuff, I would use the Xrandr link I gave you. Tweaking tweaking tweaking...until you find the best... :)

---

### Post by UniverseA7X on 2010-01-28
In that driver section, the driver is pointed out as being "ati".  I do remember seeing a separate "rage128" driver in synaptic, which is the card that this Mac has. Do you think changing the driver would help, since it is the driver for this card?

---

### Post by linuxopjemac on 2010-01-28
that driver is called "r128", see [http://linux.die.net/man/4/r128](http://linux.die.net/man/4/r128)

---

### Post by UniverseA7X on 2010-01-28
Well, you are really resourceful. 

Okay, I'm going to keep trying this, but tomorrow. It's 3 AM here and I have classes tomorrow. Thank you so much for dedicating time to help me through this. I really do appreciate it. :)

Good night.

---

### Post by linuxopjemac on 2010-01-28
thank you, sleep well and cu tomorrow then ;)

---

### Post by UniverseA7X on 2010-01-28
Hokay. 

I took the fbset of two resolutions, one with the vertical lines and one that doesn't fit the screen, but has no refresh issues. 

```

brandon@PowerMacG3:~$ fbset -x

Mode "1280x960"
    # D: 108.003 MHz, H: 60.002 kHz, V: 60.002 Hz
    DotClock 108.004
    HTimings 1280 1376 1488 1800
    VTimings 960 961 964 1000
    Flags    "+HSync" "+VSync"
EndMode

brandon@PowerMacG3:~$ fbset -x

Mode "1440x900"
    # D: 108.849 MHz, H: 56.930 kHz, V: 60.179 Hz
    DotClock 108.850
    HTimings 1440 1472 1880 1912
    VTimings 900 918 927 946
    Flags    "+HSync" "+VSync"
EndMode

```

I think It's because the Horizontal refresh differs from the Vertical refresh rate. 

I know the moniter can handle 75Hz, but all that shows up on xrandr is this:
```

brandon@PowerMacG3:~$ xrandr
Screen 0: minimum 800 x 600, current 1440 x 900, maximum 1440 x 1024
default connected 1440x900+0+0 0mm x 0mm
   1440x900       60.0* 
   1280x1024      60.0  
   1024x768       60.0  
   1280x960       60.0  
   1280x800       60.0  
   1280x768       60.0  
   800x600        60.0     56.0  
   1440x1024      60.0  

```

How would I go about adding the 75Hz refresh rate?

I tried doing what the person pointed out on the link you gave me:
```

aa@aa-desktop:/$ cvt 1920 1200 60
# 1920x1200 59.88 Hz (CVT 2.30MA) hsync: 74.56 kHz; pclk: 193.25 MHz
Modeline "1920x1200_60.00"  193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync
aa@aa-desktop:/$ cvt 1680 1050 60
# 1680x1050 59.95 Hz (CVT 1.76MA) hsync: 65.29 kHz; pclk: 146.25 MHz
Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
aa@aa-desktop:/$ xrandr --newmode "1920x1200_60.00"  193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync
aa@aa-desktop:/$ xrandr --newmode "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
aa@aa-desktop:/$ xrandr --addmode DVI-1 "1920x1200_60.00"
aa@aa-desktop:/$ xrandr --addmode DVI-0 "1680x1050_60.00"

```

But with the --addmode argument, I don't know what should be in place of "DVI-1", whatever I type for that argument brings me an error with a list of possible arguments for that application. I tried adding "1440x900_75.00".

---

### Post by UniverseA7X on 2010-01-28
Okay, here's where I've gotten.

```

brandon@PowerMacG3:~$ cvt 1440 900 75
# 1440x900 74.98 Hz (CVT 1.30MA) hsync: 70.64 kHz; pclk: 136.75 MHz
Modeline "1440x900_75.00"  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync

```

Did a cvt to find out what the clock speeds for 75Hz would be.

I tried to follow the instructions on the link, but I don't know the output argument:
```

brandon@PowerMacG3:~$ xrandr --newmode "1440x900_75.00"  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync
brandon@PowerMacG3:~$ xrandr --addmode DVI-1 "1440x900_75.00"
xrandr: cannot find output "DVI-1"

```

---

### Post by UniverseA7X on 2010-01-28
Duh. the missing argument was just "default".

It added a 75Hz refresh rate option to the Screen Resolution GUI, but when I clicked on it, it did nothing, and upon a restart, disappeared. I'm so lost.

---

### Post by UniverseA7X on 2010-01-28
Well, I have a monitor that's 1280x1024 that I plugged in and that works. might just use this one. If you have any possible solutions, just let me know, but I really appreciate your help, and I learned a LOT about working out the quirks with this and working the X server, so I also thank you for showing me that. 

On a side note, Debian runs FAST on this nearly ten year old computer, there's no lag scrolling on the internet. None of the bloat of OS X. I thought I might be doomed to running OS 9, which I had for a while. But this is overall really wonderful.

---

### Post by linuxopjemac on 2010-01-29
This is also how far my knowledge stretches...If you played around enough, you should be happy at some point you know. I think you learned a lot and I am sure you are a happy user of Debian now. It is a WHOLE lot better than OS9, believe me. Debain is rock solid. It runs on an old Pismo G3 PowerBook of mine for years. Never had any trouble...

---

