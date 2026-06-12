---
title: "Why do updates mess up menu.lst?"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by Patrick K on 2007-04-18
It happen again. Every time there is some update to the kernel, headers this time, menu.lst gets scrambled. Ubuntu is installed on hda11. It has been since start. Yet, these updates change menu.lst to another partition. This time it decided that hda8 and hd0,8 (which isn't even the same partition) is where Linux resides. I know how to fix the problem but I wonder why it does this. Does anyone else have this problem?

---

### Post by confused57 on 2007-04-18
> **Patrick K said:**
> It happen again. Every time there is some update to the kernel, headers this time, menu.lst gets scrambled. Ubuntu is installed on hda11. It has been since start. Yet, these updates change menu.lst to another partition. This time it decided that hda8 and hd0,8 (which isn't even the same partition) is where Linux resides. I know how to fix the problem but I wonder why it does this. Does anyone else have this problem?

See what your groot & kopt lines show:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

see the relevant sections on this page

---

### Post by Paradoxdruid on 2007-04-18
Yeah, one of the latest kernel updates rebuilt my menu.lst changing it from hd(0,2) to hd(0,0).

That would be a "end game" for a less experienced user, since safe mode, memtest, etc all failed to boot afterward, until corrected via command line in grub.  

Looking at my menu.lst, it appears the groot setting is at fault.  Thanks for the tip!

How could groot be auto-updated, or would that create more porblems then it solves?  Hmm...

---

### Post by Patrick K on 2007-04-18
Thanks for the link. Both groot and kopt were pointing to the wrong partitions. 

Early on in my Ubuntu live, a reinstall renamed the partitions, that was fun to track down, but the liveCD and GParted came to the rescue. That could be where the groot and kopt errors came from.

Glad to get this resolved before the Feisty upgrade.

---

