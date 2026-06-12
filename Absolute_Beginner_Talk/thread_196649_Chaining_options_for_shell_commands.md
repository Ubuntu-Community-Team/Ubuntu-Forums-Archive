---
title: "Chaining options for shell commands?"
date: 2006-06-14
forum: Absolute Beginner Talk
---

### Post by jonboy99 on 2006-06-14
I can't quite figure out the syntax for this. I want to run make, but have more than one of the options.
Ie I want to run make with both the -i  and the -f switches.  If I just wanted the -f switch I would type 

 > make -f Makefile-i386

but if I type

 > make -f -i Makefile-i386

or 

 > make -fi Makefile-i386

for example, it doesn't work.  I've tried a few other ways with no joy.  How do I run both switches at once?

Cheers
Jon

---

### Post by 23meg on 2006-06-14
Because -f is a mandatory one to be put right before the file name, whereas -i is an option. You'll have to do ```
make -f Makefile-i386 -i
```Refer to the manpage when in doubt:```
man make
```

---

