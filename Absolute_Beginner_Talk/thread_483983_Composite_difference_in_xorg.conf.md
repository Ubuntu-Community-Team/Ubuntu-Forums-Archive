---
title: "Composite difference in xorg.conf"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by ROUBOS on 2007-06-25
OK

Whats the difference between the following two Sections in xorg.conf

Section "Extensions"
        Option  "Composite" "false"
EndSection

Section "Extensions"
        Option  "Composite" "Disable"
EndSection

Section "Extensions"
        Option  "Composite" "0"
EndSection


I've seen around some readings regarding ATI card drivers, and in some pages it mentioned to enter "false" and in others "Disable". Also seen it with a "0". Is it the same thing?

Meanwhile fglrxinfo gives me the following:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 XT Platinum Edition
OpenGL version string: 2.0.6473 (8.37.6)


This means that I have 3D acceleration running with my ATI card working with fglrx drivers right?
But I still get the error message "The Composite extension is not available" under System>Preferences>Desktop Effects

EDIT>> 

Just another question. With this business of installing and reinstalling drivers etc. Does it mess up the OS to the point where a clean re-installation be required? (like in M$)

---

### Post by Waappu on 2007-06-25
> **ROUBOS said:**
> OK

Whats the difference between the following two Sections in xorg.conf

Section "Extensions"
        Option  "Composite" "false"
EndSection

Section "Extensions"
        Option  "Composite" "Disable"
EndSection

Section "Extensions"
        Option  "Composite" "0"
EndSection

All those mean same thing

---

### Post by ROUBOS on 2007-06-25
Thought so. Thanks.

Don't know why I cannot get Desktop Effects to work... My 3D acceleration card is working fine. :/

---

### Post by Waappu on 2007-06-25
> **ROUBOS said:**
> Thought so. Thanks.

Don't know why I cannot get Desktop Effects to work... My 3D acceleration card is working fine. :/

I think you need install XGL and create session for that. Then  login that session. ATI "fglrx" driver not support composite and thats why you need use XGL.

---

### Post by wyrmfire on 2007-12-31
Hi,

Have you tried checking to see if your driver is whitelisted in /usr/bin/compiz?

Check that you have the same driver name in that file in the whitelist as you've used for your video card in xorg.conf.

Also, switch Composite to "1".

It didn't seem to make a difference for me.

I'm using an ATI 2400 HD and it has Desktop Effects running now quite smoothly (only the occassional crash :))

Anyway, hope that helps.

Regards,

Wyrmfire

---

### Post by mcduck on 2007-12-31
If you are using fglrx drivers from Ubuntu repositories you need to install XGL as well (sudo apt-get install xserver-xgl). There's no need to create a new session for it in Gutsy, it's handled automaticaly for you.

If you are using new drivers straight from Ati/AMD, they don't need XGL any more but you need to enable composite in xorg.conf, and then whitelist the driver in some compiz setting file (which I can't remember right now).

---

