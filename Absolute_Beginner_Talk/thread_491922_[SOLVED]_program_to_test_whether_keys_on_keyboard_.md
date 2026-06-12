---
title: "[SOLVED] program to test whether keys on keyboard are working"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by hanzj on 2007-07-04
Hello, 
My PrintScreen button on my keyboard has stopped bringing up the "Print Screen" dialog window. (Applications -> Accessories -> Take Screenshot still works fine, however.) I tried popping the key off and seeing if there was dirt or something inside but it looks ok.

Is there a program that will "listen" in as I press keys on the keyboard and will give some indication that the computer has heard what I've just pressed?

I'm trying to diagnose the problem with the PrintScreen button... to see if it's a hardware problem or a software (ubuntu) problem.

Thanks.

---

### Post by energiya on 2007-07-04
Type
```

xev

```
in a terminal window. I'm not sure Ubuntu has it installed by default...

---

### Post by hanzj on 2007-07-04
Energiya,
Thanks. xev is installed by default. And that's just what I was looking for.

Thanks again!

---

