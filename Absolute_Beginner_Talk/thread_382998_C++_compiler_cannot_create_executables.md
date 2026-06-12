---
title: "C++ compiler cannot create executables ??"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by pspman3 on 2007-03-12
Ok, im pretty new to Ubuntu and I must say im very impressed with it GUI and support wise (ive played with Gentoo,YDL,Debian, and some other distros) but I cant get source code compiled I dont know if its me or if my system is missing some key component but every time I try to compile something form source it gives me this message and stops (the compiling not the system)

checking for C++ compiler default output... configure: error: C++ compiler cannot create executables

:confused: 
can someone tell me how to fix this it works fine with .deb files 
P.S. Im running pretty good hardware 
Pentium 4 @ 3.0Ghz 
512 MB RAM
DVDRW
128 MB Ati radeon 9200

thanks :guitar:

---

### Post by Scunizi on 2007-03-12
It sounds like you're trying to create an "exe" file for the windows environment.  If that's the case you might need to create it from within the windows environment.  There are GPL tools to do that similar to what you're using to create deb's.

---

### Post by brianw0667 on 2007-03-13
I can't compile either.  the compiler can't find standard libraries (stdio.h, iostream.h, etc...).  When I search for these include files they can't be found. Have tried to install another version of gcc but still can't compile.

---

### Post by lloyd_b on 2007-03-13
> I can't compile either. the compiler can't find standard libraries (stdio.h, iostream.h, etc...). When I search for these include files they can't be found. Have tried to install another version of gcc but still can't compile.

In a terminal window, run "sudo apt-get install build-essential".  It sounds like you're missing one particular package (libc6-dev, IIRC), but I wouldn't bet against there being other things missing.  "build-essential" should install everything that you need to have a working compiler.

Lloyd B.

---

### Post by brianw0667 on 2007-03-13
Thanks,  I will try that.  Just to let you know I have Xubunto installed which I downloaded recently and installed.

---

### Post by brianw0667 on 2007-03-14
Thanks again, that worked.

---

