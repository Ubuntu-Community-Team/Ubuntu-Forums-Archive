---
title: "Nvidia legacy drivers resolution and refresh"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by getut on 2006-11-15
I am not having any luck at all with video drivers. I fought the ATI in my laptop at work for 2 days and decided to work with an old PC at home tonight.

It has a NVidia Vanta video card. I successfully have the legacy Nvidia drivers loaded and tested with glxgears but nothing I do will let me adjust the display any higher than 1024x768 at 60HZ. It is really ugly and HURTS the eyes!!!
xorg.conf file below. Please help me.
```

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
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV6 [Vanta/Vanta LT]"
    Driver         "nvidia"
    Option         "NoLogo"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV6 [Vanta/Vanta LT]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions" 
        Option  "Composite" "Disable"
EndSection
```

---

### Post by getut on 2006-11-15
Ok.. giving an update on this one in hopes someone can help. I have gone through MANY threads on this site as well as google dealing with this issue and still haven't gotten off of 1024x768@60Hz yet.

It is an Nvidia Vanta card and Dell D1226H monitor (capable of 1600x1200 @ 70Hz).

I found one thread that mentioned that there may be a bug in the Nvidia drivers that requires a metamodes option as a workaround and even that didn't help me. I try change after change most of the time causing it to even max out lower at 800x600 or not start at all, switch back to the xorg.conf above and try yet again.

I'm at a loss.

---

### Post by yurtfg89327tfg0o on 2006-11-15
Are you sure that

HorizSync       28.0 - 51.0
VertRefresh     43.0 - 75.0

are correct for your monitor?

---

### Post by getut on 2006-11-15
Thanks for the reply... I'm not really certain, but I've commented them out many times to let it autodetect and it still didn't help.

The 75 max on the vertical refresh is good for all resolutions except for 1600x1200.

I've tried many different modelines but have had varying results from barely functional to blowing up X and having to restore backed up config.

---

### Post by percival95 on 2006-11-17
I would try the manufacturers website and get the actual refresh rates and use those. That is what I had to do however I am running a different nvidia card.

---

### Post by CatKiller on 2006-11-18
> **getut said:**
> It is an Nvidia Vanta card and Dell D1226H monitor (capable of 1600x1200 @ 70Hz).

Is [this]("http://support.dell.com/support/edocs/monitors/59119/specs.htm") it? That suggests you should have ```
    HorizSync       30-95
    VertRefresh     50-160
``` in your Monitor section.

---

### Post by wcowger22 on 2007-08-08
here is my xorg.conf with resolution support up to 1280x1024 with nVidia Corporation NV6 [Vanta/Vanta LT]

and accel, Beryl or compiz does not work with this card just hangs there and tries to load.




Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load            "i2c"
        Load            "bitmap"
        Load            "ddc"
        Load            "extmod"
        Load            "freetype"
        Load            "glx"
        Load            "int10"
        Load            "vbe"

EndSection

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
        Identifier      "nVidia Corporation NV6 [Vanta/Vanta LT]"
        Driver          "nvidia"
        Busid           "PCI:1:0:0"
        Option          "NoLogo"        "True"
        Option          "AllowGLXWithComposite" "True"

EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV6 [Vanta/Vanta LT]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
        Option "Composite" "Disable"
EndSection

---

### Post by hollerith on 2007-08-09
I just picked up a bog standard Compaq Pentium 4 workstation from some company. It has the aforementioned nvidia Yanta card and I´m using the same 19"Dell monitor.  

I installed feisty and seveas-all.  Without modifying xorg, I can start beryl using the nv driver.  I get the white cube, which I can rotate with a red diamond on the top.  Its slow but not bad for 16M of card memory.  

The out of the box, fresh feisty install sets the scan rate too high 75Hz and I get loads of flicker and shadows.  Reducing this to 60Hz using screen resolution GUI helps somewhat.  

Using Envy to install the legacy nvidia drivers means I get much reduced resolution but a better picture.  However beryl will not load at all which is only slightly worse than loading with a white cube screen.  I would have assumed that I need restricted drivers to get beryl but am actually slightly worse off with them as it stands.  

I´ve searched high and low for some nvidia + beryl but I can´t seem to find and rtfm.  As you know there&#347; plenty of noise but little help.  I tried all sorts of voodoo settings XGL this, Force NVidia that.  No idea really how to make this work.  

You have dri 0666 but no dri module loaded btw.  I don´t suppose that it matters since all the faq say comment out dri and use glx instead.  Enable composite?

See I tried all [this]("http://doc.gwos.org/index.php/Latest_nvidia_feisty") and had a hell of a time recovering.  It wouldn´t load X as it couldn´t find nvidia.ko - sure none exisited but WTF not?  I installed legacy and got nvidia_new.ko .  I hacked the xorg to say nvidia_new to no effect.  I finally managed to get it started again.  I´m about to screw it up again..

---

