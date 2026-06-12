---
title: "Screen resolution too high"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by David Miller on 2008-04-08
Hi 

I'm new to Ubuntu(7.1), only just installed it this week, and the screen resolution 1280x1084 seems to be a lot higher than the monitor can handle, while the only other option offered in the screen resolution dialog is 640X480, which is far too low. 

At the current (higher) resolution, I am having to raise the size of text on the web massively to get it readable, which is frankly, breaking the web. Things like login inputs only display the top third of text etc.

How do I go about getting an option somewhere in between? I have looked up  the previous threads on this, and although I tried to use the terminal to configure some kind of file, it just didn't work at all. This may well be because I am very new to Linux and only vaguely understood the answers posted. (Assuming that I've never gotten the command line/terminal to do anything at all other than give me an error message would be both correct, and helpful.)

Any help much appreciated

David

---

### Post by twin_57103 on 2008-04-08
Would you post some system specs?  It could have to do with your graphics card/driver.

---

### Post by David Miller on 2008-04-08
Of course, sorry.

Graphics card: Hercules 3D Prophet 9200 128MB DVI-I/TV-OUT
Processer: AMD Athlon "Barton" XP2800+ 333FSB

As for the driver, I'm afraid I don't know, or know how to find out. 

David

---

### Post by scragar on 2008-04-08
try:
```
 cat /etc/X11/xorg.conf
```
and look for the 3 sections with your graphics card, monitor and screen(do not edit the file unless you get told to!!)

- mine for example:```
Section "Device"
        Identifier      "ATI Technologies Inc ATI Default Card"
        Driver          "fglrx"
        Busid           "PCI:1:0:0"
        Option          "VideoOverlay"  "on"
        Option          "OpenGLOverlay" "off"
EndSection

Section "Monitor"
        Identifier      "NEC CI FC700"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc ATI Default Card"
        Monitor         "NEC CI FC700"
        Defaultdepth    24
        SubSection "Display"
                Modes           "1280x1024"     "1024x768"      "800x600"      "720x400"        "640x480"
        EndSubSection
EndSection
```

---

### Post by David Miller on 2008-04-08
Thanks, that gives me the following:

```
 Section "Device"
        Identifier      "ATI Technologies Inc RV280 [Radeon 9200 PRO]"
        Driver          "ati"
        BusID           "PCI:3:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-64
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc RV280 [Radeon 9200 PRO]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x400"
        EndSubSection
EndSection

```

David

---

### Post by scragar on 2008-04-08
ok, well your screen clearly supports a range of resolutions, but you are using a generic driver, so that may be the problem. Try going to
System > Administration > Restricted Driver Monitor
and seeing if there is the official driver available, that should support more modes(if that doesn't work download envy from [here](http://www.albertomilone.com/nvidia_scripts1.html) and see if that may install your graphics card.

In order for graphics card changes to take effect you will either need to restart the computer or reset the graphics layer(by pressing ctrl+alt+backspace ).

---

### Post by David Miller on 2008-04-28
Hi,

Took me a couple of weeks to properly address this as I got prompted to insert the Ubuntu 7 cd when installing Envy only to find that I'd lost it. 

I have since upgraded my Ubuntu version to Ubuntu 8, which solved that problem when i tried to install Envy. 

Unfortunately it now gives me the following when I try to install the ATI driver: 

Your graphic card has been detected as ATI Radeon 9250
Your graphic card is supported by the legacy driver
EnvyNG Error: ATI's legacy driver does not support your operating system

Any ideas as to what this means? 

Many thanks

David

---

