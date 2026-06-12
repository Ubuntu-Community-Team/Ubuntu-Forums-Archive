---
title: "Command Question"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by Christopher on 2006-07-31
I was wondering the command i can type in console to see how big my swap file is. Thank you in advance. ;)

---

### Post by aysiu on 2006-07-31
```
df -h
``` **Edit**: Never mind. I guess that *doesn't* tell you your swap size. Try ```
top
```

---

### Post by Christopher on 2006-07-31
> **aysiu said:**
> ```
df -h
``` **Edit**: Never mind. I guess that *doesn't* tell you your swap size. Try ```
top
```


Thank you very much for the quick reply aysiu. :D

---

### Post by Christopher on 2006-07-31
top is pretty cool whats all that mean aysiu? At the top it says 2 users, whats that mean?

---

### Post by aysiu on 2006-07-31
Notice how the "user" running most processes is *root* and then the rest are being run by *christopher*?

Even though you haven't created a root account that you can log into, *root* is a "user" that runs some systemwide tasks.

---

### Post by Christopher on 2006-07-31
> **aysiu said:**
> Notice how the "user" running most processes is *root* and then the rest are being run by *christopher*?

Even though you haven't created a root account that you can log into, *root* is a "user" that runs some systemwide tasks.

Ok cool, thank you very much for the info.

My swap is: Swap:  1614492k total,        0k used,  1614492k free,   179872k cached

I have 768mb of PC2100 DDR, is my swap big enough? Thank you in advance.

---

### Post by aysiu on 2006-07-31
1.6 GB? Is that how big you made your swap? That's almost *too* big. Won't harm your computer, but it takes up a lot of disk space unnecessarily.

Unless I'm reading that wrong and it's really 161 MB, in which case it's too small.

---

### Post by IYY on 2006-07-31
The rule used to be "make swap twice the RAM" but today this is not really the case. With 768 MB you will barely need the swap.

---

### Post by Christopher on 2006-07-31
> **aysiu said:**
> 1.6 GB? Is that how big you made your swap? That's almost *too* big. Won't harm your computer, but it takes up a lot of disk space unnecessarily.

Unless I'm reading that wrong and it's really 161 MB, in which case it's too small.

Yep thats 1.6gig(1,614,492k) swap file, someone correct me if im wrong but i believe thats 1.6gig..hehe.

---

