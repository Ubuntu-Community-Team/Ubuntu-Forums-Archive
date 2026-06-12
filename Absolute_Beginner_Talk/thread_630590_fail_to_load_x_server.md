---
title: "fail to load x server"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by colomob on 2007-12-03
i updated ubuntu 7.04 and when i did the reset it tells me fail to load the x server and it says :
kinit: no resume image, doing normal boot....
ubuntu 7.04 manny-laptop tty1
manny-laptop login : and the comand terminal appeas..
what can i do??

---

### Post by lswest on 2007-12-03
well...the kinit comes up on my distro too (cuz i installed kdebase for some compatibility problems with kwifimanager) and that, to the best of my knowledge, doesn't affect the xserver.  Maybe it's a driver issue?  maybe try re-installing your driver if you updated Ubuntu.  Other than that, try running the xserver using the vesa driver or something similar, so you can see if it is actually working.

(from terminal view just "sudo vim /etc/X11/xorg.conf" and edit the driver "[whatever is here]" to vesa)

hope the updating the driver helps!

---

