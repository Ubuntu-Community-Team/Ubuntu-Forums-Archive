---
title: "how to stop things from loading while they are loading"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by RudolfMDLT on 2007-07-25
Hi there,

Ubuntu hangs at the "CONFIGURING NETWORK INTERFACES" step in the boot. even when booting into recovery mode( which really sucks during a recovery). Is there any key combination that i can press to stop that specific task from happening?

any other tips or advice? :)

Thanks for any help,
 
Rudolf

---

### Post by FleetAdmiral74 on 2007-07-25
I tried searching. The general solution seemed to be use a LiveCD to boot up, and then edit one of the statup files involved. I'm not sure how to do this though, this might point you in the right direction.

---

### Post by tama on 2007-07-25
You can try booting with the LiveCD and then commenting out with # everything in <yourrootsystem>/etc/network/interfaces except these two lines:
```
auto lo
iface lo inet loopback

```

---

### Post by FleetAdmiral74 on 2007-07-25
What he said :)

edit: zomg I have a coffee cup in my icon, yay!

---

