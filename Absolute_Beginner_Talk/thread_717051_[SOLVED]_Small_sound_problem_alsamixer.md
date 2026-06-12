---
title: "[SOLVED] Small sound problem/ alsamixer"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by billgoldberg on 2008-03-06
Recently (I had been tinkering with the system for a few hours) my headphones wouldn't work on ubuntu 7.10 anymore. 

I opened a terminal and opened alsamixer but was unable to change the headphone settings.

I downloaded "gnome alsa mixer" and there I could turn the headphones back on.

The problem is that I have do this each time I reboot.

How would I make this permanent?

(it's only a small issue, but still)

---

### Post by herbster on 2008-03-06
Try

```
sudo alsactl store
```

That should store whatever current mixer levels you have set, permanently.

---

### Post by billgoldberg on 2008-03-06
Thanks

---

