---
title: "Problem with sound card"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by cypry on 2007-09-02
The new kernel(2.6.20-16) doesn't seem to detect my sound card. Everything works fine with 2.6.20-15, but when booting with the new kernel, it doesn't. What should I do?

---

### Post by Daveth on 2007-09-02
why not just return to the one that works?  it should still be listed in your grub menu.lst and will show up as an option to load. Then keep an eye on the kernel fixes, and when it is sorted move to the new.

---

### Post by freakzilla on 2007-09-02
Might be like the same problem a few people had in this thread: [http://ubuntuforums.org/showthread.php?t=540296](http://ubuntuforums.org/showthread.php?t=540296).

I recompiled the latest alsa and my sound came back.

---

