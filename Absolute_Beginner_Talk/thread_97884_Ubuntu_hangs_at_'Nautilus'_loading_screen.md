---
title: "Ubuntu hangs at 'Nautilus' loading screen"
date: 2005-12-01
forum: Absolute Beginner Talk
---

### Post by Auto|MaG on 2005-12-01
Just installed unbuntu yesterday on my laptop(compaq v2000) which uses the 200m intergrated graphics card. I had a few problems even getting into the GUI, but finally got that sorted out(I think, at least I can get to the login screen!). After logging in, I get the splash screen with 3 Icons, and uplon loading the 3rd one called Nautilus it just hangs there. 

I do have a mouse cursor, but if I left click anywhere the loading screen goes away and im left with a blank brownish/orangish background. Its not completely frozen since Ctrl-Alt-Bksp works to get back to the login screen again.

After reading a ton, I would guess its an issue with the ATI drivers, as lots of people seem to be having the same/similar problems. 

Right now the driver is set to ATI(tried vesa also) and I added 'Option "No Accel" ' to xorg.conf. Kinda stuck on where to go from here. What kind of information do you guys need in order to get some idea of what may help?(a log file somewhere?) 

Thanks a ton!

---

### Post by aysiu on 2005-12-02
I don't know if this helps solve your problem, but it may help to diagnose it if you try a few things:

1. Logging in as a different user--any different?
2. Logging into a different desktop environment (KDE or XFCE)--any different?
3. Using a lower screen resolution

---

