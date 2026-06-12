---
title: "The Almost Fixed Sound Problem..."
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by Darklighter137 on 2007-02-08
I'm having a very odd problem with my sound.  Yesterday, all the sound was working perfectly.  Today only my midi player, timidi and the buttons where you click to see if the various sound components are working properly actually make any noise.  No noise from any other programs or the system (the midi player was installed while the sound still worked).  In order to get what I've got, I had to turn everything in the Device tab to "OSS - Open Sound System".  

Please help.  :(

---

### Post by jpeddicord on 2007-02-08
Go ahead and set your sound back to Autodetect, ALSA, or ESD. Use ALSA as a last option; try the other two first. Next, open up a terminal window and run: ```
killall esd
```

That will stop the sound system, and then any sound applications (that don't use OSS) will work properly. If you want to run an OSS sound app, then you must close all other applications that use sound.

Jacob

---

### Post by Darklighter137 on 2007-02-09
Sorry, that was just what I needed!  The trouble I was having was operator induced. =P

---

