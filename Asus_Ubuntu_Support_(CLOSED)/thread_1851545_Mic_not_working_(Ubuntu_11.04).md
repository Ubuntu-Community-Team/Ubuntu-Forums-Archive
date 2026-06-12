---
title: "Mic not working (Ubuntu 11.04)"
date: 2011-09-28
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Arjandew on 2011-09-28
Hi all,

I've a dualboot with Win7 for a month or so, and my mic is still not working.
I have tried to fix it by myself but, i'm a fool cause i can't fix it... ;)

My laptop is an Asus X70A. (64-bit)
Dualboot: Ubuntu 11.04 (x32) alongside Win7 (x64)

Please help!

---

### Post by ajgreeny on 2011-09-28
You may need to install several pulseaudio packages if they are not installed by default, so check you have pavucontrol and padevchooser installed, and if not install them.

Run alsamixer in terminal and check that the levels of inputs/outputs are not set too low.
Move from slider to slider, and raise and lower levels with the cursor keys, particularly for mic;  note that there may be more than one mic showing so raise levels for both if needed.
Mute and unmute with the "M" key.
Tab will move you from "playback" to "capture".  On capture screen make sure the mic is active, as in the screenshot and if not move to the mic column and hit space bar.
Esc will save and exit.

Now open up Pulse Audio Volume Control from the Sound and Video menu and make sure in the Input Devices tab that the Mic is not muted and the Port box shows microphone; again see screenshot.

Try all that and come back again if still no go.

---

### Post by Arjandew on 2011-10-01
Hi!

Thanks for your (fast) reply!

I've everything tried, with alsamixer and the Volume Control, but it is still not working in the right way... (That means, my mic is not working.. ;) )

I'll add some screenshots of my settings.

I hope, the problem can be solved..

---

