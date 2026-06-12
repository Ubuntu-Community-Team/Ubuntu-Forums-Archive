---
title: "Not sure what's up with this"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by jazmo14 on 2008-03-07
I start up Ubuntu 7.10, then this screen pops up.

"The display server has been shut down about 6 times in the last 90 seconds, it is likely that something bad is going on. Waiting for 2 minutes before trying again on display :0.

                                              <OK>                                                     "

So I hit the "OK" button and it takes me to this screen...

"
*STARTING ANAC(H)RONISTIC CRON ANACRON                      [OK]
*STARTING DEFFERD EXECUTION SCHEDULER ATD                  [OK]
*STARTING PERIODIC COMMAND SCHEDULER CROND             [OK]
*CHECKING BATTERY STATE...                                                  [OK]
*RUNNING LOCAL BOOT SCRIPTS (/etc/rc.local)                       [OK]
_
"

I have no idea what is up with it, and I'm completey new to Linux.

Any help here would be appreciated.

---

### Post by neurostu on 2008-03-07
Does that message come up everytime you boot or just the last time?

If it doesn't come up again I wouldn't worry about it.

---

### Post by spydon on 2008-03-07
Try boot into recovery mode and write this command and follow the prompts:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by jazmo14 on 2008-03-07
> **neurostu said:**
> Does that message come up everytime you boot or just the last time?

If it doesn't come up again I wouldn't worry about it.

Yes it does :(

> Try boot into recovery mode and write this command and follow the prompts:
Code:

sudo dpkg-reconfigure xserver-xorg


I've tryed that thanks it worked.

---

### Post by spydon on 2008-03-11
You can mark the thread as solved now so others can see how you solved the problem. :)
Thread tools -> Mark this thread as solved

---

