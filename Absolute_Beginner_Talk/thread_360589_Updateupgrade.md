---
title: "Update/upgrade"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by AlliumPorrum on 2007-02-13
Could some please explain all these methods for updating my Ubuntu? I mean, if you read these forums, someone are talking about commant 'apt-get' when other talk about 'aptitude'?? And for 'apt-get' you can give parameters as dist-upgrade, upgrade or update. And maybe some other also? What's the meaning of all these parameters??

---

### Post by John.Michael.Kane on 2007-02-13
When one runs sudo aptitude update it'susally after manually editing their sources.list

Running sudo aptitude ugrade will upgrade all packages that have updates waiting for them in the repo's

As for dist-upgrading running sudo aptitude distr-upgrade will upgrade ubuntu to next version

---

### Post by Aberrix on 2007-02-13
> **SD-Plissken said:**
> 
As for dist-upgrading running sudo aptitude distr-upgrade will upgrade ubuntu to next version

can you elaborate a little more on that as to what exactly that means? if I do a dist-upgrade on 6.06LTS is it going to bring me to 6.10? how do you check your current version? thanks.

---

