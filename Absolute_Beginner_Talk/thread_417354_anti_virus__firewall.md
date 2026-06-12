---
title: "anti virus / firewall?"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by fire_storm on 2007-04-21
Hi

do i need an anti virus, firewall , or anti spyware ??
and which are the best ?

Thank you

---

### Post by aysiu on 2007-04-21
Read this:
[http://psychocats.net/ubuntu/security#firewallantivirus](http://psychocats.net/ubuntu/security#firewallantivirus)

---

### Post by fire_storm on 2007-04-21
thank you , this link was helpful

can i ask 1 last question, what is cracking and how can it be dangerous?

---

### Post by aysiu on 2007-04-21
> **fire_storm said:**
> thank you , this link was helpful

can i ask 1 last question, what is cracking and how can it be dangerous?
*Cracking* is usually what the mass media calls *hacking*--it involves someone 'breaking into' your computer.

[http://en.wikipedia.org/wiki/Hacker](http://en.wikipedia.org/wiki/Hacker)
[http://en.wikipedia.org/wiki/Password_cracking](http://en.wikipedia.org/wiki/Password_cracking)

---

### Post by fire_storm on 2007-04-21
they could just call it hacking :(  
anyways i looked for programs to prevent these root kits but haven't found any can you recommend me one


Thanks

---

### Post by Pobega on 2007-04-21
iptables is built into the kernel, it's definitely a tool you should use; If you have no experience with the cli I'd just stick to using a front-end, like firestarter or something similar.

---

### Post by aysiu on 2007-04-21
> **fire_storm said:**
> they could just call it hacking :(  
anyways i looked for programs to prevent these root kits but haven't found any can you recommend me one


Thanks
Where were you searching? Synaptic? Adept?

If not, maybe you should.

You may want to start off by reading this:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

In any case, the ones in the repositories (to understand what that word means, read the link above) are: *chkrootkit* and *rkhunter*

---

### Post by raffytaffy on 2007-04-21
> **fire_storm said:**
> they could just call it hacking :(  
anyways i looked for programs to prevent these root kits but haven't found any can you recommend me one


Thanks
Enable your universe and multiverse repos. then seach for "chkrootkit" and "rkhunter" you can also install a program called "port sentry" for port sentry i use "webmin" a web based php admin tool, to set up my port sentry. this program is actually quite usefull as it can allow you to set up alot of dif programs using gui. Including firewall rules and such.

---

