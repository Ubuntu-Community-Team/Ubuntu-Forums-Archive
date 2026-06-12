---
title: "Yet another sound problem.... but this one is odd."
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by Codix121 on 2007-10-14
Ok, so I fixed my sound about 4-5 days ago using a tutorial i found on here.
everything was fine, until today..

I mean even this morning, i was listening to music.
well then, I tried playing some music and I got no sound...

and I tried using this tutorial:

[http://ubuntuforums.org/showthread.php?t=568463](http://ubuntuforums.org/showthread.php?t=568463)

to fix the prob.

now when i move my sound wheel,
the levels dont even go up or down, it's just full.

and when i try to play music i get an
Error output plugin something like that (I included a screenshot)

If you guys can help, thanks.

---

### Post by djchandler on 2007-10-15
> **Codix121 said:**
> Ok, so I fixed my sound about 4-5 days ago using a tutorial i found on here.
everything was fine, until today..

I mean even this morning, i was listening to music.
well then, I tried playing some music and I got no sound...

and I tried using this tutorial:

[http://ubuntuforums.org/showthread.php?t=568463](http://ubuntuforums.org/showthread.php?t=568463)

to fix the prob.

now when i move my sound wheel,
the levels dont even go up or down, it's just full.

and when i try to play music i get an
Error output plugin something like that (I included a screenshot)

If you guys can help, thanks.

Use Synaptic to install the missing ALSA plug-in.

DJ

---

### Post by Codix121 on 2007-10-16
I couldnt find the plugin I went to the XMMS website,
but it wasnt available..

I really need to fix this..

and also, i get Ubuntu -16 and 15 in my boot menu....
idk why I have two..

---

### Post by djchandler on 2007-10-17
> **Codix121 said:**
> I couldnt find the plugin I went to the XMMS website,
but it wasnt available..

I really need to fix this..

and also, i get Ubuntu -16 and 15 in my boot menu....
idk why I have two..

This could be a hardware problem. Those ALSA drivers and plug-ins should install by default in Ubuntu.

If you have used update manager to update the kernel, that's why you are getting  GRUB menu choices.

DJ

---

