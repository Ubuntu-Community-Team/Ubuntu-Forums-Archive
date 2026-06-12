---
title: "Unable to find mactel kernel patches for MacBook trackpad and fn keys"
date: 2008-04-08
forum: Apple Intel Users
---

### Post by goiuts on 2008-04-08
Hi everyone,
I read the guide "MacBook Santa Rosa" about making the trackpad working as on Mac OS X and also the FN keys... but it requires me to install via apt-get the mactel kernel patches.
When I add the urls indicated to my sources file and then run apt-get update and apt-get upgrade, simply no new packages are installed. 
May the urls be wrong?

Thank you in advance.

P.S. Do you know what repository (and how to) install the 2.6.24 kernel (Hardy???) that seems to have the same effect of the mactel patches? Thank you.

---

### Post by cyberdork33 on 2008-04-08
> **goiuts said:**
> Hi everyone,
I read the guide "MacBook Santa Rosa" about making the trackpad working as on Mac OS X and also the FN keys... but it requires me to install via apt-get the mactel kernel patches.
When I add the urls indicated to my sources file and then run apt-get update and apt-get upgrade, simply no new packages are installed. 
May the urls be wrong?

Thank you in advance.

P.S. Do you know what repository (and how to) install the 2.6.24 kernel (Hardy???) that seems to have the same effect of the mactel patches? Thank you.
Most everything that was in the mactel repo has been added to the standard gutsy kernel so there is no "newer" packages in the mactel repo anymore.... which is why nothing shows up. 

Hardy is released in two weeks, I would just wait for that, or install the Beta and update .

---

