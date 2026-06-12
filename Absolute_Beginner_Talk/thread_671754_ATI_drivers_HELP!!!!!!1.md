---
title: "ATI drivers HELP!!!!!!1"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by pirateofthenet on 2008-01-18
ok i'm new to linux and just installed ubuntu 7.1 everything works great except the ati graphics drivers i'm running a lappy w/ a mobile x1400 I found the driver on ATI's sight but now i'm lost the installer complains about dependencies could someone help me or point me to a guide

---

### Post by Medieval_Creations on 2008-01-18
You shouldn't have to go through all that.  If you launch the "Restricted Drivers Manager" it should show that it found an ATI video card and once you check it, should take care of it from there...

I forget exactly where it is under menu's since I don't run Gnome, most likely under System -> Administrator.  (Or something close to that).

Or you can launch it from the command line.

```
sudo restricted-manager &
```

That's all I do to install it on my laptop with an ATI vid card.

---

### Post by spiderbatdad on 2008-01-18
what are you trying to acomplish? xgl rendering...wide screen resolution?

---

### Post by bwhite82 on 2008-01-18
> **pirateofthenet said:**
> ok i'm new to linux and just installed ubuntu 7.1 everything works great except the ati graphics drivers i'm running a lappy w/ a mobile x1400 I found the driver on ATI's sight but now i'm lost the installer complains about dependencies could someone help me or point me to a guide

[The Wiki is your friend.]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

---

