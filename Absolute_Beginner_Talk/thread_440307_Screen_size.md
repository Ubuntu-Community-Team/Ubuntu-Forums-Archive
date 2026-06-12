---
title: "Screen size"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by Benbow on 2007-05-11
I have feisty on both my computers. On the laptop screen size is ok but on the desktop it has moved over to the right about one inch. Any ideas as to how I can correct this problem?

---

### Post by heimo on 2007-05-11
I'd try using xvidtune (run from terminal) to tweak modeline for /etc/X11/xorg.conf

More details:
[http://www.ubuntuforums.org/showthread.php?t=83973](http://www.ubuntuforums.org/showthread.php?t=83973)

---

### Post by Benbow on 2007-05-11
Thanks for your help heimo, I have noted it for future use. Before I got too involved in tinkering around, I checked the setting buttons on the side of my monitor, a philips 190X, and found an automatic positioning button - problem solved.

---

### Post by heimo on 2007-05-11
> **Benbow said:**
> Thanks for your help heimo, I have noted it for future use. Before I got too involved in tinkering around, I checked the setting buttons on the side of my monitor, a philips 190X, and found an automatic positioning button - problem solved.

:D Much better. If using dual-boot, using monitor menu settings may cause the screen to be ok for other OS and offset for the other, in that case, using xvidtune helps.

---

