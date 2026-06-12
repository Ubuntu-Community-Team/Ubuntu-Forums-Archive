---
title: "Left click on MacBook"
date: 2007-05-06
forum: Apple Intel Users
---

### Post by RelativelyQuantum on 2007-05-06
Hi all.

 Just wondering about the compatibility of Ubuntu features on an apple MacBook. I'm thinking about buying one, and wondered how I could access the right-click menus with only one button. Copy/paste would be no problem using Edit or keyboard commands, but I'm not sure how I would add to my panels, change my wireless network in roaming mode, etc. If anyone could give me some feedback I would really appreciate it.

---

### Post by The_Giver on 2007-05-06
> **RelativelyQuantum said:**
> Hi all.

 Just wondering about the compatibility of Ubuntu features on an apple MacBook. I'm thinking about buying one, and wondered how I could access the right-click menus with only one button. Copy/paste would be no problem using Edit or keyboard commands, but I'm not sure how I would add to my panels, change my wireless network in roaming mode, etc. If anyone could give me some feedback I would really appreciate it.

There are tools like QSynaptics and GSynaptics which allow you to configure your trackpad for right clicks...... I have mine set to be two finger tap on the trackpad.

---

### Post by eldepeche on 2007-05-06
I didn't like the way gsynaptics worked, but you can also use an .xmodmap file to map keys to mouse buttons. For example, on my US keyboard, I have the right apple key as a middle button and the enter key as a right button.

---

### Post by benanzo on 2007-05-06
by default Ubuntu sets F11 as middle click and F12 as right-click --the giant button by the touchpad is Left-click(obviously)

Here's my script for making the right Apple key left-click and the lower Enter key delete.
By default the upper "delete" key is backspace and Fn+"delete" is delete.

```

#!/bin/bash
#
# Configures Macbook's right apple key to be right mouse-click
# and lower enter key to be delete.
# Install xkbset (sudo apt-get install xkbset).
# Copy this script to ~/bin/macbook (or wherever you put your scripts)
# set GNOME to run it at login.

xmodmap -e 'keycode 116 = Pointer_Button3'
xmodmap -e 'keycode 108 = Delete'
xkbset m

```

---

### Post by eldepeche on 2007-05-06
> **benanzo said:**
> by default Ubuntu sets F11 as middle click and F12 as right-click --the giant button by the touchpad is Left-click(obviously)

Here's my script for making the right Apple key left-click and the lower Enter key delete.
By default the upper "delete" key is backspace and Fn+"delete" is delete.

You could also put the following in a file called .xmodmap in your home directory:
```
keycode 116 = Pointer_Button3
keycode 108 = Delete

```
Then after that, when you log into Gnome, it will ask you the first time if you want to load the .xmodmap file, and after that, it won't ask again, and it will be loaded automatically.

You also have to turn on mousekeys in the keyboard accessability preferences.

---

### Post by danilo666 on 2007-05-07
I've found somewhere this configuration for xorg.conf for the synaptic driver, which gives you all of the features the MAC OS X fives plus some extra.

I mean double-fingers scroll, two-fingers tap => middle button three-fingers tap => left button etc.

in the xorg.con file, you may find a section "InputDevice"  with identifier "synaptics"

this is how I got everything to work, write this in the /etc/X11/xorg.conf at the right place

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "CorePointer"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "LeftEdge"              "100"
        Option          "RightEdge"             "1120"
        Option          "TopEdge"               "50"
        Option          "BottomEdge"            "310"
        Option          "FingerLow"             "20"
        Option          "FingerHigh"            "30"
        Option          "MaxTapTime"            "150"
        Option          "MaxTapMove"            "220"
        Option          "MaxDoubleTapTime"      "180"
        Option          "VertScrollDelta"       "25"
#       Option          "HorizScrollDelta"      "30"
        Option          "VertTwoFingerScroll"   "true"
#       Option          "HorizTwoFingerScroll"  "true"
#       Option          "FastTaps"              "true"
        Option          "TapButton2"            "2"
        Option          "TapButton3"            "3"
        Option          "MinSpeed"              "0.79"
        Option          "MaxSpeed"              "0.88"
        Option          "AccelFactor"           "0.015"
        Option          "SHMConfig"             "on"
EndSection


for the admins: maybe you should add this to the wiki page for the macbook, as I see a lot of people wondering how to do such things, and everyone is providing half-solutions, or are referring to some apps to solve the problem.

hope this help

danilo.

---

### Post by RelativelyQuantum on 2007-05-08
Thanks alot you guys, this really helps. I wasn't sure weather it was possible, but I see now that it's fairly straightforward to overcome the problems. That's a big load off my mind; now I can enjoy the benefits of Apple *and* Ubuntu. :)

---

### Post by frafu on 2007-07-16
Hello, 

An utility to open the contextual menu with a left click&hold is under development. It also has other features, is called mousetweaks and the contextual menu function can be activated under the 'delay click' tab. 

You can find the current version in [this thread]("http://ubuntuforums.org/showthread.php?t=494037"). But you have to compile it yourself; I am not able to build a debian package for this architecture, as I don't have a Mac with Ubuntu running on it. 

Any feedback will be appreciated. 

Francesco

---

### Post by Gen2ly on 2007-07-17
Thanks for the suggestions, these methods is much nicer than editing the mac_hid in /proc.  Anyone here attempted frafu's app?

---

### Post by frafu on 2007-07-17
Hello, 

I am satisfied by it (running it on a i386; not mac), though it has two points that might be disturbing for a newcomer: 

- in linux a right click on the scrollbutton moves the page to the extremity; as the left click&hold sends a right click if the pointer does not move after a certain delay, the page scrolls the the extremity. I simply use the scrollbar instead of the scrollbutton. Another workaround is to move the pointer away from the scrollbutton; it is not as practical, but the page continues to scroll

- you have to avoid to do a click&hold on the titlebar of a window without moving the pointer, otherwise the window will be moved to the upper left corner (this is a sideeffect of the implementation of the function) 

The developer knows about these two points... 

Thanks in advance for any comments. 

Francesco

---

### Post by thonuz on 2007-07-17
Ive never had F11 or F12 do right and middle by default so maybe the setup is different for different macbooks. Mine is core 2 duo. One Feisty it just worked fine by 3 finger tap on touchpad. I'm now running gutsy and have configured nothing but wireless and i915. Everything else I need works. In fact in OSX there is more effort required to do simple things so I gave up on it. I think osx is really over-rated.

---

### Post by Gen2ly on 2007-07-18
i think so as well.  I tried mapping the control key to Super_L (left Apple).  xev actually shows it as the control keycode but it looks as if it is not possible to be used in combination with another keypress.  Seems to me someone else earlier tried to do this...

---

