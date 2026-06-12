---
title: "FIXED/WORKAROUND: Random Lock Ups"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by davidork on 2008-03-21
So recently I upgraded from a AMD Athlon 3800+  (single core) to an Opteron 185 (dual core) 
I started randomly experiencing lockups. I checked the forums and it seemed as though a lot of people have the same problem mainly with dual core AMD processors.

I've found a fix that stops the random hangs completely, though it comes at a cost:
```
sudo apt-get remove powernowd
```

You'll lose cpu frequency scaling, but you won't lock up randomly either.

I would submit a bug report, but i have no clue as to whats wrong with powernowd, all i know is it seems to cause my system to randomly lock up.

Hopefully this will help someone out.

---

