---
title: "Low volume in Exaile"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by xkendrax on 2007-11-28
Hello, since i installed some gstreamer files the volume in Exaile got lowered.

What can i do to fix this_

---

### Post by FuturePilot on 2007-11-28
Do you have the Equalizer enabled?

---

### Post by xkendrax on 2007-11-28
I have the equalizer enabled and when its not it sounds even lower...

---

### Post by imdano on 2007-11-29
Run exaile with the command ```
exaile --no-equalizer
```And the volume should be normal.  It's a gstreamer bug (not actually an exaile problem) that I think is actually fixed in their development version.

---

