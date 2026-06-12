---
title: "what the hell does this mean?"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by shredfitz on 2007-12-02
sbin/iptables -A INPUT -i eth1 -m state --state ESTABLISHED,RELATED -j ACCEPT

sbin/iptables -A INPUT -i lo -j ACCEPT

If you cant tell me what this all means can you point me to where I could easily find out?

---

### Post by jfinkels on 2007-12-02
Those are commands to run programs (specifically iptables). Enter them in the terminal (Applications > Accessories > Terminal) ONLY IF YOU KNOW WHAT THEY DO. Are you following the instructions from a website or something?

---

### Post by shredfitz on 2007-12-02
ITs from some schoolwork. The instructor is pissing me off. He wants to know in detail what these commands do, yet the reading material he assigned to go with this homework makes ZERO mention of anything remotely associated with this. I don't want someone to do the work for me, but I am having a helluva time finding laymens defintions for what these commands do. It is NOWHERE in his reading material. I have read it over three times.

---

### Post by ac7ss on 2007-12-02
Type 
```
man iptables
```
this will explain the command.  It is for IPv4 packet filtering. Was this a command given to you from a outside source?
```
sbin/iptables -A INPUT -i eth1 -m state --state ESTABLISHED,RELATED -j ACCEPT
```
establishes an input filter on eth1 matching the state of established or related connections, accept.
```
sbin/iptables -A INPUT -i lo -j ACCEPT
```
establishes an input filter on the loopback interface ta accept connections.

---

### Post by Partyboi2 on 2007-12-02
This could help explain it as well
[http://www.puschitz.com/FirewallAndRouters.shtml](http://www.puschitz.com/FirewallAndRouters.shtml)

---

### Post by bodhi.zazen on 2007-12-02
[https://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/ref-guide/ch-iptables.html](https://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/ref-guide/ch-iptables.html)

---

### Post by shredfitz on 2007-12-02
Alright, I appreciate everyones' assistance. I now have the matter under control and have learned more than my instructor or my textbook was giving me thanks to fellow users of this forum. Thanks again.

---

### Post by BLTicklemonster on 2007-12-02
> **shredfitz said:**
> ITs from some schoolwork. The instructor is pissing me off. He wants to know in detail what these commands do, yet the reading material he assigned to go with this homework makes ZERO mention of anything remotely associated with this. I don't want someone to do the work for me, but I am having a helluva time finding laymens defintions for what these commands do. It is NOWHERE in his reading material. I have read it over three times.

Yes, "instructor", not teacher. Tar and feather that dork and get the school to hire someone who wants to teach for God's sake. Man that burns me up when "instructors" do that.

---

