---
title: "no sound after update today"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by Tucatts on 2006-09-15
I downloaded the updates and now no sound at all. I can boot the os just fine and nothing else seems to be wrong just the sound. I go to updates and after checking my system it says I am up to date. I also went to terminal and put in sudo apt get update and it ran quite a bit of information. Said DONE and that was that. This is the second time a update has broken my OS, kinda makes you nervous about doing any updating. 
Anyway, what do i do to get my sound back?
Tucatts

---

### Post by Najand on 2006-09-15
Hmm, run:
```

sudo alsamixer

```
and try to change the master volumes/etc and see if it workks or not.

---

### Post by xpod on 2006-09-15
Is mine broke?....i just need to type "alsamixer" without the "sudo"?
Should that happen?

---

