---
title: "how to install DMG file?"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by adi_das on 2008-02-08
how to install DMG file? please tell how to install the  file for firefox in ubuntu 7.10?

File name: divxwebplayer.dmg

---

### Post by Dr Small on 2008-02-08
Where did you get that file from?

---

### Post by lswest on 2008-02-08
i believe dmg files are mac files, and so can't be installed in Linux or windows

---

### Post by adi_das on 2008-02-08
from stage6.com

---

### Post by click4851 on 2008-02-08
isn't that an Apple file format, why would you want to load that?

---

### Post by wheredidrealitygo on 2008-02-08
.dmg files are mac disk images, they will not work properly.

if you want to enable divx web player in firefox, you need to symlink your /usr/lib/mozilla/mplayerplug-in-dvx.so and  /usr/lib/mozilla/mplayerplug-in-dvx.xpt to /usr/lib/firefox/mplayerplug-in-dvx.so and /usr/lib/firefox/mplayerplug-in-dvx.xpt respectively.

---

### Post by banished_one on 2008-02-08
dmg it the apple disc image format, i found this after a quick search hope it helps 
[http://dmg2iso.sourceforge.net/Home.html](http://dmg2iso.sourceforge.net/Home.html)

---

### Post by macogw on 2008-02-08
> **wheredidrealitygo said:**
> .dmg files are mac disk images, they will not work properly.

if you want to enable divx in firefox, you need to symlink your /usr/lib/mozilla/mplayerplug-in-dvx.so and  /usr/lib/mozilla/mplayerplug-in-dvx.xpt to /usr/lib/firefox/mplayerplug-in-dvx.so and /usr/lib/firefox/mplayerplug-in-dvx.xpt respectively.
Translation:
```

cd /usr/lib/mozilla
sudo ln -s mplayerplug-in-dvx.so mplayerplug-in-dvx.xpt
cd ../firefox
sudo ln -s mplayerplug-in-dvx.so mplayerplug-in-dvx.xpt

```

---

### Post by wheredidrealitygo on 2008-02-08
> **macogw said:**
> Translation:
```

cd /usr/lib/mozilla
sudo ln -s mplayerplug-in-dvx.so mplayerplug-in-dvx.xpt
cd ../firefox
sudo ln -s mplayerplug-in-dvx.so mplayerplug-in-dvx.xpt

```

Correction:

```
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so /usr/lib/firefox/plugins/mplayerplug-in-dvx.so
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt /usr/lib/firefox/plugins/mplayerplug-in-dvx.xpt
```

Sorry, forgot the plugins directory. macogw, your code would have linked the .so to the .xpt within the same directory, slightly messy ;)

---

### Post by macogw on 2008-02-08
> **wheredidrealitygo said:**
> Correction:

```
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so /usr/lib/firefox/plugins/mplayerplug-in-dvx.so
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt /usr/lib/firefox/plugins/mplayerplug-in-dvx.xpt
```

Sorry, forgot the plugins directory. macogw, your code would have linked the .so to the .xpt within the same directory, slightly messy ;)

*shrug* I just translated the "symlink x to y" into code.  Idk where the files *actually* go :P

---

