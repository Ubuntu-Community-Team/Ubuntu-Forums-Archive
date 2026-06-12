---
title: "RAM usage"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by stonecoldjha on 2008-04-17
i run a desktop that has got 2 GB of RAM and a 2 GHz Core2Duo intel processor.can i not voluntarily increase RAM usage on ubuntu  to maximise the capabilities of my system.

---

### Post by StOoZ on 2008-04-17
yes, if I understood you correctly.

---

### Post by stonecoldjha on 2008-04-17
how can i increase RAM usage.

---

### Post by Oldsoldier2003 on 2008-04-17
> **stonecoldjha said:**
> i run a desktop that has got 2 GB of RAM and a 2 GHz Core2Duo intel processor.can i not voluntarily increase RAM usage on ubuntu  to maximise the capabilities of my system.

Ubuntu will use all the RAM it needs. The OS will also retain programs in RAM even when they are not needed (caching).  Linux memory management is pretty good but you have to look at it differently than you do with windows. use the terminal command free -m to check how your memory is being used.

---

### Post by kerry_s on 2008-04-17
search for swappiness

---

### Post by Oldsoldier2003 on 2008-04-17
> **kerry_s said:**
> search for swappiness

I know that people say that swappiness helps, but to be honest i haven't noticed a difference and dont think most users will unless they run their sytem maxed out on load most of the time...

---

### Post by herbster on 2008-04-17
What's the question here?

---

### Post by martrn on 2008-04-17
I 'think' the answer to your question here is no.

I belive it is the linux kernel that decides how much ram to use for physical applications, how much ram to use as a buffer and how much ram to use for chached applications that it belives you might be useing next.  

I don't think there is away to allicate memory without using a diffrent kernel, or without I belive downloading kernel source code and re-compiling your kernel.

Like I said this is what I think - linux has memory optimisations built in to the kernel.

---

### Post by stchman on 2008-04-17
> **stonecoldjha said:**
> i run a desktop that has got 2 GB of RAM and a 2 GHz Core2Duo intel processor.can i not voluntarily increase RAM usage on ubuntu  to maximise the capabilities of my system.

So let me get this straight, you want to increase Ubuntu's RAM usage?  If you want to do that then just open a massive amount of programs, burn a DVD, recode a .avi into an mpeg, etc.

The OS will use more RAM and swap as needed.  The less RAM it is using the better.  I find Ubuntu and the Linux programs it runs very efficient.

You could write a C program to dynamically allocate (malloc) about 1.5GB of memory to a double precision floating point array.

---

### Post by PetePete on 2008-04-17
> The less RAM it is using the better.

actually, no.. the more RAM in use == better

which is why ubuntu always seems to be at max memory in use (after few hours uptime), even if you dont have much open, unlike windows where you can see how much memory is currently in use, and see how much is free.

the idea is that if you open a large program, its better to store it in the memory even after being closed as you are v likely to re-open that program and its MUCH MUCH faster to reopen from memory than disk

so i have 1gb memory, currently got amarok, firefox, kmail and terminal open, yet I have 928mb of memory in use. ... Good thing :)

---

### Post by stchman on 2008-04-17
> **PetePete said:**
> actually, no.. the more RAM in use == better

which is why ubuntu always seems to be at max memory in use (after few hours uptime), even if you dont have much open, unlike windows where you can see how much memory is currently in use, and see how much is free.

the idea is that if you open a large program, its better to store it in the memory even after being closed as you are v likely to re-open that program and its MUCH MUCH faster to reopen from memory than disk

so i have 1gb memory, currently got amarok, firefox, kmail and terminal open, yet I have 928mb of memory in use. ... Good thing :)

I guess if you really want to maximize memory usage then set the swap file to like 128MB.

I think Ubuntu does a great job of memory management.  I have 2GB of RAM and the most I have ever see is aroun 450MB of usage when I had many apps open.  The system was still very responsive.

Here is a YouTube video of a guy TRYING to make Ubuntu crash.  They were unsuccessful.  I looks like they had about 30 apps open and Ubuntu still did its job and the K3b finished the burn.

[http://www.youtube.com/watch?v=y1uCM_fAtmU](http://www.youtube.com/watch?v=y1uCM_fAtmU)

---

