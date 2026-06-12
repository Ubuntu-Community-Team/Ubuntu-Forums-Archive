---
title: "Hissing sound."
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by Smygen on 2007-07-26
I have two problems with my sound in Ubuntu.
1: There is a constant hissing sound when I turn the volume over 60% or so. 
2: There is a low (but high enough to hear) squeaking sound whenever I move the mouse.
I didn't have any of these problems in Windows.

---

### Post by forestpixie on 2007-07-26
my volume level is controlled by master volume, pcm and front speakers . you can double click volume icon to open that and check those levels - or uses alsamixer which is likely to give you more options

open terminal and enter
```

alsamixer
```

check the levels of other controls in there.

If that doesn't help - posting your sound card model might help others.

Can't help with mouse.

---

### Post by Smygen on 2007-07-26
The sound card is Realtek ACL880. I tried installing new drivers for it, but it didn't work.

---

