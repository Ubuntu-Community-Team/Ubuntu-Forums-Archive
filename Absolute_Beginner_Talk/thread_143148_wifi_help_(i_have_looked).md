---
title: "wifi help (i have looked)"
date: 2006-03-11
forum: Absolute Beginner Talk
---

### Post by obey43 on 2006-03-11
but... i can't seem to find a thread that fits my problem.

so my wireless works perfectly at my school. (as far as i know, it will connect to the schools wireless when it sees it as managed, but it won't when it is ad-hoc, if there is a reason, i'd like to understand why).

but... i am not at school and my sister's wireless.
in wifi radar i see three bars, but am having the hardest time connecting and staying connecting.  the router is somewhat far away.  i am wondering why i am having such difficulties.

i am on an dell inspiron with a broadcom 4306 wireless internal adapter.
my sister's dell latitude connects perfectly, it is her business laptop so i am wondering if she just has a better card, or if it is because she is on windows and i am linux.

does this sound normal?

really patchy connection that constanty drops and i have to sudo dhclient to somewhat reconnect and windows right next to me works perfectly.

any suggestions?

---

### Post by Zeroedout on 2006-03-12
It depends on many factors. Are you using a native driver or ndiswrapper (Broadcom so i'm guessing ndiswrapper)? Is it an external antenna on both cards, or are they both internal? How much further away are you compared to your sis's laptop?

If you are using ndiswrapper, it's possible it is causing some sorte of problem, afterall, it's not using a driver built for linux. It could be possible the antenna on your card is just not as powerfull as your sisters (and this is most likely the case), or it could be that your router is just not powerfull enough to send you the signal. It could also be interference on the spectrum, it runs at 2.4ghz just like cordless phones, and the emissions form microwaves are at this frequency as well. There are too many factors to boil it down to a windows VS linux problem.

---

