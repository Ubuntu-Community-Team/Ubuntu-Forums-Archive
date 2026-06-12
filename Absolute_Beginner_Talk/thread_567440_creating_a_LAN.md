---
title: "creating a LAN"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-10-04
is it possible to create a LAN using my Desktop as a router (its wireless) when only using an ethernet cable rather than a Crossover cable?

i have

Wireless Desktop = router

laptop connected to desktop = ethernet

what settings do i need in Desktop's netowrk admin?
what settings do i need in laptops netowrk-admin?

---

### Post by Haegin on 2007-10-04
If the desktop is on the internet through the first network interface (call it eth0) and you have a second network interface (eth1) then you should be able to plug a cable between eth1 on the desktop and the ethernet port on the laptop and bridge the connection between eth1 and eth0 using iptables rules.

More info here: [http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

---

