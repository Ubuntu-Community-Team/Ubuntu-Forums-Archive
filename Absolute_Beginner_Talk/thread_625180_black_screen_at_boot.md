---
title: "black screen at boot"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by spiderbatdad on 2007-11-27
Could someone please Help me with this. I have recently encountered a problem when I turn my laptop on. The HDD starts for a few seconds then stop, and just a blank screen is there. After a few minutes I can press the esc key and the disk starts again for a moment, then stops. If I hit the esc key several more times, the disk starts and the login screen comes up.

This was in /var/log/user.log

Nov 27 17:45:07 private-laptop dhcdbd: Started up.
Nov 27 17:45:10 private-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Nov 27 17:45:14 private-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Nov 27 17:45:14 private-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Nov 27 17:45:14 private-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Nov 27 17:45:14 private-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers

I don't know if this is from starting thunderbird after I logged in, or something occuring while the login screen would not com up.
I cannot find a file called /var/log/bootchart

It doesn't seem like the same symptoms I have read about where nosplsh fixed the problem.

---

### Post by Grey Box on 2007-11-27
I don't think I can help much with this, but just curious - are you running redhat?

---

### Post by sports fan Matt on 2007-11-27
Spider,

Kind of same thing with my desktop--although i dont know a fix..Mine boots up normally, i've tried to reconfigure xorg and reinstall several things and nothing works..all i get is a yellow screen without a login and it keeps saying in recovery mode that "cant find ubuntu " even though it boots, so i feel your pain...

---

### Post by spiderbatdad on 2007-11-27
no redhat. Gutsy Ubuntu

---

