---
title: "compiler/java"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by deji04 on 2007-09-17
I'm trying to compile some fortan program and I get this message:
/usr/bin/ld: crtl.o: No such file or directory
collect2: ld returned 1 exit status
maybe it's because I' new to both fortran and linux. also when I tried to compile hello.f,
I get " Invalid first character at (^) [info  -f g77 M LEX]
Please help!

---

### Post by jamvegan on 2007-09-17
What editor are you using to write the code?  Did you copy and paste any or all of it?  I've always had problems with C/C++ code that's copied from a word processor, even OpenOffice, and even if I go through in vim and replace everything that seems suspect (fancy quotes, line breaks, etc.) gcc complains about bad characters.  Then if I completely retype everything in vim, ending up with a new file that looks exactly the same as the original file, it compiles just fine. (And this does produce linker errors, too, when the mysterious bad characters prevent the compiler from processing includes properly.)

---

