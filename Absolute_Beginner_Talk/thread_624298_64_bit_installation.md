---
title: "64 bit installation"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by jmucha on 2007-11-26
can a 64 bit Ubuntu 7.1 installation work on a 32 bit machine? so far it is

---

### Post by mikewhatever on 2007-11-26
> **jmucha said:**
> can a 64 bit Ubuntu 7.1 installation work on a 32 bit machine? so far it is

No, but a 32 bits version can work of a 64 bits one.

---

### Post by rsambuca on 2007-11-26
Impossible.

Post the output of

uname -a

and what is your cpu?

---

### Post by jmucha on 2007-11-26
my cpu is an intel T2310 but I am on my Vista partition now (no wireless yet) so I can't post an output now but my Compaq is 32 bit

---

### Post by ryanVickers on 2007-11-26
you say "so far it is" !?!? :lolflag:
I know mac os x has some magic features to run the os, programs, and computer in any combo of 64/32 bit in certain conditions, but I'm not sure how exactly that works... :p

---

### Post by mikewhatever on 2007-11-26
> **jmucha said:**
> my cpu is an intel T2310 but I am on my Vista partition now (no wireless yet) so I can't post an output now but my Compaq is 32 bit

If I remember corrrectly, T2310 is core duo, a 32 bits CPU, which means you can't be running a 64 bits OS.

---

### Post by jmucha on 2007-11-26
although my Ubuntu 7.1 seems to be working okay, I guess I'll uninstall it and get the 32 bit version.

---

### Post by ryanVickers on 2007-11-26
well, you rather are already using 32 bit and just don't know it, or you have a 64 bit processor and just don't know it :p

Either way, if it's working, then it must be one of the 2 and, yeah, id it's al working, just keep it! :D

---

### Post by jmucha on 2007-11-27
well, it's a miracle,, I guess because the installation disk says for 64 bit computers and this a 32 bit machine??and the installation appears to be good except for the wireless card not beiing recognized.

---

### Post by ryanVickers on 2007-11-27
but, but, it defies all laws of computing!!!! *brain explodes*

oh, and wireless is always a struggle :p

---

### Post by asaz989 on 2007-11-27
> **mikewhatever said:**
> If I remember corrrectly, T2310 is core duo, a 32 bits CPU, which means you can't be running a 64 bits OS.

Actually, I'm currently running 64-bit on a core duo system; from my understanding, all of the dual-core 32-bit systems function as 64-bit (two 32-bit processors can run 64-bit arithmetic, maybe?). For whatever reason, when I was looking online for which version to install, I read that dual-core systems should be treated as 64-bit processors.

---

### Post by ryanVickers on 2007-11-27
well, that's not "real" 64 bit then - just adding the cores is not the same as a true AMD 64 bit :p

never liked intel, and now I know why... *sigh* ;)

---

### Post by asaz989 on 2007-11-27
> **ryanVickers said:**
> well, that's not "real" 64 bit then - just adding the cores is not the same as a true AMD 64 bit :p

Well, it works, anyway :P

---

### Post by rsambuca on 2007-11-27
The T2310 is a 64bit processor, according to the [Intel]("http://www.intel.com/products/processor/pentium_dual-core/specs.htm") site and [Wikipedia.]("http://en.wikipedia.org/wiki/List_of_Intel_Pentium_Dual-Core_microprocessors#.22Merom-2M.22_.2865_nm.29")  Guess the universe you live in still obeys the laws of physics.

---

### Post by mikewhatever on 2007-11-27
> **asaz989 said:**
> Actually, I'm currently running 64-bit on a core duo system; from my understanding, all of the dual-core 32-bit systems function as 64-bit (two 32-bit processors can run 64-bit arithmetic, maybe?). For whatever reason, when I was looking online for which version to install, I read that dual-core systems should be treated as 64-bit processors.

Once you've posted <uname -a> and <cat /proc/cpuinfo> outputs we shall all see. Meanwhile, all I can say is dual core CPUs are not necessarily 64 bits capable. That is one of the differences between Yonah and Merom CPUs, both dual cores.

[http://en.wikipedia.org/wiki/Intel_Core](http://en.wikipedia.org/wiki/Intel_Core)
vs
[http://en.wikipedia.org/wiki/Intel_Core_2_Duo](http://en.wikipedia.org/wiki/Intel_Core_2_Duo)

---

### Post by digby dart on 2008-01-25
This has to be one of the most amusing threads ever.

The t2310 is running 64bit Ubuntu - that is apparently impossible to some on here.

Then the t2310 is stated to be 64bit by intel but again that's not real 64bit according to the same author.

If one ran 64bit vista with a t2310 it goes quite happily but that would join the ranks of the impossible for those same persons in this thread.

Oh how hard it is to be so clearly wrong while being so determined to be so clearly right. :) If all else fails sound right.

---

