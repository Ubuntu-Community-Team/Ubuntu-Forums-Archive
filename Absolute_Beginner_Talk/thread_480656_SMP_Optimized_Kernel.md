---
title: "SMP Optimized Kernel"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by bagrol1 on 2007-06-21
In this post:

[http://ubuntuforums.org/showthread.php?t=85917](http://ubuntuforums.org/showthread.php?t=85917)

there is a lengthy discussion about choosing i686-SMP kernel for a dual core CPU. That post started 2 years ago and more recent replies suggest that it is not valid anymore.

So does Fiesty install with SMP optimized kernel or installing this i686 kernel would benefit my rig speed with dual CPU? I am not sure but I think that standard Feisty kernel is i386 so what is i686 and should I worry about it???

Thanx

---

### Post by Quintin Riis on 2007-06-22
You needn't concern yourself with it.  Just install linux-image-generic and be happy.

---

### Post by Seisen on 2007-06-22
I think the only kernel avaliable through the repos is the generic kernel unless you feel frisky and want to build your  own.

---

### Post by 5-HT on 2007-06-22
> **bagrol1 said:**
> I I am not sure but I think that standard Feisty kernel is i386 so what is i686 and should I worry about it???

the -686 kernel is no more, -generic has SMP support enabled (-386 does not).

---

