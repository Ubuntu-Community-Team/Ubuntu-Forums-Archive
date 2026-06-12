---
title: "Swap File at Install"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by Hahnarama on 2006-11-01
OK I have used GParted to add partion space, and I thought I was ready to go. I format the it and hit install. It keeps stopping at step 5 of 6 saying that I do not have any Swap File space. I was never prompted for it. How can I set this required space? And out of 11 GB set aside for Ubuntu how big should my swap file be?

Thanks,

---

### Post by bsussman on 2006-11-01
2gig or 2xmem size, whichever is smaller

This is the maximum that linux will actually use, though wasting more will not harm you.

---

### Post by raqball on 2006-11-01
> **bsussman said:**
> 2gig or 2xmem size, whichever is smaller

This is the maximum that linux will actually use, though wasting more will not harm you.

Respectfully disagree... The swap is a basic emergency memory dump. X2 ram is old school way of doing it. I would say set it at the ram you actually have but thats just my opinion.

---

### Post by Hahnarama on 2006-11-01
> **bsussman said:**
> 2gig or 2xmem size, whichever is smaller

This is the maximum that linux will actually use, though wasting more will not harm you.

Great! now I just need to find out how to set up it up during the install process and I will be all set.

---

### Post by taurus on 2006-11-01
> **bsussman said:**
> 2gig or 2xmem size, whichever is smaller
That was an ancient method!!!  You probably don't need more than 512MB of swap space!  Anything more than that is probably a waste of space...

---

### Post by dillbertdabomb on 2006-11-01
1024mgs works for me
(1gib)

---

### Post by Hahnarama on 2006-11-01
HELP! :) I still need to know how to set up the Swap File during the initial install process.


Thanks

---

### Post by raqball on 2006-11-01
Easy go to custom partitioning then

Set your partitions for the HD..

I have an 80gb HD and here is what I have (no dual boot, Ubuntu only)

/ (5gb)
swap (1gb)
/home (rest of hd)

If you are using the standard install it will auto set a / and a swap :)

---

### Post by raqball on 2006-11-01
In your case with 11gb... I would set as follows:

/ 5gb
swap (your actual memory size)
/home (the rest of available space

Hope this helps if not ask away :)

---

### Post by dimnullspace on 2007-02-07
What are the settings for swap?

i.e. mout point = none?
.
.
.

do you just make a partion and name it swap?

when i do that the install still asks for a swap partion...

does swap live above ./    root dir?

that is during the partioning what makes swap diff from:

/ (5gb)  <-------this
swap (1gb)
/home (rest of hd) <-------or this


Regards

aha

---

