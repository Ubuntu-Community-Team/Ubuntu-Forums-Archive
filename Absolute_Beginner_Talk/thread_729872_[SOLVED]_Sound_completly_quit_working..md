---
title: "[SOLVED] Sound completly quit working."
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by Dr Small on 2008-03-20
I have checked alsamixer, and gmix. Nothing is muted that would hinder sound. Speakers are unmuted and plugged in.

I launch VLC from the command line and try to play a song, and here is the terminal output:
```
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
[00000529] oss audio output error: cannot open audio device (/dev/dsp)

```

Here are the permission sets for /dev/dsp:
```
crw-rw---- 1 root audio      14,   3 2008-03-05 08:46 dsp
```

And I am in the audio group:
```
audio:x:29:drsmall
```

What should I try to get my sound working again?

Dr Small

---

### Post by ohzopants on 2008-03-20
Enjoy the silence and patiently wait for PulseAudio in Hardy? I tried it in fedora core 8 and it is absolutely fantastic!

Just kidding, of course, but unfortunately I have no real solution to propose.

I've had a similar problem but it was always because some program which was using the sound card crashed and didn't release the sound card properly (mostly firefox and flash); the only way to get sound back after that is a reboot for me.

---

### Post by Dr Small on 2008-03-20
LOL. Ok. I was afraid of that. Some geeks cherish their uptime, and I didn't want to reboot :p
But, if all else fails, reboot will become a neccessity. Which reminds me, the last time I remember sound working was while playing bzflags, so maybe it is still holding the sound card.

There is no way to "release" the sound card, or restart the service without a reboot is there?

Dr Small

---

### Post by ohzopants on 2008-03-20
None that I know of.  Although that would be great since firefox and flash really don't get along very well in Gutsy.

---

### Post by Dr Small on 2008-03-20
Problem Solved :) and no reboot was necessary!
I simply ran:
```
ps aux | grep bz
```

And found bzfs running, so I killed it and now sound works :)
Whew. I wish every problem was that easy to fix.
Thanks for your help, it was invaluable :D

Dr Small

---

### Post by ohzopants on 2008-03-20
How do you change the title of a thread? (Like adding [Solved])

---

### Post by Dr Small on 2008-03-20
Thread Tools > Mark Thread as Solved ;)

---

### Post by Andavane on 2008-03-20
> **ohzopants said:**
> How do you change the title of a thread? (Like adding [Solved])
You just type what you want in the bar above, under "Title:"

---

### Post by rcxjflores on 2008-03-21
This was completely a trial and error kind of thing so take this with a grain of salt. Noticing the other postings about individual packages and references to ALSA, I went into the Synaptic Package Manager (did a search on **_Sound_**) and added the handful of ALSA packages that were not installed that I thought should have been and Voila!
Like I said, trial and error (dumb luck mixed with very little common sense), but I haven't rebooted my machine yet. If I don't respond back it's all still working :lolflag:

---

