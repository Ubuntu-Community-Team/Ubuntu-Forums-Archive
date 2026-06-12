---
title: "ddd debugger"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by rob21 on 2008-02-01
in a ddd debugger I cannot get the source code files to dispaly so that I can debug the various functions and variables. I tried everything in the menu bar. Please help.
         thanks.

---

### Post by mattismyname on 2008-02-01
Sorry for the (probably) useless response, but I would use gdb.  Every time I've ever tried to start using ddd, I get mad and punch the computer.

Also, a commercial app like totalview is a nice GUI debugger.

---

### Post by Cypher on 2008-02-01
How are you compiling your code? You have to use the "-g" or "-g3" for extra debugging information before the debugger will show you anything of value.

DDD is just a front-end to GDB..

---

