---
title: "Multi Head Macbook"
date: 2007-09-02
forum: Apple Intel Users
---

### Post by mealz on 2007-09-02
I have just had some success that I thought someone else might benefit from.

I have a Core 2 Duo Macbook and a 1680x1050 LCD connected via DVI.
My task was to get it to work!
I have succeeded!
Note: This is not necesarily the best way... its just a way that worked for me.
 __________________________________________________________
First remove the new intel driver and replace it with the older i810 driver.
```
sudo apt-get remove xserver-xorg-video-intel
sudo apt-get install xserver-xorg-video-i810
```

Next backup your /etc/X11/xorg.conf and use this one or make a similar config.

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)

Section "Files"
  FontPath "/usr/share/fonts/X11/misc"
  FontPath "/usr/share/fonts/X11/cyrillic"
  FontPath "/usr/share/fonts/X11/100dpi/:unscaled"
  FontPath "/usr/share/fonts/X11/75dpi/:unscaled"
  FontPath "/usr/share/fonts/X11/Type1"
  FontPath "/usr/share/fonts/X11/100dpi"
  FontPath "/usr/share/fonts/X11/75dpi"
  # path to defoma fonts
  FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
  Load "i2c"
  Load "bitmap"
  Load "ddc"
  Load "extmod"
  Load "freetype"
  Load "int10"
  Load "vbe"
  load "glx"
  load "GLcore"
  load "v4l"
EndSection

Section "InputDevice"
  Identifier "Generic Keyboard"
  Driver "kbd"
  option "CoreKeyboard"
  option "XkbRules" "xorg"
  option "XkbModel" "pc105"
  option "XkbLayout" "us"
  option "XkbVariant" "us"
  option "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
  Identifier "Configured Mouse"
  Driver "mouse"
  option "CorePointer"
  option "Device" "/dev/input/mice"
  option "Protocol" "ImPS/2"
  option "ZAxisMapping" "4 5"
  option "Emulate3Buttons" "true"
  option "SHMConfig" "true"
EndSection

Section "InputDevice"
  Identifier "Synaptics Touchpad"
  Driver "synaptics"
  option "CorePointer"
  option "Device" "/dev/input/mouse1"
  option "Protocol" "auto-dev"
  option "LeftEdge" "20"
  option "RightEdge" "1000"
  option "TopEdge" "17"
  option "BottomEdge" "700"
  option "FingerLow" "5"
  option "FingerHigh" "7"
  option "MaxTapTime" "180"
  option "MaxTapMove" "220"
  option "MaxDoubleTapTime" "180"
  option "TapButton2" "3"
  option "TapButton3" "2"
  option "VertScrollDelta" "7"
  option "MinSpeed" "0.79"
  option "MaxSpeed" "0.88"
  option "AccelFactor" "0.0015"
  option "LeftRightRepeat" "0"
  option "UpDownRepeat" "0"
  option "UpDownScrolling" "on"
  option "RTCornerButton" "0"
  option "RBCornerButton" "0"
  option "LTCornerButton" "0"
  option "LBCornerButton" "0"
  option "EdgeMotionUseAlways" "0"
  option "EdgeMotionMinZ" "25"
  option "EdgeMotionMaxZ" "60"
  option "EdgeMotionMinSpeed" "150"
  option "EdgeMotionMaxSpeed" "200"
  option "SHMConfig" "on"
  # turn off horizontal scrolling
  #Option "HorizScrollDelta" "0"
  # turn off corner buttons
  # edge motion
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "cursor"
  option "Device" "/dev/wacom"# Change to 
  option "Type" "cursor"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
  # /dev/input/event
  # for USB
EndSection

Section "Device"
  identifier "0 Intel 945GM"
  busid "PCI:0:2:0"
  driver "i810"
  screen 0
  option "MonitorLayout" "DFP,LFP"
EndSection

Section "Device"
  identifier "1 Intel 945GM"
  busid "PCI:0:2:0"
  driver "i810"
  screen 1
  option "MonitorLayout" "DFP,LFP"
EndSection

Section "Monitor"
  identifier "Generic Monitor"
  modelname "Flat Panel 1280x800"
  Option "DPMS"
EndSection

Section "Monitor"
  identifier "External Monitor"
  modelname "Flat Panel 1680x1050"
  Option "DPMS"
EndSection

