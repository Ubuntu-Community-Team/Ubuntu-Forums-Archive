---
title: "KDE resolution problem"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by stevephp on 2007-01-24
Hi,

I've searched around here and found quite a few threads asking about resolution problem but this one seems a little different....

I installed Ubuntu a while back and have been using Gnome on it. I have a widescreen monitor with a native resolution of 1440x900 and Gnome displays this fine. 

I installed KDE-core and switched to KDE last night and now my desktop is too high! 

The 1440x900 entry is in xorg.conf and was working fine with Gnome - what's up with KDE?

thanks.

---

### Post by Canis familiaris on 2007-01-24
Perhaps try installing the kubuntu-desktop package instead of kde core.
```
sudo aptitude install kubuntu-install
```

---

### Post by stevephp on 2007-01-24
Thanks, I'll give that a try but I'm not confident it will fix the problem. Surely screen resolution / desktop sizing is a CORE feature?

---

### Post by stevephp on 2007-01-24
I found the answer to this!

I opened a console and ran *krandrtray*; it adds a screen resolution item to the system tray ( bottom right ). It was then easy to click on the new item and see what resolution was set - turns out I had not been running at 1440x900!

---

