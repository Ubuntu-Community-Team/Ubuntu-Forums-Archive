---
title: "Hard drive full?"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by Ashtoreth on 2007-08-16
I have a 60gb hard drive with a reasonably new install of Ubuntu on it.  The hard drive is aparrently full.

A few days ago I copied about 40gb of music to my home folder, today I deleted it through nautilus.  I then emptied my trash, but the drive is still full.  Using du and df I managed to track the problem down to /root/.Trash, where all the music files I had copied there seem to have been put.  Problem is I can't remove these files, if I try doing rm -rf /root/.Trash I get 'permission denied.'

Any suggestions?

---

### Post by schorsch on 2007-08-16
Try

```
sudo rm -rf /root/.Trash/*
```

and enter your password.

---

