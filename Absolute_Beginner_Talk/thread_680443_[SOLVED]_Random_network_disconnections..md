---
title: "[SOLVED] Random network disconnections."
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by mouseboyx on 2008-01-27
I am on a wired network with dhcp server.

It seems about 50% of the time I goto a website and it is fast, or instant like normal, but the other 50% firefox stalls, and it says looking up example.com in the status bar.  When i try to ping there is a long delay and then it starts to ping the site.

Can someone help diagnose this problem?

---

### Post by mattismyname on 2008-01-28
Could it possibly be an ISP issue?  Do you suffer this issue from OSes other than your Ubuntu/Linux install?

---

### Post by sports fan Matt on 2008-01-28
i get the same thing so a fix would be nice

---

### Post by mouseboyx on 2008-01-28
The problem just started, and all of the other machines do not suffer from it, I am starting to  believe there is a problem with my on board eth0.

---

### Post by mouseboyx on 2008-01-28
Yes, my suspicion was confirmed, I stole a network card from my server, and it works perfectly now. eth1 instead of eth0

---

### Post by mouseboyx on 2008-01-29
No, It is now disconecting again, but my integrated nic seems to not be the problem.

---

### Post by mouseboyx on 2008-01-29
Switched to open dns and things are perfect!

---

