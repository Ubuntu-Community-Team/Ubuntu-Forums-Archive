---
title: "Why compile?"
date: 2005-09-26
forum: Absolute Beginner Talk
---

### Post by sig_UVa on 2005-09-26
I am a noob and I keep reading about recompiling the Linux kernel to optimize for your system's architecture.  I installed Kubuntu on my Dell 8100 1Ghz, 512MB Ram, Nvidia Geforce Go (I think...32mb).  It runs pretty well and I like it, but if I could make it run faster, why not!  My question is will I see a good performance gain by recompiling?  Is it risky?  I won't lose my original install will I?  There are several Howto's on the Wiki..what's the best one for a noob?  Thanks for your help as always!!

---

### Post by bored2k on 2005-09-26
No you don't really want to compile. What you want is to install the linux-686 kernel if you have an Intel box (sudo apt-get install linux-686 from a terminal), restart and select that boot option. You might also want to enable prelink. [http://ubuntuforums.org/showthread.php?t=1971&highlight=prelink](http://ubuntuforums.org/showthread.php?t=1971&highlight=prelink)

---

### Post by sig_UVa on 2005-09-26
By installing this kernel, will I wipe out my existing install?  Thanks!

---

### Post by Turtle.net on 2005-09-26
No you will note wipe out anything (that's why linux is so wonderful you can change the heart of the system whitout re-installing everything).

If you want to really understqnd how linux works, I think that compiling a kernel is a good start. That's not SO difficult, but you'll certainly need some practice before doing it correctly. Be careful, compiling can be really annoying if you do something wrong.

But for performances, use a pre-compile kernel...that's the more efficient way to improve your linux box ;)

---

### Post by sig_UVa on 2005-09-26
Fantastic!  Thank you much!

I have an old box that I'll experiment on with compiling the kernel.  

Thanks again.

---

### Post by Duncan_Idaho on 2005-09-27
so, say, which kernel do I need to install for an athlon xp 2400+?
:confused: 
it's the k7, right??

---

### Post by Manny C on 2005-09-27
k7 kernel is optimised for athlon processors.

---

### Post by Duncan_Idaho on 2005-09-29
[QUOTE=Manny C]k7 kernel is optimised for athlon processors.[/QUOTE]
thanx man:)

---

