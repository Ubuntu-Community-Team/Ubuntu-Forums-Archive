---
title: "Question about repo's."
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by lodravah on 2007-01-16
So

There is one thing I've been wondering about for some time, ever since I started using Ubuntu. Every once in a while a link in my repo's goes dead, and I don't know if I get a replacement. I'm using the repo's from Ubuntuguide.org ([http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories)](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories)). And now these two links are dead: 

Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/edgy/free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/edgy/free/binary-i386/Packages.gz)  404 Not Found

Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/edgy/non-free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/edgy/non-free/binary-i386/Packages.gz)  404 Not Found

How do I know which links to use to get to the right repo's when I comment these out from sources.list? They have been down for quite some time, so I really think they are dead. Which ones should I use to make certain I get access to the right upates, security and packages both?

---

### Post by bruenig on 2007-01-16
These are third party repos. Deleting them won't affect updates or security or anything important like that.

---

### Post by lodravah on 2007-01-16
So what do these repo's contain? I don't want to miss useful programs and such because of missing repo's..

---

### Post by bruenig on 2007-01-16
Probably stuff like codecs and since you probably have those installed already, they really serve no purpose after that. It is very very unlikely that one of the codecs will be updated as there is not much really that can be done since they work already.

---

