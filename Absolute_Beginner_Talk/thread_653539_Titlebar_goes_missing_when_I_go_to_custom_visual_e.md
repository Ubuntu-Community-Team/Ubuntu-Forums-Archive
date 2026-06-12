---
title: "Titlebar goes missing when I go to custom visual effects"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by gianthobbit on 2007-12-30
When I go to no visual effects my title bars come back  and when I go back to advanced or customized they disappear.  How do I fix this?

---

### Post by fmartinez on 2007-12-30
In a terminal try: metacity --replace &
If you have emerald installed: emerald --replace &
Then close then terminal.

---

### Post by gianthobbit on 2007-12-30
I should have mentioned this as well, when I have the customized appearance my terminal is all white, I have to go to no effects to get a working termainal

---

### Post by overdrank on 2007-12-30
> **gianthobbit said:**
> I should have mentioned this as well, when I have the customized appearance my terminal is all white, I have to go to no effects to get a working termainal

If you have a nvidia card then you may try to add this to your xorg
First back up your xorg
To copy Xorg
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
```
To restore backup
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
Option "AddARGBVisuals" "True"
Option "AddARGBGLXVisuals" "True"
Edit your xorg with this command ```
gksudo gedit /etc/X11/xorg.conf
``` You can use this command via alt, F2 keys because your terminal is white.

Example
Section "Device"
    Identifier     "nVidia Corporation NV43 [GeForce 6600 GT]"
    Driver         "nvidia"
Option "AddARGBVisuals" "True"
Option "AddARGBGLXVisuals" "True"
EndSection

---

### Post by gianthobbit on 2007-12-30
When I type the string in to do a backup do I check the run in terminal?  I did it both ways and when I went into the folder it did not look like it made a back up.  I manually made a back up of the file by just copying and renaming the extension.  

When I run the open xorg.conf it is all white with no text to edit.  I assume that if I go back to no effects that my xorg.conf file changes or should I go into no effects to make these changes and will they stick when I go to customize effects.

Thanks

---

### Post by overdrank on 2007-12-30
> **gianthobbit said:**
> When I type the string in to do a backup do I check the run in terminal?  I did it both ways and when I went into the folder it did not look like it made a back up.  I manually made a back up of the file by just copying and renaming the extension.  

When I run the open xorg.conf it is all white with no text to edit.  I assume that if I go back to no effects that my xorg.conf file changes or should I go into no effects to make these changes and will they stick when I go to customize effects.

Thanks

Hi if you typed the command make sure the X capital. You can just copy and paste. The command is case sensitive.

---

### Post by SOULRiDER on 2007-12-30
What kind of video card do you have?
If you have nvidia try this in a terminal
```
sudo nvidia-xconfig
```

After that restart xorg by pressing ctrl + alt + backspace

---

### Post by gianthobbit on 2007-12-30
I tried it with the exact same syntax and I still don't see it making a back up file.  Don't know what is going wrong there but regardless I have manually made a back up.

The video card I have is integrated card for the HP Pavililion a330n says Nvidia GeForce 4 on the front of the box.

I can run the code but only when I am in no effect mode.  I cant even get the "sudo nvidia-xconfig" to run through f2 method, and when I do it opens a blank white terminal box.  Can I edit xorg.conf in no effect mode or does it change every time I make it go to customize.  Anything else I can try?

---

### Post by jdholifield on 2007-12-30
Had the exact same problem the other day.  Here is how I fixed it.  I went into the synaptic package manager and noticed that one package ( sorry forgot the name - but related to gnome and compiz was not selected ), so I selected it and it worked find after that.

---

### Post by overdrank on 2007-12-30
> **gianthobbit said:**
> I tried it with the exact same syntax and I still don't see it making a back up file.  Don't know what is going wrong there but regardless I have manually made a back up.

The video card I have is integrated card for the HP Pavililion a330n says Nvidia GeForce 4 on the front of the box.

I can run the code but only when I am in no effect mode.  I cant even get the "sudo nvidia-xconfig" to run through f2 method, and when I do it opens a blank white terminal box.  Can I edit xorg.conf in no effect mode or does it change every time I make it go to customize.  Anything else I can try?

Ok could you post the output of this command in the terminal  ( if you have to turn off the effects then do so) ```
cat /etc/X11/xorg.conf
```

---

### Post by gianthobbit on 2007-12-30
How do I find the Synaptic package manager (brand spanking new to Ubuntu).

Here is the output from that code you wanted me to run 
```

