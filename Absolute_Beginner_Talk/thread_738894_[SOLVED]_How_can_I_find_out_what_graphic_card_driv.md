---
title: "[SOLVED] How can I find out what graphic card driver I'm using?"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by FreewareFan on 2008-03-29
Is there a terminal command I can enter to see what graphic card driver I am using?

I know I can look in the xorg.conf file, but I need a way to find out what the driver is on Hardy, and xorg.conf file does not list it in that case.  So, when I boot up using the Live CD, is there a command I can enter to see what driver has been chosen?

---

### Post by szymon_g on 2008-03-29
cat /etc/X11/xorg.conf | grep driver 

should work (i'm not on ubuntu now, so i cannot say it for sure)

---

### Post by FreewareFan on 2008-03-29
With my system, using the LIve CD, Hardy 8.04 does not list the driver in xorg.conf.   I am looking for a command I can enter in the terminal to find out what driver is being used..

Thanks.

---

### Post by dcstar on 2008-03-29
> **FreewareFan said:**
> With my system, using the LIve CD, Hardy 8.04 does not list the driver in xorg.conf.   I am looking for a command I can enter in the terminal to find out what driver is being used..

Thanks.

```
lshw
```
and look for the "Display" section.

---

### Post by bumanie on 2008-03-29
I would have thought that off the live cd, the generic 'vesa' driver would be used. Please correct me if I'm wrong.

---

### Post by FreewareFan on 2008-03-29
Actually, it turned out that the Live CD used the correct driver, that being ati .  Surprised me too!

Thanks much, folks!!

---

