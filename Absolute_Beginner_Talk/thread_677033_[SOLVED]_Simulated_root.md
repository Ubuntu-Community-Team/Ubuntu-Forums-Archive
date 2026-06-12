---
title: "[SOLVED] Simulated root?"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by TJCIB on 2008-01-24
I installed Linux on one computer at the school where I teach.  It is my first experience with Linux, I am happy so far, and I have it all set up to meet the students' needs.  I have a "student" login so they cannot mess anything up...but kids are curious, they want to play around with new things.

Is there any way to get the high schoolers experience on a Linux box without them seriously messing something up.  I was thinking like a "simulated root" type thing where they can type in commands and then see results and process, but when they are done nothing has really changed?

I have thought of getting it set up how I want and making a boot CD from that so I could reinstall anytime something goes funny, but that is way time consuming (since I am not the IT guy, we don't have one).

I was thinking like a system restore (which I know does not exist), or revert, or a dummy terminal program or something.  I don't know enough yet to know the possibilities.

A simple "no" might be the answer.

Thanks from Brazil...

---

### Post by emarkd on 2008-01-24
How about runninng a Linux environment inside a virtual machine?  That way if something goes wrong, you can just copy over a good hard disk image.

Check out VirtualBox or VMWare

---

### Post by insane_alien on 2008-01-24
indeed, a virtualised system would be perfect for this. set it up use the snapshot feature and if anything gets screwed up just hit 'revert to snapshot' i use this for testing purposes if i'm doing anything dodgy.

---

### Post by fatality_uk on 2008-01-24
Perfect advice gents. Just gonna stick thanks to both of you :)

---

### Post by TJCIB on 2008-01-24
Indeed, thanks for the advice...

---

### Post by y-lee on 2008-01-24
Also of interest might be, [Cygwin]("http://www.cygwin.com/"). Cygwin gives windows users a Linux/Unix like terminal. :) See [Wikipedia]("http://en.wikipedia.org/wiki/Cygwin") for more.

---

