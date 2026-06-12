---
title: "services problem"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by lledurt on 2007-06-12
I was troubleshooting a USB problem in virtual box and was trying to restart a service.  I ran services in the administration menu and turned off something (I think it was DBUS) thinking it would reset the UBS buses.  Well the system crashed and now it will reboot but it comes up the an error unable to start HAL and it will not run services (The configuration could not be loaded, you are not allowed access to the system configuration.)  I am root when I run it so I can only assume I turned something off that is not easily turned back on.
Any way to fix it.
P.J.

---

### Post by muximus on 2007-06-12
try starting the dbus service on its own... u knw.. the links are in /etc/init.d

---

