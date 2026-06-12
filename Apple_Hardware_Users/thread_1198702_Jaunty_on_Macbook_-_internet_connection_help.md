---
title: "Jaunty on Macbook - internet connection help?"
date: 2009-06-27
forum: Apple Hardware Users
---

### Post by cosmicappuccino on 2009-06-27
I've successfully gotten Mac OS X, Windows XP, and Ubuntu Jaunty triple-booting on my Macbook.

At this stage I can't figure out how to connect (wirelessly, as I always do from OSX and XP) to the internet from Ubuntu, and I haven't yet been able to find any clear instructions anywhere. Any advice would be greatly appreciated!

Thanks a lot

---

### Post by NoBugs! on 2009-06-27
System > Admin menu > Hardware Drivers
Enable the wifi card driver and restart, if needed.

---

### Post by cosmicappuccino on 2009-06-28
Thanks for the help, NoBugs. :)

The wireless driver was enabled but it said it wasn't currently in use. This bug is discussed here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/343556](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/343556). I found that disabling the driver, rebooting, enabling the driver, and rebooting again worked for me.

---

