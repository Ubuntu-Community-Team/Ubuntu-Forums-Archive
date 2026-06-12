---
title: "no sound on a compaq presario"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by Timmy66 on 2007-07-27
A fresh install of feisty on a compaq presario 5240.
1869 ESS audio drive,on-board sound.

Install went flawlessly with no problems.Except it got the cluster size wrong on my different  partitions.
what can I do to get my sound up.Other then that I love ubuntu.

---

### Post by ReaderRat on 2007-07-28
Try:
```
aplay -l
```The "l" is a lower case "L".
tosee if your on-board sound is recognized.

---

