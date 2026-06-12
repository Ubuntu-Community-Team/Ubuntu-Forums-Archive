---
title: "Gutsy almost perfect!..."
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by CM Xtasy on 2007-10-28
Are there any ways to speed up performance?  Like boosting start up on programs and such.  So far I've turned off unnecessary services and used no special effects for the desktop.  I've also uninstalled programs that I dont need.

---

### Post by caffienefree on 2007-10-28
There were speed tweaks like setting concurrency=shell in /etc/init.d/rc for multicore systems... but I seem to remember that breaking HAL in gutsy. I don't know what the resolution on that was... so I wouldn't recommend anything offhand. Maybe using a lightweight environment like fluxbox.

How long is your bootup taking? If it's an inexordinate amount of time based on your system resources, that might indicate another problem.

---

### Post by CM Xtasy on 2007-10-28
> **caffienefree said:**
> There were speed tweaks like setting concurrency=shell in /etc/init.d/rc for multicore systems... but I seem to remember that breaking HAL in gutsy. I don't know what the resolution on that was... so I wouldn't recommend anything offhand. Maybe using a lightweight environment like fluxbox.

How long is your bootup taking? If it's an inexordinate amount of time based on your system resources, that might indicate another problem.

Am I crazy, or did I notice a speed increase when I turned off my swap?

I have a Core2Duo and 2GB of ram.

---

### Post by bobbob1016 on 2008-03-11
If you want to enable concurrency (ONLY on a multi-core system) on Gutsy, you need to follow skymera's post here, [http://ubuntuforums.org/showthread.php?t=611049&highlight=concurrency&page=2](http://ubuntuforums.org/showthread.php?t=611049&highlight=concurrency&page=2)
You just need press ALT+F2, and enter "gksu nautilus /etc/rc2.d" rename s12hal to s13hal
That will make HAL start after dbus, as it should.

---

### Post by VoidedCheck on 2008-03-11
You can also use the sessions manager to tune/eliminate startup programs and options, improving boot time and freeing initial resources (System --> Preferences --> Sessions).  See:
[https://help.ubuntu.com/7.04/user-guide/C/prefs-system.html](https://help.ubuntu.com/7.04/user-guide/C/prefs-system.html)
It covers 7.04, but most applies to 7.10 too.

---

### Post by agtownz on 2008-03-14
> If you want to enable concurrency (ONLY on a multi-core system) on Gutsy, you need to follow skymera's post here, [http://ubuntuforums.org/showthread.p...urrency&page=2](http://ubuntuforums.org/showthread.p...urrency&page=2)
You just need press ALT+F2, and enter "gksu nautilus /etc/rc2.d" rename s12hal to s13hal
That will make HAL start after dbus, as it should.
Still broken, tried changing priority also, no avail.  Time to look for the CD again.

---

