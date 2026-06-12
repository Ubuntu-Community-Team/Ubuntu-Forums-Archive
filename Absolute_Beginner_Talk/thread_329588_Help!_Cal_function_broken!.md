---
title: "Help! Cal function broken!"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by evanvlane on 2007-01-01
Hey,
I'm trying to use the cal function, and
```
cal
``` works just fine.

However
```
cal -j 2 2007
``` outputs

```
       February 2007
 Su  Mo  Tu  We  Th  Fr  Sa
                 32  33  34
 35  36  37  38  39  40  41
 42  43  44  45  46  47  48
 49  50  51  52  53  54  55
 56  57  58  59

```

It seems like it doesn't reset the counter, but I'm not sure how to fix the function...


Any ideas?

---

### Post by chippy99 on 2007-01-01
The -j option tells cal to use julian dates numbered from 1st of Jan, so output is correct. If you just enter cal 2 2007 you get the normal output.

---

### Post by evanvlane on 2007-01-01
Perfect. Thanks!

---

