---
title: "How do I undo this apt-get command?"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2007-07-24
How do I undo this apt-get command?
```
sudo apt-get install libdvdcss2 w32codecs
```

I'm having troubles playing all my media files that I'm usually able to do when following this tutorial
[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)
But after having done some tinkering on my xorg.conf file my media capabilities has lowered.
So I'm trying to undo all media installs including that of Automatix and re-install from scratch.

---

### Post by Mornedhel on 2007-07-24
sudo apt-get --purge remove libdvdcss2 w32codecs

---

