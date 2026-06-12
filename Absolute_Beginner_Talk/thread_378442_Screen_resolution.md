---
title: "Screen resolution"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by essendon on 2007-03-07
I have a nvidia video card.  It's a geforce2 MX 100.  For some reason it's stuck at 640x480.  I know it can do better than that.  How do I get better resolutions?

I do know how to change the resolution, but it won't let me

---

### Post by Kateikyoushi on 2007-03-07
First try this to reconfigure X, after that I would install the nvidia driver.

```
sudo dpkg-reconfigure xserver-xorg
```

---

