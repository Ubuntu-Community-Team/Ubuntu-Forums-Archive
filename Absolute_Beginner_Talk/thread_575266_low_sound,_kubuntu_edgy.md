---
title: "low sound, kubuntu edgy"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by baja munda on 2007-10-13
While playing music on Amarok (or flash files), the volume is barely audible, this when all volume control is set to max.

Interestingly when playing the same music file through real player, there is no such problem.

What might be the issue?

---

### Post by baja munda on 2007-10-14
*bump*

---

### Post by strabes on 2007-10-14
```
amixer set Master 150 unmute
```

If that doesn't work, run "alsamixer" and make sure nothing is muted and everything is turned up. If something is muted "MM" will appear below its slider. To unmute it, press m.

---

