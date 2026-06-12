---
title: "blacklisting bcm make it go faster?"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by Ripfox on 2007-02-20
I just blacklisted the bcm4xx driver then re-did ndiswrapper...and its like 10x faster. Am I imagining this? Before, I was using ndiswrapper and didn't have the Edgy driver blacklisted, because I didn't know how.

---

### Post by equal on 2007-02-21
It's entirely possible. The Edgy driver for BCM cards sucks. ndiswrapper works much better.

---

### Post by CCBalla10 on 2007-02-21
> **ripfox said:**
> I just blacklisted the bcm4xx driver then re-did ndiswrapper...and its like 10x faster. Am I imagining this? Before, I was using ndiswrapper and didn't have the Edgy driver blacklisted, because I didn't know how.

i dunno so much about making it faster...but i too had to blacklist the bcm driver and one thing it did do was not take as long to boot up.  System skips loading the driver and continues :)

---

### Post by Ripfox on 2007-02-23
Well, I can report up to 6meg downloads wireless with ndiswrapper!! rockin, so happy now.

---