family@family-desktop:~$ cat /etc/x11/xorg.conf
cat: /etc/x11/xorg.conf: No such file or directory
family@family-desktop:~$ cat /etch/X11/xorg.conf
cat: /etch/X11/xorg.conf: No such file or directory
family@family-desktop:~$ cls
bash: cls: command not found
family@family-desktop:~$ clear
family@family-desktop:~$ cat /etc/X11/xorg.conf
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon Apr 16 20:37:13 PDT 2007

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
    Identifier     "Default Layout"
    Screen      0  "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
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
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    VendorName     "Gateway"
    ModelName      "Gateway EV700"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 120.0
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
    ModeLine       "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
    ModeLine       "640x480@85" 36.0 640 696 752 832 480 481 484 509 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
    ModeLine       "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
    ModeLine       "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
    ModeLine       "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
    ModeLine       "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
    ModeLine       "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync +vsync interlace
    ModeLine       "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
    ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
    ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
EndSection

Section "Monitor"

 #                    
    Identifier     "monitor1"
    VendorName     "Plug 'n' Play"
    ModelName      "Plug 'n' Play"
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
    ModeLine       "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
    ModeLine       "640x480@85" 36.0 640 696 752 832 480 481 484 509 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
    ModeLine       "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
    ModeLine       "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
    ModeLine       "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
    ModeLine       "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
    ModeLine       "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync +vsync interlace
    ModeLine       "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
    ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
    ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
EndSection

Section "Device"
    Identifier     "nVidia Corporation NV18 [GeForce4 MX - nForce GPU]"
    Driver         "nvidia"
    BoardName      "nv"
    BusID          "PCI:2:0:0"
    Screen          0
EndSection

Section "Device"

 #                    
    Identifier     "device1"
    Driver         "nvidia"
    BoardName      "nv"
    BusID          "PCI:2:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV18 [GeForce4 MX - nForce GPU]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Virtual     1400 1050
        Depth       24
        Modes      "1152x864@75" "1280x960@60" "1024x768@43" "1280x1024@60" "1024x768@60" "1400x1050@60" "1024x768@70" "1024x768@75" "1024x768@85" "832x624@75" "800x600@60" "800x600@85" "800x600@75" "800x600@72" "800x600@56" "640x480@85" "640x480@75" "640x480@72" "640x480@60"
    EndSubSection
EndSection

Section "Screen"

 #                    
    Identifier     "screen1"
    Device         "device1"
    Monitor        "monitor1"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "640x480@60" "640x480@72" "640x480@75" "640x480@85" "800x600@56" "800x600@72" "800x600@75" "800x600@85" "800x600@60" "832x624@75" "1024x768@85" "1024x768@75" "1024x768@70" "1024x768@60" "1024x768@43" "1152x864@75" "1280x960@60" "1280x1024@60" "1400x1050@60"
    EndSubSection
EndSection

family@family-desktop:~$ 
```

---

### Post by overdrank on 2007-12-30
Ok I believe that my first post will work but you say you can not open the xorg with the gedit command?
```
gksudo gedit /etc/X11/xorg.conf
```
Edit if you cant open the gedit file then try this command
```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
``` Then restart x

---

### Post by gianthobbit on 2007-12-31
It's working!  Thanks allot for your great help.

I just did a reboot and my resolution and everything was reset, what's up with that?  Does that have anything to do with the refresh.  Come to think of it seems to do that allot after a reboot.

---

### Post by gianthobbit on 2008-01-02
Any ideas here guys?

---

### Post by overdrank on 2008-01-02
> **gianthobbit said:**
> Any ideas here guys?

HI does it do it every time you reboot the system? The only thing I can figure is if does it after a update maybe.

---

