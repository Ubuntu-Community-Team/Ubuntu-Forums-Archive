---
title: "How to disable Synchronizing clock"
date: 2005-10-05
forum: Absolute Beginner Talk
---

### Post by oragon on 2005-10-05
evrytime ubuntu boots, it consume 5 mins to synchronize from ntp.ubuntu... since my box doesnt connected to internet. how do i disable this temporarily?
thanks!

---

### Post by fourchannel on 2005-10-05
i will tell you now, im not entirely sure how to set up boot up procedures in ubuntu, or any version of linux.

but your computer has ntpd installed. on my old computer i placed 
```
ntpd
``` into the /etc/rc.d/local file and it would launch it after it had finished booting. 

check your /etc/rc1-6.d's for ntpd in runlevels 3, and 5. i think.

i wouldn't suggest deleting them, but you might try renaming them..

```
# mv ntpd _ntpd
``` 
hope that helps. I'm sure there is a much more effecient, elegant, or perhaps even working way to do this. :)

---

