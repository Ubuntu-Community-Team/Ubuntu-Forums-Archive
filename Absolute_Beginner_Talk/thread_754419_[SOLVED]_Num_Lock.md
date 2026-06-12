---
title: "[SOLVED] Num Lock"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by frayalejandro on 2008-04-13
Hi. How do I configure my Num Lock so that every time I boot it is turned on?

---

### Post by forestpixie on 2008-04-13
Not sure about laptops - but with my pc I installed numlockx and use that

```
sudo apt-get install numlockx
numlockx on
```

---

### Post by oilchangeguy on 2008-04-13
> **frayalejandro said:**
> Hi. How do I configure my Num Lock so that every time I boot it is turned on?

most computers have an option in the bios to enable number lock on at boot.

---

### Post by forestpixie on 2008-04-13
Yes indeed that's so and I've personally never seen one that doesn't, but mine has never seemed to work properly here - which is why I used numlockx - which does work - that said I haven't actually tried without since I started with feisty and it wouldn't work there.

Next time I reboot I'll look and see if it's changed at all.

---

### Post by frayalejandro on 2008-04-13
> **forestpixie said:**
> Not sure about laptops - but with my pc I installed numlockx and use that

```
sudo apt-get install numlockx
numlockx on
```

I allready installed it, but whwn I reboot my desktop, it still has the num lock turned off...

---

### Post by frayalejandro on 2008-04-13
> **oilchangeguy said:**
> most computers have an option in the bios to enable number lock on at boot.

Yes, and it is turned on on the BIOS. 
Since I have dual boot *windows and ubuntu*, when I boot from Windows :( it turns on the Num Lock automatically, but it doesn't from Ubuntu.

---

### Post by cardinals_fan on 2008-04-13
Check under the Services config (I think it's at System -> Services).  There might be a Numlock option.

---

### Post by frayalejandro on 2008-04-13
> **cardinals_fan said:**
> Check under the Services config (I think it's at System -> Services).  There might be a Numlock option.
 
Unfortunately, there isn't.

---

### Post by cardinals_fan on 2008-04-13
> **frayalejandro said:**
> Unfortunately, there isn't.
That's odd... the Services editor on Zenwalk has it :mad:

---

### Post by frayalejandro on 2008-04-13
yup.

---

### Post by frayalejandro on 2008-04-13
there is, indeed, a keyboard layout menu, but it shows no options to change the num lock function.

---

### Post by frayalejandro on 2008-04-13
:confused:

---

### Post by forestpixie on 2008-04-13
I don't know then I had the same issue as you worked in windows not in ubuntu - but numlockx worked ok for me. I'll search when I have a spare 10 minutes but can't do anything else I'm afraid.

---

### Post by frayalejandro on 2008-04-13
Thanks. 
I appreciate your help.

---

### Post by frayalejandro on 2008-04-13
:confused:

---

### Post by frayalejandro on 2008-04-14
> **forestpixie said:**
> Not sure about laptops - but with my pc I installed numlockx and use that

```
sudo apt-get install numlockx
numlockx on
```

This instruction finally worked. Thanks.

---

### Post by zvacet on 2008-04-14
[Here](http://easylinux.info/wiki/Ubuntu:Gutsy#Enabling_NUM_LOCK_at_boot)

---

### Post by frayalejandro on 2008-04-14
> **zvacet said:**
> [Here](http://easylinux.info/wiki/Ubuntu:Gutsy#Enabling_NUM_LOCK_at_boot)

Even better! Thanks a lot.:)

---

