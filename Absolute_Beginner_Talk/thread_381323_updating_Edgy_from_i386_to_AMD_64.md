---
title: "updating Edgy from i386 to AMD 64??"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by jbulcher on 2007-03-10
Hi guys!

I'm a bit (read very) new to Linux, and for a number of embarrassing reasons I won't go into, I accidentally installed the i386 version of Ubuntu instead of the version that supports the AMD 64. I managed to do a lot in terms of setting up Linux before I realized my error - is there a way to upgrade to the 64 bit version without losing everything - like installing a package or something?

I tried searching the forums for an answer, but I had no luck. If there is something out there, maybe one of you could point me in the right direction?

Thanks much!

---

### Post by igknighted on 2007-03-10
No, i386 cannot be "upgraded" to x86_64, but this mistake might be a blessing for you.  AMD64 is really just a subset of x86 architecture (i386 Ubuntu).  Therefor, it is fully supported by i386, but not vice versa (kind of like the square is a rectangle but a rectangle isn't a square type of deal).  AMD64 Ubuntu is very young.  There are some bugs, but the major issue it has is a lack of applications.  Flash is a prime example, but many other programs dont have a 64bit version yet either.  You need to do many "workarounds" to get stuff up and running properly.  You should be aware that 64bit is a project much more than 32bit before you start.  As far as what performance you lose, it depends on what you do.  For nearly all tasks, 32bit and 64bit are indistinguishable.  Very processor intensive tasks (e.g. compiling a custom kernel, or maybe very heavy photo/video manipulation) will see some difference, but unless these are tasks you plan to perform regularly I would stick with 32bit for the time being.

---

### Post by jbulcher on 2007-03-10
Thanks for the tip!

---

