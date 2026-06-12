---
title: "Ethernet card missing"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by gazruss on 2006-12-03
Hi folks..... i knew i had given myself bad luck a few weeks ago when i asked what i had to do to make this software "break". Well i found out. I installed a new hard drive, formatted it and installed dapper onto it. Exact same hardware that worked without problems for months and months (except HDD of course) anyway, installed it and now i only have a modem in my network showing. Can't see my network or connect to the internet. Any idea's where to start looking, I have installed it twice now today, formatted both times but with same result. Green light is on the NIC card.

---

### Post by jordanmthomas on 2006-12-03
First, you need to find out what kind of ethernet card you have
```
lspci | grep Ethernet
```

Then, you can look up your card to see if others have problems, or you can post the results back here to see if someone might know.

**edit** I don't do much hardware stuff, so I might not be able to help, but hopefully I can at least get you going in the right direction.

---

### Post by houstonbofh on 2006-12-03
Boot a live CD or two (different distributions) and see if the NIC works.  If so, look to see what it detects as.

---

### Post by gazruss on 2006-12-03
Thanx for the fast response,

Tried your suggestion, and a lot from other posts, no luck, so i changed the card for another one, and it worked first time, but the card i took out works with no probs on my XP unit....

---

### Post by houstonbofh on 2006-12-04
And without us knowing what the card is, we have no way to tell you why.  Some cards are better detected than others.

PS:  The works in XP thing.  Did it actually work directly in XP, or did you need to load a driver disk?  Just keeping the comparison fair.

---

