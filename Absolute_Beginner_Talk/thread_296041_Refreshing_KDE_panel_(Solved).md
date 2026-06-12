---
title: "Refreshing KDE panel (Solved)"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by LLRNR on 2006-11-09
Hi all !

I don't know wether it's correct to say "KDE panel", please excuse me for my ignorance, but I have installed kubuntu-desktop for only a few days ; I like it very much, I made KDM default, but the only thing that kind of bothers me is that I'm not able to find an equivalent for the command ```
killall gnome-panel
```
What I'd like to get is the same effect as in Gnome, i.e. to restart the "KDE panel" without ending my session (without having all my apps closed and without having to re-login). Would this be possible ?

Thanks in advance,

LLRNR

---

### Post by aysiu on 2006-11-09
I know there's one command that does this, but I can't remember what it is. In the meantime, try this: ```
killall kicker
kicker
```

---

### Post by LLRNR on 2006-11-09
Alright aysiu, that did it ! Thanks, I had no idea of kicker. (whoa it scared me a little since it showed a lot of X Errors, but eventually it _does_ its job...)

LLRNR

---

### Post by Jucato on 2006-11-09
or

```
dcop kicker kicker restart
```

---

