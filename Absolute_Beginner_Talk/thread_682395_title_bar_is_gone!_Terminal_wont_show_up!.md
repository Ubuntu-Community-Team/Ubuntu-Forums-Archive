---
title: "title bar is gone! Terminal wont show up!"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by rnazario on 2008-01-30
The title bar is gone guys, I cannot resize, move, minimize or anything without going to the tab, right clicking on it and selecting the feature.No title bar... I need to figure out how to fix this... I have tried metacity --replace and emerald --replace but all metacity --replace does is revert everything back to no effects (granted it does bring back my bar but the effects are my favorite part of Ubuntu). emerald --replace does nothing. Granted all of these things are being typed using the ALT + F2 due to the fact that any time I pull my terminal all i get is this white square where my terminal should be... so to recap, no title bar and no terminal... please help. 

P.S. if at all possible try to dumb down the answers as much as possible, I am completely new to anything Linux related. Thank you in advance for all of your help :)

---

### Post by asmoore82 on 2008-01-30
you just answered your own question...
some combination of your hardware and/or software settings makes "Desktop Effects" unstable;
I know that using them with Intel graphics chipsets
is hit and miss but nVidia "Just Works!"

---

### Post by jaytek13 on 2008-01-30
From my limited understanding of this, it is actually compiz that acts as the window manager, not emerald, so you would have to do a compiz --replace... But again, I'm not terribly familiar.

---

### Post by rnazario on 2008-01-30
> **asmoore82 said:**
> you just answered your own question...
some combination of your hardware and/or software settings makes "Desktop Effects" unstable;
I know that using them with Intel graphics chipsets
is hit and miss but nVidia "Just Works!"

My computer is a P4 with a nvidia Gforce 3 TI 200... everything was working fine before and then I restarted, that is when it started acting funky...

---

### Post by lswest on 2008-01-30
occasionally, when i'm using emerald for title bars/window borders, they just disappear, and usually return after a restart/restarting X server.  Sometimes not, then i just disable all emerald themes, and disable desktop effects, restart, re-enable, and it all works for me (using an Nvidia MCP67M) but seeing as i hardly have that happen, never looked into a permanent fix.

---

### Post by rnazario on 2008-01-30
> **jaytek13 said:**
> From my limited understanding of this, it is actually compiz that acts as the window manager, not emerald, so you would have to do a compiz --replace... But again, I'm not terribly familiar.
I just tried a compiz --replace, my screen flashed but when it came back it was the same...

---

### Post by bumanie on 2008-01-30
This code should work
> sudo nvidia-xconfig --add-argb-glx-visuals -d 24
If you have a nvidia graphics card. I'm not sure how to do it for an ati card if that's what you have.

---

### Post by Sidewinder1 on 2008-01-30
I had *exactly* the same symptoms with the Title Bars and the Terminal that you describe. Not sure how or why it happened. The way I fixed it was to go to my Nvidia Restricted Driver, that I was using, disable it then re-enable it, reboot. Problem solved. Hope it works for you.

---

### Post by Flyingjester on 2008-01-30
try alt f2, metacity --replace, if your titlebars come back, it's compiz's fault.

---

### Post by asmoore82 on 2008-01-30
> **rnazario said:**
> My computer is a P4 with a nvidia Gforce 3 TI 200... everything was working fine before and then I restarted, that is when it started acting funky...

are you using the official "Restricted Driver" on Gutsy(Ubuntu 7.10)?

---

### Post by antisocialist on 2008-01-30
this is due to compiz being unstable, a great fix to this is to replace compiz with beryl. to do this run the following commands
be sure to disable desktop effects first and then run them in the terminal.
```
sudo aptitude install beryl
sudo aptitude remove compiz

```

once this is finished press ctrl+alt+bksp
log in

go to applications>system tools> beryl manager

you will get a red ruby in the tray, right click it and select beryl for window manager (this will enable desktop effects) and for window decorator select compiz gtk (if you want to use emerald then go ahead, but that will probably result in no titlebar)

enjoy

---

### Post by rnazario on 2008-01-30
ok thanks I will try all of those suggestions when I get home (im in class right now). thanks again for the responses, I will let you guys know how it goes.

---

### Post by jordanmthomas on 2008-01-30
Sounds like you need to run with indirect rendering.  I have to on my Intel chip or windows don't update themselves.
```
compiz --replace --sm-disable --ignore-desktop-hints ccp --indirect-rendering
```

---

### Post by oedha on 2008-01-30
I am using Intel 915mobile.....
fresh compiz installation just fine....
now i have autumn, 3d, snow and atlantis run well
but everytime i restart....the title bar, menu bar were missing and i just faced the walpaper.......
i dont need to be busy with this because after i rotate the cube ( ctrl+alt+mouse drag) everything back to normal........

regards;
~E~

---

### Post by pijits on 2008-01-30
It might be your visual effects, i know i had a similar problem because of my vid card drivers.

Try right clicking on your desktop. 

Clicking Change Desktop Picture.

Go to the Visual Effects tab.

Then select none and see if that helps.

---

### Post by rnazario on 2008-01-31
> **antisocialist said:**
> this is due to compiz being unstable, a great fix to this is to replace compiz with beryl. to do this run the following commands
be sure to disable desktop effects first and then run them in the terminal.
```
sudo aptitude install beryl
sudo aptitude remove compiz

```

once this is finished press ctrl+alt+bksp
log in

go to applications>system tools> beryl manager

you will get a red ruby in the tray, right click it and select beryl for window manager (this will enable desktop effects) and for window decorator select compiz gtk (if you want to use emerald then go ahead, but that will probably result in no titlebar)

enjoy

I tried this and the only problem was that under the applications tab there is no system tools...

---

### Post by rnazario on 2008-01-31
> **pijits said:**
> It might be your visual effects, i know i had a similar problem because of my vid card drivers.

Try right clicking on your desktop. 

Clicking Change Desktop Picture.

Go to the Visual Effects tab.

Then select none and see if that helps.

It does and thats great and all but i dont get any of my neat effects at that point, which saddens me.

---

### Post by rnazario on 2008-01-31
> **jordanmthomas said:**
> Sounds like you need to run with indirect rendering.  I have to on my Intel chip or windows don't update themselves.
```
compiz --replace --sm-disable --ignore-desktop-hints ccp --indirect-rendering
```

When I type that in the terminal, i get this:

raul@Raul-Linuxdesktop:~$ compiz --replace --sm-disable --ignore-desktop-hints ccp --indirect-rendering
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0201 (rev a3) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1360x768) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (resizeinfo) - Warn: Bind Pixmap to Texture failure
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (resizeinfo) - Warn: Bind Pixmap to Texture failure
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32

All of my effects come back but still no title bar...

---

### Post by rnazario on 2008-01-31
Ok guys I finally got it to work. I uninstalled my nvidia drivers restarted, installed them, restarted, and everything worked great (hopefully it stays that way. Thank you all for your suggestions and help! :-)

---

### Post by raydar on 2008-01-31
Well, blow me down.  I just had this problem on an UbuntuStudio machine upgraded from a fresh Feisty to Gutsy, 32-bit, NVIDIA GeForce FX-5600.  Got to the end of this thread & tried the disable-nVidia-driver, restart, enable-nVidia-driver, restart method--worked like a charm; thank you! :)

---

