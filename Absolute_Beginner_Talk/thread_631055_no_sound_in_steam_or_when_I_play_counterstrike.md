---
title: "no sound in steam or when I play counterstrike"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by chaddiesel on 2007-12-04
Well,  I have a problem with no sound in steam or counterstrike when I am playing. I can't play any music or any sounds whenever steam is running on the "top menu bar". 

The error is a totem error that says that it can't play the file..."Is another program using it? ". 

Whenever you exit steam everything works fine. Any ideas on how to get the sound to work?

---

### Post by crav on 2007-12-04
are you using wine or a virtual machine to play it?

---

### Post by chaddiesel on 2007-12-04
i'm using wine.

---

### Post by chaddiesel on 2007-12-04
Any Ideas? I'm still not getting any sound to work whenever steam is running

---

### Post by crav on 2007-12-04
I didn't get any sound in wine for a while... than I configured wine!

at terminal type:
```
winecfg
```
this will bring up the wine configuration window. Click the audio tab. At the bottom, I had to change it to "emulation" to get sound to work.

Hope this helps!

---

### Post by ArmyOfOrr42 on 2007-12-10
I'm having the same problem.  Changing the audio setting to emulation didn't work for me

---

### Post by keyboardslave on 2008-01-21
im also having the same problem i have emulation turned on and i have oss as driver also i turned exeleration down but still no sound in ccs using wine.

---

### Post by sjforrester on 2008-02-24
Same issue here. Has anyone found a solution? :confused:

---

### Post by iverson2 on 2008-03-25
Yeah I have this problem too.  When I hit 'test sound' in config, it always comes up with Audio Test Failed!

---

### Post by LowSky on 2008-03-25
you cannot use ALSA you need to use OSS... at least that is what I found will checking WineHQ. Im suprised you can get Counterstrike running at all, it always fails on me within 30 seconds of play.

---

