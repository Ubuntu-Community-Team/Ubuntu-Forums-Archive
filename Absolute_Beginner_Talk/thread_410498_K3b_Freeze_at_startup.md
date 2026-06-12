---
title: "K3b Freeze at startup"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by odyssey41 on 2007-04-15
K3b is freezing at startup. When opened it just freezes ("uninterruptible" process) in conjunction with CD Audio icon that cannot be closed either. Please help.:confused:

---

### Post by Jonam on 2007-04-17
I have had this problem with k3b as well and have reported this as a bug to the k3b development team. It started to happen on my machine when the latest kdelibs (version 4c2a) was installed about two weeks ago through the automatic updates. It also happened when I first installed k3b over two months ago but at some stage, disappeared.

I believe it happens because the CD drive does not respond to a command sent to it. k3b (or kdelibs) ends up waiting forever and going into Uninterruptible state. This might be a bug in the kdelibs as I did not have this problem before.

I was lucky in finding a solution in that I upgraded from a CDR - CDRW system to a DVDRW-CDRW system. The removed CDR drive was the one not responding properly to k3b but not everyone can just go swapping drives to find one that works with k3b.

I would recommend you add your comments to the bug report found at:

[http://bugs.kde.org/show_bug.cgi?id=144286](http://bugs.kde.org/show_bug.cgi?id=144286)

Hope this helps.

Jonam

---

