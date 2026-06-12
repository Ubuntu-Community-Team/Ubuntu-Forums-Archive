---
title: "How do I find my boot loader?"
date: 2005-07-27
forum: Absolute Beginner Talk
---

### Post by saelwen on 2005-07-27
A few years back I installed Mandrake 7.2 and partitioned my drive. At some point I dropped the boot loader (I think it was lilo?) prompt, and now I can't remember how to get it back...? Currently it just jumps straight into loading Windows, but I want to install Ubuntu on the partitioned section I set aside. I'm *REALLY* not sure where to go from here.  ](*,)

---

### Post by doobit on 2005-07-27
When you install Ubuntu the installer will give the option of installing a new bootloader after you format the partitions. The installer is pretty much step-by-step so just follow it. If you had Mandrake, then you probably already have three Linux partitions. The smallest one in the middle is the swap. the next smallest is the / or /root and the bigger one is /home. When the installer gives you the choice, go ahead and install the bootloader in the MBR. Grub is not as pretty as Lilo, but it works.

---

### Post by saelwen on 2005-07-28
So, basically, I can just install Ubuntu overtop of everything and not worry about re-partitioning everything again? Plus, if I'm working from Windows how would the downloading work? Is there a FAQ about this somewhere? A website? Something?

*sigh*

I wish there was a book I could hold in my hands and flip to the index... I'm *NOT* a visual learner..

saelwen
(a tactile learner in a visual world)

---

