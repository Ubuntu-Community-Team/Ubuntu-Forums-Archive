---
title: "Dual screen questions"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by Hobo Joe on 2007-08-21
Ok, so I have dual screens set up pretty much exactly how I want, when press maximize, it just fills one screen, I can drag windows between the two and all that jazz. But the problem is, when there is a fullscreen app, like a game, it will try and fill the screen, but with a horribly stretched resolution, as you can imagine, with an aspect ratio of about 9:3. The only way to get around this, as far as I know, is too put it into windowed mode. 

The other problem is Ubuntu seems to want to switch the order of my monitors, because when I boot into Ubuntu, the log in screen is on my secondary monitor. But I know it's not from plugging them in wrong, because the motherboard splash screen and GRUB is on the other monitor(as it should be), also, Windows treats that monitor as primary(as it should). I also know that its not my drivers, because this happens even before I get my drivers installed.
The strange thing to me is though, that when I run a game fullscreen, it wants to stretch, but movies want to fullscreen in the secondary monitor(the one that SHOULD be secondary anyway).

So basically I want it to work like it does in Windows, I want things to fullscreen and maximize in one monitor(my primary), and not try to stretch, and I want movies to maximize in the primary monitor. And I also would like to figure out why Ubuntu seems to want to switch my primary and secondary.

(sorry if this is too long-winded and unclear, let me know if something doesn't make sense.)

---

### Post by madcow72 on 2007-08-21
Sounds like you're using an ATI graphics card.  I may get flamed for saying this, (probably will) but honestly, switching over to NVidia has solved every graphics card related issue for me, such as the one you're mentioning above.  No futzing around - it's all done with a GUI driver configuration exactly like it was done in Windows.

What are you using for dual head anyway?  BigDesktop, Xinerama,...  Perhaps a post of your xorg.conf would be useful.

---

### Post by Hobo Joe on 2007-08-21
> **madcow72 said:**
> Sounds like you're using an ATI graphics card.  I may get flamed for saying this, (probably will) but honestly, switching over to NVidia has solved every graphics card related issue for me, such as the one you're mentioning above.  No futzing around - it's all done with a GUI driver configuration exactly like it was done in Windows.

What are you using for dual head anyway?  BigDesktop, Xinerama,...  Perhaps a post of your xorg.conf would be usefull.

Actually, it is an nVidia. :)
And it did fix almost all my problems(I used to have an ATi), except this one.

It's an 8800 GTS.

Xorg.conf:

```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       30.0 - 100.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "ViewSonic A72f-2"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTS"
Option "XAANoOffscreenPixmaps" "true"
Option "AddARGBGLXVisuals" "true"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "UseFBDev" "true"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT-0: 1152x864 +1152+0, CRT-1: 1152x864 +0+0; CRT-0: nvidia-auto-select +800+0, CRT-1: 800x600 +0+0; CRT-0: nvidia-auto-select +640+0, CRT-1: 640x480 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

---

### Post by madcow72 on 2007-08-21
Good choice on the card!  I'm using an NVidia 6200 - although I'm not sure where the difference would lie in terms of your specific problems by comparing our cards.  Quick question:  Did you use the nvidia-settings package to configure your xorg.conf?  Whenever I re-install my OS, I do:
Alt+F2 and type in nvidia-settings
I configure the system for Dual Head TwinView with the correct orientation of my monitors and then hit "Save to X Configuration File."  However, because I'm not root (you could try running this configuration utility as root - Can't remember if I've tried that or not.) it won't actually save, but will give you a button which shows you a preview of your xorg file, which I copy and paste into gedit on my desktop.  After that, I open a terminal and replace /etc/X11/xorg.conf with the new generated xorg.conf file....  Then everything works for me.

Does this do anything?

---

### Post by Hobo Joe on 2007-08-21
> **madcow72 said:**
> Good choice on the card!  I'm using an NVidia 6200 - although I'm not sure where the difference would lie in terms of your specific problems by comparing our cards.  Quick question:  Did you use the nvidia-settings package to configure your xorg.conf?  Whenever I re-install my OS, I do:
Alt+F2 and type in nvidia-settings
I configure the system for Dual Head TwinView with the correct orientation of my monitors and then hit "Save to X Configuration File."  However, because I'm not root (you could try running this configuration utility as root - Can't remember if I've tried that or not.) it won't actually save, but will give you a button which shows you a preview of your xorg file, which I copy and paste into gedit on my desktop.  After that, I open a terminal and replace /etc/X11/xorg.conf with the new generated xorg.conf file....  Then everything works for me.

Does this do anything?

Yes this card rocks! :D

And I have configured my setup with nvidia-settings, setup as Twinview. I also know how to run the control panel as root. There are two ways:
One, is to run 'sudo nvidia-settings', the other is to go to System > Preferences > Main menu, and find the control panel, and prefix the command with 'gksu'.

---

### Post by madcow72 on 2007-08-22
Sorry!  I'm not sure what else to suggest, 'cause using TwinView with NVidia on all 3 of my systems behaves appropriately when maximizing and all that.  

Anyone else?

---

### Post by Hobo Joe on 2007-08-22
> **madcow72 said:**
> Sorry!  I'm not sure what else to suggest, 'cause using TwinView with NVidia on all 3 of my systems behaves appropriately when maximizing and all that.  

Anyone else?

It's not maximizing that's the problem, it's fullscreen apps.

Maximizing works exactly how I want it too, but I just can't seem to figure out the fullscreen issue.
It's not caused by compiz by the way, in case anyone was going to suggest that.

---

