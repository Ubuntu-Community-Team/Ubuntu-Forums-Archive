---
title: "Problem with last HAL update and power manager applet"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by kilou on 2007-05-15
Hi,

I'm running Feisty and I use the Power manager applet on the Ubuntu panel to access power management settings. Everything was working well, I could properly suspend, hibernate and resume my laptop but since recently it seems that after a resume from suspend and hibernate the power manager is not loaded immediately and it takes 5-10 secs to come back on the Gnome panel. During that time the LCD brightness also fluctuates. The only thing I recall that have been changed on my system recently is the HAL update (which didnd't solve the eject problem of my USB external disks...).

I think there might be a link between this problem and the HAL update because HAL and power management (through uswsusp) seem related: [http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/](http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/)

Is there anyway to solve this? Since the HAL update didn't solve my issues with ejection of USB disks is it possible to revert to the old version? Whicj package should I revert???

Thanks

---

### Post by kilou on 2007-05-16
I can confirm that reverting to the old HAL version solves the problem....... :confused:

---

