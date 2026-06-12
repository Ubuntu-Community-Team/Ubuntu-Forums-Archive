---
title: "Sansa dansa"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by phantalon on 2007-12-04
My sansa e250 won't show up...i'm noticing alot of questions about this here...does it have anything to do with processor speed? rhythmbox will open when i plug in sansa but then it just closes. And Amarok wont recognize it at all, says something dbus not activated or something ...it doesn't show up as a drive at all...1.86 celeron, 2 G ram laptop.

---

### Post by p_quarles on 2007-12-07
Dbus and USB devices seem to be an ongoing problem with the Linux kernel. I had a similar problem with a USB flash drive once, and was able to fix it by restarting dbus (and never had that problem again). If things go well, this will do the trick:
```
sudo /etc/init.d/dbus start
```
If that returns an "already running" error, try this one instead:
```
sudo /etc/init.d/dbus restart
```
Hope that fixes it.

---

