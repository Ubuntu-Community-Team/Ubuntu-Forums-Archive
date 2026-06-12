---
title: "320gig hardrive only about 298gig????"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by HoLLyw00dGT on 2008-03-04
Here's the deal:

I have been working on betting my linux to work right for the last week and a half. It has been nothing but me pulling out my hair and wanting to just say eff it and remove ubuntu. I mean i can't even get my res right for my tv! Anyway, thats a different story. I have a 320g hardrive...i did multiple reinstalls of windows and ubuntu last week trying to get my dual boot worked out, when i finally did, i'm only seeing about 298gig....where the hell does a random 20 gigs go???? If i go into disk management in windows xp i see my partitions and they only add up to about 298 gigs NOT 320! Did i ruin my hardrive?

-Justin

---

### Post by mcdan on 2008-03-04
this is because when they advertise 320gb, they mean 320*10^9 bytes, meaning 1000 bytes in a kb, 1000kb in a mb, and 1000 mb in a gb
but when a computer looks at it, it reads 1024 bytes in a kb, and 1024 kb in a mb and 1024mb in a gb, this is because 2^10=1024.
so, it takes the 320,000,000,000, bytes, and divides it by 1024^3... and the result is 298.02gb.  

hope that makes as much sense as it does in my head

---

### Post by newlinux on 2008-03-04
Hard drive manufacturers and most OSs use different definitions for the 1 GB. The former uses 10^9 while the latter uses 2^30 (I think or something like that). The difference is that for every 100GB your hard drive is labeled as, the OS will only report 93GB. There's nothing missing. II's a difference in definition.

---

### Post by stchman on 2008-03-04
> **HoLLyw00dGT said:**
> Here's the deal:

I have been working on betting my linux to work right for the last week and a half. It has been nothing but me pulling out my hair and wanting to just say eff it and remove ubuntu. I mean i can't even get my res right for my tv! Anyway, thats a different story. I have a 320g hardrive...i did multiple reinstalls of windows and ubuntu last week trying to get my dual boot worked out, when i finally did, i'm only seeing about 298gig....where the hell does a random 20 gigs go???? If i go into disk management in windows xp i see my partitions and they only add up to about 298 gigs NOT 320! Did i ruin my hardrive?

-Justin

That is absolutely correct.  Hard drive manufaturers are more marketing.  Remember there are 1024MB in a GB, 1024KB in a MB, 1024B in a KB.

So yes there are 320,000,000,000 bytes on your hard disk which translates into ~298GB.

---

### Post by HoLLyw00dGT on 2008-03-04
You know...my dumbass should have known that lol. I'm no hardware newb...i built this pc a month ago and i could have sworn it let me partition out of 320 but who knows. Well thx for answereing guys, it makes PERFECT sense. :oops:

-Justin

---

