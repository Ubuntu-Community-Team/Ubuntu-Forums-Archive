---
title: "MacBook Pro 9,1 (mid 2012, non retina, 15&quot;) Sleep Raring 13.04"
date: 2013-04-20
forum: Apple Hardware Users
---

### Post by philcolbourn on 2013-04-20
Trying raring.

On lid-close MBP does not sleep.

But I found that briefly (1 second or less) touching magnetic lid switch area with a magnet causes it to sleep.

Lid switch is on LHS near [fn] key on edge where pin-holes end, above microphone port.

I use a small piece of a HDD magnet wrapped in tape to avoid scratching case.

[shift] wakes MBP.

Any ideas on what is going wrong here?

---

### Post by philcolbourn on 2013-04-22
Switching to Intel GPU seems to solve this problem for 3.7.5 and 3.9.0 rc7 kernel! I have not tried 3.8 kernel yet.

So, probably not a Ubuntu issue, but somehow a nouveau issue. Just guessing.

---

