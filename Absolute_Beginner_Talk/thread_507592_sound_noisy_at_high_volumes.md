---
title: "sound noisy at high volumes"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by tech_cheetah on 2007-07-23
When i play mp3 files (in VLC or Totem player ), the sound is a bit noisy at full volume on my laptop (keeping Master and PCM to the max) . The sound is however fine at max level on windows.
I have compiled alsa libraries,core and util but the problem is still there.
I have conexant sound module in my hp dv6114tx laptop .
any suggestions how to remove this problem !!

---

### Post by WinterWeaver on 2007-07-23
It seems as though this is a common problem. I see it everywhere lol .... My sound does the same, and it doesn't seem as though developers are gonna fix it soon. I just live with it, and keep my sound levels down a bit. I even installed Ubuntu Studio, with the hopes that it will fix the problem, but it didn't.

maybe there is someone out there that knows of a proper solution, (other than "take the levels down)

Good Luck

WW

---

### Post by 3rdalbum on 2007-07-23
The correct solution is to turn down the PCM channel a little bit. You can have the master at 100%, as long as the PCM is down a bit.

---

### Post by Inxsible on 2007-07-23
> **tech_cheetah said:**
> When i play mp3 files (in VLC or Totem player ), the sound is a bit noisy at full volume on my laptop (keeping Master and PCM to the max) . The sound is however fine at max level on windows.
I have compiled alsa libraries,core and util but the problem is still there.
I have conexant sound module in my hp dv6114tx laptop .
any suggestions how to remove this problem !!
 
Have you changed your audio output from ALSAMixer to Linux OSS in VLC ?
 
VLC - Settings - Preferences - Audio - Output modules. Enable the advanced options and then change the sound output. That worked for me.
 
I didnt have that problem in Totem, so I dont know how to fix it in Totem :(

---

