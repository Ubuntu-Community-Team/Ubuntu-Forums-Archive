---
title: "[SOLVED] Is it possible to run Fx from swap, rather than RAM?"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by oldb0y on 2008-01-23
Is it possible to run Firefox form swap, instead of running it on RAM?

---

### Post by SOULRiDER on 2008-01-23
What do you mean exactly? Remember RAM is much faster than your hard drive.

---

### Post by Paulmd on 2008-01-23
> **oldb0y said:**
> Is it possible to run Firefox form swap, instead of running it on RAM?


NO. 

WHY??????

Even if it were possible, it's not a good idea.

---

### Post by dasunst3r on 2008-01-23
From what I've seen in most cases for Linux in general is that Linux would rather eat up all your RAM first before resorting to using swap.  I rarely, if ever, see Linux use 1/4 of my RAM.

---

### Post by oldb0y on 2008-01-23
I understand that it will run slower, but is it possible?

Edit: Is it possible to install Fx on swap-partition, and run it from there?

---

### Post by Paulmd on 2008-01-23
> **oldb0y said:**
> I understand that it will run slower, but is it possible?

Is this a real question, or is there some kind of bet going on? With money riding on the answer.

You can't override the memory management in Ubuntu, Nor should you.

You still havn't answered the question, "why do you want to?".

Some piece of WHATEVER program is running MUST be in ram, That's how modern computers are designed. Be it Dos, Windows, Linux, MacOS, Irix, OS/2. You Must have some piece of the program in ram. Period. 

Swap may act as additional ram, by storing pieces of programs that are not being used immediately. They are pulled into real ram when needed. You can not run ANY program entirely in swap space.

---

### Post by steveneddy on 2008-01-23
RAM is about 100,000 times faster than anything coming off of the hard drive, which is where the swap file partition is.

Maybe you need more RAM?

---

### Post by oldb0y on 2008-01-23
Easy now! It was just a thought I had... 
I'm not going to mess with my memory-management;)
Anyways, thanks for the reply guys!

---

### Post by jd65pl on 2008-01-23
[LIST=1]
[*]RAM that is not used is being wasted, the kernel will try to use all available ram
[*]If your system is aggressively swapping (using swap when there is free memory mostly on 2.14.xx kernels) then you should upgrade to another kernel
[*]Swap is just a portion of your hard drive that is used if your ram is is full, blocks which are not accessed often are put there
[*]If an application is in swap it needs to be transferred to RAM in order for it to be executed
[*]Memory management is done by the kernel, I very much doubt if you could force an application to be automatically swapped out
[*]Even if you could it is one of the most inefficient things you could do to an OS which goes against one of the three primary aims of an operating system[/LIST]

---

### Post by Delkster on 2008-01-23
> **oldb0y said:**
> I understand that it will run slower, but is it possible?
It's slower by several orders of magnitude. Computers have been designed to use RAM as their temporary storage so that's also what is being used for processes. Not using RAM isn't really an option -- it would take quite a bit of hacking on the low level of the operating system and perhaps even hardware, and if that were done, it would be very, very, very slow.

Perhaps you meant running Firefox so that it is using *mostly* swap. I don't suppose that's possible without specific hacks to the kernel (the core of the operating system) either, and I don't suppose anybody has done that for your convenience because in practical use it doesn't make any sense.

In any case, the thought experiment might be interesting but the practical result might not be what you wanted.

> Edit: Is it possible to install Fx on swap-partition, and run it from there?

That wouldn't make it use swap instead of RAM. After all, swap is on the hard drive, and the hard drive is where the browser is installed even now (albeit on a different partition than swap) and it still uses RAM when run. And no, that's not really possible without hacking either.

---

### Post by bodhi.zazen on 2008-01-23
LOL, sure, make a large swap file and physically downgrade to 64 Mb of RAM :twisted:

See this link : [http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

You can "tune" your system's swapiness, but you need some RAM.

---

