---
title: "powerbook wallstreet problem"
date: 2007-05-31
forum: Apple PPC Users
---

### Post by richaoj on 2007-05-31
Dear All,
After many excruciating hours or dealing with Bootx etc, i finally have ubuntu 6..06 (Dapper) PPC booting up on an Old-World Powerbook G3 Wallstreet. The login screen pops up perfectly. I even have gotten good video. However, nautilus won't start, because of some error with the bonobo activation server.

The comand line output is:
```

Bonobo-Activation-Warning **: Strange exception (IDL:omg.org/COBRA/COMM_FAILURE:1.0) from active server registration
ALSA lib confmisc.c:672:(snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function and snd_func_concat returned error: No such device
ALSA lib confmisc.c:1072: (snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function send_func_refer returned error: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default

```
Does anyone have any clue as to what this means!?
Does ubuntu not know about my sound card or something?
Is there a way to disable sound and then login anyway?


This is a new install--haven't tweaked any settings yet or anything . . .

Thanks in advance for the help. =)

---

### Post by richaoj on 2007-05-31
I solved my issue -- the powerbook has a dead pram battery, and the date was set to 1922.  apparently, ubuntu doesn't like that . . .

---

