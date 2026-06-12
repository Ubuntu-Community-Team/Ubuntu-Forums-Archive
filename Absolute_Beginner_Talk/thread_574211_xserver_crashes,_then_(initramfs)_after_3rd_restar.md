---
title: "xserver crashes, then (initramfs) after 3rd restart after changing xorg.conf"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by gettingpissed on 2007-10-12
about to claw my eyeballs out...I'm brand new to linux.  laptop has intel 845g board, after install of ubuntu 7.04, backd up xorg.conf, then reconfiged xorg and used i810 driver, 64mb to video, 24 bit, 1024, 800, and 680 were the chosen resolutions, the rest was left to default.  after restarting xserver, could change to 800x600, but not 1024x768. also, restarted twice (i read on some forum a couple of restarts may be needed) on 3rd reboot, xserver could not start ( i noticed it said ram value was not high enough)  tried to go into reconfig the xserver, rebooted and now have a half *** of a shell with 

(initramfs)

can i restore my xorg.conf from here? how the *#@$ do I at least get back to a shell so I can forrest gump my way back to a GUI.

I'm three days old in linux, so be gentle

---

### Post by twiceasworn on 2007-10-12
When you say you have rebooted three times, are you talking about the X server or the actual computer?  I would try booting in recovery mode (by hitting ESC when grub is loading, selecting the recovery option).

---

### Post by gettingpissed on 2007-10-12
when I try to goto recovery...

Begin: waiting for root file system...
done.

check root= bootarg cat /proc/cmdline or missing modules, devies: cat
/proc/modules ls /dev
ALERT! does not exist. Dropping to a shell!

then I get the

/bin/sh: cant access tty; job control turned off
(initramfs)

---

