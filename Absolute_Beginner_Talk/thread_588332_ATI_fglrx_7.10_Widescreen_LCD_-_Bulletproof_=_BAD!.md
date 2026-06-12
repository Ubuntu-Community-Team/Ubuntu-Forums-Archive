---
title: "ATI fglrx 7.10 Widescreen LCD - Bulletproof = BAD?!"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by myk.dinis on 2007-10-23
ATI X700
DVI Widescreen LCD 1440x900 @75 , 
Ubuntu 7.10...

Can I get some 3d love or should I just go back to using dual monitors and loving life slightly less?

I can't even get the screen to look proper...

It seems the drivers are mucked up...?? I have no idea...
I'm going to include all the EE's from X**.log and my fglrxinfo...
fglrxinfo:
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual!

There were no EE's...weird...probably because it's using the vesa driver...I'm baffled...

Bulletproof seems to hate my computer...

Can I use ATI and composite? I saw it for a second when I first tried and only had one monitor...
Then it was gone...:(

I would love some help...

Any outputs you guys need to see to help me I will produce on demand as I am constantly monitoring this board...thank you!

myk

---

### Post by sdowney717 on 2007-10-23
[http://digg.com/linux_unix/AMD_releases_new_ATI_Linux_Driver](http://digg.com/linux_unix/AMD_releases_new_ATI_Linux_Driver)

ATI is late releasing this driver. But it will be coming out.
it is not your fault.

---

### Post by misfitpierce on 2007-10-23
Install propraity driver for your ATI card by using a tool called Envy...

[http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.8-0ubuntu8_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.8-0ubuntu8_all.deb)

Try that and then restart and let it auto setup xorg... last answers should be yes and yes...

Composite = No. Not until new ATI driver releases sometime this month. ATI promises AIGLX in it which will enable compositing by default. You can create an XGL session for feisty with a guide found through google. Much easier on Gutsy atm lol. But yes try Envy for setting up grapics drivers off Vesa.

---

### Post by myk.dinis on 2007-10-23
WTF! Everytime I edit my xorg.conf it is ignored by gutsy...

It dumps me back at the bulletproof-x thing gtk-displayconfig or whatever...

I don't know why it's not loading fglrx or even if it is...

Arggh...

I can't seem to get it right...

and only in gutsy...at least with feisty if I modified the xorg by hand it would accept it...now it ignores it completely...

What info can I give you guys to give you a clue to the source of the problem...

myk

---

### Post by myk.dinis on 2007-10-23
ok...so everytime I try to modify the xorg.conf with gtk-displayconfig it asks me to restart the computer...I restart and it the process starts all over again...I used envy to install the proprietary drivers and it still doesn't like me...gahhh.

---

