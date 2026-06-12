---
title: "V4l drivers not loading at startup"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by elbeasto on 2006-10-26
Hi,
I finnaly managed to get my Dvico Fusion HDTV Hybrid up and running using the v4l drivers. I found that Kaffeine was the only program that worked with digital (haven't tried mythtv yet). Kdetv, tvtime and xawtv work with analog but with no sound.

The problem is that every time I reboot I have to go to the v4l-dvb directory and type:

```
sudo make reload
```

before Kaffeine will have the dvb button enabled.

How do I get these drivers to load at startup?

Thanks

---

