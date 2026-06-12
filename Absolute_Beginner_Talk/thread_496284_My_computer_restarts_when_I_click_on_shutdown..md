---
title: "My computer restarts when I click on shutdown."
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by clipse on 2007-07-08
I have 7.04. It didn't used do that. I didn't change anything. Any ideas of why this happened and how I can fix it?

thanks,

clipse

---

### Post by FleetAdmiral74 on 2007-07-09
This didn't happen after the kernel upgrade did it? That messed up a lot of stuff, or so I hear. You can try booting off the old kernel and seeing if that makes a difference.

---

### Post by Old Pink on 2007-07-09
Run ```
sudo shutdown -h now
```and see if it has the same effect? 

Even if it's just a temporary solution... :) 

(The -h calls "halt" which should stop a reboot)

---

