---
title: "can't run executable I compiled"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by markg729 on 2006-10-14
ok so i have an executable that i had compiled from c++ code that ran fine when i compiled it for windows but now when i double click the executable nothing happens, help?

---

### Post by David_T on 2006-10-14
are you running this on windows or linux?
and what did you use to compile?

---

### Post by markg729 on 2006-10-14
im running this in linux, and just used gcc to compile it using "g++ *** -o ***"

---

### Post by taurus on 2006-10-14
You cannot run a binary that you compiled in Windows under Ubuntu unless you use some kind of emulator!  Therefore, get out your source for that binary and compile it again under Ubuntu then...

p.s.  Try running it from a terminal with

```
./<filename>
```

---

### Post by markg729 on 2006-10-14
thanks guys, i didnt realize that it wouldnt run if it wasnt in the terminal

---

### Post by IYY on 2006-10-14
It probably still ran, but you didn't see output because it sent it to stdout which is basically the terminal.

---

