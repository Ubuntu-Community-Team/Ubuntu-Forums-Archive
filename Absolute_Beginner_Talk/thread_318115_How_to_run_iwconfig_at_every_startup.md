---
title: "How to run iwconfig at every startup"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by Hillerd on 2006-12-13
Hi,
I want to reduce the WLAN of my laptop at start-up (security reason).
I found the command "iwconfig eth1 txpower 0" to reduce it to 0 dBm (1mW), which still allows me to surf w/o problems.
How do I make this command run at every start-up?

Thanks
   Dietmar

---

### Post by daller on 2006-12-15
You could add it to this file:

/etc/init.d/bootmisc.sh

---

### Post by Hillerd on 2006-12-16
Thanks, that does it

---

