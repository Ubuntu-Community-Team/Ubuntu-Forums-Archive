---
title: "Circuits designing program"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by zerofreeze on 2007-12-06
i need a perfect program that design circuits like EWB"multi sim" that works under ubuntu ...because i tried QUCS and some others and i think they are too old ...

---

### Post by kebes on 2007-12-06
> **zerofreeze said:**
> i need a perfect program that design circuits like EWB"multi sim" that works under ubuntu ...because i tried QUCS and some others and i think they are too old ...

I've never used it, but does [gEDA]("http://en.wikipedia.org/wiki/GEDA") do what you want? This Linux Journal article provides an overview of what gEDA can do:
[http://www.linuxjournal.com/article/8438]("http://www.linuxjournal.com/article/8438")

---

### Post by frafu on 2007-12-08
Hello, 

The Accessibility Forum being intended to talk about software related to disabilities, I have moved this thread to a more appropriate forum. 

Have a nice day. 

Francesco

---

### Post by AndyC_772 on 2007-12-08
> **zerofreeze said:**
> i need a perfect program that design circuits like EWB"multi sim" that works under ubuntu ...because i tried QUCS and some others and i think they are too old ...

Well, it's not "perfect" - somehow I doubt that's quite what you meant to say - but KICAD is pretty good. It includes a hierarchical schematic editor and a PCB layout tool.

If you need a simulation tool, the best I've come across by far is Linear Tech's LTSpice, but that's a Windows application. Maybe it would work under Wine.

---

### Post by zerofreeze on 2007-12-08
what is wine ?

---

### Post by kebes on 2007-12-08
> **zerofreeze said:**
> what is wine ?

[Wine]("http://www.winehq.org/") is a program that lets you run Windows programs in Linux. It's isn't perfect, but for many Windows programs, you can install them and they will run just fine. So if you have a piece of Windows software you want to run, it's worth a try.

---

### Post by AndyC_772 on 2007-12-09
I actually tried LTspice under Wine yesterday. It does work, though it seems slower than running it natively in Windows.

---

### Post by lethallogic on 2008-01-10
Hi, 

I am using Ubuntu 7.10
wine 0.9.46
and LTSpice 2.22c

I am unable to get any graphs to display.

Could you let me know how you got the graphics to work?

---

### Post by AndyC_772 on 2008-01-11
It just worked for me. Have you used LTSpice before? What happens when you click on a node - does the graph window open at all?

---

### Post by lethallogic on 2008-01-14
My bad! I was not adding nodes to the graph window!! Once I did that, voila it worked!

So,

Ubuntu 7.10, Wine 0.9.46 and LTSpice2.22c work together fine

---

