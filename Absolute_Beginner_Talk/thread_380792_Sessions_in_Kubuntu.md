---
title: "Sessions in Kubuntu"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by charles.g.moore on 2007-03-10
I just installed the kubuntu desktop but I can't figure out how to start my nm-applet at startup.
In ubuntu it was admin>pref>sessions or something like that.
Anyone know how?

---

### Post by Crooksey on 2007-03-10
Open a terminal..

```

$ cd ~/.kde/Autostart/
$ gedit nm-applet.sh

```

Now here type the command to launch the program, then save and close.

```

$ chmod +x nm-applet.sh

```

Volia!

---

### Post by bobbob1016 on 2007-03-17
If gedit doesn't work, try kate, kate is the gedit equivalent for KDE.

---

