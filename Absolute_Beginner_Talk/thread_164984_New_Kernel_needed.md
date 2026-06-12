---
title: "New Kernel needed?"
date: 2006-04-23
forum: Absolute Beginner Talk
---

### Post by 1derphull on 2006-04-23
I have a AMD Athlon 64 +2800, running Ubuntu 2.6.12-10-386.

Should I be running 2.6.12-10-686?

If so, how can I do this without repartitioning/reinstalling?

I've installed a ton of stuff on here in the past few days and wouldnt know where to begin if I needed to totally reinstall.

---

### Post by xXx 0wn3d xXx on 2006-04-23
[QUOTE=1derphull]I have a AMD Athlon 64 +2800, running Ubuntu 2.6.12-10-386.

Should I be running 2.6.12-10-686?

If so, how can I do this without repartitioning/reinstalling?

I've installed a ton of stuff on here in the past few days and wouldnt know where to begin if I needed to totally reinstall.[/QUOTE]
No, you should be using the k7 kernel. It's designed for AMD processors. You don't need to re-install/repartition.

> sudo apt-get install linux-k7 

If you have dual processors/cores:

> sudo apt-get install linux-k7-smp

---

### Post by 1derphull on 2006-04-23
Wow, thanks for the quick reply!

---

### Post by xXx 0wn3d xXx on 2006-04-23
[QUOTE=1derphull]Wow, thanks for the quick reply![/QUOTE]
No problem :) I'm using an AMD 64 processor too.

---

### Post by 1derphull on 2006-04-23
Just installed it, and rebooted now running 2.6.12-10-k7. :)

Let me just say that this is one of the BEST and most HELPFUL communities I've come across in all my years online!  

This experience is making it easier for me to migrate over to Linux, I'm switching because I've been a Windows user all my life and don't want to migrate to Vista down the road. Might as well start learning Linux now!

---

