---
title: "valgrind memory leak check for C++ binaries"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by mdecler2 on 2006-10-03
Hello. I am a relatively new user to Ubuntu.
I have been using Ubuntu to compile C++ programs, but when I use ```
valgrind --leak-check=full ./<binary>
```
I always get 27 errors about ld (which apparently is a linker) about "Conditional jump or move depends on unitialized values".  The ld program is /lib/ld-2.3.5.so .

Any help, advice, or question is appreciated.

---

