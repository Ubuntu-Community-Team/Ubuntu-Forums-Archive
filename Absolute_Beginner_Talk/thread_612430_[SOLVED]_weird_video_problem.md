---
title: "[SOLVED] weird video problem"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by rexxxlo on 2007-11-13
on my computer i have ubuntu on one drive and xp on the other 

xp works as well as expected???

but when i start ubuntu i get a weird resolution thing happening i toor a picture of it and used anothe machine to load it on to a photobucket account please look here

[IMG]http://i232.photobucket.com/albums/ee266/psychoacoustics/linux003.jpg[/IMG]

[IMG]http://i232.photobucket.com/albums/ee266/psychoacoustics/linux002.jpg[/IMG]

im confused i did a startup with the live d and all is fine but when i load from the hdd i get that  what can i do ?

---

### Post by rexxxlo on 2007-11-13
whoops i didnt mean to post the whole pic just the link oh well ill see what happens

---

### Post by alienexplorers on 2007-11-13
Looks like you have a refresh/resolution error.  Hit Ctrl+Alt+F1 login and enter:
> sudo dpkg-reconfigure xserver-xorg

---

### Post by FuturePilot on 2007-11-13
Can you post your xorg.conf?
```
cat /etc/X11/xorg.conf
```

---

### Post by rexxxlo on 2007-11-13
> **alienexplorers said:**
> Looks like you have a refresh/resolution error.  Hit Ctrl+Alt+F1 login and enter:

how/when do i do this when i am logging in because that is the only thing i can remotely make out on the screen .

---

### Post by rexxxlo on 2007-11-13
> **FuturePilot said:**
> Can you post your xorg.conf?
```
cat /etc/X11/xorg.conf
```

again how im sorry this is my first week of ubuntu 

i can login because i know what it is asking me but that is about it.

the mouse pointer is duplicated about 6 times along with every part of the screen i can tell what pointer to use but not what icon it is on....

---

### Post by rexxxlo on 2007-11-13
> **rexxxlo said:**
> again how im sorry this is my first week of ubuntu 

i can login because i know what it is asking me but that is about it.

the mouse pointer is duplicated about 6 times along with every part of the screen i can tell what pointer to use but not what icon it is on....

ok i got to the terminal thanks     alienexplorers

then the cat  /etc/Xll/xorg.conf

told me no such file or folder existed

---

### Post by rexxxlo on 2007-11-13
ok well that was fun ifiddled around and then couldnt get out of the terminal so i rebooted 

the system is in low resolution mode and the network card will not work now ??

---

### Post by rexxxlo on 2007-11-14
ok so the network card isnt playing nice with my router i unhooked and went direct and im back on the problem machine now

ok so what do i have to do to get better resolution im at 800x600 now?

---

### Post by rexxxlo on 2007-11-14
FuturePilot

 ok it worked here are the results

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
        Identifier      "Generic Video Cardnvidiageforce6100"
        Driver          "nv"
        BusID           "PCI:0:13:0"
        VideoRam        6400
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-100
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Cardnvidiageforce6100"
        Monitor         "Generic Monitor"
        DefaultDepth    24
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
EndSection

---

### Post by rexxxlo on 2007-11-14
i rebooted after that and everything seems fine now...

thank you

---

