---
title: "Ubuntu freezes / locks up randomly"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by TURNER on 2007-09-26
hi all, help would be appreciated in order to resolve the following problem:

I am running feisty on an IBM thinkpad p3, using a wireless card from belkin, for some strange reason my laptop freezes/locks up completely randomly, when it does lock up I am unable to move the mouse or perform any tasks, if music is playing it simply stops.....I have absolutely no idea where to start here, and have read a few threads with similar issues however none seem relevant in this case and have been attributed to graphics cards...any ideas??

If you need further info in order to debug this issue I would be more than happy to provide it,,,

thanks in advance,

---

### Post by Terl on 2007-09-26
Could you expand on your system specs (ram, cpu, etc)?

I wonder if it may be a resource issue.   At the times this happens are you running a lot of programs?

---

### Post by TURNER on 2007-09-26
Hi, i have p3 processor with 512 ram....iam not running many problems when this happens, the times when this has happened however I have been using either firefox or songbird.....I wonder if this is somehow related...in that they are both based on the same engine?

---

### Post by wpshooter on 2007-09-26
> **TURNER said:**
> Hi, i have p3 processor with 512 ram....iam not running many problems when this happens, the times when this has happened however I have been using either firefox or songbird.....I wonder if this is somehow related...in that they are both based on the same engine?

Should be easy enough to diagnose.

Just uninstall the Songbird software, restart the computer and test it out for a while and see if it still freezes.

Have you considered that it could be an overheating problem ?

---

### Post by TURNER on 2007-09-26
seems to be a resources issue...with just one firefix open tapping free in a terminal reveals:

```
turner@turner-laptop:~$ free
             total       used       free     shared    buffers     cached
Mem:        515468     364888     150580          0      19872     212792
-/+ buffers/cache:     132224     383244
Swap:      1253028          0    1253028
```

over heating could also be an option the fans are running alot on the laptop, even when its only been used for a few minutes...

any tips would be appreciated here.....maybe a switch to xubuntu?

---

