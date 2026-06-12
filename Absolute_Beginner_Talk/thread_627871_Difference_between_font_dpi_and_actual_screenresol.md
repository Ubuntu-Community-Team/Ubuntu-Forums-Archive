---
title: "Difference between font dpi and actual screenresolution dpiCan somebody explain to me"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by Bandicoot on 2007-11-30
Can somebody explain to me the difference between font DPI and the actual resolution my monitor is showing ?? I've set my fontsize to 96 DPI (well actual that&#347; the standard setting) I was expecting that the resolution of my monitor ( a 19" TFT @ 1280x1024) would also be 96 DPI ( i read somewhere in a HOWTO about clear fonts that my fonts dpi and screen dpi should be 96). But when I checked I got the following

edensal@Gutsy-desktop:~$ xdpyinfo | grep dimensions
  dimensions:    1280x1024 pixels (382x302 millimeters)

edensal@Gutsy-desktop:~$ xdpyinfo | grep resolution
  resolution:    85x86 dots per inch

That means my screen is running on 85 dpi , right ?? Is this normal or should I change something ?  The dimensions (382x302 mm) are correct for my TFT.

I am sorry if I sound a bit fuzzy, that's probably because I'm a bit confused about what those number do/mean.

---

### Post by david_2001 on 2007-11-30
I'm no expert on this but the trick is to get the display resolution reported by xdpyinfo to match the font resolution (System -> Preferences -> Appearance -> Fonts -> Details... in Gnome).  To set the display resolution for my 19" 1280x1024 TFT monitor / nvidia card to 96dpi I just followed part of the instructions in the [COLOR="DarkOrange"][Arch Wiki]("http://wiki.archlinux.org/index.php/Xorg#Display_Size.2FDPI")[/COLOR] and added 
```
        Option          "UseEdidDpi" "False"
        Option          "DPI" "96 x 96"
```
to the "Device" section of /etc/X11/xorg.conf.  If I leave this out I get more or less the same output from xdpyinfo as you quoted and nasty, unpleasant fonts.  If I put it back in and restart X then I get:
```
[david@darkstar ~]$ xdpyinfo | grep -B1 dot
  dimensions:    1280x1024 pixels (339x271 millimeters)
  resolution:    96x96 dots per inch
```
and nice clear fonts.

---

### Post by Bandicoot on 2007-12-01
I followed the above instructions but I still get :

dimensions:    1280x1024 pixels (382x302 millimeters)
  resolution:    85x86 dots per inch

This is how my xorg.conf looks like now: 

Section "Device"
    Identifier     "nVidia Corporation NV40.2 [GeForce 6800 LE]"
    Driver         "nvidia"
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    Option         "UseEdidDpi" "False"
    Option         "DPI" "96 x 96"
    BusID          "PCI:1:0:0"
EndSection


What am I doing wrong or is is my TFT  not meant to display 96 DPI ?? BTW my screen is a Dell 1908FP

---

### Post by david_2001 on 2007-12-01
Not sure at all - the specification of your monitor looks similar to mine only better.  What do you have in the "Monitor" and "Screen" sections of xorg.conf?  Here's what I have for comparison:
```
Section "Device"
        Identifier      "NVIDIA GeForce 7100 GS"
#       Driver          "nv"
        Driver          "nvidia"
        BusID           "PCI:2:0:0"
        Option          "TripleBuffer" "True"
        Option          "AddARGBGLXVisuals" "True"
        Option          "DisableGLXRootClipping" "True"
# See https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/104105
        Option          "DynamicTwinView" "False"
        Option          "UseEdidDpi" "False"
        Option          "DPI" "96 x 96"
EndSection

Section "Monitor"
        Identifier      "F-419"
        Option          "DPMS"
        HorizSync       24-80
        VertRefresh     49-75
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA GeForce 7100 GS"
        Monitor         "F-419"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
```
Also, does nvidia-settings give any useful information (see screenshot)?

---

### Post by Bandicoot on 2007-12-01
**This post could be related to an Ubuntu bug filed at**: [/HTML] [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Here how it looks on my system (btw how do I use a code window like you did?):

Section "Monitor"
    Identifier     "DELL 1908FP"
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL 1908FP"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 76.0
EndSection

Section "Device"
    Identifier     "nVidia Corporation NV40.2 [GeForce 6800 LE]"
    Driver         "nvidia"
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    Option         "UseEdidDpi" "False"
    Option         "DPI" "96 x 96"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6800 LE"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV40.2 [GeForce 6800 LE]"
    Monitor        "DELL 1908FP"
    DefaultDepth    24
    SubSection     "Display"
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1280x1024_60 +0+0; 1280x1024 +0+0; 1152x864 +0+0; 1024x768 +0+0; 800x600 +0+0; 640x480 +0+0"
EndSection

I also made a screenshot of my nvidia-settings.

---

### Post by david_2001 on 2007-12-01
Adding the code tags is as easy as highlighting some text and clicking the hash button in the toolbar.  Anyway, it seems that we have a bug but the URL is missing.  In the meantime, your xorg.conf looks wrong to me because it contains duplicated monitor, device and screen sections.  The working parts should look more like:
```
Section "Monitor"
Identifier "DELL 1908FP"
Option "DPMS"
HorizSync 31.0 - 83.0
VertRefresh 56.0 - 76.0
EndSection

Section "Device"
Identifier "nVidia Corporation NV40.2 [GeForce 6800 LE]"
Driver "nvidia"
Option "AddARGBVisuals" "True"
Option "AddARGBGLXVisuals" "True"
Option "NoLogo" "True"
Option "UseEdidDpi" "False"
Option "DPI" "96 x 96"
BusID "PCI:1:0:0"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "nVidia Corporation NV40.2 [GeForce 6800 LE]"
Monitor "DELL 1908FP"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
EndSubSection
EndSection
```
There will also be a ServerLayout section elsewhere in xorg.conf that should look something like:
```
Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

```
(You'll have to check that the identifiers are correct/consistent for the Screen and all InputDevices.)

---

### Post by Bandicoot on 2007-12-01
Pfff I am really confused now, I can see what you mean with the double entries, but I am affraid that I if I change something my x-server will crash,because I do not exactly know what has to stay and what I can leave out.  

My serverconfig looks like this:

```
Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
```

---

### Post by david_2001 on 2007-12-01
Be brave!  Make a backup copy of /etc/X11/xorg.conf before making any changes.
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
If X won't start then you should be dropped to a console prompt from which you can log in and restore the backup or you could boot into recovery mode or whatever Ubuntu calls it - check out the different kernel options that GRUB lists - to go straight to a console.  The alternative is to have a live CD to hand and boot from that to make the change.

Edit your xorg.conf so that you have just one each of the Monitor, Device and Screen sections, as in my earlier post, and then change the ServerLayout section to:
```
Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
    Identifier     "Default Layout"
    Screen         "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection
```

---

### Post by Bandicoot on 2007-12-01
Thank you very much for your detailed help ! I've edited everything the way you told me, and now my screen is running on 96 DPI !!

---

### Post by david_2001 on 2007-12-01
> **Bandicoot said:**
> Thank you very much for your detailed help ! I've edited everything the way you told me, and now my screen is running on 96 DPI !!

8)

---

