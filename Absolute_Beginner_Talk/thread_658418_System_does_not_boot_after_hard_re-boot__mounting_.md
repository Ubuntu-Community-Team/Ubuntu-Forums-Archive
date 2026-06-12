---
title: "System does not boot after hard re-boot : mounting /sys on /root/sys failed"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by mguevrem on 2008-01-04
Hi,

I need help resurrecting my system.  After physically moving my desktop, I reinstalled all the wires and accessories.  On the first boot after login in the Gusty 7.1  system froze. I did a hard boot. On the second boot after login the video driver (nvidia) went black.  It used to work...  I did a second hard boot.  On the 3rd boot I do not get to the login screen.  The boot sequence fails and kicks me the initramfs shell with the message:

mount: Mounting /sys on root/sys failed no such file or directory
mount: Mounting /proc on /root/proc failed no such file or directory
target system doesn't have /sbin/init

This is an AMD dual boot system.  On the 2nd partition (Windows 2000) the system re-assigned its IRQ setting in two boots and is running correctly.

Can someone help resurrecting my Ubuntu 7.10 partition?

Help and regards,

Marco

---

### Post by eternicode on 2008-01-05
Hard shutdowns are never good, let alone two in a row.  Only do a hard shutdown if [Alt+Print Screen+REISUB]("http://lifehacker.com/software/linux-tip/gently-restart-a-frozen-system-298891.php") doesn't work.

Chances are you've got errors of some kind on the root partition.  If you have a live cd, or some environment where you can unmount your root partition, boot to that.  Open a terminal window, make sure the root partition is unmounted, and run the appropriate fsck on it ("man fsck" for details).

---

