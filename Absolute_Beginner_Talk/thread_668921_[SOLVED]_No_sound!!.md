---
title: "[SOLVED] No sound?!!"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by cartisdm on 2008-01-15
I tried to play my first DVD on a new installation yesterday so I downloaded all the required codecs etc and finally got it working without too much trouble.  I played a DVD fine and dandy.  I turned off the computer and Just turned it back on tonight to play another DVD and now I have no sound.

Not just with DVDs, but with anything.  I can't possibly think of anything I could have changed.

I ran
```
lspci
```

and my sound card is detected and no, I don't have mute on or anything.  What went wrong?!:confused:

---

### Post by FuturePilot on 2008-01-15
.

---

### Post by cartisdm on 2008-01-15
> **FuturePilot said:**
> .

um.......

---

### Post by FuturePilot on 2008-01-15
> **cartisdm said:**
> um.......

Sorry. I read your post to fast and misunderstood the issue so my reply was irrelevant.

---

### Post by cartisdm on 2008-01-15
no problem

---

### Post by sumguy231 on 2008-01-15
Go to a terminal, run alsamixer, and make sure everything relevant is turned up sufficiently, especially PCM. Just play around with all the levels there, you won't break anything.

---

### Post by kostkon on 2008-01-15
> **cartisdm said:**
> I tried to play my first DVD on a new installation yesterday so I downloaded all the required codecs etc and finally got it working without too much trouble.  I played a DVD fine and dandy.  I turned off the computer and Just turned it back on tonight to play another DVD and now I have no sound.

Not just with DVDs, but with anything.  I can't possibly think of anything I could have changed.

I ran
```
lspci
```

and my sound card is detected and no, I don't have mute on or anything.  What went wrong?!:confused:

What do you mean you don't have sound? Do you mean that when you try to use a media player you get an error message or just that you play something but you don't hear any sound?

In the first case, I would like to ask you if you got any updates before you closed your PC. Maybe an update caused a problem to your sound card (more likely if you got a kernel update).

In the second case, more likely it is a volume level problem. Try opening a terminal and running *alsamixer* to adjust the levels from there.

---

### Post by cartisdm on 2008-01-16
Oddly enough this solved the problem yet I don't really know what happened.

```
sudo apt-get install asoundconf-gtk
```

then ran

```
asoundconf-gtk
```

then changed the default card to one of the listed settings and everything worked.  During the movie about 10 minuted into it I noticed the sound was off by about a half a second so I closed it, opened the movie up again and it was back to normal.

I'm still not certain what happened though or what would cause my sound to be off:confused:

---

