---
title: "AcidRip problem"
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by sYs^ on 2006-03-27
Hi!

I'd like to rip some of my DVDs to .avi but when I read a DVD with AcidRip which was written by one of my friends from an .iso image it writes (original discs are working fine):

**AcidRip message - Can't read DVD track. Faulty Disc?**

AcidRip uses lsdvd so perhaps this is the reason of the problem.

```
dani@ubuntu:~$ lsdvd -t 27 -a -s -O h
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Can't open file VTS_02_0.IFO.
Can't open ifo 2!
dani@ubuntu:~$
```

But the DVD is working fine when I play it simply in mplayer for example.

Any ideas?

---

### Post by sYs^ on 2006-03-28
Problem resolved by k9copy, I recoded it and after that everything went fine.

---

