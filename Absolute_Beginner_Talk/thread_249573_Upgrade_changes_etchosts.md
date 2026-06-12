---
title: "Upgrade changes /etc/hosts"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by FoggyMtn on 2006-09-02
I'm sure this is simple, but the solution has eluded me in the archives, and googling

I run ubuntu as a file server for my home network.  I change the /etc/hosts file to include all computers on the network.  Whenever I upgrade the system, it replaces my ./hosts file with a new one, and removes my entries.

How can I stop this?

THanks
rob

---

### Post by FoggyMtn on 2006-09-03
Maybe not so simple??   Surely I'm not the only one.

Any takers?

Thanks
rob

---

### Post by xXx 0wn3d xXx on 2006-09-03
> **FoggyMtn said:**
> Maybe not so simple??   Surely I'm not the only one.

Any takers?

Thanks
rob

You could:

1. Back it up and then restore it

2. Or say no when you get the option that asks if you want to replace it. (if you get it)

and what are you upgrading ?

---

### Post by mssever on 2006-09-03
I eventually decided to switch from hosts files to DNS because it's a lot easier to manage once you set it up. Install the package bind9 on the computer that will serve as the DNS server and edit /etc/resolv.conf on each machine to point to your DNS server instead of your ISP's.

There's a good HOWTO [here]("http://www.tldp.org/HOWTO/DNS-HOWTO.html"). If you need additional help with this, I can probably provide it.

---

### Post by FoggyMtn on 2006-09-04
This sounds more like what I was hunting.  Thanks!  I'll review the link you provided and post back back if (more likely, when) I need some more help

Thanks again to all!

Rob

---

