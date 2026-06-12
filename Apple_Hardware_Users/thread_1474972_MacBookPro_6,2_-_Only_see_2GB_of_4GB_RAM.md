---
title: "MacBookPro 6,2 - Only see 2GB of 4GB RAM"
date: 2010-05-06
forum: Apple Hardware Users
---

### Post by kripkenstein on 2010-05-06
I installed 32-bit 10.04, and only see 2GB of the 4GB available:

```

$ free -m
             total       used       free     shared    buffers     cached
Mem:          2193       1223        969          0         57        817
-/+ buffers/cache:        348       1844
Swap:         4092         25       4066

```

I was expecting to see 3GB of memory (since I installed 32-bit Ubuntu), which is what I was used to on other systems, but 2GB seems odd. Is there a way to improve things?

---

### Post by linuxopjemac on 2010-05-06
I remember something like a pae kernel ? I think that will enable more RAM in 32 bit...

---

### Post by abel_bcn on 2010-05-06
I've got the pae kernel 32-bit ubuntu and I get the 4 gigs:

>              total       used       free     shared    buffers     cached
Mem:          3875        586       3288          0         83        236
-/+ buffers/cache:        266       3608
Swap:         2259          0       2259


---

### Post by kripkenstein on 2010-05-06
Thanks guys, with the pae kernel things look ok :)

---

