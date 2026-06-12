---
title: "grub question"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by framinglory on 2007-05-24
when you dual boot using grub, and select windows, does grub then pass over booting to the windows booter? or does grub just flat out boot windows? i'm wondering because i used WUBI to install ubuntu, and am considering installing some other distros, but am unsure if i can acess the virtual install of ubuntu with grub.
thanks

---

### Post by eapache on 2007-05-24
I believe that it chain-loads it (passes it to the windows booter), but I could be wrong.

---

### Post by indytim on 2007-05-24
A couple of good sources of info on Grub-Related:

[http://kubuntuforums.net/forums/index.php?topic=3081671.0]("http://kubuntuforums.net/forums/index.php?topic=3081671.0")

[http://users.bigpond.net.au/hermanzone/p15.htm]("http://users.bigpond.net.au/hermanzone/p15.htm")

IndyTim

---

### Post by melancholeric on 2007-05-24
When I had a dual boot setup it chainloaded to the windows boot menu after grub. So yeah, that should be what it does unless grub has changed dramatically since Dapper ...

---

### Post by Happy_Man on 2007-05-24
> **melancholeric said:**
> When I had a dual boot setup it chainloaded to the windows boot menu after grub. So yeah, that should be what it does unless grub has changed dramatically since Dapper ...

Which it hasn't.....

---

