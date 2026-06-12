---
title: "DHCP server, domain name servers"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by ster1988 on 2008-03-06
I recently put ubuntu on my setup the reason is that i know linux is supposed to be better at setting up servers. I have never set up a DHCP server and i am completely lost and kind of confused. My current set up is i have a modem which i plugged into 1 out of 2 ethernet ports on my motherboard. Then i have a second ethernet cord running from the other port to a dlink 5 port switch. from the switch i have 1 xp home laptop, 1 360, and 1 net gear wireless router. My question is how do i know what i am supposed to choose for the domain name serve. I have installed dhcp3 correctly and i even tried configuring the server through GDHCPD. So according to what i have written i am wonder if anyone has any ideas on how to trouble shoot this. When i look in the lease files it did not lease any IP's. I think the problem is either in the way i have it set up physically or i dont know what domain name server to choose.

any and all help is appreciated

thanks in advanced

---

### Post by hyper_ch on 2008-03-06
DHCP and DNS server are different kind of servers. What do you actually want to accomplish?

---

### Post by mikeyphi on 2008-03-06
Try the following for DNS:
194.119.131.65
194.119.131.66

---

### Post by ster1988 on 2008-03-06
> **hyper_ch said:**
> DHCP and DNS server are different kind of servers. What do you actually want to accomplish?

I want to be able to have my other devices on the network obtain an IP from my linux one.

---

### Post by hyper_ch on 2008-03-07
then you want dhcp

but why not giving those devices a static ip?

---

