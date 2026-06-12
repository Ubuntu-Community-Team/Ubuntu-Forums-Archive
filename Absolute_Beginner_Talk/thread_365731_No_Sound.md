---
title: "No Sound"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by philip360 on 2007-02-20
Hi all, I did a fresh install of Dapper (after some drama trying to upgrade kernel to 6.10)
I have no sound other than the system post beep.
Sound works good when booted in XP
Checked BIOS, sound enabled AC 97 audio controller.

I have followed the basics here:
[http://www.ubuntuforums.org/showthread.php?t=205449](http://www.ubuntuforums.org/showthread.php?t=205449)

aplay -l 
showed the onboard sound

lspci -v
listed the sound device

sudo modprobe snd-via82xx 
did not show anything, just returned to command prompt

alsamixer
un muted everything and set to 100

made sure totem player, amarok were not muted

"Getting the Alsa drivers from a fresh kernel" is the next procedure in the above listed thread.
Does this seem like the best course of action???

Any help appreciated, Philip

---

### Post by energiya on 2007-02-20
I don't see anything else to do... reinstall alsa. It isn't difficult.

---

### Post by mahiyar on 2007-02-20
In system>preferences>sound>Device, is the device shown OK, can you try fiddling around with various devices (ALSA should work) and play test sound.

---

### Post by philip360 on 2007-02-23
I have removed and reinstalled alsa as per the thread I originally quoted.

sudo aptitude --purge remove linux-sound-base alsa-base alsa-utils

and then:

sudo aptitude install linux-sound-base alsa-base alsa-utils

I rebooted and nothing. HMMMM????

---

### Post by myotheralt on 2007-03-09
ok, im in the same sound problem boat here, i think.  if i turn my speakers all the way up, and set the alsamiser to 100% across the board, i get a wisper out of the speakers.

what can i do?

---

