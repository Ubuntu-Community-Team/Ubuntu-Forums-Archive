---
title: "Networking issues"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by Scienceman123 on 2007-12-17
I connect to the internet over an ADSL line via a router. This works fine in XP (plug it in) but in Gibbon it does not. I have fiddled with the controls, trying DHCP, manual config, etc to no avail. Anyone have any ideas?

---

### Post by spiderbatdad on 2007-12-17
should also be plug n play in Ubuntu. try, in a terminal:```
sudo lshw -C network
``` to see that your network card is detected.

---

### Post by Scienceman123 on 2007-12-17
It's recognized...

---

### Post by spiderbatdad on 2007-12-17
do you have a network icon in the notification area of your panel? If so, can you right-click on the icon and check "enable networking."

---

### Post by Scienceman123 on 2007-12-17
It's enabled.

---

### Post by spiderbatdad on 2007-12-17
not sure what the problem is. I have been through several distributions, and initially with Gutsy (wireless in particular) i had to go through the manual configuration several times, and it finally stuck. All I can advise is keep trying. More than likely someone with some expertise will eventually address your post if you havent solved the problem yourself.
Sorry,

---

### Post by spiderbatdad on 2007-12-17
wonder what```
ifconfig
``` shows you regarding your network connections.

---

