---
title: "Mouse middle click configuration"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by TuZhao on 2007-07-21
Welcome to the *N*th thread about configuring a mouse.
I'll be concise: I'm kinda new to Linux, I decided to go for Ubuntu for its alleged userfriendliness but I already spent hours to configure (almost) succesfully the touchpad. Now I'm losing sleep to get the mouse work as I'd like.
I have no fancy mice with dozens of buttons, but a plain and simple USB **Logitech Pilot Wheel**mouse, with cord and ball and 2 keys + wheel.
Well, I just seem to be unable to configure the middle click to act as the *back* function, like I do in windoze. Back in the browsers, and back in the file browser. Simple as that.
I tried almost everything I googled for. **lmwheel** doesn't do the trick. It says the middle click is Button6 while **xev** says it's Button2.
A couple of *.imwheelrc* I tried:
```
"*." None,Button2,Alt_L|Left
```
```
"^Firefox-bin$" None,Left,Alt_L|Left
```
I don't even remember why I used *Left* as definition for the mouse button in the second example, it's been days since I started this chore!
My current relevant section in xorg.conf looks like this:
```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
#       Option          "Protocol"              "ImPS/2"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "Buttons"               "5"
        Option          "ButtonMapping"         "1 2 3 4 5"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "false"
EndSection
```
When I tried the following, Ubuntu would hang after the loading bar with a black screen if I booted without the mouse plugged in:
```
#Section "InputDevice"
#        Identifier    "Configured Mouse"
#        Driver        "evdev"
#       Option          "CorePointer"
#       Option        "Protocol"        "evdev"
#       Option        "Dev Name"        "Logitech USB Mouse"
#       Option        "Dev Phys"        "usb-*/input0"
#        Option        "Device"        "/dev/input/event2"
#       Option        "Buttons"        "5"
#       Option        "ZAxisMapping"        "4 5"
#EndSection

```

I'm really hating all of this. It shouldn't be so fiendishly hard making a middle click work as desired. At night I should be sleeping, not cursing at linux configuration files while drinking beer.
Please help the Ubuntu community: avoid it losing a new user ;)

---

### Post by annda on 2007-07-21
unfortunately i have an unproductive reponse: linux actually uses middle-click, it's not a gimmick like a configurable 7th button (or the 3rd button under windows). that's why it's so hard to remap it, like remapping the right-click in windows. but i'm almost sure it can be done. it's just difficult - as i said, unproductive, sorry...

---

### Post by pyros on 2007-07-21
have you looked here?
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Activate_side-mouse-buttons_in_FireFox](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Activate_side-mouse-buttons_in_FireFox)
not the side button in your case, but it might be of help.
If not, check out this post:
[http://ubuntuforums.org/showthread.php?t=316441](http://ubuntuforums.org/showthread.php?t=316441)

---

### Post by TuZhao on 2007-07-22
Thanks for the answers.
It is true that Ubuntu "sees" the middle click, in fact on the destkop I can click-drag with it and get the "move here, etc." context menu. I wonder why you can't configure it with a simple mouse control panel. That would be what people expect from a user friendly linux release!
Pyros: I saw both the links in my recent wandering around looking for solutions, but I still haven't tried the *xte / xbindkeys* way. That'll be my next (and final attempt)...

---

### Post by pyros on 2007-07-22
> **TuZhao said:**
> Thanks for the answers.
It is true that Ubuntu "sees" the middle click, in fact on the destkop I can click-drag with it and get the "move here, etc." context menu. I wonder why you can't configure it with a simple mouse control panel. That would be what people expect from a user friendly linux release!
Pyros: I saw both the links in my recent wandering around looking for solutions, but I still haven't tried the *xte / xbindkeys* way. That'll be my next (and final attempt)...

Unfortunatly, there isn't a preexisting solution;  I know it is something that has been discussed for upcomming releases, but it doesn't exist at the moment. Of course ubuntu is improving with every release, and I am certainly hopeful.

---

### Post by TuZhao on 2007-07-22
[COLOR="Red"]Solved![/COLOR] :)
Luckily **xbindkeys** saved my day, though I had to use the second method (*xte* instead of *xvkbd*).
Whoa, this time I really thought that I had to give up, but these 20 minutes' work while I was waiting for the MotoGP were worth a lot ;)

For anyone willing to bind the middle click to the back function, this is the *.xbindkeysrc* file to use:
```
"/usr/bin/xte 'keydown Alt_L' 'key Left' 'keyup Alt_L' &"
b:2
```
Put it in your home and add **xbindkeys** to the startup, et voilà (assuming that your middle button is button 2).

Well well, now I feel better about this Linux thing :D

---

