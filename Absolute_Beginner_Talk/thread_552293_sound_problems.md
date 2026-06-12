---
title: "sound problems"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by CrazY^ on 2007-09-16
hi there ...i ve got some problems with the sound .. when i enter in cs16 steam with wine idont have any sound and when leave the game i dont have sound , plz help me
Note: beforce enter the game i have sound

---

### Post by vinutux on 2007-09-18
Plz understand WINE is still in development and in beta stage (not stable)

it is usually crashed.............

i think wine crashed with u r sound daemon (ie alsa)

restarting is the best solution............

but u have 3 solutions

1.dont use wine

2.use commercial counterpart of wine such as "cedega" crossover office

3. use emulaters such as virtualbox or vmware to play windows games

......................................

but that is not least

try this too

update wine to latest version 
 apt-get update wine

and install additional wine programs such as xwine with it

apt-get install xwine
apt-get install wine-utils:popcorn:

---

### Post by Daveth on 2007-09-18
are you

"Use the ALSA driver - Some games do require OSS to work, but unless absolutely required, always use ALSA. The OSS driver is no longer being developed and Wine's Alsa support is currently under very active development. Each new release of Wine includes significant sound improvements for ALSA."

[http://ubuntuforums.org/showthread.php?t=497332](http://ubuntuforums.org/showthread.php?t=497332)

the option would be in 

```
winecfg
```

---

