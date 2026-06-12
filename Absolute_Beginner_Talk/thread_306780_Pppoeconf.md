---
title: "Pppoeconf"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by Desy on 2006-11-25
Ok can anyone help.  I have fot a bt5861 dsl router connected to my pc via ethernet.  I have logged into terminal as root and typed the following

sudo apt-get install pppoeconf && pppoeconf

Then i get a box asking me to scan my comp, at the end i get a message saying

' Sorry I scanned 1 interface but the access concentrator of your provider did not respond.  Please check your network and modem cables.  Another reason for the scan failure may also be another running pppoe process which controls the modem'

Anyone got any ideas, my isp is talktalk.  I am totally lost now and dont know how to get online

Thanks everyone](*,)

---

### Post by jerrykenny on 2006-11-25
I'm not familiar with that router, however most routers dont even need pppoeconf . . . not if they're on the eth0 

Try just going into the gnome "admin" "networking" facility

Alternately, is the router configureable via web-browser ? most routers are, make sure the router has "DHCP" enabled

---

### Post by nixclusive on 2006-11-25
are you trying to connect to an xDSL provider? try rp-pppoe for a simpler setup:

[http://www.roaringpenguin.com/pppoe/](http://www.roaringpenguin.com/pppoe/)

---

