---
title: "Can I use cool'n'quiet for my AMD Opteron in Ubuntu?"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by SPQQKY on 2007-07-22
I was just wondering if cool'n'quiet works in Ubuntu? 
Also, how can I check to see what speed my cpu is running if it is available. Thanks.

---

### Post by wolfen69 on 2007-07-22
see this    [http://ubuntuforums.org/showthread.php?t=485447&highlight=cool+quiet+amd](http://ubuntuforums.org/showthread.php?t=485447&highlight=cool+quiet+amd)

---

### Post by SPQQKY on 2007-07-22
> **wolfen69 said:**
> see this    [http://ubuntuforums.org/showthread.php?t=485447&highlight=cool+quiet+amd](http://ubuntuforums.org/showthread.php?t=485447&highlight=cool+quiet+amd)
So how do I check if it is working? Within windows I can use CPU-Z, how do I check with Linux?

---

### Post by SPQQKY on 2007-07-22
> **SPQQKY said:**
> So how do I check if it is working? Within windows I can use CPU-Z, how do I check with Linux?

Anyone?

---

### Post by the.phantom on 2007-07-22
there was a bug with cool and quiet and think it was related to nvidia drivers and the solution was to turn it OFF

would lock up the system

---

### Post by SPQQKY on 2007-07-22
I ran cat /proc/cpuinfo in a terminal and it says my opteron 1212 is at 1GHz, so it appears the scaling is working. How can I recheck if it scales back up? What is a good cpu intensive app to run and check again to see if it scales back up?

Edit: Okay, I just decided to open a few videos with VLC and Totem at the same time and then ran cat proc/cpuinfo again and it showed the cpu at 2GHz.

---

