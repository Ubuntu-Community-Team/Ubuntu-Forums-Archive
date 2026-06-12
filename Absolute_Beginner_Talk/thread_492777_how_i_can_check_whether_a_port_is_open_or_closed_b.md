---
title: "how i can check whether a port is open or closed by linux firewall?"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2007-07-05
Hi
Is there an way to check whether a port is open or close?
also, how i can disable the firewall totally, its really annoying.


thanks

---

### Post by moredhel on 2007-07-05
Installing firestarter gives a nice gui to the built in firewall - iptables.

I have never used it, but It probably is somewhere in it :)

---

### Post by nitro_n2o on 2007-07-05
```
sudo apt-get install nmap 
man nmap
```

---

### Post by scxtt on 2007-07-05
**sudo iptables -L** [ to view the rules ]
**sudo iptables -F** [ to "flush" the rules, turn them off ]

---

### Post by Kent84 on 2007-07-05
System->Administration->Network Tools then Portscan "localhost"

---

### Post by legolas_w on 2007-07-06
Hi all
Thank you for your reply.
But your command caused my linux to stop connecting to internet
i think flush command caused that firewall block all connections,

Can some one tell me which text file i should edit and what should i add to it to ensure that my internet start working again?

I am posting this message from windows machie.


thanks

---

### Post by legolas_w on 2007-07-06
Any comment?
I can not use my linux because of this problem :(
Thanks

---

### Post by scxtt on 2007-07-06
the flush is temporary, AFAIK - and even tho i doubt flushing the rules would stop your connection from working - a reboot should put them back how they were ... my **iptables -L** is empty for my kubuntu box and my internet still works ... unless you're using this box for NAT i don't see how the internet could stop working ...

---

