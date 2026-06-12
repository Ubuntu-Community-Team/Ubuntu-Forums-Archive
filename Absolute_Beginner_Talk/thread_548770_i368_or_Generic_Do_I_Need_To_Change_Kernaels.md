---
title: "i368 or Generic: Do I Need To Change Kernaels?"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by StupendousMan on 2007-09-11
Hello all.  I am an absolute n00b to Ubuntu (been using it for less than a month),  and I was reading something in a magazine article by Barry Shilliday in *Personal Computer World* magazine about switching from the i386 kernel to the Generic kernel.  He mentioned in the article that "a CPU-optimized kernel will run much faster."

My question is this: as a total n00b who is still trying to get the hang of using Linux, do I, *should I*, even try to install a different kernel and will the benefit be worth the effort?

Thanks for the input!  :)

---

### Post by aspen_dv on 2007-09-11
Hello,
Yes, you can install many kernel as you would like. 
Benefits: you can switch back and forth between kernel. it's good if you are developing or testing hardware/software that can only works on certain kernel.
There isn't really much effort, most kernel are precompiled. Unless you are trying to compile the kernel to your specific needs.

---

### Post by az on 2007-09-11
The default install uses the generic kernel already.  The generic kernel is a 386 type kernel but will use 686 or k7 optimizations at run-time.  It used to be that those optimizations were only available at compile-time which meant that if you wanted to use them, you needed to recompile the kernel or install a different kernel.  

This is no longer so and the generic kernel handles all 32-bit architectures just fine.

---

### Post by StupendousMan on 2007-09-12
OK, great!  Thanks for the information.  Coming from a Windows environment as a power user, I'm willing to give changing and compiling kernaels a try, but since this is a totally different OS it's all just a bit intimadating trying to learn Linux *and [ubuntu* at the same time. Thanks again!  :)

---

