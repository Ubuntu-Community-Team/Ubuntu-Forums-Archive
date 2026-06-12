---
title: "Cannot Get Wireless To Work"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by alistaira on 2007-09-09
I recently installed Ubuntu 6.06 on a Dell Inspiration 1200 laptop. Everything seems to be in order except connecting to a wireless network. I'm not sure if its the actual internal card that is not working with the OS, or if I'm just not using Ubuntu correctly. I would appreciate any help as I am a first time Linux user.

---

### Post by Linux_Man on 2007-09-09
Its going to be much harder to have wireless on 6.06, you would most likely have better luck with 7.04 with improved wi-fi and network manager.

---

### Post by ugm6hr on 2007-09-09
Couple of things might help:

The output of this will tell you what hardware you have (look for Ethernet / Network Controller)
```
lspci -nn
```

If it is surported by Ubuntu - best to try Wicd (see the link in my signature).

---

