---
title: "Swap Space"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by SABOT00 on 2008-04-10
**DO I ABSALOTELY NEED A SWAP PARTITION?**
I have 4gb of ram

---

### Post by thisiam on 2008-04-10
no,but if you had say 2gb swap on a 500GB hardrive, you wont notice the  space missing.

---

### Post by PeterJS on 2008-04-10
Depends, if you've got a 32bit system you won't beable to address anything beyond 3.7gig so you won't even ever be using all of your RAM, much less any swap space you allocate. If you're on a 64 bit system, you can certainly make use of the space, if you're absolutely sure you'll never use more tha 4 gigs of RAM, you'll be fine. But if you ever get to 4.00001gig, rather than gracefully slowing down and moving stuff to swap your system will just stop loading stuff in to RAM, and likely crash.

---

### Post by ferdostar on 2008-04-10
No swap needed, but it's useful

---

### Post by NightwishFan on 2008-04-10
Swap is also used for hibernating. So you should at least have as your ram.

---

### Post by st33med on 2008-04-10
> **PeterJS said:**
> Depends, if you've got a 32bit system you won't beable to address anything beyond 3.7gig ...

actually, that is beyond 4 Gigabytes, if read correctly somewhere.

Anyway, it is a good idea to have swapspace just in case. A gigabyte would be good for you, minimum of half a gig.

---

### Post by kerry_s on 2008-04-10
no you don't, just install a dynamic swap program to cover just in case. they create swap files when swap is needed.
i've used swapd in the past(sudo apt-get install swapd) works good.
i'm currently using swapspace, to see if that's any good, just installed it about an hour ago, so i can't say anything about it.(sudo apt-get install swapspace)
there are others you can use instead, use google look into it.

i only have 256mb ram and i've turned off my swap partion. so if i crash or freeze then i'll know if it's working or not.

---

### Post by st33med on 2008-04-10
> **kerry_s said:**
> no you don't, just install a dynamic swap program to cover just in case. they create swap files when swap is needed.
i've used swapd in the past(sudo apt-get install swapd) works good.
i'm currently using swapspace, to see if that's any good, just installed it about an hour ago, so i can't say anything about it.(sudo apt-get install swapspace)
there are others you can use instead, use google look into it.

i only have 256mb ram and i've turned off my swap partion. so if i crash or freeze then i'll know if it's working or not.

Wait, dynamic swapspace? I have never heard of that! Once I get my lappy repaired and get off this Windows desky (BLEH), I think I will try that...

---

### Post by PeterJS on 2008-04-11
> **st33med said:**
> actually, that is beyond 4 Gigabytes, if read correctly somewhere.

Anyway, it is a good idea to have swapspace just in case. A gigabyte would be good for you, minimum of half a gig.

Yeah, I know the number is supposed to be 4 gig, but I could have sworn it rounded to something weird like 3.7 under most real world conditions.

---

