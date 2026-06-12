---
title: "How do I set prefered WIFI hotspot"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by neurostu on 2008-03-11
So for security issues I have my WIFI router set to **NOT** broadcast its SSID. So in order to connect I need to tell my computer the explicit name of my router to connect.

Every time I come home from work I have to manually reconnect to  my router, is there anyway to get Ubuntu to remember my preferred WIFI routers and to automatically connect to those routers when their in range?

---

### Post by &#7940;&#957;&#952;&#961;&#969;&#960;&#959;&#962; on 2008-03-11
Enable roaming mode for wireless interface in network setting
see if that helps

---

### Post by neurostu on 2008-03-11
Roaming mode is already enabled.

---

### Post by neurostu on 2008-03-12
bump*

---

### Post by Golem XIV on 2008-03-12
You can try replacing the standard network manager with [wicd]("http://wicd.sourceforge.net/").  IIRC wicd has the option to autoconnect to a pre-specified network.

---

