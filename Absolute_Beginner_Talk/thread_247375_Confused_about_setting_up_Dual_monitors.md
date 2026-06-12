---
title: "Confused about setting up Dual monitors"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by BigJeep on 2006-08-30
I have been searching around today trying to figure out the best way to set up dual monitors on this machine.  I have read about twinview, Xinerama, and just modifying the xorg.conf file but I havent found any articles that have made anything clear.

I have an AGP nVidia geForce 6800 and a PCI nVidia geForce 6200.  The reasoning for the 2 cards is to get digital signals to each monitor.  I have 2 samsung 930b 19" LCDs that I will be running.

Any ideas?

---

### Post by bodhi.zazen on 2006-08-30
Since no-one has answered I will take a crack.

You will need to configure X; specifically xorg.config.

First
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.org # org for origional
```

Next: Generate a working xorg.conf for each video card and monitor. You will need this information to construct a new xorg.conf

Your new xorg.conf will look something like this perhaps:
```
Section "ServerLayout"
    Identifier "Layout0"
    Screen 0 "Screen0"
    InputDevice "Mouse0" "CorePointer"
    InputDevice "Keyboard0" "CoreKeyboard"
EndSection

Section "ServerLayout"
    Identifier "Layout1"
    Screen 0 "Screen1"
    InputDevice "Mouse0" "CorePointer"
    InputDevice "Keyboard0" "CoreKeyboard"
EndSection

    Identifier "keyboard0"
    Driver  "kbd"
    Option "AutoRepeat" "500 30"
    Option "XkbModel"   "pc105"
    Option "XkbLayout"  "us"
    Option "XkbVariant" "nodeadkeys"

Section "InputDevice"
    Identifier "Mouse0"
    Driver "mouse"
    Option "Device" "/dev/mouse"
    Option "Protocol" "IMPS/2"
    Option "Emulate3Buttons" "off"
    Option "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier "Unknown" # **Put your first monitor specs here**
    VendorName "Unknown" #YOU NEED TO KNOW THIS INFORMATION
    ModelName "Unknown" #YOU NEED TO KNOW THIS INFORMATION
    HorizSync ? #YOU NEED TO KNOW THIS INFORMATION
    VertRefresh ? #YOU NEED TO KNOW THIS INFORMATION
EndSection

Section "Monitor"
    Identifier "Unknown" **# Put your second monitor specs here**
    VendorName "Unknown" #YOU NEED TO KNOW THIS INFORMATION
    ModelName "Unknown" #YOU NEED TO KNOW THIS INFORMATION
    HorizSync ? #YOU NEED TO KNOW THIS INFORMATION
    VertRefresh ? #YOU NEED TO KNOW THIS INFORMATION
EndSection

Section "Device" **# First Video card Get this information from your current xorg.conf**
    Identifier "FireGL 1000 PRO" # call it what you will.
    Driver "glint" #YOU NEED TO KNOW THIS INFORMATION
    BusID "pci:1:0:0"#YOU NEED TO KNOW THIS INFORMATION
    BoardName "Unknown"#YOU NEED TO KNOW THIS INFORMATION
EndSection

Section "Device" **# Second Video card Get this information from your current xorg.conf**
    Identifier "Voodoo" # Call it what you will
    Driver "glide" #YOU NEED TO KNOW THIS INFORMATION
    BusID "pci:0:12:0" #YOU NEED TO KNOW THIS INFORMATION
EndSection

Section "Screen"
    Identifier "Screen0"
    Device "Use first device Identifier (name)"
    Monitor "use first monitor Identifier (name)"
    DefaultDepth 16
    Subsection "Display"
       Depth 16
       Modes "1024x768"
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen1"
    Device "Use second device Identifier (name)"
    Monitor "Use second monitor Identifier (name)"
    DefaultDepth 16
    SubSection "Display"
       Depth 16
       Modes "1024x768"
    EndSubSection
EndSection
```

Well, that should be the meat and potatoes. I listed only the relevent sections, sections not listed do not need to be modified. You can likely use monitor, mouse, keyboard sections in your current xorg.conf as is.

THIS IS NOT A COMPLETE XORG.CONF FILE. USE AS A TEMPLATE FOR YOURS.

If you get up and going let me know. The mouse may be an issue. I do not know if this will work with twinview.

---

### Post by BigJeep on 2006-08-30
This is what I have so far. 

```

Section "Device"
        Identifier      "n6800"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Screen          0
EndSection

Section "Monitor"
        Identifier      "monitor0"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Device"
        Identifier      "n6200"
        Driver          "nvidia"
        BusID           "PCI:0:9:0"
        Screen          1
EndSection

Section "Monitor"
        Identifier      "monitor1"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "screen0"
        Device          "n6800"
        Monitor         "monitor0"
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
EndSection

Section "Screen"
        Identifier      "screen1"
        Device          "n6200"
        Monitor         "monitor1"
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
EndSection

Section "ServerFlags"
        Option "Xinerama"       "true"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen 0        "screen0" 0 0
        Screen 1        "screen1" RightOf "screen0"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

This is the error I am getting

```

(WW) NVIDIA: No matching Device section for instance (BusID PCI:0:9:0) found

```

---

### Post by BigJeep on 2006-08-31
After fooling around with it for a while, cpugeniusmv figured it out for me.

This is my working xorg.conf file

```

Section "Device"
        Identifier      "n6800"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "monitor0"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Device"
        Identifier      "n6200"
        Driver          "nvidia"
        BusID           "PCI:0:9:0"
EndSection

Section "Monitor"
        Identifier      "monitor1"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "screen0"
        Device          "n6800"
        Monitor         "monitor0"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
                ViewPort        0 0
        EndSubSection
EndSection

Section "Screen"
        Identifier      "screen1"
        Device          "n6200"
        Monitor         "monitor1"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
                ViewPort        0 0
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "screen0"
        Screen          "screen1" Rightof "screen0"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

It was modeled from the following howto:

[http://tldp.org/HOWTO/Xinerama-HOWTO/xf86config.html](http://tldp.org/HOWTO/Xinerama-HOWTO/xf86config.html)

---

### Post by bodhi.zazen on 2006-08-31
Nice!! Nice Link.

Is it working?

Are you using Twinview?

Do you need help configuring the mouse? i.e. Can you move the mouse between the two monitors?

---

### Post by BigJeep on 2006-08-31
> **bodhi.zazen said:**
> Nice!! Nice Link.

Is it working?

Are you using Twinview?

Do you need help configuring the mouse? i.e. Can you move the mouse between the two monitors?

Its working great, we didn't use twinview because that is primarily for doing 2 monitors from 1 GPU.  I left the mouse settings and everything else alone and it works great.

---

### Post by bodhi.zazen on 2006-08-31
Thank you for posting you solution. Sorry My suggestion was so far off.

---

