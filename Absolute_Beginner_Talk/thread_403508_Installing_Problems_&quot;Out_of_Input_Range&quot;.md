---
title: "Installing Problems &quot;Out of Input Range&quot;"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by kvarley on 2007-04-07
I have a Dell Dimension 5000 with a Pentium Prossessor 4 (hyperthread) with a HP Pavilion Monitor. The problem for me is I stick the CD in the drive, I go to install off the CD and after it has loaded my monitor pops up a message. "Input out of Signal Range"  Now I have tried using a different monitor which displays Ubuntu fine, I now realise it isn't to do with the monitor but the graphics card inside which is a newish 
Nvidia graphics card, I have tried booting up with "vga=none" but that messes up at the end. 

Anybody know how to solve this?

-Vitium-

---

### Post by freebird54 on 2007-04-07
I would try with a vga=###  where the number is for an appropriate value that your monitor can handle  (eg 791)

Here is a handy table:

C```
olours   640x400 640x480 800x600 1024x768 1152x864 1280x1024 1600x1200
--------+--------------------------------------------------------------
 4 bits |    ?       ?      770       ?        ?        ?         ?
 8 bits |   768     769     771      773      353      775       796 
15 bits |    ?      784     787      790      354      793       797 
16 bits |    ?      758     788      791      355      794       798 
24 bits |    ?      786     789      792       ?       795       799 
32 bits |    ?       ?       ?        ?       356       ?
```


Hope that helps!

---

### Post by igknighted on 2007-04-07
Your best bet would be to install via the alternate CD and then install the nvidia-glx package in recovery mode if need be.

As for fixing your issue, the problem is likely one of two places:

(a) your monitor is hard to detect.  One of Ubuntu's (linux's in general) weak points is monitor detection.  I always have to enter my exact horizontal and vertical sync rates manually to get it right.  You might have a similar issue.  If so, try hitting ctrl+alt+F1 when the screen gives that message.  That takes you to a terminal where you can run "sudo dpkg-reconfigure xserver-xorg" and then see if it works.

(b) you are using a dvi adapter for a vga monitor, or possibly even just a dvi monitor.  For some reason the default nvidia driver doesn't like this (especially the adaptor).  If this is the case, use a VGA output or install via the alternate disk and get nvidia-glx as described above.

---

### Post by kvarley on 2007-04-07
Thanks for the extremely quick responses! I will be letting you know how it goes, your help is much appreciated! 

-Vitium-

p.s. If anybody else has any more ways I would be delighted to know them!

---

### Post by kvarley on 2007-04-14
Thanks for alll the help, I much appreciate it! 

I have solved the problem like this:
> I hit Ctrl Alt F1 when the message popped up and inserted the code after the boot location, now I can view my installed Ubuntu!

---

