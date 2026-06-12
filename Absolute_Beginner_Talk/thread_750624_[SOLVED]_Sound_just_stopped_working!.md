---
title: "[SOLVED] Sound just stopped working!"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by Tom--d on 2008-04-09
I think I have an Intel HD audio sound card in my laptop. 

It was working for ages, perfectly. From when I installed Ubuntu.. 

Just a minute a go, it just stopped. The music plays but nothing comes out of the speakers.

Ive restarted twice now and still nothing. :|

Ive tried the head phone socket and no sound is coming out of that.

What happened? 
How do I restore the sound?


Thanks,
Tom

---

### Post by Sef on 2008-04-09
How old is your computer?  It could be the sound card went bad.

---

### Post by Tom--d on 2008-04-09
Its brand new. 
I brought it on Boxing day in 2007. 

Its a Toshiba A200-1VO

I did put it in stand by before the sound stopped working. 
Did that do anything?

---

### Post by Sef on 2008-04-09
Do you have Windows still on it?  If so, check to see if Windows' sound is still working.   I had a laptop whose sound card went bad after a few days.

---

### Post by Tom--d on 2008-04-09
No, Sorry I dont. 

I could try the live cd again and see if that works.

---

### Post by Tom--d on 2008-04-09
Tried the live cd and sound works... mmm

Its not the hardware which messed up..

---

### Post by Sef on 2008-04-09
Try the live cd.  Use a format that is supported out-of-the-box by Ubuntu.

---

### Post by Tom--d on 2008-04-09
I tried all the examples.. they all work.

I've stoped ALSA and restarted it. No sound

---

### Post by FuturePilot on 2008-04-09
Are any of the channels like Master, PCM, Front, Main muted in ```
gnome-volume-control
```

---

### Post by Tom--d on 2008-04-09
> **FuturePilot said:**
> Are any of the channels like Master, PCM, Front, Main muted in ```
gnome-volume-control
```

When opened, I had PCM on MUTE. Then I put it to full and sound works!!! It works again :D

But what caused it to go to mute? Because I never did it.

---

### Post by FuturePilot on 2008-04-09
> **Tom--d said:**
> When opened, I had PCM on MUTE. Then I put it to full and sound works!!! It works again :D

But what caused it to go to mute? Because I never did it.

No clue. Weird things happen sometimes :p
Glad that got it working for you. :D

---

### Post by Tom--d on 2008-04-09
Thank you so much :)

I now know next time what to do :)

---

