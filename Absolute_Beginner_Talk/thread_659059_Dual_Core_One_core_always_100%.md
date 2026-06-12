---
title: "Dual Core One core always 100%"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by gentlemanmasher on 2008-01-05
I have a dual core AMD Opteron model 170. I have my system dual booting with Windows.  I had to clear my cmos to reinstall windows (long story).  Anyway now my first core on my processor is always at 100%.   This is causing programs to shut down in mid use.  When I look in my running processes it says I only have 3 and Python is using 50 percent of the CPU.

What could be causing this?

---

### Post by skymera on 2008-01-05
go to terminal and type

```
 top 
```

and look what is uising the precious cpu

---

### Post by gentlemanmasher on 2008-01-05
Looks like's it' Python.  Should this be taking up 100%?  What can I do to fix this?

---

### Post by spydon on 2008-01-05
> **gentlemanmasher said:**
> Looks like's it' Python.  Should this be taking up 100%?  What can I do to fix this?

You can try kill python and see if it works better...

---

