---
title: "Help Configuring Grub"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by punkrockscks on 2007-03-26
Hi.  I have a core 2 duo processor and when I turn on my computer, the default linux kernel is i386 and I noticed only one of the cores is being detected.  I tried the "generic" kernel and both cores are enabled.  
So I'm wondering if there is a way to remove the i386 kernels from the grub menu.  I can just pick "Generic" all the time, but sometimes I forget and just want them gone.  Also, where did they come from? It seems like after I installed the Nvidia drivers they showed up, but I'm not sure.

Thanks!

---

### Post by dacool25 on 2007-03-26
Start up Manager is a great fix to this problem, and you can totally customize the grub menu, even add backgrounds to it and adjust all of the settings your looking to adjust.  i believe there is a sub forum here for it.

---

### Post by punkrockscks on 2007-03-26
Thx, I'll look for it.  Man, I love this place!  Post a question, and 3 minutes later you get an answer!  :guitar:

---

### Post by igknighted on 2007-03-26
By using the generic kernels is your nvidia card still running the proper drivers?  If you want you can uninstall the 386 kernels in synaptic (or via apt-get remove).  I think the package name is "linux-image-386".  Be aware that the nvidia drivers might rely on these packages.  You might have to install them another way (Envy or by hand, or find a 3rd part repo with the nvidia drivers).

---

