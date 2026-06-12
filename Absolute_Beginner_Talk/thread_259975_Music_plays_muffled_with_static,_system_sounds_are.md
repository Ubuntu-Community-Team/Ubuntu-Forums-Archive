---
title: "Music plays muffled with static, system sounds are great?"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by uncreative on 2006-09-18
What is up with this, my MP3s used to play fine, then about two days ago they started playing muffled and with lots of static.  I don't even know where to begin because Its the same result no matter what player I choose.  

And system sounds are all great, no static etc.

Any ideas?

---

### Post by Lord Illidan on 2006-09-18
I'd suggest 1 or 2 things.

Run ```
killall esd
``` in a terminal before playing music.

Or else...run ```
alsamixer
``` in a terminal and adjust down the PCM or WAVE volumes..when they are at 80% or higher, I've found them to increase static.

---

### Post by Zackie on 2008-02-18
My Music and sounds, sound fine but on some Linux Games it as if the sound Clips... or red lines... i turned it all down to 65% and the same.. happens... any ideas?

---

### Post by PmDematagoda on 2008-02-18
This thread is more than one year old.

If you want to ask a support question then I suggest that you start your own thread concerning your problem.

This thread is closed.

---

