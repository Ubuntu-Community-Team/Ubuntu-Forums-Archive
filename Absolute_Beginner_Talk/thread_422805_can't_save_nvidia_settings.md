---
title: "can't save nvidia settings"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by joshaude on 2007-04-25
I just installed feisty fawn on my laptop and I am dual booting with xp.  I have a flat panel LCD monitor and of course the laptop monitor and I am trying to set up separate x screens or twinview.  I used envy to install the proper nvidia drivers but every time I change something in the control panel and click "Save to X Configuration", it reverts back to the default when I restart the X server.  It wont keep any settings at all.  This is extremely frustrating and I would appreciate any advice.

my specs:
nVidia GeForce 6200 Go
14.1" flat panel, max res. 1024x768
19" flat panel, max res. 1280x1024 - attached to VGA out

---

### Post by Nythain on 2007-04-25
run it with gksudo or kdesu or whatever graphical sudo you use... it needs root privelages to write to the xorg.conf

---

### Post by THEnumber337 on 2007-04-25
run
```

sudo nvidia-settings

```

I think that should work.

---

### Post by joshaude on 2007-04-25
I'm not sure what you mean by root privileges but I don't have any trouble running the nvidia-settings.  The problem is that any changes I make don't get saved.

---

### Post by compmodder26 on 2007-04-25
That is most likely due to nvidia-settings not being run with root privileges.  All nvidia-settings is, is a front-end for making relevant changes to xorg.conf.  Xorg.conf is owned by root.  Therefore, if nvidia-settings isn't being run with root privileges, any changes you attempt to make with it will not work.  Odd that you wouldn't get a permission denied error somewhere though.

---

### Post by Nythain on 2007-04-25
yeah, that lack of a access denied error sucks... took me almost a month before it clicked in my head that was the problem :)

---

### Post by joshaude on 2007-04-25
So how can I get it to have root privileges?

P.S. Thanks for helping me out on this.

---

### Post by compmodder26 on 2007-04-25
Posts 2 and 3 have that information

---

### Post by Nythain on 2007-04-25
you can

A: open a terminal and run sudo nvidia-settings
or
B: edit the menu list and add sudo before the nvidia-settings command

---

### Post by joshaude on 2007-04-25
Awesome! It's working. Thanks for all the help!

---

### Post by Nythain on 2007-04-25
no prob... like i mentioned, since it doesnt give any access denied error it can be a bit tricky to figure out, and took me almost a month

---

### Post by sisco311 on 2007-04-25
> edit the menu list and add **sudo** before the nvidia-settings command
**gksu** nvidia-settings

---

### Post by Nythain on 2007-04-25
yeah... sorry bout that... i use kde so i can never remember what the graphical sudo command for gnome is... thanks for the correction

---

### Post by gohanssjn on 2007-05-16
I am having a similar problem.

The settings are getting saved it seems, but they don't apply whenever I restart the system.  As soon as I type sudo nvidia-settings to open the GUI, they settings apply themselves.

Any way to fix this?

---

### Post by Hobo Joe on 2007-05-16
> **gohanssjn said:**
> I am having a similar problem.

The settings are getting saved it seems, but they don't apply whenever I restart the system.  As soon as I type sudo nvidia-settings to open the GUI, they settings apply themselves.

Any way to fix this?

Once you have it opened with root privileges, set everything how you want, click 'apply', then click 'Save X to configuration file'. 

Reboot, then tell us if it worked.

---

### Post by gohanssjn on 2007-05-16
That's what I did first.  No go.

---

### Post by kinkdxm on 2007-07-04
bump!
:)

I have the same problem
I do 
sudo nvidia-settings
make the changes 
save to x configuration file
and when I restart or log off it reverts back to something else

---

### Post by dsmorgan6922 on 2007-07-22
I am also saving the same problem but I'm getting errors! I used Envy to install the nvidia drivers but when I try to run sudo nividia-settings I get the following errors:

> ERROR: Cannot open display 'DSMLAPTOP:0.0'.


ERROR: Unable to assign attribute DigitalVibrance specified on line 19 of
       configuration file '/home/doug/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute SyncToVBlank specified on line 20 of
       configuration file '/home/doug/.nvidia-settings-rc' (no Display
       connection).


