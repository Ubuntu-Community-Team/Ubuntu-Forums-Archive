---
title: "C++ Compiler"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by Cullen on 2007-08-21
I am enrolled in a beginning programming class for college.  Class started this last Monday, and they want me to procure Microsoft Visual Studio, is there a Linux alternative?

---

### Post by Michael Young on 2007-08-21
Alternative for a C++ compiler?  Sure.  (Although Visual Studio supports a suite of compilers, not just C++.)  Try gcc/g++.
Alternative for a GUI IDE?  Sure.  Try kdevelop.
Alternative for all the libraries and frameworks that come with Visual Studio?  Functional equivalents, probably - but things are different between Windows and Linux.
I guess the bottom line depends upon what the course content is - does it teach standard C++, or MS Visual C++ / MFC / Windows programming?  (A lot of teachers unfortunately do not even know that what they teach includes proprietary VC++ extensions.)  Also, keep in mind that your prof and/or TA will probably only provide help if you're in a familiar, standard environment that they specified - i.e., MS Visual Studio.  But kdevelop/g++ is a reasonable equivalent in Linux.

---

### Post by Frak on 2007-08-21
G++ (from GCC) is good
install it with
```
sudo aptitude install build-essential
```

---

### Post by tzulberti on 2007-08-21
You should install build-essential...

Also, you have the following ides:
Codeblocks (you have a deb package in their page)
Kdevelop
Geany.

---

### Post by Cullen on 2007-08-21
Thanks for the input.

I think you're right, not sure the professor is willing to deal with me working outside the confines of the Visual Studio environment.  Oh well maybe there's wine support for it.....(I dual boot but starting to really dislike Windows)

---

### Post by Paulmd on 2007-08-22
> **Cullen said:**
> I am enrolled in a beginning programming class for college.  Class started this last Monday, and they want me to procure Microsoft Visual Studio, is there a Linux alternative?


When I was learning various programming languages, some of the professors wanted to turn in the compiled program on floppies, just to prove they actually work. 

You may have to make EXEs, and not the linux equivlents.

---

