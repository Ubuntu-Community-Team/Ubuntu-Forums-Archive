---
title: "External soundcard problems"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by getmeoutofhere on 2007-08-25
I'm finding Ubuntu very difficult to deal with, but I'm giving it one more go.  Drivers are a real problem for me.  But I'll take things one step at a time.

 I'm currently having difficulties with a USB-connected external soundcard, the Edirol UA-25 to be precise.  The sound works fine, but I can't record on it, using either Audacity or the gnome sound recorder.  This is in spite of the fact that the microphone is picking up sound - when I knock it, the peak limiter light registers.  When I click the volume icon, at the top right of the screen, next to the date, the controls only relate to playback, and not for the soundcard - which shouldn't be relevant anyway, because the UA-25 volume controls are on the soundcard, not the computer.  I believe that the UA-25 is the default soundcard, because when I log on, and once I've entered the password, the sound comes out of the soundcard, not the computer speakers.  The only sound coming out of the computer speaks is the drum-like noise as I'm prompted to enter my username, on log on.  

I've tried using a different USB microphone, and that doesn't work either.

Any suggestions as to how I might get my microphone working?  Thanks.

---

### Post by badactress on 2007-08-25
Often by default, the line-in and mic volume controls are turned to zero in Ubuntu.

Have you tried opening a terminal & typing: alsamixer

this brings up a set of volume controls. Use the arrow keys to move across to line-in and mic & use up/down arrows to turn their levels up. Then 'escape' to exit.

I'm not saying this will solve the problem but it's the 1st thing you should check :)

---

