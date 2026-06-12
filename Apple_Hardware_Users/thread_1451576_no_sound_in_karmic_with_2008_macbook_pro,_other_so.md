---
title: "no sound in karmic with 2008 macbook pro, other solutions haven't worked"
date: 2010-04-10
forum: Apple Hardware Users
---

### Post by phytophilous on 2010-04-10
Hey all,

I'm running an ubuntu partition on a 2008 MacBook Pro 2.4Ghz Duo. I recently upgraded procedurally from Hardy, in which my sound worked fine. I searched around these forums and on google and found some similar issues, but none of the proposed solutions worked for me. I've tried removing pulse, installing oss, recompiling alsa, backporting alsa, backporting the linux kernel, and none of it has worked. Right now I am back to the -20 kernel and most recent version of alsa, alsa-oss and alsa-utils.

As things stand right now I get the following message from aplay -l:

> aplay: device_list:223: no soundcards found...


And this from alsamixer:

> alsamixer: function snd_ctl_open failed for default: No such file or directory

Any help would be greatly appreciated!

Thanks <3

---

### Post by cph05a on 2010-04-10
I have a macbook pro 5, 5 and had the same problem with karmic. I ended up using lucid. I've been using it since alpha 3 and things have been going well. If you need this computer for work, don't install lucid until April 29th (the full release will be out then).

Maybe someone else knows how to get it working in karmic :-?

---

### Post by phytophilous on 2010-04-10
My ubuntu partition is purely for recreational exploration and aesthetics so I may give lucid a shot. Thanks :)

---

