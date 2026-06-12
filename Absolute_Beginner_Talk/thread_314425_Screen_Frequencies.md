---
title: "Screen Frequencies"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by dupa on 2006-12-07
Hello
I have a CRT monitor.
I have taken a look in xorg.conf and there are the resolution and color depth supported.
I have not found any row about the supported frequencies.. where are they stored?
thanks.

---

### Post by ahaslam on 2006-12-07
Under: *Section "Monitor"*
You should have something like:* HorizSync 31.5 - 50.0 / VertRefresh 40-90*
It should use the highest possible in the given range.

Tony.

---

