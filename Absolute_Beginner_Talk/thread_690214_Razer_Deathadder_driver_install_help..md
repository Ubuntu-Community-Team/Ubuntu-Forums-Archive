---
title: "Razer Deathadder driver install help."
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by Calibre on 2008-02-07
Hi, could someone please help me with installing the DeathAdder driver/GUI tool, I'd like a step by step guide on how to do this if possible, this would help other people trying to install too. 

I've checked all the posts here regarding this and couldn't find a easy way to do it, and I havn't found any infomation on the new GUI tool. I've already setup my xorg.conf, here's what i've done so far.

> Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "Name" "Razer DeathAdder"
    Option         "Vendor" "Razer"
    Option         "CorePointer"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Device" "/dev/input/mice"
    Option         "Buttons" "7"
    Option         "ButtonMapping" "1 2 3 6 7"
    Option         "Resolution" "900"
    Option         "SampleRate" "1000"
EndSection

Also every post i've read here about setting up xorg.conf for razer mice say to set "SampleRate" to "1000Hz" or whatever Hz you need that is compatible for your mouse, I have tried "1000Hz" and got a (WW) warning error in the xorg.conf log "var/log/Xorg.0.log" saying that "SampleRate" needs to be an _Integer_ this is the error:

> (WW) Option "SampleRate" requires an integer value

So i've change it to "1000" without the "Hz" the mouse is now smoother and the log now reads..

> (**) Option "SampleRate" "1000"
(**) Configured Mouse: SampleRate: 1000

Here are links for the driver and gui tool that i'm trying to install:

Driver: [http://bu3sch.de/deathadder.php]("http://bu3sch.de/deathadder.php")
GUI Tool: [http://bu3sch.de/razercfg.php]("http://bu3sch.de/razercfg.php")

I'm not sure if I need both or just the new GUI tool.

Cheers :)

---

### Post by matthodge on 2008-02-09
I'm using a RazorCopphead (which I know doesn't have the 3G Sensor) but in my xorg config I didn't define the SampleRate. Here is my xorg config section for the mouse.

```
Section "InputDevice"

   Identifier     "Configured Mouse"
   Driver         "mouse"
   Option         "CorePointer"
   Option         "Device" "/dev/input/mice"
   Option         "Protocol" "ExplorerPS/2"
   Option         "Buttons" "7"
   Option         "Resolution" "2000"
   Option         "ZAxisMapping" "4 5"
   Option         "ButtonMapping" "1 2 3 6 7"
   Option         "Emulate3Buttons" "true"
EndSection
```

For me having ultra high sensitivity isn't an issue as I'm not doing gaming under linux, I just want access to all the buttons on the mouse. So leaving the sample rate out is probably ok.

---

### Post by Calibre on 2008-02-10
Yeah, leaving "SampleRate" out would be fine it'll just be set to default. If you don't need the 1000Hz "Ultrapolling", I didn't use it on my old Diamondback Plazma.

Although i'd recommend setting "xset m 0 0" on startup to get rid of mouse accel in desktop, because I can imagine 2000dpi with acceleration to be crazy :)

But suppose it's personal preference as I dont really like 1600dpi on my mouse it's to sensitive for me in XP and Openbox/Xfce, I just set it to 900dpi in windows which saves it to mouse in a profile and then also in Xorg.conf to get slower controlable mouse speed. but I also game with low sens @ 450dpi or 900dpi.

EDIT: Also only use "Emulate3Buttons" "true" if you want leftclick+rightclick to act like middleclick.

---

