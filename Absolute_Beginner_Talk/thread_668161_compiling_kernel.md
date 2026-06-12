---
title: "compiling kernel"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by andale on 2008-01-15
so, i don't that i understand this whole kernel thing quite right. I get that it's basically the hub of my OS but that's about it. My real question though would have to be "Does compiling your own (custom?) kernel make a big difference in the speed of operation? How hard is it? (Most importanly!) How hard is it to recover from if you screw it up?

I feel like I'm doing myself a disservice in firstly not knowing this and secondly not knowing if this is the thing to do to improve so many little problems.

---

### Post by lizzard on 2008-01-15
The adavantage of compiling his own kernel is that you will only insert the hardware drivers into the kernel you really need for your specific hardware configuration. So you'll get a slim kernel, that probably loads a bit faster than the standard kernel. If you plan to compile a kernel by yourself, follow the HowTo's that are available and - most important - don't delete your old kernel. Otherwise it could happen you won't be able to boot up, if your self-compiled kernel fails.

---

### Post by naja on 2008-01-15
hi
try this out,ive tested it myself
[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)
cheers

---

### Post by andale on 2008-01-15
ok, i understand that i guess, kinda like the equivalent of making your own winCD with Pete's winmaker (or whatever it's called) to remove all but the most important drivers to you. It makes the install faster and the load times are better for awhile, til u start adding things.
I think I'm not gonna do that right now, maybe if I make a new computer with more power. Sitting on a 1.2G Athlon with like 460 RAM (yah, I know, odd number)

---

### Post by family on 2008-01-15
Compiling your own kernel is overrated. The first time you do it, you pretty much spend 2 hours bleeding your eyes out at the Qconf screen, and I had it easy, cuz all of my specs are Intel.
Its all about optimization...
The speed difference for me was a boot time that was a half second faster or so, but that could be coincidence. Then again, I have 1 gig of ram...

---

### Post by fatality_uk on 2008-01-15
> **family said:**
> Compiling your own kernel is overrated. The first time you do it, you pretty much spend 2 hours bleeding your eyes out at the Qconf screen, and I had it easy, cuz all of my specs are Intel.
Its all about optimization...
The speed difference for me was a boot time that was a half second faster or so, but that could be coincidence. Then again, I have 1 gig of ram...

Here here. Life is FAR too short to be compiling kernels. Either:
1) You'll get hooked and ALWAYS be looking for that last 3.5% of extra processor power you KNOW is in there.
2) You'll just go blind!!!
3) You know this will happen!!! You have a decent, working machine and you think, "Hmm wonder if..."

---

### Post by naja on 2008-01-15
> **andale said:**
> 460 RAM (yah, I know, odd number)
hi
I am sitting on a notebook with 448MB!!
Well it is usefull to compile the kerenel to be able to apply custom patches,which i do to get my cpu undervolted,though it takes quiet long time to compile,you can make deb, rpm or whatever of it and install it in other pcs -with the same specification-.

---

