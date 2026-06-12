---
title: "Can't reach external sites"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by Imsdal on 2008-01-26
I had a bunch of problems with networking from my Ubuntu machine. After asking some questions here and googling, I resolved most of these, and I think the number one helper was installing winbind. (This is given as background in case winbind has some side effects I'm unaware of.)

Now I can access my Ubuntu computer from my Vista computer and vice versa, but I can't access anything external from the Ubuntu machine.

The wireless card obviously works as the Ubuntu machine is headless and I access it from Vista with VNC. However, pinging returns notning.

If I "ping hp" (the name of the Vista machine), it will resolve to correct ip address, but not receive any packages. If I ping any other address by name, I just get a "unknown host", and pinging by ip I receive nothing, including "ping <ip of hp>".

How do I detect and correct what is wrong?

---

### Post by energiya on 2008-01-27
If the computer you are trying to ping has an active firewall that rejects this kind of requests, it will not work.

---

### Post by stump138 on 2008-01-27
Do you have the DNS servers set properly on the ubuntu machine?  Sounds as if you aren't resolving host names properly.  Also make sure that the default gateway is set to that of your router (or whatever is connecting you to the internet if you are connection sharing).

---

### Post by Imsdal on 2008-01-27
> **stump138 said:**
> Do you have the DNS servers set properly on the ubuntu machine?  Sounds as if you aren't resolving host names properly. 

This is indeed the case - my problems with pinging internal addresses was with a change of default ip addresses in the router. Now pinging works by ip address, but not by name, fr both internal and external locations.

The router is set up to use the DSN from my ISP. This works for the Vista machine, so I'd guess this isn't the problem...

>  Also make sure that the default gateway is set to that of your router (or whatever is connecting you to the internet if you are connection sharing).

... but tis may very well be it. How do I check that? route -n gives the following output:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
198.172.0.0     *               255.255.255.0   U     0      0        0 ath0
link-local      *               255.255.0.0     U     1000   0        0 ath0
default         198.172.0.1     0.0.0.0         UG    100    0        0 ath0
```

The ip address of the router is indeed 198.172.0.1, but I can't interpret if this is correct or not.

---

