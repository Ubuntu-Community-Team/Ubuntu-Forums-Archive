---
title: "iBook G4 poor battery life"
date: 2007-03-05
forum: Apple PPC Users
---

### Post by surfingpenguin on 2007-03-05
I've been running ubuntu as the main OS on my iBook G4 1.33GHz for a week now, and I've noticed that the battery life is just bad. At a full charge, it only gets a maximum of an hour and a half. Under OSX, i would get at least three hours. CPU scaling is working properly, it scales from 666MHz to 1.33GHz. I think I turned off bluetooth by disabling the service.  

Any ideas?

---

### Post by quizno50 on 2007-04-04
That's weird that it's acting different in Mac OS X and Ubuntu... I honestly have never noticed a big difference between the two... I'd try draining the battery all the way down in Ubuntu then resetting the PMU, I don't know the exact key sequence to do that, but I'm sure you can find it on google... something like Ctrl+Option+Shift+Power but I'm not 100% sure... If that doesn't help; check your CPU usage, you might have something in the backgorund sucking up clock cycles which won't help battery life, just open a terminal and type 'top' (without quotes) and find out what's on top; anything over 1.0% CPU usage and it'd be worth investigating...

---

### Post by surfingpenguin on 2007-04-04
thanks a lot for the delayed response, but after reinstalling OSX as a dual boot, i discovered that my battery just so happened to die right when i installed linux after two years of pretty heavy use. Ordered a new one.

Thanks

---

