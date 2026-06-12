---
title: "Laptop randomly enters standby mode"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by MedellinManDem on 2008-04-15
Hi, 

for some reason, my Dell Vostro 1500 has randomly entered standby mode today on at least three occasions...It's obviously not desirable and is quite annoying.

I'm running Hardy Heron.

Any ideas?

---

### Post by MedellinManDem on 2008-04-15
bump

---

### Post by MedellinManDem on 2008-04-15
bump

---

### Post by MedellinManDem on 2008-04-16
Can nobody help with this?

---

### Post by joe.turion64x2 on 2008-04-16
Hello.

How long has this happened? I mean, did it occur after some updates? Or is it a fresh install?

Seems that Ubuntu doesn't take along well with your power management system. Try to use the parameter **noapic** to the kernel upon boot.

One method to do it is by doing the following: when you see grub type _e_ and get to the line where the kernel is selected. There, at the end of the line write noapic and hit enter.

Hope that solves your problem.
Joe.

---

### Post by MedellinManDem on 2008-04-16
Thanks

---

