---
title: "can't run updater/software management"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by bullwink1e on 2007-02-01
Hi,

I'm a complete beginner and recently installed Dapper Duck. Became completely unresponsive when I tried to run the software update for the first time (icon in top panel on right!?) and I restarted. Now I can't install things if I click on the same icon and I get a message telling me 'only one software management tool is allowed to run at the same time. Please quit the other tool eg. 'aptitude' or 'Synaptic'.' They're not running as far as I know! How?!

If I try to run Synaptic I get 'E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.'

I am totally at sea when it comes to using the terminal, but I'm trying to learn!

Any help would be gratefully received.

---

### Post by devils_casper on 2007-02-01
open terminal and execute this
```

sudo dpkg --configure -a
```






Casper

---

### Post by bullwink1e on 2007-02-01
Excellent! Thanks for that.

---

### Post by devils_casper on 2007-02-01
you are Welcome ! :)






Casper

---

### Post by atoik98 on 2007-07-10
Wow, I'm thanking you too...I thought I was the only one having a problem with that.

---

