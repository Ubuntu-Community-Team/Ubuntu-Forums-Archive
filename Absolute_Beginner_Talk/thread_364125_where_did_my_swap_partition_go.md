---
title: "where did my swap partition go?"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by yvinogradov on 2007-02-17
i installed Ubundu today. I first tried manual partitioning and dedicated 12 Gigs for / and swap. It told me it failed. So I went back and chose autamatic mode. It did something and to my relief both XP and Ubundu loaded up nicely. Now it looks like my Ubundu has 11 Gigs to it, so I am guessing 1 Gig went to swap, but how can I tell for sure? Is there an application that can tell me (preferably in graphical mode) what partitions where and such?

Thanks.

---

### Post by i-am-me on 2007-02-17
On the live CD, there was a partitioning program called GParted (QtParted for Kubuntu). I believe you can use Synaptic (Adept in Kubuntu) to re-install it. If you don't want to, then you can always bott from the CD again and check.

---

### Post by fusiachi on 2007-02-17
From terminal
```

sudo fdisk -l

```
This will list your partitions for you.

---

### Post by yvinogradov on 2007-02-17
thanks. did both, it dedicated half a Gig to swap. Is that enough? I heard recommendations to make swap twice the size of my RAM, and I have 1 Gig of it. Should I worry about it?

Thanks.

---

### Post by fusiachi on 2007-02-17
Really depends on how you use your system.

It's entirely possible that 512mb is more than enough.  Then again, you could find yourself needing 2gigs--it really depends on what you're trying to do.

---

