---
title: "Why can parted resize HFS+ but gparted can't?"
date: 2006-06-04
forum: Apple PPC Users
---

### Post by n00bWillingToLearn on 2006-06-04
I resized my HFS+ partition using parted when I first installed Ubuntu and I was going to give Ubuntu more space using the Dapper live/"desktop" CD and gparted said HFS+ is unsupported. This could be a huge barrier for PPC users and although I assume boot camp can resize HFS+ partitions for intel macs that is just one extra step that users shouldn't have to do if parted can resize HFS+.

---

### Post by Ptero-4 on 2006-06-05
The problem seems to be that gParted assumes that parted can't resize hfs+ (which was the case some time ago), the only solution so far is to use parted for now and tell the gparted developpers that the new versions of parted support resizing hfs+ so they upgrade gparted (remember that gparted is only a GUI for parted, gParted developpers rely on guessing what features parted support to put the correct options and warnings in the GUI).

---

