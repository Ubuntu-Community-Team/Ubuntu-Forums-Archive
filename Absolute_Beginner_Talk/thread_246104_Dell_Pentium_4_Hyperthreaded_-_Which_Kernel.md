---
title: "Dell Pentium 4 Hyperthreaded - Which Kernel?"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by docshawnc on 2006-08-28
I have a hyperthreaded Pentium 4 chip and am currently using the 386 kernel - would the 686 help or will there be problems on this machine? thanks in advance for the advice.

---

### Post by Leif on 2006-08-28
```
sudo apt-get install linux-686-smp
```

Reboot and you're set. The 686 should give a bit of a boost, but the smp will enable hyperthreading, which should really help.

---

### Post by docshawnc on 2006-08-30
Thanks!  I'll give it a shot

---

