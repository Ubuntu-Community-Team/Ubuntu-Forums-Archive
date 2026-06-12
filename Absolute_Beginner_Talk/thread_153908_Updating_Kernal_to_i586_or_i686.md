---
title: "Updating Kernal to i586 or i686?"
date: 2006-04-02
forum: Absolute Beginner Talk
---

### Post by wolfee on 2006-04-02
I have a p4 3.o ghz 512 ram machine Should I use synaptics to update kernal? I tried from terminal the last time and it took 2 hrs!!! And I dont think things where configured right because even though i didn't see any error messages I didn't see any real differance in perrformance. But I want to try it again.:rolleyes:

---

### Post by trent dillman on 2006-04-02
The best way to get a performance boost from a kernel change is to actually compile your own, custom tailored to the specific hardware (which is a pain). But you can try, just don't uninstall the other one just in case...

---

### Post by wolfee on 2006-04-02
Ya I was just reading a post on linuxguestions.or on how this gut just copiled a kernal for gentoo. He said with a step by step instruction manual it aint to hard. Is there 1 for ubuntu?

---

### Post by bluevoodoo1 on 2006-04-02
Try this...
[http://ubuntuforums.org/showthread.php?t=85064](http://ubuntuforums.org/showthread.php?t=85064)

---

### Post by wolfee on 2006-04-02
[QUOTE=bluevoodoo1]Try this...
[http://ubuntuforums.org/showthread.php?t=85064](http://ubuntuforums.org/showthread.php?t=85064)[/QUOTE]
:D Thanx!! I don't remember if this is what I did the last time. I remember it took 2 hours!!! I'll give this a try!!

---

### Post by veighjay on 2006-04-02
so what's the difference? does upgrading to i686 make things work smoother/faster?

i have a toshiba laptop, pentium m1.6, 512ram, ati mob radeon 9600. how will i know if i benefit from i686 (which is what i am running atm)? or are these just silly questions?

thanks....

---

### Post by Perfect Storm on 2006-04-02
Mostly if you have 1g+ ram i686 is good to have. Also it is optimized for Pentium + and upwards.
But if you want the big effect you want to compile your own and disable stuff you don't use, add stuff you want to use, make some tweaks here and there.

---

### Post by veighjay on 2006-04-02
'disable stuff you don't use, add stuff you want to use'
what exactly do u mean by this? you mean options/programs in ubuntu? (i prob shouldn't be considering making a kernel if i don't even know this, but still, gota get into it somewhere :) )...
thnx...

---

### Post by Perfect Storm on 2006-04-02
No, when you compile a kernel, you have to enable/disable etc. in the kernel itself usually done with 'sudo make xconfig' (or similar tool).

---

