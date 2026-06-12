---
title: "problem with sound in Edubuntu"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by newchalk on 2007-02-19
Friends had an old 333 mhz POS they were going to toss out.  I told them I would install Edubuntu on it for their children. It's a bit slow, but certainly usable. However, I can't get sound to work.  It works with Damn Small Linux, and it looks like DSL is loading the ad1848 driver. I did a sudo modprobe on ad1848 in Edubuntu. The system didn't barf, but it didn't add sound either. What step(s) do I need to take to install the driver?  I know DSL uses an older kernel, but can't I load the driver into Edubuntu?

---

### Post by carlosfocker on 2007-02-21
Remember to check that Master volume, and PCM levels in alsamixer.

---

