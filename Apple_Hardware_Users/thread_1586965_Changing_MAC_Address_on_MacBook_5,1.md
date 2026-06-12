---
title: "Changing MAC Address on MacBook 5,1"
date: 2010-10-02
forum: Apple Hardware Users
---

### Post by maxbucknell on 2010-10-02
Hi. I'm semi new with linux. Familiar with basics, but this has me beaten.

I have an internet curfew which is MAC address based. In OS X, I can very easily change it to an unrestricted address.

I assumed that this would be the same in linux, and for most people it is. But not here. running:
sudo ifconfig eth0 down
. . .

changes the eth0 MAC address fine, but if I try this with eth1 (the AirPort interface) then it gives some error about not having permission (or there being too many files open when done with sudo).

I went google diving and tried macchanger. No luck there either. It says that the interface is still up, when I know for a fact that it isn't.

I'm beginning to think that maybe the drivers for airport don't support MAC spoofing, which would really rain on my parade, so I'm putting this question out to the world.

Thanks in advance

---

