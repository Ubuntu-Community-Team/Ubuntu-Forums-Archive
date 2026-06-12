---
title: "[SOLVED] help with compiz"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by xxxYURAxxx on 2008-02-05
in my pc with ubuntu 7.10 installed:
1. nvidia-glx
2. nautilus and emerald
3. compiz-*

after F2 and compiz --replace
no scenery windows(window border)

---

### Post by lduplantie on 2008-02-05
You may want to read this thread
[http://ubuntuforums.org/showthread.php?t=685636](http://ubuntuforums.org/showthread.php?t=685636)

---

### Post by overdrank on 2008-02-05
> **xxxYURAxxx said:**
> in my pc with ubuntu 7.10 installed:
1. nvidia-glx
2. nautilus and emerald
3. compiz-*

after F2 and compiz --replace
no scenery windows(window border)

HI and yes as lduplantie linked you may only need to add 

```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```

Edit if you need more help then post the output of this command cat /etc/X11/xorg.conf

---

### Post by xxxYURAxxx on 2008-02-06
solved with install nvidia-glx-new

---

