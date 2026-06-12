---
title: "Gaim automatically closing"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by Dual Cortex on 2006-10-05
Seems to have a problem, with one of my MSN accounts. Whenever I log in, it automatically closes COmpletely. Accessing another MSN or Yahoo account does not cause any problems.
Could it be the characters of any of my buddies' names?
Thanks.

---

### Post by Dual Cortex on 2006-10-05
bump

---

### Post by kkellner on 2006-10-05
if you have gaim 2.0.0beta3, it might be a problem with gaim itself.  their sourceforge site said they had problems with msn login, but that they fixed the problem in 2.0.0beta3.1

---

### Post by Dual Cortex on 2006-10-05
> **kkellner said:**
> if you have gaim 2.0.0beta3, it might be a problem with gaim itself.  their sourceforge site said they had problems with msn login, but that they fixed the problem in 2.0.0beta3.1

Gaim 1.5.1cvs...came with ubuntu,

---

### Post by umbrako on 2006-10-06
I have the same problem. Installed ubuntu as my first linux installation ever. So I'm very much a newbee. 

How do I update to the Gaim beta? I have not yet figured out how to install software except from the Synaptic manager. I can't find the beta release there...

Thanks

---

### Post by Dual Cortex on 2006-10-09
I just decided to use Kopete, seems much better, and their new beta has webcam support... which actually works for me!

---

### Post by Ben Sprinkle on 2006-10-09
> **Dual Cortex said:**
> Seems to have a problem, with one of my MSN accounts. Whenever I log in, it automatically closes COmpletely. Accessing another MSN or Yahoo account does not cause any problems.
COuld it be the characters of any of my buddies' names?
Thanks.

Me friend, xpod on this forum had the same issue. He would push send and it would close. PM him about it, he seemed to solve it.

---

### Post by nerval on 2006-10-09
same here too ..
fixed amsn the other day from the forum,
now gaim ain't working.

ah, i've missed the good old days when i was cursing at windows creators mothers about why the hell it crashes all the time.

but now our technology is way to faraway.

nowadays just the program crashes, not the whole system.

soon, we'll crash and punch the monitor and everything will be solved as humanly as possible.

---

### Post by dmizer on 2006-10-09
the crash happens because of msn, not because of gaim.  microsoft is playing around with a new generation of msn messenger (windows live ... sorry i couldn't find more information) which they intend to have integrated into many different aspects of the windows environment.

to prevent this crash, delete your profile from your gaim folder:
```
sudo rm ~/.gaim/accounts.xml
```
reopen gaim.

now when you create your msn account, be sure to go to "advanced", and check the "use HTTP Meathod".  when you start your msn account now, you will find that all your settings and preferences are still in place.

since microsoft is still tinkering with their diabolical plans, you might not want to make msn automatically connect on starting gaim for the near future.  this way, you can make changes to your msn account if/when problems occur in the future.

this fix should work with either the beta version or the current 1.5cvs version.

---

