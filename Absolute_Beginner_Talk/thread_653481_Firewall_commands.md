---
title: "Firewall commands"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by pavicnat on 2007-12-29
I know I have a firewall, but what are the commands to check it's status and change it's settings?

---

### Post by taurus on 2007-12-29
The easiest way is to install firestarter and use it to configure your firewall, iptables.

```
sudo apt-get update
sudo apt-get install firestarter
gksudo firestarter
```

---

### Post by pavicnat on 2007-12-30
ok, I did that, it's asking me if I want to share my internet connection with users in the same network. What users are considered on my network and how do I know what my network is. Does this work only between unix based systems?

---

### Post by SOULRiDER on 2007-12-30
Your network as in your LAN or WLAN.
As for your second question, im not sure but im guessing it refers to all OS'es, not just UNIX or UNIX-like systems.

---

### Post by pavicnat on 2008-01-06
Thanks for the information.

---

