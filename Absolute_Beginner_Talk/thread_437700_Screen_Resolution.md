---
title: "Screen Resolution"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by KenR on 2007-05-09
Hi!

Hope someone can help me with this small but important issue... :mad: 

Have just installed Ubuntu and got it online after some trouble.
Now my screen resolution is set to 640x480 witch is only half of what I want.

The resolution was set to 1280x1024, but now I cant get it back.... :confused: 

Help pls...!

---

### Post by ramjet_1953 on 2007-05-09
Laptop, deskop, brand name?

Video card, brand name?

It's a bit hard to help if you don't tell us what's under the hood!

Regards,
Roger :cool:

---

### Post by Schalken on 2007-05-09
In case you hadn't already tried, you can change the screen resolution in sys>prefs>screen res

---

### Post by MrPyro321 on 2007-05-09
Have you tried changing the screen resolution?
System> Preferences> Screen Resolution

I also found this:

[http://ubuntuforums.org/showthread.php?t=246988](http://ubuntuforums.org/showthread.php?t=246988)

---

### Post by KenR on 2007-05-09
How do I edit the xorg.conf file?
Get it opened, but I am not allowed to save it....

:popcorn:

---

### Post by KenR on 2007-05-09
ok - open it in terminal as SU and that did the trick!

Thanks guys! :guitar: 

kenji

---

### Post by J_A on 2007-05-09
hi all of ya,

so, I've installed ubuntu & kubuntu on my dell inspiron 6400 and so far things seem to be working well and I will freely admit I'm already falling in love with linux. however, there's this screen res problem.

my screen should have a res of 1280x800 & I have the ATI mobility graphics card. ubuntu only sees 1024x800 and that's the highest res I'm able to get. I tried editing the xorg.conf file and there, it shows the options (like someone already posted in this thread), yet I can't set it to this.

I've just looked at the ddcprobe file, here are its contents:

"vbe: VESA 3.0 detected.
oem: ATI ATOMBIOS
vendor: (C) 1988-2005, ATI Technologies Inc.
product: M54P 01.00
memory: 16384kb
mode: 640x400x256
mode: 640x480x256
mode: 800x600x256
mode: 1024x768x256
mode: 1280x1024x256
mode: 132x25 (text)
mode: 132x43 (text)
mode: 640x480x32k
mode: 640x480x64k
mode: 640x480x16m
mode: 800x600x32k
mode: 800x600x64k
mode: 800x600x16m
mode: 1024x768x32k
mode: 1024x768x64k
mode: 1024x768x16m
mode: 1280x1024x32k
mode: 1280x1024x64k
mode: 1280x1024x16m
mode: 320x200x32k
mode: 320x200x64k
mode: 320x200x16m
mode: 1600x1200x256
mode: 1600x1200x32k
mode: 1600x1200x64k
edid:
edid: 1 3
id: a900
eisa: LPLa900
serial: 00000000
manufacture: 0 2006
input: analog signal.
screensize: 33 21
gamma: 2.200000
dpms: RGB, no active off, no suspend, no standby
dtiming: 1280x800@60
dtiming: 1280x800@60"
and then the monitorid follows

are there other edits I can make to the xorg.config file so it accepts the change?

can anyone offer more advice on this?

thanks

---

### Post by J_A on 2007-05-09
anyone? do I have to open a new thread on this?

---

