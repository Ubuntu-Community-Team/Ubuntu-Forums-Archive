---
title: "how can i keep update manager from trying to update hal"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by foytix on 2007-11-27
i'm having to run a patched version of hal_0.5.9.1 in order for my cd drive to recgonize any cd's but my update manager keeps asking me to update my hal to replace hal_0.5.9.1-6ubuntu5 with hal_0.5.9.1-6ubuntu5 and if i do my cd drive quits working again.   How can i keep the update manager from trying to install this update? (looking for something more permanent than unchecking the box)

thanks for any help

---

### Post by mcduck on 2007-11-27
Open Synaptic, find the package you don't want to update and select it. Then use Package/Lock Version to lock that package to the version you now have.

---

### Post by foytix on 2007-11-28
thanks

---

