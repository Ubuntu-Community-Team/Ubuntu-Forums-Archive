---
title: "How to change screen resolution...?"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by tbasherizer on 2006-08-10
Hey, I'm new here, and I have dual-booted windows xp and ubuntu on two hard drives. On Ubuntu, everything is way too big for my screen,like my desktop only fits like 4 icons, and I cannot see the entirety of pop-up windows. I tried changing the resolution, but there was only one option for resolution: 800by600. I was wondering if I could use Terminal to change the resolution.

Thanks a lot for any replies

---

### Post by GuitarHero on 2006-08-10
sudo dpkg-reconfigure xserver-xorg
Do that, and select more screen resolutions when the screen comes up.  There are many things in there, only change the resolution part.  Then you can select higher rez resolutions.

---

### Post by Jagot on 2006-08-10
Try this from the terminal:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by tbasherizer on 2006-08-10
Thanks guys.

---

