---
title: "how to"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by empcrono on 2006-09-13
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail                                                              able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc                                                              ess using it?
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail                                                              able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc                                                              ess using it?

**_what do you do to make it avliable agian with out rebooting_**

---

### Post by hw-tph on 2006-09-13
Exit all Debian package management programs - Synaptic, apt-get, aptitude, dselect, and so on.

If you have lsof installed you can type **lsof /var/lib/dpkg/** to see what application is using it.



Håkan

---

### Post by empcrono on 2006-09-13
> **hw-tph said:**
> Exit all Debian package management programs - Synaptic, apt-get, aptitude, dselect, and so on.

If you have lsof installed you can type **lsof /var/lib/dpkg/** to see what application is using it.



Håkan

ok i'll try it thnx

---

