---
title: "Update software manager"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by a.v.l on 2007-04-04
When I'm advised that there are software updates available to install, I  allow all of these believing that many will be security related. I understand the importance of updates but presently they are arriving  daily and have done so for some time it seems.  I've  now began to wonder about the HD space these will occupy, especially if they continue arriving at the same frequency. 

Should I be allowing every single update that I'm  informed about, or can I be more selective. Many of these udates are difficult to understand as a beginner, so I'm unsure which to allow and which not too, some advice from the more experienced would be much appreciated.

---

### Post by BarfBag on 2007-04-04
I advise updating everything.  In the long run, it won't take up much more space.  The packages it upgrades are already installed, which means that space is going to be taken anyway.

The only thing that could hog space are the actual .deb packages.  I believe it keeps them around even when it's finished with them.  There's a command to clear this up, but I can't remember it.  Perhaps someone else does?

---

### Post by Jonne on 2007-04-04
If a package is updated, the old one is removed (i think). To make sure you can always run
```
sudo apt-get autoclean
```
which will remove some unnecessary packages from your cache.

Sometimes updates aren't security related, but they're 'backported', which means they're a new versions of the package. You need to have backports enabled for this, though, which isn't the default.

---

### Post by a.v.l on 2007-04-05
Many thanks.

---

