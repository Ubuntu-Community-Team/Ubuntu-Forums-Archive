---
title: "Emergency Please Help"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by MikeyRibbs on 2007-04-22
I was upgrading to Feisty Fawn and when I rebooted it was all CLI and I couldn't do much. I think my hard drive is still intact but I need to get my music and other files off of it first before I format. When I boot from a live CD I can't access my files but I'm pretty sure they are still there. How can I move them, if they exist, to my external HDD? Please Help!

---

### Post by Happy_Man on 2007-04-22
boot from the LiveCD, and once you do, get to a Terminal (Applications --> Accessories --> Terminal) and type this in:

```
mount /dev/<your internal hard drive name> (eg sda1, sda2)
```

From there transfer your stuff.

---

