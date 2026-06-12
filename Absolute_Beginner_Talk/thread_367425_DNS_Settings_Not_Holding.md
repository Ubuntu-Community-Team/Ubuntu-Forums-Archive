---
title: "DNS Settings Not Holding"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by IronMac on 2007-02-22
Hi all,

I've been finding that my system (5.10) is not keeping the DNS settings (from OpenDNS) that I've set. For some reason, it seems to be reverting to the settings (guessing that that is what they are) given to me by my DSL ISP. BTW, I am using this on a wireless connection. Any ideas what is going on? How can I stop it from doing this? Thanks.

---

### Post by ^rooker on 2007-02-22
You're probably getting your DNS-settings by DHCP from the Wireless router. Depending on the DHCP lease time, your computer refreshes this data after the lease expires.

I'm pretty sure that you can configure the DHCP client to ignore the DNS settings sent by the router. I will see if I can find that option for you, if you're not sure.

---

### Post by IronMac on 2007-02-22
The odd thing is that the DNS settings have changed in the middle of a session (this morning actually). I would understand if the lease settings refreshed after a couple of days but in the course of less than a day? :confused:

---

### Post by ^rooker on 2007-02-22
The default lifetime of a DHCP lease is not "a few days"... it's usually a handful of hours, maybe sometimes even the magical value of 3600 seconds (=1 hour).

You should check that.

---

### Post by IronMac on 2007-02-22
Would I check that in the router? The DSL modem?

---

### Post by ^rooker on 2007-02-22
You can see it somewhere on the client side, but change it only on the DHCP-server side (whatever that is in your case, but I presume it's the router if you have one)

If I remember correctly you should see it somewhere in /var/log/daemon or /var/log/messages... 

There you should see the DHCP lines the dhclient writes. They should contain info about the lease time. 

BUT: if you have access to the router's config, check there since you can change it then right away.



(sorry for being so vague, but my brain's a sponge, leaving only rough sketches of memories in my head - sometimes more surrealistically drawn :) ...)

---

