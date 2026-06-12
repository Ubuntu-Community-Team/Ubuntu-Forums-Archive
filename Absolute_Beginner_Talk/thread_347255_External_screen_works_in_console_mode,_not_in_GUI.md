---
title: "External screen works in console mode, not in GUI"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by dr_d on 2007-01-27
Hi guys...

I'm trying to get my laptop to work with an external screen.

The external screen works when I am booting up, but the minute the graphical login window loads up it switches back to the laptop screen.

The external screen also works when I am in console/tty mode (i.e. if I press CTRL+ALT+F1).


This leads me to suspect that it's a config problem... Here are the details of my setup:

> 
I have edited xorg.conf to enable the nvidia driver. I have also set the default depth to 24. I have not installed beryl/compiz (although they run fine on my setup, the software was a bit too buggy for me).

The resolution for my laptop screen is 1920x1200, and refresh rate is 60Hz. I'm not sure if my external monitor supports this resolution (although I suspect that it does, as it's a fairly newish dell lcd). Also I can't test with a lower res because the System>Preferences>Screen Resolution program wont let me change either the resolution or the refresh rate.

The external monitor is connected to my laptop over the white digital port. I'm using a white DVI digital cable. Both my laptop and the monitor *also* have blue vga ports but I cant find a cable for that atm.


Okay hit me. What is likely to be causing the problem?

Thanks,
Dr D

---

