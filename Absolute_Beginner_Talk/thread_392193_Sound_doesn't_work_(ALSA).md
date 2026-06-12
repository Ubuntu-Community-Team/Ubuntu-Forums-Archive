---
title: "Sound doesn't work (ALSA)"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by kbsuperstar on 2007-03-24
I downloaded all the driver, lib, utils, and oss from alsa-project.org, and I followed [this tutorial]("http://alsa.opensrc.org/Quick_Install"), but my sound doesn't work.

I got it to work one time before on the laptop I'm using (before I erased the HD by accident with an XP install CD).

The error I get when I type 'alsamixer' into the console is this:

```
kyle@kyle-laptop:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device

```

What should I do to fix this?

---

### Post by zvacet on 2007-03-26
I don´t understand why you have to compile?Aren´t Alsa in synaptic or add/remove?Maybe just chek menu layout and anable it there(volume control).

---

### Post by kbsuperstar on 2007-03-26
Current ALSA add/remove or installing through Synaptic doesn't come with the most recent drivers, libraries, etc., so it's necessary to compile if you want/need these. I'm not certain how many people experience this problem (quite a few, I believe), but many sound cards don't work correctly without the updated drivers and such. For example, I'm using a Compaq Presario v5000 with an integrated Intel soundcard, and I'm to get the sound very loud at all (it's much lower than when I had XP). Plus, the PCM is pretty messed up -- the sound is crackly unless it's lowered to around 75%, which also lowers the level of volume drastically.

So...

Unless someone knows how I can easily install ALSA with the recent drivers (1.0.14rc3), libraries (1.0.14rc3), utils (1.0.14rc2), and OSS (1.0.12), then I think I need to resort to re-compiling.

Can someone help me with either? Thanks

---

