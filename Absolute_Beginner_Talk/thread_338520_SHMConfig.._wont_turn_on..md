---
title: "SHMConfig.. wont turn on."
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by astrogiblet on 2007-01-14
Ok.. I'm trying to get my touchpad to turn off on my laptop. 

I've followed at least 5 different guides, and they all tell me to go to:

/etc/X11/xorg.conf

And put the following in (this is a direct copy from my xorg.conf file):

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "on"
EndSection


And then save and exit.. which I've done like 4 times now.. With both nano and gedit... And yet, I try to do:

synclient TouchpadOff=1

And it gives me the following error:
Can't access shared memory area. SHMConfig disabled?

I'm running Dapper Drake w/ Kubuntu KDE Desktop if that matters.

Does anybody know whats wrong? 


Thanks.

---

### Post by astrogiblet on 2007-01-15
Can anybody help me?

---

### Post by jordanmthomas on 2007-01-15
Probably a stupid question, but have you tried restarting X?  If you haven't, you need to
```
(ctrl-alt-backspace)
```
*note, all your programs will close, so save your work first

---

### Post by astrogiblet on 2007-01-15
No, I havent yet, but one of the guides I was reading said "We do it this way so we can avoid having to restart x."


Argh. 

Haha. I'll try that next. I'll let you know how that goes. :)


Thanks.

---

### Post by astrogiblet on 2007-01-15
Ok. That worked great. Thanks :)



-Brandon

---

