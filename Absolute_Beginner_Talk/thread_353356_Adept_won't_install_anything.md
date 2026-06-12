---
title: "Adept won't install anything"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by SuperCool4678 on 2007-02-04
I'm running Kubuntu 6.06 on a laptop, and for some reason Adept won't install anything.  It installed a couple of things at first, but then for some reason, I got a "Break" message when I tried to install anything else.  Is there anything I need to do to my sources.list file?

---

### Post by taurus on 2007-02-04
Shut down adept.  Then open a terminal and run these two commands.

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by SuperCool4678 on 2007-02-04
That fixed it, thanks!

---

