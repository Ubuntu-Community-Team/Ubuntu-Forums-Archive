---
title: "screen resolution made my system mess up?"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by rockinlinux on 2008-01-12
Ok yesterday i was messing with my res, i changed it a couple time from 1280 to 1024, usually it is at 1280 and when i shut down it was at 1280. Today when i started my computer the gui did not load and i was not given any errors about x...so what happened? I am luck that i have a separate /home so in the confusion i just re-installed and everything was fine.

my qustions:
why did this happen?
if i do this again how do i get my gui back from the coamnd line?

thanks in advance!!

---

### Post by santaslittlehelper on 2008-01-12
Hi

I don't want to take a guess to how come that happened.
If all you did was to change you're resolution it might have been fairly easy to fix though. 
If it happens to you again then maybe pop in the live CD and drop a question here at the forum and someone will probably be able to tell you what info they need and be able to help you out.

That probably didn't do much for you, just friendly advise :)

---

### Post by nikoPSK on 2008-01-12
you might want to give reconfiguring x a go :)
```

sudo dpkg-reconfigure -phigh xserver-xorg
```

Best,
nikoPSK

---

### Post by rockinlinux on 2008-01-13
ok well i guess i need to figrue out how i can saftly drop my res. I build some web sites and i prefer the 1280 but i need to check how they look in 1024 and 800....how can i do this without  messing everything up?

---

### Post by nikoPSK on 2008-01-13
> **rockinlinux said:**
> ok well i guess i need to figrue out how i can saftly drop my res. I build some web sites and i prefer the 1280 but i need to check how they look in 1024 and 800....how can i do this without  messing everything up?

I think the option is under display, but I using a business centre with xp, if you find it there, tell me.

Regards,
nikoPSK

---

### Post by rockinlinux on 2008-01-14
yes it is but this is what i did when it mesed up my x.

---

