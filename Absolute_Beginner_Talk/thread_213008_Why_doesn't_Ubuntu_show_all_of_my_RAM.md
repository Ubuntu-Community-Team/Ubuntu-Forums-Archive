---
title: "Why doesn't Ubuntu show all of my RAM?"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by Cherry Popper on 2006-07-10
OK, so I'm checking out the System Monitor and I notice that under 'Memory and Swap History', it says I have 1009.7 MiB of memory. Shouldn't it be 1024? :confused:
I'm using 2x512MB RAM sticks if it matters.

---

### Post by echo $USER on 2006-07-10
Mine does the same.

---

### Post by donnysrx on 2006-07-10
mine show 1011.8, hadnt looked till I read your post, lol.

I got 2 x 512 too!

I'm certainly not going to worry about though, ;) , too small too notice any effect.

i dual boot with windows xp pro, (legit), and ubuntu faster , just.

---

### Post by kinematic on 2006-07-10
the memory that doesn't show up is memory occupied by the kernel and it can't be swapped out and therefore it doesn't show up
i have 512mb and 503mb is shown...nothing to worry about.

---

### Post by shuflie on 2006-07-10
That's strange, I've got 2 GB and in the User Memory section its showing up the full 2GB. Any chance that its memory being stolen by your motherboards for something like onboard graphics or sound?

---

### Post by verbatim210 on 2006-07-10
i notice windows does the same thing
kinematic sounds right, kernel taking it up
another theory maybe rounding up/down
this would explain why 2GB shows 2GB
the value is too high for the number rounding to show any significant difference.

infact, im pretty sure the ram gets rounded down.  
same thing applies for HDD capacity
notice how you never get a full 80GB hd?
you get like, 75.9GB or what ever.

---

### Post by GStubbs43 on 2006-07-10
Mine says 1003.8 MiB with two 512mb sticks. Just thought I would join in! ;)

---

### Post by verbatim210 on 2006-07-10
0.99GB with 2x512 sticks

---

### Post by fhqwhgads on 2006-07-10
Interesting. I just read this earlier:
[quote=Peturrr]There is also a physical memory limit with the 386 kernel. No more than 1GB ram is useable.
At least that is what I found out a year ago, don't know if this still applies.

Anyway, you definately want a 686 kernel automatically installed if the system is suited for it.
It should be quite easy to detect a processortype.[/quote]
here: [http://www.ubuntuforums.org/archive/index.php/t-193576.html](http://www.ubuntuforums.org/archive/index.php/t-193576.html)

Anyone in the know? Maybe I should test it myself. Mine shows 1011 of 1024 MB, I'm using 386 with a Pentium M 2GHz.

---

### Post by kinematic on 2006-07-11
> **kinematic said:**
> the memory that doesn't show up is memory occupied by the kernel and it can't be swapped out and therefore it doesn't show up.

that's what i was told by a friend of mine who uses gentoo...

---

### Post by Tom Brokaw on 2006-07-11
> notice how you never get a full 80GB hd?  you get like, 75.9GB or what ever.

Not sure how Linux or its GUIs count megabytes, but the difference is that the manufacturers - Maxtor, Seagate, et al - count the bytes in decimmal (bytes*10^x), where Windows (and I'm assuming Ubuntu since it's mentioned here) counts the bytes in binary  bytes^(a multiple of two)).

The former should be notated "GB" and the latter "GiB."  So HDD capacity in Gibibyte (GiB) = HDD capacity in Gigabyte (GB) x 10^9 / 2^30.  Or something like that, my head gets turned around.

I'd heard there was a class action against one of the manufacturers for this little quirk.

---

