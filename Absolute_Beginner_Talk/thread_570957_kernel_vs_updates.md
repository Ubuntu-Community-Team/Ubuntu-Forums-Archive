---
title: "kernel vs updates"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by tronnix75 on 2007-10-08
what is the difference between running the updates like windows updates than updating the kernel manually via commands?:confused:

---

### Post by scrooge_74 on 2007-10-08
You don't always update your kernel, but you get frecuent updates of other apps in your system.
Also you can make updates  of the kernel or the apps an automatic task or run it manually.

---

### Post by tronnix75 on 2007-10-08
thanks for the quick reply, so what do i do to update the kernel and is there a program to run live updates?

---

### Post by Crenfinkle on 2007-10-08
From what I understand, the Update Manager will update the kernel after it has been thoroughly tested with all of the different architectures and Ubuntus.....

I think that getting the update from the community (who have had a good chance to test it with Ubuntu in many different configurations) is much better than updating manually via commands and "throwing caution to the wind."

just my opinion though...

---

### Post by oilchangeguy on 2007-10-08
why make life hard? when you are prompted to perform updates (the little star burst icon near the clock) just do it.

---

### Post by tronnix75 on 2007-10-08
i need to know how to do this stuff manually for my job, i need to know how to update the kernel, where do i get the latest for ubuntu? and tweak it..  does the update manager only update apps not the kernel?

---

### Post by oilchangeguy on 2007-10-08
> **tronnix75 said:**
> i need to know how to do this stuff manually for my job, i need to know how to update the kernel, where do i get the latest for ubuntu? and tweak it..  does the update manager only update apps not the kernel?

what job requires you to know how to manually update ubuntu? and why? when the operating system will hand you updates when they are available. you, and your employer are wasting time.

---

### Post by macogw on 2007-10-08
The update manager will automatically update new Ubuntu kernels that are fully tested.  You'll know it happened because those are the only updates which prompt a reboot.

If you want to install a newer vanilla kernel from kernel.org, you'll probably have to look that up with Google.  You have to compile it, but I don't know how to do it.  We don't know how the vanilla kernel will work with your hardware, though, and you might have to recompile some drivers.

Why do you need to know that for work? O_o

---

### Post by scrooge_74 on 2007-10-08
> **tronnix75 said:**
> i need to know how to do this stuff manually for my job, i need to know how to update the kernel, where do i get the latest for ubuntu? and tweak it..  does the update manager only update apps not the kernel?

you open a terminal then type

sudo apt-get update
sudo apt-get upgrade

say yes and that is all

you can also do it from synaptic which is in the Admin section

or from the terminal 

gksudo synaptic

---

### Post by Hospadar on 2007-10-08
If you want to manually update your kernel or re-compile it because you need some special options, there's really no easy place to do it.  The first thing you would want to do is download the source from the latest kernel out of the repositories and then you'll need to do a little hunting to find out how to get it all working right.

---

### Post by JBAlaska on 2007-10-08
If you really want to compile a newer kernel there is a great little utility called [KernelCheck](http://kcheck.sourceforge.net/) that can make the process almost painless, check out this thread;
```
http://ubuntuforums.org/showthread.php?t=311158
```

---

### Post by master_kernel on 2007-10-10
> **JBAlaska said:**
> If you really want to compile a newer kernel there is a great little utility called [KernelCheck](http://kcheck.sourceforge.net/) that can make the process almost painless, check out this thread;
```
http://ubuntuforums.org/showthread.php?t=311158
```
Thanks for the KernelCheck mention, just wanted to add that it will have support for installing nVidia and ATi drivers in the next release.

---

