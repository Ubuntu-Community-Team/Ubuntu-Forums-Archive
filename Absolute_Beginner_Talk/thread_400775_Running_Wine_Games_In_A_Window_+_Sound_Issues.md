---
title: "Running Wine Games In A Window + Sound Issues"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by mjhasbach on 2007-04-03
I'm sure everyone is familiar with "Wine," the program that allows you run windows programs in linux. I have it mostly working, however, I am having difficulty running programs in wine in a window (i.e. games not being full screen.) I am also having problems with getting sound to work. I have messed with winecfg and whenever I go into the sound tab, I get this message displayed in the terminal:

fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack

Any ideas? By the way, congrats to the Ubuntu team for making Feisty such a great release! Wireless internet finally works with no effort =].

---

### Post by Motoxrdude on 2007-04-03
Uncheck the "OSS" box and check the "ALSA" box.

For the full screen issue
```
winecfg
``` go to the "Graphics" tab and check the "Emulate a Virtual Desktop" box. Go ahead and make the resolution to your liking. (usually i do 1024x768 and my desktop is at 1280x1024).

---

### Post by mjhasbach on 2007-04-03
Thanks for your fast reply.

ALSA worked like a charm for my sound. But for some reason, regardless of what I put into the resolution fields of "Emulate a virtual desktop, it runs it at full screen (I have messed with this option before).

Btw, my screen resolution is running at 1400x1050 and the game I am trying to play is starcraft, which reduces my resolution to 640x480.

---

### Post by Motoxrdude on 2007-04-03
Ah, sorry to hear about that. I have no clue on what to do, sorry. Maybe try and reinstall wine and then try again.

---

