---
title: "firestarterblocks my router!"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-09-02
sometimes when i start ubuntu i have no internet connection.
even though its enabled.

so i opened firestarter and in terminal typed

sudo /etc/init.d/networking restart

and firestarter showed that its blocking DHCP, DNS, MDNS, from my router.

but if i restart, its fine!?

why is this happening?

---

### Post by bone2006 on 2007-09-07
firestarter is just the gui to your iptables.  It is probably another setting that you need to work on and not firestarter and iptables itself I would assume.

---

### Post by the.phantom on 2007-09-07
check your firestarter settings for network !
there are a few that can do that

---

