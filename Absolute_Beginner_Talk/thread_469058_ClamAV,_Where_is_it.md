---
title: "ClamAV, Where is it?"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by SegMat on 2007-06-09
Hello everyone, I'm new to this so be nice!  I've been running Windows for a long time and just recently switched to Ubuntu after trying Simply Mepis for a while and not liking it.  The Gnome interfaces is simply amazing and I love how the package manager works.  My only question is where is ClamAV?  I can't find it in the package manager or in the menu's at the top of the screen.  I'm wondering where to get it from, how to download/install it and/or if there's a better Anti-Virus for Ubuntu.  I know that virus' aren't really a huge issue for Ubuntu but I don't want to become a spreader of virus' to my Windows friends through email and the like.  Please help me with this and keep in mind that I'm a total newbie and have no knowledge of command line or anything so installers have to be VERY user friendly or the instructions have to be very detailed.  Thanks again and kudos to everyone here, long live open source!

Matt Segstro

---

### Post by Outrunner on 2007-06-09
Simply open a termial and type 
```

sudo aptitude install clamav
```

EDIT:

Then you should be able to start it with 
```

clamav
```

If it asks you for root permissions start it with

```
gksudo clamav
```

---

### Post by ggaaron on 2007-06-09
Install klamav with this - clamav is cmd line only.

---

