---
title: "[SOLVED] no advanced desktop effect settings"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by ssharps711 on 2008-02-05
My Advanced desktop effect settings is gone. And even when I go into Appearance>Visual Effects>Custom the preferences won't come up. Just won't open.

---

### Post by emarkd on 2008-02-05
Try running it from the command line and looking for error messages:

```
ccsm
```

---

### Post by ssharps711 on 2008-02-05
```
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'
```

Huh?

---

### Post by emarkd on 2008-02-05
Huh, never seen that before.  Maybe uninstall compizconfig-settings-manager and reinstall it.

---

### Post by ryanVickers on 2008-02-05
yea, theres something wrong with one of it's python dependencies...

---

### Post by ssharps711 on 2008-02-05
It's a common bug I just googled it. Any suggestions?

---

### Post by emarkd on 2008-02-05
I've never experienced it.  Did you try removing and reinstalling compizconfig-settings-manager?

---

### Post by ssharps711 on 2008-02-05
K. I # out all eye candy in sources.list. Then uninstalled all compiz then installed them and took #'s out.

It's good now.

Weird.

---

### Post by emarkd on 2008-02-05
Wow, I'm glad you got it fixed, but you all you should'vehad to do was

```
sudo apt-get install --reinstall compizconfig-settings-manager
```

---

### Post by ssharps711 on 2008-02-05
lol. I'm new, and coming from XP, so you can probably imagine that I overthink Linux.

---

### Post by emarkd on 2008-02-06
Don't worry about it.  You got it handled.  Just tuck that away in case you've got a recurring bug that comes up again in the future.  It's probably a lot saver alternative that ripping out all of compiz.

---

