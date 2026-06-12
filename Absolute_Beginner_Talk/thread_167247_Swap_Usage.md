---
title: "Swap Usage?"
date: 2006-04-28
forum: Absolute Beginner Talk
---

### Post by aPello on 2006-04-28
For Some reason my computer is tending to use very little swap, and have high ram usage. Everything seems to work normal however. I have had ubuntu installed before and this has never occured. 

My system stats can be seen here: [http://home.ruckus.biz/uptime/](http://home.ruckus.biz/uptime/) (I run apache/php for development reasons)

---

### Post by croak77 on 2006-04-28
You're ok as long has system performance is good. Cached should be counted as free. Do 'free -m' from a terminal and look for -/+ buffers/cache: line under free. That should be more accurate.

---

### Post by aPello on 2006-04-28
Free -m Produced:
```

ruckus@home:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           314        307          7          0         20        131
-/+ buffers/cache:        154        159
Swap:          313          0        312
ruckus@home:~$

```
Which is basically the same thing phpsysinfo says. Performance is fine, i just didnt think it was normal. Previously when i had ubuntu installed, it would use around 60% ram, and then use like 70% swap.

---

### Post by Sef on 2006-04-28
Linux usually uses the ram first and then allocates it as necessary.   if needed swap is used if no ram is free.

---

### Post by garner_nc on 2006-04-28
I have 640 megs of ram in my laptop. I've left in on for 2 days using Open Office, MySQL and  Apache (for development, not as a server), and web surfing. It's rare my machine touches the 256 meg swap partiton I have.  As I write this it's been on over 2 hours with MySQl etc. running and I have over 200 meg of free memory.

   There seems to be no real consensus on swap partition size. Most desktops I've seen with 512 meg of ram for normal personal use don't use much swap at all. I've known people with a gig of ram to set-up 2 gig swap partitions. Is this really reasonable? Maybe if you were running a database server with hundreds of hits per hour?

    How does everyone elses memory usage compare? Inquiring minds........

All the Best,
Doug White

---

### Post by NeghVar on 2006-04-28
Swap is generally twice the amount of ram present. I have 512 ram and a 1 gig swap file. My computer has been running non stop without log outs for about 4 weeks now (had a bad program that locked it all up) and I'm still only using 11% swap.

I had it up for 2-3 months or so before and it was using 27% I think when it had that bad program.

---

### Post by user1397 on 2006-04-28
All I have running is firefox, xpad, firestarter gui, gmail-notify, and a terminal, and out of my 1012 MB of ram, im using 995 MB, and out of my 2.965 GB swap partition (the default installation made it so), only 187 MB are being used.  What a waste of space!!!!!:(
I noticed, [COLOR=Black]croak77, that you said to type "free -m", instead of just "free."  
When I type free -m, i get this: 
                    total       used       free     shared    buffers     cached
Mem:          1012         997         14          0         49            217
-/+ buffers/cache:        731        281
Swap:         2965         187       2777


And when I type free, i get this: 
                         total       used       free     shared    buffers     cached
Mem:       1036648    1021796      14852          0      50316     222876
-/+ buffers/cache:     748604     288044
Swap:      3036244     192264    2843980
Why the different numbers?

[/COLOR][]("http://www.ubuntuforums.org/member.php?u=83560")

---

### Post by garner_nc on 2006-04-28
free shows Kilobytes by default.

free -m shows, you guessed it, Megabytes.


All the Best,
Doug White

---

### Post by user1397 on 2006-04-28
[quote=garner_nc]free shows Kilobytes by default.

free -m shows, you guessed it, Megabytes.


All the Best,
Doug White[/quote]
wow that was pretty obvious i feel like a ******* idiot! (it's okay my precious, it's okay) :D

---

