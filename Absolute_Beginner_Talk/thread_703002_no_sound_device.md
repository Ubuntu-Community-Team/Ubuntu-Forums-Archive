---
title: "no sound device"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by cane1832 on 2008-02-20
so here is my story,
i was trying to fix the issue with the intel_hda outputing threw both speaker and headphones. I did somthings and now i have no sound what so ever. When i type aplay in console it says 

cane@cane-laptop:~$ aplay
ALSA lib confmisc.c:769:(parse_card) cannot find card ''
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3982:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:545: audio open error: No such device

don't know what to do from here and none of the sound how tos seem to get me anywhere. Any help is thanked.

Cane

---

### Post by spiderbatdad on 2008-02-20
try ```
asoundconf list
```

---

### Post by cane1832 on 2008-02-20
cane@cane-laptop:~$ asoundconf list
Names of available sound cards:

---

### Post by Hobo Joe on 2008-02-20
> **cane1832 said:**
> cane@cane-laptop:~$ asoundconf list
Names of available sound cards:

Umm, you missed the part with the sound card. ;)

Paste the whole output of it.

---

### Post by spiderbatdad on 2008-02-20
not sure what to recommend. You might list the steps you took, or link to the guide you followed in trying to get your sound card working. You might try uninstalling and reinstalling the alsa-base.
Did you blacklist your card in /etc/modprobe.d/blacklist or remove it from /etc/modprobe.d/alsa-base?

---

### Post by cane1832 on 2008-02-20
it displays nothing

---

### Post by cane1832 on 2008-02-20
so i did end up doing a sudo gedit /etc/proc/modprob.d/alsa-base

and the only thing i changed in it was at the bottom where its says

options snd-hda-intel model= xyz

---

### Post by spiderbatdad on 2008-02-20
and what is your computer model?

---

### Post by cane1832 on 2008-02-20
i have the compaq c715nr

I fixed it though

where the = xyz 
                 ^ no space 

lol oops 

thanks for you help and do you have any idea how to fix the output on both speakers and headphones to one when they are connected

Cane

---

