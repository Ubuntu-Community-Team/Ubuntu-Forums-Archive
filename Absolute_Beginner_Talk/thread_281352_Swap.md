---
title: "Swap"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by Mazen on 2006-10-20
hey guys,
i have a small swap partition so i created a new one using partition magic on windows but it won't merge into the old one, is there any way to do that, or jst to make the SWAP drive bigger?
thanks

---

### Post by madmetal on 2006-10-20
> **Mazen said:**
> using partition magic on windows

why not use gparted from ubuntu?:-k

---

### Post by PriceChild on 2006-10-20
You can always just mount both...

---

### Post by Mazen on 2006-10-20
mm..how can i do that?
and would it have the same results in performance? ( ne is 350MB and the other is 2GB!)

---

### Post by madmetal on 2006-10-20
how much memory do you have?
i have 1.5gb ram and swap is most time not used at all..

---

### Post by ReaderRat on 2006-10-20
Why not just erase both partitions and re-partition the space as /swap?

EDIT: Are the spaces contiguous?

---

### Post by Mazen on 2006-10-20
i have 1GB of ram and i notice that my SWAP is not used too..so it means no big deal? i don't need to extend it that much?

---

### Post by po0f on 2006-10-21
With hard drive space being so cheap (and memory too), I don't see a problem with running two gigabytes of swap.  With today's multi-gigabyte memory configurations, I would at least equal swap space with memory (ie if you have two gigs of memory, why not two gigs of swap?).  Right now on my main box, I have 768 MB of RAM, and a two GB swap partition (I plan on upgrading to one gig of RAM).

Point is, you can never have too much memory (or swap).

---

