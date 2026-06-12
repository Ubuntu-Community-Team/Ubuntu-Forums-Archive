---
title: "Broken Time (time-admin)"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by zasdarq on 2006-08-26
I can't change the time... apparantly:

/usr/share/zoneinfo/zone.tab is missing

I went to zoneinfo, it's completely empty.  I'm pretty sure that's a bad thing.  Any way to replace whatever should be in there?

Thanks!
Matthew

---

### Post by msak007 on 2006-08-26
Did you possibly try to install anything that may have uninstalled libc6, or installed a different version? Open Synaptic, search for "libc6", and try to install it (if it's missing) or reinstall it (if it's already installed) as it may be broken. I've seen a few posts lately where libc6 / tzdata are getting corrupted or overwritten by upgrades.

---

### Post by zasdarq on 2006-08-26
Yes,

I was one of those posts.  I tried to update lib6 and it failed, and I ended up reinstalling the previous version.  I will attempt to reinstall it again, but I'm not optimistic.

-Matthew

---

