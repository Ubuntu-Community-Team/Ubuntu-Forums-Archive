---
title: "nameserver problem"
date: 2006-02-10
forum: Absolute Beginner Talk
---

### Post by sod on 2006-02-10
Im having a DHCP modem/router and my problem is that sessions such as Synaptic loading, or downloading media files thru browser stops with [1.0.0.0]:...
Found one tread who suggested to edit /etc/resolv.conf file. In my file it only stands: nameserver 192.168.1.1 the suggestion was to edit whith
nameserver 61.1.96.69
nameserver 61.1.96.71
nameserver 192.168.1.1
in that order.
Did and it works! for 1 or 2 minutes in Synaptic then I have to edit again because the list returns to:
nameserver 192.168.1.1 only.
Another note is when my comp starts it cannot sync external clock.
Maybe same problem?

Could anyone help me please?

---

### Post by sharke on 2006-02-12
you Cannot set dns by editing /etc/resolv .config . First make sure you have the correct dns set in your router. you can also take a look at this thread [http://www.ubuntuforums.org/showthread.php?t=11544&highlight=d-link+adsl+router](http://www.ubuntuforums.org/showthread.php?t=11544&highlight=d-link+adsl+router)
Regards
Sharke

---

