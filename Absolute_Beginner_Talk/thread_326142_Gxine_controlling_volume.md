---
title: "Gxine controlling volume"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by bcdeck on 2006-12-27
I've been diagnosing an audio issue, and I've found that the volume setting in gxine seems to be controlling volume in other applications, ie. Totem movie player and Rhythmbox. If Gxine volume is low (whether Gxine is running or not), I get low volume in the other apps as well. 

Anyone know if this normal? If not, is there a fix?

---

### Post by Jussi01 on 2006-12-27
Yeah, its a bug - try right clicking on your volume control, then preferences then select pcm. this should make your main volume control all of the apps. 

Hope this helps

---

### Post by rajeev1204 on 2006-12-27
yes i have the same issue.

one time i had no sound at all on my system and when i just started gxine to play a movie i found volume on zero.!!

---

### Post by bcdeck on 2006-12-27
I have pcm selected, but gxine is still controlling overall volume.

I'm guessing this has something to do with other aps using the gxine engine. Is three another option, one that would let me remove gxine altogether? And will that other option have the same volume issue?

---

### Post by rajeev1204 on 2006-12-27
this is cos gxine adjusts the PCM instead of the master volume


just leave pcm settings as it is in volume properties and only adjust master

or if u want u can get rid of gxine alltogether if this bugs u


u should probably just run one app at a time!


regards

rajeev

---

### Post by pseudonym on 2006-12-27
> **rajeev1204 said:**
> this is cos gxine adjusts the PCM instead of the master volume
You can change the mixer gxine uses in the configuration menu -

File>Configuration>Settings, then on the 'audio' section go to the 'device' tab and look for 'alsa_mixer_name'. Changing this to 'Master' should resolve your issue.

---

### Post by rajeev1204 on 2006-12-27
thanks for the tip pseudo

but my problem is the changes dont take effect.


i also tried to install w32 and real codecs and edited my xine-config , but it still doesnt change


the xine-config file is in my home folder ( hidden) , is that the problem?


regards

rajeev

---

### Post by pseudonym on 2006-12-27
> **rajeev1204 said:**
> thanks for the tip pseudo

but my problem is the changes dont take effect.

well, it was kind of a guess ;)

a similar option seems to work in xmms, though, if you didn't already know. In xine apps (and probably everything else) I think the best thing to do (depending on your sound hardware) is to up the volume to about 80 and check the 'remember volume' box. Then after you adjust your alsa mixer to appropriate levels,  just control all volume from your speakers/receiver.

> **rajeev1204 said:**
> the xine-config file is in my home folder ( hidden) , is that the problem?
btw, that file is where it is supposed to be, and is not part of the problem.

---

### Post by rajeev1204 on 2006-12-27
thanks

i have been using that remember volume option for some time now.

It works for me :) 

i prefer gxine for my video needs so i will mess around with it some more. plays everything well.

Also looks nice with gnome

---

