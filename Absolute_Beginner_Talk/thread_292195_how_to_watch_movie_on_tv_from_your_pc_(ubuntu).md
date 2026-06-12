---
title: "how to watch movie on tv from your pc (ubuntu)"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by Bahal on 2006-11-03
Hi
how can I connect my tv to my pc...its easy on windows, just right click on your desktop and....bla bla bla...

but how is it done in unbuntu? I have a graphic-card named "ATI Mobility Radeon 9700"...help me out please...:)

---

### Post by electricshoes on 2006-11-03
try tvtime - You can choose what device to scan for signal.
What kind of video input do you have on your video card ?

---

### Post by Bahal on 2006-11-03
what do your mean by "tv-time"....Im asking since Im newbi...
btw, how can I find out what kind of video input I have on mye video card?

thx;)

---

### Post by electricshoes on 2006-11-03
search synaptic for tvtime.

[http://tvtime.sourceforge.net/](http://tvtime.sourceforge.net/)


 When you run it, you can choose what input you want to be on.

---

### Post by jsandys on 2006-11-03
You need the fglrx drivers to use your ATI Video output, to display the computer screen on your TV.  If you want to play a DVD you can only view it on one screen.  You will need to edit the xorg.conf file to get TwinView to work.  Check the stickys in the Multimedia & Video forum, and search for fglrx, TwinView, TV and TexturedVideo.

And Good Luck.  ATI works fine on Windows but I tried for a week to get an ATI 9600 to work with both my TV via S-video and my monitor via VGA.  All I wanted was to play FlightGear and watch DVDs on either screen.  What ever I did to get the DVD to work on the TV made FlightGear run a one frame a second, or if I got FlightGear running smoothly I couldn't get a good DVD deisplay.  I finally yanked the ATI card and put in an Nvidia.  I'll keep the ATI card for either a Windows computer or a monitor only (no TV) computer.

---

