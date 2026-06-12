---
title: "My Ubuntu failed the &quot;Shields UP!&quot; test"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by metalaxesucks on 2006-08-16
Everything about my Ubuntu setup is default, except for my flashplayer which I installed using the "Add/Remove Applications" from the Applications menu. Additional info: I just installed all the available updates for Ubuntu as of Aug 16. As far as I know Ubuntu doesn't have a firewall by default?
Well anyway, here is why it said I failed the test:

"Ping Reply: RECEIVED (FAILED) — Your system REPLIED to our Ping (ICMP Echo) requests, making it visible on the Internet. Most personal firewalls can be configured to block, drop, and ignore such ping requests in order to better hide systems from hackers. This is highly recommended since "Ping" is among the oldest and most common methods used to locate systems prior to further exploitation."

Should I be concerned about this?

Thanks

Shields up:
[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

---

### Post by Klaidas on 2006-08-16
It's just a ping, it's nothing dangerous.
Ping tells if a computer is responsive.
Example, in terminal
```
ping www.ubuntuforums.org
```

If you really want, you can block pings using IPtables, or Firestarter.
```
sudo apt-get install firestarter
```

Preferences -> ICMP filtering.
But again, ping is nothing dangerous.

---

### Post by ComplexNumber on 2006-08-16
> As far as I know Ubuntu doesn't have a firewall by default? it does have a firewall by default - all linux distros have. its called iptables. i guess you'e thinking of a firewall frontend such as firestarter, which is a GUI to configure iptables.

i always rcommend that people get themselves a router when conencted to the internet, and make sure that every port is stealthed between the router and the internet.

---

### Post by Metacarpal on 2006-08-16
How does one go about stealthing ports?

---

### Post by TMR on 2006-08-16
You'll find that most firewall routers do it by default, and you open up ports one at a time as and when you need them (and, if you are super-obsessive, you close them afterwards).

TMR

---

### Post by az on 2006-08-16
> **Metacarpal said:**
> How does one go about stealthing ports?



You use a firewall for that.  But it's useless.

Unless you have something listening, there is no danger.

And as soon as you use your box to do anything, like surf the web, it is not hard for someone to figure out you are there, so stealthing is not very useful.

And if you are running something that listens, you need to punch a hole throught the firewall anyway.  Useless.

---

