---
title: "help me.  video quality."
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by je.famous chief on 2008-03-08
i'm new.  quality on videos and dvds on full screen is pretty nasty.  i usually get a big line going diagonally across the screen.  

I know this has been asked before and i came across this tread.
[http://ubuntuforums.org/showthread.php?t=692827](http://ubuntuforums.org/showthread.php?t=692827)
I really don't know what that means.  Xorg.conf?  what? 

i set a lot of stuff before i went on a long vacation.  now back to square one.  i'm stuck.  


I know i'm not giving enough details, so let me know what information you need to help me with this.  i'm determined to learn this stuff.  I should get it eventully.  help me.  
thanks.

---

### Post by halitech on 2008-03-08
what program are you using to play the videos and dvds? are the dvds commercial dvds or burned ones?

---

### Post by je.famous chief on 2008-03-08
VLC player i usually use.  But they all seem to do the same stuff.  theres are commercial dvds.

---

### Post by halitech on 2008-03-08
you don't notice the line in any other application? could be something to do with codecs although normally vlc doesn't need them ...

---

### Post by je.famous chief on 2008-03-08
good point.  the video is just ugly either way.  i get the line, or grainy nasty video.  It completely gave up when i tried to play the planet earth dvd.  
i have put on the Xserver a while ago.  would that hurt this?  i tried to look at the nvidia driver and the  it told me that it wasn't in use.

---

### Post by je.famous chief on 2008-03-08
and i know it really doesn't sound like i know what i'm talking about.  i don't know what i'm talking about.  i have done a lot of really nice things to this without really knowing how.

---

### Post by halitech on 2008-03-08
what video card and monitor do you have and what resolution are you running at?

don't worry about not knowing what you are talking about, we all start somewhere and its the same place for all of us, just some started earlier then the rest of us :)

---

### Post by je.famous chief on 2008-03-08
what would be the best way to figure that all out?

---

### Post by Nythain on 2008-03-08
you can either type
```

cat /etc/X11/xorg.conf

```in a terminal and paste the contents here in a code tag
or open gedit and open file /etc/X11/xorg.conf
and copy paste the contents of the file here in code tag

xorg.conf is the configuration file for your xserver-xorg, basically X wich is responsible for all the pretty GUI'ness on your computer...
in it, you tell xorg what video driver to use, where the video card is, what monitor you have, its vert and horizontal refresh rates and a whole lot of other info... pretty nifty file, and the first actuall configuration file i familiarized myself with in linux/ubuntu...

once we have its contents, we can see if its a poorly configured usage of either the nv or nvidia driver or go from there to look for other possibilities...

VLC usually doesnt require any extra "codecs" just to play video files of any type, its very smart like that, so codecs more than likely arent the immediate problem, though the video output you are telling VLC to use (ie xv, opengl, etc) might be the problem

EDIT: one more question, do you have "desktop effects" turned on, or compiz installed at all???

---

### Post by je.famous chief on 2008-03-08
```
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
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "stylus"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "eraser"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "cursor"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "nVidia Corporation NV34M [GeForce FX Go5200 64M]"
        Driver          "nvidia"
        Busid           "PCI:1:0:0"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        Horizsync       28-64
        Vertrefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV34M [GeForce FX Go5200 64M]"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Modes           "1280x800"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
        Inputdevice     "Synaptics Touchpad"
EndSection
Section "Module"
        Load            "glx"
EndSection

```

and, i had the desktop effects on '"custom" but i recently turned that off to see if it would make a difference.  wobbly windows is pretty nice.

---

### Post by halitech on 2008-03-08
are you using a widescreen lcd?

---

### Post by je.famous chief on 2008-03-08
yes.

---

### Post by halitech on 2008-03-08
ok, was wondering when I saw the resolution of 1280x800. I wonder if its something oto do with the horizontal and vertical rates, they seem a little low to me for an LCD

---

