---
title: "Exclusive External Monitor on Macbook 2,1"
date: 2008-05-26
forum: Apple Hardware Users
---

### Post by lijamez on 2008-05-26
At home, I use my external monitor only. To do that on OS X I would just connect the monitor using the Mini-DVI - DVI adapter, press the power button, and immediately close the lid. OS X will then use my external monitor exclusively and turn the laptop's screen off. 

In Ubuntu, I have tinkered with the screen resolution settings and I cannot get it to display on only my external monitor. The native resolution of my external is 1680 x 1050 and I can achieve that properly only if my laptop's screen is set to anything except "off." If I try to turn the laptop's screen off, the external will display a garbled screen like static and basically becomes unusable. 

Is it possible to use Ubuntu with only the external monitor with the laptop's screen turned off and lid closed? Getting this to work is an absolute necessity for me.

Note: 
The graphics controller in the Macbook 2,1 is an Intel GMA950
I've tried turning desktop effects off. Problem still exists.

---

### Post by xerosis on 2008-05-26
I can't promise your monitor is supported but all I do to get mine to work is plug in with the mini-VGA and restart X with ctrl+alt+backspace. When it comes back on, it displays on my monitor and macbook at the monitor resolution, I then close the macbook to switch the screen off (your settings may vary)

---

### Post by lijamez on 2008-05-26
When I restart X my external monitor is set at a default resolution of only 1280x800. I can change it in the settings, but closing the lid will either (depending on power settings):
A) Leave the laptop's display on while lid is closed
B) Turn both laptop's and external display off

After some more messing around, I noticed some **very strange** behavior. When I set the external display to its native resolution 1680 x 1050 and the laptop's display to "Off", I must move the mouse around the screen as the resolution is being changed to avoid the "static effect" on my external! :shock: I assume this is a horrible bug in the display driver but is there a fix?

---

### Post by lijamez on 2008-06-04
I also noticed that when the screen is going crazy I can, with some effort, open a "Appearance Preferences" window by right clicking the desktop and clicking "Change Desktop Background" and the flickering/static/garbled screen instantly goes away. Once I close that window, however, it comes right back. Does anyone have an explanation for this?? The problem appears every time at startup.

Video of the problem here: [http://youtube.com/watch?v=H0fIacaO-_U](http://youtube.com/watch?v=H0fIacaO-_U)

---

### Post by mabovo on 2008-06-04
Please, report a bug on launchpad about this.

Thnks !

---

