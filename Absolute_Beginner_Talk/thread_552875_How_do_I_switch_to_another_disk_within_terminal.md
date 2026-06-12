---
title: "How do I switch to another disk within terminal?"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by Rev4n on 2007-09-17
I know that the command cd can be used to bring you up and down directories, but I'm having trouble navigating to my external HD by means of the terminal.  the furthest up I get just brings me to the home folder.  Is there any special way to do it, or am I just really dumb?

The drive is FireWire, if that makes a difference.

I just recently installed Linux and I'm still kind of figuring it all out.

Thanks!

---

### Post by andrewPCT on 2007-09-17
To get to the root directory, enter: cd /
In most cases, your external disk is mounted at /media/disk, which you can get to using: cd /media/disk

---

### Post by Rev4n on 2007-09-17
thank you very much!

---

