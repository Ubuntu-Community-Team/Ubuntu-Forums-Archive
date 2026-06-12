---
title: "Thinkpad x60s, sound stopped working"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by Kamu on 2008-02-25
I have been using my thinkpad x60s for months and the sound worked flawlessly (well, more or less).  But now I have a mystery problem.

For the first time, I have used the hardware button (at the top, by the big blue thinkvantage button) to mute the sound and it will sadly not come back up!

To give more details:  after muting, I turned the computer off and noticed the lack of sound only at reboot.  I tried to toggle the switch multiple times, but it only shows "mute on", never "mute off".  I have an IBM external keyboard, too, and the mute button on that keyboard toggles mute on and off just fine normally, but now it just says "mute off" but does not actually turn the sound on anymore.

I opened alsamixer and noticed that the master channel was muted no matter what the mute buttons were claiming, so I turned it back on but still no sound.

Interestingly, with the master on, if I turn on the mic and get the volume up, I get a high-pitched feedback, but no actual sound.

I am really puzzled... Any ideas?

---

### Post by Kamu on 2008-02-25
Ooops, I am ashamed that I had not noticed that I had forgotten to put the Master channel in KMix back to Master (from PCM to which it had changed somewhere in all my poking around).

Sound works ok now.

Presumably just turning things back on in alsamixer did the trick.  I will go be ashamed of taking all your time and looking stupid in the process in a dark corner.

---

### Post by mjwhitfield on 2008-02-25
Mark the thread as solved! it'll help anyone that makes the same mistake :)

---

