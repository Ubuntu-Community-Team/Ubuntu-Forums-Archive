---
title: "network connection doesn't restart after resume"
date: 2008-01-31
forum: Apple PPC Users
---

### Post by shaunconn on 2008-01-31
Hi

I'm running 7.10 on a G4 iBook, and all works fine - I've installed the driver for the wifi card, and the machine tsleeps/resumes OK, but when it resumes, the wireless network never restarts.

If I manually do "ifdown eth0" then "ifup eth0", the network restarts fine, but its a real pain to have to do it manually.  I've tried adding these commands to /etc/apm scripts and to /etc/power but I can't be sure they're working, since the wireless network still fails to restart.

Has anyone got the wireless network to resume on an iBook running 710?

Regards
Shaun

---

