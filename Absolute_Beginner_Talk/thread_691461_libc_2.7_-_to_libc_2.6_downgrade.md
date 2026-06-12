---
title: "libc 2.7 - to libc 2.6 downgrade"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by mzakharo on 2008-02-08
Hi, a package that i installed required libc6 version 2.71 - I installed it (despite the warning) - but now I need to go back to libc6 2.6 - I downloaded the deb package from the internet, but when I try to run it, it flags that an older version is already installed (duh). I tried removing the 2.7, but it wants to take all my apps with it! - is there anything I can do, besides reloading the whole system?

---

### Post by mc4man on 2008-02-08
The last person I know that got themselves in this situation ended up doing a reinstall. Without actually following thru go back to synaptic, search libc6, highlight it and from packages tab choose force version. 2.6.1 should be a choice, select it and _see_ what it wants to do.

---

### Post by mzakharo on 2008-02-08
THANK YOU SO MUCH!! it did the trick! :)

---

