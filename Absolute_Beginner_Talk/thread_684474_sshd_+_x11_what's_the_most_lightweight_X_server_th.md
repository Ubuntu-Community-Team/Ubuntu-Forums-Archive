---
title: "sshd + x11: what's the most lightweight X server that can handle wine?"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by joesmith1234 on 2008-02-01
The general idea being reduction of overall graphical information to help with latency issues.

---

### Post by Origin415 on 2008-02-13
Unless you are running short on memory, the main overhead caused by environments, you really arent going to notice enough improvement to be worth the lack of features and support. Wine is slower than running natively all by itself -- not much is going to fix that.

But if this is your problem, XFCE4 (in Xubuntu) is a very lightweight, but still rather full-featured environment, and even smaller is FluxBox (in Fluxbuntu).

---

### Post by emarkd on 2008-02-13
There's really only one X-server.  There's lots of window managers and desktop environments that you can run on top of it.  FluxBox, as mentioned above, is a great choice for a lightweight window manager.  IceWM is another.  But don't expect the same features as you get with a true desktop environment like Gnome/KDE/XFCE.

If harddrive space is not an issue, you can install any window manager you want on your Ubuntu box and just select it from the sessions list in the GDM login screen.  Then you can experiment and find what works for you.

---

