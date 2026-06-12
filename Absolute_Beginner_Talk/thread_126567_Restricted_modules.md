---
title: "Restricted modules???"
date: 2006-02-06
forum: Absolute Beginner Talk
---

### Post by Razorback on 2006-02-06
Is it OK to have linux restricted modules for both 686 and 386 loaded on your machine?  I am trying to get my 3d going on my ATI card and found that both show up in synaptic.  I am having no luck with the how-tos and am wondering if this may be causing problems.  I am running a Celeron cpu.

---

### Post by Kyral on 2006-02-07
Yes it is okay. 
[I]Begin Quick Explanation

[/I]Kernel modules have to be compiled against the kernel they are meant to go into. Since the 386 and 686 kernels, while exactly the same options, are different kernels, then the modules have to be compiled against them seperately, hence LRM-386 and LRM-686 (and -K7)
Only the modules for the running kernel will be loaded into memory (although the modules for the other kernels will still be on the HD, useful in some cases)
*End Quick Explanation*

---

### Post by Razorback on 2006-02-08
Thank you!

---

