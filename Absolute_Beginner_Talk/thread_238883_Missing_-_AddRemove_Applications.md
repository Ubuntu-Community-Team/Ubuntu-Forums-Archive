---
title: "Missing - Add/Remove Applications"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by rgates on 2006-08-18
I must have installed something incorrectly. Ubuntu 6.06 LTS

If I go to the Applications tab - Add/Remove Applications is missing.

Also if I go to System - Administration, the Synaptic Pakage Manager is missing.

Can this be easily fixed?

Thanks,
Bob

---

### Post by syedn on 2006-08-18
perhaps this?  open up the terminal (applications > accessories > terminal) and type

```
sudo aptitude install synaptic
```

edit sorry just put the code the first time..

---

### Post by Metacarpal on 2006-08-18
> **rgates said:**
> I must have installed something incorrectly. Ubuntu 6.06 LTS

If I go to the Applications tab - Add/Remove Applications is missing.

Also if I go to System - Administration, the Synaptic Pakage Manager is missing.

Can this be easily fixed?

Thanks,
Bob

Is this a new user account you added?  If so, you'll need to login to the main account, go to System > Administration > User... (can't remember the exact wording, and at my @$#%& work Windows box) and add permission to add/remove programs.

If this is your main account, have you changed the permissions or groups recently?

---

### Post by rgates on 2006-08-18
Thank you very much... The problem is resolved 

It, in fact, was the permissions problem. Wow, fast
response and right on the mark.

Thanks again,

---

### Post by Metacarpal on 2006-08-18
Glad I could help! :D

---

