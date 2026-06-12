---
title: "[SOLVED] How do I make apt save all downloaded packages?"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by skippy_1 on 2008-01-29
As in when you install something or upgrade and all, is there a limit on how many of the packages get saved in /var/cache/apt ? Can I remove the limit?

---

### Post by Rocket2DMn on 2008-01-29
There is a program called *apt-cache* which you should already have installed.  I believe this is what you're looking for.

---

### Post by skippy_1 on 2008-01-29
I see the program but am not sure how to set to allow an unlimited cache?

---

### Post by FuturePilot on 2008-01-29
I think the only limit is on physical disk space.

---

### Post by skippy_1 on 2008-01-29
Thanks! that's what I wanted to know:)

---

### Post by Rocket2DMn on 2008-01-29
I don't think the cache ever cleans itself unless you tell it to with either
```
sudo apt-get autoclean
or
sudo apt-get clean
```
Otherwise, everything you download should stay in the cache.

---

