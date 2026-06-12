---
title: "NVIDIA driver destruction"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by ~chinook~ on 2007-11-07
I have wrecked my driver. It says that the restricted drivers are installed, but the are not working. I tried to use envy. However, that just made things worse. So, if someone has a guide to remove and reinstall the drivers I will be very happy.

---

### Post by Hospadar on 2007-11-07
what exactly is wrong?
what error messages are you getting?
Also what hardware are you using?

Also, what exactly did you do when you used envy.

Furthermore, could you attatch a copy of your /etc/X11/xorg.conf file or post the terminal output of "cat /etc/X11/xorg.conf"

---

### Post by ~chinook~ on 2007-11-07
The driver is not loaded. IE no compiz fusion no games. No 3d acceleration.
I was trying to upgrade my drivers as I was getting an error with the Enemy Territory quake wars demo. That didn't work so I tried to do a clean with envy. Now this is where I am.

8600gt

---

### Post by ~chinook~ on 2007-11-07
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "nVidia Corporation NVIDIA Default Card"
        Driver          "nv"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-64
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NVIDIA Default Card"
        Monitor         "Generic Monitor"
        DefaultDepth    16
        SubSection "Display"
                Modes           "1280x1280"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

---

### Post by ~chinook~ on 2007-11-07
updated xorg

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
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
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
    HorizSync       28.0 - 64.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1280x1280"
    EndSubSection
EndSection
  

Still no worky with driver install. Can't enable desktop effects or anything needing 3d acceleration.

---

### Post by ~chinook~ on 2007-11-07
chinook@chinook-laptop:~$ glxinfo | grep rendering
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".


So acceleration isn't working, but driver is installed.

---

### Post by ~chinook~ on 2007-11-08
Anyone?

---

### Post by ~chinook~ on 2007-11-08
I hate to bump threads, but I am getting no help thus far.

---

### Post by ~chinook~ on 2007-11-08
So, shall I reinstall?

---

### Post by forestpixie on 2007-11-08
i did [this]("http://ubuntuforums.org/showpost.php?p=3725041&postcount=11") 

don't know if it'll work for you

---

### Post by Maestro23 on 2007-11-08
> **forestpixie said:**
> i did [this]("http://ubuntuforums.org/showpost.php?p=3725041&postcount=11") 

don't know if it'll work for you

Getting ready to post that forest.:)

---

### Post by forestpixie on 2007-11-08
...the other thread got closed :) - nice thread to read though I like that ff tool - installed that now. Seems to be a general reluctance to search I'd say - the thread I posted it in was only yesterday. Best stop or I'll get a slapped wrist.

---

### Post by ~chinook~ on 2007-11-09
I followed all of those steps, but still have the problem with no video driver being used.

---

### Post by forestpixie on 2007-11-09
when you restarted did you get the 'gutsy is starting with default' or similar?

Did it start with 800x600?

---

### Post by ~chinook~ on 2007-11-09
It starts with a message saying it can't detect the video driver and it loads up the vesa ones.

---

### Post by forestpixie on 2007-11-09
and once you're in - what does restricted driver manager say?

 or does it say it's enabling and download/install the driver and then put you right back where you started?

---

### Post by ~chinook~ on 2007-11-09
after I cleared everything restarted, then reinstalled the modules it shows the nvidia driver not in use. I then install the nvidia drivers and resart. Upon restart it says going into low graphics mode can't detect display. If I go into restricted drivers it says they are installed. However, running nvidia-settings says that "You don't appear to be using the nvidia X driver. And if I run glx info I get no 3d rendering.

---

### Post by forestpixie on 2007-11-09
have you tried setting the driver in system  >admin > screens and graphics

or maybe try installing from the nvidia download,

can't suggest anything else I'm afraid, once I'd uninstalled and reinstalled everything was fine for me

---

### Post by ~chinook~ on 2007-11-09
Nope. That didn't help at all either. I select NVIDIA, but on reboot VESA gets loaded again. And the low graphics screen comes back again.

---

