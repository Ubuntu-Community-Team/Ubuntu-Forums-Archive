---
title: "desktop multiplier? uhoh"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by ahervey85 on 2008-01-20
okay i was updating some packages and now i have a problem. ubuntu keeps rebooting (im on vista now) i think the program desktop multiplier was checked off and i rebooted before could change it. could this be my problem or something else? is there any way i could go into recovery console and undo what i did? if you need more info i will try to give it to you. if anyone can help?

---

### Post by shearn89 on 2008-01-21
you could try booting into recovery mode, and running apt-get with no parameters:
```

sudo apt-get

```
I think it makes it try and fix any broken dependencies...

---

