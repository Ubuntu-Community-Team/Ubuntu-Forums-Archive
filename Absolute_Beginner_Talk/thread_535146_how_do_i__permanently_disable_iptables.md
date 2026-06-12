---
title: "how do i  permanently disable iptables"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by swoll1980 on 2007-08-26
It's messing my router up

---

### Post by heimo on 2007-08-26
> **bloor75 said:**
> It's messing my router up

I'm interested, how did you determine this? And how did you configure firewall in the first place? Using iptables on command line, or perhaps firestarter? You could use that tool to remove any rules and add default policy to accept all connections (input/output chains).

---

### Post by Austin_KW on 2007-08-26
> **bloor75 said:**
> It's messing my router up

Unlikely, unless you linux box is your router and then you would need iptables.

You can remove all iptables rules using the command "sudo iptables -F" but i suspect you are misdiagnosing the problem.

---

