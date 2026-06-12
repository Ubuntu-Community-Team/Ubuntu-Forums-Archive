---
title: "powerbook sound issue"
date: 2005-03-24
forum: Apple PPC Users
---

### Post by khc on 2005-03-24
Whenever I play any sound (rhythmbox, /usr/bin/play, doesn't matter), the volume is extremely low, even if I max out everything I can set in alsamixer. Say if I play a song, the first half a second or so the volume would seem normal, then the volume would be so low that I almost can't hear anything. If I stop it and wait a couple seconds, the problem happens again.

It's probably best to illustrate it with the system bell. Open a terminal, type nothing and hit backspace. Normally you would hear a "Beep" sound. Hit it a couple times fast, and you should hear
a couple "beep"s, all at the same volume. For me only the first "beep" is at the "normal" volume, and the rest are really quiet. Wait a couple seconds then the first "beep" would be normal again.

Note that this problem did not happen with Warty, nor in OS X, so I don't think it's a hardware problem. I think it might have even worked when I first installed Hoary (around December), but I am not too sure.

---

### Post by umbertoz on 2005-03-25
I had same problem but now alsa sound system works.

You should open volume control and manage, select the right mixer (ALSA)
and turn up or down the DRC Range control -

when you modify this parameters, you'll can modify all others parameters and
set up your system.

uz.

---

### Post by khc on 2005-03-26
Thanks! I've always been using the right mixer, but I guess somehow the "DRC Range control" value was changed (not by me). Any idea what the value "should" be?

---

### Post by umbertoz on 2005-03-26
You have to save alsa settings once.

$ sudo alsactl store 0

I think it's a bug.

regards.

---

### Post by Kanma on 2005-09-19
Hello, I'm sort of a newbie linux user. I tried that alsamixer thing you mention, and it allows me to increase the sound volume, but very very sightly, not enough. What's wrong?

By the way, I tried to plug in my headphones, and the sound appears to work perfectly through them. Are Powerbook speakers incompatible with Hoary?

Thank you.

---

### Post by Flaystus on 2005-09-29
Same problem here with my Powermac G5 (Dual 1.8ghz)

I had to goto OSX turn the volume ALL THE WAY UP. Turn the Speakers all the way up. Go back to ubuntu and now I can at least hear things but the sound levels are speaker blowing when the system BONG sounds off.

Something is not quite right here. Total Linux newbie BTW.

---

