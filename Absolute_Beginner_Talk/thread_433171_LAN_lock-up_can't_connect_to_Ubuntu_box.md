---
title: "LAN lock-up: can't connect to Ubuntu box"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by aalien on 2007-05-04
Hi everybody.

I'm just installed Ubuntu Feisty Fawn (7.04), played with it a little, ran a few services (ssh, daapd and netatalk), and then rebooted.
...and lost daapd and netatalk: system weren't able to get short hostname of... well, of itself.
I've somehow managed to edit /etc/hosts and all of a sudden... it works. Forces of Evil are now... oh, wait. Nevermind.

One more reboot... bang! No ssh, no afp, no trace of Apache. When i try to run it locally on the Ubuntu Box, it works, both as localhost and 192.168.x.x (and yes, there's a static DHCP on router). But when i try ssh or afp or http or vnc from my MacBook, nothing happens. Well, in fact,  "Operation timed out" happens.


And yes, i didn't find anything in this forum (maybe because i'm a real noob in a) networking issues and b) Ubuntu)

Any suggestions / links?

---

### Post by aalien on 2007-05-04
sudo ifdown eth0 / sudo ifup eth 0 doesn't help either.

---

### Post by aalien on 2007-05-04
Uh-huh. Found the source of a problem. Firestarter is to blame.

---

