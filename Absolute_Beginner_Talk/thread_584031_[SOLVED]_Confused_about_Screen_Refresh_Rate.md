---
title: "[SOLVED] Confused about Screen Refresh Rate"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by LibertyShadow on 2007-10-20
The picture says it all. [IMG]http://www.skidmore.edu/~vnewell/WHAT.png[/IMG]

I want it to be 60 Hz, but I don't know how to tell.

---

### Post by LibertyShadow on 2007-10-20
I forgot this one:

[IMG]http://www.skidmore.edu/~vnewell/WHAT2.png[/IMG]

I configured /etc/X11/xorg.conf using the nvidia-settings... all seemed to go well except I have no clue what the refresh rate actually is.

BTW I am not an ABSOLUTE beginner... only about 6 months under my belt... however I don't pretend to know more than I do :D

---

### Post by insane_alien on 2007-10-20
LCD's are a bit iffy on the refresh rates. most of the time only part of the screen will refresh. it'll be about 60Hz anyway. or 100Hz if it is newer. it doesn't really work like an LCD ans only the pixels that are changing will get refreshed.

---

### Post by LibertyShadow on 2007-10-20
[My computer manual]("http://support.dell.com/support/edocs/systems/ins6400/en/om/specs.htm#wp1074108") (Dell E1505) says my refresh rate is 60Hz.  I guess it doesn't matter.  Its all just really confusing.

---

### Post by insane_alien on 2007-10-20
yeah. theres the hardware refresh rate(the refresh rate that it WILL go at no matter what) the software refresh rate (the refresh rate for writing to the screen buffer where it will wait till the next hardware refresh) and the render rate(the rate that it produces frames to be written to the screen buffer though only the one existing when the software refresh rate rolls around will be picked.)

---

### Post by LibertyShadow on 2007-10-20
There really never was a problem, just a confusing annoyance..  Thanks for the reply :)

Marking as solved.

---

