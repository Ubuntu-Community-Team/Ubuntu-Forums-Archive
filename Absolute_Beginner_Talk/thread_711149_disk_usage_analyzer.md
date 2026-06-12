---
title: "disk usage analyzer"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by DarinB on 2008-02-29
how to use the disk user analyzer...
when i open it up it shows total filesystem capacity is 217.9GB
i have two hard drives one 160GB and a second (auto mnt) 75GB that is 235GB
it says 115GB available??????
that is both disks if i use preference i can take out the mnt and see how my main drive is.... 
how can i see each drive separate???? 
so i can keep an eye in the secondary drive with out all the extra calculations?
AND when i open my home folder that is on the primary drive it says 85GB free what is that????
 just the primary and why doesn't it match the other numbers????? 
even gparted shows different sizes?????
Bottom line i  want to keep an eye on things???????
Is there an easier way???????

---

### Post by philinux on 2008-02-29
I never liked DUA. I use System>Admin>system monitor

Click the file system tab. I've got it as a launcher on my top panel.

---

### Post by DarinB on 2008-02-29
exactly what i was looking for thanks!
why does terminal commands  :df -h -T give smaller values than the system monitor does?????????????????????????

---

### Post by herbster on 2008-02-29
I'm guessing df -h is showing you human-readable sizes while System monitor might be rounding the real values.

---

### Post by DarinB on 2008-02-29
so what is the -T value for??????
and thy round up and the terminal seems to be less that the gui or the gparted amounts... the gparted amount is 3 Gigs more at least

---

### Post by DarinB on 2008-02-29
Yeah i just checked it the terminal gives a lower value.
what is the amount i should leave to spare 10% or something like that?????
i remember in M$ it was less that a Gig but the overall drives where smaller too.

---

### Post by herbster on 2008-02-29
To spare? What do you mean specifically? If you're talking about having spare space for a swap file which is what I believe Windows requires, you don't need that on linux. You have a separate swap partition (or at least you should hehe), which is the "spare" space needed should all your RAM be in use.

---

### Post by DarinB on 2008-03-01
i don't think i espressed myself improperly.
i do know i should get a bigger hard drive before it fills up.
so at what point is that????
when i have a gig left or what????

---

### Post by herbster on 2008-03-01
You would get a new hard drive when you don't have enough space on the current one. It's really that simple :) If yours fills up completely and you need more space, then the obvious beckons..

There's no specific amount of space you need to have free, or amount that is a warning to get a new one or anything like that. Obviously, however, waiting until you've got 1mb of space left or something isn't a bright idea ;)

---

### Post by DarinB on 2008-03-01
ok thanks

---

