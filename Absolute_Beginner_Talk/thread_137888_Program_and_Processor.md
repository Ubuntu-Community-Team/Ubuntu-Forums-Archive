---
title: "Program and Processor"
date: 2006-02-28
forum: Absolute Beginner Talk
---

### Post by primetime on 2006-02-28
This might be a really crazy question, but programs compiled on a certain processor in Linux can't run on another type of processor right?

---

### Post by gord on 2006-02-28
not allways, it depends on how the person has compiled it, for example i compile most of my stuff with AthlonXP extensions so it runs quicker on my processor, but if i didn't include those then they would run just fine on other processors.

---

### Post by Jucato on 2006-02-28
Also, some programs for i386 will work also for i486,i586,i686 and their AMD equivalents. However, things change when you are talking about 64-bit processors and PPC (apple). These generally do not mix.  Some may work (i386 on 64-bit, but not vice-versa, I think). Other will definitely not (i386 on PPC).

So in the end you get 3 categories of processors: x86 (intel and AMD), 64-bit, and PPC.

---

### Post by primetime on 2006-02-28
So a linux binary can run on any flavour of linux?  The reason I'm asking is that if I have a binary compiled under i386, and I run it under a PowerPC processor will there be any adverse problems?  

Edit:  Ah thanks Fenyx.  So I gotta figure out some other way to run this program then.

---

### Post by Jucato on 2006-02-28
Generally, most sites offer different versions of a package/binary for different processors, sometimes even for different processors for the same category (x86's).

Try to check where you got that binary (btw, what is it?) and see if they offer it for other processors.

---

### Post by primetime on 2006-02-28
[http://www.bearware.dk/software.php?pageid=teamtalkd](http://www.bearware.dk/software.php?pageid=teamtalkd)

I ran it on a Live CD (i386) and it works.  However I plan to run this daemon off a PowerPC based computer.

---

