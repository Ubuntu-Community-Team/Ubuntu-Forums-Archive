---
title: "xserver restarting"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by rmalleman on 2007-01-14
A few days ago there was an update of some sorts to xserver on Synaptic.  Ever since then, everytime my laptop wants to go screensaver it restarts x-server like i pressed ctrl-alt-backspace.  It's really annoying especially since I have to sit and babysit the terminal when im doing time-intensive compiling.  Is anybody else having this problem since the update?

---

### Post by oyvindaa on 2007-01-15
Maybe a

```
dpkg-reconfigure xserver-xorg
```

would sort it out?

You could always roll back the version though.

You could also try searching for 'xserver+restart' on the forum, people might have had the same problem :)

---

