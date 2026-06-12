---
title: "max amount of ram with 32 bit processor/operating system"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by thebestofall007 on 2007-12-26
i have an acer 5610z laptop with one gig of ram and i was wondering what the maximum amount of ram i could upgrade to with a 32 bit processor/operating kernel (if i had either/or) and have ubuntu still read it all. my laptop can have up to four gigs according to specs, but i heard that if i didnt have a 64 bit processor/kernel Ubuntu wouldn't read all of it if i had the four gigs of ram.  also, how do i determine whether i have a 32 or 64 bit processor, as the specs dont clearly show this.

---

### Post by jas0 on 2007-12-26
32 bit architecture is limited to around 4 billion addressable bits of memory, or around 4GB. You will not get the full 4GB due to certain limitations. You will get around 3.25GB-3.75GB depending your how much video memory you have and a couple of other things determined by the kind of motherboard you have.

As far as the kind of processor you have--to find out run the following command:

```
dmesg | grep "processor"
```

---

### Post by Hospadar on 2007-12-26
Note, if you have a 64 bit machine that is running a 32 bit OS you will still only get 4 gig of adressable memory.  I suspect though that if you really need more than 4 gig, you'll be more worried about what kind of monster frankenstien app you are running than getting your wifi card to work, so 64 bit OS's are all good =)

Also I think if you have more than 4 gig sometimes OS's can still make use of it as some kind of funky swap deal and virtual adressing, but I'm really not sure how/if that works so I wouldn't count on it.

---

