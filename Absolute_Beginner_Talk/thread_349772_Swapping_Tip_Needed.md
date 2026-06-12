---
title: "Swapping Tip Needed"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by syalam on 2007-01-30
Is it better to swap out inactive processes to the disk or is it better to leave everything in RAM? I was thinking about changing my swappiness value but wasn't sure which would result in the best performance.

---

### Post by Tomosaur on 2007-01-30
Linux is pretty good with RAM. When it's needed, it's assigned pretty fast - and idle RAM is allocated to system processes (idle RAM is wasted RAM!), so the default is probably just fine. If you only have a very limited amount of RAM, then maybe you should think about forcing more swapping, but for most systems, you probably won't notice any benefit.

---

### Post by syalam on 2007-01-30
Cool thanks for the info, i guess its time for me to learn some more stuff...

Most of my processes are "sleeping" and one of them is a zombie what exactly does this mean?

---

