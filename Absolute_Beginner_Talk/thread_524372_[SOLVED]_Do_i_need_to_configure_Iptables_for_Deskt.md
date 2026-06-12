---
title: "[SOLVED] Do i need to configure Iptables for Desktop??"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by Hopeless on 2007-08-13
Hi,

a poster said you don't need to configure Iptables for Desktop Edition...is this true or should i follow the community Docs.....

What do you think? :popcorn:

---

### Post by undertakingyou on 2007-08-13
I understand that by default IPTABLES has everthing blocked, and that ports open as apps need them automatically.  I don't ever change it unless I need a certain app to work that isn't.

---

### Post by avik on 2007-08-13
No, you don't need to configure it unless you want to explicitly allow something like a web server.  In that case, there are iptables front-ends, such as Firestarter.

---

### Post by Jimmyfj on 2007-08-13
I think that the safest way is to invest in a broadband router with build in firewall. This is by far the easiest way for people new to the world of Linux. If you are behind a routers firewall you need not think about the firewall build in unless you need to operate a server on your local LAN. Ubuntu is extremely safe out of the box and do not need antivirus or firewall. If you want to configure your own settings for the firewall you can do so through Firestarter. But you really don't need to think that much about the security - Linux is safe.

---

### Post by Hopeless on 2007-08-13
OK thanks for the info..
:)

---

### Post by Hopeless on 2007-08-13
Why does it say this:

Ubuntu has a built-in firewall system called IPtables (netfilter) that is enabled by default. At installation all ports are open and there is effectively no filtering/protection. To close the ports and leave only the ones you want open, you must either manually edit the iptables or use a GUI (such as Firestarter). Once you edit the iptables configuration, your computer will be better protected from attacks from the Internet.

---

### Post by avik on 2007-08-14
> At installation all ports are open and there is effectively no filtering/protection.

I'm pretty sure all ports are *closed*, not open.  I used to run a web server, and I manually had to open port 80.

---

### Post by ramjet_1953 on 2007-08-14
Yes, all ports are closed.

Just go to ShieldsUp website to prove it.

Regards,
Roger :cool:

---

