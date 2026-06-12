---
title: "no splash screen"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by stonecoldjha on 2008-03-17
my monitor blacks out during start up and shut down,with a message telling me-"out of range".is there a way to make splash screen show up?

---

### Post by jken146 on 2008-03-17
The wrong resolution may be set for the splash screen.  Change it in /etc/usplash.conf

```
gksu gedit /etc/usplash.conf
```

---

### Post by mcdan on 2008-03-17
you can also try using startup manager to change your resolution or what bit amount of color is used

---

### Post by stonecoldjha on 2008-03-18
i  executed the following and the file was successfully opened.
gksu gedit /etc/usplash.conf
initially the resolution read something that was way too high,i modified to 1024*768,then saved the file and rebooted.but at the startup no splash screen showed up.how should i effect these changes to the resolution of splash screen.

---

### Post by ubuntu-freak on 2008-03-18
As someone said already, install this app;
 
**sudo apt-get install startupmanager**
 
Make sure the resolution is correct, and try a16-Bit colour depth.
 
Nathan

---

### Post by KingArthur10 on 2008-03-18
[http://ubuntuforums.org/showpost.php?p=4526658&postcount=5](http://ubuntuforums.org/showpost.php?p=4526658&postcount=5)

That guide always solves my problems.

---

