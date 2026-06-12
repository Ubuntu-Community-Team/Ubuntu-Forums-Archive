---
title: "beryl+new kernel crashing the Xserver"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by mendingo84 on 2007-02-12
title says it all. it only happens from time to time. what i need to know is if that happens to someone else.
oh, i go with Intel 855GM graphic card (i810 driver), KDE Desktop

---

### Post by jpeddicord on 2007-02-12
Beryl, in its current development stage, can be very crashy at times. It crashes occasionally on me if I try to play video, or even on a random occurence when I spun the cube too fast.

There is no avoiding it, other than keeping up-to-date with current releases. You can also try Compiz instead of Beryl. There are less features, but it is more stable.

Jacob

---

### Post by Archmage on 2007-02-12
Wild guess - you didn't install the new modul with the new kernel. Therefore the X-server crashed.

That could happen also without beryl.

Try this to confirm:

```
dpkg-reconfigure x-server
```

Accept anything beside when choosing the grafic mode choose VESA.

---

