---
title: "uname"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by arijarot on 2006-09-06
i'm confused about something... i was playing around in my terminal because i wanted to see what kernel version i had... i finally found the command to display it (uname) and this is what it said (uname --a):

Linux helsinki 2.6.15-26-386 #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006 i686 GNU/Linux

i'm pretty sure that the kernel version 2.6.15-26-386 refers to the x86 install that i made, but this is what i don't understand: i686. the help function said that this is my machine hardware name (uname --m)... doesn't i686 mean two processors (that's what i see ppl saying to update kernel to when they get a machine with a core duo processor)?

---

### Post by angkor on 2006-09-06
I think i686 just means an advanced version of the i386. It doesn't necessarily have anything to do with dual core procs. i686 kernels support dual cores and the i386 don't.

I'm running Ubuntu on an AMD x2 64 proc with a K7 kernel. My line also shows i686:

```
uname --a
Linux bayon 2.6.15-26-k7 #1 SMP PREEMPT Thu Aug 3 03:40:32 UTC 2006 i686 GNU/Linux
```

I think only the first part is actually your kernel name.

---

### Post by Anonii on 2006-09-06
> **arijarot said:**
> i'm confused about something... i was playing around in my terminal because i wanted to see what kernel version i had... i finally found the command to display it (uname) and this is what it said (uname --a):

Linux helsinki 2.6.15-26-386 #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006 i686 GNU/Linux

i'm pretty sure that the kernel version 2.6.15-26-386 refers to the x86 install that i made, but this is what i don't understand: i686. the help function said that this is my machine hardware name (uname --m)... doesn't i686 mean two processors (that's what i see ppl saying to update kernel to when they get a machine with a core duo processor)?
AFAIK i686 like angkor said is an advanced i386 architecture that can speed you up (a little) on Intel (and another company I dont remember) if it supports this architecture.

The command to see your kernel version and not all the other things is:
uname -r

---

### Post by arijarot on 2006-09-06
> **angkor said:**
> I think i686 just means an advanced version of the i386. It doesn't necessarily have anything to do with dual core procs. i686 kernels support dual cores and the i386 don't.

I'm running Ubuntu on an AMD x2 64 proc with a K7 kernel. My line also shows i686:

```
uname --a
Linux bayon 2.6.15-26-k7 #1 SMP PREEMPT Thu Aug 3 03:40:32 UTC 2006 i686 GNU/Linux
```

I think only the first part is actually your kernel name.

does that mean that my kernel is not the best for my machine ? should i upgrade it ? how does this work ?

---

### Post by arijarot on 2006-09-06
> **Anonii said:**
> AFAIK i686 like angkor said is an advanced i386 architecture that can speed you up (a little) on Intel (and another company I dont remember) if it supports this architecture.

The command to see your kernel version and not all the other things is:
uname -r

so if i change my kernel end to i686 my comp will work a little faster? do you know if i686 is as stable as 386(based on my experience)? are there advantages/disadvantages etc in switching ?

---

### Post by Anonii on 2006-09-06
> **arijarot said:**
> so if i change my kernel end to i686 my comp will work a little faster? do you know if i686 is as stable as 386(based on my experience)? are there advantages/disadvantages etc in switching ?
Unfortunately, I dont know, thats why I'm still using i386, even tho I believe that my machine supports i686.
But i'm sure that someone in here, knows the pros/cons and the stability of it. So.. just wait for a reply :]

---

### Post by arijarot on 2006-09-06
> **Anonii said:**
> Unfortunately, I dont know, thats why I'm still using i386, even tho I believe that my machine supports i686.
But i'm sure that someone in here, knows the pros/cons and the stability of it. So.. just wait for a reply :]

:D no problem, thanks, Anonii --  :-k we'll figure this out yet!

---

### Post by arijarot on 2006-09-06
what changes if i change my 386 to a 686? does this mean different software/hardware compatibility, for example? 

what is the difference between the 386 and 686 ?

---

