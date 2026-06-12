---
title: "problems with Intel Fortran Compiler"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by Darzic on 2007-10-24
Didn't know where to put this, but seeing as i am completely new to ubuntu, i decided to try it here.

i have managed to install intel fortran 10.0.026 with ubuntu 7.10.  i can now find intel and run ifort.  but when i try to compile a simple program like hello world i get an error saying:

/opt/intel/fc/10.0.026/bin/fortcom: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
ifortbin: error #10257: Fatal error in /opt/intel/fc/10.0.026/bin/fortcom, terminated by 0x7f

now I am pretty sure that what i need is the      libstdc++.so.5    anyone have any idea how to find this and install it?  cause i have had no luck so far

---

### Post by Darzic on 2007-10-24
ok, i found the answer by doing some more searching...

so for anyone else wondering about the same, here is the answer, thx to Joshuwa


Code:

sudo apt-get install libstdc++5

will install what you need

---

### Post by Maestro23 on 2007-10-24
Good deal.  Can you mark this SOLVED via the Thread Tools.

Thanks.:)

---

