---
title: "failed to fetch?"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by aaron1011 on 2007-10-26
when i try to update certain applications, and my ubuntu distribution
i get the error that says 

failed to fetch
[http://uu.enarel.eu.dists/fiesty/all/binary-i386/packages.gz](http://uu.enarel.eu.dists/fiesty/all/binary-i386/packages.gz) 404 not found

and then i cant update 

what should i do to fix this problem?
thanks

---

### Post by ItsMitsHere on 2007-10-26
Pls make it clear how are u trying to update? looking at your message it is possible that the perticular application u want to upgrade is temporarily unavailable from the server or the default link to the update is broaken somehow. the problem usually gets solved within hours. It is also possible that the problem may have arisen due to extra repositories that you had added. while updating make sure that you disable all extra reopsitories.

---

### Post by FredB on 2007-10-26
> **aaron1011 said:**
> when i try to update certain applications, and my ubuntu distribution
i get the error that says 

failed to fetch
[http://uu.enarel.eu.dists/fiesty/all/binary-i386/packages.gz](http://uu.enarel.eu.dists/fiesty/all/binary-i386/packages.gz) 404 not found

and then i cant update 

what should i do to fix this problem?
thanks

Go in synaptic, (System / Administration / Synaptic) and then in  configuration / repositories

2nd tab ("3rd party...") and try unchecking this repository.

Hope it helps ;)

---

