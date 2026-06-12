---
title: "Freeze on startup during load bar"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by Jugney on 2007-12-26
I recently reinstalled to go from the 32 bit from the 64 bit version of Ubuntu 7.10. On the first load after installation, it froze showing the load bar, about 1/5 of the way done.

I edited the boot mode and remoevd "Quite splash" so I could see where it froze. The line was the following:

Loading Hardware drivers
error receiving uevent message: No buffer space available

I'm running an HP Pavilion dv6000 dual boot with Vista. 120GB HD, 2GB RAM, AMD Turion 64 x2. Vista partition has 31GB, Ubuntu has about 80.

---

### Post by riven0 on 2007-12-27
I'm guessing the error is saying you have no memory available, though I don't know how that could be when you've got 2GB. :confused: My first suggestion is to run the memtest to make sure there is no corruption. If it checks out clean, you may want to file a bug report at Launchpad, because I have no idea what could be the problem.

---

