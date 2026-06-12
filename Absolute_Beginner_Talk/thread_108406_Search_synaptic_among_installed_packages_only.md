---
title: "Search synaptic among installed packages only?"
date: 2005-12-26
forum: Absolute Beginner Talk
---

### Post by harisund on 2005-12-26
Synaptic is great, but I want a search filter that allows me to search only among installed packages. Is there a way to do that? 

The thing is, sometimes I break a package in a terrific way, and want to start fresh. (Especially when dealing with PHP/MySQL/Apache configurations.) So I fire up synaptic and reinstall everything. So I execute a search for, say, "MySql" but every single package that even remotely has the word MySQL in it turns up, and I want only those packages to turn up that actually have been installed and configured. (I know, even dpkg-reconfigure will be fine) 

Thanks !

---

### Post by fannymites on 2005-12-26
*Deleted*  misunderstood the problem.

---

### Post by harisund on 2005-12-26
dpkg-reconfigure -a 

This command reconfigures everything that used debconf. 

Yes, clicking on custom does show me packages installed, and that list is huuuuuuuuuge. I want to filter from that list. 

Thanks anyway

---

