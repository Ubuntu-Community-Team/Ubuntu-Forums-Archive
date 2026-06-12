---
title: "slow frame rate... Mesa GLX Indirect..."
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by 88ivorykeys on 2007-11-04
Hi, i just upgraded to gutsy the other day, and with it i got my brothers old video card (Mesa GLX Indirect). (i overheard him saying while he was doing the install that it wasn't current, which im not too surprised at... >.>) I do know that it does 3D though, but whenever I run glxgears, it runs smoothly for like 1.5 seconds, then starts jumping...
```
~$ glxgears
456 frames in 6.3 seconds = 71.830 FPS
339 frames in 5.5 seconds = 61.887 FPS
339 frames in 5.5 seconds = 61.883 FPS
339 frames in 5.5 seconds = 62.036 FPS
339 frames in 5.5 seconds = 61.958 FPS
339 frames in 5.5 seconds = 61.873 FPS

```

whenever i try to run tuxracer, it jumps as well.. and when i try to iniate compiz (just the normal setting) it says that it cannot be enabled.

how can i get glxgears to run smoothly? and get compiz to work? and games like tuxracer to run smoothly?
..
..
..
help? (plz use simple linux terms, as im still in the learning process) thanks!

---

### Post by 88ivorykeys on 2007-11-19
i realized the other day... my video card isnt Mesa GLX Indirect... 
It is a _Viper II_ card made by *Diamond Multimedia.*

OpenGL works great in windows 2k (quake 3 arena)... but i guess not in linux..?

---

### Post by avik on 2007-11-19
> **88ivorykeys said:**
> i realized the other day... my video card isnt Mesa GLX Indirect... 
It is a _Viper II_ card made by *Diamond Multimedia.*

OpenGL works great in windows 2k (quake 3 arena)... but i guess not in linux..?

I'm not sure if the mesa drivers support hardware accelerated 3d, but maybe there's some driver out there for Linux?  I couldn't find anything on Google though.

---

