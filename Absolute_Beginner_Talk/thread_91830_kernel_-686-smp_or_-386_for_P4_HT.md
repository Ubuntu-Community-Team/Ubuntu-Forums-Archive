---
title: "kernel *-686-smp or *-386 for P4 HT?"
date: 2005-11-18
forum: Absolute Beginner Talk
---

### Post by domino on 2005-11-18
Please excuse me, i'm still a work in progress Ubuntu user.

I have a P4 2.8C HT processor. All this time, I was under the impression that the 686-smp kernel was better than the 386 kernel. I looked at the boot logs and I noticed that on the  686-smp, HT was disabled! So i'm saying to mysefl, WTF!? Being relativly new Linux, this is NOT GOOD, correct?

Now that I booted to the 386 kernel, vmware will not start unless I recompile it to use the 386 kernel. Is there a command that will tell me what other applications need to be recompiled so that it will use the 386 kernels? Or is this a "see what happens" thing? Does anyone have other pointers to make these application transition back to the 386 kernel as painless as possible? Is it safe to uninstall the 686-smp source, headers, and the kernel itself?

Thanks

---

### Post by gord on 2005-11-18
its perfectly safe to uninstall the 686 kernel and headers, on your boot menu (grub) it will just not display them anymore, will still display your 386 headers though.

allthough i think hyper threading... isn't really supported all that great in the linux kernel yet (might be wrong on that, might just have to compile your own kernel and enable it yourself), using a 686 kernel isn't a bad idea. its optimised for newer processors.

---

### Post by domino on 2005-11-18
I kind of grasp your point gord. It makes sense that using 686 is better than 386. I hope someone here knows for sure whether it's better to use which kernel for the P4C HT. If compiling my own kernel with HT enabled only get me less than 5% performance, then I can live with not compiling it.

---

### Post by domino on 2005-11-18
I think a better support thread is here:

[http://ubuntuforums.org/showthread.php?t=85917&page=9](http://ubuntuforums.org/showthread.php?t=85917&page=9)

---

