---
title: "problem with games in ubuntu"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by uio on 2007-12-23
I posted this also in gaming and leisure but no replies, judging by the speed of other replies I thought I might have posted in the wrong place or something. Sorry if I am being an ***, idk.


Hi guys, I am only a semi-noob, but not that good. I dont know exactly what I need to do with these problems when I tried to run these games to try out my system

desktop:~$ spring
Aborted (core dumped)
desktop:~$ neverball
ALSA lib pcm_dmix.c:864snd_pcm_dmix_open) unable to open slave
Sound disabled
Aborted (core dumped)
desktop:~$

The games dont load at all

I know its probably a driver issue, but I dont know. Please help

When I reconfigured ALSA I didnt have any errors, but I dont have sound except in Wine

I am pretty sure xorg is configured alright, probably a sound card driver issue

Using a C-media cmi-8738

Thank you, sorry I am long winded

---

### Post by Slingshot on 2007-12-23
Hi there. probably not enough information here to point to a direct problem. Could tell us if you have problems playing music, playing a 2D game like one that come in a default Ubuntu install (with sound). Is your 3D acceleration working (glxinfo | grep direct will tell you if it is working).

---

### Post by uio on 2007-12-23
-desktop:~$ glxinfo | grep direct
direct rendering: Yes

games work, but chess wont do 3d, I need to install Open Gl python bindings and such.

I'll look into installing these, hopefully his is the problem, would fit because games I am trying to play are 3d. Thanks

---

### Post by uio on 2007-12-23
I could install everything but gtkglext python bindings, for which I get an error (1) problem, whatever that is

---

### Post by Slingshot on 2007-12-24
I'm thinking this is 2 errors you are having.

```
desktop:~$ neverball
ALSA lib pcm_dmix.c:864snd_pcm_dmix_open) unable to open slave
Sound disabled
```

That's a ALSA error have a look at this [http://ubuntuforums.org/showthread.php?t=601522&highlight=pcm_dmix]("http://ubuntuforums.org/showthread.php?t=601522&highlight=pcm_dmix")

```
Aborted (core dumped)
```

That's the one we need to isolate. 

1) post your general system specs (32bit/64bit, video card make and model etc)
2) confirm your 3D is working with
```
glxgears
```
3) Post your /etc/X11/xorg.conf

> When I reconfigured ALSA I didn't have any errors, but I dont have sound except in Wine

Think by default Wine uses OSS not ALSA for sound. that maybe why you have sound in under Wine .. What did you use to test for sound under Wine BTW?

---

