---
title: "How I can disable all Ubuntu 7.10 firewalls?"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2008-01-13
Hi
Thank you for reading my post
How I can disable all ubuntu 7.10 firewalls?
What is best firewall GUI administration for UBuntu 7.10?

thanks.

---

### Post by fiddledd on 2008-01-13
Best GUI for iptables is Firestarter IMHO, it's in the repositories so you can install with Synaptic.

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-01-13
by default there open
but no programs are tide to ports

---

### Post by thelatinist on 2008-01-13
You don't need to "stop" the firewall.  In fact, I'm not even sure it's possible without recompiling the kernal. All you really need to do is to delete all rules closing ports, which you can easily do using Firestarter.

---

### Post by The Cog on 2008-01-13
Unless you have gone to the effort of installing a firewall GUI like firestarter, you probably don't have any firewall filtering active, so nothong to disable. What are you actually trying to achieve and why?

P.S. If you run the command
```
sudo iptables -L
```
and get this output:
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```
then you have no firewall rules, and nothing is being blocked.

---