Section "Screen"
  Identifier "Default Screen"
  Device "0 Intel 945GM"
  Monitor "Generic Monitor"
  DefaultDepth 24
  SubSection "Display"
    depth 24
     modes "1280x800"
EndSubSection
EndSection

Section "Screen"
  Identifier "External Screen"
  Device "1 Intel 945GM"
  Monitor "External Monitor"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    modes "1680x1050"
  EndSubSection
EndSection

Section "ServerLayout"
  Identifier "Default Layout"
  screen 0 "Default Screen"
  screen 1 "External Screen" above "Default Screen"  
  InputDevice "Generic Keyboard"
  InputDevice "Synaptics Touchpad"
  InputDevice "Configured Mouse" "SendCoreEvents"
#  Option 	"Xinerama" "true"  
EndSection

Section "DRI"
  Mode 0666
EndSection

```

Uncomment the Xinerama option if you would like to treat both displays as one desktop.
I haven't done this as you may find you "loose" windows when you are on the road without your external display!

An important thing to note is the option "MonitorLayout" "DFP,LFP".
The macbook has the options of LFP, DFP, CRT, TV
This specifies the connections for the primary and secondary display.
It is REVERSE to what you would think.
It is done in this format "MonitorLayout" "<screen1>,<screen0>"

Next we must work with 915resolution so that we can set the external resolution correctly. You most probably already have 915resolution installed (to give you 1280x800 on your internal LCD).
If not:
```
sudo apt-get install 915resolution
```

By default it seems that 915resolution only supports either an auto mode where your lcd is queried for its native resolution, or a manual setting where you specify what resolution you want to use.

In this case we want both! (auto for internal lcd, and manual for external monitor).
So I simply went and edited /etc/init.d/915resolution
I have taken out the if statement... so we get the auto and manual modes together.
Listing starts around line 84:
```
start|restart|force-reload)
	echo -n "Starting $DESC: "
	
	    auto_select_modes
	    $PROG $MODE $XRESO $YRESO $BIT	
	echo "$NAME."
	;;

```

Finally we need to edit /etc/default/915resolution to set the mode of our external display.

```
#
# 915resolution default
#
# find free modes by  /usr/sbin/915resolution -l
# and set it to MODE or set to 'MODE=auto'
#
# With 'auto' detection, the panel-size will be fetched from the VBE
# BIOS if possible and the highest-numbered mode in each bit-depth
# will be overwritten with the detected panel-size.
MODE=5a
#
# and set resolutions for the mode.
# e.g. use XRESO=1024 and YRESO=768
XRESO=1680
YRESO=1050
#
# We can also set the pixel mode.
# e.g. use BIT=32
# Please note that this is optional,
# you can also leave this value blank.
BIT=

```

After a reboot you should now have a working external display!

Hope this has been useful to someone.

---

### Post by cryptocoryne on 2007-09-02
I think I have it working using the new intel driver. I have a 22" Westinghouse LCM-22W3 with a native resolution of 1680x1050. At first, I used the xorg.conf that was suggested in the Ubuntu macbook documentation.  This got xinerama working but only at 1280x1024. (I edited the changes a little to include 1680x1050 mode.) The macbook display was at 1200x800. Any attempt to switch to higher resolutions just gave a scrambled screen.

I find xinerama a bit clunky and think that a more sensible default is for the external display to just be the only display when a monitor is connected.  i.e. with no monitor connected, the macbook should use its built-in screen and when you connect an external display, the laptop screen should switch off and the external monitor should be the only display.

Xinerama sucks because you lose 3D accel eye candies and it makes your xorg.conf more confusing.

Mirroring sucks because it won't go over the macbook screen's 1200x800 resolution. When I tried it, the external would only do 1200x768 and the bottom of the screen was cut off.

Finally, I settled on just letting dpkg configure xorg.conf. Then I had to go back and add a modeline for 1680x1050.  When I restarted X, gdm's login screen appeared perfectly at 1680x1050, but the when I logged in, all I got was 1200x768.  I tried using gnome's "Screen Resolution" control to switch, but it just scrambled the screen.  Using gconf-edit to change the resolution for screen 0 to 1680x1050 and restarting did it.  Now the laptop screen shows a 1200x800  slice of the larger external screen.  For now, I just look at the external screen.

The only big problem now is that the system no longer wakes from sleep. I just get a black screen with an underscore flashing in the left upper corner. When I'm more in the mood, I'll test with eye candy turned off.

---

