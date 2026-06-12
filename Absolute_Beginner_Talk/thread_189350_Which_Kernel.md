---
title: "Which Kernel?"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by joewhite on 2006-06-05
I just did a uname-r and realised I have 386 kernel rather than 686 but I have an Athlon 1.8 gig, sigh. Does this mean I have to compile a new Kernel? Is there a quick way to upgrade?

---

### Post by mat1t on 2006-06-05
you should be able to find the equivalent kernel in synaptic that says 686 rather than 386. Installing that will take about 5 mins, then it will appear in GRUB on your next boot. Leave the old one in just in case it doesn't work.

Good luck

---

### Post by joewhite on 2006-06-05
Thanks. Should I disable my NVIDIA drivers? I installed the new ones.

---

### Post by Sutekh on 2006-06-05
Are AMD Athlons not K7 chips?  I don't know for sure though.  There is a kernel for K7 chips too.

How did you install the NVIDIA drivers?  

If you installed the **nvidia-glx** package, when you update the kernel, you should install the **linux-686**/**linux-k7** package.  
```
sudo apt-get install linux-686
``` OR```
sudo apt-get install linux-k7
``` It includes the restricted modules package, which will keep you NVIDIA drivers intact.  Otherwise you will need to reinstall them with the new kernel.  If you installed the NVIDIA drivers, from the NVIDIA web-site, you will definately need to again for the new kernel.



This link, although for Breezy, is still pertinent for choosing the right kernel.

[Ubuntu Forums - Picking the Kernel thats Right for You (Possible Speed Increase)]("http://ubuntuforums.org/showthread.php?t=85917")

---

### Post by localzuk on 2006-06-05
Did you install the official ones? If so, yes you should remove them, install the new kernel and then re-install the nvidia drivers.

---

### Post by mat1t on 2006-06-05
[QUOTE=Sutekh]Are AMD Athlons not K7 chips?  I don't know for sure though.  There is a kernel for K7 chips too.[/QUOTE]

Sorry, I completely forgot about that. I think you could well be right! :)

---

