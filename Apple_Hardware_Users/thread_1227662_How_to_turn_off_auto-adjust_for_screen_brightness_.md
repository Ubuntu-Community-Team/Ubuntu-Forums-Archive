---
title: "How to turn off auto-adjust for screen brightness with Jaunty/MBP5-2?"
date: 2009-07-30
forum: Apple Hardware Users
---

### Post by swarup on 2009-07-30
I have just installed Jaunty on my new MBP5-2 17" laptop, and configured it using this [wiki]("https://help.ubuntu.com/community/MacBookPro5-1_5-2/Jaunty"), and Jaunty seems for the most part to be working really well. One very important problem though, is that the screen brightness auto-adjusts and makes itself very dim. I set it to the brightest setting using the manual adjustment (F2 button), and 5-10 seconds later it makes itself dim again. How do I turn off the auto-adjust for the screen brightness?

---

### Post by crocowhile on 2009-08-01
```

gconftool -s /apps/gnome-power-manager/ambient/enable -t bool false

```

---

