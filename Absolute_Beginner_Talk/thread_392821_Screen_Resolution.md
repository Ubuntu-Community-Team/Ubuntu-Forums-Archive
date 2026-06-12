---
title: "Screen Resolution"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by zeroo on 2007-03-25
So I just got my nvidia drivers going.  When I booted up the computers resolution is at 640x480, how do I change this?

---

### Post by taurus on 2007-03-25
You can edit /etc/X11/xorg.conf

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/X11/xorg.conf
```
and add whatever resolutions you want to use in there.

---

### Post by zeroo on 2007-03-25
I try to edit the file and it loads for a while then it just freezes not letting me move in the terminal
Any Ideas?

---

### Post by taurus on 2007-03-25
Can you post your /etc/X11/xorg.conf here?

```
cat /etc/X11/xorg.conf
```

---

### Post by zeroo on 2007-03-25
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
    Identifier     "LCD-MONITOR"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "LCD-MONITOR"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

---

### Post by taurus on 2007-03-25
How did you install nVidia driver for your graphic card since you are using it in /etc/X11/xorg.conf?

---

### Post by zeroo on 2007-03-25
I just used envy to install it.

---

### Post by david_kt on 2007-03-25
May be you could try this first:

[INDENT]sudo dpkg-reconfigure -phigh xserver-xorg[/INDENT]

And see what happen, and post again your /etc/X11/xorg.conf after executing the above command. If nothing change, may be you should reinstall your driver, using other method.

DK

---

### Post by zeroo on 2007-03-25
sudo dpkg-reconfigure -phigh xserver-xorg


worked perfectly. thanks.

---

### Post by david_kt on 2007-03-25
Glad to hear it works. But actually I am a little bit doubtful of what happen, i.e. why you need to install video driver in the first place. To check if everything really ok, could you try this command:

[INDENT]
glxinfo | grep render[/INDENT]

And then post the result here?

DK

---

### Post by zeroo on 2007-03-25
direct rendering: Yes
OpenGL renderer string: GeForce 7900 GS/PCI/SSE2/3DNOW!
    GL_NVX_conditional_render, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod,

---

### Post by david_kt on 2007-03-25
Congratulation. I think somehow it works properly now. Previously I worried the Vesa driver was loaded.

DK

---

