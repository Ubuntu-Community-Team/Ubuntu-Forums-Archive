---
title: "laptop screen color too light, How can I darken?"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by mike_m on 2007-10-03
On my old Dell laptop my screen is too light and colors don't show right, many light colors view as almost white. I don't have any controls like a desktop monitor and can't find any setting in the System menu. I checked my bios / setup at boot for setting but found none.

How can I darken my screen colors a little?

Thanks, Mike

---

### Post by Terl on 2007-10-03
> **mike_m said:**
> On my old Dell laptop my screen is too light and colors don't show right, many light colors view as almost white. I don't have any controls like a desktop monitor and can't find any setting in the System menu. I checked my bios / setup at boot for setting but found none.

How can I darken my screen colors a little?

Thanks, Mike

There is usually some control to alter the screen brightness.  Does the laptop have an Fn key?

---

### Post by jensjk on 2007-10-03
You will have to enter the gamma settings. If you try in a shell:

xgamma

you will probably see a return of 1.0.

Try

xgamma -gamma 0.7

- jensjk.dk

---

### Post by mike_m on 2007-10-04
Terl, I do have Fn keys but they don't work with Ubuntu, thanks though :)

Jensjk, **xgamma returned** -> Red  1.000, Green  1.000, Blue  1.000 then **xgamma -gamma 0.7**  changed it to
<- Red  0.700, Green  0.700, Blue  0.700
thats a little better, thanks for the good tip! 
Are there other commands like that, for say, contrast?

Ps, I liked your web cam site, nice job.

---

