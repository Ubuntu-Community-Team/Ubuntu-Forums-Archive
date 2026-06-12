---
title: "Xubuntu - python inexplicably eating up CPU"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by Fraoch on 2007-08-10
I've recently installed Xubuntu on an old machine (AMD K6-2 400 MHz, 192 MB RAM).

For its age, it runs Xubuntu pretty well.  But about once every 10 minutes or so, it just locks up at 100% CPU for several minutes at a time.

"top" indicates it's python taking up all this CPU.

But I have not consciously installed any python apps.  I suppose this is caused by a system-installed tool that uses python.  How do I determine which python application is calling python and blocking everything up?

Hint/possible red herring: just before this happens, my keyboard goes funny - the key I'm pressing gets repeated as if I'm holding it down.

Thanks!

---

### Post by Hobo Joe on 2007-08-24
I'm having this same problem in Ubuntu. After a while it just starts maxing out one of the cores on my CPU, while the other hovers between 5 and 20, even when I'm doing nothing.

I'd like to know what causes this.

Also, gnome-panel is taking up 340 MB of memory, and java is taking up 110.

---

