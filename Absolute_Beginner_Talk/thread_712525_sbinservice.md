---
title: "/sbin/service"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by RyanZec on 2008-03-01
at worki am used to /sbin/service for control mysql and apache, is thier a way to get that functionality in ubuntu?

---

### Post by cmnorton on 2008-03-02
[http://ubuntu-tutorials.com/2007/11/13/service-tool-available-on-ubuntu-710/](http://ubuntu-tutorials.com/2007/11/13/service-tool-available-on-ubuntu-710/)

It's supposed to be available on 7.10.

I am curious as to what extra benefit comes from using /etc/service?

---

### Post by RyanZec on 2008-03-03
when i try to install sysvconfig it tells me it is not authenticaed, shoudl i install it?  

BTW: /etc/service does not exist on my laptop, I just want a common place to start/stop services like apache2 and mysql and whatever, anything that does that would be fine, does not have to be "service 'service' 'command'"

---

### Post by cmnorton on 2008-03-03
I'm not an expert on the repositories, and have never seen that message. How are you trying to download this? Also, does this have the service utility?

---

### Post by lswest on 2008-03-03
generally you start and stop services such as apache and mysql with ```
/etc/init.d/[program name] start|stop|restart|etc
``` so for example, apache2 would be ```
/etc/init.d/apache2 restart
```

NOTE: those commands must be run as root (using sudo)

---

### Post by cmnorton on 2008-03-03
> **lswest said:**
> generally you start and stop services such as apache and mysql with ```
/etc/init.d/[program name] start|stop|restart|etc
``` so for example, apache2 would be ```
/etc/init.d/apache2 restart
```NOTE: those commands must be run as root (using sudo)

I'm with you; I prefer to manipulate the service directly, but am also interested in the folklore of why /sbin/service was created.

---

