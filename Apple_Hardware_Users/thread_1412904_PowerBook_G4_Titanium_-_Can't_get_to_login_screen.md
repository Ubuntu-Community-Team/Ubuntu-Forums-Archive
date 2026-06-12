---
title: "PowerBook G4 Titanium - Can't get to login screen"
date: 2010-02-21
forum: Apple Hardware Users
---

### Post by marshmallow1304 on 2010-02-21
I just installed Karmic on a PowerBook G4 Titanium.  The install went fine after I figured out that I had to set the date in the open firmware because the PRAM battery is dead.  Now when I boot, I get a white screen with black text telling me it's found the display then the splash screen shows up but I never get the login screen, just a blank screen.  I can switch to the virtual consoles and fool around, but I haven't gotten it to work yet.

I'm not very experienced with Macs and Yaboot, so any help would be greatly appreciated.


Edit: I've attached .xsession-errors
(Has UF always required file extensions?)

---

### Post by linuxopjemac on 2010-02-22
I guess what you need is a working Xorg.conf file for your PowerBook. What kind of video card is in your machine ?

---

### Post by marshmallow1304 on 2010-02-22
[QUOTE=lspci | grep VGA]
0000:00:10.0 VGA compatible controller: ATI Technologies Inc Rage Mobility M3 AGP 2x (rev 02)[/QUOTE]

I've tried a couple different xorg.confs, but with no luck.

---

### Post by linuxopjemac on 2010-02-23
Try Debian Lenny, works pretty good on these machines.

---

### Post by marshmallow1304 on 2010-02-23
I just tried Lenny and got the same problem.

Edit:

Now I'm back on Ubuntu, because if I'm going to mess around to get one of them working, I'd rather it be Ubuntu.

I get a bunch of these in the Xorg log

> (II) Not using default mode "<a resolution>" (<reason>)
The reason varies, including "insufficient memory for mode", "hsync out of range", and "unknown reason".

Amidst those, every third line is
> (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument

---

