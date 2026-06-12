---
title: "Kernels, restricted modules, images, help?"
date: 2006-06-21
forum: Absolute Beginner Talk
---

### Post by bohboh on 2006-06-21
Can someone explain for noobies like me, the idea of kernels, the different versions, (intel, amd etc) and the idea behind restricted modules.

And also, compiling kernels, when and why would you need to do this.

I have been through hell getting my ati card 3d accelleration working and have come across all this. 

I know have K7 (AMD) installed with restricted modules for the K7 image. But that was because i followed a tut and not because i actually know what i was doing or even understand why i was doing it.

Many thanks.

---

### Post by xXx 0wn3d xXx on 2006-06-21
[QUOTE=bohboh]Can someone explain for noobies like me, the idea of kernels, the different versions, (intel, amd etc) and the idea behind restricted modules.

**A**: There are 4 basic kernel versions. 386 for older computers, 686 for Intel Pentium 2+, k7 for AMD processors running 32 bit Ubuntu, and a k8 kernel specifically for AMD 64 processors running 64 bit Ubuntu.

And also, compiling kernels, when and why would you need to do this.

**A**: Some people do it because new kernels have better hardware support while others do it because you can select/deselect options and tweak your kernel to maxium performance.

I have been through hell getting my ati card 3d accelleration working and have come across all this. 

I know have K7 (AMD) installed with restricted modules for the K7 image. But that was because i followed a tut and not because i actually know what i was doing or even understand why i was doing it.

**A**: Could you explain what problems you are having in the two paragrahs above ? Are you having trouble getting fglrx (3d accel) working ?

Many thanks.[/QUOTE]
Hope that answers some questions...

---

### Post by bohboh on 2006-06-21
Thanks for replying.

I dont have problems anymore, i just wanted to know what it was i actually did.

Especially the bit about restricted modules, what are they for?

---

### Post by steve.horsley on 2006-06-21
[QUOTE=bohboh]
Especially the bit about restricted modules, what are they for?[/QUOTE]
Restricted in the sense that they are not free to be copied, modified, redistributed in the way that GPL licensed stuff is. They contain software that is released under licenses that preclude inclusion with the main Ubuntu software set.  This includes 3d accelerators from ATI and nVidia.

---

