---
title: "No sound with new ubuntu install"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by rgardner on 2007-07-01
I love what I see, but I don't hear anything! I have an Audigy sb0090 sound card and I can see it listed in device manager with 18 lines of details. I think I need some basic instruction on how to learn what driver and something called a module I need, where to get them, and how to install them. I've read some instructions about typing commands in root or gnome, but I don't know how to get to those places.  I have installed Frisky Fawn, if that matters. Thanks

---

### Post by ugm6hr on 2007-07-01
First thing to try is Alsamixer:
In Terminal enter:
```
alsamixer
```
Then use "M" to unmute all the settings (MM=mute; oo=unmuted), and the left/right & up/down arrows to maximise all volumes.
Then escape to exit

Then see if you can hear anything (make sure something is playing).

---

