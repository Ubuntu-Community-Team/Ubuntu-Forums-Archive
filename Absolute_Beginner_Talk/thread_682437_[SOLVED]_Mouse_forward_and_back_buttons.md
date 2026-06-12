---
title: "[SOLVED] Mouse forward and back buttons"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by cane1832 on 2008-01-30
hello,

i have the razzor copperhead mouse and i installed ubuntu and the front and back buttons on the mouse do not work with mozilla is there a solution out there..;?

Thank you

---

### Post by LowSky on 2008-01-30
yes there is how many buttons does the mouse have if say five (left, right, forward, back, and scroll... folllow my directions


open terminal
```


sudo gedit /etc/X11/xorg.conf
```
now find this part of the coding

```
Section "InputDevice"       
 Identifier      "Configured Mouse"        
Driver          "mouse"       
 Option          "CorePointer"       
 Option          "Device"                "/dev/input/mice"        
Option          "Protocol"              "ExplorerPS/2"        
Option          "Emulate3Buttons"       "true"
EndSection
```

 change it to this

```

Section "InputDevice"        
Identifier      "Configured Mouse"        
Driver          "mouse"        
Option          "CorePointer"        
Option          "Device"                "/dev/input/mice"        
Option          "Protocol"              "ExplorerPS/2"        
Option          "Buttons"               "7"        
Option          "ZAxisMapping"          "4 5"       
Option          "ButtonMapping"         "1 2 3 6 7"        
Option          "Emulate3Buttons"       "false"
EndSection

```

then save, be carefull or you will mess up your xorg file, and then you will have to rebuild it...and that aint fun

---

### Post by cane1832 on 2008-01-30
Thank you,

I did that but dont' know where to configure what button to what and is still no working...

i appreciate your time

---

### Post by Sunflower1970 on 2008-01-30
I was able to get my side buttons working on a wireless MS Intellimouse by doing this:

```
sudo aptitude install imwheel
```

The next step was already given above

Then gedit ~/.imwheelrc
```
".*"
None, Up, Alt_L|Left
 None, Down, Alt_L|Right
  
 "(null)"
 None, Up, Alt_L|Left
 None, Down, Alt_L|Right
```

sudo gedit /etc/X11/imwheel/startup.conf
Find 
```
IMWHEEL_START=0
```
Replace with
```
IMWHEEL_START=1
```

Next:
sudo gedit /etc/X11/Xsession.d/63xmodmap
```
 killall imwheel
 xmodmap -e "pointer = 1 2 3 6 7 4 5"
 BINARY=$(which imwheel)
 $BINARY -k -p -b "67"
```

If this doesn't work replace the above with 
```
 killall imwheel
 xmodmap -e "pointer = 1 2 3 4 5 6 7"
 BINARY=$(which imwheel)
 $BINARY -k -p -b "67"
```

Then: sudo chmod 777 /etc/X11/Xsession.d/63xmodmap

Restart X.

I don't remember who posted this fix, (I saved it over a year ago) but I'm indebted to them. I only wish I could get this to work in Nautilus, or Thunar too :)

---

### Post by cane1832 on 2008-01-30
Thank you for your help its working now

---

### Post by LostMagix on 2008-02-01
I am tring to do with same thing with a rocketfish 2,4 wireless lazy USB mouse.

Nine buttons:

Rclick, Lclick, Side1, Side2, Scroll Up, Scrol lDown, Wheal Click, Wheal Left Tilt, Wheal Right Tild (it also was a button marked "dpi" in the center which in meant to switch res. profiles)

I have tried many different howto with no luck

---

### Post by jjnguy13 on 2008-02-07
> **LowSky said:**
> yes there is how many buttons does the mouse have if say five (left, right, forward, back, and scroll... folllow my directions


open terminal
```


sudo gedit /etc/X11/xorg.conf
```
now find this part of the coding

```
Section "InputDevice"       
 Identifier      "Configured Mouse"        
Driver          "mouse"       
 Option          "CorePointer"       
 Option          "Device"                "/dev/input/mice"        
Option          "Protocol"              "ExplorerPS/2"        
Option          "Emulate3Buttons"       "true"
EndSection
```

 change it to this

```

Section "InputDevice"        
Identifier      "Configured Mouse"        
Driver          "mouse"        
Option          "CorePointer"        
Option          "Device"                "/dev/input/mice"        
Option          "Protocol"              "ExplorerPS/2"        
Option          "Buttons"               "7"        
Option          "ZAxisMapping"          "4 5"       
Option          "ButtonMapping"         "1 2 3 6 7"        
Option          "Emulate3Buttons"       "false"
EndSection

```

then save, be carefull or you will mess up your xorg file, and then you will have to rebuild it...and that aint fun

Tried this, my two side buttons now work.

Thank you!

---

### Post by MattiMg on 2008-02-11
I'm having a weird problem. After installing compiz & emerald, I was messing around with the bindings and now mouse scrolling up doesn't work. But scrolling down does.. Is there a command restoring default bindings ?

---

### Post by MattiMg on 2008-02-11
Fixed, didn't see the "reset to defaults" in preferences tap

---

