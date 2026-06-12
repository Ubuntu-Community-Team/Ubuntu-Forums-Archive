---
title: "problem trying to run a bash/iptables script"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by foxystoatyweasely on 2007-03-18
Hi, thanks in advance for any assistance.

Trying to get my head round some firewall stuff but I'm obviously doing something really dumb which is stopping me from getting ahead with my iptables script.

I can enter (sudo) iptables commands at the command line no problem but as soon as I try running the same command(s) within a bash script I get 'no chain/target match by that name' error message. Is it an ownership/permissions issue with bash rather than an iptables issue?

---

### Post by astrolabio on 2007-03-18
ehm.. maybe you should post your script... :)

---

### Post by foxystoatyweasely on 2007-03-18
> **astrolabio said:**
> ehm.. maybe you should post your script... :)

No need - even a single line like iptables -L will produce this error message.

---

