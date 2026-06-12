---
title: "[SOLVED] Audacious stoped workign after xmms removed"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by saj0577 on 2008-04-15
Audacious stopped working when upgraded it and removed xmms.


Eroor when click play in audacious
```
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
MADPlug-Message: failed to open audio output: XMMS reverse compatibility output plugin

```

What plug in is it i need?

Saj

---

### Post by game_plan on 2008-04-15
I use adacious on my systems and its always a pain to get it to work on Fedora for whatever reason. I think your's is asking for libmad.dev

If that doesn't work I would just reinstall audacious and plugins from package manager

---

### Post by saj0577 on 2008-04-15
Total uninstall then installed again. Sometimes best way.

Saj

---

### Post by javaguru on 2008-06-19
actually you just need to :
1. Uninstall audacious
2. Remove the old configuration directories which reside in your home dir
3. Reinstall audacious

> 
adyhasch@jenna:~$ apt-get remove audacious
adyhasch@jenna:~$ rm -r .audacious/ /home/adyhasch/.config/audacious /home/adyhasch/.cache/audacious  home/adyhasch/.local/share/audacious /home/adyhasch/.local/share/applications/audacious-usercustom-usercustom-1.desktop
adyhasch@jenna:~$ apt-get install audacious


now you've hopefully wiped all traces of audacious, and got a clean install.

---

