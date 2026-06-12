---
title: "Sound Problem in Ubuntu Gutsy"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by aleph one on 2008-01-06
I've had Gutsy installed on my machine for a couple of months now and have had no problems with sound up until now.  Sound was working fine about two weeks ago before I went on a trip out of state.  When I returned last night and booted up, I had absolutely NO sound.  Unlike others, I don't even have sound during login/logout.  The only thing I can think of that triggered this is right before I left I changed the login sound to one of my own, but I doubt that has anything to do with it.  I am using onboard sound with my Asus A8N-E mobo and Linux says it has no problem detecting it (I don't see any reason why it should considering it worked fine earlier).  Plugging my speakers or headphones into the front audio ports on my rig does not work either.  I've been using Ubuntu for about a year now, but I'm still not entirely Linux-savvy, so any help would be greatly appreciated.

---

### Post by blueridgedog on 2008-01-06
Some simple things, that may not help, but may reveal some additional information:

right click the speaker icon, select "open volume control" then verify that your output is not muted, also select file then "change device" and verify that you have a device configured.

---

### Post by aleph one on 2008-01-06
blueridgedog-
Thank you for your reply.  I have checked both, and my system is not muted and the device is detected and working correctly.

ANY input is appreciated.

---

### Post by philinux on 2008-01-06
Check the PCM slider in volume control.

---

### Post by blueridgedog on 2008-01-06
I have no clue as to the error, but perhaps if you tried to play something in the terminal, it may give you a clue as to what is wrong.  Try:

```
mplayer /path/to/a/musicfile.mp3
```

(replace the second part with a path to one of your music files)

---

