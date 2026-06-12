---
title: "Working Sound on Toshiba Satellite A135"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by Sparkster185 on 2007-05-26
I got this laptop about a month ago and I never had sound, until this morning.  I spent hours and hours searching for a fix and finally found it.

Here is the post I found (on these wonderful forums) that fixed my problem.

> 
Added "options snd-hda-intel model=3stack" at the end of /etc/modprobe.d/alsa-base, and now sound works! Try it out! (I have a Toshiba Satellite A135-S4407).


The thread can be found here: [http://ubuntuforums.org/showthread.php?t=392350&highlight=toshiba](http://ubuntuforums.org/showthread.php?t=392350&highlight=toshiba)

It's quite possible some things I did in the past, in addition to what I have posted here, actually led to the fix.  What exactly, I'm not too sure of since I tried lots of different things.

I do know that I have the Alsamixergui installed in my system, if that can point anyone in the right direction.

Just wanted to share this for anyone else having the same problem as me.  I will subscribe to this thread and check up on it so maybe I can help someone else with the same problem I once had.

Regards to anyone whose help led to my fix, and best luck to anyone else with this problem in the future.

-Sparkster

EDIT:  Just for the record, here is the hardware my machine has:
```

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Aud
io Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff01


```

---

