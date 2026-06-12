---
title: "non-linear volume control response"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by mattismyname on 2008-04-06
When I try to adjust my speaker volume using a software mixer (Gnome volume applet, kmix, etc) it gives an extremely non-ilnear response.  From 0-50%, there is almost no change in volume, from 50-75% there is a modest increase in volume and then from 75%-100% it increases really fast.  Even a single-pixel move of the mouse in this range can take it from too-quiet to too-loud.

My particular audio device is a "Sound Fusion CS46xx'.

---

### Post by leturbo on 2008-05-05
I'm having this exact same issue.  Volume at 50% is almost dead silent, 100% is blaring loud and distorted.  

Any suggestions?

---

### Post by SmokinJuan on 2008-06-22
Looks like this "bug" was [recently assigned]("http://https://bugs.launchpad.net/ubuntu/+bug/204898"). That bug says the control is linear but needs to be logarithmic. 

leturbo, you may be able to clear out some distortion using the PCM volume control... I had to set it somewhere between 50-75% to keep mine from clipping.

---

### Post by krlhc8 on 2008-06-22
You can go to System>Preferences>Sound and change which line your hotkeys control.  If you want a more logarithmic (decibel-wise) control, then under the devices tab and under "Default Mixer Tracks," select "Headphones" instead of "Master."

---

