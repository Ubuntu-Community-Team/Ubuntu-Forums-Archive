---
title: "Need to make 1 continuous partition out of 3 using gparted"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by Yellowbelly on 2007-07-10
hokay. here's the deal. I got a 120gb hard drive from my brother which he had windows on it. He had 3 partitions, 1 for windows, 1 for movies and music, 1 for the rest, and a piece of 8mb of unallocated. Basically I need these 3-4 partions into 1. Problem is that moving around in gparted is a pain. Once I delete the partitions, there are 3 separate areas of unallocated crap. I just need 1 maybe 2 partions and not 3 or more potential ones. Is there any way to do this.

---

### Post by Inxsible on 2007-07-10
If you delete the partitions the unallocated areas should merge into one huge chunk

---

### Post by Yellowbelly on 2007-07-10
that what I thought but it doesn't wanna do that for some reason. I have like 39gb unallocated here, skip a space, 90gb unallocated here, skip a space, 8mb unallocated here (created unnecessarily by yours truely, Microsoft Windows)

---

### Post by Inxsible on 2007-07-10
> **Yellowbelly said:**
> that what I thought but it doesn't wanna do that for some reason. I have like 39gb unallocated here, skip a space, 90gb unallocated here, skip a space, 8mb unallocated here (created unnecessarily by yours truely, Microsoft Windows)
 
How about you format the entire drive using GParted on the LiveCD. You can later create whatever partitions you want

---

