---
title: "Ubuntu Startup Resolution Stuck at 640x480"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by princeofhosts on 2007-03-16
Good morning,

I just made the switch to Ubuntu/Beryl this past weekend from Vista, I love it dearly.  However, a problem has started...

...whenever I restart my PC, I am forced back into a 640x480.

When I type in "cat /etc/X11/xorg.conf"

I get this:

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

        # path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 32.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "640x480"
    EndSubSection
EndSection


My normal resolution should be 1280x720, but it keeps resetting after I restart my PC.  I can normally reset it back once I log in via the nVidia settings but this is a hassle for me.

Also, I am unable to stream live video...how do I do such?  I normally used WMP11 on Vista or iTunes/Quicktime on my Apple, but I use VLC from time to time...which is the best media player for Linux?

Thank you.

---

### Post by qpwoeiruty on 2007-03-16
Under "Depth 24" at the bottom of the file, try changing "Modes "640x480"" to "Modes "1280x720""

---

### Post by princeofhosts on 2007-03-16
> **qpwoeiruty said:**
> Under "Depth 24" at the bottom of the file, try changing "Modes "640x480"" to "Modes "1280x720""

How do I do such?

---

### Post by qpwoeiruty on 2007-03-16
> **princeofhosts said:**
> How do I do such?

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf

```

The first line makes a backup of your xorg.conf file and the second opens it in an editor. After that, just scroll to the bottom and make the amendment. GL!

---

### Post by wpshooter on 2007-03-16
use - 

sudo gedit /etc/X11/xorg.conf

I would suggest that you save the original file under another name before you start editing it.

Good luck.

---

### Post by princeofhosts on 2007-03-16
Ah sweet, I tried restarted with Ctrl+Alt+BackSpace and it worked.

Thankies, ah...about the streaming video?

---

### Post by qpwoeiruty on 2007-03-16
> **princeofhosts said:**
> Ah sweet, I tried restarted with Ctrl+Alt+BackSpace and it worked.

Thankies, ah...about the streaming video?

What kind of streaming video? Flash (like YouTube), Shoutcast's nsv streams (those listed in Winamp), or what?

---

### Post by AndyCooll on 2007-03-16
Just to clarify a bit further, gedit is a text editor so you are going to manually add "1280x720" in front of each occurrence of "640x480" (leave a space in between the two settings).

Each of my lines for instance now reads something like:
Modes "1280x720" "1024x768" "800x600" "640x480"

:cool:

---

### Post by princeofhosts on 2007-03-16
> **qpwoeiruty said:**
> What kind of streaming video? Flash (like YouTube), Shoutcast's nsv streams (those listed in Winamp), or what?

Well I got YouTube running, but if I want to stream live video, it won't let me...
...what do I use in replacement of WMP and Quicktime?

---

### Post by princeofhosts on 2007-03-16
> **AndyCooll said:**
> Just to clarify a bit further, gedit is a text editor so you are going to manually add "1280x720" in front of each occurrence of "640x480" (leave a space in between the two settings).

Each of my lines for instance now reads something like:
Modes "1280x720" "1024x768" "800x600" "640x480"

:cool:

Oui, I replaced every single 640x480 to 1280x720.  It should be better now?

---

### Post by qpwoeiruty on 2007-03-16
Changing them all is good. If you ever wanted a lower color depth, the 1280x720 will stick to those too. You could have also added the 1280x720 in front of the 640x480 entries instead of replacing them, but it's no problem if it's not there.

As for streaming, you may need to install the codecs if you haven't done so yet: [here](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Multimedia_Players_.26_Browser_Plug-ins)
and playing streaming video in the browser:

```
sudo apt-get install mplayer mozilla-mplayer
```

---