I've been looking in my xorg.conf file and 'DSMLAPTOP:0.0' isn't mentioned there. I did take a look at the .nvidia-settings-rc file and there is nothing there that seems off.  I'm thinking I have to insert DSMLAPTOP:0.0 somewher ein xorg.conf but don't know where, any help?

---

### Post by TwistedAx on 2008-01-10
having a huge problem here..
used gksu, gksudo, sudo and non of the 3 work
when i restart linux it just reverts back to 1024_768@50, need @75, and non my other nvidia-settings configs never stick either
it will NOT let me save, even when actualy logged in as root, and using gksu

always get the following errors, sometimes they dont show in termainal but happen anyway (settings dont load same as if errors are shone):

ERROR: Cannot open display 'drake-desktop:0.0'.


ERROR: Unable to assign attribute DigitalVibrance specified on line 19 of
       configuration file '/home/kayce/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute ImageSharpening specified on line 20 of
       configuration file '/home/kayce/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute SyncToVBlank specified on line 21 of
       configuration file '/home/kayce/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute AllowFlipping specified on line 22 of
       configuration file '/home/kayce/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAniso specified on line 23 of
       configuration file '/home/kayce/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAA specified on line 24 of configuration
       file '/home/kayce/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute TextureSharpen specified on line 25 of
       configuration file '/home/kayce/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute ForceGenericCpu specified on line 26 of
       configuration file '/home/kayce/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GammaCorrectedAALines specified on line 27 of
       configuration file '/home/kayce/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadow specified on line 28 of
       configuration file '/home/kayce/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowXOffset specified on line 29 of
       configuration file '/home/kayce/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowYOffset specified on line 30 of
       configuration file '/home/kayce/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowAlpha specified on line 31 of
       configuration file '/home/kayce/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowRed specified on line 32 of
       configuration file '/home/kayce/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowGreen specified on line 33 of
       configuration file '/home/kayce/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowBlue specified on line 34 of
       configuration file '/home/kayce/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAAAppControlled specified on line 35 of
       configuration file '/home/kayce/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAnisoAppControlled specified on line 36 of
       configuration file '/home/kayce/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedBrightness specified on line 37 of
       configuration file '/home/kayce/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenBrightness specified on line 38 of
       configuration file '/home/kayce/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueBrightness specified on line 39 of
       configuration file '/home/kayce/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedContrast specified on line 40 of
       configuration file '/home/kayce/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenContrast specified on line 41 of
       configuration file '/home/kayce/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueContrast specified on line 42 of
       configuration file '/home/kayce/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedGamma specified on line 43 of
       configuration file '/home/kayce/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenGamma specified on line 44 of
       configuration file '/home/kayce/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueGamma specified on line 45 of
       configuration file '/home/kayce/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute OpenGLImageSettings specified on line 46 of
       configuration file '/home/kayce/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureSyncToVBlank specified on line
       47 of configuration file '/home/kayce/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoBlitterSyncToVBlank specified on line
       48 of configuration file '/home/kayce/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoSyncToDisplay specified on line 49 of
       configuration file '/home/kayce/.nvidia-settings-rc' (no Display
       connection).


   my xorg.conf file:

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Hitachi PLASMA TV"
    HorizSync       24.0 - 109.0
    VertRefresh     50.0 - 85.0
    ModeLine       "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
    ModeLine       "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
    ModeLine       "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
    ModeLine       "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
    ModeLine       "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
    ModeLine       "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
    ModeLine       "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "640x480@85" 36.0 640 696 752 832 480 481 484 509 -hsync -vsync
    ModeLine       "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
    ModeLine       "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7800 GTX"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0; 1024x768@85 +0+0; 1024x768@75 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


AMD 64x2 4800+ @2.520, 2gb ram,
Nvidia 7800GTX 256mb mem
Hitachi Plasma 42" 50-85hz
(if it helps)

---

### Post by kinkdxm on 2008-01-11
switched to using an ati video card instead of my older nvidia one and actually everytime I restart the computer the resolution reverts back as well.

luckly though I don't restart that often.

---

### Post by TwistedAx on 2008-01-11
unfortunatly for me, i tend to restart at least 1-3 times a day..

---

