---
title: "right/ctrl-click mouseemu on 15'' PowerBook G4"
date: 2006-09-15
forum: Apple PPC Users
---

### Post by dizib on 2006-09-15
Hi!

I just installed Kubuntu on my 15'' PowerBook G4 and everything works amazingly well!

I just have some issues with the emulation of right-click through CTRL-click:
I followed nkbj's instructions found at the [right/ctrl-click on Mac G5, showkey]("http://ubuntuforums.org/showthread.php?t=193864") thread.
So my /etc/default/mouseemu file looks like that:
```
MID_CLICK="-middle 125 272"      # Command key + mouse click
RIGHT_CLICK="-right 29 272"      # Control key + mouse click
SCROLL="-scroll 56"              # Alt key + mouse movement
TYPING_BLOCK="-typing-block 300" # block mouse for 300ms after a keypress
```
It works perfectly with the USB mouse I have: when I CTRL-left click it's button I get the right button emulated as expected... But it doesn't work with the touchpad button!!

Here is an extract of my xorg.conf:
```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "ch"
        Option          "XkbVariant"    "fr"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
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
```
Does anybody have a clue why this mouseemu works with the USB mouse button but not with the touchpad button? What is wrong?

Another problem I have with that, is that even with the USB mouse, the scroll emulation with ALT + mouse movement doesn't work. As expected, the cursor doesn't move when holding down the ALT key, but nothing gets scrolled when moving the mouse.

Thank you for your help!

---

### Post by dizib on 2006-09-16
Ok the problem with the ALT + mouse movement for scrolling works, but only in firefox, not in KDE applications... But this is not vital.

Another problem with my touchpad is that when i double-tap it, it suddenly makes the cursor move to the top-left! Really weird! Single-tapping doesn't make it click either...

---

### Post by TomWoozle on 2007-09-16
Hi,

I also have installed mouseemu on my Powerbook Ubuntu(Feisty), and it doesn't work for for trackpad either (I've not tried a mouse).

I can only imagine this is because the code mouseemu has for a trackpad press (272) is incorrect for our machines - but I have no clue how to find out what the code should be (showkey works for keyboard, but not mouse).

Does anybody know how to find out the code, or better yet know how to make Ctrl-Click work as Right-Click for us?

Any help would be greatly appreciated! :)

---

### Post by isaacj87 on 2007-09-16
Hey guys...

Try looking at this website...This guy posted his xorg.conf for powerbook G4. If this isn't helpful, I'll try finding something else for you guys!

[Powerbook G4 on Ubuntu]("http://www.akropolix.net/rik0/blogs/2006/11/12/one-of-the-things-i-didnt-really-like-about-ubuntu-standard-configuration-was-the-track-padin-fact-although-correctly-recognized-using-the-synaptics-xorg-driver-default-was-really-poor-the-mouse-moved/")

or maybe this is helpful?

[Another Powerbook G4 xorg.conf]("http://joona.kuori.org/ubuntu-powerbook/")

I suggest these pages because it looks like your synaptics configuration look incomplete. These setups should feel more like how Mac OSX handles the touchpad.

---

### Post by TomWoozle on 2007-09-16
Hi isaacj87,

Thanks for the link - I had seen this, but it doesn't seem to help with what I want to do.

I have actually got 2 finger scrolling working (which when I finally found a good link for, was very easy!) - it is just Ctrl-Click for Right-Click that is missing.

Thanks for your efforts! Anything else you can dig up would be great. :)

---

### Post by isaacj87 on 2007-09-16
How about instead of crtl+click for right click...maybe a 3 finger tap for right click? Would that be better??

Look at this:

[http://www.popies.net/atp/]("http://www.popies.net/atp/")

---

### Post by isaacj87 on 2007-09-16
Sorry guys if none of this stuff is helpful...I'm not familiar with Macs...

---

### Post by TomWoozle on 2007-09-16
isaacj87- your help is greatly appreciated. Unfortunately, I am using 2-finger scrolling which would probably conflict with 3 finger tapping.

Ctrl-Click should be possible (and is working for a lot of people it seems).

---

### Post by isaacj87 on 2007-09-16
Hmm...okay...3 finger taping shouldn't conflict with the 2 finger scrolling...but I can check and see if I can find something to work with your Mac....

Could you give the exact model and post your xorg.conf file?

Thanks

---

### Post by isaacj87 on 2007-09-16
oh and BTW:

after installing mouseemu and adding these lines

```

MID_CLICK="-middle 125 272"      # Command key + mouse click
RIGHT_CLICK="-right 29 272"      # Control key + mouse click
SCROLL="-scroll 56"              # Alt key + mouse movement
TYPING_BLOCK="-typing-block 300" # block mouse for 300ms after a keypress
```

did you run this command?

```

sudo /etc/init.d/mouseemu start

```

I only ask because maybe mouseem isn't being invoked upon startup
Just checking. :)

---

