---
title: "[SOLVED] Distorted video. Need some help pls."
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by Ronjr on 2007-12-02
I was in windows the other day and I restarted so I can get into ubuntu. After I selected which OS I wanted the pop up that I got before came up. It said that the it basically said that it was going into low quality video mode or something like that. So it loaded to desktop at 800 x 600. I went into graphics and screens and chose the video driver and then selected the monitor type and I picked the closest model, I have a MAG 778PF-s and I selected 770. Anywas this worked for me before when this happened after trying to fix my mouse back/forward buttons but this time it did not work and only made things worse. I have very distorted video in ubuntu, I cant see anything just the beige color and white. This only happens in ubuntu. 

How can I fix this?

---

### Post by Ronjr on 2007-12-02
Also, I know my video might not be the best for ubuntu but it did work fine for me for 2 days. I have onboard Radeon Xpress200, which is propiotary to HP's MB from asus.

---

### Post by Ronjr on 2007-12-02
I've been searching on here and I still haven't found anything. If anybody can help me it would be much appreciated.

If nothing else I will just reinstall it.

---

### Post by overdrank on 2007-12-02
> **Ronjr said:**
> I've been searching on here and I still haven't found anything. If anybody can help me it would be much appreciated.

If nothing else I will just reinstall it.

Hi and have you tried to configure your xorg from recovery mode. ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Ronjr on 2007-12-02
I went into recovery mode but I'm new and didn't have a clue as to what to do.

Is that all I have to do? Will there be any other steps?

---

### Post by overdrank on 2007-12-02
> **Ronjr said:**
> I went into recovery mode but I'm new and didn't have a clue as to what to do.

Is that all I have to do? Will there be any other steps?

It may ask you to choose resolutions but yea, I hope this helps as it beats reinstalling. :KS
Edit and  of  course reboot

---

### Post by Ronjr on 2007-12-02
Your a god! lol

That worked. I really appreciate your help.

---

### Post by overdrank on 2007-12-02
> **Ronjr said:**
> Your a god! lol

That worked. I really appreciate your help.

Thanks and great, please mark the thread as solved under thread tools and good luck! :KS

---

