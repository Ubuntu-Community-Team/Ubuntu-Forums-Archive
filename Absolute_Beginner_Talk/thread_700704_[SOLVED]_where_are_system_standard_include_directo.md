---
title: "[SOLVED] where are system standard include directories in Ubuntu"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by bobbyubun on 2008-02-18
Hello group,

I just wanted to know where are system standard include and library
path or directories in Ubuntu?
I searched in /usr/include and /usr/local/include and I could not find
any header?!! gcc is already installed in my system!
also I looked in:
usr/local/include
/usr/lib/gcc-lib/target/version/include
/usr/target/include
/usr/include
as indicated in [http://m68hc11.serveftp.org/doc/cpp_2.html#SEC8](http://m68hc11.serveftp.org/doc/cpp_2.html#SEC8)
still could not find stdlib.h types.h stdio.h and so on!!!
I appreciate it if you send me the list of the directories the gcc
looks for the header files and libraries for compilation in Linux
Ubuntu.

Thank you for your help
bobby

---

### Post by ruy_lopez on 2008-02-18
/usr/include is correct. You need to install "build-essential" package.

---

### Post by bobbyubun on 2008-02-19
Thanks a lot 
Problem Solved

---

