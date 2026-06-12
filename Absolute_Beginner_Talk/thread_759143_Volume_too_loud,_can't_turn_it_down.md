---
title: "Volume too loud, can't turn it down"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by NR1224 on 2008-04-18
This isn't a problem per se, but it is a little annoying. I cant ajust my volume, it is either 100% or 0%. This isn't a big deal because i can ajust the speaker volume, but if there is a quick fix for this i would be very grateful

---

### Post by HereInOz on 2008-04-18
So are you saying that when you click on the speaker icon up near the clock, that you are not able to move the slider and change the volume, or is it that you can move the slider but it makes no difference?

---

### Post by NR1224 on 2008-04-18
when i click on the volume icon, the slider is a 100%. Moving it does nothing, and snaps back to 100%. Even when it ocassionally stays at another number, it changes nothing

---

### Post by Bubba64 on 2008-04-18
Right click on volume and open volume control this will allow you to assign the volume stuff you have to sort of figure it out by hit and miss. The preferences on the right click will actually assign volume control,

---

### Post by Dr Small on 2008-04-18
Try going into alsamixer and see if you can adjust volume there:
```
alsamixer
```

Dr Small

---

### Post by NR1224 on 2008-04-18
right clicking doesnt seem to change it. The slider keeps jumping back to 100%. Its really not a big deal, but is this simply a bug? maybe i have an unsupported audio driver? if so, how would i go about finding what audio device i am using, as far as I know, i think im just using my motherboards onboard audio

ohh, i also get this with alsa mixer, even with sudo, 
alsamixer: function snd_mixer_load failed: No such file or directory

---

### Post by NR1224 on 2008-04-18
ok found my audio stuff, my mixer device is a Realtek ALC861, and next to it in parenthesis it says OSS Mixer. Is it possible to use ALSA instead?

---

### Post by erlyrisa on 2008-04-18
> **Bubba64 said:**
> Right click on volume and open volume control this will allow you to assign the volume stuff you have to sort of figure it out by hit and miss. The preferences on the right click will actually assign volume control,

as bubba said... you have more than one option for sound output (and input probably)

you need to "check box" one of the sound devices in order for the slider on the applet to know which devices volume to adjust.

---

