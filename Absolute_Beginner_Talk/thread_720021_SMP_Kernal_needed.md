---
title: "SMP Kernal needed"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by PawnerGaSp on 2008-03-09
Hey, i am on the 32 bit 7.10 Gusty, and I need the 2.6 SMP Kernel, I can't find it any where, I have an AMD Phenom and only one core is showing up...my 'uname -a' results are 
```
Linux gasp-desktop 2.6.24-11-386 #1 Fri Feb 29 21:28:00 UTC 2008 i686 GNU/Linux

``` 

I have looked in other threads and found out that i needed that kernel, but i need help getting it, i searched for a long time and i need help with it. 
Thanks
-GaSp

---

### Post by dcstar on 2008-03-10
> **PawnerGaSp said:**
> Hey, i am on the 32 bit 7.10 Gusty, and I need the 2.6 SMP Kernel, I can't find it any where, I have an AMD Phenom and only one core is showing up...my 'uname -a' results are 
```
Linux gasp-desktop 2.6.24-11-386 #1 Fri Feb 29 21:28:00 UTC 2008 i686 GNU/Linux

``` 

I have looked in other threads and found out that i needed that kernel, but i need help getting it, i searched for a long time and i need help with it. 
Thanks
-GaSp

The generic kernel has SMP built in, if you new processor does not show up correctly it is because you are using an ancient 386 kernel.

---

### Post by PawnerGaSp on 2008-03-10
I was using the 2.6.24-11 kernel and i just updated it to 2.6.24-12 and it works with all the cores perfectly, theres just one issue, no sound. It says it can't find the devices or something, but that isn't the place for it.  I read in another thread that this particular kernel breaks it, oh well, at least i can use all my 4 cores now = )
Thanks for the help anyway.

---

