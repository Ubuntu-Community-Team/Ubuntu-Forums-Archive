---
title: "A Question on Power (Management)"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by kristalsoldier on 2007-02-26
This is not really a problem but I would like to know why it happens or is happening to me. I am running Edgy (on a dual boot with XP) on a Sony Vaio (VGN FE-28B, Core Duo, 1GB RAM) - not been more than 2 days or so. I noticed that when running only on battery, the info shows something like this: 91% battery remaining, 46 minutes left! (which is kinda strange). After a while - say about 25-30 minutes, it shows - 76% battery remaining, 4 hrs 12 minutes remaining! After about 5 minutes from the last info, it again says, 75% remaining, 1 hr 12 minutes remaining! The numbers - only the time though - keeps varying/ fluctuating!

Why does this happen? Is there something I should be doing?

Now, I have timed the life of the battery running on Edgy and I get about 3 hours or so - the Vaio manual says that optimally the battery should run (when set to factory defaults for power settings) for about 3.3 hrs or so. So, my timing with Edgy falls within (I think) an acceptable ballpark - I have only timed it once though - I would need to run such tests at least 5-6 times more to gain some confidence.

Thanks.

---

### Post by Mozork on 2007-02-27
Well I guess the remaining time is calculated every t seconds, so it is not only dependent on the state of the battery (which is somewhat linear, at least approximately) but also on the usage, or load at exactly the time the remaining time is calculated. So if you're not running any programs at all, the time estimate should be far more than when your copying a 3.2GB file to a ntfs partition or when your running some other ressource intensive tasks.
So some fluctuation could be because of very different cpu loads per time. But those variations ar kind of big, I have to admit. you could test hov the time estimate corresponds to the cpu load, or what happens when your not running any special tasks...

---

### Post by kristalsoldier on 2007-02-27
Thanks. That does make sense! But I guess the same principle would apply when operating under XP too correct, which does not happen. 

I was reading some posts here and elsewhere which say that there may be some issues with the ACPI with Edgy (and linux in general). Perhaps that's a reason too. I wonder if in the April release some of these issues will be addressed.

---

