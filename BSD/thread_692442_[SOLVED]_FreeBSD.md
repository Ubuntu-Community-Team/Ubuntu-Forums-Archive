---
title: "[SOLVED] FreeBSD"
date: 2008-02-09
forum: BSD
---

### Post by chris200x9 on 2008-02-09
I'm going to build a computer this summer and I'm looking for an OS, I'm probably going to go with gentoo or freebsd so I have a few questions.


1. does freebsd have 64 bit support?

2. I have heard it is optimized for KDE would installing fluxbox be a step back from fluxbox on gentoo performance wise?

3. I know it has a linux compatability layer but can I compile and install linux source code as a native bsd program?

4. is there anyway to kind of "build it myself" so it's optimized for my machine like I can with gentoo?

5. which one would give me the best overall performance?


thanks

---

### Post by jinx099 on 2008-02-09
Yep, FreeBSD has an amd64 port.  That'll work with your 64-bit AMD or Intel CPU.

I'm not sure about compiling linux code on FreeBSD.  I've got a freeBSD box here that I might try that out on.  Is there anything in particular you'd like me to try?

I don't think you can optimize it as much as gentoo.  Gentoo makes heave use of the USE flags which I found to be a big PITA.  If you really find out the bare minimum USE flags you need, gentoo would probly be a lot more optimized than freeBSD.

What are you using this system for?

---

### Post by chris200x9 on 2008-02-09
ummm yea actually if you could I was looking on sourceforge and found that almost all linux source compiled on the system will run on any unix-like system but I'm not sure about handbrake and that is a crucial app for me so if you would be so kind to go to handbrake.fr and download the source code and compile it and see if it works I would really appreciate it, and if you can just run it on default settings and give me the average FPS (so I can see if there is any performance hit)  that would be awesome too!


thanks so much!

as far as what I'm using it for, basically just learning and a desktop, but I am also a "power user" you might say so I want to get as much performance as I can out of my hardware. Also I might want to learn networking maybe.

---

### Post by jinx099 on 2008-02-10
I havent been able to compile it, it doesn't like "jam"

```
-bash: ./jam: cannot execute binary file
```

But, I did download the linux binary and it seems to run fine.  I did not try actually using the software to convert something.  Maybe I'll mess with it more later.  I'm running the 386 version of FreeBSD BTW.

---

### Post by chris200x9 on 2008-02-10
thanks for your help looks like I'll probably go with gentoo

---

