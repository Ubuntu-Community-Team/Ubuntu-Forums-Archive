---
title: "Dual boot iMac G5 Ubuntu OSX - any traps?"
date: 2010-01-10
forum: Apple Hardware Users
---

### Post by aa4bb on 2010-01-10
I'm a new Ubuntu user and doing nicely with dual boot on the PC after much wrangling with partitioning issues.

Now I'd like to dual boot on my iMac G5. I've run the Live 9.04 with success except for wireless, which I think I can solve. If I plunge right ahead to install Ubuntu, will the partitioning be obvious and straightforward (i.e., not like the Vista nightmare)? Will I need to back up my OS X before I install? Is there some reference about partitioning on OS X that I need to consult to become more familiar?

Thanks in advance...

---

### Post by tiresia on 2010-01-10
> **aa4bb said:**
> Now I'd like to dual boot on my iMac G5. I've run the Live 9.04 with success except for wireless, which I think I can solve.
Yes, it shouldn't be a problem to install drivers for wireless
> If I plunge right ahead to install Ubuntu, will the partitioning be obvious and straightforward (i.e., not like the Vista nightmare)?
If you want to keep your MacOSX Partition, as it is without reinstalling it, you need to shrink that partition (according to your needs and to the capacity of your HD) with gparted before installing in the gained free space.

> Will I need to back up my OS X before I install?
**[COLOR="Red"]YES[/COLOR]**

> Is there some reference about partitioning on OS X that I need to consult to become more familiar?
Have a look on the powerpc FAQ in my signature

---

