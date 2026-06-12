---
title: "Microphone jack not working on a MacBook (3rd gen)"
date: 2008-10-09
forum: Apple Hardware Users
---

### Post by robzon on 2008-10-09
Hello,

just like in the title - I plug in the mic, but still all the apps use the internal mic. Has anyone encountered a similar issue? Any fixes in the wild?

thanks

---

### Post by cyberdork33 on 2008-10-09
> **robzon said:**
> Hello,

just like in the title - I plug in the mic, but still all the apps use the internal mic. Has anyone encountered a similar issue? Any fixes in the wild?

thanks
The switching is probably not automatic. run 'alsamixer' in a terminal, mute the internal mic, and unmute the "Line In"

---

### Post by wepalm on 2008-10-13
does the microphone power itself using batteries?  if it requires power from the computer it will not work.  To tge best of my knowledge Macbooks do not have a microphone jack but rather a line-in jack.  The mic must power itself.

---

### Post by robzon on 2008-10-13
Thanks for your replies.

I've tried all possible combinations of volume settings (using gnome's volume control though, with all channels and switches on) and it doesn't work.

And the same mic works fine on OS X so it must be something with the driver. Cyberdork33 is most probably right, the input source doesn't get switched automatically, but from what I see there's no way to switch the source manually.

There are also other issues with the sound driver like channels being mixed up, and overall volume level is lower than on OS X. Microphone jack is the only thing that really annoys me, it makes using VoIP on Linux really hard :(

I do keep OS X for cases like that, but I'd really rather use Ubuntu <3 :-)

Cheers

---

### Post by cyberdork33 on 2008-10-13
> **robzon said:**
> And the same mic works fine on OS X so it must be something with the driver. Cyberdork33 is most probably right, the input source doesn't get switched automatically, but from what I see there's no way to switch the source manually.
Use alsamixer, it will be sure to give you all the channels.

---

