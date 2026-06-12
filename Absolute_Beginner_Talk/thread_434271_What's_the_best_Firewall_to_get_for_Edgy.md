---
title: "What's the best Firewall to get for Edgy?"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by zhinker on 2007-05-05
The title pretty much says it all...

---

### Post by starcraft.man on 2007-05-05
The best firewall for ANY computer running ANY OS, is a NAT router. In all honesty, a software firewall is irrelevant when you are behind a well configured router. Why? Because a hardware firewall rarely fails, it can't be bypassed, turned off or reconfigured without your permission (long as you put a good password on it and turn off wan management). The way a NAT router works is that it simply drops off all traffic that comes to your computer and makes you appear "stealthed" as in, it will make you appear to not even exist on the net, thus preventing you from being a target of a hacker or other malware.

So, simple suggestion, go out to hardware store and buy any recent router (any router in last 4 years should be nat equipped), they are as cheap as 40 dollars now. I like the Linksys WRT54GS. Thats the end of my speel. :)

---

### Post by zhinker on 2007-05-05
That sounds nice, but I'd prefer something that a little...free-er.  Plus it doesn't sound like I'd be able to upload things from filesharing programs like azerus with that

---

### Post by pay on 2007-05-05
> **zhinker said:**
> That sounds nice, but I'd prefer something that a little...free-er. Plus it doesn't sound like I'd be able to upload things from filesharing programs like azerus with thatYou can upload things with a nat firewall.
Ubuntu comes with iptables as it's firewall, but if you want to edit them you might need to use something like firestarter.

---

### Post by starcraft.man on 2007-05-05
> **zhinker said:**
> That sounds nice, but I'd prefer something that a little...free-er.  Plus it doesn't sound like I'd be able to upload things from filesharing programs like azerus with that

It is easier in my experience to configure a router with NAT than spending time setting up a software firewall. And you did ask whats the BEST, and a NAT router is that. A software firewall will always be second banana to a router equipped with NAT.

Not to mention, look at it this way, since your using Ubuntu, I assume you haven't bought a version of Vista so, your already saving money. Consider it a worthy investment. Choice is yours though.

If you really want a software firewall, search for firestarter.

---

### Post by ramjet_1953 on 2007-05-06
You don't need an additional firewall for ANY Linux Distribution.

By default [COLOR="Blue"]iptables[/COLOR] is enabled and protecting your system.
All ports are closed and the system is already secure.

If you need to make any changes to iptables, your best bet is to download [COLOR="Red"]firestarter[/COLOR], using the Synaptic package manager. Remember, firestarter is not a firewall, it is a configuration tool.

Two pieces of advice here, though:

1. Unless you really know what you are doing and understand the ramifications of changing iptables, leave well alone.

2. To start firestarter, you need to enter your password, as it runs in root mode. This is for a very good reason as [COLOR="Red"]running firestarter continually is a security risk[/COLOR].

Regards,
Roger :cool:

---

