---
title: "Just a reminder - is YOUR cache working?  Type &quot;free&quot; in terminal to see."
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by emarkay on 2007-01-18
If not - and I had no clue MY cache was not enabled (since I first installed Ubuntu!) - then follow along with me to see what I had to do to get my cache working...

[http://ubuntuforums.org/showthread.php?p=2031150#post2031150](http://ubuntuforums.org/showthread.php?p=2031150#post2031150)

[insert befuddled but calm smiley here]

---

### Post by mcduck on 2007-01-18
I think you are talking about swap, not cache ;)

---

### Post by emarkay on 2007-01-18
Yea, oops; but at least I didn't say swapfile or pagefile....   :)

---

### Post by Buck2348 on 2007-01-18
I don't understand--could you tell us exactly what was wrong and what you did to fix it?

Buck

---

### Post by emarkay on 2007-01-19
> **Buck2348 said:**
> I don't understand--could you tell us exactly what was wrong and what you did to fix it?
Buck

I discovered that my disc swap was not enabled - and the above post link details what I had to do to fix it - to test, just type "free" into the terminal and see if your swap (disk cache) is enabled.

---

### Post by mikewhatever on 2007-01-19
It is set up, but zero of it is used, so I guess it's a no.

---

### Post by stoer on 2007-01-19
Quiet evening and just for interest i tried this...

```
steve@laptop:~$ free
             total       used       free     shared    buffers     cached
Mem:       1556156     356912    1199244          0      10896     204660
-/+ buffers/cache:     141356    1414800
Swap:       763016          0     763016

```

I see also a great big zero...:confused:  On or Off?
Having read your other link i'm even more confused :confused: 
How did you fix it in the end???

---

### Post by Enverex on 2007-01-19
If "Total" for SWAP is above 0 then it's working fine. Linux only USES it as a last resort.

---