### Post by Iowan on 2006-09-06
[http://doc.gwos.org/index.php/Kernel_Compilation_Dapper]("http://doc.gwos.org/index.php/Kernel_Compilation_Dapper")

> BRIEF EXPLANATION: if you open another Terminal and type: cat /proc/cpuinfo | grep "model name" you will see the exact model of your CPU. 386 will work on intel and amd processor (it's very generic). 686 is for pentium 2 or higher. K7 is for AMD 32bit processors (works also for AMD 64 bit). K8 is for AMD 64 processors.


---

### Post by comppsyco on 2006-09-06
I'm pretty sure that you can't just change the name, that you'll have to re-compile the kernel. There are plenty of gui's to do this, but I don't know any by name.

---

### Post by angkor on 2006-09-07
> **arijarot said:**
> what changes if i change my 386 to a 686? does this mean different software/hardware compatibility, for example? 

what is the difference between the 386 and 686 ?

Nothing much changes. Some have said their computers 'felt' a bit snappier (more responsive) but since the difference is so small this may just be a placebo effect. What does help is that the i386 used to support only up to +/- 900Mb of RAM (don't know if this is still the case). So if you have more it's a good idea to install the i686 or the k7 (for AMD).

to install the 686 kernel simply copy and paste this line in the terminal:

```
sudo aptitude install linux-image-686
```

Remember that any driver (or module I think) that you've setup for you current kernel needs to be build again for the new kernel (graphics, wifi etc).

---

### Post by arijarot on 2006-09-07
> **angkor said:**
> Nothing much changes. Some have said their computers 'felt' a bit snappier (more responsive) but since the difference is so small this may just be a placebo effect. What does help is that the i386 used to support only up to +/- 900Mb of RAM (don't know if this is still the case). So if you have more it's a good idea to install the i686 or the k7 (for AMD).

to install the 686 kernel simply copy and paste this line in the terminal:

```
sudo aptitude install linux-image-686
```

Remember that any driver (or module I think) that you've setup for you current kernel needs to be build again for the new kernel (graphics, wifi etc).

thanks, angkor.... curious, though, i never built any kernel for my graphics, wifi, ... ?

---

### Post by angkor on 2006-09-07
> **arijarot said:**
> thanks, angkor.... curious, though, i never built any kernel for my graphics, wifi, ... ?

Welcome, some people need to build specific drivers for their wifi cards and those are built for the kernel you are running at the time. If you install a different kernel you will need to rebuild those. I also think that if you're using the propietary nvidia or ati drivers you will need to reinstall them after the kernel upgrade.

The upgrade itself is painless, if the new kernel for some reason doesn't work as you'd expect you can always boot your old kernel from grub.

---

### Post by arijarot on 2006-09-07
> **angkor said:**
> Welcome, some people need to build specific drivers for their wifi cards and those are built for the kernel you are running at the time. If you install a different kernel you will need to rebuild those. I also think that if you're using the propietary nvidia or ati drivers you will need to reinstall them after the kernel upgrade.

The upgrade itself is painless, if the new kernel for some reason doesn't work as you'd expect you can always boot your old kernel from grub.

Thanks for the welcome :) i never built any kernel for anything, when install ed unbuntu it detected wifi and for my nvidia i just had to enable it... will it be that easy for the 686 too? my chip is a pentium 4, is it even worth it, since most ppl say you wont even notice the difference...?

---

### Post by Average Joe on 2006-09-07
As far as I know the 686 kernel is especially complied for Pentium 4 (or M) processors. So the 686 kernel should work smoother/faster when you have such a processor. I am running the 686 kernel and I didn't notice that much of a difference. Both the 386 and the 686 work fine for me.:)

---

### Post by arijarot on 2006-09-07
> **Average Joe said:**
> As far as I know the 686 kernel is especially complied for Pentium 4 (or M) processors. So the 686 kernel should work smoother/faster when you have such a processor. I am running the 686 kernel and I didn't notice that much of a difference. Both the 386 and the 686 work fine for me.:)

but you did notice a difference by upgrading though, right? are you on a P 4 too?

---

### Post by Average Joe on 2006-09-07
Yes, I have a Pentium 4 processor, or actually a Pentium M, since I have a laptop. I upgraded to the 686 kernel because it is supposed to be optimized for these processors. But I didn't notice any difference when I upgraded. However, since it doesn't run worse than before (i.e. the 386 kernel), I just stick to the 686 kernel, and I uninstalled the 386 kernel to save disk space.

---

### Post by arijarot on 2006-09-07
> **Average Joe said:**
> Yes, I have a Pentium 4 processor, or actually a Pentium M, since I have a laptop. I upgraded to the 686 kernel because it is supposed to be optimized for these processors. But I didn't notice any difference when I upgraded. However, since it doesn't run worse than before (i.e. the 386 kernel), I just stick to the 686 kernel, and I uninstalled the 386 kernel to save disk space.

thanks ave Joe :D i was wishing for a better outcome, but that's that... :roll:

---

### Post by Average Joe on 2006-09-07
> **arijarot said:**
> thanks ave Joe :D i was wishing for a better outcome, but that's that... :roll:

I guess it also depends on what you use your computer for. I don't expect it to perform better running the 686 kernel if you only check the Ubuntu forum on the Internet :). Maybe the difference only shows when you start using your CPU more seriously.

---

### Post by arijarot on 2006-09-07
> **Average Joe said:**
> I guess it also depends on what you use your computer for. I don't expect it to perform better running the 686 kernel if you only check the Ubuntu forum on the Internet :). Maybe the difference only shows when you start using your CPU more seriously.

you mean like having many apps open at once or something like programming, for example?

---

### Post by Average Joe on 2006-09-07
> **arijarot said:**
> you mean like having many apps open at once or something like programming, for example?

Exactly. But I am not sure if it will make a difference even then. I haven't tested it, and I am not planning to either. The 686 kernel works perfectly for me (as the 386) so there is no need for me to change it.

More on picking the right kernel you can find here:
[http://ubuntuforums.org/showthread.php?t=85917](http://ubuntuforums.org/showthread.php?t=85917)

---

### Post by arijarot on 2006-09-07
> **Average Joe said:**
> Exactly. But I am not sure if it will make a difference even then. I haven't tested it, and I am not planning to either. The 686 kernel works perfectly for me (as the 386) so there is no need for me to change it.

More on picking the right kernel you can find here:
[http://ubuntuforums.org/showthread.php?t=85917](http://ubuntuforums.org/showthread.php?t=85917)

Thanks, Joe, that's a great link :)

---

