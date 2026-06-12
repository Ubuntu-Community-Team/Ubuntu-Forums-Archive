---
title: "Stop Download new kernels"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by cneil on 2006-08-25
I thought I would ask for a little advice about this.
I have been playing around with Dapper on my laptop for about six months.  I finally have all of the drivers, xgl/compiz/ and network connectivity functioning properly.  I am afraid that someday a new kernel update (or something else) will break some of the functionality that I have worked so hard to achieve.
Is there a way to prevent automatic update from downloading new kernels and driver updates?  Is this a smart thing to want to do?
Thanks for your advice.

---

### Post by muep on 2006-08-25
It would be better to make the system a bit more safer than that. Kernel updates shouldn't be a problem because you can always have the older kernels available. The other updates could make troubles, but they probably won't.

If you disable the dapper-updates repository, you would only get the security updates from dapper-security. Maybe this is what you want?

But really, the configuration will be much easier when you do it the next time, because you already have done it.

---

### Post by cneil on 2006-08-25
That is the thing.  I'd rather that there NOT be a next time, at least until Edgy Eft becomes stable one or two years from now.

---

### Post by Bachstelze on 2006-08-25
As muep said, if there's a kernel update and it breaks something, you can still use the old one my choosing it in GRUB.
If you reakky want to disable kernel updates, you can right-click on the packages in Synaptic and choose "Lock version".

---

