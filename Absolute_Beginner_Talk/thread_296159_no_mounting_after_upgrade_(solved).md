---
title: "no mounting after upgrade (solved)"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by macdo on 2006-11-09
Hey all,

Since upgrading to edgy, my external 100G HD (via USB 2.0) no longer mounted, or indeed, appeared in /dev/ 

(at this point in my typing this message, I actually got it to work, so this is FYI only. Hurrah.)

The thing that got it to work was unplugging replugging it, then at the CL: 

```
rmmod ehci-hcd
```

But arrrgh! Not amused! (the disk in question holds all the backups that I did before reformating / reinstalling...)

Tchüss

Dom

---

