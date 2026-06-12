---
title: "mplayer cannot find header inttypes.h"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by huntyr on 2007-03-24
When I try to configure mplayer with ./configure it cannot find inntypes.h

please help!

---

### Post by zvacet on 2007-03-25
No need for compile.You have mplayer in add/remove and in synaptic.Install from there.

---

### Post by soenderg on 2008-02-06
> **huntyr said:**
> When I try to configure mplayer with ./configure it cannot find inntypes.h

please help!

Just install g++:

  sudo apt-get install g++

inttypes.h is provided by the libc library. All that will be install with the g++ package.

---

