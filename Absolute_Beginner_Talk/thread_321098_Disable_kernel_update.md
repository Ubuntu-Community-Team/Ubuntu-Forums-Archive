---
title: "Disable kernel update?"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by kilou on 2006-12-18
Hi,

I'm using the latest vanilla kernel (2.6.19) on Edgy Eft. Should I disable any kernel updates in the update manager to prevent weird problems???? Any clue on how to do this??

Thanks

---

### Post by gigaferz on 2006-12-18
Hello,
I have a similar question.

Right now I'm using ubuntu 6.10.  A couple of weeks ago the systems showed me an update for the kernel.
Now its showing me another 26mb kernel update.
My question is: is this update necesary?
If I keep updating the system, am I going to end up with 6 or 10  obsolete kernels?
In windows there are this files $$unistalld330xxyy$$$ and those are kind of big, Is it going to be the same with ubuntu?

Tha nk you

---

### Post by lamego on 2006-12-18
Didn't tested myself but it should prevent kernel upgrades:
Create  /etc/apt/preferences with:
```
Package: 1001
Pin-Priority: 1001
```

---

### Post by pormogo on 2006-12-18
is there any reason that you would want to stop kernel upgrades. you could always delete the new kernels or choose just not to download them if you don't want them.

---

### Post by gigaferz on 2006-12-18
how do i delete old kernels?

---

### Post by kilou on 2006-12-19
> **pormogo said:**
> is there any reason that you would want to stop kernel upgrades. you could always delete the new kernels or choose just not to download them if you don't want them.

Since I use Vanilla kernel 2.6.19 I don't want or need kernel updates from Ubuntu. I just wonder if by any chance an kernel update from Ubuntu could mess with something now that I run a vanilla kernel. This is probably non sense because after all the vanilla kernel is now 2.6.19 and Ubuntu updates are only for the 2.6.17 kernel, right??? So I shouldn't get any updates anyway?

---

