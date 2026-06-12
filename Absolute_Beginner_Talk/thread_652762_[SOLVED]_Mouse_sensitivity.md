---
title: "[SOLVED] Mouse sensitivity"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by Shadyjames on 2007-12-29
My razer diamondback is too sensitive, and the preferences sensitivity control doesn't affect it in any way. I know this is a known issue, and that there is a fix for it that you can copy and paste into your xorg.conf, but my problem is said fix *breaks the whole system*.
After restoring my xorg.conf backup four times i've well and truly established its not just a stupid mistake on my part, but most likely a not-quite-as-stupid mistake on my part. Anybody have any help? Didn't want to necro the other thread, its like a year old and i cbf finding it again :D
In short the fix was something like

```
Section "InputDevice"
stuff
EndSection
```
And it broke everything :(

My wrists are beginning to hurt from controlling a gaming mouse on my non-gaming OS, please help before i need carpal tunnel surgery :lolflag:
Ways to make a mouse less sensitive?
Ideas?

---

### Post by Malta paul on 2007-12-29
Hi, you could try: System>Preferences>Mouse> Motion 
Hope this works :)

---

### Post by SpacePilot on 2007-12-29
Well, since you don't say what exactly you put in there that broke things it's a bit hard to give you a proper answer.

You have to keep in mind that what the gui applications do IS to edit the xorg.conf for you, so there is absolutely no reason in the world that you can not do it manually.

If I want to adjust the sensitivity "stuff" as you put it usually contain

    Option         "MinSpeed" "1.0"
    Option         "MaxSpeed" "1.0"
    Option         "AccelFactor" "0.3"
 

play around with the MinSpeed and MaxSpeed settings. 

This is what I do with a synaptics touchpad. But you didn't even say what kind of mouse you had??

Say you have a usb mouse, you probably want to skip all of that and put in:

Option "Resolution" "50"


Play around with the value until you find what you like. Default is 90 or 100 I think.

You also have the xset possibility. Then you have to read up on the xset manual

Type man xset.

Regards.

---

### Post by Shadyjames on 2007-12-29
sorry, i was a bit rushed when i posted that. Razer diamondback = USB mouse, correct. i've just found one of the two xorg.conf changes that i tried that broke my computer 

```
Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "Buttons" "7"
Option "Resolution" "1600"
Option "ZAxisMapping" "4 5"
Option "ButtonMapping" "1 2 3 6 7"
Option "Emulate3Buttons" "true"
EndSection
```

He said i could change the DPI/resolution down so that it makes my mouse less sensitive, but even without changing it it breaks the computer >_>

at the moment all of my mouse settings are loaded from the defaults and, while i thank malta for the effort, i did say that didn't work in my original post :P

Thanks for the advice spacepilot despite not having much to work with, i'll try xset now :D
This if my fourth full day of having this OS so i still don't know where those sorts of things are. Thanks again

Edit: SOLVED! YOU'RE AWESOME!
xset m 5/8 FTW!

---

