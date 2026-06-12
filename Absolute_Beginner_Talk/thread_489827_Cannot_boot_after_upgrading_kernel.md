---
title: "Cannot boot after upgrading kernel"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by ksattic on 2007-07-01
Hi,

As the title says, I cannot boot after upgrading my kernel using the desktop update system. I don't recall the name of the exact program since I rarely use Ubuntu, but it is the default update manager that comes with Ubuntu.

Before this, there was one occasion where Ubuntu failed to load in the same way. I rebooted in recovery mode, and then rebooted again as normal and the problem went away. Also, before this happened, my keyboard (PS/2) and mouse (USB) would intermittently fail to work (sometimes just one, sometimes both).

I asked how to debug the boot sequence on #ubuntu but got no replies. I looked through the dmesg log but saw nothing out of the ordinary.

What do I do now to debug this?

Thanks,

Simon

---

### Post by Raineer on 2007-07-01
Where exactly does it fail? Are there no messages on the screen?

Also, if you upgraded your kernel you should be able to choose the older kernel from the grub list (the list of operating systems on your PC), it should say something like "Press ESC in 3 seconds to menu".

---

