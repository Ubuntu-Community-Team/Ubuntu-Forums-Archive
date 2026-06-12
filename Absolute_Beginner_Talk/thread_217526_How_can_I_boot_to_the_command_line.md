---
title: "How can I boot to the command line?"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by n00b@linux on 2006-07-17
[LEFT]Is there a way I can alter GRUB so that it boots to the console and does not start X?[/LEFT]

---

### Post by slimdog360 on 2006-07-17
its the safe graphics mode, there is also a way to stop X from loading if you want to do that.

---

### Post by n00b@linux on 2006-07-17
[LEFT]> **slimdog360 said:**
> there is also a way to stop X from loading if you want to do that.Yes.  How do I do that?[/LEFT]

---

### Post by slimdog360 on 2006-07-17
```
sudo update-rc.d -f gdm remove
``` to stop it
```
sudo update-rc.d -f gdm defaults
``` to re-enable it

---

