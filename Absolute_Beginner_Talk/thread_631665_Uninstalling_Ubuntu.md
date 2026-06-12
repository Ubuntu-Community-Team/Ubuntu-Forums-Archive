---
title: "Uninstalling Ubuntu"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by Totem_NZ on 2007-12-04
Okay, don't shoot me. I have Vista. Installed Ubuntu on the whole laptop. How do I get rid of it, so I have Vista back, and then can reinstall, setting aside a partition for Windows progs that are uncompatible with Ubuntu (e.g. editing software).

I don't have a recovery disk.

---

### Post by Xavieran on 2007-12-04
Boot into the LiveCD and open GParted in System>Administration>GParted (It could be called Partition editor if you're using Gutsy Gibbon) .

Look for the "ext3" partition on the hard drive diagram and click delete at the top of the partition editor...then do the same thing for the "Linux Swap" and "Extended" partitions in that order or it won't let you delete them.

Whatever you do DO NOT touch the ntfs partition...doing so will get rid of vista.

---

