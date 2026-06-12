---
title: "Out of My Depth / xserver-xorg"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-03-11
I had a disk blow up trying to fix the sound problem. I put in a 2nd disk (it is now hda1). While booting form grub, which shows both hard drives and all the kernels ever installed, I cursored down to hdb1 to the most recent kernel, which was an .i686 rescue mode.  I tried to dpkg-reconfigure xserver-xorg, answered all the questions. sudo'd /etc/init.d/gdm start and saw the same problem, the kernel says modprobe fatal many time and I'm returned to mark@lexington:

The foregoing is only the preface.

So, after a while of trying different combinations of xorg-conf configurations, I gave up and decided to reboot to the hda1 (primary master). Now it's gnome/xserver is gone bad. After again running  dpkg-reconfigure xserver-xorg against it, it booted BUT gave a window on the desktop saying that the HAL was in an error state. Yikes!!!

What is the safest way to correct a hardware abstraction error SAFELY?

---

### Post by undertherift on 2007-03-27
Mark, 
I don't have the expertise to solve your issue.  But have you considered this?

Boot a live cd, mount your drives, and copy the live cd's xorg.conf over your own?  It might just give you a stable enough system to resolve whats happening with your hardware conflicts. You may be able to apt-get update or something like that to help update your kernel version or something?  

If that's not any help, apologies.  Just saw this unanswered thread and thought of this idea.

Regards,

---

