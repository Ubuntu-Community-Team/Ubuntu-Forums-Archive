---
title: "Very strange! (sound problem)"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by kitt on 2006-07-24
Ubuntu cant play sounds!

Hi everyone,
All of a sudden, ubuntu has stopped playing sounds- BUT..I am able to play the sound files i want..its just that no program (games, ubuntu, etc.) is able to play any sounds.
Everything was working perfectly out-of-the-box, but now i can only play the sound files in the media players.

aplay returns this:
-------------------------------------------------------------------------
ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card 'Audio'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:544: audio open error: No such device
-----------------------------------------------------------------------------

aplay -l returns:
-----------------------------------------------------------------------
**** List of PLAYBACK Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
Subdevices: 1/1
Subdevice #0: subdevice #0
------------------------------------------------------------------
And heres what alsamixer throws up:
alsamixer: function snd_ctl_open failed for default: No such device
------------------------------------------------------------------
My machine: acer aspire 5004

---

### Post by kitt on 2006-07-25
Some one please help me!!

---

### Post by richbarna on 2006-07-25
Have you tried System/Preferences/Sound to make sure you've got the default card set?

---

### Post by kitt on 2006-07-25
Yes..it recognizes my card :SiS Sl7012

btw..i tried using a different user account..and it works perfectly!
Im really confused..whats going on here?

---

### Post by richbarna on 2006-07-25
Ok, I remember having a similar problem earlier this year. There is probably a very simple explanation for this, but I tried without success. What I did was to create a new user, move all my backed up files there, then delete the old user. If you are really dead-set on keeping your user/login name, do what I said above, and repeat it and create another user "again" with your old login name.

It seems that when you change the system config or install stuff, this can happen with ALSA.

---

