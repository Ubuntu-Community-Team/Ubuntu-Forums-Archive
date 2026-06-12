---
title: "Ubuntu Edgy Problems"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by RankWeis on 2007-03-17
Well, It's that time of year again, when I decide to see if I like Linux. Every time I decide I do, but I keep coming up with problems.

Every time I start my computer(which isn't usually much, but it's still a problem) it takes a good 10 minutes for Ubuntu(Edgy Eft x86_64) to load. First I have to perform a manual fsck, then it has to restart again and load in.

Now, Gedit doesn't seem to want to ever run. Text Editor from the applications menu doesn't load, and typing in "Gedit" or "sudo Gedit" in the command line gives me:

Inconsistency detected by ld.so: ../sysdeps/x86_64/dl-machine.h: 416: elf_machine_rela_relative: Assertion `((reloc->r_info) & 0xffffffff) == 8' failed!

So, I'm reaching out! Thanks.

And, if you need them, system specs

Asus A8V mobo
1 gig corsair RAM
120 WD HDD
AMD 3500+
Some Nvidia graphics card

---

### Post by Drakkor on 2007-03-17
> it takes a good 10 minutes for Ubuntu(Edgy Eft x86_64) to load.
Jeez, don't know what to tell you, maybe try the 32bit  install ??  Mine boots up in about 45 seconds !

---

### Post by BarfBag on 2007-03-17
One of my friends was having that same problem.  I ended up just sending him over to [SimplyMepis]("http://www.mepis.org/").  That's even more newbie friendly then Ubuntu.  Virtually everything works out of the box.  If you decide to try it, grab version 6.5.  It's in beta right now, but VERY stable.

Now, onto your GEdit problem.  I'm not sure what could be causing this.  I notice that you typed it as "sudo Gedit."  The capitalization could be what's causing the problem.  Next time, type "sudo gedit" and then the location of the file you want to edit.  If you just want to open it through the terminal, simply type gedit.  If worst comes to worst, you could use a text-based editor called nano.  It works the same way as GEdit.

Hope this helps.

---

### Post by RankWeis on 2007-03-17
Ah, well, the capitalized 'g' isn't what I'd done in the terminal, it was a typo on the forum.

I also want to learn Linux, not just use it...it just seems like a useful bit of knowledge to have- so I don't want to completely be babied through the OS; plus, I don't feel like reformatting again, I had to do it about 4 times to get ubuntu to work, my hard drive needs a break Thank you for the suggestion though, and I'll keep it bookmarked.

I think the problem with the load time is my motherboard. It's always given me trouble, and on my old mobo, ubuntu would install flawlessly, and it was just the technical aspects I couldn't deal with, not so much the actual operating system.

---

### Post by BarfBag on 2007-03-17
> **RankWeis said:**
> I think the problem with the load time is my motherboard. It's always given me trouble, and on my old mobo, ubuntu would install flawlessly, and it was just the technical aspects I couldn't deal with, not so much the actual operating system.

That's possible.  It sounds like your new motherboard isn't as compatible as your old one.

I hope this works out for you.

---

### Post by PurplePenguin on 2007-03-17
Give the normal 32 bit version a shot... people have more problems getting 64 bit stuff working.  And you won't notice a difference in daily use, anyway.

---

