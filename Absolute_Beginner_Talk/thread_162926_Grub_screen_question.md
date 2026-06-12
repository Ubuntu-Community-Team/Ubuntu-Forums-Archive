---
title: "Grub screen question"
date: 2006-04-19
forum: Absolute Beginner Talk
---

### Post by x5452 on 2006-04-19
when my computer boots up, it starts at the screen saying GNU Grub version 0.95  then lists the following:
Ubuntu Kernel 2.6.12-10-386
Ubuntu Kernel 2.6.12-10-386 (Recovery mode)
Ubuntu Kernel 2.6.12-9-386
Ubuntu Kernel 2.6.12-9-386   (Recovery mode)

Ubuntu Memtest 86+

Other Operating system 
Microsoft windows xp Professional

first off what is the recovery mode, and what is the memtest?  also, why is there two kernel things, dont i only need one?  :confused:

---

### Post by Mustard on 2006-04-19
Recovery mode will drop you to a root prompt at command line, so that you can troubleshoot issues with root privileges from there.  Issues that this can help with are things like, misconfigured display settings, superuser privileges misconfigured, host configurations problems that affect superuser privileges and more.

Memtest will run tests on your RAM to see if it has any faults that may be causing issues with your system..ie mysterious restarts etc.

There are two kernels because you have upgraded an older kernel, but you can still boot to that older kernel.  This is actually quite helpful if your new kernel causes the system to not be able to boot, or other issues with new kernels that occasionally occur.  You can remove the extra entries if you like, but it's quite useful to have the extra entries, as I have said earlier.

---

### Post by yager on 2006-04-19
[QUOTE=x5452]first off what is the recovery mode, and what is the memtest?  also, why is there two kernel things, dont i only need one?  :confused:[/QUOTE]

I have not had to use the recovery mode yet so I have no answer there.  

Memtest is great for testing your computer's memory.  It immediately starts up a small program that runs your computer's memory through a series of complex tasks to verify that there are no defects.  My computer had been acting strange with random freeze ups and using memtest told me exactly what the problem was.  I was able to modify the Grub startup on my kernel to limit the amount of memory to avoid the defective spots in memory.  Once confirmed, I was able to get a replacement memory module.

There are 2 kernels because you upgraded the kernel during a recent update.  Instead of removing the old kernel, Ubuntu leaves it around and you can then pick which kernel to boot into using the Grub menu.  I supose this would be handy in the event that there was some conflict between a new kernel and your system.  You could always boot into the known good kernel to do testing.

---

### Post by brentoboy on 2006-04-19
there are two kernels becuase the first was installed by your original installer, the second (2.6.12-10-386) was added as part of an update.

the first wasnt removed, becuase what if the second one sucked really bad on your PC?  you have options.  You dont even have to do a system rollback or anything, just boot the old kernel.

once you know you like it, uninstll the old kernel using synaptic.

---

### Post by x5452 on 2006-04-19
ah that all make great sense, thanks very much, ill hang on to the other kernel for now because who knows how much a noob can screw up a kernel!!  :mrgreen:

---

