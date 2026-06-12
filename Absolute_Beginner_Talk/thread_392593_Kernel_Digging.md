---
title: "Kernel Digging"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by firefire on 2007-03-24
Is here anyone who would like to share his/her learning experience on studying Kernel?

I would like to study Kernel and understand it (not totally) within a year. 
Kernel is so beautiful. 
:KS :KS :KS :

---

### Post by markitect on 2007-03-27
I'm a little unsure how to answer your question, but I'm pretty sure you won't find much help on the beginners forum.  The Kernel is a fairly complicated mess of code, but most of it is very understandable.  Still you need to be familiar with linux programming, and the size and complexity keeps a lot of experience developers away.

If you know what you would learn about it that could be helpful, but if you want to pop the hood and look inside:
[LIST]
[*]learn C (im guessing you already know C )
[*]become familiar with compiling the kernel.
[*]Learn about booting off a new kernel  (initrd system.map etc)
[*]Learn about loading modules(lsmod insmod)
[*] Find a good book or tutorial that introduces the main sections and read it.  Linux Kernel Primer is a good one (with the lightsaber on the front)
[*] Pick an area of the kernel that interests you and look at the code(have your book handy)
[*] Mess with it, make some changes to a module and recompile, load it manually so when it crashes your system will work with a reboot. 
[/LIST]

The best thing you can do to increase you understanding of the kernel is to go through bits of code and do cleanup and commenting.  Reading the code to add comments about algorithms and functionality will not only increase your understanding, but are also a great way for someone new to the kernel to help out.

---

