---
title: "Youtube quiet even on full volume"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by dac10 on 2007-08-16
im using firefox with adobe flash player 9 installed and the videos on youtube are playing exceptionally quietly even when i have the volume turned right up. this is not the case when using XMMS to play my mp3's though.

any reasons why this might be? thanks,

---

### Post by Hobo Joe on 2007-08-16
This happened to me, try closing firefox and restarting, if that doesn't work, do a quick reboot.

---

### Post by dac10 on 2007-08-16
no joy, i think it may have even gotten quieter :eek:

---

### Post by Hobo Joe on 2007-08-16
Is anything else quite or is it just Youtube?


You could also try a full reboot.

---

### Post by dac10 on 2007-08-16
i did a full reboot, and i think its everything including music on bebo. i really need this fixed ASAP.

---

### Post by Hobo Joe on 2007-08-16
Ok, now that I know it's more than youtube, I can help more.

open alsamixer,(type that into the terminal) and check the levels, particularly master and PCM.

---

### Post by dac10 on 2007-08-16
PCM is only 2 grey bars, front is nearly full and i cant see a master.

---

### Post by Hobo Joe on 2007-08-16
Put up PCM.

---

### Post by dac10 on 2007-08-16
i dont know how?

---

### Post by Hobo Joe on 2007-08-16
Arrow keys for left and right, and up and down to change volume to 'm' to mute/unmute.

---

### Post by dac10 on 2007-08-16
thank you ever so much! :) thats EXACTLY what was wrong :D

---

### Post by gatorbrit on 2008-04-13
Hi I am having the same problem.  I opened the alsamixer in terminal and got full bars on PCM and Mic, but nothing on Master - just "00"

Any suggestions.I am running Ubuntu 7.10 on a Toshiba Satellite laptop

---

### Post by original_jamingrit on 2008-04-13
hey gatorbit,
you can use the arrow keys to put up the Master Volume in alsamixer.

If for some reason you can't, you could also use the W key.

---

### Post by gatorbrit on 2008-04-14
> **original_jamingrit said:**
> hey gatorbit,
you can use the arrow keys to put up the Master Volume in alsamixer.

If for some reason you can't, you could also use the W key.

Thanks, but doesn't seem to help - I attached a screen shot to show what the settings are.  I just don't have any "bars" for the master volume control.

When I hit the "test" button on the sound prefs box I get a tone.

Thanks again!!!

Rich

---

